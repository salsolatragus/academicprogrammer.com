---
title: TDD vs. Architecture
categories:
  - Quality
  - Testing
modified: 2017-03-03

---

In 2007, [Robert C. Martin (Uncle Bob) and James O. Coplien (Cope) had a discussion about TDD at the JAOO Conference][cope-ubob]. Uncle Bob opened the discussion proclaiming that it has become infeasible for a professional developer not to practice TDD. Cope, on the other hand, states that he has adopted a very strong position against what, in particular, the XP community calls TDD and absolutely rejects Uncle Bob's thesis. 

Cope's main concern is the idea that by practicing TDD architecture emerges and evolves automagically, even without extensive knowledge of the domain. He, and others he talked to, witnessed repeatedly that this attitude leads to dead ends in architecture that cannot (practically) be fixed. Uncle Bob agrees that this idea, which was the conviction of many agilists around 2000, is and has always been bullshit. Domain knowledge and a certain amount of consideration are necessary, but should be kept to the absolute minimum. As Kent Beck put it in "[XP Explained][xp-explained]": "Yes, do some up-front architecture, but don't knock yourselves out" and "you don't want to be guessing."

> Personally, I think Cope raises a very important point here. In my experience, it is very hard to refactored away from an unfitting design, also because unit tests do not well support moving functionality between classes and modules. So we should consider whatever domain knowledge we have available, to save us from such work. In a fact, Uncle Bob also agrees that [Little Design Up Front (LDUF) makes perfect sense][ubob-tdd-lduf].
>
> Unfortunately, sometimes there just isn't a business expert with the necessary domain knowledge (available), in which case we have to make do with the next-best thing we've got. With my benchmark pipeline [MuBench][mubench] for example, we went through multiple architecture changes in the past. As this pipeline is an integral part of my PhD, I'm probably the closest thing to a business expert that one might hope to find. We plan our architecture (BDD-style, if you so will), but still, sometimes I get it wrong. So we build the architecture according to what I currently think best fits our use cases and accept that this might change in the future, as we reach a better understanding of how we need the system to work.
>
> I've found that architecture changes often reduce test-code quality. When migrating tests to another object, we need to ensure they still make sense. If not, they should be deleted and replace by sensible ones, if necessary.

On the aspect of professionalism, Uncle Bob explains that he's convinced that shipping even a single line of code that has not been executed by a unit test is irresponsible and that one of the best ways to ensure testing is TDD. Cope counters that tests can only ever show the presence of bugs, not their absence and that, given the state space of an average object, writing tests is essentially playing hit and miss. He has found [design by contract][design-by-contract] to be more effective, essentially because it reduces the codebase to only production code and, thereby, the probability of bugs (which may also occur in test code). The discussion ends without further exploration of the matter.

> I absolutely, 100% agree with Bob that shipping untested code is unprofessional. However, "tested" doesn't imply a unit test. Just a test. Even a manual one. I preach this to students regularly: "Do what's reasonable to ensure you deliver. That's the essence of agile." Sounds dead simple, but I still regularly go rampage, because students send me code that they obviously didn't execute even once. It seems to me that a time of rigorously following TDD reduce the chances of such idiocy, but that's merely anecdotal evidence. I digress...
>
> Not testing is unprofessional, because you leave others to deal with the mess that you caused. Be it the users of your product or the poor PhD student 3 years down the road, who desperately tries to reproduce your experiment. The idea of having a test (in mind) first certainly helps, but executing it before you ship is the crucial part. Whether this test is a unit test, a manual test, an integration test, or a contract validation... I don't care.

***

[My tweet of this article](https://twitter.com/svamann/status/827993698684305409) caused quite some discussion. Today, Uncle Bob posted [this excellent response](http://ht.ly/xLna309yR8b) on the matter.

  [dawn-of-tdd]: {{ site.baseurl }}{% post_url 2017-01-27-a-little-history-of-tdd---dawn-of-tdd %}
  [cope-ubob]: https://www.infoq.com/interviews/coplien-martin-tdd
  [xp-explained]: https://books.google.de/books?id=-DNcBAAAQBAJ
  [ubob-tdd-lduf]: https://web.archive.org/web/20110713062831/http://blog.objectmentor.com/articles/2009/04/25/the-scatology-of-agile-architecture
  [design-by-contract]: https://en.wikipedia.org/wiki/Design_by_contract
  [mubench]: https://github.com/stg-tud/MUBench
