###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Infrastructure Architecture](https://github.com/RyKaj/Documentation/tree/master/Agile/README.md) |
------------





Infrastructure Architecture - Monolithic Architecture
===================================================

Context
-------

You are developing a server-side enterprise application. It must support a variety of different clients including desktop browsers, mobile browsers and native mobile applications. The application might also  expose an API for 3rd parties to consume. It might also integrate with other applications via either web services or a message broker. The application handles requests (HTTP requests and messages) by executing business logic; accessing a database; exchanging messages with other systems; and returning a HTML/JSON/XML response. There are logical components corresponding to different functional areas of the application.

Limitation of Monolithic Architrecture
--------------------------------------

-   **Application Scaling:**As the successful Web Scale companies enjoy exponential growth, their softwares also need to support high horizontal scalability. Sometimes, only a part of the software which is e.g. CPU intensive or I/O intensive needs to be scaled and handled separately (implemented with polyglot programming). Monolithic software works as a single unit and developed in a single programming language using a single Tech Stack. To achieve horizontal scaling, the whole application needs to be scaled. Correspondingly as the Monolithic software only supports one programming language, it is not possible to implement one single module of it in other programming language or in other Tech Stack.
-   **Development Velocity:**To shorten time to market, every company nowadays wants to have fast feature development. In a large, complex and often multi-million line Monolithic Application, adding new feature is very slow because such a Monolithic Application gives huge Cognitive Load to the Developer. Modules of giant Monolithic applications are tightly coupled and provide an additional challenge to add new features. As a result, adding new features in a Monolithic application is often slow and very expensive.
-   **Development Scaling:**Companies often want to parallelize the development by hiring more developers to have a competitive advantage or to catch the low hanging fruits. Developers cannot work autonomously on a giant, Monolithic, tightly coupled code base and often needs extra synchronization, guard not to bump into each other's work. Adding more developers does not produce more feature and sometimes delivers even fewer features. Similarly due to the high Cognitive Load to understand the whole Monolithic code base, new hires or fresh graduates often take a long time to write first lines of productive code. In 2008, I had an interview in a Telecom company in Berlin where the Technical Manager told me with a proud smile that they have multi-million lines of C++ code base and new developers can only write productive codes after 3--6 months.
-   **Release Cycle:**Release Cycle of large Monolithic applications is often too large and usually 6 months to 2/3 years plus another few months to several years delay due to its size. In modern days, large release cycle often put the company under competitive disadvantages as within this large release gap, a new company can come and take away its market.
-   **Modularization**: In Monolithic Architecture, the boundary between Modules are often internal Interfaces. As soon as the application grows in size, the boundary between modules starts to fall apart. As a result, often the Modules in Monolithic Architecture are tightly coupled instead of the double dictum "Loosely coupled, highly cohesive". *If we compare the Software development with society, then Monolithic Modularization is like moralistic, religious rules which as we know cannot ensure law and order in the society*.
-   **Modernization:**Existing successful applications needed to be modernized due to many factors (e.g. taking advantage of modern Hardware, Browser, Network Bandwidth, Tech Stack or Attract good developers). Modernization of Monolithic application is often expensive and time-consuming as it needs a Big Bang modernization of the whole application without disrupting the Service.

### Problem

What's the application's deployment architecture?

Forces
------

-   There is a team of developers working on the application
-   New team members must quickly become productive
-   The application must be easy to understand and modify
-   You want to practice continuous deployment of the application
-   You must run multiple instances of the application on multiple machines in order to satisfy scalability and availability requirements
-   You want to take advantage of emerging technologies (frameworks, programming languages, etc)

Solution
--------

Build an application with a monolithic architecture. For example:

-   a single Java WAR file.
-   a single directory hierarchy of Rails or NodeJS code

### Example

Let's imagine that you are building an e-commerce application that takes orders from customers, verifies inventory and available credit, and ships them. The application consists of several components including the StoreFrontUI, which implements the user interface, along with some backend services for checking credit, maintaining inventory and shipping orders.

The application is deployed as a single monolithic application. For example, a Java web application consists of a single WAR file that runs on a web container such as Tomcat. A Rails application consists of a single directory hierarchy deployed using either, for example, Phusion Passenger on Apache/Nginx or JRuby on Tomcat. You can run multiple instances of the application behind a load balancer in order to scale and improve availability.

![](https://microservices.io/i/DecomposingApplications.011.jpg)

Resulting Context
-----------------

This solution has a number of benefits:

-   Simple to develop - the goal of current development tools and IDEs is to support the development of monolithic applications
-   Simple to deploy - you simply need to deploy the WAR file (or directory hierarchy) on the appropriate runtime
-   Simple to scale - you can scale the application by running multiple copies of the application behind a load balancer

However, once the application becomes large and the team grows in size, this approach has a number of drawbacks that become increasingly significant:

-   The large monolithic code base intimidates developers, especially ones who are new to the team. The application can be difficult to understand and modify. As a result, development typically slows down. Also, because there are not hard module boundaries, modularity breaks down over time. Moreover, because it can be difficult to understand how to correctly implement a change the quality of the code declines over time. It's a downwards spiral.

-   Overloaded IDE - the larger the code base the slower the IDE and the less productive developers are.

-   Overloaded web container - the larger the application the longer it takes to start up. This had have a huge impact on developer productivity because of time wasted waiting for the container to start. It also impacts deployment too.

-   Continuous deployment is difficult - a large monolithic application is also an obstacle to frequent deployments. In order to update one component you have to redeploy the entire application. This will interrupt background tasks (e.g. Quartz jobs in a Java application), regardless of whether they are impacted by the change, and possibly cause problems. There is also the chance that components that haven't been updated will fail to start correctly. As a result, the risk associated with redeployment increases, which discourages frequent updates. This is especially a problem for user interface developers, since they usually need to iterative rapidly and redeploy frequently.

-   Scaling the application can be difficult - a monolithic architecture is that it can only scale in one dimension. On the one hand, it can scale with an increasing transaction volume by running more copies of the application. Some clouds can even adjust the number of instances dynamically based on load. But on the other hand, this architecture can't scale with an increasing data volume. Each copy of application instance will access all of the data, which makes caching less effective and increases memory consumption and I/O traffic. Also, different application components have different resource requirements - one might be CPU intensive while another might memory intensive. With a monolithic architecture we cannot scale each component independently

-   Obstacle to scaling development - A monolithic application is also an obstacle to scaling development. Once the application gets to a certain size its useful to divide up the engineering organization into teams that focus on specific functional areas. For example, we might want to have the UI team, accounting team, inventory team, etc. The trouble with a monolithic application is that it prevents the teams from working independently. The teams must coordinate their development efforts and redeployments. It is much more difficult for a team to make a change and update production.

-   Requires a long-term commitment to a technology stack - a monolithic architecture forces you to be married to the technology stack (and in some cases, to a particular version of that technology) you chose at the start of development . With a monolithic application, can be difficult to incrementally adopt a newer technology. 
    For example, let's imagine that you chose the JVM. You have some language choices since as well as Java you can use other JVM languages that inter-operate nicely with Java such as Groovy and Scala. But components written in non-JVM languages do not have a place within your monolithic architecture. Also, if your application uses a platform framework that subsequently becomes obsolete then it can be challenging to incrementally migrate the application to a newer and better framework. It's possible that in order to adopt a newer platform framework you have to rewrite the entire application, which is a risky undertaking.

References

-   <https://patterns.arcitura.com/microservice-patterns>
-   <https://microservices.io/patterns/>
-   [Towards Data Science - microservice architecture a brief overview and why you should use it in your next project](https://towardsdatascience.com/microservice-architecture-a-brief-overview-and-why-you-should-use-it-in-your-next-project-a17b6e19adfd)
