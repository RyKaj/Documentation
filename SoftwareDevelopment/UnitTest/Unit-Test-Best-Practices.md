###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Unit Test](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/UnitTest/README.md) |
------------

# Information Technology : Unit Test - Best Practices


Let's look at some best practices for building, running, and maintaining
unit tests, to achieve the best results.

  - Test cases should be small and isolated. As mentioned above, they
    should test something specific about the code.
  - Try keeping test to assertion ratio near to 1. It makes it easy to
    identify any assertion which has failed. Having multiple assertions
    can make it cumbersome to verify which assertion went rogue.
  - Always avoid test interdependence. Each test case should handle
    their own build up and tear down. Test runners don't generally run
    tests in any specified order. Thus, we can not assume anything based
    on the order in which we write the cases.
  - A test case approaches the behavioral aspect of the code. So it
    should be easily comprehensible in the sense that what we are
    testing and what to do in case of failure.
  - Mock as little as needed. Too many fakes create fragile tests which
    break when they code undergoes changes in production.
  - Avoid mocking chatty interfaces. Any change in the order of calling
    may break the test.
  - It should be independent of external factors. You must not require a
    setup to run a unit test.
  - We must maintain a clear naming convention in writing unit tests.
    This simply makes our code more comprehensible.
  - While working on a continuous integration build, always add the unit
    test cases to the build so that whenever one test case fails, the
    whole build fails thus leaving no exemptions.
  - **Fast**. It is not uncommon for mature projects to have thousands
    of unit tests. Unit tests should take very little time to run.
    Milliseconds.
  - **Isolated**. Unit tests are standalone, can be run in isolation,
    and have no dependencies on any outside factors such as a file
    system or database.
  - **Repeatable**. Running a unit test should be consistent with its
    results, that is, it always returns the same result if you do not
    change anything in between runs.
  - **Self-Checking**. The test should be able to automatically detect
    if it passed or failed without any human interaction.
  - **Timely**. A unit test should not take a disproportionately long
    time to write compared to the code being tested. If you find testing
    the code taking a large amount of time compared to writing the code,
    consider a design that is more testable.

## Unit Tests Should Be Trustworthy

The test must fail if the code is broken and only if the code is broken.
If it doesn't, we cannot trust what the test results are telling us.

## Unit Tests Should Be Maintainable and Readable

When production code changes, tests often need to be updated, and
possibly debugged as well. So it must be easy to read and understand the
test, not only for whoever wrote it, but for other developers as well.
Always organize and name your tests for clarity and readability.

## Unit Tests Should Verify a Single-Use Case

Good tests validate one thing and one thing only, which means that
typically, they validate a single use-case. Tests that follow this best
practice are simpler and more understandable, and that is good for
maintainability and debugging. Tests that validate more than one thing
can easily become complex and time-consuming to maintain. Don't let this
happen.

Another best practice is to use a minimal number of assertions. Some
people recommend just one assertion per test (this may be a little too
restrictive); the idea is to focus on validating only what is needed for
the use-case you are testing.

## Unit Tests Should Be Isolated

Tests should be runnable on any machine, in any order, without affecting
each other. If possible, tests should have no dependencies on
environmental factors or global/external state. Tests that have these
dependencies are harder to run and usually unstable, making them harder
to debug and fix, and end up costing more time than they save (see
**trustworthy**, above).

Martin Fowler, a few years ago, [wrote
about](https://www.martinfowler.com/bliki/UnitTest.html) "solitary" vs.
"sociable" code, to describe dependency usage in application code, and
how tests need to be designed accordingly. In his article, "solitary"
code doesn't depend on other units (it's more self-contained), whereas
"sociable" code does interact with other components. If the application
code is solitary, then the test is simple, but for sociable code under
test, you can either build a "solitary" or "sociable" test. A "sociable
test" would rely on real dependencies in order to validate behavior,
whereas a "solitary test" isolates the code under test from
dependencies. You can use mocks to isolate the code under test, and
build a "solitary" test for "sociable" code. We'll look at how to do
that below.

![](https://blog.parasoft.com/hs-fs/hubfs/sociable%20vs%20solitary%20tests.png?width=424&name=sociable%20vs%20solitary%20tests.png)

***Figure 1:** Sociable vs Solitary Tests. Source: Martin Fowler, 2014,
["Unit Test"](https://www.martinfowler.com/bliki/UnitTest.html)*

In general, using mocks for dependencies makes our life easier as
testers, because we can generate "solitary tests" for sociable code. A
sociable test for complex code may require a lot of setup, and may
violate the principles of being isolated and repeatable. But since the
mock is created and configured in the test, it is self-contained and we
have more control over the behavior of dependencies. Plus, we can test
more code paths. For instance, I can return custom values or throw
exceptions from the mock, in order to cover boundary or error
conditions.

## Unit Tests Should Be Automated

Make sure tests are being run in an automated process. This can be
daily, or every hour, or in a Continuous Integration or Delivery
process. The reports need to be accessible to and reviewed by everyone
on the team. As a team, talk about which metrics you care about: code
coverage, modified code coverage, number of tests being run,
performance, etc.

A lot can be learned by looking at these numbers, and a big shift in
those numbers often indicates regressions that can be addressed
immediately.

## Use a Good Mixture of Unit and Integration Tests

Michael Cohn's book, *[Succeeding with Agile: Software Development Using
Scrum](https://www.goodreads.com/book/show/6707987-succeeding-with-agile),*
addresses this using a testing pyramid model (see illustration in the
image below). This is a commonly-used model to describe the ideal
distribution of testing resources. The idea is that as you go up in the
pyramid, tests are usually more complex to build, more fragile, slower
to run, and slower to debug. Lower levels are more isolated and more
integrated, faster, and simpler to build and debug. Therefore, automated
unit tests should make up the bulk of your tests.

![](https://blog.parasoft.com/hs-fs/hubfs/pyramid.png?width=700&name=pyramid.png)

Unit tests should validate all of the details, the corner cases and
boundary conditions, etc. Component, integration, UI, and functional
tests should be used more sparingly, to validate the behavior of the
APIs or application as a whole. Manual tests should be a minimal
percentage of the overall pyramid structure, but are still useful for
release acceptance and exploratory testing. This model provides
organizations with a high level of automation and test coverage, so that
they can scale up their testing efforts and keep the costs associated
with building, running, and maintaining tests at a minimum.

## Unit Tests Should Be Executed Within an Organized Test Practice

In order to drive the success of your testing at all levels, and make
the unit testing process scalable and sustainable, you will need some
additional practices in place. First of all, this means **writing unit
tests as you write your application code**. Some organizations write the
tests before the application code (
[test-driven](https://dzone.com/articles/why-developers-dont-use-tdd) or
[behavior-driven](https://dzone.com/articles/tddbdd-an-introduction-amp-usage-guide)
programming). The important thing is that tests go hand-in-hand with the
application code. The tests and application code should even be reviewed
together in the code review process. Reviews help you understand the
code being written (because they can see the expected behavior) and
improve tests too\!

Writing tests along with code isn't just for new behavior or planned
changes, it's critical for bug fixes too. **Every bug you fix should
have a test that verifies the bug is fixed**. This ensures that the bug
stays fixed in the future.

Adopt a zero-tolerance policy for failing tests. If your team is
ignoring test results, then why have tests at all? Test failures should
indicate real issues...so address those issues right away, before they
waste QA's time, or worse, they get into the released product.

The longer it takes to address failures, the more time and money those
failures will ultimately cost your organization. So run tests during
refactoring, run tests right before you commit code, and don't let a
task be considered "done" until the tests are passing too.

Finally, **maintain those tests**. As I said before, if you're not
keeping those tests up-to-date when the application changes, they lose
their value. Especially if they are failing, failing tests are costing
time and money to investigate each time they fail. Refactor the tests as
needed, when the code changes.

As you can see, maximizing your returns on money and time invested in
your unit tests requires some investment in applying best practices. But
in the end, the rewards are worth the initial investment.

