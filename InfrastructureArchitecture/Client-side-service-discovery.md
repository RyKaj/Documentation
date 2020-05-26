









Infrastructure Architecture - Client-side service discovery
=========================================================


 
Context
-------

Services typically need to call one another. In a monolithic
application, services invoke one another through language-level method
or procedure calls. In a traditional distributed system deployment,
services run at fixed, well known locations (hosts and ports) and so can
easily call one another using HTTP/REST or some RPC mechanism. However,
a modern 
[microservice-based](https://microservices.io/patterns/microservices.html) application
typically runs in a virtualized or containerized environments where the
number of instances of a service and their locations changes
dynamically.

![](https://microservices.io/i/servicediscovery/discovery-problem.jpg){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}

Consequently, you must implement a mechanism for that enables the
clients of service to make requests to a dynamically changing set of
ephemeral service instances.

Problem
-------

How does the client of a service - the API gateway or another service -
discover the location of a service instance?

Forces
------

-   Each instance of a service exposes a remote API such as HTTP/REST,
    or Thrift etc. at a particular location (host and port)
-   The number of services instances and their locations changes
    dynamically.
-   Virtual machines and containers are usually assigned dynamic IP
    addresses.
-   The number of services instances might vary dynamically. For
    example, an EC2 Autoscaling Group adjusts the number of instances
    based on load.

Solution
--------

When making a request to a service, the client obtains the location of a
service instance by querying a  [Service
Registry](https://microservices.io/patterns/service-registry.html),
which knows the locations of all service instances.

The following diagram shows the structure of this pattern.

![](https://microservices.io/i/servicediscovery/client-side-discovery.jpg){.confluence-embedded-image
.img-responsive .confluence-external-resource
.confluence-content-image-border height="250"}

This is typically handled by a  [Microservice chassis
framework](https://microservices.io/patterns/microservice-chassis.html)

Examples
--------

The  [Microservices Example
application](https://github.com/cer/microservices-examples) is
an example of an application that uses client-side service discovery. It
is written in Scala and uses Spring Boot and Spring Cloud as the 
[Microservice
chassis](https://microservices.io/patterns/microservice-chassis.html).
They provide various capabilities including client-side discovery.

Resulting Context
-----------------

Client-side discovery has the following benefits:

-   Fewer moving parts and network hops compared to  [Server-side
    Discovery](https://microservices.io/patterns/server-side-discovery.html)

Client-side discovery also has the following drawbacks:

-   This pattern couples the client to the  [Service
    Registry](https://microservices.io/patterns/service-registry.html)
-   You need to implement client-side service discovery logic for each
    programming language/framework used by your application, e.g
    Java/Scala, JavaScript/NodeJS. For example,  [Netflix
    Prana](https://github.com/Netflix/Prana) provides an
    HTTP proxy-based approach to service discovery for non-JVM clients.



 



