::: title
The State of Mocking Frameworks in Software Testing: A Narrative Review
:::

::: subtitle
Hendra Anggrianto Wijaya (A20529195)<br>
Department of Information Technology and Management<br>
ITMD-536-01: Software Testing and Maintenance<br>
Dr. Nazneen Hashmi<br>
Septempber 30, 2023
:::

## Abstract

::: abstract
The use of mocking technology is prevalent in software testing to separate the
code from its dependencies. However, the concept of object simulation is not
definitive, leaving the door open for own interpretations ensuing in hundreds of
different tools available today. Moreover, there are growing concerns pointing
out that mocking might be detrimental to the project's reliability and
maintainability. To answer the allegation, this paper takes several of the most
popular tools for a literature review which involves how they function, their
comparison against each other, and their impact on software application testing
and development. Beyond theoretical examination, the paper explores the
technology integration in existing projects. The research evaluation is
presented narratively instead of scientifically.
:::

*Keywords*: Software mocking, mocking frameworks, mocking libraries, mocking
tools, unit testing

## Introduction

Software development nowadays is a complex process consisting of different
components balanced by team members. These components are bound to use external
services and partnerships, even more so in this digital era. Think of a food
delivery app that uses a third-payment gateway, an e-commerce website relying on
shipping carriers to deliver products, or a satellite-assisted global
positioning system (GPS) in modern cars. The additional services are
indispensable to the day-to-day operation and are to be considered when
performing a test or making an incremental change to the main code. However,
being off-site parties, they have uncontrollable states and independent behavior
which impair the ability of the development to move forward. When an external
service unexpectedly terminates, it brings down other dependent services running
concurrently, resulting in the failed pass of the software test in question.

The uncertainties of communication standards, instability of hardware uptime,
and other suspicions about foreign actors are where the mocking solution fits
in. A mocking framework creates fake objects &ndash; also known as stubs and
mocks &ndash; that strategically replace the original ones to reduce or
ultimately remove unpredictable dependencies during testing. While the purpose
may seem self-defeating (producing false records), the act of self-isolation
helps the development team focus on the relevant piece of code rather than the
environment beyond their control. Besides, not having to wait for external
feedback like database queries or web services means that unit tests carried out
using mocking technology finish faster than conventional tests. Software
engineers also utilize mocking technology to improve test coverage reports when
a test scenario is too difficult to reproduce in a real-world setting. There are
even several software development methodologies such as test-driven development
(TDD) and behavior-driven development (BDD) which promote writing empty or
faulty unit tests first and functioning main code later (Moe, 2019).

But make no mistake, simulations are still fakes regardless of how well-crafted
they are. Mocks are conceived under the pretense that they resemble real
objects, and behave appropriately, but shall never match the capacity and
variation offered by real-world settings. The system will eventually have to
face an uncertain scenario in which it will be underprepared for having less
exposure, causing the main code to become less resilient. The tests written
using this concept also face the same resilience issue, requiring an update when
a subsequent mock structure considerably changes. Above all, exploiting software
mocking techniques requires the practitioners to invest time to adapt to a
specific framework. Sadly, the expertise that the practitioners may gain during
software development is rarely translatable to other frameworks. All said
factors contributed to the heightening of the project's complexity before the
team could even benefit from a mocking solution.

In this paper, I will attempt to list and compare contemporary software mocking
technologies by their usage type. These components are wildly unidentical to
each other, not least because they may be composed of different programming
languages, but they also try to solve different problems in their scope. As
such, this report is fixated on the mocking practices rather than the result or
convenience they provide. In my opinion, the study of their practices includes
what they do under the hood, what information they regularly emit, and the
likely repercussions of that action. In addition, the paper may also contain
code snippets to conceptualize how certain parts of third-party libraries or
frameworks operate.

## Related Work

Analyses observing mocking practices are by no means rare in any scholarly or
journalistic repositories, though a fair amount of them are not inherently
related to mocking but also general software testing. The ones that do undertake
software mocking as the main topic are studied using a limited number of
programming languages, rendering the considerations to be less effective in
other languages. However, comparing software tools of the same programming
language is beneficial for a software team researching to decide the most
suitable tool for their use case. For example, the empirical study of
open-source Java testing libraries would be of value for teams working on
Java-based systems (Zerouali, 2017). Whereas this paper lacks professional use
because of its language-agnostic nature.

## Evaluation

Mocking technology customarily takes shape as a software library that can be
easily integrated into an application without much overhead and plays well with
other libraries. It can also be a framework, an architecture taking a larger
role in the complete restructuring of application development, and is typically
incompatible with other frameworks. In the scope of this paper, it will
disregard the difference in size among these tools to avoid misambiguity. They
will refer to the same entity when this paper mentions a library or a framework
for the sake of simplicity.

Upon observing the usage type of existing mocking frameworks, it is apparent
that most mocking tools belong to 4 categories: basic tools presenting core
functionality, services tools mimicking application programming interface (API)
endpoints of web services, power tools exposing internal properties of otherwise
inaccessible parts of code, and bundled tools included as part of a larger
framework. The paper acknowledges the existence of other categorizations such as
generalizing mocking frameworks by features, size, or any other metrics. In the
end, the paper decided to refrain from covering them as it may unwittingly muddy
the main point of the research.

### General-purpose Frameworks

::: figure
![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/proj/evaluation1.png)<br>Figure 1A &mdash; General mocking architecture
:::

Open-source mocking toolkits like *Mockito* for Java, *Moq* for C#, and
*Testify* for Go support foundational mocking paradigms and represent the most
widely used concepts retained across multiple programming languages. Positioning
themselves as general-purpose tools, it is incumbent upon them to be lightweight
and user-friendly, contributing facts that see them being imported by subsequent
and more sophisticated tools. At its core, these tool sets produce test doubles:
fakes, stubs, and mocks (McDonough, 2021). They are terms used to describe
simulated objects and when to apply them according to common practices in the
software testing industry.

Fakes and stubs are the simplest form of test doubles theory to grasp. Both
portray the actual objects by mimicking their namespace and other specifications
of the production code. Consider a student database system, a faked database
instance would preserve all the original's public properties plus its
implementation, however flawed they might be. On the other hand, stubs do not
contain custom logic and instead are just a collection of hard-coded values or
comments. When a test triggers the execution of inserting a new student or
listing existing entries, the tested data are irrelevant to the underlying
database as they are merely designed to satisfy test requirements.

::: figure
```c#
public interface IStudentDatabase
{
  List<object> SelectAll();
}

public class FakeStudentDatabase : IStudentDatabase
{
  private List<object> _students =
      new List<object>() { "Jack", "John" };

  public List<object> SelectAll()
  {
    return _students;
  }
}

public class StubStudentDatabase : IStudentDatabase
{
  public List<object> SelectAll()
  {
    return Enumerable.Empty<object>().ToList();
  }
}

[TestFixture]
public class DatabaseTest
{
  [Test]
  public void GetStudents()
  {
    // simulate values
    var fake = new FakeStudentDatabase();
    var stub = new StubStudentDatabase();

    // assert appropriate behavior
    Assert.IsNotEmpty(fake.SelectAll());
    Assert.IsEmpty(stub.SelectAll());
  }
}
```
Figure 1B &mdash; Fake and stub in plain C#
:::

Nevertheless, values contained within a fake and a stub are static, thus not the
most right fit for test cases needing dynamic feedback. Take for example a
university course registration system, a course may have mutable attributes too
complicated for both fakes and stubs to simulate. Aptly configured mocks are
usually more sophisticated than fakes and stubs, giving the test writer more
control by defining their behavior upon creation. They are tailored for deep
interactions in unit and interaction tests.

::: figure
```c#
public interface ICourse
{
  object Instructor { get; set; }

  int GetSeats();
}

[TestFixture]
public class CourseTest
{
  [Test]
  public void MathCourse()
  {
    // simulate behaviors
    var mock = new Mock<ICourse>();
    mock.SetupProperty(x => x.Instructor, new Instructor("Jane Doe"));
    mock.Setup(x => x.GetSeats()).Returns(30);

    // assert dynamic values
    Assert.AreEqual("Jane Doe", mock.Object.Instructor.Name);
    Assert.AreEqual(30, mock.Object.GetSeats());
  }
}
```
Figure 1C &mdash; Mock in C# using Moq
:::

### Web Services Frameworks

::: figure
![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/proj/evaluation2.png)<br>Figure 2A &mdash; Services mocking architecture
:::

Apps and websites communicate with each other using web services via backend
transmissions. One of the most common communication protocols is
Representational State Transfer (REST) API, it adheres to Hypertext Transfer
Protocol (HTTP) which is growing increasingly intricate with each incremental
version (Fielding et al., n.d.). Perhaps this is an explanation for why there
are so many API mocking frameworks with distinctive approaches in development
today such as *WireMock* for Java, *Mock Service Worker (MSW)* for JavaScript,
and *Mockery* for PHP. Take, for example, a simulation of the HTTP GET method of
a university backend attached.

::: figure
```js
// setup REST API
const worker = setupWorker([
  rest.get('/students', async (req, res, ctx) => {
    return res(ctx.json([
      { name: 'Jack' },
      { name: 'John' },
    ]));
  }),
]);
worker.start();

// test a response
(listStudents = function() {
  // make the request
  const response = await fetch('/users');

  // assert response
  expect(response.json()).toEqual([
    { name: 'Jack' },
    { name: 'John' },
  ]);
})();
```
Figure 2B &mdash; HTTP GET in JavaScript using MSW
:::

As an extension, MSW can also simulate *Graph Query Language (GraphQL)* API, a
novel query language aimed to be a full replacement for REST with an easier
learning curve (Brito & Valente, 2020). At a glance, what stands out the most
with GraphQL is that the request schema is declared in the query, providing
unparalleled control compared to key-to-value assignment in traditional REST
API. What sets it apart from other communication protocols is efficiency, the
main feature that ensures the server only returns data that are requested,
deliberately ignoring the excess to conserve resources.

::: figure
```js
// setup GraphQL API
const worker = setupWorker([
  graphql.query('GetStudents', async (req, res, ctx) => {
    return res(ctx.data({
      students: [
        { name: 'Jack' },
        { name: 'John' },
      ],
    }));
  }),
]);
worker.start();

// test a response
(listStudents = function() {
  // make the request
  const response = await fetch('/graphql', {
    body: JSON.stringify({
      query: `
        query GetStudents {
          student {
            name
          }
        }
      `,
    }),
  });

  // assert response
  expect(response.json()).toEqual({
    data: {
      students: [
        { name: 'Jack' },
        { name: 'John' },
      ],
    },
  });
})();
```
Figure 2C &mdash; GraphQL query in JavaScript using MSW
:::

### Highly-customizable Frameworks

::: figure
![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/proj/evaluation3.png)<br>Figure 3A &mdash; Customizable mocking architecture
:::

Oftentimes, there are cases where access to the internal components of an
immutable code is a prerequisite for a test to pass. These attempts will
inevitably fail since the original writer does not intend the values to be
obtainable, let alone changing them. Deep mocking tools like *PowerMock* for
Java, *GoogleTest* for C++, and *OCMock* for Objective-C offer relief for this
kind of playout. They expose private fields and methods by executing at runtime,
allowing a dynamic change to the building code after compile time. For example
below, a mock manipulated the name of a university, which is obtained using a
private method.

::: figure
```java
public class University {
  private String getName() {
    return "Illinois Institute of Technology";
  }
}

@RunWith(PowerMockRunner.class)
@PrepareForTest(University.class)
public class UniversityTest {
  @Test
  public void PrivateMethod() {
    // create false instance
    University university = PowerMockito.spy(new University());
    Mockito.when(university.getName()).thenReturn("Illinois Tech");

    // assert changed value
    Assert.assertEquals("Illinois Tech", university.getName());
    Mockito.verify(university, Mockito.times(1)).getName();
  }
}
```
Figure 3B &mdash; Spying private method in Java using PowerMock
:::

Alternatively, PowerMock can deceive static properties by abusing the Java
reflection feature, a legacy technology that manipulates Java classes, fields,
methods, and parameters. Some parts of the test or main code might be dependent
on the results brought by the static properties and are now customizable using a
deep mocking tool. This technique is especially useful for a software team
looking to improve the code coverage standings, and in turn, generate a better
report. Though being highly customizable has its merits, it eventually
detriments the size of the project and concerns the effectiveness of future
development. Imagine a team conducting an immense update massively changing the
structure of the main code. The test mocks, in turn, would likely break as they
are tailored for the previous version.

::: figure
```java
public class UniversityUtility {
  private UniversityUtility() {}

  public static int getDefaultSeats() {
    return 20;
  }
}

@RunWith(PowerMockRunner.class)
@PrepareForTest(UniversityUtility.class)
public class UniversityUtilityTest {
  @Test
  public void StaticMethod() {
    // observe static method
    PowerMockito.mockStatic(UniversityUtility.class);
    PowerMockito.when(UniversityUtility.getDefaultSeats())
        .thenReturn(30);

    // assert changed value
    Assert.assertEquals(30, UniversityUtility.getDefaultSeats());
  }
}
```
Figure 3C &mdash; Mocking static method in Java using PowerMock
:::

### Pre-installed Frameworks

::: figure
![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/proj/evaluation4.png)<br>Figure 4A &mdash; Bundled mocking architecture
:::

The last category is a smaller pool of mocking tools that comes as a package
with a more significant framework tackling bigger issues. *Spring Framework* is
a perfect example, it is an all-encompassing Java application infrastructure
prized for its enterprise features and active communities. Spring Framework
&ndash; not to be confused with their similarly-named subsidiary *Spring Boot*
&ndash; has included `spring-mock` in their mainline product delivering
convenient mocking capabilities without the need for external dependencies.
Other notable frameworks such as *SonarQube* for static code analysis and
*VRaptor* for web development utilizing dependency injection have followed suit,
comprising in-house mocking tools albeit with the help of more abstract tools.

By bundling the mocking tools, the owner of the larger framework expects them to
be the default mocking solution. Nonetheless, the owner's preferences are rarely
enforced and thus could be disregarded when there exist better perspectives in
other options. Consider the test classes below to help visualize, both yield the
same result despite using different mocking tools.

::: figure
```java
@SpringBootTest
public class MySpringTest {
  @MockBean
  private MyBean myBean;
}

@RunWith(MockitoJUnitRunner.class)
public class MySpringTestUsingMockito {
  @Mock
  private MyBean myBean;
}
```
Figure 4B &mdash; Default vs. external mocking in Java using Spring Framework
:::

## Findings

I would like to begin with a disclaimer that I do not own the sampling data
shown in this section. They are comprised of separate scholarly studies, a few
of which may be proprietary information that I presume are still allowed to be
displayed under a fair policy of education purposes. I am oblivious to their
completeness and relinquish any responsibility regarding their accuracy. Since
the paper does not conduct its surveys, it is essentially a compiled review of
existing reviews. While it lacks original data, it will avoid projecting
assumptions toward the result, deciding to stick with the judgment of the cited
article's authors.

### Java Mocking Practices

::: figure
![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/proj/finding1.png)<br>Figure 5A &mdash; Apache Java mocking architecture
:::

An examination of Java mocking frameworks was spearheaded by the *Stevens
Institute of Technology* when they produced an evaluative comparison report in
partnership with the *University of Cincinnati* and the *University of Texas*
(Xiao et al., n.d.). The report conducted a thorough source code review of 193
projects maintained by the Apache Software Foundation (ASF), a non-profit
organization renowned for its open-source contribution to cloud computing,
databases, programming languages, and countless other topics in a smaller
capacity. 129 out of the said 193 projects are proven to use at least one tool,
cementing the proposition that ASF encourages the practice of mocking to isolate
dependencies. Figure 5 depicts a common architecture in an ASF project and how
are they being mocked.

::: figure
| Name | Projects | Acc. of Projects |
| --- | ---: | ---: |
| Mockito | 99 (77%) | 77% |
| EasyMock | 36 (28%) | 91% |
| PowerMock | 16 (12%) | 92% |
| Spring Framework | 16 (12%) | 94% |
| Others | 8 (6%) | 100% |
| Multiple Frameworks | 56 (40%) | - |
Table 1A &mdash; Popularity of Java unit testing frameworks
:::

Mockito is the most widely used framework scoring 77% of imports followed by
EasyMock with a significantly lower 28%. 12% of projects use Spring Framework as
it is the ASF integrated infrastructure of choice. Furthermore, 40% of the
projects chose to adopt multiple frameworks, a decision that is usually driven
by the project's complexity. The smallest portion, 6%, is dedicated to projects
that opted to use other lesser-known tools. It is crucial to point out that
their data-gathering process is automated by a script, allowing room for
inaccuracies for up to 9% of non-Mockito projects.

::: figure
| Name | Minimum | Average | Median | Maximum |
| --- | ---: | ---: | ---: | ---: |
| Test files | 1 (0.03%) | 50 (10.2%) | 13.5 (6.05%) | 492 (62.17%) |
| Mocked classes | 1 (0.7%) | 3.2 (16%) | 2 (12.1%) | 67 (100%) |
| Library classes | 0 (0%) | 25.4 (61.1%) | 9 (65.2%) | 622 (100%) |
| Mock files<br>without dependencies | 0 (0%) | 3.04 (0.6%) | 0 (0%) | 158 (11.5%) |
Table 1B &mdash; File count of Java mocking frameworks
:::

Table 1B shows that, in almost all of their test cases, the mocking framework
generates substantially less number of mock classes relative to the test
classes. However, the library infrastructure itself brought much more payload
than the classes they generated. In the most extreme case, their file count
difference ratio is roughly 10 times (622 to 67 files). Interestingly, there is
a small portion of projects in the organization that perform mocking techniques
without third-party libraries. Although its level of mocking sophistication
could not verified, thereby unable to determine whether or not said projects
should have used a mocking tool.

::: figure
| Function | Invokes | Description |
| --- | ---: | --- |
| createNiceMock | 5,555 | Create an empty mock object with default returns. |
| createMock | 2,668 | Create an empty mock object without default returns. |
| expect | 2,638 | Specify a method and enable stubbing. |
| andReturn | 1,067 | Stub the return value for a method returns anything but void. |
| replay | 891 | Switch mock object to replay mode. |
| verify | 425 | Verify a specific behavior of the mock object. |
| anyTimes | 276 | Expect a method of a mock object to be executed any times. |
| expectLastCall | 264 | Stub the behavior of void methods. |
| eq | 238 | Expects an object equals to the given value. |
| andStubReturn | 216 | Specific the default return for a method. |
| isA | 138 | Expects an object implementing the given class. |
Table 1C &mdash; Top ten most triggered methods in EasyMock
:::

The authors narrowed their focus to EasyMock in Table 1C to see how often each
API is called in the ASF projects. Unlike the Swiss army knife that is a
PowerMock, EasyMock is designed as an effortless library and, thus easier to
administer than its peers. They found that EasyMock's simpler APIs are
disproportionately triggered, an unsurprising discovery given that EasyMock
appeals to projects requiring convenience at the cost of customization. For
instance, the `createNiceMock` function is just a version of `createMock` with
default return values, yet is invoked twice as much. It is important to note
that the table included EasyMock's non-standard mocking exercises like recording
and `replay`.

::: figure
![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/proj/finding2.png)<br>Figure 5B &mdash; No mocking vs. mocking Java project size comparison
:::

In the last figure, the article theorized that a software team as large-scale as
ASF should expect approximately a 1.6 times increase in overall project size
should they decide to use a mocking framework in their project. The Java
programming language is already notorious for being bloated due to the bytecodes
they compiled. A further increase of 1.6 has the potential to drive the software
teams away from using a third-party tool. At the same time, working build size
is a less pressing matter considering computer storage drives are abundant. One
could even argue that this issue is supposedly insignificant in the future when
computers get more powerful.

### C++ Mocking Practices

::: figure
![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/proj/finding3.png)<br>Figure 6 &mdash; C++ abstract mocking architecture
:::

Contrary to the interpreted language that is Java, compiled languages like C++
and Rust are not translated line-by-line upon execution, allowing them to run
faster at the expense of reduced portability and elevated configuration
specifications. One extra specification is Dynamic Link Libraries (DLLs) in a
.NET platform found on all Microsoft Windows desktop computers. It is a
compilation mechanism that modularizes C++ programs (and other native
programming languages) by allowing the system-wide sharing of external
libraries. An assessment of C++ unit testing frameworks is detailed in a journal
released by *Yeungnam University* and the *Pusan National University* (Heo &
Sohn, 2013). In the examples provided by them in Figure 6, DLL dependencies are
decoupled from a unit test by using a separate test runner, which then creates
executables based on the DLLs.

::: figure
| Name | xUnit | Fixtures | Mocks | Exception | Macros | Templates |
| --- | :---: | :---: | :---: | :---: | :---: | :---: |
| CppUnit | &check; | &check; | &cross; | &check; | &check; | &cross; |
| Boost.Test | &check; | &check; | &cross; | &check; | User-configurable | &check; |
| GoogleTest | &check; | &check; | &check; | &check; | &check; | &check; |
| WinUnit | &check; | &check; | &cross; | &check; | &check; | &cross; |
| Cfix | &check; | &check; | &cross; | &check; | &check; | &cross; |
| Mock Object Testing | &check; | &check; | &check; | &cross; | &check; | &cross; |
Table 2 &mdash; Features of C++ unit testing frameworks
:::

It should be no surprise to anyone that mocking frameworks written in C++ are
much less populated than Java, a fact ascribed by how vastly famous Java is. The
journal reported that only 2 out of 6 prominent mocking frameworks natively
support mocks (Heo & Sohn, 2013). The authors stated that GoogleTest is the most
feature-rich and advocated that it should be the developer's first choice when
mocking is essential to their test. Despite their suggestion, it concluded that
no single unit test is the best as they come from distinct backgrounds. For one,
Cfix and Mock Object Testing are the work of a single software engineer while
the rest are affiliated with an organization, either created initially by or
transferred to one. Mock Object Testing, in particular, may be perceived as
inferior in contrast to GoogleTest but still is useful when a software team is
already familiar with the ecosystem.

## Conclusion

Even with all their bells and whistles, mocking objects in a test is
indisputably practical and a popular consensus among modern projects. I argue
that the keys to successful interaction between a team and a mocking technology
are tight management and strategic usage in each unique situation. In my
opinion, learning when to use a mocking framework is a more productive
discussion than being preoccupied with which tool is superior. Software
developers must identify a correct circumstance when mocking is necessary by
familiarizing themselves with the concept of test doubles. A better approach
would be utilizing object-oriented programming (OOP) characteristics in mocking
like construction and abstraction (Nandigam et al., 2010). As stated earlier,
over-mocking test objects complicate the codebase and lead to a resourcefully
expensive project. The repercussions of inexperience in basic techniques, to
some extent, outweigh the conveniences the mocking technology brings.

When the efficiency of mocks is an issue, the discussion should be directed
towards procedures to improve them rather than switching altogether to a new
tool. It is imperative for mocking practitioners to understand not only the
objects but also the roles in which mocks are supposed to act. Declare
documentation of mocking standards and demand the development team to follow the
directive. Documentation in any form aids in clearing ambiguity in mocking
practices and is exceptionally helpful to new members of the team. Further
enhancing the mocking effectiveness could be achieved by introducing new
concepts such as supporting cache, sequencing, and time restrictions (Freeman et
al., 2004). All of these are configurable into any mocking technology.

### Reflection

I have reviewed the rewards and drawbacks of utilizing mocking tools in software
testing, be it unit or integration tests. Despite mentioning more than a dozen
tools throughout the paper, I have admittedly only ever used a few of them and
am heavily underqualified to pass judgment against the rest. I learned a lot of
new things about mocking tools from the referred articles, especially in C++, a
topic I have no experience with. Therefore, my primary takeaway is that the
professional field of software testing is a rapidly growing industry with an
ever-evolving environment. Therefore, it is best to stay humble and up-to-date
with the latest mocking trends.

### Future Work

Knowing that the findings only included Java and C++, future work of the paper
could account for more programming languages, preferably of other types. For
example, Java and C++ already represent an interpreted and a compiled language,
respectively. The future work could extend into Haskell which constitutes a
functional language, and JavaScript, a scripting language. Supplementarily, it
could delve deeper into the unit testing subject as some of the studied tools
already possess such capability. At last, it could discuss an emerging trend of
Artificial Intelligence (AI)-assisted mocks with the recent rise of neural
network and machine learning movement.

## Acknowledgement

This research paper is a university work under the supervision of the Department
of Information Technology and Management at the Illinois Institute of
Technology. My thanks are directed to Dr. Nazneen Hashmi for guiding me toward
the mocking technology topic and for being supportive all the way.

## References

::: references
McDonough, J. E. (2021). Test Doubles. Automated Unit Testing with ABAP: A Practical Approach, 159-210. https://link.springer.com/chapter/10.1007/978-1-4842-6951-0_8

Moe, M. M. (2019). Comparative Study of Test-Driven Development TDD, Behavior-Driven Development BDD and Acceptance Test–Driven Development ATDD. International Journal of Trend in Scientific Research and Development, 3, 231-234. https://www.academia.edu/download/59918587/47_Comparative_Study_of_Test-Driven_Development__TDD___Behavior-Driven_Development__BDD__and_Acceptance_Test-20190702-92470-o453so.pdf

Zerouali, A. (2017). Analysis and observations of the evolution of testing library usage. In 2017 the Seminar Series on Advanced Techniques and Tools for Software Evolution (SATToSE). https://apps.umons.ac.be/docnum/c7b423fd-d183-486c-9cec-966066b9b364/86CCBF61-9EEF-451C-904C-FCC77FD66280/SATToSE_2017_paper_18.pdf

Brito, G., & Valente, M. T. (2020, March). REST vs GraphQL: A controlled experiment. In 2020 IEEE international conference on software architecture (ICSA) (pp. 81-91). IEEE. https://arxiv.org/pdf/2003.04761.pdf

Fielding, R. T., Nottingham, M., & Reschke, J. (n.d.). RFC 9110. RFC 9110: HTTP Semantics. https://www.rfc-editor.org/rfc/rfc9110.html

Xiao, L., Li, K., Lim, E., Wang, X., Wei, C., Yu, T., & Wang, X. (n.d.). An Empirical Study on the Usage of Mocking Frameworks in Apache Software Foundation. Available at SSRN 4100265. https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4100265

Heo, S. Y., & Sohn, Y. H. (2013). A Study of Unit Testing Frameworks on Open Source C++. Convergence Security Journal, 13(4), 33-39. https://koreascience.kr/article/JAKO201336448942865.pdf

Nandigam, J., Tao, Y., Gudivada, V. N., & Hamou-Lhadj, A. (2010). Using mock object frameworks to teach object-oriented design principles. The Journal of Computing Sciences in Colleges, 26(1), 40-48. https://www.researchgate.net/profile/Charles-Peck-4/publication/234827961_LittleFe_Parallel_and_distributed_computing_education_on_the_move/links/548985100cf2ef34479299a6/LittleFe-Parallel-and-distributed-computing-education-on-the-move.pdf#page=49

Freeman, S., Mackinnon, T., Pryce, N., & Walnes, J. (2004, October). Mock roles, not objects. In Companion to the 19th annual ACM SIGPLAN conference on Object-oriented programming systems, languages, and applications (pp. 236-246). https://planningcards.com/assets/downloads/papers/pra25-MockRoles.pdf
:::
