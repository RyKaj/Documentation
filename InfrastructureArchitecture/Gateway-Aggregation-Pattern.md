Infrastructure Architecture - Gateway Aggregation Pattern
=======================================================

Overview
--------

Use a gateway to aggregate multiple individual requests into a single
request. This pattern is useful when a client must make multiple calls
to different backend systems to perform an operation.

Context and Problem
-------------------

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

![](attachments/463533350/463533348.png){.confluence-embedded-image .confluence-thumbnail .confluence-content-image-border height="150"}

Solution
--------

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
.confluence-thumbnail .confluence-content-image-border height="150"}
![New-API-GW-Diagram](https://d1.awsstatic.com/serverless/New-API-GW-Diagram.c9fc9835d2a9aa00ef90d0ddc4c6402a2536de0d.png){.confluence-embedded-image .confluence-external-resource .confluence-content-image-border height="150"}
![](https://microservices.io/i/apigateway.jpg){.confluence-embedded-image .img-responsive .confluence-external-resource .confluence-content-image-border height="150"}
![](attachments/463533350/463533529.png){.confluence-embedded-image .confluence-thumbnail .confluence-content-image-border height="150"} ![](attachments/463533350/463533530.png){.confluence-embedded-image .confluence-content-image-border height="150"}
![](https://microservices.io/i/bffe.png){.confluence-embedded-image .img-responsive .confluence-external-resource .confluence-content-image-border height="150"} 

### Using an API gateway has the following benefits {#GatewayAggregationPattern-UsinganAPIgatewayhasthefollowingbenefits}

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

Issues and Considerations
-------------------------

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
-   Implement a resilient design, using techniques such as 
    [bulkheads](https://docs.microsoft.com/en-us/azure/architecture/patterns/bulkhead), 
    [circuit
    breaking](https://docs.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker), 
    [retry](https://docs.microsoft.com/en-us/azure/architecture/patterns/retry),
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

When to use this Pattern
------------------------

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
