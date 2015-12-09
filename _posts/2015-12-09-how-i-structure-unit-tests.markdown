---
layout: post_image
title: "How I Structure Unit Tests"
date: 2015-12-9 02:04:00
image_file: "blog/unit-tests.jpg"

tags:
- programming
- unit testing
---

# How I Structure Unit Tests

There are likely as many conventions for unit test structure as there are programmers. However, for the past few years I've used a slightly modified version of one I found in Phil Haack's [Structuring Unit Tests blog post](http://haacked.com/archive/2012/01/02/structuring-unit-tests.aspx/). It goes like this:

## The Pattern

	[P] SomeProject.UnitTests
		[F] SomeLogicalGroupTests (0-N optional)
			[F] SomeClassTests
				[C] MethodShould.cs
					[M] DoSomethingGivenSomeCondition

Where:

	- [P] = project
	- [F] = folder
	- [C] = class
	- [M] = method

Which, in the real world looks something like this (assuming a C# project):

	TheWorldNeedsAnother.Calculator.UnitTests.csproj
		OperationTests
			PrimaryOperationTests
				AddTests
					SumShould.cs
						ReturnPositiveNumberGivenPositiveOperands()
						ReturnNegativeNumberGivenNegativeOperands()

I really like how all this works out and I haven't stumbled upon a better way yet. What surprised me the most is how it really made it much simpler to *quickly* identify what was broken without having to dig around a giant unit test class. When I see a failed test, the test runner has already given me a lot of information by nature of the convention.

Additionally, I've found it very valuable when I'm thinking about test coverage. With this structure, I can tell immediately if a method has any coverage or not without needing to open a single file. What's more, I can browse the structure quickly and spot coverage gaps without having to wade through dozens or hundreds of tests.

Oh, and did I mention how easy it makes refactoring? If I move a method from one type to another or perform other significant refactorings, putting the unit tests where they belong (which is sometimes in the garbage bin) is quick, easy, and safe.

### PROS

- It keeps the tests very nicely organized
- It makes it dead-simple to "eyeball" coverage
- It reads very nicely in tools such as NUnit Test Runner and ReSharper's test runner

### CONS

- You have to make a new class (file) per method under test (unless you don't mind more than one class per file)

Is this the One True Unit Test Structure? I honestly don't know. I _do_ know, however, that it's the structure that has worked really, really well for me.
