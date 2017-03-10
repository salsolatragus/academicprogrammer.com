---
title: Academics Code Only Prototypes
categories:
  - Quality
  - Project Management

---

> "Academic code is like startup code, only we don't claim its production ready." ~A speaker at the 33C3

I claim there's no conceptual difference between software development in academic research and software development in industry. However, there certainly is a difference between software products developed in academia and products developed in industry. Why? Well, because they serve different goals. 

The goal of an industry product usually is to serve someone other than the respective developers in his or her everyday work. When I'm downloading software to work with, I have several implicit expectations. For example, I expect the product to run stable, regardless of the specific system I'm running it on. I expect a decent user interface and intuitive workflows. In other words, I expect the product to fullfil its tasks without getting in my way and without failing me.

For the developer of such a product this has several implications. For example, they need to support multiple platforms, various data formats, and to consider possible error scenarios, such as lack of disk space, no network connection, or a system crash, to name only a few. They also need to think about alternative workflows, since some users might prefer using the mouse while others prefer keyboard shortcuts. From an industry perspective, these are hard requirements, because otherwise the products fail to sell.

Software products from academia usually do not meet such requirements, because they don't need to. They are prototypes, meant to demonstrate the feasibility of some concept. It is sufficient for them to accept one input format and produce one output format. They may make assumptions about resources, such as network or disk space, and simply fail when these are not met, because dataloss is often not critical. And they need to support the workflow of nobody but the (commonly small) group of researchers developing it. Since these people are both developers and expert users, there is no necessity for commonly intuitive user interfaces or workflows. From an academic perspective, all these things are not required for the product to fullfil its purpose.[^lean]

Unfortunately, both academia and industry use similar terminology, such as "tool," to talk about their quite different concepts of a software product. This becomes problematic, if one is unaware of the difference. Something I got reminded of only recently, when we met with Charlie about a potential collaboration with his company.

From a previous meeting we already knew that Charlie wanted to *research* *tools* to assist his developers in finding mistakes in their source code. Some detector similar to FindBugs, from a user perspective, but tailored to their codebase through the powers of machine learning.

We had also already told Charlie about our prior *research* in the area of machine learning for bug detection, so he knew what to expect from us. In theory, that is. In practice, however, we discovered a major discrepancy between what we thought we've told him and what he though we'd told him. But I'm getting ahead of myself.

I'm currently devising an API-misuse detector. Conceptually, this detector learns about the correct usage of APIs from examples and then reports divergences from such usage as potential mistakes. We're still struggling with some conceptual problems, but are generally making progress. To benchmark the concept in some experiments, I've implemented it. And I've compared my detector with several other detectors from previous research in these experiments. That's what I'd told Charlie.

Speaking from my academic context, it was clear to me that the *tools* I was referring to are *research prototypes*. Since Charlie said he wanted to *research* such *tools*, this seemed a well enough fit. However, to Charlie, *researching* meant trying out and comparing a number of existing tools and then given the best or maybe a combination of the best of these tools to his developers for everyday use. What he heard me saying is that I'd, basically, already did the work and all that's left to do is pick the cherry. A matter of weeks, at worst.

Charlies euphoria collapsed, when I sent him my tool for a test run. First, we ran into several technical problems trying to run my tooling on his machine.[^docker] Then, his test projects were too small for my detector to find anything, so I had to add support for it to work on multiple projects simultaneously. And then, when we finally got results, he struggled interpreting the output and told me, desperately, that he cannot possibly hand this tool to his developers. He'd already announced to present the tool the week after.

Needless to say that, at this point, our cooperation crash landed.

Looking back, this story feels like a text-book example of how not to [manage expectations][exp-mngnt]. It all started, because we were using the same terminology to talk about quite different things and failed to clarify this. It was amplified by Charlie selling the bear's skin before we had killed the beast and by him not bringing this up with us beforehand. Be aware of who you talk to. We're all living in our filter bubbles.

  [^lean]: Interestingly, by not adding these extra features, academics follow the lean principle of [eliminating waste](https://en.wikipedia.org/wiki/Lean_software_development#Eliminate_waste).
  [^docker]: Turns out, running Docker on Ubuntu in a VM on Windows is not a good idea. And here I'd thought that, by moving to Docker, I had left platform incompatibilities behind...
  [exp-mngnt]: https://books.google.de/books?id=6VMUAAAAQBAJ
