---
title: Precise Condition Synthesis for Program Repair
categories:
  - ICSE17

---

In test-based program repair, the problem to solve is to take a program with a test suite and at least one failing test, to generate a match that makes the program pass all tests. A big problem to this approach is that in real-world projects tests suites are often too weak to guarantee correctness. This leads to very low precision of repair tools, such that they are unlikely to be adopted in practice. Therefore, Yingfei Xiong's work aims to increase the precision of repair tools.

Yingfei presents an approach called Accurate Condition Synthesis (ACS). ACS uses two sets of template for repairs:

* *Oracle Returning* templates that conditionally return (or throw) the expected result (as defined by the test), where the condition is the synthesis task.
* *Condition Modification* which either widens or narrows an existing condition by a synthesized predicate.

The challenge is that the space of possible conditions is too large for enumeration. Therefore, they synthesize the conditions together with a probability of it being correct and to stop synthesis when the probability is too low. Therefore, the authors apply divide-and-conquer: They first rank the involved variables and second rank the predicate per variable. This reduces the search space drastically, especially because the number of variables is usually small.

One strategy to rank variables is to order them by their data-dependency order. An alternative method is to prioritize variables that appear in the JavaDoc documentation. To rank predicates they use the variable type, the variable name, and the enclosing method name. To approximate respective probabilities, they query GitHub and consider only predicates that appear frequently enough.

The evaluation on four real-world projects shows that the new approach has a precision of 78.3% in average, which widely outperforms existing approaches (around 20% precision).

---

* Read [the paper preprint](http://sei.pku.edu.cn/~xiongyf04/papers/ICSE17a.pdf).
