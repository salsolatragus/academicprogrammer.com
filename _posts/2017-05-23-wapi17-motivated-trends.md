---
title: "Mining Motivated Trends of Usage of Haskell Libraries"
categories:
  - ICSE17
  - WAPI17
excerpt: Anand Ashok Sawant presents a preliminary study about why developers migrate between API versions.

---

Anand Ashok Sawant presented the work of his four students Marc Juchli, Lars Krombeen, Shashank, and Chak Shun Yu, who aim to mine reasons for why developers migrate between API versions (i.e., dependency versions). They mined Hackage, the Haskell library repository, to analyze usage trends for libraries.

The data shows that some versions of APIs are adopted immediately with their release, which indicates that they might have been well advertised. Also, there are a bunch of versions that remain basically untouched by clients. It seems that popularity of an API version depends on the early adopters and that popular versions usually become very popular.

Another insight came from looking at the commit messages of the changes in each version, which they classified as corrective (fixing problems), adaptive (adding features), or perfective (increase performance, maintainability, or style). Additionally, they classified them as either addition (entirely new or updated dependency) or deletion (removed or downgraded dependency). They found that most additions and deletions where adaptive and only very few were corrective. This indicates that dependency upgrades happen mainly to enable new functionality, and rarely to improve or fix existing functionality.

---

* [Paper preprint](https://w-api.github.io/resources/api-haskell-main.pdf)
