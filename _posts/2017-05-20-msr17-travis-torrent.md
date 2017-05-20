---
title: Travis Torrent Mining Challenge
categories:
  - MSR17
  - ICSE17

---

[Travis](https://travis-ci.org/) is a free-of-charge continuous integration service tightly integrated with GitHub. [Travis Torrent](https://travistorrent.testroots.org/) is a dataset containing build data about 1.200 Java and Ruby projects with ~2.6 million builds. The dataset contains general metadata about the project and, for each build, the previous build, the commit(s) included in the build, the build result, details about the individual build tasks, and whether tests ran, failed, or where skipped.

In the [MSR Data Challenge](http://2017.msrconf.org/#/challenge) participants used the Travis Torrent dataset (in addition to other data sources of their choice) to answer a broad variety of research questions. Out of the 31 submissions, a total of 14 were accepted for publication and presentation at MSR'17. Here's a summary of all of these 14:

The first callenge paper investigated the differences between unit and integration testing. This work is motivated by the shift from traditional software development processes, where integration testing usually follow at a later state than unit testings, to agile models, where this no longer holds. The dataset statistics show that the vast majority of tests are unit tests. The analysis indicates that these tests find more defects, but also that it takes usually longer time and more coordination to fix them.

The second paper aims to predict build outcome using cascaded classifiers, to save costs. The underlying assumption that CI builds are costly, i.e., we should try to reduce the number of builds by predicting build results. They observe, that failing builds are more informative than successful builds, since they are considerably less frequent and identify a problem. Therefore, they try to predict successful builds with high precision, in order to skip the actual execution of those. The discussion of the findings was skipped, because the presenter ran out of time.

The third paper discusses the effect of emotions and the success of CI builds. The idea is that the emotions of developers making the commits that trigger the build may impact the build outcome. To this end, the authors correlated the sentiments identified in the commit messages with the build outcome. They identify a vicious circle: Negative feelings significantly correlate with build failures (though with a small effect size).

The fourth paper looks at the number of builds per day, to see whether there are patterns in the distribution of CI builds. Over all projects, they found multiple periodic peaks in the number of builds per day, e.g., every 7 days. They also identified a monthly periodicity in the Apache Drill project and differences that imply that the maturity of projects, i.e., the project lifecycle phase, impacts the number of builds per day. They could predict the number of daily builds with a 68% accuracy 3 months in advance, which could be interesting for resource acquisition.

The fifth paper finds that the complexity of a task (measured by code churn and number of changed files) is significantly correlated to the build result with small-to-medium effect size. Furthermore, they find that the build tool significantly correlates with build success. Projects using Gradle or Ruby seem more likely to have successful builds than projects using Maven or Ant. Projects using any other type of build configuration are the least likely to have successful builds. On the other hand, using Pull Requests versus using push-based contribution, as well as team and projects size don't seem to have a significant impact.

The sixth paper looks at the dimensions of personell costs. They classified contributors as either build architects (people changing the build configuration) or regular programmers. They find that the number of build architects is mostly constant over time and bounded by 20, regardless of the overall team size. This leads them to the conclusion that CI becomes more beneficial with an increasing team size.

The seventh paper found that many contributors only contribute very little to Open Source projects (casual contributors). They argue that this might be due to high entry barriers for newcomers. As one factor that might impact this, they investigate whether casual contributors more often cause build failures. They find that such contributors create smaller changes (in terms of modified code lines and number of changed files), but in general they don't directly cause more failing builds. However, projects with casual contributors generally have more builds failures than other projects.

The eighth paper looked at the relation between non-function requirements and build results. They identify topics from commit messages and, thereby, classify commits as contributing to one of reliability, efficiency, usability, portability, maintainability, or functionality. They find that there's relatively many commits related to efficiency and usability. Further, they identify that efficiency-change-related build failures in Ruby projects take relatively long to get fixed, while for Java projects it's reliability-change-related build failures that take relatively long to get fixed.

The ninth paper analyzed the impact of social attributes on commit integration success. They extracted a set of technical attributes of every commit and, in addition, determined for the committers who triggered the build the repos he contributed to, his GitHub stars, followers, and following, and the number of contributions in the last year. They find that including these social factor increases the prediction quality for build success/failure by 12%. Especially, developers with more followers have a higher chance of triggering a successful build.

The tenth paper looked at build duration. Due to acoustical disturbances I was unable to follow this presentation, I'm more than happy to add a description, if it should happen to find its way to me.

The eleventh paper investigated whether the adoption of CI impacts the attraction and retention of contributors to Open Source projects. They identified projects with both a pre-CI period and a post-CI period and compared for both periods how the contributor attraction and retention developed. They found that adoption of CI leads to significant-but-small reduction in both contributor attraction and retention.

The twelfth paper also investigated whether software development practices, such as CI, attract new contributors to projects. They clustered project by popularity and investigated whether projects in the same cluster have similar properties with respect to the employed processes. They identified different properties of the groups, such as projects with high tests focus and projects with much experimentation (leading to many failing tests).

The thirteenth paper investigated on the relation between code reviews (Pull Request reviews) and CI. They find that a successful build outcome is more likely to trigger code review activity.

The fourteenth paper investigated how merge conflicts impact CI. They found that non-merge commits are more likely to co-occur with a build failure. A possible explanation for this might be that a merge-commit-triggered build has two predecessors that have already been successfully built and, thus, failures only happen in case of incompatible changes. In most cases the effort to fix builds after a merge-commit is very low in terms of number of changed lines (less than 10 lines) and the time (next build on the same day) required to fix the build. These changes are normally changes in source files.
