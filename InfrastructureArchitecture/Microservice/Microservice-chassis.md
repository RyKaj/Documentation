###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Infrastructure Architecture](https://github.com/RyKaj/Documentation/tree/master/InfrastructureArchitecture/README.md) |
------------


Infrastructure Architecture - Microservice chassis
================================================


 
Context
-------

When you start the development of an application you often spend a
significant amount of time putting in place the mechanisms to handle
cross-cutting concerns. Examples of cross-cutting concern include:

-   Externalized configuration - includes credentials, and network
    locations of external services such as databases and message brokers
-   Logging - configuring of a logging framework such as log4j or
    logback
-   Health checks - a url that a monitoring service can "ping" to
    determine the health of the application
-   Metrics - measurements that provide insight into what the
    application is doing and how it is performing
-   [Distributed
    tracing](https://microservices.io/patterns/observability/distributed-tracing.html) -
    instrument services with code that assigns each external request an
    unique identifier that is passed between services.

As well as these generic cross-cutting concerns, there are also
cross-cutting concerns that are specific to the technologies that an
application uses. Applications that use infrastructure services such as
databases or a message brokers require boilerplate configuration in
order to do that. For example, applications that use a relational
database must be configured with a connection pool. Web applications
that process HTTP requests also need boilerplate configuration.

It is common to spend one or two days, sometimes even longer, setting up
these mechanisms. If you going to spend months or years developing a
monolithic application then the upfront investment in handling
cross-cutting concerns is insignificant. The situation is very
different, however, if you are developing an application that has the 
[microservice
architecture](https://microservices.io/patterns/microservices.html).
There are tens or hundreds of services. You will frequently create new
services, each of which will only take days or weeks to develop. You
cannot afford to spend a few days configuring the mechanisms to handle
cross-cutting concerns. What is even worse is that in a microservice
architecture there are additional cross-cutting concerns that you have
to deal with including service registration and discovery, and circuit
breakers for reliably handling partial failure.

Forces
------

-   Creating a new microservice should be fast and easy
-   When creating a microservice you must handle cross-cutting concerns
    such as externalized configuration, logging, health checks, metrics,
    service registration and discovery, circuit breakers. There are also
    cross-cutting concerns that are specific to the technologies that
    the microservices uses.

Solution
--------

Build your microservices using a microservice chassis framework, which
handles cross-cutting concerns

Examples
--------

Resulting Context
-----------------

The major benefit of a microservice chassis is that you can quickly and
easy get started with developing a microservice.

You need a microservice chassis for each programming language/framework
that you want to use. This can be an obstacle to adopting a new
programming language or framework.



 



