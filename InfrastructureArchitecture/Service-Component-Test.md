









Infrastructure Architecture - Service Component Test
==================================================


 
Context
-------

You have applied the  [Microservice
architecture](https://microservices.io/patterns/Microservices.html) pattern.
The application consists of numerous services. Services often invoke
other services. You must write automated tests that verify that a
service behaves correctly.

Problem
-------

How do you easily test a service?

Forces
------

-   End to end testing (i.e. tests that launch multiple services) is
    difficult, slow, brittle, and expensive.

Solution
--------

A test suite that tests a service in isolation using test doubles for
any services that it invokes.

Examples
--------

[Spring Cloud
Contract](https://cloud.spring.io/spring-cloud-contract/) is
an open source project that supports this style of testing.

Examples
--------

This pattern has the following benefits:

-   Testing a service in isolation is easier, faster, more reliable and
    cheap

This pattern has the following drawbacks:

-   Tests might pass but the application will fail in production

This pattern has the following issues:

-   How to ensure that the test doubles always correctly emulate the
    behavior of the invoked services?



 



