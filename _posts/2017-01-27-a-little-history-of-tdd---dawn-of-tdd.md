---
title: The Dawn of TDD
categories:
  - Testing
  - TDD

---

Young and unexperienced our art is and unique properties it has.

As a result, there's much discussion going on about what defines professionalism in software development. Developer-testing practices and Test-Driven Development (TDD), in particular, are part of these discussions.

But what is this TDD? Where did it come from? How did it attract both fanboys and haters? Why has is it well-known advocates---such as Robert C. Martin (Uncle Bob), Martin Fowler, and Kent Beck---as well as opponents---such as David Heinemeier Hansson (DHH), Jim Coplien (Cope), and Rick Hickey?

Let's take a step back and do a little research, before we jump in screaming and shouting, shall we?

## A Little History of TDD

About 41 years ago, in October 1976, Glenford Myers published his book "[Software Reliability][sw-reliability]," which states as an axiom that "a developer should never test their own code." The Agile Alliance refers to the following years as [the Dark Age of Developer Testing][aa-tdd]. A time where valiant developers fought (not-so-)heroic battles against evil QA departments, who would try to blame them for producing buggy code. And it was not until the early 90's that the dawn of a new era began.

In 1991, [developers at Taligent came up with the Test Framework][tf-taligent], a framework for executing, logging, and evaluating tests. This apparently completely independent work is surprisingly to the mother of all unit-testing frameworks, [SUnit][sunit],[^sense8] which Kent Beck started to work on in 1994. Kent first wrote about SUnit in "[The Smalltalk Report][sunit-tsr]," recommending that "developers write their own unit tests, one per class" and "that developers spend 25-50% of their time developing tests."

In 1999, Kent Beck's "[Extreme Programming Explained: Embrace Change][xp-explained]" states that whether developers write new functionality, refactor existing code, or fix a bug, they should "start with a test, so we know when we are done." Kent further mentions that writing tests first requires developers to "do a certain amount of design" and that they should "design and implement just enough to get the test running" and repeat this in process over and over again.

Until 2002, the concept of "test first" slowly evolves to "test driven". Much of this happened on [Ward Cunningham's wiki][c2-wiki-tdd]. In November 2002, Kent Beck publishes "[Test Driven Programming: By Example][tdd-by-ex]", which became *the* reference to this very day. The book is received enthusiastically by many developers.

In the following years, more and more positive effects are associated with TDD:

* The XP Lessons Learned state that TDD leads to [faster development, higher code quality, better design, and less waste][xp-test-first].
* Martin Fowler considers [self-testing code and clean interfaces][tdd-fowler] the main benefits.
* Uncle Bob lists [exhaustive test suites, close to no debugging, changing code without fear, documentation by example, ensured compatibility with external dependencies, and reduced coupling][tdd-ubob] among others.
* James Shore adds [fast feedback in case of mistakes and safe refactoring][tdd-shore].

In June 2007, Uncle Bob publishes the article "[Professionalism and Test-Driven-Development][tdd-professional]" in the IEEE Software magazine. TDD is now officially associated with good software craftsmanship and [considered a mature pratice][aa-tdd].


## Joining Later

I first started programming in the late '90s or early '00. It was not until around 2005 that I first heard of TDD. I had enough experience at the time to know the troubles of debugging and the pain, if you find you broke a part of the code by seemingly unrelated changes in another one. So I was eager for solutions.

At that time, I was a kid programming mostly on his own. I didn't know about waterfall, nor had I heard about agile, or even XP. With this background, I first read about TDD.[^reverse-waterfall] I heard the praise and was awed by all the good it would do.

What I realized only much later is that I was completely missing the context of the things I read.

All the reports about TDD were written by developer who had experienced the Dark Age. If I read their articles and comments now, I note the sporadic hints at the alternative to test-first programming being a waterfall-like setting, where *all* testing happens after *all* development, possibly by an entirely different team. And I understand that the reason many documents don't mention this at all, is probably because at the time of writing this seemed obvious to the authors.

It is easy for us to forget the context of statements, especially when reading documents without publication dates.

The let's review thing and put them in context. For next week, I plan to look at what people say against TDD. And then, of course, there's also the "neutral" side! So let's see what academic studies have contributed to the mess.

There's a long road ahead of us. Let's go.

 [^sense8]: Ideas for which the time was right have always had the tendency to pop up independently in various places at about the same time. According to the [Christmas Special](http://www.imdb.com/title/tt5031232/) such "coincidences" might be explained by the existence of [Sense8](https://en.wikipedia.org/wiki/Sense8).
 [^reverse-waterfall]: Looking back, I didn't even understand the concept. To me, test-first programming meant that I would write *all* tests before *any* production code. A reversed waterfall, if you so will. It was an eye-opening moment, when I finally understood.

 [sw-reliability]: https://books.google.de/books?id=NtQmAAAAMAAJ
 [aa-tdd]: https://www.agilealliance.org/glossary/tdd/
 [tf-taligent]: https://shebanator.com/2007/08/21/a-brief-history-of-test-frameworks/
 [sunit]: http://sunit.sourceforge.net/
 [sunit-tsr]: http://www.macqueen.us/smalltalkReport/ST/91_95/SMAL0402.PDF
 [xp-explained]: https://books.google.de/books?id=G8EL4H4vf7UC
 [xp-test-first]: http://www.extremeprogramming.org/rules/testfirst.html
 [c2-wiki-tdd]: http://wiki.c2.com/?TestDrivenDevelopment
 [tdd-by-ex]: https://books.google.de/books?id=CUlsAQAAQBAJ
 [tdd-professional]: http://www.researchgate.net/publication/3248924_Professionalism_and_Test-Driven_Development
 [tdd-fowler]: https://martinfowler.com/bliki/TestDrivenDevelopment.html
 [tdd-ubob]: http://butunclebob.com/ArticleS.UncleBob.TheThreeRulesOfTdd
 [tdd-shore]: http://www.jamesshore.com/Agile-Book/test_driven_development.html
