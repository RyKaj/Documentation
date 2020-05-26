




3.  [Microservices & Distributed
    System](Microservice-DistributedSystem.html)


Infrastructure Architecture - Microservice Architecture
=====================================================


 

Created by Ryan Kajiura, last modified on Mar 22, 2020


 {#main-content .wiki-content .group}
Author: [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

\

![](https://miro.medium.com/max/3888/1*Truk-k8ByTT8vSlBiTdajg.jpeg){height="250"} 
![](https://miro.medium.com/max/3543/1*_xgCMK7sfxI8aPnm48E_Qg.jpeg){height="250"}![](attachments/Microservice-Architecture_0.png){.confluence-embedded-image
.confluence-content-image-border height="250"}

\

 {#expander-83930646 .expand-container}
 {#expander-control-83930646 .expand-control}
What is Microservices?


 {#expander-content-83930646 .expand-content}
In a large application, pieces of code are always calling each other.
This creates a web of dependencies such that changing a piece of code
may have effects elsewhere.

There is no consensus for the definition of a microservice. But, each
can run by its own and tends to have the following characteristics:

-   **Small**: The code that implements the service should be short. Sam
    Newman from O'Reilly states that they should be small enough and no
    smaller. Each should fulfill one business need.
-   **Loosely-coupled**: Developers can update and deploy each service
    independently without affecting others.
-   **In a bounded context**: Each service models real-world domains.
    These models are not shared with other bounded context

In the case of a taxi-hailing app, a microservice can be built for each
business need as shown below. A microservice may be enough for each
green hexagon:

![](https://miro.medium.com/max/700/1*nW7jwz5IEDJu8sWUIJ87NQ.png){height="250"}

\

> Microservice Architecture is about decomposing a Software System into
> autonomus Units which are independently deployable and which
> communicates via lightweight, language agnostic way and together they
> fulfill the business goal.

**Microservice Architecture** also uses the same technique of **divide
and conquer** to tackle the complexity of software systems like Modular
Monolithic architecture where a complex Software system is divided into
many Microservices which communicates via external Interfaces. The key
difference between Modular Monolithic and Microservice Architecture is
that every Microservice can be deployed independently whereas all
Modules usually are deployed as a whole (deployment Monolith). As shown
in the

![](https://miro.medium.com/max/1403/1*Koab_ZShvletO6JaPfyE6Q.jpeg){height="250"}

image above, Monolithic application is one single unit (tightly coupled)
like a single Cube. Modular application is like Rubric Cube which can
contain small modules but the modules cannot be separated and can only
be deployed together. Microservices are like a lego cube made by lego
blocks where the blocks are loosely coupled, easily separable and all
the lego blocks together made the cube.



 {#expander-1224774644 .expand-container}
 {#expander-control-1224774644 .expand-control}
Ideologies underlying microservices


 {#expander-content-1224774644 .expand-content}
The idea of microservices didn't pop up one day, but is rather the
product of a few trends. These trends work to help developers
collaborate and deploy code:

1.  **Domain-driven design**: This is the importance of representing the
    real world in code, harmonizing business logic with development.
    Splitting up an application into microservices will help each team
    follow patterns relevant to their domain.
2.  **Continuous delivery**: This is about improving the efficiency of
    getting code changes to production. As microservices are
    loosely-coupled, developers can deploy them independently.
3.  **Virtualization**: This is about provisioning servers for each
    service at will. Splitting up an application into parts allows one
    to provide more computing power to services with more traffic. This
    would save costs over upgrading servers for an entire monolithic
    application.
4.  **Hexagonal architecture**: This is keeping the input/output at the
    edge of the design of a service. Such a design allows developers to
    switch out different handlers without changing core code.
    Microservices are easy to replace due to their simplicity and size.
5.  **Development through small teams**: This is the idea that small and
    independent teams should be responsible for the entire life-cycles
    of their applications. Large tech firms like Google and Amazon
    popularized this style of development.



 {#expander-983672991 .expand-container}
 {#expander-control-983672991 .expand-control}
Advantages of using microservices


 {#expander-content-983672991 .expand-content}
Along with the benefits conferred from following the above trends, here
are others that microservices bring:

1.  **Technology heterogeneity**: Monolithic apps confine technologies
    that developers can use (eg. database, language). Services allow for
    different technologies, leading to greater optimizations. Developers
    can also use past knowledge of technologies that are not currently
    used by the app.
2.  **Resilience**: It is easier to isolate a problem in a service when
    it fails. As the services don't share many resources, it is likely
    that the rest of the system can continue to function.
3.  **Composability**: Developers can reuse and reconfigure
    microservices in different ways. They may expand or take out
    features without affecting other services too much.

Application Scaling:  {#MicroserviceArchitecture-ApplicationScaling:}
---------------------

Firstly, Microservices are often Stateless and if they are carefully
deployed using **Docker**, **Kubernetes** or using other
Infrastructures, Microservices can offer horizontal Scaling within
seconds.

Development Speed {#MicroserviceArchitecture-DevelopmentSpeed}
-----------------

Microservices are often quite small in size (several hundred to several
thousand). Due to the size, adding new features in Microservices are
usually faster.

Development Scaling {#MicroserviceArchitecture-DevelopmentScaling}
-------------------

Microservices are autonomous and can be developed independently. As a
result, Developer Scalability is much better as different
developers/teams can work on different microservices autonomously
without bumping into each other's code. So, companies can easily hire
more developers and can scale development. Similarly, due to their
sizes, Microservices puts small Cognitive load on newly hired Developers
or fresh graduates and new Developers can normally write productive
codes in a matter of days instead of weeks or months.

Release Cycle {#MicroserviceArchitecture-ReleaseCycle}
-------------

In my opinion, the coolest features of Microservice Architecture is that
every Microservice is independently deployable. As a result, the
Software Release Cycle in Microservice Applications is much smaller and
with **CI/CD**, it is possible to give several releases per day.

Modularization {#MicroserviceArchitecture-Modularization}
--------------

In Microservice Architecture, the boundary between the Microservices are
external Interfaces aka Physical (Network) which is hard to cross. As a
result, correctly designed Microservices often offers the "Loosely
coupled, highly cohesive" Modularization. If we compare Software
Development with society, then Microservice Modulation is like strict
national, international laws with police/punishments. As we know
already, usually strict national, international laws can ensure law and
order in society.

Modernization {#MicroserviceArchitecture-Modernization}
-------------

As Microservices are loosely coupled and only communicate via
language-agnostic way with each other, a single Microservice can easily
be replaced by a new one which can be developed using a new programming
language and Tech Stack without affecting the whole system.
Modernization in Microservice Architecture is incremental and not Big
Bang.



 {#expander-985993206 .expand-container}
 {#expander-control-985993206 .expand-control}
Disadvantages of using microservices


 {#expander-content-985993206 .expand-content}
As like anything in life, Microservice Architecture has also its price
and a fair share of disadvantages. It is by no means a **Golden
Hammer** which can solve all sort of Problems in a Software Application
or in the Organization. It is no surprise that fellow Microservice
expert [***Sam
Newman***](https://twitter.com/origsmartassam?lang=en) has
started his highly acclaimed book "[**Building
Microservices**](https://samnewman.io/books/building_microservices/)"
with a scenario where moving to Microservice Architecture from
Monolithic Architecture without proper architecture/consideration which
leads to the nightmarish condition. There are also some Blog posts like
"[**Goodbye Microservices: From 100s of problem children to 1
superstar**](https://segment.com/blog/goodbye-microservices/)"
or "[**The Death of Microservice Madness in
2018**](https://dwmkerr.com/the-death-of-microservice-madness-in-2018/)"
where the writers discussed the great number of ordeals and pains they
suffered to move from Monolith to Microservice Architecture. Here are
some disadvantages of Microservice Architecture:

-   **Design Complexity**: Monolithic Architecture often gives "One size
    fits for all" solution for Business applications. For example, if a
    Web application is a few thousand lines of Code or several millions
    of lines of Code, Monolithic Architecture gives the same solution
    (Enterprise Java or Ruby on Rails or PHP). But in Microservice
    Architecture, there are many solutions possible depending on the
    applications and use cases. So, if the wrong solution is taken for
    wrong application size/type (e.g. put a kid\'s clothes on a
    full-grown man or vice versa), then Microservice Architecture is
    bound to fail. Also, designing Microservices is challenging as there
    are far more moving parts compared to Monoliths. Usually, a badly
    designed Microservice is worse than a Monolith.
-   **Distributed Systems Complexity: **Microservices are often
    distributed system and we know that Distributed Systems are complex
    and has a unique set of challenges compared to single Machine
    systems. A detailed discussion of Distributed systems is out of the
    scope of this article but interested readers can read "[**The
    Fallacies of Distributed
    Systems**](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing)".
    In short, the following problems can arise in Distributed
    Microservices: ***Overall System latency is higher, Network failure
    or Individual Node failure can bring the whole system down,
    Operational complexities are higher***.
-   **Operational Complexity**: Once the complex Monolithic application
    is decomposed into many Microservices, the complexity often moves
    from source code to operations. Simple operations like Logging,
    Monitoring became more complex because instead of one Systems, many
    more Systems need to be handled. Often, the existing
    Logging/Monitoring tool does not fit with Microservices and new
    Logging, Monitoring tools are needed. Tracing is also very important
    in Microservices to measure the performance/latency of individual
    Microservices for a Service Request. The complete System test is
    likewise quite complex in Microservices compared to Monolithic
    Applications. Likewise, new Infrastructures are needed for Service
    Discovery, Resiliency. As renowned Computer Scientist and
    Microservice Guru [***Martin
    Fowler***](https://martinfowler.com/) have pointed
    out, the initial Development Velocity of Microservice Architecture
    is lower compared to Monolithic Architecture due to the Operational
    Complexities.

![](https://miro.medium.com/max/937/1*MrDMARKuvUCZliIvT5XtGg.png){height="250"}

-   **Security:** Security in Software Systems is often the Elephant in
    the Room what everybody can see but nobody wants to talk about.
    Securing one Software Application is hard, securing hundreds of
    Microservices which are often Distributed Systems is quite a
    challenge.
-   **Data Sharing and Data Consistency: **Ideally, every Microservice
    should have its own Data Store. The downside is that the
    Microservices need to share data between themselves to fulfill the
    Business goal. Data consistency is another challenge because the
    classical [**Two Phase
    Locking**](https://en.wikipedia.org/wiki/Two-phase_locking) to
    support consistency in the distributed databases is not recommended
    for two reasons: It does not Scale and many Modern Data Store does
    not support it. Most of the modern [**NoSQL
    Databases**](https://en.wikipedia.org/wiki/NoSQL) only
    offers [**Eventual
    Consistency**](https://en.wikipedia.org/wiki/Eventual_consistency) which
    needs careful design.
-   **Communication Complexities:** As already discussed, Microservices
    achieves strict modularity and development autonomy via
    process/network boundaries. The downside is that the services can
    only communicate via the physical network which eventually leads to
    higher network latency. There are many ways Microservices can
    communicate with each other: **Synchronous
    Communication** using [**REST**](https://en.wikipedia.org/wiki/Representational_state_transfer), [**gRPC **](https://en.wikipedia.org/wiki/GRPC)or **Asynchronous
    Communication** using [**Message
    Queue**](https://en.wikipedia.org/wiki/Message_queue), [**Message
    Broker**](https://en.wikipedia.org/wiki/Message_broker) where
    each of them has Pros and Cons. Synchronous communication is easier
    to implement but can lead to the so-called D**istributed Monolith**.
    Asynchronous Communication via Messaging gives more flexibility with
    the price of higher implementational complexity. Choosing the right
    Communication mechanism depending on the application is also
    challenging in Microservice Architecture.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Considerations**


 {.panelContent}
When switching to microservices, there are two main areas of design
considerations:

**On the design of microservices**:

-   What microservices are needed for the application?
-   How will data be shared between microservices?

**On the availability and resilience of a distributed system**:

-   How will you handle new problems arising from networked services,
    such as latency and durability of data?
-   What sort of stops and checks (eg. timeouts and circuit-breakers)
    will you need when a microservice goes down?
-   As opposed to a few measures (eg. CPU and memory usage) used to
    monitor a server supporting one monolithic app, how will you monitor
    50--100 processes at the same time and gauge the health of the app?

\

 {#expander-1600424832 .expand-container}
 {#expander-control-1600424832 .expand-control}
When to use the microservice architecture?


 {#expander-content-1600424832 .expand-content}
Author: [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

\

One challenge with using this approach is deciding when it makes sense
to use it. When developing the first version of an application, you
often do not have the problems that this approach solves. Moreover,
using an elaborate, distributed architecture will slow down development.
This can be a major problem for startups whose biggest challenge is
often how to rapidly evolve the business model and accompanying
application. Using Y-axis splits might make it much more difficult to
iterate rapidly. Later on, however, when the challenge is how to scale
and you need to use functional decomposition, the tangled dependencies
might make it difficult to decompose your monolithic application into a
set of services.

 {#expander-1748403512 .expand-container}
 {#expander-control-1748403512 .expand-control}
Constraints Imposed by Microservice Style


 {#expander-content-1748403512 .expand-content}
By adhering to the following constraints imposed by microservice
architecture style, what we get is a system where services can be
deployed independently, faults are isolated, frequent updates are
possible and it's easy to introduce new technologies into the
application.

-   Each service represents a single responsibility.
-   Every service is independent of the others.
-   Each service needs its own JVM (or equivalent) so instances are
    isolated.
-   Data is private to the service that owns it.
-   Services do not share data and need to implement queries that need
    to retrieve data owned by multiple services.
-   Well defined mechanism to implement service-to-service communication
    and scheme to deal with partial failure.
-   Requests that span multiple services and require careful
    coordination between the teams.
-   Testing to cover the interactions between services.
-   Deploying and managing a system comprised of many different
    services.



 {#expander-1033808973 .expand-container}
 {#expander-control-1033808973 .expand-control}
Consider Challenges Versus Benefits


 {#expander-content-1033808973 .expand-content}
Each architectural constraint has its own associated
challenges/benefits, so it's important to understand and balance both.
Before adopting any style of architecture, you have to ask yourself if
the benefits outweigh the challenges for the application you are
considering.

In the table below, we take a look at the benefits versus challenges of
microservice style applications.

 {.table-wrap}
+----------------------------------+----------------------------------+
| **Benefits**                     | **Challenges**                   |
+==================================+==================================+
| Enables the continuous delivery  | There is an additional           |
| and deployment of large, complex | complexity of creating a         |
| applications.                    | distributed system.              |
+----------------------------------+----------------------------------+
| Improved maintainability: Each   | Implementing requests that span  |
| service is relatively small so   | multiple services is more        |
| it's easier to understand and    | difficult.                       |
| change.                          |                                  |
|                                  | Maintaining data consistency     |
|                                  | between service(s) is a          |
|                                  | challenge.                       |
+----------------------------------+----------------------------------+
| Better Testability: services are | Testing the interactions between |
| smaller and faster to test.      | services is more difficult.      |
+----------------------------------+----------------------------------+
| Better deployability: services   | Increased operational and        |
| can be deployed independently.   | deployment complexity of         |
|                                  | deploying and managing a system  |
|                                  | comprised of many different      |
|                                  | services.                        |
+----------------------------------+----------------------------------+
| Each team can develop, test,     | Implementing requests that span  |
| deploy and scale their services  | multiple services requires       |
| independently of all of the      | careful coordination between the |
| other teams.                     | teams.                           |
+----------------------------------+----------------------------------+
| Improved fault isolation.        | Inter-service communication and  |
|                                  | dealing with partial failure     |
|                                  | implementation is challenging.   |
+----------------------------------+----------------------------------+
| Eliminates long-term commitment  | Overhead of multiple JVM         |
| to a technology stack.           | runtimes (or equivalent) and     |
|                                  | increase in memory consumption   |
|                                  | needs to be taken care of.       |
+----------------------------------+----------------------------------+




 {#expander-1914198527 .expand-container}
 {#expander-control-1914198527 .expand-control}
Scenarios Where You Can Consider Going for Microservice


 {#expander-content-1914198527 .expand-content}
Consider an scenario where you are developing an enterprise application
that must support the following characteristics:

-   Support for different variety of clients that includes desktop
    browsers, mobile browsers and native mobile applications.
-   Expose an API for third parties to consume.
-   Integration with other applications via web services or a message
    broker.
-   Run multiple instances of the application on multiple machines to
    fulfill scalability and availability NFR requirements.
-   Adopt emerging technology stack.
-   Planning to go for continuous deployment pipeline setup for the
    application.

From the requirements above, you can very well say the application is
100% fit for a microservices architecture.

You have to define an architecture that structures the application as a
set of loosely coupled, collaborating services. Services can communicate
using either synchronous or asynchronous protocols. Services can be
developed and deployed independently of one another. Each service has
its own database in order to be decoupled from other services.

Let's look at some of the typical scenarios where you can consider going
for microservice style of architecture:

1.  Monolithic application migration due to improvements needed in
    scalability, manageability, agility or speed of delivery.
2.  Re-platform a legacy application by transforming functions/modules
    to microservices.
3.  Rewriting legacy application to modern languages, technology stack
    to meet the demands of modern business.
4.  Individual cross-cutting services that are independent in nature.
    For example: encryption services, authentication services, etc.
5.  Independent business applications or services reused across multiple
    channels. For example, payment services, login services, flight
    search services, customer profile services, notification services,
    etc.
6.  Commonly used enterprise applications. For example, time tracking
    application.
7.  Scenarios where a service provider makes computing resources and
    infrastructure management available to the customer as needed. For
    example, forecasting services, price calculation services,
    prediction services, etc.
8.  Back-end services for responsive client-side web application where
    data could be coming from multiple channels or different data
    sources.
9.  Highly agile applications or applications demanding speed of
    delivery or time to market or innovation pilots, etc.
10. Applications that got polyglot, multi-language, cloud application
    development.





 {#expander-1741309332 .expand-container}
 {#expander-control-1741309332 .expand-control}
How to maintain data consistency?


 {#expander-content-1741309332 .expand-content}
In order to ensure loose coupling, each service has its own database.
Maintaining data consistency between services is a challenge because 2
phase-commit/distributed transactions is not an option for many
applications. An application must instead use the [Saga
pattern](https://microservices.io/patterns/data/saga.html).
A service publishes an event when its data changes. Other services
consume that event and update their data. There are several ways of
reliably updating data and publishing events including [Event
Sourcing](https://microservices.io/patterns/data/event-sourcing.html) and [Transaction
Log
Tailing](https://microservices.io/patterns/data/transaction-log-tailing.html).



 {#expander-1185566672 .expand-container}
 {#expander-control-1185566672 .expand-control}
How to implement queries?


 {#expander-content-1185566672 .expand-content}
Another challenge is implementing queries that need to retrieve data
owned by multiple services.

-   The [API
    Composition](https://microservices.io/patterns/data/api-composition.html) and [Command
    Query Responsibility Segregation
    (CQRS)](https://microservices.io/patterns/data/cqrs.html) patterns.





 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Decomposition Patterns**


 {.panelContent}
How to decompose the application into services? {#MicroserviceArchitecture-Howtodecomposetheapplicationintoservices?}
-----------------------------------------------

Another challenge is deciding how to partition the system into
microservices. This is very much an art, but there are a number of
strategies that can help:

-   [Decompose by business
    capability](https://microservices.io/patterns/decomposition/decompose-by-business-capability.html) and
    define services corresponding to business capabilities.
-   [Decompose by domain-driven design
    subdomain](https://microservices.io/patterns/decomposition/decompose-by-subdomain.html).
-   Decompose by verb or use case and define services that are
    responsible for particular actions. e.g.
    a `Shipping Service`{.highlighter-rouge} that's responsible for
    shipping complete orders.
-   Decompose by by nouns or resources by defining a service that is
    responsible for all operations on entities/resources of a given
    type. e.g. an `Account Service`{.highlighter-rouge} that is
    responsible for managing user accounts.

Ideally, each service should have only a small set of responsibilities.
(Uncle) Bob Martin talks about designing classes using the [Single
Responsibility Principle
(SRP)](http://www.objectmentor.com/resources/articles/srp.pdf).
The SRP defines a responsibility of a class as a reason to change, and
states that a class should only have one reason to change. It make sense
to apply the SRP to service design as well.

Another analogy that helps with service design is the design of Unix
utilities. Unix provides a large number of utilities such as grep, cat
and find. Each utility does exactly one thing, often exceptionally well,
and can be combined with other utilities using a shell script to perform
complex tasks.

 {#expander-1697173609 .expand-container}
 {#expander-control-1697173609 .expand-control}
Decompose by business capability


 {#expander-content-1697173609 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

\

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You are developing a large, complex application and want to use
the [microservice
architecture](https://microservices.io/patterns/microservices.html).
The microservice architecture structures an application as a set of
loosely coupled services. The goal of the microservice architecture is
to accelerate software development by enabling continuous
delivery/deployment.

![](https://microservices.io/i/successtriangle.png){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}

The microservice architecture does this in two ways:

1.  Simplifies testing and enables components to deployed independently
2.  Structures the engineering organization as a collection of small
    (6-10 members), autonomous teams, each of which is responsible for
    one or more services

These benefits are not automatically guaranteed. Instead, they can only
be achieved by the careful functional decomposition of the application
into services.

A service must be small enough to be developed by a small team and to be
easily tested. A useful guideline from object-oriented design (OOD) is
the Single Responsibility Principle
([SRP](http://www.objectmentor.com/resources/articles/srp.pdf)).
The SRP defines a responsibility of a class as a reason to change, and
states that a class should only have one reason to change. It make sense
to apply the SRP to service design as well and design services that are
cohesive and implement a small set of strongly related functions.

The application also be decomposed in a way so that most new and changed
requirements only affect a single service. That is because changes that
affect multiple services requires coordination across multiple teams,
which slows down development. Another useful principle from OOD is the
Common Closure Principle (CCP), which states that classes that change
for the same reason should be in the same package. Perhaps, for
instance, two classes implement different aspects of the same business
rule. The goal is that when that business rule changes developers, only
need to change code in a small number - ideally only one - of packages.
This kind of thinking makes sense when designing services since it will
help ensure that each change should impact only one service.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to decompose an application into services?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   The architecture must be stable
-   Services must be cohesive. A service should implement a small set of
    strongly related functions.
-   Services must conform to the Common Closure Principle - things that
    change together should be packaged together - to ensure that each
    change affect only one service
-   Services must be loosely coupled - each service as an API that
    encapsulates its implementation. The implementation can be changed
    without affecting clients
-   A service should be testable
-   Each service be small enough to be developed by a "two pizza" team,
    i.e. a team of 6-10 people
-   Each team that owns one or more services must be autonomous. A team
    must be able to develop and deploy their services with minimal
    collaboration with other teams.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Define services corresponding to business capabilities. A business
capability is a concept from business architecture modeling. It is
something that a business does in order to generate value. A business
capability often corresponds to a business object, e.g.

-   *Order Management* is responsible for orders
-   *Customer Management* is responsible for customers

Business capabilities are often organized into a multi-level hierarchy.
For example, an enterprise application might have top-level categories
such as *Product/Service development*, *Product/Service
delivery*, *Demand generation*, etc.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
The business capabilities of an online store include:

-   Product catalog management
-   Inventory management
-   Order management
-   Delivery management
-   ...

The corresponding microservice architecture would have services
corresponding to each of these capabilities.

![](https://microservices.io/i/decompose-by-business-capability.png){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
This pattern has the following benefits:

-   Stable architecture since the business capabilities are relatively
    stable
-   Development teams are cross-functional, autonomous, and organized
    around delivering business value rather than technical features
-   Services are cohesive and loosely coupled



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Issues**


 {.panelContent}
There are the following issues to address:

-   **How to identify business capabilities?** Identifying business
    capabilities and hence services requires an understanding of the
    business. An organization's business capabilities are identified by
    analyzing the organization's purpose, structure, business processes,
    and areas of expertise. Bounded contexts are best identified using
    an iterative process. Good starting points for identifying business
    capabilities are:

    -   organization structure - different groups within an organization
        might correspond to business capabilities or business capability
        groups.
    -   high-level domain model - business capabilities often correspond
        to domain objects





 {#expander-1069641233 .expand-container}
 {#expander-control-1069641233 .expand-control}
Decompose by subdomain


 {#expander-content-1069641233 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You are developing a large, complex application and want to use
the [microservice
architecture](https://microservices.io/patterns/microservices.html).
The microservice architecture structures an application as a set of
loosely coupled services. The goal of the microservice architecture is
to accelerate software development by enabling continuous
delivery/deployment.

![](https://microservices.io/i/successtriangle.png){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}

The microservice architecture does this in two ways:

1.  Simplifies testing and enables components to deployed independently
2.  Structures the engineering organization as a collection of small
    (6-10 members), autonomous teams, each of which is responsible for
    one or more services

These benefits are not automatically guaranteed. Instead, they can only
be achieved by the careful functional decomposition of the application
into services.

A service must be small enough to be developed by a small team and to be
easily tested. A useful guideline from object-oriented design (OOD) is
the Single Responsibility Principle
([SRP](http://www.objectmentor.com/resources/articles/srp.pdf)).
The SRP defines a responsibility of a class as a reason to change, and
states that a class should only have one reason to change. It make sense
to apply the SRP to service design as well and design services that are
cohesive and implement a small set of strongly related functions.

The application also be decomposed in a way so that most new and changed
requirements only affect a single service. That is because changes that
affect multiple services requires coordination across multiple teams,
which slows down development. Another useful principle from OOD is the
Common Closure Principle (CCP), which states that classes that change
for the same reason should be in the same package. Perhaps, for
instance, two classes implement different aspects of the same business
rule. The goal is that when that business rule changes developers, only
need to change code in a small number - ideally only one - of packages.
This kind of thinking makes sense when designing services since it will
help ensure that each change should impact only one service.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to decompose an application into services?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   The architecture must be stable
-   Services must be cohesive. A service should implement a small set of
    strongly related functions.
-   Services must conform to the Common Closure Principle - things that
    change together should be packaged together - to ensure that each
    change affect only one service
-   Services must be loosely coupled - each service as an API that
    encapsulates its implementation. The implementation can be changed
    without affecting clients
-   A service should be testable
-   Each service be small enough to be developed by a "two pizza" team,
    i.e. a team of 6-10 people
-   Each team that owns one or more services must be autonomous. A team
    must be able to develop and deploy their services with minimal
    collaboration with other teams.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Define services corresponding to Domain-Driven Design (DDD) subdomains.
DDD refers to the application's problem space - the business - as the
domain. A domain is consists of multiple subdomains. Each subdomain
corresponds to a different part of the business.

Subdomains can be classified as follows:

-   Core - key differentiator for the business and the most valuable
    part of the application
-   Supporting - related to what the business does but not a
    differentiator. These can be implemented in-house or outsourced.
-   Generic - not specific to the business and are ideally implemented
    using off the shelf software



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
The subdomains of an online store include:

-   Product catalog
-   Inventory management
-   Order management
-   Delivery management
-   ...

The corresponding microservice architecture would have services
corresponding to each of these subdomains.

![](https://microservices.io/i/decompose-by-subdomain.png){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
This pattern has the following benefits:

-   Stable architecture since the subdomains are relatively stable
-   Development teams are cross-functional, autonomous, and organized
    around delivering business value rather than technical features
-   Services are cohesive and loosely coupled



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Issues**


 {.panelContent}
There are the following issues to address:

-   **How to identify the subdomains?** Identifying subdomains and hence
    services requires an understanding of the business. Like business
    capabilities, subdomains are identified by analyzing the business
    and its organizational structure and identifying the different areas
    of expertise. Subdomains are best identified using an iterative
    process. Good starting points for identifying subdomains are:

-   organization structure - different groups within an organization
    might correspond to subdomains

-   high-level domain model - subdomains often have a key domain object







 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Database**


 {.panelContent}
 {#expander-167008903 .expand-container}
 {#expander-control-167008903 .expand-control}
Database per Service Pattern


 {#expander-content-167008903 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
Let's imagine you are developing an online store application using
the [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html).
Most services need to persist data in some kind of database. For
example, the `Order Service`{.highlighter-rouge} stores information
about orders and the `Customer Service`{.highlighter-rouge} stores
information about customers.

![](https://microservices.io/i/customersandorders.png){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
What's the database architecture in a microservices application?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   Services must be loosely coupled so that they can be developed,
    deployed and scaled independently

-   Some business transactions must enforce invariants that span
    multiple services. For example,
    the `Place Order`{.highlighter-rouge} use case must verify that a
    new Order will not exceed the customer's credit limit. Other
    business transactions, must update data owned by multiple services.

-   Some business transactions need to query data that is owned by
    multiple services. For example,
    the `View Available Credit`{.highlighter-rouge} use must query the
    Customer to find the `creditLimit`{.highlighter-rouge} and Orders to
    calculate the total amount of the open orders.

-   Some queries must join data that is owned by multiple services. For
    example, finding customers in a particular region and their recent
    orders requires a join between customers and orders.

-   Databases must sometimes be replicated and sharded in order to
    scale. See the [Scale
    Cube](https://microservices.io/articles/scalecube.html).

-   Different services have different data storage requirements. For
    some services, a relational database is the best choice. Other
    services might need a NoSQL database such as MongoDB, which is good
    at storing complex, unstructured data, or Neo4J, which is designed
    to efficiently store and query graph data.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Keep each microservice's persistent data private to that service and
accessible only via its API. A service's transactions only involve its
database.

The following diagram shows the structure of this pattern.

![](https://microservices.io/i/databaseperservice.png){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}

The service's database is effectively part of the implementation of that
service. It cannot be accessed directly by other services.

There are a few different ways to keep a service's persistent data
private. You do not need to provision a database server for each
service. For example, if you are using a relational database then the
options are:

-   Private-tables-per-service -- each service owns a set of tables that
    must only be accessed by that service
-   Schema-per-service -- each service has a database schema that's
    private to that service
-   Database-server-per-service -- each service has it's own database
    server.

Private-tables-per-service and schema-per-service have the lowest
overhead. Using a schema per service is appealing since it makes
ownership clearer. Some high throughput services might need their own
database server.

It is a good idea to create barriers that enforce this modularity. You
could, for example, assign a different database user id to each service
and use a database access control mechanism such as grants. Without some
kind of barrier to enforce encapsulation, developers will always be
tempted to bypass a service's API and access it's data directly.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
The [FTGO
application](https://chrisrichardson.net/post/microservices/patterns/data/2019/07/15/ftgo-database-per-service.html) is
an example of an application that uses this approach. Each service has
database credentials that only grant it access its own (logical)
database on a shared MySQL server. For more information, see this [blog
post](https://chrisrichardson.net/post/microservices/patterns/data/2019/07/15/ftgo-database-per-service.html).



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
Using a database per service has the following benefits:

-   Helps ensure that the services are loosely coupled. Changes to one
    service's database does not impact any other services.

-   Each service can use the type of database that is best suited to its
    needs. For example, a service that does text searches could use
    ElasticSearch. A service that manipulates a social graph could use
    Neo4j.

Using a database per service has the following drawbacks:

-   Implementing business transactions that span multiple services is
    not straightforward. Distributed transactions are best avoided
    because of the CAP theorem. Moreover, many modern (NoSQL) databases
    don't support them.

-   Implementing queries that join data that is now in multiple
    databases is challenging.

-   Complexity of managing multiple SQL and NoSQL databases

There are various patterns/solutions for implementing transactions and
queries that span services:

-   Implementing transactions that span services - use the [Saga
    pattern](https://microservices.io/patterns/data/saga.html).

-   Implementing queries that span services:

    -   [API
        Composition](https://microservices.io/patterns/data/api-composition.html) -
        the application performs the join rather than the database. For
        example, a service (or the API gateway) could retrieve a
        customer and their orders by first retrieving the customer from
        the customer service and then querying the order service to
        return the customer's most recent orders.

    -   [Command Query Responsibility Segregation
        (CQRS)](https://microservices.io/patterns/data/cqrs.html) -
        maintain one or more materialized views that contain data from
        multiple services. The views are kept by services that subscribe
        to events that each services publishes when it updates its data.
        For example, the online store could implement a query that finds
        customers in a particular region and their recent orders by
        maintaining a view that joins customers and orders. The view is
        updated by a service that subscribes to customer and order
        events.





 {#expander-797004229 .expand-container}
 {#expander-control-797004229 .expand-control}
Shared Database


 {#expander-content-797004229 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
Let's imagine you are developing an online store application using
the [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html).
Most services need to persist data in some kind of database. For
example, the `Order Service`{.highlighter-rouge} stores information
about orders and the `Customer Service`{.highlighter-rouge} stores
information about customers.

![](https://microservices.io/i/customersandorders.png){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="150"}



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
What's the database architecture in a microservices application?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   Services must be loosely coupled so that they can be developed,
    deployed and scaled independently

-   Some business transactions must enforce invariants that span
    multiple services. For example,
    the `Place Order`{.highlighter-rouge} use case must verify that a
    new Order will not exceed the customer's credit limit. Other
    business transactions, must update data owned by multiple services.

-   Some business transactions need to query data that is owned by
    multiple services. For example,
    the `View Available Credit`{.highlighter-rouge} use must query the
    Customer to find the `creditLimit`{.highlighter-rouge} and Orders to
    calculate the total amount of the open orders.

-   Some queries must join data that is owned by multiple services. For
    example, finding customers in a particular region and their recent
    orders requires a join between customers and orders.

-   Databases must sometimes be replicated and sharded in order to
    scale. See the [Scale
    Cube](https://microservices.io/articles/scalecube.html).

-   Different services have different data storage requirements. For
    some services, a relational database is the best choice. Other
    services might need a NoSQL database such as MongoDB, which is good
    at storing complex, unstructured data, or Neo4J, which is designed
    to efficiently store and query graph data.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Use a (single) database that is shared by multiple services. Each
service freely accesses data owned by other services using local ACID
transactions.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
\



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Related Context**


 {.panelContent}
The benefits of this pattern are:

-   A developer uses familiar and straightforward ACID transactions to
    enforce data consistency
-   A single database is simpler to operate

The drawbacks of this pattern are:

-   Development time coupling - a developer working on, for example,
    the `OrderService`{.highlighter-rouge} will need to coordinate
    schema changes with the developers of other services that access the
    same tables. This coupling and additional coordination will slow
    down development.

-   Runtime coupling - because all services access the same database
    they can potentially interfere with one another. For example, if
    long running `CustomerService`{.highlighter-rouge} transaction holds
    a lock on the `ORDER`{.highlighter-rouge} table then
    the `OrderService`{.highlighter-rouge} will be blocked.

-   Single database might not satisfy the data storage and access
    requirements of all services.





 {#expander-533675 .expand-container}
 {#expander-control-533675 .expand-control}
Sagas


 {#expander-content-533675 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Database per
Service](https://microservices.io/patterns/data/database-per-service.html) pattern.
Each service has its own database. Some business transactions, however,
span multiple service so you need a mechanism to ensure data consistency
across services. For example, lets imagine that you are building an
e-commerce store where customers have a credit limit. The application
must ensure that a new order will not exceed the customer's credit
limit. Since Orders and Customers are in different databases the
application cannot simply use a local ACID transaction.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to maintain data consistency across services?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   2PC is not an option



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Implement each business transaction that spans multiple services as a
saga. A saga is a sequence of local transactions. Each local transaction
updates the database and publishes a message or event to trigger the
next local transaction in the saga. If a local transaction fails because
it violates a business rule then the saga executes a series of
compensating transactions that undo the changes that were made by the
preceding local transactions.

![](https://microservices.io/i/data/saga.jpg){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
There are two ways of coordination sagas:

-   Choreography - each local transaction publishes domain events that
    trigger local transactions in other services
-   Orchestration - an orchestrator (object) tells the participants what
    local transactions to execute

Example: Choreography-based saga {#MicroserviceArchitecture-Example:Choreography-basedsaga}
--------------------------------

![](https://microservices.io/i/data/Saga_Choreography_Flow.001.jpeg){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}

An e-commerce application that uses this approach would create an order
using a choreography-based saga that consists of the following steps:

1.  The `Order Service`{.highlighter-rouge} creates an Order in
    a *pending* state and publishes
    an `OrderCreated`{.highlighter-rouge} event
2.  The `Customer Service`{.highlighter-rouge} receives the event
    attempts to reserve credit for that Order. It publishes either
    a `Credit Reserved`{.highlighter-rouge} event or
    a `CreditLimitExceeded`{.highlighter-rouge} event.
3.  The `Order Service`{.highlighter-rouge} receives the event and
    changes the state of the order to either *approved* or *cancelled*

Example: Orchestration-based saga {#MicroserviceArchitecture-Example:Orchestration-basedsaga}
---------------------------------

![](https://microservices.io/i/data/Saga_Orchestration_Flow.001.jpeg){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}

An e-commerce application that uses this approach would create an order
using an orchestration-based saga that consists of the following steps:

1.  The `Order Service`{.highlighter-rouge} creates an Order in
    a *pending* state and creates
    a `CreateOrderSaga`{.highlighter-rouge}
2.  The `CreateOrderSaga`{.highlighter-rouge} sends
    a `ReserveCredit`{.highlighter-rouge} command to
    the `Customer Service`{.highlighter-rouge}
3.  The `Customer Service`{.highlighter-rouge} attempts to reserve
    credit for that Order and sends back a reply
4.  The `CreateOrderSaga`{.highlighter-rouge} receives the reply and
    sends either
    an `ApproveOrder`{.highlighter-rouge} or `RejectOrder`{.highlighter-rouge} command
    to the `Order Service`{.highlighter-rouge}
5.  The `Order Service`{.highlighter-rouge} changes the state of the
    order to either *approved* or *cancelled*



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
This pattern has the following benefits:

-   It enables an application to maintain data consistency across
    multiple services without using distributed transactions

This solution has the following drawbacks:

-   The programming model is more complex. For example, a developer must
    design compensating transactions that explicitly undo changes made
    earlier in a saga.

There are also the following issues to address:

-   In order to be reliable, a service must atomically update its
    database *and* publish a message/event. It cannot use the
    traditional mechanism of a distributed transaction that spans the
    database and the message broker. Instead, it must use one of the
    patterns listed below.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Related Patterns**


 {.panelContent}
-   The [Database per Service
    pattern](https://microservices.io/patterns/data/database-per-service.html) creates
    the need for this pattern
-   The following patterns are ways to *atomically* update
    state *and* publish messages/events:
    -   [Event
        sourcing](https://microservices.io/patterns/data/event-sourcing.html)
    -   [Transactional
        Outbox](https://microservices.io/patterns/data/transactional-outbox.html)
-   A choreography-based saga can publish events
    using [Aggregates](https://microservices.io/patterns/data/aggregate.html) and [Domain
    Events](https://microservices.io/patterns/data/domain-event.html)





 {#expander-889139528 .expand-container}
 {#expander-control-889139528 .expand-control}
Command Query Responsibility Segregation (CQRS)


 {#expander-content-889139528 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservices architecture
pattern](https://microservices.io/patterns/microservices.html) and
the [Database per service
pattern](https://microservices.io/patterns/data/database-per-service.html).
As a result, it is no longer straightforward to implement queries that
join data from multiple services. Also, if you have applied the [Event
sourcing
pattern](https://microservices.io/patterns/data/event-sourcing.html) then
the data is no longer easily queried.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to implement a query that retrieves data from multiple services in a
microservice architecture?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Define a view database, which is a read-only replica that is designed to
support that query. The application keeps the replica up to data by
subscribing to [Domain
events](https://microservices.io/patterns/data/domain-event.html) published
by the service that own the data.

![](https://microservices.io/i/patterns/data/QuerySideService.png){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
-   My book's FTGO example application has
    the [`Order History Service`{.highlighter-rouge}](https://github.com/microservices-patterns/ftgo-application#chapter-7-implementing-queries-in-a-microservice-architecture),
    which implements this pattern.

-   There are [several Eventuate-based example
    applications](http://eventuate.io/exampleapps.html) that
    illustrate how to use this pattern.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
This pattern has the following benefits:

-   Supports multiple denormalized views that are scalable and
    performant
-   Improved separation of concerns = simpler command and query models
-   Necessary in an event sourced architecture

This pattern has the following drawbacks:

-   Increased complexity
-   Potential code duplication
-   Replication lag/eventually consistent views



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Related Patterns**


 {.panelContent}
-   The [Database per Service
    pattern](https://microservices.io/patterns/data/database-per-service.html) creates
    the need for this pattern
-   The [API Composition
    pattern](https://microservices.io/patterns/data/api-composition.html) is
    an alternative solution
-   The [Domain
    event](https://microservices.io/patterns/data/domain-event.html) pattern
    generates the events
-   CQRS is often used with [Event
    sourcing](https://microservices.io/patterns/data/event-sourcing.html)







 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**API Gateway Pattern**


 {.panelContent}
 {#expander-1792453142 .expand-container}
 {#expander-control-1792453142 .expand-control}
Gatewapy API


 {#expander-content-1792453142 .expand-content}
Author: [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Overview
--------


 {.panelContent}
Use a gateway to aggregate multiple individual requests into a single
request. This pattern is useful when a client must make multiple calls
to different backend systems to perform an operation.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context and Problem
-------------------


 {.panelContent}
To perform a single task, a client may have to make multiple calls to
various backend services. An application that relies on many services to
perform a task must expend resources on each request. When any new
feature or service is added to the application, additional requests are
needed, further increasing resource requirements and network calls. This
chattiness between a client and a backend can adversely impact the
performance and scale of the application. Microservice architectures
have made this problem more common, as applications built around many
smaller services naturally have a higher amount of cross-service calls.

In the following diagram, the client sends requests to each service
(1,2,3). Each service processes the request and sends the response back
to the application (4,5,6). Over a cellular network with typically high
latency, using individual requests in this manner is inefficient and
could result in broken connectivity or incomplete requests. While each
request may be done in parallel, the application must send, wait, and
process data for each request, all on separate connections, increasing
the chance of failure.

![](attachments/463533350/463533348.png){.confluence-embedded-image
.confluence-thumbnail .confluence-content-image-border height="150"}

\



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Use a gateway to reduce chattiness between the client and the services.
The gateway receives client requests, dispatches requests to the various
backend systems, and then aggregates the results and sends them back to
the requesting client.

This pattern can reduce the number of requests that the application
makes to backend services, and improve application performance over
high-latency networks.

In the following diagram, the application sends a request to the gateway
(1). The request contains a package of additional requests. The gateway
decomposes these and processes each request by sending it to the
relevant service (2). Each service returns a response to the gateway
(3). The gateway combines the responses from each service and sends the
response to the application (4). The application makes a single request
and receives only a single response from the gateway.

![](attachments/463533350/463533349.png){.confluence-embedded-image
.confluence-thumbnail .confluence-content-image-border
height="150"}![New-API-GW-Diagram](https://d1.awsstatic.com/serverless/New-API-GW-Diagram.c9fc9835d2a9aa00ef90d0ddc4c6402a2536de0d.png){height="150"}![](https://microservices.io/i/apigateway.jpg){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border
height="150"}![](attachments/463533350/463533529.png){.confluence-embedded-image
.confluence-thumbnail .confluence-content-image-border
height="150"}![](attachments/463533350/463533530.png){.confluence-embedded-image
.confluence-content-image-border
height="150"}![](https://microservices.io/i/bffe.png){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="150"}

\

Using an API gateway has the following benefits {#MicroserviceArchitecture-UsinganAPIgatewayhasthefollowingbenefits}
-----------------------------------------------

-   Insulates the clients from how the application is partitioned into
    microservices
-   Insulates the clients from the problem of determining the locations
    of service instances
-   Provides the optimal API for each client
-   Reduces the number of requests/roundtrips. For example, the API
    gateway enables clients to retrieve data from multiple services with
    a single round-trip. Fewer requests also means less overhead and
    improves the user experience. An API gateway is essential for mobile
    applications.
-   Simplifies the client by moving logic for calling multiple services
    from the client to API gateway
-   Translates from a "standard" public web-friendly API protocol to
    whatever protocols are used internally



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Issues and Considerations
-------------------------


 {.panelContent}
-   The gateway should not introduce service coupling across the backend
    services.
-   The gateway should be located near the backend services to reduce
    latency as much as possible.
-   The gateway service may introduce a single point of failure. Ensure
    the gateway is properly designed to meet your application\'s
    availability requirements.
-   The gateway may introduce a bottleneck. Ensure the gateway has
    adequate performance to handle load and can be scaled to meet your
    anticipated growth.
-   Perform load testing against the gateway to ensure you don\'t
    introduce cascading failures for services.
-   Implement a resilient design, using techniques such
    as [bulkheads](https://docs.microsoft.com/en-us/azure/architecture/patterns/bulkhead), [circuit
    breaking](https://docs.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker), [retry](https://docs.microsoft.com/en-us/azure/architecture/patterns/retry),
    and timeouts.
-   If one or more service calls takes too long, it may be acceptable to
    timeout and return a partial set of data. Consider how your
    application will handle this scenario.
-   Use asynchronous I/O to ensure that a delay at the backend doesn\'t
    cause performance issues in the application.
-   Implement distributed tracing using correlation IDs to track each
    individual call.
-   Monitor request metrics and response sizes.
-   Consider returning cached data as a failover strategy to handle
    failures.
-   Instead of building aggregation into the gateway, consider placing
    an aggregation service behind the gateway. Request aggregation will
    likely have different resource requirements than other services in
    the gateway and may impact the gateway\'s routing and offloading
    functionality.
-   How implement the API gateway? An event-driven/reactive approach is
    best if it must scale to scale to handle high loads. On the JVM,
    NIO-based libraries such as Netty, Spring Reactor, etc. make sense.
    NodeJS is another option.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
When to use this Pattern
------------------------


 {.panelContent}
Use this pattern when:

-   A client needs to communicate with multiple backend services to
    perform an operation.
-   The client may use networks with significant latency, such as
    cellular networks.

This pattern may not be suitable when:

-   You want to reduce the number of calls between a client and a single
    service across multiple operations. In that scenario, it may be
    better to add a batch operation to the service.
-   The client or application is located near the backend services and
    latency is not a significant factor.







 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Service Discovery**


 {.panelContent}
 {#expander-1506449518 .expand-container}
 {#expander-control-1506449518 .expand-control}
Client Side


 {#expander-content-1506449518 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
Services typically need to call one another. In a monolithic
application, services invoke one another through language-level method
or procedure calls. In a traditional distributed system deployment,
services run at fixed, well known locations (hosts and ports) and so can
easily call one another using HTTP/REST or some RPC mechanism. However,
a
modern [microservice-based](https://microservices.io/patterns/microservices.html) application
typically runs in a virtualized or containerized environments where the
number of instances of a service and their locations changes
dynamically.

![](https://microservices.io/i/servicediscovery/discovery-problem.jpg){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}

Consequently, you must implement a mechanism for that enables the
clients of service to make requests to a dynamically changing set of
ephemeral service instances.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How does the client of a service - the API gateway or another service -
discover the location of a service instance?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   Each instance of a service exposes a remote API such as HTTP/REST,
    or Thrift etc. at a particular location (host and port)
-   The number of services instances and their locations changes
    dynamically.
-   Virtual machines and containers are usually assigned dynamic IP
    addresses.
-   The number of services instances might vary dynamically. For
    example, an EC2 Autoscaling Group adjusts the number of instances
    based on load.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
When making a request to a service, the client obtains the location of a
service instance by querying a [Service
Registry](https://microservices.io/patterns/service-registry.html),
which knows the locations of all service instances.

The following diagram shows the structure of this pattern.

![](https://microservices.io/i/servicediscovery/client-side-discovery.jpg){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}

This is typically handled by a [Microservice chassis
framework](https://microservices.io/patterns/microservice-chassis.html)



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
The [Microservices Example
application](https://github.com/cer/microservices-examples) is
an example of an application that uses client-side service discovery. It
is written in Scala and uses Spring Boot and Spring Cloud as
the [Microservice
chassis](https://microservices.io/patterns/microservice-chassis.html).
They provide various capabilities including client-side discovery.

`RegistrationServiceProxy`{.highlighter-rouge} is a component of that
application. In order to register a user, it invokes another service
using the Spring Framework's `RestTemplate`{.highlighter-rouge}:

> ``` {.highlight}
> @Component
> class RegistrationServiceProxy @Autowired()(restTemplate: RestTemplate) extends RegistrationService {
>
>   @Value("${user_registration_url}")
>   var userRegistrationUrl: String = _
>
>   override def registerUser(emailAddress: String, password: String): Either[RegistrationError, String] = {
>
>       val response = restTemplate.postForEntity(userRegistrationUrl,
>         RegistrationBackendRequest(emailAddress, password),
>         classOf[RegistrationBackendResponse])
>        ...
> }
> ```

It is injected with the RestTemplate and
the `user_registration_url`{.highlighter-rouge}, which specifies the
REST endpoint.

When the application is
deployed `user_registration_url`{.highlighter-rouge} is set to this
URL `http://REGISTRATION-SERVICE/user`{.highlighter-rouge} - see
the `docker-compose.yml`{.highlighter-rouge} file. `REGISTRATION-SERVICE`{.highlighter-rouge} is
the logical service name that is resolved to a network location using
client-side service discovery. The service discovery is implemented
using [Netflix
OSS](http://netflix.github.io/) components. It
provides [Eureka](https://github.com/Netflix/eureka/wiki/Eureka-at-a-glance),
which is a [Service
Registry](https://microservices.io/patterns/service-registry.html),
and [Ribbon](https://github.com/Netflix/ribbon), which
is an HTTP client that queries Eureka in order to route HTTP requests to
an available service instance.

Client-side service discovery is configured using various Spring Cloud
annotations:

> ``` {.highlight}
> @Configuration
> @EnableEurekaClient
> @Profile(Array("enableEureka"))
> class EurekaClientConfiguration {
>
>   @Bean
>   @LoadBalanced
>   def restTemplate(scalaObjectMapper : ScalaObjectMapper) : RestTemplate = {
>     val restTemplate = new RestTemplate()
>     restTemplate.getMessageConverters foreach {
>       case mc: MappingJackson2HttpMessageConverter =>
>         mc.setObjectMapper(scalaObjectMapper)
>       case _ =>
>     }
>     restTemplate
>   }
> ```

The `@EnableEurekaClient`{.highlighter-rouge} annotation enables the
Eureka client. The `@LoadBalanced`{.highlighter-rouge} annotation
configures the `RestTemplate`{.highlighter-rouge} to use Ribbon, which
has been configured to use the Eureka client to do service discovery. As
a result, the `RestTemplate`{.highlighter-rouge} will handle requests to
the `http://REGISTRATION-SERVICE/user`{.highlighter-rouge} endpoint by
querying Eureka to find the network locations of available service
instances.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
Client-side discovery has the following benefits:

-   Fewer moving parts and network hops compared to [Server-side
    Discovery](https://microservices.io/patterns/server-side-discovery.html)

Client-side discovery also has the following drawbacks:

-   This pattern couples the client to the [Service
    Registry](https://microservices.io/patterns/service-registry.html)
-   You need to implement client-side service discovery logic for each
    programming language/framework used by your application, e.g
    Java/Scala, JavaScript/NodeJS. For example, [Netflix
    Prana](https://github.com/Netflix/Prana) provides an
    HTTP proxy-based approach to service discovery for non-JVM clients.





 {#expander-106764937 .expand-container}
 {#expander-control-106764937 .expand-control}
Server Side


 {#expander-content-106764937 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
Services typically need to call one another. In a monolithic
application, services invoke one another through language-level method
or procedure calls. In a traditional distributed system deployment,
services run at fixed, well known locations (hosts and ports) and so can
easily call one another using HTTP/REST or some RPC mechanism. However,
a
modern [microservice-based](https://microservices.io/patterns/microservices.html) application
typically runs in a virtualized or containerized environments where the
number of instances of a service and their locations changes
dynamically.

![](https://microservices.io/i/servicediscovery/discovery-problem.jpg){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}

Consequently, you must implement a mechanism for that enables the
clients of service to make requests to a dynamically changing set of
ephemeral service instances.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How does the client of a service - the API gateway or another service -
discover the location of a service instance?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   Each instance of a service exposes a remote API such as HTTP/REST,
    or Thrift etc. at a particular location (host and port)
-   The number of services instances and their locations changes
    dynamically.
-   Virtual machines and containers are usually assigned dynamic IP
    addresses.
-   The number of services instances might vary dynamically. For
    example, an EC2 Autoscaling Group adjusts the number of instances
    based on load.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
When making a request to a service, the client makes a request via a
router (a.k.a load balancer) that runs at a well known location. The
router queries a [service
registry](https://microservices.io/patterns/service-registry.html),
which might be built into the router, and forwards the request to an
available service instance.

The following diagram shows the structure of this pattern.

![](https://microservices.io/i/servicediscovery/server-side-discovery.jpg){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
An AWS Elastic Load Balancer (ELB) is an example of a server-side
discovery router. A client makes HTTP(s) requests (or opens TCP
connections) to the ELB, which load balances the traffic amongst a set
of EC2 instances. An ELB can load balance either external traffic from
the Internet or, when deployed in a VPC, load balance internal traffic.
An ELB also functions as a [Service
Registry](https://microservices.io/patterns/service-registry.html).
EC2 instances are registered with the ELB either explicitly via an API
call or automatically as part of an auto-scaling group.

Some clustering solutions such
as [Kubernetes](https://github.com/GoogleCloudPlatform/kubernetes/blob/master/docs/services.md) and [Marathon](https://mesosphere.github.io/marathon/docs/service-discovery-load-balancing.html) run
a proxy on each host that functions as a server-side discovery router.
In order to access a service, a client connects to the local proxy using
the port assigned to that service. The proxy then forwards the request
to a service instance running somewhere in the cluster.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Related Context**


 {.panelContent}
Server-side service discovery has a number of benefits:

-   Compared to [client-side
    discovery](https://microservices.io/patterns/client-side-discovery.html),
    the client code is simpler since it does not have to deal with
    discovery. Instead, a client simply makes a request to the router
-   Some cloud environments provide this functionality, e.g. AWS Elastic
    Load Balancer

It also has the following drawbacks:

-   Unless it's part of the cloud environment, the router must is
    another system component that must be installed and configured. It
    will also need to be replicated for availability and capacity.
-   The router must support the necessary communication protocols (e.g
    HTTP, gRPC, Thrift, etc) unless it is TCP-based router
-   More network hops are required than when using [Client Side
    Discovery](https://microservices.io/patterns/client-side-discovery.html)







 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Service per Host**


 {.panelContent}
 {#expander-1297205035 .expand-container}
 {#expander-control-1297205035 .expand-control}
Single


 {#expander-content-1297205035 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html) and
architected your system as a set of services. Each service is deployed
as a set of service instances for throughput and availability.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How are services packaged and deployed?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   Services are written using a variety of languages, frameworks, and
    framework versions
-   Each service consists of multiple service instances for throughput
    and availability
-   Service must be independently deployable and scalable
-   Service instances need to be isolated from one another
-   You need to be able to quickly build and deploy a service
-   You need to be able to constrain the resources (CPU and memory)
    consumed by a service
-   You need to monitor the behavior of each service instance
-   You want deployment to reliable
-   You must deploy the application as cost-effectively as possible



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Deploy each single service instance on its own host



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
\



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
The benefits of this approach include:

-   Services instances are isolated from one another
-   There is no possibility of conflicting resource requirements or
    dependency versions
-   A service instance can only consume at most the resources of a
    single host
-   Its straightforward to monitor, manage, and redeploy each service
    instance

The drawbacks of this approach include:

-   Potentially less efficient resource utilization compared
    to [Multiple Services per
    Host](https://microservices.io/patterns/deployment/multiple-services-per-host.html) because
    there are more hosts



\

\



 {#expander-868935716 .expand-container}
 {#expander-control-868935716 .expand-control}
Multiple


 {#expander-content-868935716 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html) and
architected your system as a set of services. Each service is deployed
as a set of service instances for throughput and availability.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How are services packaged and deployed?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   Services are written using a variety of languages, frameworks, and
    framework versions
-   Each service consists of multiple service instances for throughput
    and availability
-   Service must be independently deployable and scalable
-   Service instances need to be isolated from one another
-   You need to be able to quickly build and deploy a service
-   You need to be able to constrain the resources (CPU and memory)
    consumed by a service
-   You need to monitor the behavior of each service instance
-   You want deployment to reliable
-   You must deploy the application as cost-effectively as possible



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Run multiple instances of different services on a host (Physical or
Virtual machine).

There are various ways of deploying a service instance on a shared host
including:

-   Deploy each service instance as a JVM process. For example, a Tomcat
    or Jetty instances per service instance.
-   Deploy multiple service instances in the same JVM. For example, as
    web applications or OSGI bundles.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
\



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
The benefits of this pattern include:

-   More efficient resource utilization than the [Service Instance per
    host
    pattern](https://microservices.io/patterns/deployment/single-service-per-host.html)

The drawbacks of this approach include:

-   Risk of conflicting resource requirements
-   Risk of conflicting dependency versions
-   Difficult to limit the resources consumed by a service instance
-   If multiple services instances are deployed in the same process then
    its difficult to monitor the resource consumption of each service
    instance. Its also impossible to isolate each instance







 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Cross-Cutting Concerns**


 {.panelContent}
 {#expander-1407265382 .expand-container}
 {#expander-control-1407265382 .expand-control}
Microservice chassis


 {#expander-content-1407265382 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
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
different, however, if you are developing an application that has
the [microservice
architecture](https://microservices.io/patterns/microservices.html).
There are tens or hundreds of services. You will frequently create new
services, each of which will only take days or weeks to develop. You
cannot afford to spend a few days configuring the mechanisms to handle
cross-cutting concerns. What is even worse is that in a microservice
architecture there are additional cross-cutting concerns that you have
to deal with including service registration and discovery, and circuit
breakers for reliably handling partial failure.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   Creating a new microservice should be fast and easy
-   When creating a microservice you must handle cross-cutting concerns
    such as externalized configuration, logging, health checks, metrics,
    service registration and discovery, circuit breakers. There are also
    cross-cutting concerns that are specific to the technologies that
    the microservices uses.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Build your microservices using a microservice chassis framework, which
handles cross-cutting concerns



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
Here, at Pinnacle, we do benefit from this pattern greatly. It is a nice
way to enforce practices while we promote reusable code.\
For all our .Net Core APIs, we always reference the following
nuget [Pinnacle.CustomerTeam.Api](http://devtools.pinnacle.com:81/feeds/Default/Pinnacle.CustomerTeam.Api).\
Once referenced, developer makes sure to configure the required cross
cutting concerns for the given project. \
\
![](attachments/451820218/471990423.png){.confluence-embedded-image
height="400"}\
\
Feel free to dig deeper into the code:\
\
[Project using the chassis]{.underline}:\
[   
https://stash.pinnacle.com/projects/CUS/repos/kyc-api/browse/Pinnacle.KnowYourCustomer.Api/Configuration](https://stash.pinnacle.com/projects/CUS/repos/kyc-api/browse/Pinnacle.KnowYourCustomer.Api/Configuration)\
[Chassis]{.underline}:\
[   
https://stash.pinnacle.com/projects/CUS/repos/shared/browse/Pinnacle.CustomerTeam.Api](https://stash.pinnacle.com/projects/CUS/repos/shared/browse/Pinnacle.CustomerTeam.Api)



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
The major benefit of a microservice chassis is that you can quickly and
easy get started with developing a microservice.

You need a microservice chassis for each programming language/framework
that you want to use. This can be an obstacle to adopting a new
programming language or framework.



\

\

\

\



 {#expander-1270315438 .expand-container}
 {#expander-control-1270315438 .expand-control}
Externalized configuration


 {#expander-content-1270315438 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
An application typically uses one or more infrastructure and 3rd party
services. Examples of infrastructure services include: a [Service
registry](https://microservices.io/patterns/service-registry.html),
a message broker and a database server. Examples of 3rd party services
include: payment processing, email and messaging, etc.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to enable a service to run in multiple environments without
modification?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   A service must be provided with configuration data that tells it how
    to connect to the external/3rd party services. For example, the
    database network location and credentials
-   A service must run in multiple environments - dev, test, qa,
    staging, production - without modification and/or recompilation
-   Different environments have different instances of the external/3rd
    party services, e.g. QA database vs. production database, test
    credit card processing account vs. production credit card processing
    account



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Externalize all application configuration including the database
credentials and network location. On startup, a service reads the
configuration from an external source, e.g. OS environment variables,
etc.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
[Spring Boot externalized
configuration](https://docs.spring.io/spring-boot/docs/current/reference/html/boot-features-external-config.html) reads
values from a variety of sources including operating system environment
variables, property files and command line arguments. These values are
available within the Spring application context.

`RegistrationServiceProxy`{.highlighter-rouge} from the [Microservices
Example
application](https://github.com/cer/microservices-examples) is
an example of a component, which is written in Scala, is configured with
the variable `user_registration_url`{.highlighter-rouge}:

> ``` {.highlight}
> @Component
> class RegistrationServiceProxy @Autowired()(restTemplate: RestTemplate) extends RegistrationService {
>
>   @Value("${user_registration_url}")
>   var userRegistrationUrl: String = _
> ```
>
> The `docker-compose.yml`{.highlighter-rouge} file supplies its value
> as an operating system environment variable:
>
> ``` {.highlight}
> web:
>   image: sb_web
>   ports:
>     - "8080:8080"
>   links:
>     - eureka
>   environment:
>     USER_REGISTRATION_URL: http://REGISTRATION-SERVICE/user
> ```

`REGISTRATION-SERVICE`{.highlighter-rouge} is the logical name of the
service. It is resolved using [Client-side
discovery](https://microservices.io/patterns/client-side-discovery.html).



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Related Context**


 {.panelContent}
This pattern has the following benefits:

-   The application runs in multiple environments without modification
    and/or recompilation

There are the following issues with this pattern:

-   How to ensure that when an application is deployed the supplied
    configuration matches what is expected?







 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Testing patterns**


 {.panelContent}
 {#expander-912477413 .expand-container}
 {#expander-control-912477413 .expand-control}
Service Component Test


 {#expander-content-912477413 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservice
architecture](https://microservices.io/patterns/Microservices.html) pattern.
The application consists of numerous services. Services often invoke
other services. You must write automated tests that verify that a
service behaves correctly.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How do you easily test a service?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   End to end testing (i.e. tests that launch multiple services) is
    difficult, slow, brittle, and expensive.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
A test suite that tests a service in isolation using test doubles for
any services that it invokes.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
[Spring Cloud
Contract](https://cloud.spring.io/spring-cloud-contract/) is
an open source project that supports this style of testing.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
This pattern has the following benefits:

-   Testing a service in isolation is easier, faster, more reliable and
    cheap

This pattern has the following drawbacks:

-   Tests might pass but the application will fail in production

This pattern has the following issues:

-   How to ensure that the test doubles always correctly emulate the
    behavior of the invoked services?





 {#expander-269431778 .expand-container}
 {#expander-control-269431778 .expand-control}
Service Integration Contract Test


 {#expander-content-269431778 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservice
architecture](https://microservices.io/patterns/Microservices.html) pattern.
The application consists of numerous services. Services often invoke
other services. You must write automated tests that verify that a
service behaves correctly.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to easily test that a service provides an API that its clients
expect?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   End to end testing (i.e. tests that launch multiple services) is
    difficult, slow, brittle, and expensive.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
A test suite for a service that is written by the developers of another
service that consumes it. The test suite verifies that the service meets
the consuming service's expectations.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
[Spring Cloud
Contract](https://cloud.spring.io/spring-cloud-contract/) is
an open source project that supports this style of testing.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Related Context**


 {.panelContent}
This pattern has the following benefits:

-   Testing a service in isolation is easier, faster, more reliable and
    cheap

This pattern has the following drawbacks:

-   Tests might pass but the application will fail in production

This pattern has the following issues:

-   How to ensure that the consumer provided tests match what the
    consumer actually requires?







 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Circuit Breaker**


 {.panelContent}
 {#expander-163235287 .expand-container}
 {#expander-control-163235287 .expand-control}
Circuit Breaker


 {#expander-content-163235287 .expand-content}
Author: [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Overview
--------


 {.panelContent}
Handle faults that might take a variable amount of time to recover from,
when connecting to a remote service or resource. This can improve the
stability and resiliency of an application.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context and Problem
-------------------


 {.panelContent}
In a distributed environment, calls to remote resources and services can
fail due to transient faults, such as slow network connections,
timeouts, or the resources being overcommitted or temporarily
unavailable. These faults typically correct themselves after a short
period of time, and a robust cloud application should be prepared to
handle them by using a strategy such as the [Retry
pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/retry).

However, there can also be situations where faults are due to
unanticipated events, and that might take much longer to fix. These
faults can range in severity from a partial loss of connectivity to the
complete failure of a service. In these situations it might be pointless
for an application to continually retry an operation that is unlikely to
succeed, and instead the application should quickly accept that the
operation has failed and handle this failure accordingly.

Additionally, if a service is very busy, failure in one part of the
system might lead to cascading failures. For example, an operation that
invokes a service could be configured to implement a timeout, and reply
with a failure message if the service fails to respond within this
period. However, this strategy could cause many concurrent requests to
the same operation to be blocked until the timeout period expires. These
blocked requests might hold critical system resources such as memory,
threads, database connections, and so on. Consequently, these resources
could become exhausted, causing failure of other possibly unrelated
parts of the system that need to use the same resources. In these
situations, it would be preferable for the operation to fail
immediately, and only attempt to invoke the service if it\'s likely to
succeed. Note that setting a shorter timeout might help to resolve this
problem, but the timeout shouldn\'t be so short that the operation fails
most of the time, even if the request to the service would eventually
succeed.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
The Circuit Breaker pattern, popularized by Michael Nygard in his
book, [Release
It!](https://pragprog.com/book/mnee/release-it), can
prevent an application from repeatedly trying to execute an operation
that\'s likely to fail. Allowing it to continue without waiting for the
fault to be fixed or wasting CPU cycles while it determines that the
fault is long lasting. The Circuit Breaker pattern also enables an
application to detect whether the fault has been resolved. If the
problem appears to have been fixed, the application can try to invoke
the operation.

> The purpose of the Circuit Breaker pattern is different than the Retry
> pattern. The Retry pattern enables an application to retry an
> operation in the expectation that it\'ll succeed. The Circuit Breaker
> pattern prevents an application from performing an operation that is
> likely to fail. An application can combine these two patterns by using
> the Retry pattern to invoke an operation through a circuit breaker.
> However, the retry logic should be sensitive to any exceptions
> returned by the circuit breaker and abandon retry attempts if the
> circuit breaker indicates that a fault is not transient.

A circuit breaker acts as a proxy for operations that might fail. The
proxy should monitor the number of recent failures that have occurred,
and use this information to decide whether to allow the operation to
proceed, or simply return an exception immediately.

The proxy can be implemented as a state machine with the following
states that mimic the functionality of an electrical circuit breaker:

-   **Closed**: The request from the application is routed to the
    operation. The proxy maintains a count of the number of recent
    failures, and if the call to the operation is unsuccessful the proxy
    increments this count. If the number of recent failures exceeds a
    specified threshold within a given time period, the proxy is placed
    into the **Open** state. At this point the proxy starts a timeout
    timer, and when this timer expires the proxy is placed into
    the **Half-Open** state.

    > The purpose of the timeout timer is to give the system time to fix
    > the problem that caused the failure before allowing the
    > application to try to perform the operation again.

-   **Open**: The request from the application fails immediately and an
    exception is returned to the application.

-   **Half-Open**: A limited number of requests from the application are
    allowed to pass through and invoke the operation. If these requests
    are successful, it\'s assumed that the fault that was previously
    causing the failure has been fixed and the circuit breaker switches
    to the **Closed** state (the failure counter is reset). If any
    request fails, the circuit breaker assumes that the fault is still
    present so it reverts back to the **Open** state and restarts the
    timeout timer to give the system a further period of time to recover
    from the failure.

    > The**Half-Open**state is useful to prevent a recovering service
    > from suddenly being flooded with requests. As a service recovers,
    > it might be able to support a limited volume of requests until the
    > recovery is complete, but while recovery is in progress a flood of
    > work can cause the service to time out or fail again.

![](attachments/463533311/463533310.png){.confluence-embedded-image
.confluence-thumbnail .confluence-content-image-border height="150"}

In the figure, the failure counter used by the **Closed** state is time
based. It\'s automatically reset at periodic intervals. This helps to
prevent the circuit breaker from entering the **Open** state if it
experiences occasional failures. The failure threshold that trips the
circuit breaker into the **Open** state is only reached when a specified
number of failures have occurred during a specified interval. The
counter used by the **Half-Open** state records the number of successful
attempts to invoke the operation. The circuit breaker reverts to
the **Closed** state after a specified number of consecutive operation
invocations have been successful. If any invocation fails, the circuit
breaker enters the **Open** state immediately and the success counter
will be reset the next time it enters the **Half-Open** state.

> How the system recovers is handled externally, possibly by restoring
> or restarting a failed component or repairing a network connection.

The Circuit Breaker pattern provides stability while the system recovers
from a failure and minimizes the impact on performance. It can help to
maintain the response time of the system by quickly rejecting a request
for an operation that\'s likely to fail, rather than waiting for the
operation to time out, or never return. If the circuit breaker raises an
event each time it changes state, this information can be used to
monitor the health of the part of the system protected by the circuit
breaker, or to alert an administrator when a circuit breaker trips to
the **Open** state.

The pattern is customizable and can be adapted according to the type of
the possible failure. For example, you can apply an increasing timeout
timer to a circuit breaker. You could place the circuit breaker in
the **Open** state for a few seconds initially, and then if the failure
hasn\'t been resolved increase the timeout to a few minutes, and so on.
In some cases, rather than the **Open** state returning failure and
raising an exception, it could be useful to return a default value that
is meaningful to the application.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Issues and Considerations
-------------------------


 {.panelContent}
You should consider the following points when deciding how to implement
this pattern:

**Exception Handling**. An application invoking an operation through a
circuit breaker must be prepared to handle the exceptions raised if the
operation is unavailable. The way exceptions are handled will be
application specific. For example, an application could temporarily
degrade its functionality, invoke an alternative operation to try to
perform the same task or obtain the same data, or report the exception
to the user and ask them to try again later.

**Types of Exceptions**. A request might fail for many reasons, some of
which might indicate a more severe type of failure than others. For
example, a request might fail because a remote service has crashed and
will take several minutes to recover, or because of a timeout due to the
service being temporarily overloaded. A circuit breaker might be able to
examine the types of exceptions that occur and adjust its strategy
depending on the nature of these exceptions. For example, it might
require a larger number of timeout exceptions to trip the circuit
breaker to the **Open** state compared to the number of failures due to
the service being completely unavailable.

**Logging**. A circuit breaker should log all failed requests (and
possibly successful requests) to enable an administrator to monitor the
health of the operation.

**Recoverability**. You should configure the circuit breaker to match
the likely recovery pattern of the operation it\'s protecting. For
example, if the circuit breaker remains in the **Open** state for a long
period, it could raise exceptions even if the reason for the failure has
been resolved. Similarly, a circuit breaker could fluctuate and reduce
the response times of applications if it switches from
the **Open** state to the **Half-Open** state too quickly.

**Testing Failed Operations**. In the **Open** state, rather than using
a timer to determine when to switch to the **Half-Open** state, a
circuit breaker can instead periodically ping the remote service or
resource to determine whether it\'s become available again. This ping
could take the form of an attempt to invoke an operation that had
previously failed, or it could use a special operation provided by the
remote service specifically for testing the health of the service, as
described by the [Health Endpoint Monitoring
pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/health-endpoint-monitoring).

**Manual Override**. In a system where the recovery time for a failing
operation is extremely variable, it\'s beneficial to provide a manual
reset option that enables an administrator to close a circuit breaker
(and reset the failure counter). Similarly, an administrator could force
a circuit breaker into the **Open** state (and restart the timeout
timer) if the operation protected by the circuit breaker is temporarily
unavailable.

**Concurrency**. The same circuit breaker could be accessed by a large
number of concurrent instances of an application. The implementation
shouldn\'t block concurrent requests or add excessive overhead to each
call to an operation.

**Resource Differentiation**. Be careful when using a single circuit
breaker for one type of resource if there might be multiple underlying
independent providers. For example, in a data store that contains
multiple shards, one shard might be fully accessible while another is
experiencing a temporary issue. If the error responses in these
scenarios are merged, an application might try to access some shards
even when failure is highly likely, while access to other shards might
be blocked even though it\'s likely to succeed.

**Accelerated Circuit Breaking**. Sometimes a failure response can
contain enough information for the circuit breaker to trip immediately
and stay tripped for a minimum amount of time. For example, the error
response from a shared resource that\'s overloaded could indicate that
an immediate retry isn\'t recommended and that the application should
instead try again in a few minutes.

> A service can return HTTP 429 (Too Many Requests) if it is throttling
> the client, or HTTP 503 (Service Unavailable) if the service is not
> currently available. The response can include additional information,
> such as the anticipated duration of the delay.

**Replaying Failed Requests**. In the **Open** state, rather than simply
failing quickly, a circuit breaker could also record the details of each
request to a journal and arrange for these requests to be replayed when
the remote resource or service becomes available.

**Inappropriate Timeouts on External Services**. A circuit breaker might
not be able to fully protect applications from operations that fail in
external services that are configured with a lengthy timeout period. If
the timeout is too long, a thread running a circuit breaker might be
blocked for an extended period before the circuit breaker indicates that
the operation has failed. In this time, many other application instances
might also try to invoke the service through the circuit breaker and tie
up a significant number of threads before they all fail.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
When to use this Pattern
------------------------


 {.panelContent}
Use this pattern:

-   To prevent an application from trying to invoke a remote service or
    access a shared resource if this operation is highly likely to fail.

This pattern isn\'t recommended:

-   For handling access to local private resources in an application,
    such as in-memory data structure. In this environment, using a
    circuit breaker would add overhead to your system.
-   As a substitute for handling exceptions in the business logic of
    your applications.







 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Access**


 {.panelContent}
 {#expander-469904723 .expand-container}
 {#expander-control-469904723 .expand-control}
Access Token


 {#expander-content-469904723 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservice
architecture](https://microservices.io/patterns/microservices.html) and [API
Gateway](https://microservices.io/patterns/apigateway.html) patterns.
The application consists of numerous services. The API gateway is the
single entry point for client requests. It authenticates requests, and
forwards them to other services, which might in turn invoke other
services.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to communicate the identity of the requestor to the services that
handle the request?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   Services often need to verify that a user is authorized to perform
    an operation



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
The [API
Gateway](https://microservices.io/patterns/apigateway.html) authenticates
the request and passes an access token (e.g. [JSON Web
Token](https://jwt.io/)) that securely identifies the
requestor in each request to the services. A service can include the
access token in requests it makes to other services.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
See [JSON Web Token](https://jwt.io/) for usage examples
and supporting libraries.



\

\





 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Observability Patterns**


 {.panelContent}
 {#expander-560317589 .expand-container}
 {#expander-control-560317589 .expand-control}
Log Aggregation


 {#expander-content-560317589 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html).
The application consists of multiple services and service instances that
are running on multiple machines. Requests often span multiple service
instances.

Each service instance generates writes information about what it is
doing to a log file in a standardized format. The log file contains
errors, warnings, information and debug messages.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to understand the behavior of an application and troubleshoot
problems?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   Any solution should have minimal runtime overhead



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Use a centralized logging service that aggregates logs from each service
instance. The users can search and analyze the logs. They can configure
alerts that are triggered when certain messages appear in the logs.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
-   [AWS Cloud
    Watch](https://aws.amazon.com/cloudwatch/)



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
This pattern has the following issues:





 {#expander-1095891749 .expand-container}
 {#expander-control-1095891749 .expand-control}
Application Metrics


 {#expander-content-1095891749 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

\

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html).



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to understand the behavior of an application and troubleshoot
problems?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   Any solution should have minimal runtime overhead



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Instrument a service to gather statistics about individual operations.
Aggregate metrics in centralized metrics service, which provides
reporting and alerting. There are two models for aggregating metrics:

-   push - the service pushes metrics to the metrics service
-   pull - the metrics services pulls metrics from the service



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
-   Instrumentation libraries:
    -   Coda Hale/Yammer [Java Metrics
        Library](http://metrics.dropwizard.io/3.1.0/)
    -   [Prometheus client
        libraries](https://prometheus.io/docs/instrumenting/clientlibs/)
-   Metrics aggregation services
    -   [Prometheus](https://prometheus.io/docs/introduction/overview/)
    -   [AWS Cloud
        Watch](https://aws.amazon.com/cloudwatch/)



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Resulting Conext**


 {.panelContent}
This pattern has the following benefits:

-   It provides deep insight into application behavior

This pattern has the following drawbacks:

-   Metrics code is intertwined with business logic making it more
    complicated

This pattern has the following issues:

-   Aggregating metrics can require significant infrastructure





 {#expander-1093860688 .expand-container}
 {#expander-control-1093860688 .expand-control}
Audit Logging


 {#expander-content-1093860688 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html).



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to understand the behavior of users and the application and
troubleshoot problems?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   It is useful to know what actions a user has recently performed:
    customer support, compliance, security, etc.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Record user activity in a database.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
This pattern is widely used.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
This pattern has the following benefits:

-   Provides a record of user actions

This pattern has the following drawbacks:

-   The auditing code is intertwined with the business logic, which
    makes the business logic more complicated



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
-   [Event
    Sourcing](https://microservices.io/patterns/data/event-sourcing.html) is
    a reliable way to implement auditing





 {#expander-2105617653 .expand-container}
 {#expander-control-2105617653 .expand-control}
Distributed Tracing


 {#expander-content-2105617653 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html).
Requests often span multiple services. Each service handles a request by
performing one or more operations, e.g. database queries, publishes
messages, etc.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to understand the behavior of an application and troubleshoot
problems?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   External monitoring only tells you the overall response time and
    number of invocations - no insight into the individual operations
-   Any solution should have minimal runtime overhead
-   Log entries for a request are scattered across numerous logs



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Instrument services with code that

-   Assigns each external request a unique external request id
-   Passes the external request id to all services that are involved in
    handling the request
-   Includes the external request id in all [log
    messages](https://microservices.io/patterns/observability/application-logging.html)
-   Records information (e.g. start time, end time) about the requests
    and operations performed when handling a external request in a
    centralized service

This instrumentation might be part of the functionality provided by
a [Microservice Chassis
framework](https://microservices.io/patterns/microservice-chassis.html).



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
This pattern has the following benefits:

-   It provides useful insight into the behavior of the system including
    the sources of latency
-   It enables developers to see how an individual request is handled by
    searching across [aggregated
    logs](https://microservices.io/patterns/observability/application-logging.html) for
    its external request id

This pattern has the following issues:

-   Aggregating and storing traces can require significant
    infrastructure



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Related Patterns**


 {.panelContent}
-   [Log
    aggregation](https://microservices.io/patterns/observability/application-logging.html) -
    the external request id is included in each log message





 {#expander-1464457093 .expand-container}
 {#expander-control-1464457093 .expand-control}
Exception Tracking


 {#expander-content-1464457093 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html).
The application consists of multiple services and service instances that
are running on multiple machines. Errors sometimes occur when handling
requests. When an error occurs, a service instance throws an exception,
which contains an error message and a stack trace.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to understand the behavior of an application and troubleshoot
problems?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   Exceptions must be de-duplicated, recorded, investigated by
    developers and the underlying issue resolved
-   Any solution should have minimal runtime overhead



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Report all exceptions to a centralized exception tracking service that
aggregates and tracks exceptions and notifies developers.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
This pattern has the following benefits:

-   It is easier to view exceptions and track their resolution

This pattern has the following drawbacks:

-   The exception tracking service is additional infrastructure



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Related Patterns**


 {.panelContent}
-   [Log
    aggregation](https://microservices.io/patterns/observability/application-logging.html) -
    exceptions should be logged as well as reported to a tracking
    service





 {#expander-1706960593 .expand-container}
 {#expander-control-1706960593 .expand-control}
Distributed Tracing


 {#expander-content-1706960593 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html).
Requests often span multiple services. Each service handles a request by
performing one or more operations, e.g. database queries, publishes
messages, etc.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to understand the behavior of an application and troubleshoot
problems?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   External monitoring only tells you the overall response time and
    number of invocations - no insight into the individual operations
-   Any solution should have minimal runtime overhead
-   Log entries for a request are scattered across numerous logs



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Instrument services with code that

-   Assigns each external request a unique external request id
-   Passes the external request id to all services that are involved in
    handling the request
-   Includes the external request id in all [log
    messages](https://microservices.io/patterns/observability/application-logging.html)
-   Records information (e.g. start time, end time) about the requests
    and operations performed when handling a external request in a
    centralized service

This instrumentation might be part of the functionality provided by
a [Microservice Chassis
framework](https://microservices.io/patterns/microservice-chassis.html).



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
This pattern has the following benefits:

-   It provides useful insight into the behavior of the system including
    the sources of latency
-   It enables developers to see how an individual request is handled by
    searching across [aggregated
    logs](https://microservices.io/patterns/observability/application-logging.html) for
    its external request id

This pattern has the following issues:

-   Aggregating and storing traces can require significant
    infrastructure



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Related Patterns**


 {.panelContent}
-   [Log
    aggregation](https://microservices.io/patterns/observability/application-logging.html) -
    the external request id is included in each log message





 {#expander-1724112831 .expand-container}
 {#expander-control-1724112831 .expand-control}
Exception Tracking


 {#expander-content-1724112831 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html).
The application consists of multiple services and service instances that
are running on multiple machines. Errors sometimes occur when handling
requests. When an error occurs, a service instance throws an exception,
which contains an error message and a stack trace.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to understand the behavior of an application and troubleshoot
problems?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   Exceptions must be de-duplicated, recorded, investigated by
    developers and the underlying issue resolved
-   Any solution should have minimal runtime overhead



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Report all exceptions to a centralized exception tracking service that
aggregates and tracks exceptions and notifies developers.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
This pattern has the following benefits:

-   It is easier to view exceptions and track their resolution

This pattern has the following drawbacks:

-   The exception tracking service is additional infrastructure



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Related Patterns**


 {.panelContent}
-   [Log
    aggregation](https://microservices.io/patterns/observability/application-logging.html) -
    exceptions should be logged as well as reported to a tracking
    service





 {#expander-923544656 .expand-container}
 {#expander-control-923544656 .expand-control}
Health Check API


 {#expander-content-923544656 .expand-content}
Author: [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Overview
--------


 {.panelContent}
Implement functional checks in an application that external tools can
access through exposed endpoints at regular intervals. This can help to
verify that applications and services are performing correctly.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context and Problem
-------------------


 {.panelContent}
It\'s a good practice, and often a business requirement, to monitor web
applications and back-end services, to ensure they\'re available and
performing correctly. However, it\'s more difficult to monitor services
running in the cloud than it is to monitor on-premises services. For
example, you don\'t have full control of the hosting environment, and
the services typically depend on other services provided by platform
vendors and others.

There are many factors that affect cloud-hosted applications such as
network latency, the performance and availability of the underlying
compute and storage systems, and the network bandwidth between them. The
service can fail entirely or partially due to any of these factors.
Therefore, you must verify at regular intervals that the service is
performing correctly to ensure the required level of availability, which
might be part of your service level agreement (SLA).



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Implement health monitoring by sending requests to an endpoint on the
application. The application should perform the necessary checks, and
return an indication of its status.

A health monitoring check typically combines two factors:

-   The checks (if any) performed by the application or service in
    response to the request to the health verification endpoint.
-   Analysis of the results by the tool or framework that performs the
    health verification check.

The response code indicates the status of the application and,
optionally, any components or services it uses. The latency or response
time check is performed by the monitoring tool or framework. The figure
provides an overview of the pattern.

![](attachments/463533359/463533358.png){.confluence-embedded-image
.confluence-thumbnail .confluence-content-image-border height="150"}

Other checks that might be carried out by the health monitoring code in
the application include:

-   Checking cloud storage or a database for availability and response
    time.
-   Checking other resources or services located in the application, or
    located elsewhere but used by the application.

Services and tools are available that monitor web applications by
submitting a request to a configurable set of endpoints, and evaluating
the results against a set of configurable rules. It\'s relatively easy
to create a service endpoint whose sole purpose is to perform some
functional tests on the system.

Typical checks that can be performed by the monitoring tools include:

-   Validating the response code. For example, an HTTP response of 200
    (OK) indicates that the application responded without error. The
    monitoring system might also check for other response codes to give
    more comprehensive results.
-   Checking the content of the response to detect errors, even when a
    200 (OK) status code is returned. This can detect errors that affect
    only a section of the returned web page or service response. For
    example, checking the title of a page or looking for a specific
    phrase that indicates the correct page was returned.
-   Measuring the response time, which indicates a combination of the
    network latency and the time that the application took to execute
    the request. An increasing value can indicate an emerging problem
    with the application or network.
-   Checking resources or services located outside the application, such
    as a content delivery network used by the application to deliver
    content from global caches.
-   Checking for expiration of SSL certificates.
-   Measuring the response time of a DNS lookup for the URL of the
    application to measure DNS latency and DNS failures.
-   Validating the URL returned by the DNS lookup to ensure correct
    entries. This can help to avoid malicious request redirection
    through a successful attack on the DNS server.

It\'s also useful, where possible, to run these checks from different
on-premises or hosted locations to measure and compare response times.
Ideally you should monitor applications from locations that are close to
customers to get an accurate view of the performance from each location.
In addition to providing a more robust checking mechanism, the results
can help you decide on the deployment location for the application---and
whether to deploy it in more than one datacenter.

Tests should also be run against all the service instances that
customers use to ensure the application is working correctly for all
customers. For example, if customer storage is spread across more than
one storage account, the monitoring process should check all of these.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Issues and Considerations
-------------------------


 {.panelContent}
Consider the following points when deciding how to implement this
pattern:

How to validate the response. For example, is just a single 200 (OK)
status code sufficient to verify the application is working correctly?
While this provides the most basic measure of application availability,
and is the minimum implementation of this pattern, it provides little
information about the operations, trends, and possible upcoming issues
in the application.

> Make sure that the application correctly returns a 200 (OK) only when
> the target resource is found and processed. In some scenarios, such as
> when using a master page to host the target web page, the server sends
> back a 200 (OK) status code instead of a 404 (Not Found) code, even
> when the target content page was not found.

The number of endpoints to expose for an application. One approach is to
expose at least one endpoint for the core services that the application
uses and another for lower priority services, allowing different levels
of importance to be assigned to each monitoring result. Also consider
exposing more endpoints, such as one for each core service, for
additional monitoring granularity. For example, a health verification
check might check the database, storage, and an external geocoding
service that an application uses, with each requiring a different level
of uptime and response time. The application could still be healthy if
the geocoding service, or some other background task, is unavailable for
a few minutes.

Whether to use the same endpoint for monitoring as is used for general
access, but to a specific path designed for health verification checks,
for example, /HealthCheck/{GUID}/ on the general access endpoint. This
allows some functional tests in the application to be run by the
monitoring tools, such as adding a new user registration, signing in,
and placing a test order, while also verifying that the general access
endpoint is available.

The type of information to collect in the service in response to
monitoring requests, and how to return this information. Most existing
tools and frameworks look only at the HTTP status code that the endpoint
returns. To return and validate additional information, you might have
to create a custom monitoring utility or service.

How much information to collect. Performing excessive processing during
the check can overload the application and impact other users. The time
it takes might exceed the timeout of the monitoring system so it marks
the application as unavailable. Most applications include
instrumentation such as error handlers and performance counters that log
performance and detailed error information, this might be sufficient
instead of returning additional information from a health verification
check.

Caching the endpoint status. It could be expensive to run the health
check too frequently. If the health status is reported through a
dashboard, for example, you don\'t want every request from the dashboard
to trigger a health check. Instead, periodically check the system health
and cache the status. Expose an endpoint that returns the cached status.

How to configure security for the monitoring endpoints to protect them
from public access, which might expose the application to malicious
attacks, risk the exposure of sensitive information, or attract denial
of service (DoS) attacks. Typically this should be done in the
application configuration so that it can be updated easily without
restarting the application. Consider using one or more of the following
techniques:

-   Secure the endpoint by requiring authentication. You can do this by
    using an authentication security key in the request header or by
    passing credentials with the request, provided that the monitoring
    service or tool supports authentication.

    -   Use an obscure or hidden endpoint. For example, expose the
        endpoint on a different IP address to that used by the default
        application URL, configure the endpoint on a nonstandard HTTP
        port, and/or use a complex path to the test page. You can
        usually specify additional endpoint addresses and ports in the
        application configuration, and add entries for these endpoints
        to the DNS server if required to avoid having to specify the IP
        address directly.

    -   Expose a method on an endpoint that accepts a parameter such as
        a key value or an operation mode value. Depending on the value
        supplied for this parameter, when a request is received the code
        can perform a specific test or set of tests, or return a 404
        (Not Found) error if the parameter value isn\'t recognized. The
        recognized parameter values could be set in the application
        configuration.

        > DoS attacks are likely to have less impact on a separate
        > endpoint that performs basic functional tests without
        > compromising the operation of the application. Ideally, avoid
        > using a test that might expose sensitive information. If you
        > must return information that might be useful to an attacker,
        > consider how you\'ll protect the endpoint and the data from
        > unauthorized access. In this case just relying on obscurity
        > isn\'t enough. You should also consider using an HTTPS
        > connection and encrypting any sensitive data, although this
        > will increase the load on the server.

-   How to access an endpoint that\'s secured using authentication. Not
    all tools and frameworks can be configured to include credentials
    with the health verification request. For example, Microsoft Azure
    built-in health verification features can\'t provide authentication
    credentials. Some third-party alternatives
    are [Pingdom](https://www.pingdom.com/), [Panopta](https://www.panopta.com/), [NewRelic](https://newrelic.com/),
    and [Statuscake](https://www.statuscake.com/).

-   How to ensure that the monitoring agent is performing correctly. One
    approach is to expose an endpoint that simply returns a value from
    the application configuration or a random value that can be used to
    test the agent.

    > Also ensure that the monitoring system performs checks on itself,
    > such as a self-test and built-in test, to avoid it issuing false
    > positive results.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
When to use this Pattern
------------------------


 {.panelContent}
This pattern is useful for:

-   Monitoring websites and web applications to verify availability.
-   Monitoring websites and web applications to check for correct
    operation.
-   Monitoring middle-tier or shared services to detect and isolate a
    failure that could disrupt other applications.
-   Complementing existing instrumentation in the application, such as
    performance counters and error handlers. Health verification
    checking doesn\'t replace the requirement for logging and auditing
    in the application. Instrumentation can provide valuable information
    for an existing framework that monitors counters and error logs to
    detect failures or other issues. However, it can\'t provide
    information if the application is unavailable.





 {#expander-699638060 .expand-container}
 {#expander-control-699638060 .expand-control}
Log Deployments and Changes


 {#expander-content-699638060 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html).



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to understand the behavior of an application and troubleshoot
problems?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
-   It useful to see when deployments and other changes occur since
    issues usually occur immediately after a change



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Log every deployment and every change to the (production) environment.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
A deployment tool can, for example, publish [a
pseudo-metric](https://microservices.io/patterns/observability/application-metrics.html) whenever
it deploys a new version of a service. This metric can then be displayed
alongside other metrics enabling changes in application behavior to be
correlated with deployments. See [Tracking Every Release by Mike
Brittain](https://codeascraft.com/2010/12/08/track-every-release/)

[AWS Cloud
Trail](https://aws.amazon.com/cloudtrail/) provides logs
of AWS API calls.







 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**UI Patterns**


 {.panelContent}
 {#expander-877170538 .expand-container}
 {#expander-control-877170538 .expand-control}
Client-side UI composition


 {#expander-content-877170538 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html).
Services are developed by [business
capability](https://microservices.io/patterns/decomposition/decompose-by-business-capability.html)/[subdomain](https://microservices.io/patterns/decomposition/decompose-by-subdomain.html)-oriented
teams that are also responsible for the user experience. Some UI
screens/pages display data from multiple service. Consider, for example,
an Amazon-style product detail page, which displays numerous data items
including:

-   Basic information about the book such as title, author, price, etc.
-   Your purchase history for the book
-   Availability
-   Buying options
-   Other items that are frequently bought with this book
-   Other items bought by customers who bought this book
-   Customer reviews
-   Sellers ranking
-   ...

Each data item corresponds to a separate service and how it is displayed
is, therefore, the responsibility of a different team.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to implement a UI screen or page that displays data from multiple
services?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
\



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Each team develops a client-side UI component, such an AngularJS
directive, that implements the region of the page/screen for their
service. A UI team is responsible implementing the page skeletons that
build pages/screens by composing multiple, service-specific UI
components.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Resulting Context
-----------------


 {.panelContent}
\



\

\



 {#expander-1742022010 .expand-container}
 {#expander-control-1742022010 .expand-control}
Server-side page fragment composition


 {#expander-content-1742022010 .expand-content}
Author [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Context
-------


 {.panelContent}
You have applied the [Microservice architecture
pattern](https://microservices.io/patterns/microservices.html).
Services are developed by [business
capability](https://microservices.io/patterns/decomposition/decompose-by-business-capability.html)/[subdomain](https://microservices.io/patterns/decomposition/decompose-by-subdomain.html)-oriented
teams that are also responsible for the user experience. Some UI
screens/pages display data from multiple service. Consider, for example,
an Amazon-style product detail page, which displays numerous data items
including:

-   Basic information about the book such as title, author, price, etc.
-   Your purchase history for the book
-   Availability
-   Buying options
-   Other items that are frequently bought with this book
-   Other items bought by customers who bought this book
-   Customer reviews
-   Sellers ranking
-   ...

Each data item corresponds to a separate service and how it is displayed
is, therefore, the responsibility of a different team.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Problem
-------


 {.panelContent}
How to implement a UI screen or page that displays data from multiple
services?



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Solution
--------


 {.panelContent}
Each team developers a web application that generates the HTML fragment
that implements the region of the page for their service. A UI team is
responsible for developing the page templates that build pages by
performing server-side aggregation (e.g. server-side include style
mechanism) of the service-specific HTML fragments.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Forces
------


 {.panelContent}
\



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
Examples
--------


 {.panelContent}
\



\

\





 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Known Uses**


 {.panelContent}
Most large scale web sites
including [Netflix](http://techblog.netflix.com/), [Amazon](http://highscalability.com/blog/2007/9/18/amazon-architecture.html) and [eBay](http://www.addsimplicity.com/downloads/eBaySDForum2006-11-29.pdf) have
evolved from a monolithic architecture to a microservice architecture.

Netflix, which is a very popular video streaming service that's
responsible for up to 30% of Internet traffic, has a large scale,
service-oriented architecture. They handle over a billion calls per day
to their video streaming API from over 800 different kinds of devices.
Each API call fans out to an average of six calls to backend services.

[Amazon.com](http://amazon.com/) originally had a
two-tier architecture. In order to scale they migrated to a
service-oriented architecture consisting of hundreds of backend
services. Several applications call these services including the
applications that implement
the [Amazon.com](http://amazon.com/) website and the web
service API.
The [Amazon.com](http://amazon.com/) website application
calls 100-150 services to get the data that used to build a web page.

The auction site [ebay.com](http://ebay.com/) also
evolved from a monolithic architecture to a service-oriented
architecture. The application tier consists of multiple independent
applications. Each application implements the business logic for a
specific function area such as buying or selling. Each application uses
X-axis splits and some applications such as search use Z-axis
splits. [Ebay.com](http://ebay.com/) also applies a
combination of X-, Y- and Z-style scaling to the database tier.

There are [numerous other
examples](https://microservices.io/articles/whoisusingmicroservices.html) of
companies using the microservice architecture.



 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Best Practices**


 {.panelContent}
 {#expander-1531256043 .expand-container}
 {#expander-control-1531256043 .expand-control}
Best Practices


 {#expander-content-1531256043 .expand-content}
Author: [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

Designing Microservice Architecture the right way is quite challenging
and difficult. On contrary to Monolith Architecture which gives one
solution for all, Microservice Architecture gives a different solution
for different problems. If the wrong solution is chosen, then the
Microservice Architecture is just a ticking time bomb that is destined
to explode. A badly designed Microservice Architecture is worse than a
Monolith. Defining a set of Best practices for Microservice Architecture
is also challenging. I have seen some conference talks where some
renowned and respected Software Engineers have proposed Microservice
Architecture best practices which are counterproductive.

Here I am proposing some best practices which will help to develop
effective Microservice Applications where the target project is supposed
to live more than 6 months and team size is moderate to large (6+
developers). Full disclosure, there also some other posts regarding
Microservice Architecture best practices e.g. [**Characteristics of a
Microservice
Architecture**](https://martinfowler.com/articles/microservices.html#SynchronousCallsConsideredHarmful)** **by** **[***Martin
Fowler***](https://martinfowler.com/)** **or [**Microservices
Patterns**](https://microservices.io/patterns/microservices.html) by [***Chris
Richardson***](https://www.chrisrichardson.net/) or
Adopting [**Microservices at Netflix: Lessons for Architectural
Design**](https://microservices.io/patterns/microservices.html) by [**Tony
Mauro**](https://www.nginx.com/people/tony-mauro/).
There are also some great talks e.g. [**Microservices Patterns and
Antipatterns**](https://www.youtube.com/watch?v=RsyOkifmamI) by [***Stefan
Tilkov***](https://www.innoq.com/en/staff/stefan-tilkov/), [**10
Tips for failing badly at
Microservices**](https://www.youtube.com/watch?v=X0tjziAQfNQ) by **David
Schmitz**, [**Principles of
Microservices**](https://www.youtube.com/watch?v=PFQnNFe27kU) by [***Sam
Newman***](https://samnewman.io/).

\

 {#expander-1247220670 .expand-container}
 {#expander-control-1247220670 .expand-control}
1\. Domain Driven Design


 {#expander-content-1247220670 .expand-content}
The foremost challenge to develop Microservices is to split a large,
complex application into small, autonomous, independently deployable
Modules. If Microservices are not split in the right way, there will be
tightly coupled Microservices which will have all the disadvantages of a
Monolith and all the complexities of Microservices aka **Distributed
Monolith**. Fortunately, there is already a Solution which can greatly
help in this regard. [***Eric
Evans***](https://twitter.com/ericevans0?lang=en), a
Software Engineering Consultant back then, had encountered recurring
issues regarding software complexity in Business Applications across
different companies and has summarized his valuable insight in the book
"[**Domain Driven Design: Tackling Complexity in the Heart of
Software**](http://dddcommunity.org/book/evans_2003/)"
in 2004. The book outlined three Core Concepts:

-   The software development team should work in close co-operation with
    the Business department or Domain Experts.
-   The Architects/Developers and Domain Experts should first make the
    Strategic Design: Finding the Bounded Context and related Core
    Domain and Ubiquitous Language, Subdomains, Context Maps.
-   The Architects/Developers should then make the Tactical Design to
    decompose the Core Domain into fine-grained Building blocks: Entity,
    Value Object, Aggregate, Aggregate Root

A detail discussion of Domain-Driven Design is out of the scope of this
post but you should read either the original DDD book [**Domain Driven
Design: Tackling Complexity in the Heart of
Software**](http://dddcommunity.org/book/evans_2003/)** **(Blue
Book) of [***Eric
Evans***](https://twitter.com/ericevans0?lang=en) or a
bit modern DDD book [**Implementing Domain Driven
Design**](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/ref=sr_1_3?keywords=Domain+driven+design&qid=1574198067&s=books&sr=1-3)(Red
Book) of [***Vaughn
Vernon***](https://vaughnvernon.co/). If a large system
is divided into Core Domain and Sub-domains and the Core Domain and
Sub-domains are then mapped to one or more Microservices, then we will
get the ideal loosely coupled Microservices.



 {#expander-124158052 .expand-container}
 {#expander-control-124158052 .expand-control}
2\. Database per Microservice


 {#expander-content-124158052 .expand-content}
After splitting the Complex application into Micro-Service Modules, the
next challenge arises, what to do with the Database? Shall we share the
database among Microservices or not. The answer to the question is the
double edge sword. On the one hand, sharing the database among
microservices will lead to strong coupling among the Microservices which
is exactly the opposite of the goal of Microservices Architecture. Even
a small change in a database will need synchronization among teams.
Also, managing Transaction and Locking of a Database in one service is
challenging enough. But managing Transaction/Locking among multiple
distributed Microservices is a daunting task. On the other hand, if
every Microservice has own database/private tables, then exchanging data
between Microservices opens the pandora's box of challenges. As a
result, many prominent Software Engineers have advocated for a shared
database among Microservices as a pragmatic solution. However, in my
opinion, Microservice is all about sustainable and long term software
development. As a result, every Microservice should have its Database
(or Private Tables).



 {#expander-1797241143 .expand-container}
 {#expander-control-1797241143 .expand-control}
3\. Micro Frontends


 {#expander-content-1797241143 .expand-content}
Unfortunately, most of the Backend developers have a backdated view
about Frontend Development and think that Frontend Development is
simple. As most Software Architects are Backend Developers, they have
little regard for Frontend and Frontend is usually neglected in the
Architecture Design. Very often in Microservice projects, backends are
very finely modularized with their database but there is one Monolith
Frontend. In the best case, they consider one of the hottest SPA (React,
Angular, Vue) to develop the Monolith Frontend. The main problem of this
approach is that Frontend Monolith is as bad as Backend Monolith as I
have
described [**previously**](https://towardsdatascience.com/microservice-architecture-a-brief-overview-and-why-you-should-use-it-in-your-next-project-a17b6e19adfd).
Also, when the Frontend needs to be modernized due to changes in
Browser, then it requires a Big Bang modernization (*That is the reason
why so many companies are still using the outdated Angular 1
framework*). The web is simple yet very powerful and inherently offers
transclusion. There are many ways to develop SPA based Microfrontends:
with iFrame, Web Components or via (Angular/React) Elements.



 {#expander-1944774319 .expand-container}
 {#expander-control-1944774319 .expand-control}
4\. Continuous Delivery


 {#expander-content-1944774319 .expand-content}
One of the key USP of Microservice Architecture is that each
Microservice can be deployed independently. If you have a system of e.g.
100 Microservices and only one Microservice needs to be changed, then
you can update only one Microservice without touching the other 99. But
deploying 100 Microservices independently without Automation (DevOps,
CI/CD) is a daunting task. To take full advantage of this Microservice
feature, one needs CI/CD and DevOps. Using Microservice Architecture
without CI/CD, DevOps, Automation is like buying the latest Porsche and
then drive it with hand-brake. It is no wonder
that [**CI/CD**](https://martinfowler.com/bliki/MicroservicePrerequisites.html) is
listed as one of the three prerequisites to use Microservice
Architecture by Microservice Expert ***Martin Fowler***.



 {#expander-1530478627 .expand-container}
 {#expander-control-1530478627 .expand-control}
5\. Observability


 {#expander-content-1530478627 .expand-content}
One of the main drawbacks of Microservice Architecture is that Software
Development became simple at the expense of Operations. With one
Monolith, it is much simpler to monitor the application. But having many
microservices run on containers, observability of the whole system
became very crucial and complicated. Even Logging became complicated to
aggregate logs from many containers/machines into a central place.
Fortunately, there are already many Enterprise grade solutions in the
market. For example, **ELK/Splunk** offers Logging for
Microservices. **Prometheus/App Dynamics** offers industry-grade
monitoring. Another very crucial observability tool in the Microservice
world is Tracing. Often one API request to a microservice leads to
several cascaded calls to other microservices. To analyze the latency of
a Microservice system, it is necessary to measure the latency of each
individual Microservice. **Zipkin/Jaeger** offers excellent tracing
support for Microservices.



 {#expander-956363451 .expand-container}
 {#expander-control-956363451 .expand-control}
6\. Unified Tech Stack


 {#expander-content-956363451 .expand-content}
Microservice Architecture tells us that for a Microservice, take the
programming language and framework best suitable for that microservice.
This statement should not be taken literally. Sometime, a microservice
may need a new Tech Stack e.g. for CPU heavy/high-performance tasks,
programming language like C++/Rust may be chosen. If a Microservice
works with Machine learning, maybe Python is a better choice. But using
different programming languages/frameworks without any solid reason can
lead to too many programming languages and frameworks without any real
benefit. Think about the scenario where one microservice is developed
using Spring Boot + Kotlin+ React + MySQL, the other one is with
JakartaEE + Java + Angular + PostgreSQL, the next one with Scala + Play
Framework + VueJS + Oracle then it will need a lots of effort to
maintain the different programming language, databases, frameworks
without too much gain.



 {#expander-1732171813 .expand-container}
 {#expander-control-1732171813 .expand-control}
7\. Asynchronous Communications


 {#expander-content-1732171813 .expand-content}
One of the most challenging design decisions in Microservice
Architecture is how the services will communicate and share data among
themselves. This is even more important when each Microservice has its
own Data Storage. Typically, one Microservice can exist along but it
cannot fulfill all the business goals alone. All the Microservices work
together to fulfill the Business goal and to work together, they need to
exchange data or trigger other Microservices to do a task. The easiest
and most common way to communicate between Microservices is via
Synchronous REST API which is pragmatic but a short term solution. If
Service A calls Service B, Service B calls Service C, Service C calls
service D Synchronously, then latencies added up. Also as Microservices
are mostly distributed systems, they could fail. Often Synchronous
Microservices lead to failure cascading i.e. Failure in one Service can
lead to failure in other services. Synchronous Communication between
Microservices also leads to tight coupling between Microservices. For a
long term solution, Microservices should communicate Asynchronously.
There are many ways for Asynchronous communication between
Microservices: via Message Queue e.g. Kafka, via asynchronous REST
(ATOM) or CQRS.



 {#expander-2115820046 .expand-container}
 {#expander-control-2115820046 .expand-control}
9\. Infrastructure over Libraries


 {#expander-content-2115820046 .expand-content}
During the early days of Microservice Software development, Netflix used
mainly Java programming to develop Microservices. They also developed
many libraries (Netflix OSS Stack including Hystrix, Zuul). Many
companies follow through Netflix and started to use the librariesNetflix
OSS. Later, many companies (including Netflix) found that Java is not
the de facto language to develop Microservices due to its Bulky size and
Cold-start problems. Netflix later moved on Polyglot Microservice
paradigm and decided not to develop the Netflix OSS further which lead
the follower companies into trouble. So, instead of investing heavily in
a language-specific library (e.g. Java based Netflix OSS), it is wiser
to use frameworks (e.g. Service Meshes, API gateway).\



 {#expander-1241811987 .expand-container}
 {#expander-control-1241811987 .expand-control}
10\. Organizational Considerations


 {#expander-content-1241811987 .expand-content}
Almost 50 years ago (1967), [Melvin
Conway](https://en.wikipedia.org/wiki/Melvin_Conway) gave
an observation that the Software Architecture of a company is limited by
Organizational Structure (Conway's Law). Although the observation is 50
years old, MIT and Harvard Business School have recently found that the
law is still valid in modern days. If an organization plans to develop
Microservice Architecture, then it should make the team size accordingly
(two "American" Pizza team: 7±2 person). Also, the team should be
cross-functional and ideally will have Frontend/Backend Developer, Ops
Engineering and Tester. Microservice Architecture will only work if the
higher Management also changes their viewpoint and vision accordingly.\



\

\

\

 {#expander-755070292 .expand-container}
 {#expander-control-755070292 .expand-control}
References


 {#expander-content-755070292 .expand-content}
-   [Towards Data Science - microservice architecture a brief overview
    and why you should use it in your next
    project](https://towardsdatascience.com/microservice-architecture-a-brief-overview-and-why-you-should-use-it-in-your-next-project-a17b6e19adfd)



\

\

\





 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Anti Patterns**


 {.panelContent}
 {#expander-84692369 .expand-container}
 {#expander-control-84692369 .expand-control}
Anti Patterns


 {#expander-content-84692369 .expand-content}
Author: [Ryan
Kajiura](https://wiki.pinnacle.com/display/~ryank){.confluence-userlink
.user-mention .current-user-mention}

\

 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Design**


 {.panelContent}
 {#expander-1012865696 .expand-container}
 {#expander-control-1012865696 .expand-control}
Data-Driven Migration AntiPattern


 {#expander-content-1012865696 .expand-content}
Microservices is about creating lots of small, distributed
single-purpose services, with each service owning its own data. This
service and data coupling supports the notion of a bounded context and a
share-nothing architecture, where each service and its corresponding
data are compartmentalized and completely independent from all other
services, exposing only a well-defined interface (the contract). This
bounded context is what allows for quick and easy development, testing,
and deployment with minimal dependencies.

The data-driven migration antipattern occurs mostly when you are
migrating from a monolithic application to a microservices architecture.
The reason this is an antipattern is that it seems like a good idea at
the start to migrate both the service functionality and the
corresponding data together when creating microservices, but as you will
learn in this chapter, this will lead you down a bad path that can
result in high risk, excess cost, and additional migration effort. 

There are two primary goals during any microservices conversion effort.
The first goal is to split the functionality of the monolithic
application into small, single-purpose services. The second goal is to
then migrate the monolithic data into small databases (or separate
schemas) owned by each
service. [Figure 1-1](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_101) shows
what a typical migration might look like when both the service code and
the corresponding data are migrated at the same time.

\

![](https://d3ansictanv2wj.cloudfront.net/mapr_0101-1691c33f307ff43a4a6756e744196034.png){.confluence-embedded-image
.iimagesdata-driven-1png .confluence-external-resource
.confluence-content-image-border height="400"}

Figure 1-1. Service and data migration

Notice there are three services created from the monolithic application
along with three separate databases. This is a natural migration process
because you are creating that critical bounded context between each
service and its corresponding data. However, problems start to arise
with this common practice, thus leading you into the data-driven
migration antipattern.



 {#expander-404561627 .expand-container}
 {#expander-control-404561627 .expand-control}
Too Many Data Migrations


 {#expander-content-404561627 .expand-content}
The main problem with this type of migration path is that you will
rarely get the granularity of each service right the first time. Knowing
it is always a good idea to start with a more coarse-grained service and
split it up further if needed when you learn more about the service, you
may be frequently adjusting the granularity of your services. Consider
the migration illustrated
in [Figure 1-1](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_101),
focusing on the leftmost service. Let\'s say after learning more about
the service you discover it\'s too coarse-grained and needs to be split
up into two smaller services. Alternatively, you may find that the two
leftmost services are too fine-grained and need to be consolidated. In
either case you are faced with two migration efforts---one for the
service functionality and another for the database. This scenario is
illustrated
in [Figure 1-2](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_102).

![](https://d3ansictanv2wj.cloudfront.net/mapr_0102-d855332b87b6d933ed19a6e1e63f988c.png){.confluence-embedded-image
.iimagesdata-driven-2apng .confluence-external-resource
.confluence-content-image-border height="400"}

Figure 1-2. Extra data migration after service granularity adjustment

My good friend and fellow O\'Reilly author Alan Beaulieu (*Learning
SQL*) once told me \"Data is a corporate asset, not an application
asset.\" Given Alan\'s statement, you can gain an appreciation for the
risk involved and the concerns raised with continually migrating data.
Data migrations are complex and error-prone---much more so than source
code migrations. Optimally you want to migrate the data for each service
only once. Understanding the risks involved with data migration and the
importance of \"data over functionality\" is the first step in avoiding
this antipattern.



 {#expander-1076719722 .expand-container}
 {#expander-control-1076719722 .expand-control}
Functionality First, Data Last


 {#expander-content-1076719722 .expand-content}
The primary avoidance technique for this antipattern is to migrate the
functionality of the service first, and worry about the bounded context
between the service and the data later. Once you learn more about the
service you will likely find the need to adjust the level of granularity
through service consolidation or service splitting. After you are
satisfied that you have the level of granularity correct, then migrate
the data, thereby creating the much-needed bounded context between the
service and the data.

This technique is illustrated
in [Figure 1-3](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_103).
Notice how all three services have been migrated, but are still
connecting to the monolithic data. This is perfectly fine for an interim
solution, because now you can learn more about how the service is used
and what type of requests will be handled by each service.

![](https://d3ansictanv2wj.cloudfront.net/mapr_0103-a1612b6cf55fa76e3bf16720379b5092.png){.confluence-embedded-image
.iimagesdata-driven-4apng .confluence-external-resource
.confluence-content-image-border height="400"}

Figure 1-3. Migrate service functionality first, then data portion later

![](https://d3ansictanv2wj.cloudfront.net/mapr_0201-dbf84b2d7ad3988944fba173326ee193.png){.confluence-embedded-image
.iimagestimeout-1png .confluence-external-resource
.confluence-content-image-border height="250"}

\

In [Figure 1-3](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_103),
notice how the service was found to be too coarse-grained and was
consequently split into two smaller services. Now that the granularity
is correct, the data can be migrated to create the bounded context
between the service and the corresponding data. This technique avoids
costly and repeated data migrations and makes it easier to adjust the
service granularity when needed. While it is impossible to say how long
to wait before migrating the data, it is important to understand the
consequences of this avoidance technique---a poor bounded context. The
time between when the service is created and the data is finally
migrated creates a data coupling between services. This means that when
the database schema is changed, all services using that schema must be
coordinated from a change control and release standpoint, something you
want to avoid with the microservices architecture. However, this
tradeoff is well worth the reduced risk involved with avoiding multiple
costly database migrations. 



 {#expander-1590839294 .expand-container}
 {#expander-control-1590839294 .expand-control}
The Timeout AntiPattern


 {#expander-content-1590839294 .expand-content}
Microservices is a distributed architecture, meaning all of the
components (i.e., services) are deployed as separate applications and
are accessed remotely through some sort of remote access protocol. One
of the challenges of any distributed architecture is managing remote
process availability and responsiveness. Although service availability
and service responsiveness are both related to service communication,
they are two very different things. Service availability is the ability
of the service consumer to connect with the service and be able to send
it a request, as shown
in [Figure 2-1](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_201).
Service responsiveness, on the other hand, is the time it takes for the
service to respond to a given request once you\'ve communicated with it.

Figure 2-1. Service availability vs. responsiveness

If the service consumer cannot connect with or talk to the service
(i.e., availability), the service consumer is usually immediately
notified within milliseconds,
as [Figure 2-1](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_201) shows.
The service consumer may choose to pass this error onto the client or
retry the connection several times before giving up and throwing some
sort of connection failure. However, assuming the service was reached
and a request was made, what happens if the service doesn\'t respond? In
this case the service consumer can choose to wait indefinitely or
leverage some sort of timeout value.

Using a timeout value for service responsiveness seems like a good idea,
but can lead you down a bad path known as the timeout anti-pattern.



 {#expander-709195348 .expand-container}
 {#expander-control-709195348 .expand-control}
Using Timeout Values


 {#expander-content-709195348 .expand-content}
You might be a bit confused at this point. After all, isn\'t setting a
timeout value a good thing? Maybe, but in most cases it can lead you
down a bad path. Consider the example where you are making a service
request to buy 1000 shares of Apple stock (AAPL). The very last thing
you want to do as the service consumer is time out the request right
when the service has successfully placed the trade and is about to give
you a confirmation number. You can try to resubmit the trade, but you
have to add significant complexity into your service to determine if
this is a new trade or a duplicate trade. Furthermore, since you don\'t
have a confirmation number from the first trade it is very difficult to
know whether the trade was actually successful or not.

So, given that you don\'t want to time out the request too early, what
should the timeout value be? There are several techniques to address
this problem. The first is to calculate the database timeout within the
service and use that as a base for determining what the service timeout
should be. The second solution, which is by far the most popular
technique, is to calculate the maximum time under load and double it,
thereby giving you that extra buffer in the event it sometimes takes
longer.

[Figure 2-2](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_202) illustrates
this technique. Notice that on average the service responds within 2
seconds to place a trade. However, under load the maximum time observed
is 5 seconds. Therefore, using the doubling technique, the timeout value
for the service consumer would be 10 seconds. Again, the intention with
this technique is to avoid timing out the request when in fact it was
successful and was in the process of sending you back the confirmation
number.

![](https://d3ansictanv2wj.cloudfront.net/mapr_0202-24f51f9c4f7e334861b69ca641e5c605.png){.confluence-embedded-image
.iimagestimeout-2png .confluence-external-resource
.confluence-content-image-border height="250"}

Figure 2-2. Calculating a timeout value

It should be clear now why this approach is an antipattern. While this
seems like a perfectly logical solution to the timeout problem, it
causes *every request* from service consumers to have to wait 10 seconds
just to find out the service is not responsive. Ten seconds is a long
time to wait for an error. In most cases users won\'t wait more than 2
to 3 seconds before hitting the submit button again or giving up and
closing the screen. There must be a better way to deal with server
responsiveness.



 {#expander-52626805 .expand-container}
 {#expander-control-52626805 .expand-control}
Using the Circuit Breaker Pattern


 {#expander-content-52626805 .expand-content}
Rather than relying on timeout values for your remote service calls, a
better approach is to use something called the *circuit breaker
pattern*. This software pattern works just like a circuit breaker in
your house. When it is closed, electricity flows through it, but once it
is open, no electricity can pass until the breaker is closed. Similarly,
if a software circuit breaker detects that a service is not responding,
it will open, rejecting requests to that service. Once the service
becomes responsive, the breaker will close, allowing requests through.

[Figure 2-3](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_203) illustrates
how the circuit breaker pattern works. The circuit breaker continually
monitors the remote service, ensuring that it is alive and responsive
(more on that part later). While the service remains responsive the
breaker will be closed, allowing requests through. If the remote service
suddenly becomes unresponsive, the circuit breaker opens, thus
preventing requests from going through until the service once again
becomes responsive. However, unlike the circuit breaker in your house, a
software circuit breaker can continue monitoring the service and close
itself once the remote service becomes responsive again.

![](https://d3ansictanv2wj.cloudfront.net/mapr_0203-f6181a9a1ef2e1cf22272aa45b15c0fd.png){.confluence-embedded-image
.iimagestimeout-3png .confluence-external-resource
.confluence-content-image-border height="250"}

Figure 2-3. Circuit breaker pattern

Depending on the implementation, the service consumer will always check
with the circuit breaker first to see if it is open or closed. This can
also be done through an interceptor pattern so the service consumer
doesn\'t need to know the circuit breaker is in the request path. In
either case, the significant advantage of the circuit breaker pattern
over timeout values is that the service consumer knows right away that
the service has become unresponsive rather than having to wait for the
timeout value. In the prior example, if a circuit breaker was used
instead of the timeout value, the service consumer would know within
milliseconds that the trade-placement service was not responsive rather
than having to wait 10 seconds (10,000 milliseconds) to get the same
information. 

Circuit breakers can monitor the remote service in several ways. The
simplest way is to do a simple heartbeat check on the remote service
(e.g., ping). While this is relatively easy and inexpensive, all it does
is tell the circuit breaker that the remote service is alive, but says
nothing as to the responsiveness of the actual service request. To get
better information about the responsiveness of the request you can use
synthetic transactions. A synthetic transaction is another monitoring
technique circuit breakers can use where a fake transaction is
periodically sent to the service (e.g., once every 10 seconds). The fake
transaction performs all of the functionality required within that
service, allowing the circuit breaker to gain an accurate measure of
responsiveness. Synthetic transactions can be very tricky and difficult
to implement in that all parts of the application or system need to know
about the synthetic transaction. A third type of monitoring is real-time
user monitoring, where actual production transactions are monitored for
responsiveness. Once a threshold is reached, the breaker moves into what
is called a half-open state, where only a certain number of transactions
are let through (say 1 out of 10). Once the service responsiveness goes
back to normal, the breaker is then closed, allowing all transactions
through. 

There are several open source implementations of the circuit breaker
pattern, including Hystrix from Netflix and a plethora of GitHub
implementations. The [Akka
framework](http://www.akka.io/) includes a circuit
breaker implementation as part of the framework implemented through the
Akka `CircuitBreaker` class.



 {#expander-429074790 .expand-container}
 {#expander-control-429074790 .expand-control}
The \"I Was Taught to Share\" AntiPattern


 {#expander-content-429074790 .expand-content}
Microservices is known as a \"share-nothing\" architecture.
Pragmatically, I prefer to think of it as a
\"share-as-little-as-possible\" architecture because there will always
be some level of code that is shared between microservices. For example,
rather than having a security service that is responsible for
authentication and authorization, you might have the source code and
security functionality wrapped in a JAR file named *security.jar* that
all services use. Assuming security is handled at the services level,
this is generally a good practice because it eliminates the need to make
a remote call to a security service for every request, thereby
increasing both performance and reliability.

However, taken too far, you end up with a dependency nightmare as
illustrated
in [Figure 3-1](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_301),
where every service is dependent on multiple custom shared libraries.

![](https://d3ansictanv2wj.cloudfront.net/mapr_0301-f22b1304590c1e0f709bc503083918ef.png){.confluence-embedded-image
.iimagesshare-1png .confluence-external-resource
.confluence-content-image-border height="250"}

Figure 3-1. Sharing multiple custom libraries

This level of sharing not only breaks down the bounded context of each
service, but also introduces several issues, including overall
reliability, change control, testability, and deployment.



 {#expander-382306027 .expand-container}
 {#expander-control-382306027 .expand-control}
Too Many Dependencies


 {#expander-content-382306027 .expand-content}
If you consider how most object-oriented software applications are
developed, it\'s not hard to see the issues with sharing, particularly
when migrating from a monolithic layered architecture to a microservices
one. One of the things to strive for in most monolithic applications is
code reuse and
sharing. [Figure 3-2](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_302) illustrates
the two main artifacts (abstract classes and shared utilities) that end
up being shared in most monolithic layered architectures.

![](https://d3ansictanv2wj.cloudfront.net/mapr_0302-737e345baac230f8d2d858fb3588a826.png){.confluence-embedded-image
.iimagesshare-2png .confluence-external-resource
.confluence-content-image-border height="400"}

Figure 3-2. Sharing inheritance structures and utility classes

While creating abstract classes and interfaces is a common practice with
most object-oriented programming languages, they get in the way when
trying to migrate modules to a microservices architecture. The same goes
with custom shared classes and utilities such as common date or string
utilities and calculation utilities. What do you do with the code that
needs to be shared by potentially hundreds of services?

One of the primary goals of the microservices architecture style is to
share as little as possible. This helps preserve the bounded context of
each service, which is what gives you the ability to do quick testing
and deployment. With microservices it all boils down to change control
and dependencies. The more dependencies you have between services, the
harder it is to isolate service changes, making it difficult to
separately test and deploy individual services. Sharing too much creates
too many dependencies between services, resulting in brittle systems
that are very difficult to test and deploy.



 {#expander-1091191815 .expand-container}
 {#expander-control-1091191815 .expand-control}
Techniques for Sharing Code


 {#expander-content-1091191815 .expand-content}
It\'s easy to say the best way to avoid this antipattern is simply not
to share code between services. But, as I stated at the start of this
chapter, pragmatically there will always be some code that needs to be
shared. Where should that shared code go?

[Figure 3-3](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_303) illustrates
the four basic techniques for addressing the problem of code sharing:
shared projects, shared libraries, replication, and service
consolidation.

![](https://d3ansictanv2wj.cloudfront.net/mapr_0303-01d235fa9dce344af9b47b4a83906185.png){.confluence-embedded-image
.iimagesshare-3png .confluence-external-resource
.confluence-content-image-border height="400"}

Figure 3-3. Module-sharing techniques

Using a shared project forms a compile-time binding between common
source code that is located in a shared project and each service
project. While this makes it easy to change and develop software, it is
my least favorite sharing technique because it causes potential issues
and surprises during runtime, making applications less robust. The main
issue with the shared project technique is that of communication and
control---it is difficult to know what shared modules changed and why,
and also hard to control whether you want that particular change or not.
Imagine being ready to release your microservice just to find out
someone made a breaking change to a shared module, requiring you to
change and retest your code prior to deployment.

A better approach if you have to share code is to use a shared library
(e.g., .NET assembly or JAR file). This approach makes development more
difficult because for each change made to a module in a shared library,
the developer must first create the library, then restart the service,
and then retest. However, the advantage of the shared library technique
is that libraries can be versioned, providing better control over the
deployment and runtime behavior of a service. If a change is made to a
shared library and versioned, the service owner can make decisions about
when to incorporate that change.

A third technique that is common in a microservices architecture is to
violate the don\'t-repeat-yourself (DRY) principle and replicate the
shared module across all services needing that particular functionality.
While the replication technique may seem risky, it avoids dependency
sharing and preserves the bounded context of a service. Problems arise
with this technique when the replicated module needs to be changed,
particularly for a defect. In this case all services need to change.
Therefore, this technique is only really useful for very stable shared
modules that have little or no change.

A fourth technique that is sometimes possible is to use service
consolidation. Let\'s say two or three services are all sharing some
common code, and those common modules frequently change. Since all of
the services must be tested and deployed with the common module change
anyway, you might as well just consolidate the functionality into a
single service, thereby removing the dependent library.

One word of advice regarding shared libraries---avoid combining all of
your shared code into a single shared library like *common.jar*. Using a
common library makes it difficult to know whether you need to
incorporate the shared code and when. A better technique is to separate
your shared libraries into ones that have context. For example, create
context-based libraries
like *security.jar*, *persistence.jar*, *dateutils.jar*, and so on. This
separates code that doesn\'t change often from code that changes
frequently, making it easier to determine whether or not to incorporate
the change right away and what the context of the change was.



 {#expander-471765768 .expand-container}
 {#expander-control-471765768 .expand-control}
Reach-in Reporting AntiPattern


 {#expander-content-471765768 .expand-content}
With the microservices architecture style, services and the
corresponding data are contained within a single bounded context,
meaning that the data is typically migrated to separate databases (or
schemas). While this works well for services, it plays havoc with
respect to reporting within a microservices architecture.

There are four main techniques for handling reporting in a microservices
architecture: the database pull model, HTTP pull model, batch pull
model, and finally the event-based push model. The first three
techniques pull data from each of the service databases, hence the
antipattern name \"reach-in reporting.\" Since the first three models
represent the problem associated with this antipattern, let\'s take a
look at those techniques first to see why they lead you into trouble.



 {#expander-2139077687 .expand-container}
 {#expander-control-2139077687 .expand-control}
Issues with Microservices Reporting


 {#expander-content-2139077687 .expand-content}
The problem with reporting is two-fold: how do you obtain reporting data
in a timely manner and still maintain the bounded context between the
service and its data? Remember, the bounded context within microservices
includes the service and its corresponding data, and it is critical to
maintain it.

One of the ways reporting is typically handled in a microservices
architecture is to use what is known as the *database pull model*, where
a reporting service (or reporting requests) pulls the data directly from
the service databases. This technique is illustrated
in [Figure 4-1](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_401).

![](https://d3ansictanv2wj.cloudfront.net/mapr_0401-a7a59563a7133ee4938c443d340796b5.png){.confluence-embedded-image
.iimagesreporting-1png .confluence-external-resource
.confluence-content-image-border height="250"}

Figure 4-1. Database pull-reporting model

Logically, the fastest and easiest way to get timely data is to access
it directly. While this may seem like a good idea at the time, it leads
to significant interdependencies between services and the reporting
service. This is a typical implementation of the shared database
integration style, which couples applications together through a shared
database. This means that the services no longer own their data. Any
service database schema change or database refactoring must include
reporting service modifications as well, breaking that important bounded
context between the service and the data.

The way to avoid the issue of data coupling is to use another technique
called the *HTTP pull model*. With this model, rather than accessing
each service database directly, the reporting service makes a restful
HTTP call to each service, asking for its data. This model is
illustrated
in [Figure 4-2](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_402).

![](https://d3ansictanv2wj.cloudfront.net/mapr_0402-e19c666b435bddd479fc979b169fafeb.png){.confluence-embedded-image
.iimagesreporting-2png .confluence-external-resource
.confluence-content-image-border height="250"}

Figure 4-2. HTTP pull-reporting model

While this model preserves the bounded context of each service, it is
unfortunately too slow, particularly for complex reporting requests.
Furthermore, depending on the report being requested, the data volume
might be too large of a payload for a simple HTTP call.

A third option in response to the issues associated with the HTTP pull
model is to use the batch pull model illustrated
in [Figure 4-3](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_403).
Notice that this model uses a separate reporting database or data
warehouse that contains the aggregated and reduced reporting data. The
reporting database is usually populated through a batch job that runs in
the evening to extract all reporting data that has changed, aggregate
and reduce that data, and insert it into the reporting database or data
warehouse.

![](https://d3ansictanv2wj.cloudfront.net/mapr_0403-57f5f96c50ff3bbcb8090d8a40179562.png){.confluence-embedded-image
.iimagesreporting-3png .confluence-external-resource
.confluence-content-image-border height="250"}

Figure 4-3. Batch pull-reporting model

The batch pull model shares the same issue with the HTTP pull
model---they both implement the shared database integration
style---therefore breaking the bounded context of each service. If the
service database schema changes, so must the batch data upload process.



 {#expander-33265671 .expand-container}
 {#expander-control-33265671 .expand-control}
Asynchronous Event Pushing


 {#expander-content-33265671 .expand-content}
The solution for avoiding the reach-in reporting antipattern is to use
what is called an *event-based push model*. Sam Newman, in his
book *Building Microservices*, refers to this technique as a data pump.
This model, which is illustrated
in [Figure 4-4](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_404),
relies on asynchronous event processing to make sure the reporting
database has the right information as soon as possible.

![](https://d3ansictanv2wj.cloudfront.net/mapr_0404-5e3d704e2514e97a18cc37967dbb1b45.png){.confluence-embedded-image
.iimagesreporting-4png .confluence-external-resource
.confluence-content-image-border height="250"}

Figure 4-4. Event-based push-reporting model

While it is true that the event-based push model is relatively complex
to implement, it does preserve the bounded context of each service while
at the same time ensuring a reasonable timeliness of data. Like the
batch pull model, this model also has a separate reporting database
owned by the reporting service. However, rather than a batch process
pulling data, each microservice asynchronously sends its notable data
updates (e.g., the data the reporting service needs) as a separate event
to a data-capture service, which then reduces the data and updates the
reporting database.

The event-based push model requires a contract between each microservice
and the data capture service for the data it is asynchronously sending,
but that contract is separate from the database schema owned by the
service. However, the services are somewhat coupled in that each service
must know when to send what information for reporting purposes.

In the chart
in [Figure 4-5](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_405),
you can see that the database pull model maximizes on timeliness of
data, but breaks the bounded context. The HTTP pull model preserves the
bounded context, but has issues associated with timeouts and data
volume. The batch pull model turns out to be the least-desirable model
out of the four options because optimizes neither the bounded context
nor the timeliness of data. Only the event-based push model maximizes
both the bounded context of each service and the timeliness of reporting
data.

\

![](https://d3ansictanv2wj.cloudfront.net/mapr_0405-045896b43f3d055a16b0fb5e555c47a3.png){.confluence-embedded-image
.iimagesreporting-5png .confluence-external-resource
.confluence-content-image-border height="250"}

Figure 4-5. Comparing reporting models



 {#expander-650232264 .expand-container}
 {#expander-control-650232264 .expand-control}
Grains of Sand Pitfall


 {#expander-content-650232264 .expand-content}
Perhaps one of the biggest challenges architects and developers face
when creating applications using a microservices architecture is service
granularity. How big should a service be? How small should it be?
Choosing the right level of granularity for your services is critical to
the success of any microservices effort. Service granularity can impact
performance, robustness, reliability, change control, testability, and
even deployment.

The *grains of sand pitfall* occurs when architects and developers
create services that are too fined-grained. Wait---isn\'t that why it\'s
called *micro*services in the first place? The word \"micro\" implies
that a service should be very small, but how small is \"small\"?

One of the primary reasons this pitfall occurs is because developers
often confuse a *service* with a *class*. Too many times I\'ve seen
development teams create services by thinking that the implementation
class they\'re writing is actually the service. Nothing could be further
from the truth. 

A service should always be thought of as a *service component*. A
service component is a component of the architecture that performs a
specific function in the system. The service component should have a
clear and concise roles and responsibility statement and have a
well-defined set of operations. It is up to the developer to
decide *how* the service component should be implemented and how many
implementation classes are needed for the service.

As [Figure 5-1](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_501) shows,
a service component is implemented through one or more modules (e.g.,
Java classes). Implementing a service component using a one-to-one
relationship between a module and a service component not only lends
itself toward components that are too fine-grained, it also leads to
poor programming practices as well. Services implemented through a
single class tend to have classes that are too big and carry too much
responsibility, making them hard to maintain and test.

![](https://d3ansictanv2wj.cloudfront.net/mapr_0501-664db0319ecaca44fe861eb5f617bb32.png){.confluence-embedded-image
.iimagessand-1png .confluence-external-resource
.confluence-content-image-border height="250"}

Figure 5-1. Relationship between modules and a service

The number of implementation classes should not be a defining
characteristic for determining the granularity of a service. Some
services may only need a single class file to implement all of the
business functionality, whereas others may need six or more classes.

If the number of implementation classes has no impact on the granularity
of a service, then what does? Fortunately, there are three basic tests
you can use to determine the right level of granularity for your
services: the service scope and functionality, the need for database
transactions, and finally the level of service choreography.



 {#expander-2101381227 .expand-container}
 {#expander-control-2101381227 .expand-control}
Analyzing Service Scope and Function


 {#expander-content-2101381227 .expand-content}
The first way to determine whether your services have the right level of
granularity is to analyze the scope and function of the service. What
does the service do? What are its operations? Documenting or verbally
stating the service scope and function is a great way to determine if
the service is doing too much. Using words like \"and\" and \"in
addition\" is usually a good indicator that the service is probably
doing too much.

Cohesion also plays a role with regards to the service scope and
function. Cohesion is defined as the degree and manner to which the
operations of the service are interrelated. You want to strive for
strong cohesion within your services. For example, let\'s say you have a
customer service with the following operations:

-   add\_customer
-   update\_customer
-   get\_customer
-   notify\_customer
-   record\_customer\_comments
-   get\_customer\_comments

In this example the first three operations are interrelated as they all
pertain to maintaining and retrieving customer information. However, the
last three (notify\_customer, record\_customer\_comments, and
get\_customer\_comments) do not relate to basic CRUD operations on basic
customer data. In analyzing the level of cohesion of the operations in
this service, it becomes clear that the original service should perhaps
be split into three separate services (customer maintenance, customer
notification, and customer comments).

[Figure 5-2](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_502) illustrates
the point that, in general, when analyzing the service scope and
function you will likely find that your services are too coarse-grained
and you will move toward services that are more fine-grained.

![](https://d3ansictanv2wj.cloudfront.net/mapr_0502-9be9f37a8cf617b1fda9e83ff72847c8.png){.confluence-embedded-image
.iimagessand-2png .confluence-external-resource
.confluence-content-image-border height="150"}

Figure 5-2. Impact of analyzing service functionality and scope

Sam Newman offers some good solid advice in this area---start out more
coarse-grained and move to fine-grained as you learn more about the
service. Following this advice will help you get started in defining
your service components without having to worry so much about the
granularity right away.

While analyzing the service scope and functionality is a good start, you
don\'t want to stop there. After looking at the service scope, you need
to then analyze your database transaction needs.



 {#expander-2095193740 .expand-container}
 {#expander-control-2095193740 .expand-control}
Analyzing Database Transactions


 {#expander-content-2095193740 .expand-content}
Another test for validating the level of service granularity is the need
for database transactions for certain operations. Database transactions
are more formally referred to as ACID transactions (atomicity,
consistency, isolation, and durability). ACID transactions coordinate
multiple database updates into a single unit of work. The database
updates are either committed as a whole unit or rolled back if an error
condition occurs.

Because services in a microservices architecture are distributed and
deployed as separate applications, it is extremely difficult to maintain
an ACID transaction between two or more remote services. For this
reason, microservices architectures generally rely on a technique known
as BASE transactions (basic availability, soft state, and eventual
consistency). Regardless, there will usually be times where you do
require an ACID transaction for certain business operations. If you find
you are constantly battling issues surrounding ACID vs. BASE
transactions and you need to coordinate multiple updates, chances are
you have made your services too fine-grained.

When analyzing your transaction needs and find that you can\'t live with
eventual consistency you will generally move from fine-grained services
to more coarse-grained ones, thereby keeping multiple updates
coordinated within a single service context, as illustrated
in [Figure 5-3](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_503).

![](https://d3ansictanv2wj.cloudfront.net/mapr_0503-be24bd98df9293d6521d884c01eb922f.png){.confluence-embedded-image
.iimagessand-3png .confluence-external-resource
.confluence-content-image-border height="250"}

Figure 5-3. Impact of analyzing database transactions

Notice that from an ACID transaction standpoint it doesn\'t matter
whether you consolidate the separate databases or keep them as
individual ones. Generally you will want to consolidate the databases as
well, but this is not a requirement to maintain an ACID transaction
(assuming the databases and the transaction manager you are using
support XA---e.g., two-phase commit---transactions).

Once you have analyzed your transaction needs, it\'s time to move on to
the third test, service choreography.



 {#expander-81344317 .expand-container}
 {#expander-control-81344317 .expand-control}
Analyzing Service Choreography


 {#expander-content-81344317 .expand-content}
A third test you can use to validate the level of service granularity
is *service choreography*. Service choreography refers to the
communication between services, also commonly referred to as
inter-service communication. Service choreography is generally something
you want to be careful of within in a microservices architecture. First
of all, it decreases the overall performance of your application since
each call to another service is a remote call. For example, assuming it
takes 100 milliseconds to make a restful call to another service, making
five remote service calls is a half a second spent *just in remote
access time*.

The other issue with too much service choreography is that it can impact
the overall reliability and robustness of your system. The more remote
calls you make for a single business request, the better the chances are
that one of those remote calls will fail or time out.

If you find you are having to communicate with too many services to
complete single business requests, then you\'ve probably made your
services too fine-grained. When analyzing the level of service
choreography, you will generally move from fine-grained services to ones
that are more coarse-grained, as illustrated
in [Figure 5-4](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_504).

![](https://d3ansictanv2wj.cloudfront.net/mapr_0504-582836e8a516762ca9e6bbea1e8e7562.png){.confluence-embedded-image
.iimagessand-4png .confluence-external-resource
.confluence-content-image-border height="400"}

Figure 5-4. Impact of analyzing service choreography

By consolidating services and moving to more coarse-grained services you
can improve performance and increase the overall reliability and
robustness of your applications. You also remove dependencies between
services, allowing for better change control, testing, and deployment.

The other approach when dealing with service choreography to help
overcome the performance and reliability issues is to leverage
asynchronous parallel processing combined with reactive architecture
techniques for error handling. Executing multiple requests at the same
time increases overall responsiveness, allowing you to coordinate
multiple services in a single business request in a timely fashion. The
key point here is to understand and analyze the trade-offs associated
with service choreography to ensure both sufficient responsiveness to
the user and sufficient overall reliability of your system.



 {#expander-180550477 .expand-container}
 {#expander-control-180550477 .expand-control}
Developer Without a Cause Pitfall


 {#expander-content-180550477 .expand-content}
I first saw James Dean in the movie *Rebel Without a Cause* when I was
just a young lad, but I still remember everything about the movie. When
thinking about a name for this antipattern I immediately thought of
James Dean---a troubled young man who made decisions for the wrong
reasons. Perfect.

I have observed more times that I can count architects and developers
making decisions about various aspects of microservices, particularly
with regards to service granularity and devops tools, for all the wrong
reasons. It all boils down to tradeoffs. Rich Hickey says \"Programmers
know the benefits of everything and the tradeoffs of nothing.\" My
friend Neal Ford likes to follow up on Rich\'s quote by saying
\"Architects must understand both.\" I maintain that developers should
know both as well. 



 {#expander-568788229 .expand-container}
 {#expander-control-568788229 .expand-control}
Making the Wrong Decisions


 {#expander-content-568788229 .expand-content}
[Figure 6-1](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_601) illustrates
one common scenario where services are discovered to be too
fine-grained, therefore impacting performance and overall reliability
due to the amount of interservice communication between them. In this
scenario, the developer or architect makes the decision that these
services should be consolidated into a single, more coarse-grained
service to address the performance and reliability issues.

![](https://d3ansictanv2wj.cloudfront.net/mapr_0601-b939ef333e833d8a8d7b39a937ee48fd.png){.confluence-embedded-image
.iimagesdev-cause-1png .confluence-external-resource
.confluence-content-image-border height="150"}

Figure 6-1. Moving from fine-grained to coarse-grained

While this seems like a reasonable decision, the tradeoff of doing this
is ignored. Deployment, change control, and testing are all impacted by
moving to a single coarse-grained service. The question is, what is most
important?

Consider the example illustrated
in [Figure 6-2](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_602) where
the reverse situation occurs. In this scenario services are too
coarse-grained, therefore impacting the overall testing effort and
coordination for deployment. In this case the architect or developer
makes the decision that the service should be split up into smaller
services to reduce the scope of each service, therefore making them
easier to test and deploy.

![](https://d3ansictanv2wj.cloudfront.net/mapr_0602-7a5bf86583bcf72e62a49e851a76bd1c.png){.confluence-embedded-image
.iimagesdev-cause-2png .confluence-external-resource
.confluence-content-image-border height="150"}

Figure 6-2. Moving from coarse-grained to fine-grained

While we might applaud the architect or developer for making this
decision, the tradeoffs are once again forgotten. While services are
certainly easier to test and deploy with this change, the application
suddenly experiences issues with performance and reliability due to an
increase in service choreography. Which is more important?



 {#expander-1152657823 .expand-container}
 {#expander-control-1152657823 .expand-control}
Understanding Business Drivers


 {#expander-content-1152657823 .expand-content}
Understanding Business Drivers {#MicroserviceArchitecture-UnderstandingBusinessDrivers}
------------------------------

Understanding the business drivers behind choosing microservices is the
key to avoiding this pitfall. Every architect and developer on the team
should know the answer to each of the following questions:

-   Why are you doing microservices?
-   What are the primary business drivers?
-   What architecture characteristics are most important?

Using deployability, performance, robustness, and scalability as the
primary architecture characteristics, consider the following scenarios
where the business driver is known. Notice how the business drivers are
what drive the decision regarding service consolidation or service
splitting, not the characteristics themselves.

***Scenario 1: The reason for moving to microservices is to achieve
better time to market via an effective deployment pipeline.***

In this scenario the deployability of each service outweighs
performance, reliability, and scalability, so with this business driver
you will tend to create more finer-grained services, trading off a
potential increase in service choreography (and consequently impacts on
performance and reliability). Referring back
to [Figure 6-1](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_601),
given this driver the developer would have actually made the wrong
decision to consolidate services.

***Scenario 2: The reason for moving to microservices is to increase the
overall reliability and robustness of the application.***

This scenario is a common reason for companies moving from monolithic
applications to a microservices architecture, primarily due to issues
with monolithic architectures surrounding tight coupling and hence
brittle applications. In this scenario the business driver clearly
states the need for reliability and robustness, meaning that you would
likely trade off ease of testing and deployment for better reliability
and robustness, therefore favoring more coarse-grained services rather
than finer-grained ones. 

One technique I frequently use is to write the business drivers in big
red letters on the top of the common team whiteboard as illustrated
in [Figure 6-3](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_603).
Then, anytime there is a decision on service granularity or tool
selection, the team can always look up, refer to the whiteboard, and say
\"oh, yeah, that\'s right. Okay, let\'s keep the services fine-grained
and figure out another way to address the performance and reliability
issues.\"

![](https://d3ansictanv2wj.cloudfront.net/mapr_0603-5967c15f2e14fd97af2f16716dbbc24c.png){.confluence-embedded-image
.iimagesdev-cause-3png .confluence-external-resource
.confluence-content-image-border height="250"}

Figure 6-3. Put business drivers on the whiteboard



 {#expander-569299262 .expand-container}
 {#expander-control-569299262 .expand-control}
Jump on the Bandwagon Pitfall


 {#expander-content-569299262 .expand-content}
You *must* embrace microservices. It\'s undeniably the latest trend in
the industry, everyone else is doing it, and besides, it\'s great to
have on your resume.

The *jump on the bandwagon pitfall* is all about embracing microservices
before analyzing your business needs, business drivers, and overall
organizational structure and technology environment. While the
microservices architecture is a very powerful and popular architecture
style, it\'s not suited for every application or environment.

You can easily avoid this pitfall by first understanding the advantages
and disadvantages of microservices. Then, once you\'ve gained a full
understanding of what microservices is all about, you can match your
business needs and goals to the architectural characteristics to
determine if microservices is a fit for your situation and organization.
You can also avoid this pitfall by learning more about other
architecture patterns that may be a better fit for your situation

Advantages and Disadvantages {#MicroserviceArchitecture-AdvantagesandDisadvantages}
----------------------------

The first step in avoiding this pitfall is to understand the advantages
and disadvantages of the microservices architecture style. The following
are some of the more important advantages you should know about:

DeploymentEase of deployment is one of the primary drivers for moving to
a microservices architecture. Microservices are small, single-purpose
services deployed as separate applications. It is significantly easier
and far less risk to deploy a single service than an entire monolithic
application. As a matter of fact, the whole notion of continuous
delivery is in part what prompted the creation of the microservices
architecture style.TestabilityEase of testing is another big advantage
of the microservices architecture. The small scope of a service coupled
with the lack of shared dependencies with other services makes them
relatively easy to test. However, perhaps one of the more significant
aspects of this characteristic is that with microservices you have the
ability to do more complete regression testing than with bigger
monolithic applications.Change controlWith microservices it is easier to
control what gets changed when adding new functionality. This is again
due to the limited service scope and the bounded context maintained by
each service. Having small, independent services with few
inter-dependencies means less coordination for developing, testing, and
releasing changes.ModularityMicroservices is a highly modular
architecture style, which in turn leads to highly agile applications.
Agility is best defined as the ability to respond quickly to change. The
more modular an architecture, the faster the ability to develop,
test, and release changes. The microservices architecture style is
perhaps the most modular architecture out of all the architecture
patterns due to the fine level of service granularity.ScalabilityBecause
microservices are fine-grained single-purpose services that are
separately deployed, this architecture style boasts the highest level of
scalability out of all the architecture patterns. It is relatively easy
to scale out a particular piece of functionality with the microservices
architecture style, in part due to the containerized nature of the
service topology and sophisticated monitoring tools that allow you to
start and stop services dynamically through automation.

While these advantages might convince you that microservices is the best
solution for your situation, consider the following list of
disadvantages.

Organizational change Microservices requires organizational change at
many levels. Development teams must be restructured and reorganized into
more cross-functional teams so that small teams can own the end-to-end
technical aspects of the services they are responsible for, including
the user interface, backend processing, rules processing, and database
processing and modeling. The traditional corporate development team
model of user interface teams, backend development teams, and database
engineers/administrators simply doesn\'t work with a microservices
architecture. In addition, the organizational structures involved with
releasing software must also change. With microservices it is not
feasible to use the traditional software development lifecycle
procedures that exist with monolithic, layered architectures. Rather,
you must embrace automation and leverage devops tools and practices to
develop an effective deployment pipeline for releasing microservices.
PerformanceBecause every microservice is a separately deployed
application, communication to and from services, as well as
communication between services, is remote. Performance can be
significantly impacted depending on your environment and the amount of
service choreography you have in your microservices application. It is
important to understand your remote access latency (see \"Are We There
Yet Pitfall\") and also how much service communication you will need
(see Grains of Sand Pitfall) to fully understand the performance impacts
of using microservices. ReliabilityFor the same reasons that performance
can be impacted by using microservices, the same is true with overall
reliability. Because every request is a remote access call, you run the
risk that one of the services you need to communicate with to complete a
single business request is not available or fails to respond.DevOpsWith
the microservices architecture you can have anywhere from hundreds to
even thousands of microservices. Due to the large number of services you
might have, it is simply not feasible to manually manage hundreds of
concurrent release cycles and deployments. Automation and continuous
collaboration between developers, testers, and release engineers is
vital to the success of any microservices endeavor. For this reason you
need to embrace various operations-related tools and practices, which
can be a very complicated task. There are about 12 different categories
of operations-related tools and frameworks used within a microservices
architecture, and each of those categories contains several dozen tool
and product choices. For example, there are monitoring tools, service
registry and discovery tools, deployment tools, and so on. Which ones
are best for your environment and situation? The answer to this question
requires several months of research, proof-of-concept efforts, and
tradeoff analysis to determine the best combination of tools and
frameworks for your application and environment.



 {#expander-1030698996 .expand-container}
 {#expander-control-1030698996 .expand-control}
Matching Business Needs


 {#expander-content-1030698996 .expand-content}
After understanding the advantages and disadvantages of the
microservices architecture style, you must then analyze your business
needs and goals to determine if microservices is the right approach for
the problem you are trying to solve. When determining whether
microservices is a fit, ask yourself the following questions:

-   What are my business and technical goals?
-   What am I trying to accomplish with microservices?
-   What are my current and foreseeable pain points?
-   What are the primary driving architecture characteristics for this
    application (e.g., performance, scalability, maintainability, etc.)?

Answering these questions can help you match up your business needs and
goals with the advantages and disadvantages of microservices to
determine if it is truly the right fit for your situation.



 {#expander-1236811435 .expand-container}
 {#expander-control-1236811435 .expand-control}
Other Architecture Patterns


 {#expander-content-1236811435 .expand-content}
The microservices architecture style is a very powerful one that carries
with it many advantages, but it isn\'t the only architecture style out
there. Another thing you can do to avoid this pitfall is to understand
and analyze other architecture patterns to determine if one of those
might be a better fit for your situation.

Besides microservices there are seven other common architecture patterns
you might want to consider for your application or system:

-   Service-Based Architecture
-   Service-Oriented Architecture
-   Layered Architecture
-   Microkernel Architecture
-   Space-Based Architecture
-   Event-Driven Architecture
-   Pipeline Architecture

Of course, you don\'t have to select one single architecture pattern for
your application. You can certainly combine patterns to create an
effective solution. Some examples are event-driven microservices,
event-based microkernel, layered space-based architecture, and pipeline
microkernel.

Use the following resources to learn more about other architecture
patterns:

-   [*Software Architecture Fundamentals: Understanding the
    Basics*](http://shop.oreilly.com/product/110000195.do)

-   [*Software Architecture Fundamentals: Beyond the
    Basics*](http://shop.oreilly.com/product/110000195.do)

-   [*Software Architecture Fundamentals: Service-Based
    Architecture*](http://shop.oreilly.com/product/0636920042655.do)

-   [*Software Architecture
    Patterns*](http://www.oreilly.com/programming/free/software-architecture-patterns.csp))

-   [*Microservices vs. Service-Oriented
    Architecture*](http://www.oreilly.com/programming/free/microservices-vs-service-oriented-architecture.csp)



 {#expander-2065870002 .expand-container}
 {#expander-control-2065870002 .expand-control}
The Static Contract Pitfall


 {#expander-content-2065870002 .expand-content}
All microservices have contracts between the service consumers and the
microservice. A contract usually contains a schema specifying the
expected input and output data, and sometimes the name of the operation
(depending on how you are implementing your service). Contracts are
usually owned by the service, and can be represented through formats
like XML, JSON, or even a Java or C\# object. And of course, those
contracts never change, right? Wrong.

The static contract pitfall occurs when you fail to version your service
contracts from the very start, or even not at all. Contract versioning
is absolutely critical for not only avoiding breaking changes (changing
a contract and breaking all consumers using that contract), but also to
maintain agility by supporting backward compatibility.

Here\'s an example that illustrates how you can get into trouble by not
versioning your contracts. Assume you have a microservice that is
accessed by three different clients (client 1, client 2, and client 3).
Client 1 would like to make a change to the service contract right away.
You check with client 2 and client 3 to see if they can accommodate the
change, and both clients inform you that it will take weeks to implement
that change due to other things going on with those clients. Now you
must inform client 1 that it will take weeks to make that change because
you need to coordinate the update with clients 2 and 3. However, client
1 cannot wait weeks.

By providing versioning in your contracts, and hence providing backward
compatibility, you can now be more agile in terms of client 1\'s
request. Agility is defined as how fast you can respond to change. If
you properly versioned your contracts from the very start, you could
immediately respond to client 1\'s request for the contract change by
simply creating a new version of the contract, say version 1.1. Clients
2 and 3 are both using version 1.0 of the contract, so now you can
implement the change right away without having to wait for client 2 or
client 3 to respond. In addition, you can make the change without making
what is called a \"breaking change.\"

There are two basic techniques for contract versioning: versioning at
the header level and versioning in the contract schema itself. In this
chapter I will cover each of these techniques in detail, but first
let\'s look at an example.



 {#expander-1678409982 .expand-container}
 {#expander-control-1678409982 .expand-control}
Changing a Contract


 {#expander-content-1678409982 .expand-content}
To illustrate the problem with not versioning a contract I will use an
example of buying a certain number of shares of Apple common stock
(AAPL). The schema for this request might look something like this:

    {   
        "$schema": "http://json-schema.org/draft-04/schema#",
        "properties": {
          "acct": {"type": "number"},
          "cusip": {"type": "string"},
          "shares": {"type": "number", "minimum": 100}
       },
        "required": ["acct", "cusip", "shares"]
    }

In this case to buy stock you must specify the brokerage account
(*acct*), the stock you wish to purchase in CUSIP (Committee on Uniform
Security Identification Procedures) format (*cusip*), and finally the
number of shares (*shares*), which must be greater than 100. All three
fields are required.

The code to make a request to purchase 1000 shares of Apple stock (CUSIP
037833100) for brokerage account 12345 using REST would look like this:

    POST /trade/buy
    Accept: application/json
    { "acct": "12345",
      "cusip": "037833100",
      "shares": "1000" }

Now let\'s say that the service changes its contract to accept a SEDOL
(Stock Exchange Daily Official List) rather than a CUSIP, which is
another industry standard way of identifying a particular instrument to
be traded. Now the contract looks like this:

    {   
        "$schema": "http://json-schema.org/draft-04/schema#",
        "properties": {
          "acct": {"type": "number"},
          "sedol": {"type": "string"},
          "shares": {"type": "number", "minimum": 100}
       },
        "required": ["acct", "sedol", "shares"]
    }

This would be considered a breaking change in that the prior client code
will now fail because it is still using a CUSIP. What you need to do is
use versioning so that version 1 uses a CUSIP and version 2 uses a SEDOL
to identify the stock being traded.



 {#expander-1302393103 .expand-container}
 {#expander-control-1302393103 .expand-control}
Header Versioning


 {#expander-content-1302393103 .expand-content}
The first technique for contract versioning is to put the contract
version number in the header of the remote access protocol as
illustrated
in [Figure 8-1](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_801). I
like to refer to this as *protocol-aware contract versioning* because
the information about the version of the contract you are using is
contained within the header of the remote access protocol (e.g., REST,
SOAP, AMQP, JMS, MSMQ, etc.).

![](https://d3ansictanv2wj.cloudfront.net/mapr_0801-dba99afe9ad48007a770a13d03a90971.png){.confluence-embedded-image
.iimagescontract1png .confluence-external-resource
.confluence-content-image-border height="150"}

Figure 8-1. Header contract versioning

When using REST you can use what is called a *vendor mime type* to
specify the version of the contract you wish to use in the accept header
of the request:

    POST /trade/buy
    Accept: application/vnd.svc.trade.v2+json

By using the vendor mime type (vnd) in the accept header of the URI you
can specify the version number of the contract, thereby directing the
service to perform processing based on that contract version number.
Correspondingly, the service will need to parse the accept header to
determine the version number. One example of this would be to use a
regular expression to find the version as illustrated below:

    def version
       request.headers
       ["Accept"][/^application/vnd.svc.trade.v(d)/, 1].to_i
    end

Unfortunately that is the easy part; the hard part is coding all of the
cyclomatic complexity into the service to provide conditional processing
based on the contract version (e.g., if version 1 then\... else if
version 2 then\...). For this reason, we need some sort of
version-deprecation policy to control the level of cyclomatic complexity
you introduce into each service.

Using messaging you will need to supply the version number in the
property section of the message header. For JMS 2.0 that would look
something like this:

    String msg = createJSON(
      "acct","12345",
      "sedol","2046251",
      "shares","1000")};

    jmsContext.createProducer()
    .setProperty("version", 2)
    .send(queue, msg);

Each messaging standard will have its own way of setting this header.
The important thing to remember here is that regardless of the messaging
standard, the version property is a string value that needs to match
exactly with what the service is expecting, including being
case-sensitive. For this reason it\'s generally not a good idea to
supply a default version if the version number cannot be found in the
header.



 {#expander-952369677 .expand-container}
 {#expander-control-952369677 .expand-control}
Schema Versioning


 {#expander-content-952369677 .expand-content}
Another contract-versioning technique is adding the version number to
the actual schema itself. This technique is illustrated
in [Figure 8-2](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_802).
I usually refer to this technique as *protocol-agnostic contract
versioning* because the version identification is completely independent
of the remote access protocol. Nothing needs to be specified in the
headers of the remote access protocol in order to use versioning.

![](https://d3ansictanv2wj.cloudfront.net/mapr_0802-d3d57571e3ffca3dcc869c7b0c692548.png){.confluence-embedded-image
.iimagescontract2png .confluence-external-resource
.confluence-content-image-border height="150"}

Figure 8-2. Schema-based contract versioning

By using schema-based versioning, the schema used in the previous
example would look like this:

    {   
        "$schema": "http://json-schema.org/draft-04/schema#",
        "properties": {
          "version": {"type": "integer"},
          "acct": {"type": "number"},
          "cusip": {"type": "string"},
          "sedol": {"type": "string"},
          "shares": {"type": "number", "minimum": 100}
       },
        "required": ["version", "acct", "shares"]
    }

Notice that the the schema actually contains the version number field
(*version*) as an integer value. Because you only have one schema now,
you will need to add all of the combinations of possibilities to the
schema. In the example above both the CUSIP and SEDOL are added to the
schema because that is what varies between the versions.

The big advantage of this technique is that the schema (including the
version) is independent of the remote access protocol. This means that
the same exact schema can be used by multiple protocols. For example,
the same schema can be used by REST and JMS 2.0 without any
modifications to the remote access protocol headers:

    POST /trade/buy
    Accept: application/json
    { "version": "2",
      "acct": "12345",
      "sedol": "2046251",
      "shares": "1000" }


    String msg = createJSON(
      "version","2",
      "acct","12345",
      "sedol","2046251",
      "shares","1000")};
    jmsContext.createProducer().send(queue, msg);

Unfortunately this technique has a lot of disadvantages associated with
it. First, you must parse the actual payload of the message to extract
the version number. This precludes using things like XML appliances
(e.g., DataPower) to do routing, and also might present issues when
trying to parse the schema (particularly with XML). Secondly, the
schemas can get quite complex, making it difficult to do automated
conversions of the schema (e.g., JSON to Java object). Finally, custom
validations may be required in the service to validate the schema. In
the example above, the service would have to validate that either the
CUSIP or SEDOL is filled in based on the version number.



 {#expander-1783465666 .expand-container}
 {#expander-control-1783465666 .expand-control}
Are We There Yet Pitfall


 {#expander-content-1783465666 .expand-content}
With the microservices architecture every service is deployed as a
separate application, meaning all of the communication to a microservice
from the client or API layer, as well as communication between services,
requires a remote call.

This pitfall occurs when you don\'t know how long the remote access call
takes. You might assume the latency it around 50 milliseconds, but have
you ever measured it? Do you know what the average latency is for your
particular environment? Do you know what the \"long tail\" latency is
(e.g., 95, 99, 99.5 percentiles) for your environment? Measuring both of
these metrics is important, because even with good average latency, bad
long-tail latency can destroy you.



 {#expander-1510822684 .expand-container}
 {#expander-control-1510822684 .expand-control}
Measuring Latency


 {#expander-content-1510822684 .expand-content}
Measuring the remote access latency under load in your production
environment (or production-like environment) is critical for
understanding the performance profile of your application. For example,
let\'s say a particular business request requires the coordination of
four microservices. Assuming that your remote access latency is 100
milliseconds, that particular business request would consume 500
milliseconds just in remote access latency alone (the initial request
plus four remote calls between services). That is a half a second of
request time without one single line of source code being executed for
the actual business request processing. Most applications simply cannot
absorb that sort of latency.

You might think the way to avoid this pitfall is to simply measure and
determine your average latency for your chosen remote access protocol
(e.g., REST). However, that only provides you with one piece of
information---the average latency of the particular remote access
protocol you are using. The other task is to investigate the comparative
latency using other remote access protocols such as Java Message Service
(JMS), Advanced Message Queuing Protocol (AMQP), and Microsoft Message
Queue (MSMQ).



 {#expander-371937393 .expand-container}
 {#expander-control-371937393 .expand-control}
Comparing Protocols


 {#expander-content-371937393 .expand-content}
The comparative latency will vary greatly based on both your environment
and the nature of the business request, so it is important to establish
these benchmarks on a variety of business requests with different load
profiles.

![](https://d3ansictanv2wj.cloudfront.net/mapr_0901-c8ab60023fcfbfd715852085a98198c3.png){.confluence-embedded-image
.iimageslatency1png .image .confluence-external-resource
.confluence-content-image-border height="150"}

Figure 9-1. Comparing remote access latency

In looking at the hypothetical example
in [Figure 9-1](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_901) you
notice that AMQP is in fact almost twice as fast as REST. You can now
leverage this information to make intelligent choices as to which
requests should use which remote access protocol. For example, you may
choose to use REST for all communications from client requests to your
microservices and AMQP for all interservice communication in order to
increase performance within your application.

Performance is not the only consideration when selecting your remote
access protocol. As you will see in [Give It a Rest
Pitfall](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#give_it_a_rest_pitfall),
you may want to leverage messaging to provide additional capabilities to
your application as well.



 {#expander-331152072 .expand-container}
 {#expander-control-331152072 .expand-control}
Give It a Rest Pitfall


 {#expander-content-331152072 .expand-content}
Using REST is by far the most popular choice for accessing microservices
and communicating between services. It\'s so common a choice that most
of the popular template frameworks (e.g., DropWizard, Spring Boot, etc.)
have REST access already built into the service templates. If REST is
such a popular choice, then why is it a pitfall? The give it a rest
pitfall is about using REST as the only communication protocol and
ignoring the power of messaging to enhance your microservices
architecture. For example, in a RESTful microservices architecture, how
would you handle asynchronous communications? What about the need for
broadcast capabilities? What do you do if you need to manage multiple
remote RESTful calls within a transactional unit of work?

There are two types of messaging standards you should be aware of when
considering using messaging for your microservices
architecture---platform-specific standards and platform-independent
standards. Platform-specific standards include the JMS for the Java
platform and MSMQ for the .NET platform. Both describe a standard API
used within the platform, independent of the messaging provider (vendor)
you are using. For example, in the Java platform you can swap out
brokers (e.g., ActiveMQ, HornetQ, etc.) with no API changes. While the
API is standard and remains the same, it\'s the underlying proprietary
protocol between these brokers that is different (which is why you need
to have the same client JAR and server JAR for the same vendor). With
platform-standard messaging protocols you are more concerned about
portability via a common API rather than the actual vendor product you
are using or the wire-level protocols used.

The current platform-independent standard is AMQP. AMQP, which
standardizes on the wire-level protocol, not the API. This allows
heterogeneous platforms to communicate with one another, regardless of
the vendor product you are using. A client using RabbitMQ, for example,
can easily communicate with a StormMQ server (assuming they are using
the same protocol version). AMQP using RabbitMQ is currently the most
popular choice for messaging within a microservices architecture, mostly
because of its platform-independent nature.



 {#expander-714656173 .expand-container}
 {#expander-control-714656173 .expand-control}
Asynchronous Requests


 {#expander-content-714656173 .expand-content}
The first consideration for using messaging within your microservices
architecture is asynchronous communication. With asynchronous requests
the service caller does not need to wait for a response from the service
when making a request, as illustrated
in [Figure 10-1](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_1001).
This is sometimes referred to as \"fire-and-forget\" processing.

![](https://d3ansictanv2wj.cloudfront.net/mapr_1001-b9d72dc996b8bbf29e62f8997d2681b5.png){.confluence-embedded-image
.iimagesrest-1png .confluence-external-resource
.confluence-content-image-border height="150"}

Figure 10-1. Asynchronous communications using messaging

Not only does asynchronous processing increase overall performance, but
it also adds an element of reliability to your system. Performance is
increased because callers don\'t have to wait for a response if none is
needed. Through guaranteed delivery, the message broker ensures that the
service will eventually receive the message. Reliability is increased
because the caller doesn\'t need to worry about setting timeout values
or using the circuit breaker pattern when communicating with a service
(see [The Timeout
AntiPattern](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#the_timeout_antipattern)).



 {#expander-596169323 .expand-container}
 {#expander-control-596169323 .expand-control}
Broadcast Capabilities


 {#expander-content-596169323 .expand-content}
Another very powerful feature of messaging that is not available within
REST is the capability to broadcast a message to multiple services. This
is known in messaging as \"publish-and-subscribe\" messaging, and
usually involves topics and subscribers (depending on the messaging
standard you are
using). [Figure 10-2](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_1002) illustrates
the basic behavior of broadcast messaging.

![](https://d3ansictanv2wj.cloudfront.net/mapr_1002-2199c81cd88d8b44336193d5f8662b83.png){.confluence-embedded-image
.iimagesrest-2png .confluence-external-resource
.confluence-content-image-border height="250"}

Figure 10-2. Broadcast capabilities using messaging

Broadcast messaging involves a message producer sending out the same
message to multiple message receivers (i.e., services). The message
producer generally doesn\'t know who is accepting the message or what
they are going to do with it. For example, a message producer may
broadcast a message informing consumers about a stock split for Apple
stock (AAPL). The message producer only has the responsibility of
publishing a message to a topic (JMS), a fanout or topic exchange
(AMQP), or a multicast queue (MSMQ). The stock split message may be
picked up by any number of consumers, or no consumers at all.



 {#expander-703804955 .expand-container}
 {#expander-control-703804955 .expand-control}
Transacted Requests


 {#expander-content-703804955 .expand-content}
Messaging systems support the notion of transacted messages, meaning
that if messages are sent to multiple queues or topics within the
context of a transaction, the messages are not actually received by the
services until the sender does a commit on that transaction. The service
consumer sends a message to the first service and then sends another
message to the second service, as illustrated
in [Figure 10-3](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_1003).
Until the service consumer performs a commit, those messages are held in
the queues. Once the service consumer performs a commit, both messages
are then released.

![](https://d3ansictanv2wj.cloudfront.net/mapr_1003-b683f3dc56d5ceca76c43d6874cdc577.png){.confluence-embedded-image
.iimagesrest-3png .confluence-external-resource
.confluence-content-image-border height="250"}

Figure 10-3. Transaction capabilities of messaging

If the service consumer
in [Figure 10-3](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls#fig_1003) sends
a message to the first queue, but then experiences some sort of error,
the service consumer can perform a rollback on the messaging
transaction, which would effectively remove the message from the first
queue.

Implementing this sort of transaction capability using REST would be
very difficult, essentially requiring the service consumer to issue
compensating requests to reverse the updates made by each request.
Therefore, it is a good idea to consider using transacted messaging any
time a service consumer needs to orchestrate multiple remote requests.



 {#expander-142263341 .expand-container}
 {#expander-control-142263341 .expand-control}
Loss of Control


 {#expander-content-142263341 .expand-content}
When you micromanage your staff, you limit yourself by which management
tools you have at your disposal until the only tool you have in reach is
control. And, the funny thing about control is that when it's your only
means of management, you usually end up losing it. Rather than gaining
control over your team and product, you lose control and time in trying
to micromanage your team. It's important to realize that there are many
valid management styles and every staff member reacts differently to
each. 

**Takeaway:** When you drastically limit your style you also limit your
ability to communicate and, in the end, your ability to manage.



 {#expander-1822942134 .expand-container}
 {#expander-control-1822942134 .expand-control}
Lost of Trust


 {#expander-content-1822942134 .expand-content}
Micromanagement will eventually lead to a massive breakdown of trust
between you and your staff. Your staff will no longer see you as a
manager, but a despot whose only desire is to wall up its staff. This
crushing act breaks what little trust already exists between employee
and manager. When trust is gone, two things can happen: a serious loss
of productivity and loss of employees. Yes, the latter is a worst-case
scenario, but it happens. 

**Takeaway:** Remember, trust is a two-way street. Your staff must be
able to trust you as much as you trust them. Micromanagement destroys
trust.



 {#expander-1885985912 .expand-container}
 {#expander-control-1885985912 .expand-control}
Dependent Employees


 {#expander-content-1885985912 .expand-content}
After being micromanaged, your staff will begin to depend on you, rather
than having the confidence to perform tasks on their own.
Micromanagement makes your team feel like they must have your constant
guidance. Dependent employees take more time and effort to manage, which
can take a toll on your schedule and energy. You have to remember that
those employees were initially hired because they brought something to
the table: skills, talents, and insights all unique to each and every
staff member. When your employees aren't dependent upon you, they'll
continue to think on their own---and when employees have the freedom to
think on their own, great things can happen. 

**Takeaway:** If you micromanage too much, your employees' skills,
talents, and insights can fall to the wayside, leaving you with a team
that only knows how to do what it\'s told. You must allow your employees
the freedom to think and act on their own.



 {#expander-1967834889 .expand-container}
 {#expander-control-1967834889 .expand-control}
Your Own Burnout


 {#expander-content-1967834889 .expand-content}
Micromanaging is downright exhausting. Looking over so many shoulders
every day will very quickly burn you out. Eventually, you'll grow to
hate your job, straight down to the very company that employs you. If
you hate it enough, you may even end up leaving it, and possibly never
wanting to revisit a management role again. 

Sure, burnout is always a danger in any job, but the energy burned while
micromanaging will ignite that wick faster than anything. This feeling
of burnout can affect not only your work life but can stretch into your
home life and cause anxiety and depression. And don't forget, that
burnout can infect those beneath you. Managers are not the only victims
of burnout; as you flame out, you will very likely take your staff with
you. 

**Takeaway:** Micromanagement is not only bad for your employees, but it
can take a terrible toll on your physical and mental health. Take time
to step back, breathe, and realize that your team can handle its tasks
without you constantly hovering over shoulders.



 {#expander-1746256032 .expand-container}
 {#expander-control-1746256032 .expand-control}
High Turnover of Staff


 {#expander-content-1746256032 .expand-content}
Simply put, most people don't take well to being micromanaged. When
employees are micromanaged, they often do one thing---quit. Considering
the reasons why managers micromanage (ego, insecurity, inexperience,
perfectionism, arrogance), it's simply not worth the high turnover rate.
Having to constantly train and retrain staff not only robs your
department of momentum, it makes your company lose the skilled and
effective employees it once had for second runner ups and
under-qualified people, which then affects the company's bottom line and
destroys morale. Friendships are made and destroyed, and eventually,
this will crush the spirit of your staff. 

**Takeaway:** Micromanagement leads to employees quitting.



 {#expander-1564201389 .expand-container}
 {#expander-control-1564201389 .expand-control}
Lack of Autonomy


 {#expander-content-1564201389 .expand-content}
When you micromanage, your employees begin to feel like they're losing
their autonomy. When this happens, they'll slowly lose the desire to do
anything but that which you demand, and little more. No one will step
outside the proverbial box or go the extra mile for a task. You hand
those same people a certain level of autonomy and they will take pride
in what they do and how they do it. 

**Takeaway:** A lack of autonomy will squelch growth in your employees.
One of the goals of management should be to see staff members rise in
the ranks.



 {#expander-2098314501 .expand-container}
 {#expander-control-2098314501 .expand-control}
No Innovation


 {#expander-content-2098314501 .expand-content}
One of the biggest dangers of micromanaging is crushing your employees'
creative spirit. Your team is on the front lines of your project and
they know what is happening better than anyone else, including you.
While some innovations that they bring to the table might not always be
winners, crushing innovation and creativity destroys all chances of the
good ideas coming out and being shared. By refusing to take risks in
innovation, you're also refusing the potential for progress. 

**Takeaway:** Innovation is the key to progress. Micromanaging your team
ruins any chance of growth or progression. 

If you find yourself micromanaging, you can fix it. You have to have
trust and faith in the people that you work with, and believe that they
can get the job done even without your constant oversight. With more
freedom, they will surprise you with an increase in creativity,
innovation, and productivity. 





 {.panel style="border-width: 1px;"}
 {.panelHeader style="border-bottom-width: 1px;"}
**Philosophy**


 {.panelContent}
 {#expander-928547650 .expand-container}
 {#expander-control-928547650 .expand-control}
I need a change


 {#expander-content-928547650 .expand-content}
Migrating to another architecture is like shifting to a new house.
Firstly, we need to plan what we need to move -- this list may include
furniture, gadgets, and a bunch of other things. We might as well split
the tasks into moving everything in two or more attempts. Once we have
moved everything, the next step is to place all this stuff at suitable
places.

Similarly, while moving from the monolithic architecture to the
microservices architecture, we have to analyze and devise a plan for
each service. Deciding the granularity of applications is another
tedious task when it comes to migration from one architecture to
another. On the other hand, some software systems are too small to be
broken down any further. These are probably subsystems that are already
broken down as much as they should be and breaking them down further
will do no good. If there is a broad spectrum of applications and
services that we are handling, it would make the task even more
difficult.

And that's not all... once we have moved the applications, we will have
to move the data associated with all these applications. So, there is no
real need for microservices unless the complexity factor is very high.



 {#expander-1359854354 .expand-container}
 {#expander-control-1359854354 .expand-control}
Sharing is Caring


 {#expander-content-1359854354 .expand-content}
First things first -- microservices is a "no sharing" architecture and
involves a lot of authentication and authorizations for services to be
able to communicate. We will have to find out from the DevOps team if
there are any systems or services that are interdependent or function
efficiently only when put together. For example, two or more services
may be using the same code or the same database. Clubbing up such
services might be a wiser approach rather than splitting them up because
sometimes doing so may increase the overall complexity rather than
decreasing.

Also, splitting up dependent legacy systems into microservices might
require long-term strategic planning, which might add to the time, cost,
and efforts. From my experience, a rule that applies to all the
microservices is, the more the number of dependencies, the harder it is
to isolate these services. Furthermore, if there are versioning issues
with some of these services, things can get worse.



 {#expander-156064317 .expand-container}
 {#expander-control-156064317 .expand-control}
Keep trying till you succeed


 {#expander-content-156064317 .expand-content}
The service request generated at a customer's end is handled by a
service component depending on the availability of the requested service
and how the service component responds after receiving this request. In
this case, the user needs to send the request (which needs to reach the
service component) and the service component needs to send back the
correct response (which must reach the user). If delays are introduced
in the request or response times, they are because the user and the
service component keep retrying.

However, neither the user nor the service component will keep trying
forever. There is a timeout value set, after which, both have to stop
retrying. So where's the trick? It's with setting up an appropriate
timeout value. When I say appropriate, the timeout values can be low for
services that are less critical and they must be kept high for highly
critical services such as financial transactions.

But is it an ideal thing to do? Well, I don't think so! Using circuit
breaker software, in my opinion, is a much better approach. The circuit
breaker will act as a mediator to keep a check on whether the service is
available or not in a timely manner. It will disallow requests to a
service when it is unavailable and start allowing requests to the
service when it becomes available again.

In microservices, all of the services are deployed separately and are
accessed remotely. Managing service availability & responsiveness with
software tools such as the circuit breaker becomes a major challenge for
the microservice architecture due to its distributed structure.



 {#expander-2136904512 .expand-container}
 {#expander-control-2136904512 .expand-control}
Jumping on the Microservices bandwagon


 {#expander-content-2136904512 .expand-content}
Choosing the right architecture is obviously the best thing to do but
jumping on the Microservices bandwagon right away may not be a great
idea. We should not ignore aspects like good coding, the level of
automation, design requirements, maintainability, and testability, among
others. Things can go haywire if these critical aspects are not taken
care of before achieving the migration goals. And taking care of such
aspects might even eliminate the need for microservices.

It is also very important to gauge whether your teams are equipped and
capable enough to handle processes involved while migrating toward
microservices and then the maintenance of the overall architecture.
Consulting and gaining insights from your DevOps team will also give you
a better understanding of whether you should adopt microservices or not.

Microservices are a boon for software architects and developers but
these are a few things that you must consider before resorting to
microservices. Every architecture has its pros & cons and microservices
are no different. I hope this article was insightful enough to take care
of your concerns regarding migration toward the microservices
architecture.





\

\

\

\

\

\

 {#expander-645063621 .expand-container}
 {#expander-control-645063621 .expand-control}
References


 {#expander-content-645063621 .expand-content}
-   [OReilly - microservices antipatterns and
    pitfalls](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls)
-   [Opcito - microservices anti patterns what you need to understand
    before adopting
    microservices](https://www.opcito.com/blogs/microservices-anti-patterns-what-you-need-to-understand-before-adopting-microservices/)
-   [Devops - five microservices worst
    practices](https://devops.com/five-microservices-worst-practices/)
-   [Pluralsight - why micromanagement is
    bad](https://www.pluralsight.com/blog/business-professional/why-micromanagement-is-bad)







\

\

\

 {#expander-987516612 .expand-container}
 {#expander-control-987516612 .expand-control}
References


 {#expander-content-987516612 .expand-content}
-   <https://microservices.io/patterns/>
-   <https://patterns.arcitura.com/soa-patterns/basics/whatissoa/overview>
-   <https://github.com/katopz/best-practices/blob/master/best-practices-for-building-a-microservice-architecture.md>
-   [Altkom Software - Building microservices on net core Part
    1](https://altkomsoftware.pl/en/blog/building-microservices-on-net-core-1/)
-   [Altkom Software - Building microservices on net core Part
    2](https://altkomsoftware.pl/en/blog/microservices-net-core-cqrs-mediatr/)
-   [Altkom Software - Building microservices on net core Part
    3](https://altkomsoftware.pl/en/blog/service-discovery-eureka/)
-   [Altkom Software - Building microservices on net core Part
    4](https://altkomsoftware.pl/en/blog/building-api-gateways-with-ocelot/)
-   [Altkom Software - Building microservices on net core Part
    5](https://altkomsoftware.pl/en/blog/building-microservices-domain-aggregates/)
-   [Altkom Software - Building microservices on net core Part
    6](https://altkomsoftware.pl/en/blog/building-microservices-6/)
-   [Medium - Alexander Ma - Introduction to Microservices Part
    1](https://medium.com/@alexma6614/introduction-to-microservices-pt-1-7656f2615e40)
-   [Medium - Alexander Ma - Introduction to Microservices Part
    2](https://medium.com/@alexma6614/rabbitmq-flask-go-tutorial-pt-2-7161feb654c6)
-   [Devops - when should you go for microservice
    architecture](https://devops.com/when-should-you-go-for-microservice-architecture/)
-   [Towards Data Science - microservice architecture a brief overview
    and why you should use it in your next
    project](https://towardsdatascience.com/microservice-architecture-a-brief-overview-and-why-you-should-use-it-in-your-next-project-a17b6e19adfd)
-   [Cloud Native - the difference between api gateways and service
    mesh](https://www.cncf.io/blog/2020/03/06/the-difference-between-api-gateways-and-service-mesh/)
-   [MS Doc - microservices design
    patterns](https://docs.microsoft.com/en-us/azure/architecture/microservices/design/patterns)



\

\

\

\

\

\


 {.pageSection .group}
 {.pageSectionHeader}
Attachments: {#attachments .pageSectionTitle}
------------


 {.greybox align="left"}
![](images/icons/bullet_blue.gif){width="8" height="8"}
[microservices-patterns.png](attachments/Microservice-Architecture_0.png)
(image/png)\





 

Document generated by Confluence on May 21, 2020 14:12

 {#footer-logo}
[Atlassian](http://www.atlassian.com/)



