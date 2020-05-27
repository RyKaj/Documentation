###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Infrastructure Architecture](https://github.com/RyKaj/Documentation/tree/master/InfrastructureArchitecture/README.md) |
------------


Infrastructure Architecture - Microservices Best Practices
========================================================


 
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
Microservice Architecture best practices e.g.  [**Characteristics of a
Microservice
Architecture**](https://martinfowler.com/articles/microservices.html#SynchronousCallsConsideredHarmful)
\>by [***Martin Fowler***](https://martinfowler.com/)
or  [**Microservices
Patterns**](https://microservices.io/patterns/microservices.html)
 by  [***Chris
Richardson***](https://www.chrisrichardson.net/)  or
Adopting  [**Microservices at Netflix: Lessons for Architectural
Design**](https://microservices.io/patterns/microservices.html)
 by  [**Tony
Mauro**](https://www.nginx.com/people/tony-mauro/).
There are also some great talks e.g.  [**Microservices Patterns and
Antipatterns**](https://www.youtube.com/watch?v=RsyOkifmamI)
 by  [***Stefan
Tilkov***](https://www.innoq.com/en/staff/stefan-tilkov/)
,  [**10 Tips for failing badly at
Microservices**](https://www.youtube.com/watch?v=X0tjziAQfNQ)
 by  **David Schmitz**,  [**Principles of
Microservices**](https://www.youtube.com/watch?v=PFQnNFe27kU)
 by  [***Sam Newman***](https://samnewman.io/).

1. Domain Driven Design
-----------------------

The foremost challenge to develop Microservices is to split a large,
complex application into small, autonomous, independently deployable
Modules. If Microservices are not split in the right way, there will be
tightly coupled Microservices which will have all the disadvantages of a
Monolith and all the complexities of Microservices aka  **Distributed
Monolith**. Fortunately, there is already a Solution which can greatly
help in this regard.  [***Eric
Evans***](https://twitter.com/ericevans0?lang=en), a
Software Engineering Consultant back then, had encountered recurring
issues regarding software complexity in Business Applications across
different companies and has summarized his valuable insight in the book
" [**Domain Driven Design: Tackling Complexity in the Heart of
Software**](http://dddcommunity.org/book/evans_2003/) "
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
post but you should read either the original DDD book  [**Domain Driven
Design: Tackling Complexity in the Heart of
Software**](http://dddcommunity.org/book/evans_2003/)
(Blue Book) of  [***Eric
Evans***](https://twitter.com/ericevans0?lang=en)  or a
bit modern DDD book  [**Implementing Domain Driven
Design**](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/ref=sr_1_3?keywords=Domain+driven+design&qid=1574198067&s=books&sr=1-3)
(Red Book) of  [***Vaughn
Vernon***](https://vaughnvernon.co/). If a large system
is divided into Core Domain and Sub-domains and the Core Domain and
Sub-domains are then mapped to one or more Microservices, then we will
get the ideal loosely coupled Microservices.

2. Database per Microservice
----------------------------

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

3. Micro Frontends
------------------

Unfortunately, most of the Backend developers have a backdated view
about Frontend Development and think that Frontend Development is
simple. As most Software Architects are Backend Developers, they have
little regard for Frontend and Frontend is usually neglected in the
Architecture Design. Very often in Microservice projects, backends are
very finely modularized with their database but there is one Monolith
Frontend. In the best case, they consider one of the hottest SPA (React,
Angular, Vue) to develop the Monolith Frontend. The main problem of this
approach is that Frontend Monolith is as bad as Backend Monolith as I
have described 
[**previously**](https://towardsdatascience.com/microservice-architecture-a-brief-overview-and-why-you-should-use-it-in-your-next-project-a17b6e19adfd)
. Also, when the Frontend needs to be modernized due to changes in
Browser, then it requires a Big Bang modernization ( *That is the reason
why so many companies are still using the outdated Angular 1
framework*). The web is simple yet very powerful and inherently offers
transclusion. There are many ways to develop SPA based Microfrontends:
with iFrame, Web Components or via (Angular/React) Elements.

4. Continuous Delivery
----------------------

One of the key USP of Microservice Architecture is that each
Microservice can be deployed independently. If you have a system of e.g.
100 Microservices and only one Microservice needs to be changed, then
you can update only one Microservice without touching the other 99. But
deploying 100 Microservices independently without Automation (DevOps,
CI/CD) is a daunting task. To take full advantage of this Microservice
feature, one needs CI/CD and DevOps. Using Microservice Architecture
without CI/CD, DevOps, Automation is like buying the latest Porsche and
then drive it with hand-brake. It is no wonder that 
[**CI/CD**](https://martinfowler.com/bliki/MicroservicePrerequisites.html)
 is listed as one of the three prerequisites to use Microservice
Architecture by Microservice Expert  ***Martin Fowler*** .

5. Observability
----------------

One of the main drawbacks of Microservice Architecture is that Software
Development became simple at the expense of Operations. With one
Monolith, it is much simpler to monitor the application. But having many
microservices run on containers, observability of the whole system
became very crucial and complicated. Even Logging became complicated to
aggregate logs from many containers/machines into a central place.
Fortunately, there are already many Enterprise grade solutions in the
market. For example,  **ELK/Splunk** offers Logging for Microservices. 
**Prometheus/App Dynamics** offers industry-grade monitoring. Another
very crucial observability tool in the Microservice world is Tracing.
Often one API request to a microservice leads to several cascaded calls
to other microservices. To analyze the latency of a Microservice system,
it is necessary to measure the latency of each individual Microservice. 
**Zipkin/Jaeger** offers excellent tracing support for Microservices.

6. Unified Tech Stack
---------------------

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

7. Asynchronous Communications
------------------------------

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

9. Infrastructure over Libraries
--------------------------------

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
to use frameworks (e.g. Service Meshes, API gateway).

10. Organizational Considerations
---------------------------------

Almost 50 years ago (1967),  [Melvin
Conway](https://en.wikipedia.org/wiki/Melvin_Conway) gave
an observation that the Software Architecture of a company is limited by
Organizational Structure (Conway's Law). Although the observation is 50
years old, MIT and Harvard Business School have recently found that the
law is still valid in modern days. If an organization plans to develop
Microservice Architecture, then it should make the team size accordingly
(two "American" Pizza team: 7±2 person). Also, the team should be
cross-functional and ideally will have Frontend/Backend Developer, Ops
Engineering and Tester. Microservice Architecture will only work if the
higher Management also changes their viewpoint and vision accordingly.

References

-   [Towards Data Science - microservice architecture a brief overview
    and why you should use it in your next
    project](https://towardsdatascience.com/microservice-architecture-a-brief-overview-and-why-you-should-use-it-in-your-next-project-a17b6e19adfd)


 



