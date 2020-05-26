









Infrastructure Architecture - Audit Logging
=========================================


 
Context
-------

You have applied the  [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html).

Problem
-------

How to understand the behavior of users and the application and
troubleshoot problems?

Forces
------

-   It is useful to know what actions a user has recently performed:
    customer support, compliance, security, etc.

Solution
--------

Record user activity in a database.

Examples
--------

This pattern is widely used.

Resulting Context
-----------------

This pattern has the following benefits:

-   Provides a record of user actions

This pattern has the following drawbacks:

-   The auditing code is intertwined with the business logic, which
    makes the business logic more complicated

Examples
--------

-   [Event
    Sourcing](https://microservices.io/patterns/data/event-sourcing.html) is
    a reliable way to implement auditing



 



