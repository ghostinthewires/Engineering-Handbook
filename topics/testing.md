---
layout: site
title: Testing
body_class: code
---

For any code to be considered ready for production there need to be tests. For a given change this might include writing Unit Tests[^1], Integration Tests and End to End Browser Tests. We need to ensure that we have an appropriate level of testing. Our [code review](code-reviews.html) process should pick up issues around the appropriate level of testing.

### Thoroughly test your own code

If you’re fortunate enough to have support in the form of a QA team or a group of manual testers, that’s great, but ultimately **you are responsible for the quality of what you launch.**

### General Guidelines

* All test suites should produce xUnit reports.
* All test reports should be integrated into continuous integration tools (GitHub Actions, SonarQube etc), so that the CI tool can parse those results and provide detailed reports to the team; as well as fail the build should any tests fail.
* All reports for browser test suites should include screenshots.
* If possible, tests should include code-coverage reporting, so we can monitor and improve coverage over time.
* If you pick up some untested code - this will happen - put tests in place first so our situation improves.

### Unit tests

Unit tests are a cheap way to test code, and should be included to support and document the behaviour of code. However, they are particularly useful for exercising expected error conditions (e.g. an aborted database transation; a 500 HTTP response).

It can be tempting to mock the system under test, but you should not do this as it results in a restatement of the code, which is overly-coupled to code *structure* rather than *behaviour*. Mock at service boundaries instead. Furthermore, think hard before mocking at the service boundary: does the service use file, database, or network I/O? If not, could you use the real service instead?

### Integration or end-to-end tests

Integration and end-to-end tests are much more valuable from the perspective of testing workflows. However, they typically do not allow us to exercise specific error scenarios.

Integration tests or end-to-end tests *alone* are insufficient - things that cannot be exercised in these tests **must** be covered with unit tests.

### End to End Browser Testing

End to End Browser tests are by definition time consuming. In order to ensure that we can keep build durations down we need to consider a number of things when writing them:

* Ensure that tests are atomic, in other words the test you are authoring should not be dependent on any other test in the suite, or rely on fixture data that another test is likely to change.
    * It might be helpful to ask yourself *can my test be run multiple times without the need to reset data*
* Ensure that all of our tests can be run in parallel. This is important because it is one of the most effective ways we can help ensure that build durations are kept to a minimum.
* Flaky Tests are Poison[^2]. If a test intermittently fails it creates frustration, reduces confidence and slows our ability to release. These tests should be quarantined and fixed/re-written.
* Where possible you should be avoiding the use of sleep() commands unless absolutely necessary. Instead you should be waiting for specific elements to be present/visible e.g. **$this->waitForElementID("itemAppearsOn");.**

If your browser test suite is taking longer than 45 minutes to run, then it’s time to refactor.

[^1]: [Unit Tests - Martin Fowler](https://martinfowler.com/bliki/UnitTest.html)
[^2]: [Never send a human to do a machines job](https://www.youtube.com/watch?v=_5Sr4EYH7M8)



