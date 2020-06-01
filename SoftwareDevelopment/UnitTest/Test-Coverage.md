###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Unit Test](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/UnitTest/README.md) |
------------

# Information Technology : Test Coverage


> **Side note:** Normally I use the name ***requirements coverage***, as it’s more akin to what the metric actually represents. But for consistency I’ll keep going with *test coverage* for this article.

A quick reminder:

> **Test coverage** is about the proportion of a story or feature covered by tests.

Conversations about test coverage tend to center around [acceptance
tests](https://medium.com/swlh/write-tests-at-three-levels-909561a9544b),
which follow the requirements more naturally than code-centric,
developer-owned tests (unit tests, component tests). Use a BDD framework
such as [Serenity](http://www.thucydides.info/#/whatisserenity) (wisely
renamed from Thucydides) to report on which requirements have acceptance
tests, and “pow”, you have your test coverage score. Pretty
straightforward\!

That’s all fine, but there’s much to be gained from viewing your
developer-owned tests in terms of test coverage as well.

This approach is *infinitely* more useful than code coverage (yes, that
much\!) because:

  - It encourages developers to focus their tests on the business domain
    and the requirements (stories and scenarios), with the result that…
  - Your tests will become more purposeful. And…
  - Because you’re writing a test for each scenario, you know when
    you’ve written enough tests — and *ipso facto* when you’ve written
    enough code overall.

While you’re measuring test coverage, it’s still useful to run a code
coverage tool to discover areas of code that aren’t tested at all — even
though it’s really quite a narrow metric.

But instead of asking “Why isn’t this code covered by tests?” try asking
instead:

> “Why is this code here at all?”

If the code doesn’t have any tests, that means it likely isn’t covered
by any particular story… so no-one asked for it… which means it isn’t
providing business value… which means it can probably even be deleted.

This is why the *code coverage* score is still useful. It isn’t the “80%
covered” score that you’re interested in, it’s the other side — the “20%
missed”:

<kbd>![](https://miro.medium.com/max/3382/1*UI9iCUrRPiGos7kEVqxbVA.jpeg)</kbd>

Code **un**coverage?

So the code coverage metric can be used to indicate where there might be
insufficient test coverage — or code that can potentially be deleted.

But we just used a code coverage tool to uncover missing test coverage.
Why not use a test coverage tool instead?

There are some around, generally built into BDD frameworks such as
[Robot Framework](https://robotframework.org/) and the imaginatively
named [Test Project](https://testproject.io/).

But these have the same kind-of unavoidable problem that test coverage
does—they don’t tell you the quality of your coverage. Taken to
extremes, your tests could consist of `assert 1 == 1` and get a 100%
score.

And, more pertinently, these test frameworks don’t extend beyond BDD
into the lower-level, developer-owned tests.

But that’s actually ok. As you’ve seen,

> code/test coverage scores just don’t bring home the bacon.

Really, **test coverage is more of a concept than a measurable score**.
Yet the effect of not having requirements-based tests in your project
*is* measurable, in the number of bugs that’ll surface in production.

###### References

  - [Codeburst - code coverage vs test coverage](https://codeburst.io/code-coverage-vs-test-coverage-c9afb261e902)

