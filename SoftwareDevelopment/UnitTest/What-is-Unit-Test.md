###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Unit Test](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/UnitTest/README.md) |
------------

# Information Technology : What is Unit Test

Unit testing is a proven technique for ensuring software quality, with
plenty of benefits. Here are (more than) a few great reasons to unit
test:

  - Unit testing **validates** that each piece of your software not only
    works properly today, but continues to work in the future, providing
    a solid foundation for future development.
  - Unit testing **identifies defects at early stages** of the
    production process, which [reduces the
    costs](https://blog.parasoft.com/what-is-the-shift-left-approach-to-software-testing)
    of fixing them in later stages of the development cycle.
  - Unit-tested code is generally **safer to refactor**, since tests can
    be re-run quickly to validate that behavior has not changed.
  - Writing unit tests forces developers to consider how well the
    production code is designed in order to make it **suitable for unit
    testing**, and makes developers look at their code from a
    **different perspective**, encouraging them to consider corner cases
    and error conditions in their implementation.
  - Including unit tests in the **code review process** can reveal how
    the modified or new code is supposed to work. Plus, reviewers can
    confirm whether the tests are good ones or not.

It's unfortunate that all too often, developers either don't write unit
tests at all, don't write *enough* tests, or they don't *maintain* them.
I understand — unit tests can sometimes be tricky to write, or
time-consuming to maintain. Sometimes there's a deadline to meet, and it
feels like writing tests will make us miss that deadline. But not
writing enough unit tests or not writing good unit tests is a risky trap
to fall into.

So please consider my following best-practice recommendations on how to
write clean, maintainable, automated tests that give you all the
benefits of unit testing, with a minimum amount of time and effort.

## Less Time Performing Functional Tests

Functional tests are expensive. They typically involve opening up the
application and performing a series of steps that you (or someone else),
must follow in order to validate the expected behavior. These steps may
not always be known to the tester, which means they will have to reach
out to someone more knowledgeable in the area in order to carry out the
test. Testing itself could take seconds for trivial changes, or minutes
for larger changes. Lastly, this process must be repeated for every
change that you make in the system.

Unit tests, on the other hand, take milliseconds, can be run at the
press of a button and do not necessarily require any knowledge of the
system at large. Whether or not the test passes or fails is up to the
test runner, not the individual.

## Protection Against Regression

Regression defects are defects that are introduced when a change is made
to the application. It is common for testers to not only test their new
feature but also features that existed beforehand in order to verify
that previously implemented features still function as expected.

With unit testing, it's possible to rerun your entire suite of tests
after every build or even after you change a line of code. Giving you
confidence that your new code does not break existing functionality.

## Executable Documentation

It may not always be obvious what a particular method does or how it
behaves given a certain input. You may ask yourself: How does this
method behave if I pass it a blank string? Null?

When you have a suite of well-named unit tests, each test should be able
to clearly explain the expected output for a given input. In addition,
it should be able to verify that it actually works.

## Less Coupled Code

When code is tightly coupled, it can be difficult to unit test. Without
creating unit tests for the code that you're writing, coupling may be
less apparent.

Writing tests for your code will naturally decouple your code, because
it would be more difficult to test otherwise.

