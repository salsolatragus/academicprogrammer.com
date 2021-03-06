---
title: Just Use My Testing Infrastructure
categories:
  - Maven
  - Testing
  - Developer Tools

---

I use the Maven dependency ecosystem to provide code dependencies to my students via a Maven repository hosted on my group's artifact page. This gives students access to my code, allows them to conveniently view the corresponding source, allows me to quickly distribute updates, and forces me to more cleanly separate my code.

Since I usually insist on automated tests, I repeatedly find myself with testing infrastructure code that I want to distribute alongsite the respective production code from some module, say `foo`. There's several ways to achieve this:

1. I could simply include the testing code with the production code, such that it would be available from `foo` itself. However, this would force me to turn testing dependencies, such as `hamcrest`, into production dependencies, which I consider a no-go.
2. I could create a second Maven module `foo-test` alongside the production module `foo` and move all the testing code there. This would allow others to depend on `foo-test` in the `test` scope, which resolves the dependency issue. However, since `foo-test` usually depends on `foo` and I cannot (and don't want to) declare cyclic dependencies, I cannot use the testing infrastructure in `foo-test` to write tests in `foo`. Therefore, I have to write the tests for `foo` in `foo-test`, which I find counter-intuitive. Moreover, it breaks code coverage measurement, because this happens module-wise in Maven, such that running the tests in `foo-test` does not add to the coverage of the code in `foo`.
3. I could just use Maven to solve the problem for me. Turns out this is actually quite simple, using the `maven-jar-plugin`. This gives me a clean separation of testing and production dependencies and allows the respective code to reside in the conventional locations, at the same time.

To provide all the test code from `foo` in addition to its production code when I deploy the module, I simply insert the following configuration in the module's `pom.xml`:

{% highlight xml %}
<project>
  ...
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-jar-plugin</artifactId>
        <!-- Change to the version that fits your environment! -->
        <version>3.0.2</version>
        <executions>
          <execution>
            <goals>
              <!-- Deploy test code as a separate artifact. -->
              <goal>test-jar</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      ...
    </plugins>
    ...
  </build>
</project>
{% endhighlight %}

Running `maven package` will now create an artifact called `foo-0.0.1-SNAPSHOT-tests.jar`, which contains all the test code and declares the respective production and test dependencies in its `pom.xml`. This artifact gets deployed alongside the main artifact.

To depend on `foo` and its testing code in another module or project, I insert the following dependency in the respective module's `pom.xml`:

{% highlight xml %}
<project>
  ...
  <dependencies>
    ...
    <dependency>
      <groupId>foo</groupId>
      <artifactId>foo</artifactId>
      <version>0.0.1-SNAPSHOT</version>
    </dependency>
    <dependency>
      <groupId>foo</groupId>
      <artifactId>foo</artifactId>
      <version>0.0.1-SNAPSHOT</version>
      <type>test-jar</type>
      <scope>test</scope>
    </dependency>
    ...
  </dependencies>
  ...
</project>
{% endhighlight %}

Note that I declare two dependencies, one on the production code and one on the test code, each with the respective scope. By setting the dependency `type` to `test-jar`, Maven knows to look for an artifact generated by the `test-jar` goal, as configured above. The default value for `type` is `jar`, which corresponds to the respective module's main artifact (production code).

And that's it. Problem solved.

I try to make it easy for my students to use my code. This includes testing infrastructure. Why should they reinvent the wheel? Like all of us, they are more likely to write tests, the easier it is for them to actually do so. No excuses ;)
