---
title: "Type Checking for Reliable APIs"
categories:
  - ICSE17
  - WAPI17

---

Maria Kechagia presented her work on improving the usability of APIs via type checking. Her idea is that compiler should take into account statically available information about parameters. For example, when passing a string value to create a new `URL` object in Java, the compiler forces us to handle the `MalformedURLException`. If, however, the string value is know statically, we might not actually need to handle the exception, hence, the compiler could relax its constraint under this condition.

Conversely, Java's `Pattern.compile()` method declares that it might throw a `PatternSyntaxException`, which is an unchecked exception, i.e., it doesn't need to be handled. If the pattern depends on user input, however, it might make sense to force developers to handle invalid input. The type system currently doesn't enforce this, though.

Maria proposes an extension to Java's type system that let's developers declare values as either `@Loose` or `@Wellformed` using annotations. The type system then automatically switches between checked and unchecked exceptions, accordingly.

---

* [Paper preprint](https://istlab.dmst.aueb.gr/~mkehagia/type_checking.pdf)
