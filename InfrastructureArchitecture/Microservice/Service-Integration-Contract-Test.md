[comment]: [Architecture](ReadMe.MD)

Infrastructure Architecture - Service Integration Contract Test
=============================================================


 
Context
-------

You have applied the  [Microservice
architecture](https://microservices.io/patterns/Microservices.html) pattern.
The application consists of numerous services. Services often invoke
other services. You must write automated tests that verify that a
service behaves correctly.

Problem
-------

How to easily test that a service provides an API that its clients
expect?

Forces
------

-   End to end testing (i.e. tests that launch multiple services) is
    difficult, slow, brittle, and expensive.

Solution
--------

A test suite for a service that is written by the developers of another
service that consumes it. The test suite verifies that the service meets
the consuming service's expectations.

Examples
--------

[Spring Cloud
Contract](https://cloud.spring.io/spring-cloud-contract/) is
an open source project that supports this style of testing.

**Related Context**

This pattern has the following benefits:

-   Testing a service in isolation is easier, faster, more reliable and
    cheap

This pattern has the following drawbacks:

-   Tests might pass but the application will fail in production

This pattern has the following issues:

-   How to ensure that the consumer provided tests match what the
    consumer actually requires?



 



