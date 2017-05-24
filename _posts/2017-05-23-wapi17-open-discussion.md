---
title: WAPI Open Discussion
categories:
  - ICSE17
  - WAPI17

---

We concluded the workshop with on open discussion about the different challenges we see and possible next steps for researchers to work on. I tried to capture the different thoughts as best as I could, but there was much more going on than I could possibly write down in realtime.

## Getting Feedback

As opposed to Google, not everyone has "a global view on the world", in the sense that API client code is often unknown to API Designers. This poses the question how to apply [the principles that Hyrum presented earlier today][hyrum]. Hyrum suggests to solve this problem by establishing protocols for feedback. What these protocols remains an open challenge for researchers to address.

Hyrum states that in his view, there's no globally true receipt for designing a good API. The best methodology he has seen so far is for developers to write their tests first, as if they where clients to the API. If something is terrible in the tests, it's very likely to be terrible for other API Users as well.

## Level of Abstraction

A question that impacts many of the API-related topics is how to measure the quality of an API. The most-common metric seems popularity or frequency, but it is obvious that this is not generally a good proxy. Alternative ways might be to capture API interactions in IDEs or to build  effort models for ideal/expert programmers, as a proxy for measuring how much effort it is to solve a certain task with a certain API.

Such a model might bias evaluation towards APIs that just provide high-level components that are very specific to certain tasks. It is debatable whether this is the right way to go, however, recent studies have shown that developers would like to have this, for example, for cryptographic APIs. Such wrapper APIs are more-high-level wrapper APIs around other APIs, which is essentially what most programmers are writing anyways in their respective projects. The question then becomes who should be writing this wrapper to maximize benefit and how API Designers can get feedback about common use cases to be able to build such a wrapper.

Especially in a security related context, ease of use (high-level abstractions) may be a tradeoff to the desired outcome, i.e., security in this case. The challenge is to decide how many details need to be controllable in order to achieve the desired properties and how many/which aspects can be addressed once and hidden behind an API, such that developers don't need to take care of them and cannot accidentally break them.

## Web/Cloud APIs

We ask ourselves how different Web APIs (and Cloud APIs) are from traditional language APIs. It seems like the major problem of Web APIs is known from traditional APIs: when we have primitive-type parameters (such as arbitrary character sequences) to provide a generic interface or because we cannot conveniently define a value with a more precise type (e.g., URL as string instead of an object) we run into problems, because we give up static validation. This relates to the general tradeoff between strongly-typed and dynamically-typed languages.

Current Web APIs have an enormous diversity in how they are designed, which is essentially because there is often not one correct way to do it. There's tons of articles and even books about how to do it, many of which even contradict each other, because there's tradeoffs (and of course also strong opinions).

## Consistency

We observe a similarity between API design and code formatting. Code formatting allows much variety, and there's plenty of disagreement about how to do it. There's probably a small set of things in formatting that are agreed upon by everybody and a large number of things on top that could be done in various different ways. Over time, many conventions were established and companies usually have strict style guidelines that are enforced by tools. We wonder whether a similar trend might eventually emerge for API design. The key insight is that it is not so much about doing it *correctly*, as it is about doing it *consistently*.

An approach could be to compile a possibly small set of commonly-accepted guidelines---for example, from the greatest common divisor of existing guideline sets---and implement a checker that provides API designers with feedback about their adherence to these rules.

## Identify Correct Usage

Another open challenge is the mining/classification of correct/incorrect usages. Again, frequency of equal usage is commonly used as a proxy for correctness, but recent work has shown that this does not generally hold. For example, in the context of Java Cryptography APIs the majority seems to be doing it wrong. We feel that there is probably a need to get experts into the loop, because from examples we'll always have incomplete information.

Something we could do is compare client usages to test case usages. When client usages diverge from test usages, they are either misuses or a novel way to use the API (which should be tested). Passing feedback about such usages to the API Designers (experts) could validate which of the two is the case. To solve the problem of deciding whether a test demonstrates a normal flow or an error case, one should consider also the API-implementation code.

## Tooling

We find that across all the problems we identified, probably the lack of tooling is the most frequently reoccurring problem. To advance the state-of-the-art, we need not only tooling for API Users, to assist them in using APIs efficiently and correctly, but also tooling for API Designers, to assist them with building good APIs. The latter most-likely requires to find a set of guidelines.

  [hyrum]: {{ site.baseurl }}{% post_url 2017-05-23-wapi-api-evolution-and-migration-at-google %}
