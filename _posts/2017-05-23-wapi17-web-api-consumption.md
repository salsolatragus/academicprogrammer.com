---
title: "Opportunities in Software Engineering Research for Web API Consumption"
categories:
  - ICSE17
  - WAPI17
excerpt: Web APIs are a sibling of traditional APIs, but their exact relation remains unclear. Erik Wittern gives an introduction into the problems of current Web APIs and presents an integration of IBM's API Harmony into Atom.

---

{% include image.html img="/assets/images/2017-05-23-wapi17-web-api-consumption.png" title="Erik Wittern on the Challenges and Opportunities in Using Web APIs" %}

Web APIs _are_ ubiquitous and of utmost importance to industry, says Erik Wittern, thereby underlining [Brad Myers' words earlier today][brad]. The growth in the number of APIs of the past 20 years is enormous. These APIs focus a lot on similicity and flexibility.

Erik observes that the consumption of Web APIs is very challenging, because they are basically string-based interfaces without any means of checking, such as a type system. Additionally, Web APIs change at tremendous speed, up to multiple times per day, as is the case for Twitters API. This is underlines by the existence of web services that focus on identifying changes of APIs. Another problem with Web APIs is that they are controlled by a 3rd-party and, as a result, the quality of service (QoS) may vary for consumers and end users, depending on their geolocation.

Erik observes a large gap between the activity in industry vs. the activity of researchers in this field.

Industry proposed a set of formats for the specifications of Web APIs though machine-readable API contracts, which describe information like the APIs base URL, available endpoints, required and optional parameters and data returned by the API, and additional constraints, such as headers, authentication, rate limits, etc.. In his work, Erik aims to provide static verification of Web API Requests against existing specifications. To this end, he extracts properties from the API call and automatically matches it against existing API specifications. Then he detects mismatches between the specification and the call, to assist developer in correcting their API calls. He demonstrates his research prototype, an Atom integration of API Harmony, in a short video:

<iframe width="560" height="315" src="https://www.youtube.com/embed/8IJKs7rMjJI" frameborder="0" allowfullscreen></iframe>

Some of the open challenges include, but are not limited to

* ensuring that API speicfications are up to date,
* inferring specification, e.g., from available text documentation, and
* learning how actual API usage might deviate from the intended usage/specification.

---

* [Paper preprint](https://arxiv.org/abs/1705.06586)

  [brad]: {{ site.baseurl }}{% post_url 2017-05-23-wapi17-keynote %}
