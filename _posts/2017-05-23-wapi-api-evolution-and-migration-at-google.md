---
title: "API Evolution and Migration at Google"
categories:
  - ICSE17
  - WAPI17
excerpt: Hyrum Wright reports on how Google evolves its APIs and manages the migration of its entire codebase to new API versions. He discusses various tradeoffs and open challenges for research.

---

{% include image.html img="/assets/images/2017-05-23-wapi-api-evolution-and-migration-at-google.png" title="Hyrum Wright talking about API evolution and migration at Google" %}

Hyrum Wright (Google) brings the industry perspective into WAPI. As one of the world's major software companies, Google deals with an enormous code base, maintained by 30k developers distributed across more than 40 sites globally, committing approximately 30k changes per day to a single monolithic repository, which leads to 150M daily test runs.

Google faces the challenge of keeping up with the internal changes to their APIs, as well as the changes triggered by external sources. It is in Googles interest to keep up with the most up-to-date version of APIs, in order to make it easy for developers to join a project (no learning of outdated APIs) and to avoid "haunted graveyards", i.e., parts of their source code that developers are afraid to touch. Also a consistent view state of things allos to fix bugs at scale, throughout the entire codebase, and to move/rename parts of the system without managing migration over time. Thereby, they follow the idea to "value recovering from failure (changing decisions later) over trying to do everything right."

API migration at Google is performed by teams of experts. The main workload lies with the team that developed the (old) API. Unfortunately, the teams whose (client) code is updated have little incentive to help and even sometimes resist change. Nevertheless, the process works reasonably well and, mostly, works out fine. The general idea is to first create new API, then to migrate clients, and finally to delete to old API.

**Hyrum's Law**: Every system has an explicit interface, i.e., the API you publish. Every system also has an implicit interface, i.e., the expectations users have based on the behavior of the system. Given sufficiently many users, some user will depend on every single aspect of the implementation of the API. Consequently, the implementation of the API becomes the implicit API. As a corollary, every change is gona change somebody's workflow. For example, inserting a comment once broke the tests of an API's client, who was relying on log messages issued by the API's implementation. These log messages contained line numbers, which changed due to the inserted comment.

You can prevent people from depending on an API's internal interface, by "randomizing" the implementation. For example, to ensure your code adheres to a language specification you could compile it with multiple compiler implementations. Or to ensure that nobody depends on the iteration order of a map, you could intentionally randomize it. Anticipating the things people might rely on is difficult, however.

Evolving APIs can generally be approach in different ways:

The **Greenfield Approach** means the API is written from scratch, to eventually replace the old one. Unfortunately, this often causes over-engineered solutions (as people try to build the perfect API this time) and migration mostly cannot happen until the reimplementation is complete. Consequently, migration to a new implementation is expensive and client might not do it. For example, Google's `proto-1` was released in 2000 and `proto-2` in 2008. Migration is *almost* done today. Lessons learned from this situation are

* that they spend too much time migrating dead code (which resulted in Hyrum's coefficient, following the observation that files only touched by Hyrum's migration changes over an extended period of time weren't used any longer),
* that there was too-little tools to manage API deprecation and migration, and
* that clear code ownership is required for effective migration.

> "It takes more effort almost by an order of magnitude to kill an old system than it did to write it." ~Hyrum

The **Incremental Approach** means the API evolves in-place. The idea is to make changes evolutionary, not revolutionary. On the upside, clients can recognize incremental benefits and migrate over time, with less cumulated effort. On the downside, you have to drag along tons of legacy code and support legacy users while evolving the API. Also it makes it harder to change certain aspects of the API.

The **Hybrid Approach** is to build the new implementation such that it is compatible with the old one and client may, but don't need to migrate.

In any case, migration is a difficult task. Especially for widely used APIs, where migration might touch a large number of points in the entire codebase. In fact, doing such a migration globally is practically impossible oftentimes, because its bound to create conflicts. Therefore, Google tries to cut down the migration, for example migrating one client at a time.
