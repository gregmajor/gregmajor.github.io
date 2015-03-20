---
layout: post_simple
title:  "Deleting All Docs in a Raven Collection"
date:   2015-03-18 14:33:00

tags:
- raven
- migration
- programming
---

Recently I was faced with a problem I've never encountered before. I needed to delete all of the documents in a RavenDB collection during a data migration (using FluentMigrations for what it's worth) and re-populate the collection using data from a SQL Server table. Simple, right? Well, yes and no.

Of course, we all know that RavenDB embraces the "eventual consistency" notion. That means that RavenDB *users* also have to embrace it. Okay, that's no problem, but when you're in the midst of a migration and you need to be sure that **all** of the documents are gone before you perform a bulk insert? Here's the (pseudo) code I started with:

{% highlight csharp %}
public override void Up()
{
    base.Up();

    var fooBars = new List(...);

    var operation = documentStore.DatabaseCommands
        .DeleteByIndex("Raven/DocumentsByEntityName", new IndexQuery()
            {
                Query = "Tag:FooBars"
            });

    operation.WaitForCompletion();

    using (var bulkInsert = documentStore.BulkInsert(options: new BulkInsertOptions
        {
            CheckForUpdates = true
        }))
    {
        foreach (var fooBar in fooBars)
        {
            bulkInsert.Store(fooBar, fooBar.Id);
        }
    }
}
{% endhighlight %}

So what's the problem? Well, the DeleteByIndex call will throw an exception if the RavenDB index is stale and
that puts a screeching halt to your migration. Ouch! Of course my next move was to research. There is an IndexQuery option that allows for stale indexes called **allowStale** as such:

    {% highlight csharp %}
    var operation = documentStore.DatabaseCommands.DeleteByIndex("Raven/DocumentsByEntityName", new IndexQuery() { Query = "Tag:FooBars" }, allowStale: false);
    {% endhighlight %}

That option, however, felt pretty creepy because I really didn't *want* the indexes to be stale during this operation. I wanted to *know* that every document in the collection had been deleted. Setting that option aside, my next attempt used a retry pattern that tried the DeleteByIndex above, but upon failure would fall back to a different technique shown here:

    {% highlight csharp %}
    using (var session = documentStore.OpenSession())
    {
        var start = 0;

        while (true)
        {
            var current = session.Query<FooBar>()
                .Customize(x => x.WaitForNonStaleResultsAsOfNow())
                .Take(500)
                .Skip(start)
                .ToList();

            if (current.Count == 0)
            {
                break;
            }

            start += current.Count;

            current.ForEach(x => session.Advanced.DocumentStore.DatabaseCommands.Delete(x.Id, null));
        }
        {% endhighlight %}

This works because it's transactional and takes advantage of the WaitForNonStaleResultsAsOfNow customization on the query. Still, I didn't like the way that it smelled. My migration code was growing to a ridiculous size and I knew that I was on the wrong track. Besides, why would there be a DeleteByIndex capability if it wasn't terribly usable?

Finally, I re-stated the problem in my head; _"Wait until the indexes are NOT stale then delete by index"_. From there, I set about creating this implementation:

    {% highlight csharp %}
    var retryCount = 0;

    var waitForRavenConsistency = new Action(
        delegate
        {
            while (documentStore.DatabaseCommands.GetStatistics().StaleIndexes.Length != 0)
            {
                retryCount++;
                Thread.Sleep(3000);
            }
        });

    waitForRavenConsistency.Invoke();

    documentStore.DatabaseCommands.DeleteByIndex("Auto/AllDocs", new IndexQuery { Query = "Tag:FooBars" });

    waitForRavenConsistency.Invoke();
    {% endhighlight %}

Not only does this solution knock out a LOT of complicated retry code, but it's pretty obvious what's going on and why. Of course, I'm counting on RavenDB to *eventually* become consistent. If it doesn't then I'm stuck in an endless loop. If that happens, however, I've got a more serious issue to deal with.

It still seems a little strange to me that there's not a way to say, _"Hey, RavenDB! Nuke all the documents in this collection and, if the indexes are stale then I'll wait."_ Since I'm operating with the DatabaseCommands object it seems like waiting for consistency would be built in. Either way, I'm just glad to have a solution that feels (more) right even with the assumed risk.

Have you run into this problem? How did *you* solve it? Hit me up on Facebook or Twitter and let me know!
