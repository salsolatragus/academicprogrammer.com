---
title: Is TDD Just Unit-Test Waste?
categories:
  - Quality
  - Testing
modified: 2017-03-01

---

In early 2014, Cope published an article titled "[Why Most Unit Testing Is Waste][cope-waste]" and little later a [follow up][cope-seque]. In these articles, Cope states that unit testing, i.e., testing of individual functions, targets the wrong level of granularity for object-oriented software and will only every cover a very small subset of the actual state space, therefore, finding only few bugs.[^cope-evidence] Worse, splitting functions solely for the sake of testability destroys the design. Tests (or test coverage) should never become a primary goal.

First of all, yes, Cope talks about unit testing, not TDD in particular. For me, the idea of TDD doesn't even strictly require *unit* testing, in the sense that I always have to test only an individual class, object, or function in absolute isolation. I don't see this in Uncle Bob's [Three Laws of TDD][unclebob-tdd] or in [Martin Fowler's description of TDD][fowler-tdd]. I'm aware that TDD encourages [testing small units in isolation][wp-tdd-small], but small and minimal are two different pairs of shoes. Nevertheless, Cope raises a valid point against a possible application of TDD: don't loose sight of your actual target. Writing tests or restructuring code to have a large number of tests or higher coverage is stupid [number porn][ud-number-porn].

As for the number of bugs discovered by unit testing: especially tests written in TDD can hardly discover bugs, because by definition they pass when you're finished. They encode your understanding of the requirements. If that is flawed, so are the tests. Nevertheless, they guarantee that you made no mistakes in implementing what you understand are the requirements. If you don't even know that much.... well... And don't even think about telling me you don't make mistakes. 

Cope observes further that test code may easily become larger then the production code it covers, resulting in a significant maintenance cost and increasing the probability of bugs (which my also hide in test code). Therefore, he proposes to drastically reduce the number of tests following these guidelines:

* Tests should be primarily functional tests designed by business people, i.e., derived from and clearly linked to business requirements. Tests that do not have this property should be deleted, because they are just "programmers' fantasies," unless you have a strong third-party oracle.
* Low-risk tests, i.e., tests that practically never fail, give close to no information. Therefore, *any* test that did not fail within a year should be deleted.
* Tests should be converted to assertions,[^assertion] whenever they express pre- or post-conditions of an operation or invariants. Trust your stress, integration, and system tests to reveal input that violates assertions. Ideally use this mechanism for failure detection (and possibly also recovery) in the product.

Of course, if you can do testing in direct cooperation with business experts, e.g., in a pair programming or even [mob programming][mob-programming] setting, by all means, *do it*. If you can't, at least test that what you write meets you understanding of the problem. See above. 
 
I agree that it is easy to write unit tests that are hard to trace back to business requirements and that such tests are problematic, because when they fail, you cannot be sure whether that's a problem. I believe that the solution to this problem lies in binding tests, on any level, to a justification, e.g., by adding the *Why* to the test name or as a comment. If there's no reason for the test: Delete it. It's waste. 

I'm definitely against deleting tests only because they didn't fail in a given timeframe. Admittedly, blindly executing all tests after any change is most-likely wasteful. After all, the tests for an unchanged unit will not suddenly fail. However, I want these tests to still be there when I change that particular unit. Tests often remind me of constraints I long since forgot (provided they tell me why they are there). The maintenance cost of such tests should be low, because they need to change only if the corresponding unit changes.

That said, I think [it hurts to blindly keep all tests written in TDD][seradio-256]. I often write tests that turn out to duplicate or include others. This is waste. It violates [DRY][dry]. I keep an eye out for such (fragments of) tests during the refactor phase and delete them. Again, tests are not there to satisfy you by their large number. The number of tests in your suite in itself has no value.

After reading Cope's articles, I will also keep an eye out for tests that are assertions in disguise. Currently, I imagine these to be mostly tests about illegal inputs, but I might be mistaken. In any case, these conditions are part of a contract and I believe it is a good idea if something notifies you distinctly about a caller (or worse, the callee!) violating this contract. I'll report back on where this leads me.

Finally, Cope observes that developing isolated units easily leads to them having more functionality than they require, because programmers implement them more general then they need to be in order to fullfil the business requirements. This additional functionality is waste. Cope advocates minimal functionality, like Kent Beck advocates Simplicity in "[XP Explained][xp-explained]."

As [CodingHorror][ch-ruleo3] puts it:

> "Every programmer ever born thinks whatever idea just popped out of their head into their editor is the most generalized, most flexible, most one-size-fits all solution that has ever been conceived. We think we've built software that is a general purpose solution to some set of problems, but we are almost always wrong."

We have this tendency. Every developer I've met so far has. I don't think this is related to TDD in particular, although working on isolated units may encourage it. I've seen people fall prey to [premature abstraction][premabst] and building flying castels without a single test involved. The only way I know to mitigate this threat is discipline. It helps to have guidelines, such as the [Rule of Three][ch-ruleo3], or to work in pairs, mobs, or with regular code reviews.

All in all, I find Cope's articles inspiring. Although I must admit that I was inclined to write them off as rubbish at first sight. It's so easy to do this with opinions that attacks one's believes... As I contemplated Cope's words, I came to see more and more interesting thoughts in them and, finally, found that I even agree with many. Unit testing and [TDD are no miraculous salvation][jbrains-tdd-not-magic] from all our problems. We must take care and think about how we apply them.

Thank you, Cope, for helping me go one step further.

  [cope-waste]: http://rbcs-us.com/resources/articles/why-most-unit-testing-is-waste/
  [cope-seque]: http://rbcs-us.com/resources/articles/seque/
  [^cope-evidence]: Work by Capers Jones supports Cope's hypothesis regarding the inefficiency of unit tests for findings bugs. The book "[Programming Productivity][programmer-productivity]" (1986) reports functional tests, integration tests, inspections, and reviews to be far more efficient. A draft on "[Software Defect Origins and Removal Methods][sdoarm]" (2012) confirms this finding, though the other testing methods appear less dominant.
  [programmer-productivity]: https://books.google.de/books?id=CIxQAAAAMAAJ
  [sdoarm]: https://www.google.de/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwj72uCFjYXSAhWB1hQKHa-vCEgQFgghMAA&url=http%3A%2F%2Fwww.ifpug.org%2FDocuments%2FJones-SoftwareDefectOriginsAndRemovalMethodsDraft5.pdf&usg=AFQjCNFpSIwVAQtCMCaECeXIpNw953C5AQ&sig2=qrss64We1NQOf8WBSv9buw
  [unclebob-tdd]: http://butunclebob.com/ArticleS.UncleBob.TheThreeRulesOfTdd
  [fowler-tdd]: https://martinfowler.com/bliki/TestDrivenDevelopment.html
  [wp-tdd-small]: https://en.wikipedia.org/wiki/Test-driven_development#Keep_the_unit_small
  [ud-number-porn]: http://www.urbandictionary.com/define.php?term=number%20porn
  [^assertion]: Assertion here means an assertion *in the production code*, as opposed to an assertion in a test.
  [mob-programming]: http://mobprogramming.org/
  [seradio-256]: http://www.se-radio.net/2016/05/se-radio-episode-256-jay-fields-on-working-effectively-with-unit-tests/
  [dry]: http://wiki.c2.com/?DontRepeatYourself
  [xp-explained]: https://books.google.de/books?id=-DNcBAAAQBAJ
  [ch-ruleo3]: https://blog.codinghorror.com/rule-of-three/
  [premabst]: http://wiki.c2.com/?PrematureAbstraction
  [jbrains-tdd-not-magic]: http://blog.jbrains.ca/permalink/tdd-is-not-magic
