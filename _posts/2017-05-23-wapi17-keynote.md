---
title: Human-Centered Methods for Improving API Usability
categories:
  - ICSE17
  - WAPI17

---

API as ubiquitous. For example, [www.programmableweb.com](https://www.programmableweb.com/) lists 17.5k APIs as of today. About 77% of companies rate APIs important too making their systems and data available. The total market for API Web middleware was $5.5 billion in 2014.

Brad Myers starts off [our workshop][wapi] with the observation that APIs have many stakeholders, which he groups as API Designers, API Users (developers), and Product Consumers (endusers). Each such group of stakeholders has different views and different requirements/expectations on APIs. For example, while Product Consumers have a restricted view (they may observe when an API crashes or observe its energy consumption behaviour), most of an API's properties (e.g., learnability or usability) are targeted towards API Users. For them, the main goal of APIs is to allow reuse, i.e., to increase their productivity.

Brad's goal is to allow API usability to be a first-class quality metric considered by API designers, which he perceives is rarely the case today. He looks at human-centered techniques (DevX = Developer eXperience), because APIs are the interface between programmers and functionality and it is really important that these two interface well, in order to avoid, e.g., errors and vulnerabilities.

Human-centered methods are ubiquitous. They can be used throughout the development lifecycle: in exploratory studies, design practices, evaluation studies, and field studies. Many HCI method turn our to work really well for research on APIS. A particular technique Brad puts forward is "Natural Programming" Elicitation. The idea is to hand a blank piece of paper to developer and ask developers to describe what they think the API should be doing in prose and then use their descriptions (terms, concepts, etc.) to design APIs accordingly.

Another dimension of human-centered work is the scale from professional programmers to end-user programmers. Informally, from programmers that want to program to such that have to. There's many more of the latter type, such as Excel users. They all use APIs, but bring different capabilities to the table. Learning APIs is a big barrier for all these programmers. There's a tradeoff between learning and possibilities, i.e., you can learn a high level API to do a few specific things. If you want to do more, you have to dig deeper and learn about more low level details. For example, web development achieved to lower this entry barrier quite substantially, compared to more traditional programming languages, but there's still room for improvement.

A parallel line of Brad's work targets API developers to support them in designing APIs well. An interesting insight from this line of work is that developers actually prefer APIs that allow them to initially create object in invalid states (e.g., objects without all required dependencies set up correctly), just for them to move on. They want the ability to decide later and an API that forces them do decide immediately makes them resort to all kinds of workarounds, such as passing null values. Also, alternative designs like factories take developers 2-5 times longer to figure out.

Interestingly, the number of methods on an API (i.e., on a particular class) doesn't seem to correlate with the perceived complexity of an API. On the contrary, missing a method on a type, seems to significantly set back developers. There's again a tradeoff here, because sometimes you have to decide where to put a method and API Designers might end up putting it somewhere where API Users don't expect it. Putting it at all alternative places creates cyclic dependency, which is not (generally) an acceptable solution.

Interviews with API specialists from multiple big companies revealed that they all have quite different ways to approach API design. Also, considering the number of APIs that are created, problems such as ensuring consistency and documentation is a severe challenge there.

Brad's research produced a variety of tools to assist API Designers, some of which are:

* MICA - a specialized search for API documentation and examples (discontinued, because it was based on the discontinued Google Code Search).
* Jadeite - searches for information about APIs everywhere in the web, in order to enrich JavaDoc with additional data, such as examples.
* Calcite - improves Eclipse's code completion by suggestion Jadeite's usage examples for instantiating objects.
* Dacite - provides Java annotations, such as `@StaticFactory`, which give API Designers the ability to provide information for tools to make better suggestions to API Users.
* EUKLAS - brings Java-like analysis to JavaScript.
* Graphite - provides assistance with APIs that introduce a sublanguage, e.g., when instantiating `RBGColor` you have to pass three `int` values, which the plugin allows you to determine through a color picker to make initialization easier and ensure valid values at the same time.
* Apatite - uses verbs (actions) and properties to find classes that implement them.

Brad concludes his keynote with some open challenges:

* Which design patterns are problematic or beneficial to API usability and why?
* How to coordinate cross-API usage?
* What are best practices for API design, including metrics, processes and their implementation in development teams, and design guidelines?

  [wapi]: {{ site.baseurl }}/posts/categories/wapi17
