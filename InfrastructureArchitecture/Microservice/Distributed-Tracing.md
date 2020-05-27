###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Infrastructure Architecture](https://github.com/RyKaj/Documentation/tree/master/InfrastructureArchitecture/README.md) |
------------

Infrastructure Architecture - Distributed Tracing
===============================================

Context
-------

You have applied the  [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html).
Requests often span multiple services. Each service handles a request by
performing one or more operations, e.g. database queries, publishes
messages, etc.

Problem
-------

How to understand the behavior of an application and troubleshoot problems?

Forces
------

-   External monitoring only tells you the overall response time and  number of invocations - no insight into the individual operations
-   Any solution should have minimal runtime overhead
-   Log entries for a request are scattered across numerous logs

Solution
--------

Instrument services with code that

-   Assigns each external request a unique external request id
-   Passes the external request id to all services that are involved in handling the request
-   Includes the external request id in all  [log messages](https://microservices.io/patterns/observability/application-logging.html)
-   Records information (e.g. start time, end time) about the requests and operations performed when handling a external request in a centralized service

This instrumentation might be part of the functionality provided by a 
[Microservice Chassis
framework](https://microservices.io/patterns/microservice-chassis.html).

Resulting Context
-----------------

This pattern has the following benefits:

-   It provides useful insight into the behavior of the system including the sources of latency
-   It enables developers to see how an individual request is handled by searching across  [aggregated logs](https://microservices.io/patterns/observability/application-logging.html) for its external request id

This pattern has the following issues:

-   Aggregating and storing traces can require significant infrastructure

**Related Patterns**

-   [Log aggregation](https://microservices.io/patterns/observability/application-logging.html) -
    the external request id is included in each log message



 



