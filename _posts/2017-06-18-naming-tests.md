---
title: Naming Tests
categories:
  - Quality
  - Testing

---

Recently, I received an email from a former student assistant of mine, who observed that I name tests different today, compared to when we were working together some years ago. He was curious to learn what guidelines I'm following now and what led me to them. Let me try to recap.

## Test Classes

I don't remember quite distinctly, but I assume that when I first started to write tests, I named tests quite arbitrarily, in the sense that I didn't follow any particular naming scheme. After I'd worked on my first larger test suites, however, I realized that this makes it difficult to find tests, which led to test duplication and confusion on my part. I started to look for more structure. Structuring of tests, which is closely related to naming, happens on multiple levels. Let's start by looking at what I consider the most-obvious one: *test classes*.[^class]

It is a wide-spread convention to create one test class `XTest` (or `TestX` in some languages) per production code class `X`. This obviously makes it easy to discover the tests corresponding to any particular class. Also, this approach is supported by development tools, such as the Eclipse plugin MoreUnit or IntelliJ IDEA, which makes creating/accessing a test/production class from the respective other straightforward. Therefore, I follow this convention for the most part. 

## Test Methods
 
Sometimes, I find that a particular test class grows too large for my taste. I cannot name any specific threshold for this, but rather trust my intuition and my dislike for scrolling around. I find that this is often a sign that my production class is having multiple responsibilities, but there's also cases where the responsibility just has many corner cases I want to test. In either case, my immediate reaction is to split up the test class into multiple classes and to let this process guide my decision whether to split up the production class, too, or not. To figure out where to split a large test class, I use naming on the next-lower level: *test methods*. 
 
I think the first naming convention for test methods I encountered was naming them like `shouldDoFoo[WhenBar]`.[^testprefix] I like the idea of this convention, as it nudges us to think about tests as expectations, such as "`X` should do foo [when bar]," and to formulate their names in a uniform way. Therefore, I followed this quite strictly for a while.

Eventually, I realized that the prefix `should` does not carry information other than saying that this is a test, which is usually redundant.[^testprefix] Therefore,  I started to drop `should` and to name tests expressing my expectations in plain present tense, like in "`X` does foo [when bar]." This follows the same idea as before, but makes names a little shorter. Similarly, I no longer strictly use the `when` to signal the beginning of preconditions. 

## Splitting Test Classes

Coming back to splitting test classes, I first try to group test method by common name prefixes. This often leads me to groups of cohesive functionality, such as "`X` finds product by id" and "`X` finds product by name," which are candidates for extraction into separate test classes.

I find that when I discover a group of tests that start with a different verb than the other tests, this often leads me to extract the corresponding functionality into a dedicated production class, too, because a different kind of action often corresponds to a different responsibility.

On the other hand, when I find that all my tests use the same verb (or merely one verb and its negation, e.g., "finds" and "misses"), I usually have a case of cohesive functionality with many corner cases, in which case I split the test class, but leave the production class as one. As a guide for splitting the tests in this case, I group the tests by setup/fixture, which is often reflected in the tests' name suffixes, as in "`X` fails to find foo in empty database" vs. "`X` finds foo in database with multiple foos." For each such group, I create a test class named like `XLookupInEmptyDatabaseTest`.  This has worked for me so far, but I didn't yet take it all too far, so there may be problems I'm missing here. 

## Higher-level Tests

So far, I had mostly low-level unit tests in mind. When it comes to higher-level tests,[^hltests] there's some differences to consider. For example, instead of naming these tests after a particular production class, I try to name them after the use case they cover, such as a `SellSingleItemTest` for a point-of-sale system. This approach usually leads me to cohesive test bundles, where each individual test covers one scenario, such as *successful sale*, *cancelled sale*, or *unknown item sale*.

Since I generally have much fewer of these tests, I have less need for structure and are more liberal with my naming. I focus on expressing the business case in the names, so that future me (or somebody else) understands why the system needs to pass a particular test.

## Further Considerations

There's also test-specific naming going on inside test methods. For example, xUnit speaks of the three test stages: setup, exercising, and validation. Accordingly, the naming scheme `given`/`when`/`then` has been proposed as prefixes for helper methods used in the respective parts of tests. I generally like this idea for similar reasons as the `should` convention for test names. However, I found that it is difficult to follow, at least in some languages, because much of the vocabulary is mandated by the respective testing framework, such as `assertX` in many unit testing frameworks or `verify` in mocking libraries. Especially when using multiple libraries, consistency goes down the river. Nevertheless, I find this framework useful for thinking about test elements. 

Finally, there's also some naming to do on the level of namespaces/packages. Here I mostly follow the convention to use the same package names for test code as for production code and place component tests on the highest level containing production code for the component. 

## Conclusion

I use test names as a means to give structure to test code, such that it becomes easier to find tests and, thereby, to ensure that all cases are covered (exactly once). The most important factor here is that following a convention helps me to get my thinking straight. 

What are your experiences with structuring tests? What, if any, conventions do you follow and why? Where do you see problems and benefits? Where do you agree or disagree with me? And, most importantly, where do you think I'm missing somethings? I'm curious to hear what you e got to say!

  [^class]: I'm mainly thinking about object-oriented languages here, because that's were I'm most at home. Still, I apply much of my thinking here also when working with procedural or functional languages, and didn't find this to be problematic, yet. 
  [^testprefix]: Many testing frameworks mandate naming conventions, such as prefixing test methods with `test_` or annotating them with `@Test`. I don't consider this part of the name, as it's simply a technical necessity.
  [^hltests]: Note that these might still be unit tests. I find that these additional thoughts often already apply when I start mocking other components that the unit under test relies on. For actual integration tests I apply the same principles, but name classes with a suffix, such as `IntegrationTest`, mostly because I sometimes want to separate such tests, e.g., by pattern matching on class names in a build configuration. 
