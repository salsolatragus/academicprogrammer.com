---
title: "Research Infrastructure for MSR: Needs, Wants, and Where We Are"
categories:
  - MSR17
  - ICSE17

---

Mining Software Repositories (MSR) is an important research direction in the software engineering area. Today, researchers are exploring not only traditional software repositories (i.e., SVN/Git repositories), all all kinds of data generated in the software projects, e.g., from task-managements systems, issue trackers, email, and social media.

The first session of today started, surprisingly, with an open discussion about *which infrastructure MSR researchers use/need/want for their work*. I think particularly like two aspects of this discussion, which I'm trying to wrap up here:

## Representative Samples

Abram Hindle kicked off the discussion with the observation that research on Open Source softare projects became immensely more efficient, due to [GHTorrent][ghtorrent].[^ghtorrent] This received much agreement.

Aiko Yamashita noted that while much research focuses on GitHub, not all software is in there. There's tons of software, especially older systems (Software Heritage), that is (still) maintained either on other platforms, such as SourceForge, or even in individual repositories. Such software might have distinctive properties that we ignore by focusing on the low-hanging fruit that is GitHub.

Someone countered that today, a really large fraction of state-of-the-art, Open Source projects in maintained on GitHub and also many older projects have been migrated to GitHub as well, which makes it more likely that this dataset is representative for the domain of Open Source projects.

Then someone else stated that the problem of getting a representative dataset is probably no longer to get access to projects' source code, but much more getting a representative dataset of software in a type-resolved, compilable, or even executable state. Infrastructure for these kinds of problems really isn't available.

Indeed we have means to identify projects through metadata (e.g., [GHTorrent][ghtorrent]) and source code (e.g., [BOA][^boa]), but beyond that comes a void. In my experience, the vast majority of projects on GitHub don't even use build-configuration management, such as Maven. And even for those who do, it is stil surprisingly difficult to even compile a project. Sampling for projects that can be automatically compiled (e.g., projects using any kind of Continuous Integration) introduces a huge bias.

## Bugs in Research Prototypes

Another interesting topic that was brought up is the quality of [research prototypes][proto] and infrastructure (in MSR). In what is probably the vast majority of cases (supported by a quick poll among MSR attendees), research prototypes are developed by a single academic with a deadline directly ahead. We have to acknowledge the fact that academic (software engineering) researchers are not (necessarily) professional software engineers and consider the impact this likely has on research results. Two interesting questions arose from this:

1. Why is it so uncommon to openly report when mistakes in research prototypes are discovered?
2. Why don't we employ professional software engineers for the implementation work in research projects?

  [^ghtorrent]: [GHTorrent][ghtorrent] is a data torrent that basically provides an index on GitHub projects to enable efficient searching and filtering of project samples on various project properties, such that researchers can better target their queries to GitHub, avoiding unnecessary traffic and also working around the relatively low service level in terms of the number of queries granted to every single user and their response time.
  [ghtorrent]: http://ghtorrent.org/
  [^boa]: [BOA][boa] is a platform and query language for simple static analyses on GitHub projects, including the (non-type-resolved) AST of Java source files.
  [boa]: http://boa.cs.iastate.edu
  [proto]: {{ site.baseurl }}{% post_url 2017-03-10-academics-code-only-prototypes %}
