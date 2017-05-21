---
title: An Empirical Analysis on the Docker Container Ecosystem on Github
categories:
  - MSR17
  - ICSE17

---

Docker containers power the infrastructure of modern deployments. Docker quickly became a de-facto standard in industry and made lightweight virtualization available to a greater public. On GitHub we find roughly 38k Dockerfiles, i.e., configurations of Docker containers. This raises the question how Docker containers are used.

In their work, Jürgen Cito and Gerald Schermann built a relational model over all Dockerfiles from GitHub. They provide this dataset and tools to extract and compute structural changes, as a basis for research.

Based on this infrastructure, they analyzed which Docker base images are most-frequently used. They find that by far the most prevalent base images are the pure OS images of Ubuntu and Debian. Other frequently used base images are those providing the execution environments for a specific programming language, such as Java or Python.

Interestingly, the images for Ubuntu and Debian are relatively large, compared to alternative OS base images. This incurs a runtime penalty on using the containers, which could be avoided by migrating to a different base image. Also, containers basing on larger base images take longer to build. Thus, there is a large opportunity for performance optimization in the supposedly lightweight Docker infrastructure. Development tools might help to exploit this potential by giving respective recommendations to developers.

The most-frequently used Docker command is RUN. In the vast majority of cases, it is used to declare dependencies. An additional abstraction layer for dependency declaration might help developers to more easily declare dependencies. Somebody from the audience remarked after the talk that there is a discussion about this in the Docker community and that there is a tool called ??? that already provides assistance with dependency management.

From a random sample of 560 Dockerfiles roughly 1/3 did not successfully build a container. The Dockerfiles of these containers show significantly more violations of best practices, such as declaring concrete dependency versions, as reported by [Dockerfile Linter](http://hadolint.lukasmartinelli.ch/). This indicates that such checks should also be integrated in development tools, to assist developers with the definition of correct configurations.

---

* [Paper preprint](https://peerj.com/preprints/2905/)
