---
layout: post_simple
title:  "Debugging as Twice as Hard"
date:   2015-03-17 18:21:00

tags:
- programming
- theory
- debugging
---

> Debugging is twice as hard as writing the code in the first place. Therefore, if you write the code as cleverly as possible, you are, by definition, not smart enough to debug it.

> **Brian Kernighan and P.J. Plauger, The Elements of Programming Style**

I love that quote because it's so very true. It's a tendency I see again and again. They say, *"Why, just look at how I injected the Kebabaflobber as a commanding visitor with only a little bit of reflection and some aspect libraries! Now the original method is just three lines!"* Yeah, how much impossible to debug garbage under the hood? Ugh.

There are, I suppose, a multitude of reasons why this is so common. The trait exists in nearly ever programmer, too. I know that when I saw dependency injection for the first time it became the solution I just had to refactor all of my active projects to use. Aspect oriented libraries? Yep, couldn't live without those! CQRS? Heck yeah... wait, no. I never really swallowed that as dogma.

It's short-sighted to blame the tools, however. They exist to solve problems - and they do (even if the trade is for a few new problems). Afterall, I use dependency injection, noSQL or an O/RM, and many other such tools in pretty much every project. The trick is to use the right tool for the job at hand **and** to use the fewest number of high-quality tools as I, the craftsman, consider responsible.

> Programming tools and techniques survive and spread in a chaotic, evolutionary way. It’s not always the pretty or brilliant ones that win but rather the ones that function well enough within the right niche—for example, by being integrated with another successful piece of technology.

> **Marijn Haverbeke**

When I started as a woodworker I subconciously tried to use every tool in my arsenal on each project. At least it seems that way looking back my early projects. As my skills matured I realized that craftsmanship is born of using as few tools as possible - as few "touches" as possible - to deliver my product and learning how to use those tools to the best of my ability.

Some of this comes from the understanding that each time you perform an operation you run a risk of screwing it up. Gradually I learned that a simple, sharp chisel is all I needed to, for example, mortise a hinge. With practice, I got to a place where pulling my trusty 1/2" James Swan out of my apron and getting to work was much faster and just as accurate.

Sure, there are times when you really need those speciality tools. There are also times when it just makes more sense to have timesavers. I appreciate the tools of the past, but you'd have a hard time convincing me to cut a dado by hand. The same is true with software. I have no desire to write an [object-to-object mapper](http://automapper.org/), an [OR/M](http://nhibernate.info/), or [metrics library](https://github.com/danielcrenna/metrics-net). Those are the decisions I make as a craftsman.

I believe the same applies to software. Mastering the essential tools and using as few "touches" as possible to deliver the product is what we should strive for. What
