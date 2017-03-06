---
title: Adam and the Tests
categories:
  - Quality
  - Testing

---

A strong set of tests gives me confidence that the tools I devise do what I want them to do and that my experiments test what I intend them to test. This is crucial to my research. If I wouldn't have this confidence, how could I publish the results of my experiments, claiming that I found a better solution to the problem I'm working on?

Sadly, in my experience, other researchers put less effort in ensuring that their code works correctly. While this statement is merely based on anecdotal evidence and might not at all generalize, I think that the cases I've encountered are not singularities and that there are some lessons to learn here.

Only about a year ago, I asked a fellow researcher, let's call him Adam, for the implementation that he had used in the experiments for a previous publication. Adam was happy to help, and over the next months I received various emails with different ZIPs, each containing a different version of his tool, which he had found on an old machine or in some backup folder. It took me minutes to realize that none of these versions had even a single test or had ever run on a different machine than his, because they had machine-local paths hardcoded all over them. It took me at least a month to understand that none of the versions was the one he had used in the aforementioned experiment.

At first, I was very annoyed. Adam's prototypes brutally violated what I consider general research ethics:  ensure your experiments are correct, reproducible, and replicable. However, as Adam was quite willing to help and an expert in the area of research I was only just entering, I agreed to a cooperation.

I soon started adding code to our project, including tests. These focused mainly on the new stuff I added, but I also wrote exploratory tests for the old codebase, to document my assumptions about it. Regularly, after Adam had done a change, these tests would fail. Starting to be annoyed again, I negotiated that we set up an automated build that runs the tests and notifies us when they fail. Interestingly, I found him rather enthusiastic about the idea and thanking me for configuring it.

Unfortunately, the build job didn't make him write any tests. Nor did it make him care about test failures for long. Initially, he fixed the tests he broke. Though mostly by making my test assertions conditional, which was bad. A little later he just stopped fixing them again, which is worse.

I didn't get to talk to him about it yet. However, his very actions give me reason to pause. I believe that he acts with good intentions, even if he's acting against what I believe to be a sensible procedure.[^intent] The question is: why?

  [^intent]: Even though it is easy to be annoyed when people act against ones own values---as I've already proven twice in this story---, I believe that people usually do things, because they are convinced that these are the right things to do or that they have no (sensible) other choice. And not because they want to do harm.

## Activation Energy

Adam definitely didn't spend as much time on developer testing---or software engineering practices in general---as I did. After all, he's a software-engineering researcher, not a software developer. And, as far as I know, he never intended to become one, either.

Judging from his initial enthusiasm and his, seemingly contradictory, actions, it could be that he heard over and over again that he should be testing, but never came around to actually test. It takes time and requires investment for testing to pay of. [I've been there, too][how-I-came-to-test].

It is difficult to make this investment, while under pressure to deliver features. Interestingly, "we've got no time for testing" is exactly what I got taught is a typical cheap excuse of industrial software developers. Of course, in academia that's a completely different story, right? &lt;/irony&gt;

If this is indeed the cause for Adam's actions, then there is, unfortunately, nothing much I can do about it. Since we're not directly working together, I can hardly influence or assist him. I can only continue to do the testing on my part and hope that, over time, he will pick up on it. 

  [how-I-came-to-test]: {{ site.baseurl }}{% post_url 2017-02-19-how-I-came-to-test %}

## Maintenance Cost

There is another potential cause for our situation:

*I might be overdoing it.*

I usually write quite a number of tests, so maybe they incur too much of a maintenance cost on Adam. This would likely amplify a feeling that tests are not worth the effort, lowering the motivation to try them in the first place.

The nice thing about this possibility is that I can actively do something about it. I can try to [reduce the tests to just those that have an immediate "business" value][cope-waste]. This would reduce the maintenance cost and increase the value of each individual test. Therefore, it would provide *evidence for the value of testing*. 

  [cope-waste]: {{ site.baseurl }}{% post_url 2017-02-10-a-little-history-of-tdd---unit-test-waste %}

## Conclusion

In summary, testing is not a common practice in academia, as far as my experience goes. Reasons for this are that researchers lack practice in testing, which makes it less efficient; that researchers don't feel like testing is something that they need to be bothered with, because their not building industrial-strength software; and that people like myself, who demand testing also for research prototypes, don't try hard enough to make this feasible for our colleagues.

*Change always starts with oneself.*
