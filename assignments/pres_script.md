# Evolution of Testing: From Manual to Automated

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide1.jpg)

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide2.jpg)

Software testing is the process of checking the quality, functionality, and
performance of a software product before launching. To do software testing,
testers either interact with the software manually or execute test scripts to
find bugs and errors, ensuring that the software works as expected. Software
testing is also done to see if business logic is fulfilled, or if there are any
missing gaps in requirements that need immediate tackles. 

Software testing is a crucial part of the software development life cycle.
Without it, app-breaking bugs that can negatively impact the bottom-line may go
undetected. Over time, as applications get more complex, software testing
activities have also evolved, with many new techniques and approaches
introduced.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide3.jpg)

The manual testing era refers to a time in software development when testing
processes were predominantly conducted manually, without the extensive use of
automated testing tools and frameworks. In the earlier stages of software
development, human testers were responsible for executing test cases, validating
functionalities, and identifying defects by interacting directly with the
software's user interface. This manual approach to testing was time-consuming,
labor-intensive, and prone to human errors, particularly as software systems
became more complex.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide4.jpg)

1. **Time-Consuming Process**: Manual testing can be a time-consuming process,
  especially when dealing with large and complex software applications. Testers
  need to execute test cases manually, analyze results, and report defects,
  which can slow down the overall development lifecycle.
2. **Human Error**: Manual testing is susceptible to human error, as testers
  might overlook certain scenarios or make mistakes while executing test cases.
  This can lead to inaccurate test results and potentially allow defects to go
  unnoticed, impacting the overall quality of the software.
3. **Limited Test Coverage**: Due to time constraints and the manual nature of
  the testing process, achieving comprehensive test coverage can be challenging.
  Testers may prioritize certain test scenarios or paths, leaving other parts of
  the application untested. This limitation increases the risk of undetected
  defects in the software.
4. **Repetitive Tasks**: Manual testing often involves the repetition of test
  scenarios, especially during regression testing or when new releases are made.
  Performing repetitive tasks can be monotonous and may lead to a decrease in
  the tester's attentiveness, making it more likely for them to miss critical
  defects. Additionally, the repetitiveness can impact the morale and job
  satisfaction of testing teams.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide5.jpg)

Automated testing is a software testing technique that automates the process of
validating the functionality of software and ensures it meets requirements
before being released into production. With automated testing, an organization
can run specific software tests at a faster pace without human testers.
Automated testing is best suited for large or repetitive test cases.

Automated software testing uses scripted sequences executed by testing tools.
Automated testing tools examine the software, report outcomes and compare
results with earlier test runs. An automated test script can be created once and
then used repeatedly.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide6.jpg)

1. **Efficiency**: Automated testing accelerates the testing process, providing
  quick feedback on software functionality and performance. Tests can be run
  concurrently and repeatedly, saving time and resources.
2. **Consistency**: Automated testing ensures uniform test execution, reducing
  the risk of human error and delivering accurate, reliable results. Tests
  precisely follow predefined steps, minimizing the chance of overlooking
  critical issues.
3. **Cost-effective**: Despite an initial investment in tools and
  infrastructure, automated testing proves cost-effective by reducing the need
  for a large manual testing team. This leads to overall savings in time and
  resources.
4. **Reusability and Scalability**: Automated test scripts are reusable across
  different development phases, providing consistent testing. The scalability of
  automated testing allows efficient testing of larger and more complex systems
  without a proportional increase in manual efforts.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide7.jpg)

1. **Unit Testing**: Involves testing individual components or units of a
  software application in isolation to ensure they function as intended. It is
  typically the earliest phase of automated testing and focuses on verifying the
  correctness of small, isolated code segments.
2. **Integration Testing**: Tests the interactions between different components
  or modules to ensure they work together seamlessly. Integration testing
  identifies issues that may arise when combining individual units and validates
  the proper flow of data between interconnected parts of the application.
3. **Functional Testing**: Evaluates the software's functionality by testing its
  features against specified requirements. This type of testing verifies that
  the application performs its intended functions and produces expected
  outcomes, covering scenarios such as input validation, data manipulation, and
  user interactions.
4. **Regression Testing**: Ensures that new code changes do not adversely affect
  existing functionalities. Automated regression testing involves re-running
  previously executed tests to catch any unintended side effects of recent code
  modifications, helping maintain the overall stability of the software.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide8.jpg)

1. **Performance Testing**: Focuses on assessing the speed, responsiveness, and
  overall performance of a software application under different conditions. This
  includes stress testing to evaluate system behavior under extreme loads, load
  testing to measure performance under expected user loads, and scalability
  testing to assess the application's ability to handle growing demands.
2. **Load Testing**: Evaluates a system's performance by subjecting it to
  increasing workloads. The goal is to identify the system's capacity limits and
  potential bottlenecks under various levels of user activity.
3. **Acceptance Testing**: Verifies whether the software meets the specified
  requirements and if it is ready for deployment. This type of testing often
  involves automated scripts that simulate end-user interactions to validate the
  application against predefined acceptance criteria.
4. **Security Testing**: Identifies vulnerabilities and weaknesses in the
  software's security measures. Automated security testing tools can scan for
  potential security threats, such as code vulnerabilities, data breaches, or
  unauthorized access, helping to ensure the robustness of the application's
  security features.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide9.jpg)

Test automation tools play a crucial role in streamlining and optimizing the
software testing process by automating the execution of test cases, reducing
manual efforts, and ensuring faster feedback on the application's quality.

Numerous tools, including Selenium, JUnit, and TestNG, have become integral to
automated testing. These tools provide a framework for creating, managing, and
executing automated test scripts.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide10.jpg)

Transitioning to automation in software testing involves assessing testing
requirements, providing skills training, and selecting appropriate tools such as
Selenium or JUnit. Start with pilot projects to gain hands-on experience and
gradually automate regression or repetitive test cases. Develop a scalable test
automation framework, integrate it into your CI/CD pipeline, and encourage
collaboration between testing and development teams. Leverage version control
systems, implement metrics for tracking success, and regularly reassess and
refine your automation strategy to align with evolving project needs and
technology landscapes.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide11.jpg)

1. **Early Involvement in Development**: Integrate automated testing early in
  the development lifecycle to identify and address issues at the earliest
  possible stage.
2. **Continuous Integration (CI)**: Implement automated tests within a
  continuous integration framework. This practice involves automatically running
  tests whenever code changes are committed to the version control system.
3. **Maintainable and Modular Test Scripts**: Create modular and maintainable
  test scripts. Divide tests into smaller, independent modules to enhance
  reusability and ease of maintenance. Well-organized scripts are essential for
  adapting to changes in the application without extensive rework.
4. **Version Control for Test Code**: Place automated test code under version
  control to track changes, collaborate effectively, and revert to previous
  states if necessary. Version control helps maintain a stable and reliable test
  codebase, especially in collaborative development environments.
5. **Clear and Comprehensive Test Documentation**: Document test cases, test
  data, and test results comprehensively. Clear documentation facilitates
  collaboration among team members, helps new team members understand test
  scenarios, and serves as a valuable resource for debugging and
  troubleshooting.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide12.jpg)

Overcoming challenges in test automation is crucial for a successful
implementation. Common hurdles include selecting the right tools, maintaining
test scripts, and achieving comprehensive test coverage. To address these
issues, teams can invest in training to enhance automation skills, prioritize
the creation of a robust automation framework, and regularly review and update
test scripts. Collaboration between development and testing teams is key to
aligning automation efforts with application changes.

Additionally, addressing flaky tests through stability improvements and focusing
on strategic test case selection can improve overall reliability. Embracing a
continuous learning culture, where teams stay updated on automation trends and
best practices, is essential for overcoming challenges and optimizing the
benefits of automated testing.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide13.jpg)

1. **Shift-Left and Shift-Right Testing**: Shift-Left: Emphasizes early
  involvement of testing in the development process, catching defects as soon as
  possible.
2. **AI and Machine Learning in Testing**: Integration of artificial
  intelligence (AI) and machine learning (ML) to enhance test automation,
  predict potential issues, and optimize testing processes. AI can also be used
  for intelligent test case generation and maintenance.
3. **Test Automation and DevOps**: Increased automation across the entire DevOps
  pipeline, including not only functional tests but also performance, security,
  and other types of testing. The goal is to achieve continuous testing and
  faster feedback loops.
4. **Robotic Process Automation (RPA) Testing**: Testing of robotic process
  automation workflows to ensure the reliability and efficiency of automated
  business processes. This is particularly relevant as organizations
  increasingly adopt RPA for repetitive tasks.
5. **API and Microservices Testing**: With the rise of microservices
  architectures, there is a growing emphasis on testing APIs and microservices.
  Specialized tools and frameworks are expected to evolve to meet the unique
  challenges associated with testing these distributed systems.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide14.jpg)

AI is transforming the landscape of software testing by introducing automation,
intelligence, and efficiency into traditional testing practices. One of the key
applications is in test automation, where AI facilitates the generation and
maintenance of test scripts, ensuring adaptability to evolving software.
Intelligent test execution, powered by AI algorithms, optimizes the testing
process by prioritizing test cases based on code changes, providing quicker
feedback on critical functionalities.

Test data generation benefits from AI's ability to intelligently create diverse
datasets, covering a broad range of scenarios and inputs. Additionally, AI aids
in defect prediction and prevention by analyzing historical data, enabling teams
to focus testing efforts on high-risk areas. The integration of AI-driven
analytics and autonomous testing agents further propels testing towards a more
intelligent, predictive, and efficient future.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide15.jpg)

Continuous Testing is a software testing practice integrated seamlessly into the
Continuous Integration/Continuous Deployment (CI/CD) pipeline, enabling rapid
and reliable delivery of software. It involves automating the testing process
and executing tests throughout the development lifecycle, ensuring that code
changes are continuously validated for functionality, performance, and security.
Continuous Testing aims to provide immediate feedback to developers, reducing
the time between code changes and the detection of defects. Key components
include automated unit testing, integration testing, and end-to-end testing.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide16.jpg)

1. **Initial Investment**: Implementing automated testing requires an initial
  investment in tools, infrastructure, and training, which can be a barrier for
  some organizations.
2. **Script Maintenance**: Automated test scripts need ongoing maintenance to
  adapt to changes in the application, potentially consuming resources and time
  that could offset initial gains.
3. **Test Data Management**: Generating and managing diverse, relevant test data
  for automated testing can be challenging, especially in complex scenarios.
4. **Limited User Interface Testing**: While automated testing is efficient for
  backend processes, comprehensive testing of user interfaces, especially for
  dynamic and responsive applications, may still require manual efforts.
5. **Flaky Tests**: Tests that produce inconsistent results, known as flaky
  tests, can be a persistent challenge, leading to reduced trust in automated
  testing outcomes.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide17.jpg)

1. **Efficiency and Speed**: Automated testing significantly accelerates the
  testing process, providing faster feedback on software quality and
  facilitating quicker releases.
2. **Repeatability and Consistency**: Automated tests ensure consistent
  execution of test cases, reducing the risk of human error and improving the
  reliability of testing outcomes.
3. **Regression Testing**: Automated tests are ideal for conducting thorough
  regression testing, ensuring that code changes do not adversely impact
  existing functionalities.
4. **Parallel and Scalable Testing**: Automated testing allows for parallel
  execution of tests and scalability, enabling teams to test larger and more
  complex systems efficiently.
5. **Continuous Integration/Continuous Deployment (CI/CD)**: Automated testing
  seamlessly integrates with CI/CD pipelines, providing immediate feedback and
  supporting the continuous delivery of high-quality software.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide18.jpg)

The evolution of testing from manual to automated reflects the dynamic nature of
the software development industry. Embracing automation is not just a trend but
a necessity for staying competitive and delivering high-quality software.

> ![](https://github.com/hendraanggrian/IIT-ITM536/raw/assets/assignments/pres/slide19.jpg)

Thank you for joining us in this exploration of the evolution of testing. We
hope this presentation has provided valuable insights into the transformative
journey from manual to automated testing.
