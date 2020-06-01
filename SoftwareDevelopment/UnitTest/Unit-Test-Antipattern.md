###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Unit Test](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/UnitTest/README.md) |
------------

# Information Technology : Unit Test - Antipattern

  - Using nondeterministic factors in the codebase: Such scenarios are
    difficult to test especially when they don't reproduce/hold a
    constant value on each rerun. Eg Using Time as an authentication
    measure in code which would vary at each moment and also in
    different time zones.

  - Using side-effecting methods: Testing these could be as difficult as
    testing methods with a nondeterministic factor in them. Poorly
    designed untestable code introduce unwarranted complexities.

  - Impurity is highly toxic: Method depending upon nondeterministic or
    side-effecting methods themselves become the same kind and in the
    end complicate the entire codebase. Considering the effect it may
    have on a real-life complex application, we may find ourselves
    trapped in codebase filled with antipatterns, secret dependencies
    and all sorts of unpleasant scenarios.

  - Mocking interfaces and classes outside the codebase: If you don't
    fully understand the proper usage of an interface, you should avoid
    mocking it. Rather you should wrap interaction with external API
    classes into specially created interfaces for the same purpose.

  - Working with the mutable global state: Method depending upon mutable
    global state not only requires you to consider the current value but
    also be updated about other code that may have altered its value
    earlier. Hence its advisable to avoid them.

