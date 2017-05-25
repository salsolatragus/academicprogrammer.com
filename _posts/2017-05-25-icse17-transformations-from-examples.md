---
title: Learning Syntactic Program Transformations from Examples
categories:
  - ICSE17

---

Reudismam Rolim observes that many edits are performed repeatedly, for example, when applying corresponding fixes to multiple locations. Such edits can be generalized to AST transformation, much like many developer-assistance tools use them to provide automated refactorings. However, in these cases the transformations are predefined manually. Therefore, Reudismam wants to automatically learning such transformations from change examples. He presents his prototype Refazer.

Refazer builds on a new domain-specific language for the specification of transformations (someone from the audience noted that there are many existing languages to express model transformation, which could be reused instead). It uses a domain-specific deductive algorithm to synthesize tranformations in the DSL from change examples and ranks them, by favoring transformations that reuse more existing AST nodes, transformations that consider the context of the transformed nodes, and smaller transformations.

The authors evaluated the approach in two case studies:

In the first study, they applied Refrazer to a set of real-world projects to learn reoccurring changes. They submitted the proposed changes as change requests to developers and found that the tool proposed a high rate of valid transformation. On average, Refrazer needed 2.9 examples to learn a transformation. This shows that the tool can be used to ensure intra-project consistency.

In the second case study, they applied the approach to suggest fix transformations for buggy student-assignments submissions. They select assignment with several correct and at least one broken submission. The transformations learned from the correct submission helped to fix the incorrect assignments in 87% of the cases. Furthermore, Refrazer successfully fixes the student submissions significantly faster than the students themselves are able to, i.e., in fewer corrective iterations.

---

* Read [the paper preprint](https://github.com/gustavoasoares/website/blob/master/data/icse2017_preprint.pdf)
