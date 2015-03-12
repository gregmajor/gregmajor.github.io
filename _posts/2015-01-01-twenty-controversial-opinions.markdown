---
Layout: post_simple
Title: "Twenty Controversial Opinions"
Date: 2015-03-12 

Tags:
- programming
- mac
- OSX
- Windows
---

I came across a great post over on BlogExchange titled, “20 controversial programming opinions” and before I read more than a few down the list, I decided to jot down my gut reaction to each one. Jump over there and read the original blog post then come back.

Back? Okay, here’s how it went:

1. Programmers who don’t code in their spare time for fun will never become as good as those that do.

Except for the “never” bit, I completely agree. I suppose it’s possible that someone might emerge from the womb with The Right Stuff (and probably named Bjorn or something), but it’s not very probable. All the best programmers I know are Very Smart People that live and breathe what they do.

2. Unit testing won’t help you write good code.

The assertion here is weak. I certainly believe that unit testing will help you write better code than you would have otherwise. Sounds like this guy’s issue might be more about TDD than unit testing in general.

3. The only “best practice” you should be using all the time is “Use Your Brain”

Oh, I absolutely love statements like this. I hear them quite a lot, too and it generally sounds like, “Inblerbsion of Conjiggers? Ortho-Rebobble Matching? It’s all useless overhead!“. More often than not, the person spouting this gibberish is a clock-puncher with a fear of change casually mashing out the ASCII equivalent of a supermassive black hole that even Hawking couldn’t comprehend. Hey, if you want to code like it’s 2004 that’s your business, but don’t try to pull yourself up using the “Cool kids don’t want what’s cool” strategy.

4. Most comments in code are in fact a pernicious form of code duplication.

Another all-time favorite of mine! Comments? We don’t need no stinking comm… I’ll spare you the cliche, but programmers that wear this one like a badge are generally the ones that I probably don’t want writing comments (or code) in the first place.

It’s really simple. Comment to A) express intent and B) explain your lazy bullshit. Nothing more and nothing less. Terse, intention-revealing comments are like tiny, human-compiled unit tests. What is this supposed to do? Oh, the person that wrote it left me a handy little time capsule RIGHT THERE ABOVE THE CODE. Neat!

5. “Googling it” is okay!

Damn straight it is, but Google-Paste-Go is not.

6. Not all programmers are created equal.

This is controversial?

7. I fail to understand why people think that Java is absolutely the best “first” programming language to be taught in universities.

It’s free.

8. If you only know one language, no matter how well you know it, you’re not a great programmer.

I agree in principal, but I also acknowledge that there are exceptions. I usually tell programmers that ask me the “how can I get better at <insert language>?” to go learn some other language. You’ll find yourself discovering new ways to solve old problems.

9. It’s OK to write garbage code once in a while.

Every line of code I wrote before today was complete garbage. Okay, okay… I get the spirit here and I agree with two conditions; you must be capable of recognizing that what you are writing is garbage and you must be willing to defend your decision.

10. Print statements are a valid way to debug code.

Blech.

11. Your job is to put yourself out of work.

Damn straight it is! If I’ve really done my job, there is no maintenance. No support tickets. Just a blissful green pasture of new requirements and happy users. Now all I have to do is figure out how to do my job that well all the time.

12. Getters and Setters are highly overused.

The public members in my type are a contract and interface to everything that exists beyond the boundary of that type. Exposing public fields is a bit too close to “meh, it’s just a bag of data” for me. Using accessors affords me the opportunity to hone the public contract and provide some kinds of useful behavior (NotifyPropertyChanged).

13. SQL is code. Treat it as such.

Agreed. It should be well-formatted, version controlled, and tight. SQL is not, however, where I expect to find anything beyond what’s necessary to build and maintain my persistence mechanism. Keep your business logic somewhere else, please.

14. UML diagrams are highly overrated.

Perhaps, but they’re far more useful than a stack of requirements that make a Sears catalog look like a flyer from the Chinese joint left under your windshield wiper. If your requirement can’t be summed up in just a few sentences, try drawing it on the whiteboard like you were explaining it to your kids.

15. Readability is the most important aspect of your code.

Agreed. Well formatted code is a breeze to work with. Then again, if you wrote a hideous beast that looks like an obfuscator let it rip after an ill-fated bender at Buffalo Wild Wings, but I never have to touch it because it always works. Well…

16. XML is highly overrated.

I agree that XML gets overused. Seriously, if I see one more DSL written as a meta language expressed with XML I’m going to… well, I’m probably going to play around with it.

17. Software development is just a job.

Hippie!

18. If you’re a developer, you should be able to write code.
Again, this is controversial? Who’s arguing that developers should be able to write code?

19. Design patterns are hurting good design more than they’re helping it.

Yet another long-time favorite of mine. Patterns are useless and harmful? I’m guessing that’s going to come as a real surprise to everyone that’s learned that patterns are first and foremost about recognizing patterns rather than applying them.

20. Less code is better than more!

As programmers, we should be keen on a simple formula:

    P / C = V

Where P is the problem, C is the code, and V is the proportion of value.

Your value to the domain is determined by how many problems you solved with your code, right? Not terribly unlike Stoichiometry, however, it gets complicated very quickly. See, for every unit of C we can assign a coefficient. By assigning negative coefficients to measure aspects of C that do not directly solve P and positive coefficients to the aspects of C that do solve P we can start to understand where value comes from.

For example, if…

Nah, I’ll leave this one for another day. :)
