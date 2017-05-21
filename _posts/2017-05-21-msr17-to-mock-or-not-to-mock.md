---
title: To Mock or Not To Mock?
categories:
  - MSR17
  - ICSE17

---

Whenever we write a new piece of software, we have to decide whether we want to test it in its reals context and/or in isolation. The latter case is commonly achieve by replacing dependencies by mocks (or [stubs][mocks-vs-stubs]). Among the advantages of mocking are faster and more-stable tests, as well as a less code to analyze for mistakes in case of test failures.

To investigate how developers use mocking, Davide Spadini, Mauricio Aniche, Magiel Bruntink and Alberto Bacchelli from Delft University of Technology analyzed over 2000 projects. They find that developers mostly mock databases, web servies, and external dependencies (in roughly 2/3 of all tests), while Java libraries and test support libraries are rarely (though still sometimes) mocked.

Through interview ans surveys, the authors learned that developers mock mainly when the concrete implementations of the entity that gets mocked away is complex or if the entity has an interface type. Contrarily, they mock less when the testing purpose is integration testing. As major challenges in mocking, developers see tight coupling and legacy code. Moreover, developers report that mocking requires experience and that, therefore, the application of mocking changes over time: While they, early on, tend to just mock anything, they eventually learn to identify beneficial scenarios and, consequently, avoid mocking otherwise.

---

* [Paper preprint](https://pure.tudelft.nl/portal/files/13757227/PID4728641.pdf)

  [mocks-vs-stubs]: https://martinfowler.com/articles/mocksArentStubs.html
