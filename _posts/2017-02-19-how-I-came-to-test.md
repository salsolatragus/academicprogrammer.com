---
title: How I Came to Test
categories:
  - Quality
  - Testing

---

As you might remember, [academics code][academicscode], too. And that's not even only computer scientists: The first of my friends who needed to program in university were physicists. Early on, they had to evaluate the results of their lab experiments, which produced considerable amounts of output. Too much, certainly, for any sane human to process. And since respective software was simply unaffordable, they would go and write their evaluation scripts themselves.

Of course, most of them were self-taught amateurs at the time. They didn't have any courses about programming, testing, design, or even version control. In contrast, only pros pick up computer science. These types who speak fluent assembler and run their laptops on some---preferably self-compiled---distribution of Linux. Those who simply already know how to do software development.

Honestly, these know-it-alls are the worst.

I was like that. I already taught myself programming in school. First, "C in 21 Days." Then, "C++ in 21 Days." Even wrote my own linked list during that one! And then I went over to the cool kids: "Now I learn PHP &amp; MySQL" (in 21 days, of course). Looking back, it amazes me that none of these books even mentions testing...

Luckily, there already was the internet and I had convinced my parents that we absolutely needed ISDN, so I eventually encountered PHPUnit. The idea of automated testing made sense to me. Automating part of that endless trial and error that is PHP programming. Speeds things up. Remembers this (n+1)st use case that I forgot about (again) and that I (of course) broke with my last change. So I wrote tests.

When I enrolled at university, nothing much changed, except that I switched PHP and PHPUnit for Java and JUnit, respectively. It was in my Computer Science 101 class in 2006 that I first encountered Test-driven Development:

{% capture cs101_caption %}
Introduction to TDD from My Computer Science 101 Course in Winter 2006.

{: .text-left }
Reads: "Why should I use JUnit? TDD is a design practice that is *increasingly adopted and rightly recommended*. It requires one to *first write the tests* and the code that must pass them only afterwards. TDD is a core part of XP and is, meanwhile, adopted by most agile approaches. JUnit is well-suited for TDD ... the `@Ignore` annotation is very convenient, since it allows to disable individual tests, while working on the respective implementations."
{% endcapture %}
{% include image.html img="/assets/images/2017-02-17-CS101-TDD.png" title="Computer Science 101 on TDD" caption=cs101_caption %}

To me this meant: "TDD is what the pros do. I am a pro. So I'd better TDD." Being the know-it-all I was, I also presumed to understand TDD from just this short description, which led me to believe that TDD is about JUnit and means writing all tests first and any production code only afterwards. An inverse Waterfall, if you want.

Of course, I also read Kent Beck advocating that test first gives you [faster development, higher code quality, better design, and reduces the amount of waste you produce][kent-tdd]. Martin Fowler promising that TDD gives you [self-testing code and clean interfaces][martin-tdd]. Uncle Bob proclaiming [exhaustive tests suites, close to no debugging, the ability to change code without fear of breaking anything, reduced coupling][bob-tdd], and a sheer infinit number of other benefits. And James Shore throwing [fast feedback][james-tdd] into the race. It was crystal clear to me that TDD was what I had to do, if I wanted my place among the professionals.

Only, I was still not doing it.

While unit testing had already appealed to me in my school days, with PHPUnit, I somehow lost sight of it during my studies. Of course, I wrote a few tests here and there for my class assignments. But, honestly, it never really felt like there was much danger in doing otherwise. The assignments were mostly too small to bother myself with testing and I didn't have to maintain them at all. So why care?

It was only during my Master's, when I took a one-year course called the "Software Engineering Project," that I rediscovered the value of testing. In the course, we developed a product for a real-world customer in a team of six students. Our task was a system that facilitated the exchange of orders and results of blood tests between local doctors and a laboratory.

Our initial incompetence in software quality measures of any kind eventually brought our project to the brink of failure, which made us put some serious thought into quality. In the remaining six month of the project, I actually began to understand a few things, such as the intention behind [Uncle Bob's Three Laws of TDD][bob-tdd], the differences between unit tests, regression tests, and integration tests, and the benefits and problems of software quality meatrics, such as code coverage. Most of all, I came to cherish the comfort of the safety net that an exhaustive test suite provides.

Fast forward, a couple of years into the future. Meanwhile, I finished my studies and signed up for my PhD. The projects I work on are still relatively small and there's only ever a handful of people working on them. But two things have changed dramatically, compared to class assignments:

1. The software I write is either prototypes of the algorithms and approaches I design for my research problem or experiment infrastructure to evaluate whether the former actually work. In other words, the correctness of my code is a direct precondition for the correctness of the results I then try to publish, proclaiming to the whole world that I've done the next big step towards salvation.
2. I develop my software over multiple years and have a serious interest in *not wasting my time in needless debugging or painfull changes*. In other words, I have to keep it maintainable for the sake of my own sanity.

So today, software quality and testing, for me, are *justified by my urge to survive and make progress* alone.

It took me a long time to understand this value and to refine my abilities in order to actually get the benefits from testing that I was, early on, made believe it can give me. And I'm still learning. My work with my colleagues, students, and friends helps me to advance, because I learn from their different styles of programming. Also I was lucky to meet inspiring people, such as [Joe Rainsberger][jbrains], [Uncle Bob][unclebob], and [Cope][coplien].

Now, this is my story. What is yours? Why do you value software quality and what do you do to achieve it? And how did you come to test?

  [academicscode]: {{ site.baseurl }}{% post_url 2017-01-22-extreme-researching %}
  [kent-tdd]: http://www.extremeprogramming.org/rules/testfirst.html
  [martin-tdd]: https://martinfowler.com/bliki/TestDrivenDevelopment.html
  [bob-tdd]: http://butunclebob.com/ArticleS.UncleBob.TheThreeRulesOfTdd
  [james-tdd]: http://www.jamesshore.com/Agile-Book/test_driven_development.html
  [jbrains]: http://jbrains.ca
  [unclebob]: http://cleancoder.com
  [coplien]: http://www.gertrudandcope.com/jimcoplien
