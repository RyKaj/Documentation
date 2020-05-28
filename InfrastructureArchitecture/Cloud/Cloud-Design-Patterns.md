###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Infrastructure Architecture](https://github.com/RyKaj/Documentation/tree/master/InfrastructureArchitecture/README.md) |
------------



Infrastructure Architecture - Cloud Design Patterns
=================================================


 
Overview
--------

These design patterns are useful for building reliable, scalable, secure
applications in the cloud.

Each pattern describes the problem that the pattern addresses,
considerations for applying the pattern.  However, most of the patterns
are relevant to any distributed system, whether hosted on Azure or on
other cloud platforms.

Cloud Development Categories
----------------------------

### Availability

Availability is the proportion of time that the system is functional and
working, usually measured as a percentage of uptime. It can be affected
by system errors, infrastructure problems, malicious attacks, and system
load. Cloud applications typically provide users with a service level
agreement (SLA), so applications must be designed to maximize
availability.

### Data Management  

Data management is the key element of cloud applications, and influences
most of the quality attributes. Data is typically hosted in different
locations and across multiple servers for reasons such as performance,
scalability or availability, and this can present a range of challenges.
For example, data consistency must be maintained, and data will
typically need to be synchronized across different locations.

### Design and Implementation  

Good design encompasses factors such as consistency and coherence in
component design and deployment, maintainability to simplify
administration and development, and reusability to allow components and
subsystems to be used in other applications and in other scenarios.
Decisions made during the design and implementation phase have a huge
impact on the quality and the total cost of ownership of cloud hosted
applications and services.

### Messaging

The distributed nature of cloud applications requires a messaging
infrastructure that connects the components and services, ideally in a
loosely coupled manner in order to maximize scalability. Asynchronous
messaging is widely used, and provides many benefits, but also brings
challenges such as the ordering of messages, poison message management,
idempotency, and more.

### Management and Monitoring 

Cloud applications run in a remote datacenter where you do not have full
control of the infrastructure or, in some cases, the operating system.
This can make management and monitoring more difficult than an
on-premises deployment. Applications must expose runtime information
that administrators and operators can use to manage and monitor the
system, as well as supporting changing business requirements and
customization without requiring the application to be stopped or
redeployed.

### Performance and Scalability  

Performance is an indication of the responsiveness of a system to
execute any action within a given time interval, while scalability is
ability of a system either to handle increases in load without impact on
performance or for the available resources to be readily increased.
Cloud applications typically encounter variable workloads and peaks in
activity. Predicting these, especially in a multitenant scenario, is
almost impossible. Instead, applications should be able to scale out
within limits to meet peaks in demand, and scale in when demand
decreases. Scalability concerns not just compute instances, but other
elements such as data storage, messaging infrastructure, and more.

### Resiliency 

Resiliency is the ability of a system to gracefully handle and recover
from failures. The nature of cloud hosting, where applications are often
multitenant, use shared platform services, compete for resources and
bandwidth, communicate over the Internet, and run on commodity hardware
means there is an increased likelihood that both transient and more
permanent faults will arise. Detecting failures, and recovering quickly
and efficiently, is necessary to maintain resiliency.

### Security  

Security is the capability of a system to prevent malicious or
accidental actions outside of the designed usage, and to prevent
disclosure or loss of information. Cloud applications are exposed on the
Internet outside trusted on-premises boundaries, are often open to the
public, and may serve untrusted users. Applications must be designed and
deployed in a way that protects them from malicious attacks, restricts
access to only approved users, and protects sensitive data.

### Catalog of Patterns
|Category|Pattern|Summary|
|--- |--- |--- |
|Availability|Geodes|Deploy backend services into a set of geographical nodes, each of which can service any client request in any region.|
|Availability|Health Endpoint Monitoring Pattern|Implement functional checks in an application that external tools can access through exposed endpoints at regular intervals.|
|Availability|Queue-Based Load Leveling Pattern|Use a queue that acts as a buffer between a task and a service that it invokes, to smooth intermittent heavy loads.|
|Availability|Throttling Pattern|Control the consumption of resources by an instance of an application, an individual tenant, or an entire service.|
|Data Management|Cache-Aside Pattern|Load data on demand into a cache from a data store|
|Data Management|Command and Query Responsibility Segregation (CQRS) Pattern|Segregate operations that read data from operations that update data by using separate interfaces.|
|Data Management|Event Sourcing Pattern|Use an append-only store to record the full series of events that describe actions taken on data in a domain|
|Data Management|Index Table Pattern|Create indexes over the fields in data stores that are frequently referenced by queries.|
|Data Management|Materialized View Pattern|Generate prepopulated views over the data in one or more data stores when the data isn't ideally formatted for required query operations.|
|Data Management|Sharding Pattern|Divide a data store into a set of horizontal partitions or shards.|
|Data Management|Static Content Hosting Pattern|Deploy static content to a cloud-based storage service that can deliver them directly to the client.|
|Data Management|Valet Key Pattern|Use a token or key that provides clients with restricted direct access to a specific resource or service.|
|Design and Implementation|Ambassador Pattern|Create helper services that send network requests on behalf of a consumer service or application.|
|Design and Implementation|Anti-Corruption Layer Pattern|Implement a façade or adapter layer between a modern application and a legacy system.|
|Design and Implementation|Backends for Frontends Pattern|Create separate backend services to be consumed by specific frontend applications or interfaces.|
|Design and Implementation|Command and Query Responsibility Segregation (CQRS) Pattern|Segregate operations that read data from operations that update data by using separate interfaces|
|Design and Implementation|Compute Resource Consolidation Pattern|Consolidate multiple tasks or operations into a single computational unit|
|Design and Implementation|External Configuration Store Pattern|Move configuration information out of the application deployment package to a centralized location.|
|Design and Implementation|Gateway Aggregation Pattern|Use a gateway to aggregate multiple individual requests into a single request.|
|Design and Implementation|Gateway Offloading Pattern|Offload shared or specialized service functionality to a gateway proxy|
|Design and Implementation|Gateway Routing Pattern|Route requests to multiple services using a single endpoint.|
|Design and Implementation|Leader Election Pattern|Coordinate the actions performed by a collection of collaborating task instances in a distributed application by electing one instance as the leader that assumes responsibility for managing the other instances.|
|Design and Implementation|Pipes and Filters Pattern|Break down a task that performs complex processing into a series of separate elements that can be reused.|
|Design and Implementation|Sidecar Pattern|Deploy components of an application into a separate process or container to provide isolation and encapsulation.|
|Design and Implementation|Static Content Hosting Pattern|Deploy static content to a cloud-based storage service that can deliver them directly to the client.|
|Design and Implementation|Strangler Pattern|Incrementally migrate a legacy system by gradually replacing specific pieces of functionality with new applications and services.|
|Management and Monitoring|Ambassador Pattern|Create helper services that send network requests on behalf of a consumer service or application.|
|Management and Monitoring|Anti-Corruption Layer Pattern|Implement a façade or adapter layer between a modern application and a legacy system.|
|Management and Monitoring|External Configuration Store Pattern|Move configuration information out of the application deployment package to a centralized location.|
|Management and Monitoring|Gateway Aggregation Pattern|Use a gateway to aggregate multiple individual requests into a single request.|
|Management and Monitoring|Gateway Offloading Pattern|Offload shared or specialized service functionality to a gateway proxy.|
|Management and Monitoring|Gateway Routing Pattern|Route requests to multiple services using a single endpoint.|
|Management and Monitoring|Health Endpoint Monitoring Pattern|Implement functional checks in an application that external tools can access through exposed endpoints at regular intervals.|
|Management and Monitoring|Sidecar Pattern|Deploy components of an application into a separate process or container to provide isolation and encapsulation.|
|Management and Monitoring|Strangler Pattern|Incrementally migrate a legacy system by gradually replacing specific pieces of functionality with new applications and services.|
|Messaging|Asynchronous Request-Reply Pattern|Decouple backend processing from a frontend host, where backend processing needs to be asynchronous, but the frontend still needs a clear response.|
|Messaging|Claim-Check Pattern|Split a large message into a claim check and a payload to avoid overwhelming a message bus.|
|Messaging|Choreography Pattern|Have each component of the system participate in the decision-making process about the workflow of a business transaction, instead of relying on a central point of control.|
|Messaging|Competing Consumers Pattern|Enable multiple concurrent consumers to process messages received on the same messaging channel.|
|Messaging|Pipes and Filters Pattern|Break down a task that performs complex processing into a series of separate elements that can be reused.|
|Messaging|Priority Queue Pattern|Prioritize requests sent to services so that requests with a higher priority are received and processed more quickly than those with a lower priority.|
|Messaging|Publisher-Subscriber Pattern|Enable an application to announce events to multiple interested consumers asynchronously, without coupling the senders to the receivers.|
|Messaging|Queue-Based Load Leveling Pattern|Use a queue that acts as a buffer between a task and a service that it invokes in order to smooth intermittent heavy loads.|
|Messaging|Scheduler Agent Supervisor Pattern|Coordinate a set of actions across a distributed set of services and other remote resources.|
|Messaging|Sequential Convoy Pattern|Process a set of related messages in a defined order, without blocking processing of other groups of messages.|
|Performance and Scalability|Cache-Aside Pattern|Load data on demand into a cache from a data store|
|Performance and Scalability|Choreography Pattern|Have each component of the system participate in the decision-making process about the workflow of a business transaction, instead of relying on a central point of control.|
|Performance and Scalability|Command and Query Responsibility Segregation (CQRS) Pattern|Segregate operations that read data from operations that update data by using separate interfaces.|
|Performance and Scalability|Event Sourcing Pattern|Use an append-only store to record the full series of events that describe actions taken on data in a domain.|
|Performance and Scalability|Geodes|Deploy backend services into a set of geographical nodes, each of which can service any client request in any region.|
|Performance and Scalability|Index Table Pattern|Create indexes over the fields in data stores that are frequently referenced by queries.|
|Performance and Scalability|Materialized View Pattern|Generate prepopulated views over the data in one or more data stores when the data isn't ideally formatted for required query operations.|
|Performance and Scalability|Priority Queue Pattern|Prioritize requests sent to services so that requests with a higher priority are received and processed more quickly than those with a lower priority.|
|Performance and Scalability|Queue-Based Load Leveling Pattern|Use a queue that acts as a buffer between a task and a service that it invokes in order to smooth intermittent heavy loads.|
|Performance and Scalability|Sharding Pattern|Divide a data store into a set of horizontal partitions or shards.|
|Performance and Scalability|Static Content Hosting Pattern|Deploy static content to a cloud-based storage service that can deliver them directly to the client.|
|Performance and Scalability|Throttling Pattern|Control the consumption of resources used by an instance of an application, an individual tenant, or an entire service.|
|Resiliency|Bulkhead Pattern|Isolate elements of an application into pools so that if one fails, the others will continue to function.|
|Resiliency|Circuit Breaker Pattern|Handle faults that might take a variable amount of time to fix when connecting to a remote service or resource.|
|Resiliency|Compensating Transaction Pattern|Undo the work performed by a series of steps, which together define an eventually consistent operation.|
|Resiliency|Health Endpoint Monitoring Pattern|Implement functional checks in an application that external tools can access through exposed endpoints at regular intervals.|
|Resiliency|Leader Election Pattern|Coordinate the actions performed by a collection of collaborating task instances in a distributed application by electing one instance as the leader that assumes responsibility for managing the other instances.|
|Resiliency|Queue-Based Load Leveling Pattern|Use a queue that acts as a buffer between a task and a service that it invokes in order to smooth intermittent heavy loads.|
|Resiliency|Retry Pattern|Enable an application to handle anticipated, temporary failures when it tries to connect to a service or network resource by transparently retrying an operation that's previously failed.|
|Resiliency|Scheduler Agent Supervisor Pattern|Coordinate a set of actions across a distributed set of services and other remote resources.|
|Security|Federated Identity Pattern|Delegate authentication to an external identity provider.|
|Security|Gatekeeper Pattern|Protect applications and services by using a dedicated host instance that acts as a broker between clients and the application or service, validates and sanitizes requests, and passes requests and data between them.|
|Security|Valet Key Pattern|Use a token or key that provides clients with restricted direct access to a specific resource or service.|


Design Patterns
---------------

### Ambassador Pattern

#### Overview

Create helper services that send network requests on behalf of a
consumer service or application. An ambassador service can be thought of
as an out-of-process proxy that is co-located with the client.

This pattern can be useful for offloading common client connectivity
tasks such as monitoring, logging, routing, security (such as TLS), and 
[resiliency patterns](https://docs.microsoft.com/en-us/azure/architecture/patterns/category/resiliency) in
a language agnostic way. It is often used with legacy applications, or
other applications that are difficult to modify, in order to extend
their networking capabilities. It can also enable a specialized team to
implement those features.

#### Context and Problem

Resilient cloud-based applications require features such as  [circuit breaking](https://docs.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker),
routing, metering and monitoring, and the ability to make
network-related configuration updates. It may be difficult or impossible
to update legacy applications or existing code libraries to add these
features, because the code is no longer maintained or can\'t be easily
modified by the development team.

Network calls may also require substantial configuration for connection,
authentication, and authorization. If these calls are used across
multiple applications, built using multiple languages and frameworks,
the calls must be configured for each of these instances. In addition,
network and security functionality may need to be managed by a central
team within your organization. With a large code base, it can be risky
for that team to update application code they aren\'t familiar with.

#### Solution

Put client frameworks and libraries into an external process that acts
as a proxy between your application and external services. Deploy the
proxy on the same host environment as your application to allow control
over routing, resiliency, security features, and to avoid any
host-related access restrictions. You can also use the ambassador
pattern to standardize and extend instrumentation. The proxy can monitor
performance metrics such as latency or resource usage, and this
monitoring happens in the same host environment as the application.

<img src="./attachments/463533288.png" alt="">

Features that are offloaded to the ambassador can be managed
independently of the application. You can update and modify the
ambassador without disturbing the application\'s legacy functionality.
It also allows for separate, specialized teams to implement and maintain
security, networking, or authentication features that have been moved to
the ambassador.

Ambassador services can be deployed as a 
[sidecar](https://docs.microsoft.com/en-us/azure/architecture/patterns/sidecar) to
accompany the lifecycle of a consuming application or service.
Alternatively, if an ambassador is shared by multiple separate processes
on a common host, it can be deployed as a daemon or Windows service. If
the consuming service is containerized, the ambassador should be created
as a separate container on the same host, with the appropriate links
configured for communication.

#### Issues and Considerations

-   The proxy adds some latency overhead. Consider whether a client
    library, invoked directly by the application, is a better approach.
-   Consider the possible impact of including generalized features in
    the proxy. For example, the ambassador could handle retries, but
    that might not be safe unless all operations are idempotent.
-   Consider a mechanism to allow the client to pass some context to the
    proxy, as well as back to the client. For example, include HTTP
    request headers to opt out of retry or specify the maximum number of
    times to retry.
-   Consider how you will package and deploy the proxy.
-   Consider whether to use a single shared instance for all clients or
    an instance for each client.

#### When to use this Pattern

Use this pattern when you:

-   Need to build a common set of client connectivity features for
    multiple languages or frameworks.
-   Need to offload cross-cutting client connectivity concerns to
    infrastructure developers or other more specialized teams.
-   Need to support cloud or cluster connectivity requirements in a
    legacy application or an application that is difficult to modify.

This pattern may not be suitable:

-   When network request latency is critical. A proxy will introduce
    some overhead, although minimal, and in some cases this may affect
    the application.
-   When client connectivity features are consumed by a single language.
    In that case, a better option might be a client library that is
    distributed to the development teams as a package.
-   When connectivity features cannot be generalized and require deeper
    integration with the client application.

### Anti-Corruption Layer Pattern

#### Overview

Create helper services that send network requests on behalf of a
consumer service or application. An ambassador service can be thought of
as an out-of-process proxy that is co-located with the client.

This pattern can be useful for offloading common client connectivity
tasks such as monitoring, logging, routing, security (such as TLS), and 
[resiliency patterns](https://docs.microsoft.com/en-us/azure/architecture/patterns/category/resiliency) in
a language agnostic way. It is often used with legacy applications, or
other applications that are difficult to modify, in order to extend
their networking capabilities. It can also enable a specialized team to
implement those features.

#### Context and Problem

Resilient cloud-based applications require features such as  [circuit breaking](https://docs.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker),
routing, metering and monitoring, and the ability to make
network-related configuration updates. It may be difficult or impossible
to update legacy applications or existing code libraries to add these
features, because the code is no longer maintained or can\'t be easily
modified by the development team.

Network calls may also require substantial configuration for connection,
authentication, and authorization. If these calls are used across
multiple applications, built using multiple languages and frameworks,
the calls must be configured for each of these instances. In addition,
network and security functionality may need to be managed by a central
team within your organization. With a large code base, it can be risky
for that team to update application code they aren\'t familiar with.

#### Solution

Put client frameworks and libraries into an external process that acts
as a proxy between your application and external services. Deploy the
proxy on the same host environment as your application to allow control
over routing, resiliency, security features, and to avoid any
host-related access restrictions. You can also use the ambassador
pattern to standardize and extend instrumentation. The proxy can monitor
performance metrics such as latency or resource usage, and this
monitoring happens in the same host environment as the application.

<img src="./attachments/463533415.jpg" alt="">


Features that are offloaded to the ambassador can be managed
independently of the application. You can update and modify the
ambassador without disturbing the application\'s legacy functionality.
It also allows for separate, specialized teams to implement and maintain
security, networking, or authentication features that have been moved to
the ambassador.

Ambassador services can be deployed as a 
[sidecar](https://docs.microsoft.com/en-us/azure/architecture/patterns/sidecar) to
accompany the lifecycle of a consuming application or service.
Alternatively, if an ambassador is shared by multiple separate processes
on a common host, it can be deployed as a daemon or Windows service. If
the consuming service is containerized, the ambassador should be created
as a separate container on the same host, with the appropriate links
configured for communication.

#### Issues and Considerations

-   The proxy adds some latency overhead. Consider whether a client
    library, invoked directly by the application, is a better approach.
-   Consider the possible impact of including generalized features in
    the proxy. For example, the ambassador could handle retries, but
    that might not be safe unless all operations are idempotent.
-   Consider a mechanism to allow the client to pass some context to the
    proxy, as well as back to the client. For example, include HTTP
    request headers to opt out of retry or specify the maximum number of
    times to retry.
-   Consider how you will package and deploy the proxy.
-   Consider whether to use a single shared instance for all clients or
    an instance for each client.

#### When to use this Pattern

Use this pattern when you:

-   Need to build a common set of client connectivity features for
    multiple languages or frameworks.
-   Need to offload cross-cutting client connectivity concerns to
    infrastructure developers or other more specialized teams.
-   Need to support cloud or cluster connectivity requirements in a
    legacy application or an application that is difficult to modify.

This pattern may not be suitable:

-   When network request latency is critical. A proxy will introduce
    some overhead, although minimal, and in some cases this may affect
    the application.
-   When client connectivity features are consumed by a single language.
    In that case, a better option might be a client library that is
    distributed to the development teams as a package.
-   When connectivity features cannot be generalized and require deeper
    integration with the client application.

### Asynchronous Request-Reply Pattern

#### Overview

Decouple backend processing from a frontend host, where backend
processing needs to be asynchronous, but the frontend still needs a
clear response.

#### Context and Problem

In modern application development, it\'s normal for client applications
--- often code running in a web-client (browser) --- to depend on remote
APIs to provide business logic and compose functionality. These APIs may
be directly related to the application or may be shared services
provided by a third party. Commonly these API calls take place over the
HTTP(S) protocol and follow REST semantics.

In most cases, APIs for a client application are designed to respond
quickly, on the order of 100 ms or less. Many factors can affect the
response latency, including:

-   An application\'s hosting stack
-   Security components
-   The relative geographic location of the caller and the backend
-   Network infrastructure
-   Current load
-   The size of the request payload
-   Processing queue length
-   The time for the backend to process the request

Any of these factors can add latency to the response. Some can be
mitigated by scaling out the backend. Others, such as network
infrastructure, are largely out of the control of the application
developer. Most APIs can respond quickly enough for responses to arrive
back over the same connection. Application code can make a synchronous
API call in a non-blocking way, giving the appearance of asynchronous
processing, which is recommended for I/O-bound operations.

In some scenarios, however, the work done by backend may be
long-running, on the order of seconds, or might be a background process
that is executed in minutes or even hours. In that case, it isn\'t
feasible to wait for the work to complete before responding to the
request. This situation is a potential problem for any synchronous
request-reply pattern.

Some architectures solve this problem by using a message broker to
separate the request and response stages. This separation is often
achieved by use of the  [Queue Based Load Leveling
Pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/queue-based-load-leveling).
This separation can allow the client process and the backend API to
scale independently. But this separation also brings additional
complexity when the client requires success notification, as this step
needs to become asynchronous.

Many of the same considerations discussed for client applications also
apply for server-to-server REST API calls in distributed systems --- for
example, in a microservices architecture.

#### Solution

One solution to this problem is to use HTTP polling. Polling is useful
to client-side code, as it can be hard to provide call-back endpoints or
use long running connections. Even when callbacks are possible, the
extra libraries and services that are required can sometimes add too
much extra complexity.

-   The client application makes a synchronous call to the API,
    triggering a long-running operation on the backend.

-   The API responds synchronously as quickly as possible. It returns an
    HTTP 202 (Accepted) status code, acknowledging that the request has
    been received for processing.

    *Note: The API should validate both the request and the action to be
    performed before starting the long running process. If the request
    is invalid, reply immediately with an error code such as HTTP 400
    (Bad Request).*

-   The response holds a location reference pointing to an endpoint that
    the client can poll to check for the result of the long running
    operation.

-   The API offloads processing to another component, such as a message
    queue.

-   While the work is still pending, the status endpoint returns
    HTTP 202. Once the work is complete, the status endpoint can either
    return a resource that indicates completion, or redirect to another
    resource URL. For example, if the asynchronous operation creates a
    new resource, the status endpoint would redirect to the URL for that
    resource.

The following diagram shows a typical flow:

![](attachments/463533293/463533292.png)


1.  The client sends a request and receives an HTTP 202 (Accepted)
    response.
2.  The client sends an HTTP GET request to the status endpoint. The
    work is still pending, so this call also returns HTTP 202.
3.  At some point, the work is complete and the status endpoint returns
    302 (Found) redirecting to the resource.
4.  The client fetches the resource at the specified URL.

#### Issues and Considerations

-   There are a number of possible ways to implement this pattern over
    HTTP and not all upstream services have the same semantics. For
    example, most services won\'t return an HTTP 202 response back from
    a GET method when a remote process hasn\'t finished. Following pure
    REST semantics, they should return HTTP 404 (Not Found). This
    response makes sense when you consider the result of the call isn\'t
    present yet.

-   An HTTP 202 response should indicate the location and frequency that
    the client should poll for the response. It should have the
    following additional headers:

    |Header|Description|Notes|
    |--- |--- |--- |
    |Location|A URL the client should poll for a response status.|This URL could be a SAS token with the Valet Key Pattern being appropriate if this location needs access control. The valet key pattern is also valid when response polling needs offloading to another backend|
    |Retry-After|An estimate of when processing will complete|This header is designed to prevent polling clients from overwhelming the back-end with retries.|

-   You may need to use a processing proxy or facade to manipulate the
    response headers or payload depending on the underlying services
    used.

-   If the status endpoint redirects on completion, either  [HTTP 302](https://tools.ietf.org/html/rfc7231#section-6.4.3) or 
    [HTTP 303](https://tools.ietf.org/html/rfc7231#section-6.4.4) are
    appropriate return codes, depending on the exact semantics you
    support.

-   Upon successful processing, the resource specified by the Location
    header should return an appropriate HTTP response code such as 200
    (OK), 201 (Created), or 204 (No Content).

-   If an error occurs during processing, persist the error at the
    resource URL described in the Location header and ideally return an
    appropriate response code to the client from that resource (4xx
    code).

-   Not all solutions will implement this pattern in the same way and
    some services will include additional or alternate headers. For
    example, Azure Resource Manager uses a modified variant of this
    pattern. For more information, see  [Azure Resource Manager Async Operations](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-async-operations).

-   Legacy clients might not support this pattern. In that case, you
    might need to place a facade over the asynchronous API to hide the
    asynchronous processing from the original client. For example, Azure
    Logic Apps supports this pattern natively can be used as an
    integration layer between an asynchronous API and a client that
    makes synchronous calls. See  [Perform long-running tasks with the webhook action pattern](https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-create-api-app#perform-long-running-tasks-with-the-webhook-action-pattern).

-   In some scenarios, you might want to provide a way for clients to
    cancel a long-running request. In that case, the backend service
    must support some form of cancellation instruction.

#### When to use this Pattern

Use this pattern for:

-   Client-side code, such as browser applications, where it\'s
    difficult to provide call-back endpoints, or the use of long-running
    connections adds too much additional complexity.

-   Service calls where only the HTTP protocol is available and the
    return service can\'t fire callbacks because of firewall
    restrictions on the client-side.

-   Service calls that need to be integrated with legacy architectures
    that don\'t support modern callback technologies such as WebSockets
    or webhooks.

This pattern might not be suitable when:

-   You can use a service built for asynchronous notifications instead,
    such as Azure Event Grid.
-   Responses must stream in real time to the client.
-   The client needs to collect many results, and received latency of
    those results is important. Consider a service bus pattern instead.
-   You can use server-side persistent network connections such as
    WebSockets or SignalR. These services can be used to notify the
    caller of the result.
-   The network design allows you to open up ports to receive
    asynchronous callbacks or webhooks.

### Backends for Frontends Pattern

#### Overview

Create separate backend services to be consumed by specific frontend
applications or interfaces. This pattern is useful when you want to
avoid customizing a single backend for multiple interfaces. This pattern
was first described by Sam Newman.

#### Context and Problem

An application may initially be targeted at a desktop web UI. Typically,
a backend service is developed in parallel that provides the features
needed for that UI. As the application\'s user base grows, a mobile
application is developed that must interact with the same backend. The
backend service becomes a general-purpose backend, serving the
requirements of both the desktop and mobile interfaces.

But the capabilities of a mobile device differ significantly from a
desktop browser, in terms of screen size, performance, and display
limitations. As a result, the requirements for a mobile application
backend differ from the desktop web UI.

These differences result in competing requirements for the backend. The
backend requires regular and significant changes to serve both the
desktop web UI and the mobile application. Often, separate interface
teams work on each frontend, causing the backend to become a bottleneck
in the development process. Conflicting update requirements, and the
need to keep the service working for both frontends, can result in
spending a lot of effort on a single deployable resource.

<img src="./attachments/463533295.png" alt="">

As the development activity focuses on the backend service, a separate
team may be created to manage and maintain the backend. Ultimately, this
results in a disconnect between the interface and backend development
teams, placing a burden on the backend team to balance the competing
requirements of the different UI teams. When one interface team requires
changes to the backend, those changes must be validated with other
interface teams before they can be integrated into the backend.

#### Solution

Create one backend per user interface. Fine-tune the behavior and
performance of each backend to best match the needs of the frontend
environment, without worrying about affecting other frontend
experiences.

<img src="./attachments/463533296.png" alt="">

Because each backend is specific to one interface, it can be optimized
for that interface. As a result, it will be smaller, less complex, and
likely faster than a generic backend that tries to satisfy the
requirements for all interfaces. Each interface team has autonomy to
control their own backend and doesn\'t rely on a centralized backend
development team. This gives the interface team flexibility in language
selection, release cadence, prioritization of workload, and feature
integration in their backend.

For more information, see  [Pattern: Backends For Frontends](https://samnewman.io/patterns/architectural/bff/).

#### Issues and Considerations

-   onsider how many backends to deploy.
-   If different interfaces (such as mobile clients) will make the same
    requests, consider whether it is necessary to implement a backend
    for each interface, or if a single backend will suffice.
-   Code duplication across services is highly likely when implementing
    this pattern.
-   Frontend-focused backend services should only contain
    client-specific logic and behavior. General business logic and other
    global features should be managed elsewhere in your application.
-   Think about how this pattern might be reflected in the
    responsibilities of a development team.
-   Consider how long it will take to implement this pattern. Will the
    effort of building the new backends incur technical debt, while you
    continue to support the existing generic backend?

#### When to use this Pattern

Use this pattern when:

-   A shared or general purpose backend service must be maintained with
    significant development overhead.
-   You want to optimize the backend for the requirements of specific
    client interfaces.
-   Customizations are made to a general-purpose backend to accommodate
    multiple interfaces.
-   An alternative language is better suited for the backend of a
    different user interface.

This pattern may not be suitable:

-   When interfaces make the same or similar requests to the backend.
-   When only one interface is used to interact with the backend.

### Bulkhead Pattern

#### Overview

The Bulkhead pattern is a type of application design that is tolerant of
failure. In a bulkhead architecture, elements of an application are
isolated into pools so that if one fails, the others will continue to
function. It\'s named after the sectioned partitions (bulkheads) of a
ship\'s hull. If the hull of a ship is compromised, only the damaged
section fills with water, which prevents the ship from sinking.

#### Context and Problem

A cloud-based application may include multiple services, with each
service having one or more consumers. Excessive load or failure in a
service will impact all consumers of the service.

Moreover, a consumer may send requests to multiple services
simultaneously, using resources for each request. When the consumer
sends a request to a service that is misconfigured or not responding,
the resources used by the client\'s request may not be freed in a timely
manner. As requests to the service continue, those resources may be
exhausted. For example, the client\'s connection pool may be exhausted.
At that point, requests by the consumer to other services are affected.
Eventually the consumer can no longer send requests to other services,
not just the original unresponsive service.

The same issue of resource exhaustion affects services with multiple
consumers. A large number of requests originating from one client may
exhaust available resources in the service. Other consumers are no
longer able to consume the service, causing a cascading failure effect.

#### Solution

Partition service instances into different groups, based on consumer
load and availability requirements. This design helps to isolate
failures, and allows you to sustain service functionality for some
consumers, even during a failure.

A consumer can also partition resources, to ensure that resources used
to call one service don\'t affect the resources used to call another
service. For example, a consumer that calls multiple services may be
assigned a connection pool for each service. If a service begins to
fail, it only affects the connection pool assigned for that service,
allowing the consumer to continue using the other services.

The benefits of this pattern include:

-   Isolates consumers and services from cascading failures. An issue
    affecting a consumer or service can be isolated within its own
    bulkhead, preventing the entire solution from failing.
-   Allows you to preserve some functionality in the event of a service
    failure. Other services and features of the application will
    continue to work.
-   Allows you to deploy services that offer a different quality of
    service for consuming applications. A high-priority consumer pool
    can be configured to use high-priority services.

The following diagram shows bulkheads structured around connection pools
that call individual services. If Service A fails or causes some other
issue, the connection pool is isolated, so only workloads using the
thread pool assigned to Service A are affected. Workloads that use
Service B and C are not affected and can continue working without
interruption.

<img src="./attachments/463533299.png" alt="">

The next diagram shows multiple clients calling a single service. Each
client is assigned a separate service instance. Client 1 has made too
many requests and overwhelmed its instance. Because each service
instance is isolated from the others, the other clients can continue
making calls.

<img src="./attachments/463533300.png" alt="">


#### Issues and Considerations

-   Define partitions around the business and technical requirements of
    the application.
-   When partitioning services or consumers into bulkheads, consider the
    level of isolation offered by the technology as well as the overhead
    in terms of cost, performance and manageability.
-   Consider combining bulkheads with retry, circuit breaker, and
    throttling patterns to provide more sophisticated fault handling.
-   When partitioning consumers into bulkheads, consider using
    processes, thread pools, and semaphores. Projects like 
    [resilience4j](https://github.com/resilience4j/resilience4j) and 
    [Polly](https://github.com/App-vNext/Polly) offer a
    framework for creating consumer bulkheads.
-   When partitioning services into bulkheads, consider deploying them
    into separate virtual machines, containers, or processes. Containers
    offer a good balance of resource isolation with fairly low overhead.
-   Services that communicate using asynchronous messages can be
    isolated through different sets of queues. Each queue can have a
    dedicated set of instances processing messages on the queue, or a
    single group of instances using an algorithm to dequeue and dispatch
    processing.
-   Determine the level of granularity for the bulkheads. For example,
    if you want to distribute tenants across partitions, you could place
    each tenant into a separate partition, or put several tenants into
    one partition.
-   Monitor each partition's performance and SLA.

#### When to use this Pattern

#### Use this pattern to:

-   Isolate resources used to consume a set of backend services,
    especially if the application can provide some level of
    functionality even when one of the services is not responding.
-   Isolate critical consumers from standard consumers.
-   Protect the application from cascading failures.

This pattern may not be suitable when:

-   Less efficient use of resources may not be acceptable in the
    project.
-   The added complexity is not necessary

### Cache-Aside Pattern

#### Overview

Load data on demand into a cache from a data store. This can improve
performance and also helps to maintain consistency between data held in
the cache and data in the underlying data store.

#### Context and Problem

Applications use a cache to improve repeated access to information held
in a data store. However, it\'s impractical to expect that cached data
will always be completely consistent with the data in the data store.
Applications should implement a strategy that helps to ensure that the
data in the cache is as up-to-date as possible, but can also detect and
handle situations that arise when the data in the cache has become
stale.

#### Solution

Many commercial caching systems provide read-through and
write-through/write-behind operations. In these systems, an application
retrieves data by referencing the cache. If the data isn\'t in the
cache, it\'s retrieved from the data store and added to the cache. Any
modifications to data held in the cache are automatically written back
to the data store as well.

For caches that don\'t provide this functionality, it\'s the
responsibility of the applications that use the cache to maintain the
data.

An application can emulate the functionality of read-through caching by
implementing the cache-aside strategy. This strategy loads data into the
cache on demand. The figure illustrates using the Cache-Aside pattern to
store data in the cache.

<img src="./attachments/463533303.png" alt="">

If an application updates information, it can follow the write-through
strategy by making the modification to the data store, and by
invalidating the corresponding item in the cache.

When the item is next required, using the cache-aside strategy will
cause the updated data to be retrieved from the data store and added
back into the cache.

#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

**Lifetime of cached data**. Many caches implement an expiration policy
that invalidates data and removes it from the cache if it\'s not
accessed for a specified period. For cache-aside to be effective, ensure
that the expiration policy matches the pattern of access for
applications that use the data. Don\'t make the expiration period too
short because this can cause applications to continually retrieve data
from the data store and add it to the cache. Similarly, don\'t make the
expiration period so long that the cached data is likely to become
stale. Remember that caching is most effective for relatively static
data, or data that is read frequently.

**Evicting data**. Most caches have a limited size compared to the data
store where the data originates, and they\'ll evict data if necessary.
Most caches adopt a least-recently-used policy for selecting items to
evict, but this might be customizable. Configure the global expiration
property and other properties of the cache, and the expiration property
of each cached item, to ensure that the cache is cost effective. It
isn\'t always appropriate to apply a global eviction policy to every
item in the cache. For example, if a cached item is very expensive to
retrieve from the data store, it can be beneficial to keep this item in
the cache at the expense of more frequently accessed but less costly
items.

**Priming the cache**. Many solutions prepopulate the cache with the
data that an application is likely to need as part of the startup
processing. The Cache-Aside pattern can still be useful if some of this
data expires or is evicted.

**Consistency**. Implementing the Cache-Aside pattern doesn\'t guarantee
consistency between the data store and the cache. An item in the data
store can be changed at any time by an external process, and this change
might not be reflected in the cache until the next time the item is
loaded. In a system that replicates data across data stores, this
problem can become serious if synchronization occurs frequently.

**Local (in-memory) caching**. A cache could be local to an application
instance and stored in-memory. Cache-aside can be useful in this
environment if an application repeatedly accesses the same data.
However, a local cache is private and so different application instances
could each have a copy of the same cached data. This data could quickly
become inconsistent between caches, so it might be necessary to expire
data held in a private cache and refresh it more frequently. In these
scenarios, consider investigating the use of a shared or a distributed
caching mechanism.

#### When to use this Pattern

Use this pattern when:

-   A cache doesn\'t provide native read-through and write-through
    operations.
-   Resource demand is unpredictable. This pattern enables applications
    to load data on demand. It makes no assumptions about which data an
    application will require in advance.

This pattern might not be suitable:

-   When the cached data set is static. If the data will fit into the
    available cache space, prime the cache with the data on startup and
    apply a policy that prevents the data from expiring.
-   For caching session state information in a web application hosted in
    a web farm. In this environment, you should avoid introducing
    dependencies based on client-server affinity.

### Choreography Pattern

#### Overview

Have each component of the system participate in the decision-making
process about the workflow of a business transaction, instead of relying
on a central point of control.

#### Context and Problem

In microservices architecture, it's often the case that a cloud-based
application is divided into several small services that work together to
process a business transaction end-to-end. To lower coupling between
services, each service is responsible for a single business operation.
Some benefits include faster development, smaller code base, and
scalability. However, designing an efficient and scalable workflow is a
challenge and often requires complex interservice communication.

The services communicate with each other by using well-defined APIs.
Even a single business operation can result in multiple point-to-point
calls amongst all services. A common pattern for communication is to use
a centralized service that acts as the orchestrator. It acknowledges all
incoming requests and delegates operations to the respective services.
In doing so, it also manages the workflow of the entire business
transaction. Each service just completes an operation and is not aware
of the overall workflow.

The orchestrator pattern reduces point-to-point communication between
services but has some drawbacks because of the tight coupling between
the orchestrator and other services that participate in processing of
the business transaction. To execute tasks in a sequence, the
orchestrator needs to have some domain knowledge about the
responsibilities of those services. If you want to add or remove
services, existing logic will break, and you\'ll need to rewire portions
of the communication path. While you can configure the workflow, add or
remove services easily with a well-designed orchestrator, such an
implementation is complex hard to maintain.

<img src="./attachments/463533306.png" alt="">

#### Solution

Let each service decide when and how a business operation is processed,
instead of depending on a central orchestrator.

One way to implement choreography is to use the  [asynchronous messaging pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/publisher-subscriber) to
coordinate the business operations.

<img src="./attachments/463533307.png" alt="">

A client request publishes messages to a message queue. As messages
arrive, they are pushed to subscribers, or services, interested in that
message. Each subscribed service does their operation as indicated by
the message and responds to the message queue with success or failure of
the operation. In case of success, the service can push a message back
to the same queue or a different message queue so that another service
can continue the workflow if needed. If an operation fails, the message
bus can retry that operation.

This way, the services choreograph the workflow among themselves without
depending on an orchestrator or having direct communication between
them.

Because there isn\'t point-to-point communication, this pattern helps
reduce coupling between services. Also, it can remove the performance
bottleneck caused by the orchestrator when it has to deal with all
transactions.

#### Issues and Considerations

Decentralizing the orchestrator can cause issues while managing the
workflow.

If a service fails to complete a business operation, it can be difficult
to recover from that failure. One way is to have the service indicate
failure by firing an event. Another service subscribes to those failed
events takes necessary actions such as applying  [compensating transactions](https://docs.microsoft.com/en-us/azure/architecture/patterns/compensating-transaction) to
undo successful operations in a request. The failed service might also
fail to fire an event for the failure. In that case, consider using a
retry and, or time out mechanism to recognize that operation as a
failure. For an example, see the Example section.

It\'s simple to implement a workflow when you want to process
independent business operations in parallel. You can use a single
message bus. However, the workflow can become complicated when
choreography needs to occur in a sequence. For instance, Service C can
start its operation only after Service A and Service B have completed
their operations with success. One approach is to have multiple message
buses that get messages in the required order. For more information, see
the 
[Example](https://docs.microsoft.com/en-us/azure/architecture/patterns/choreography#example) section.

The choreography pattern becomes a challenge if the number of services
grow rapidly. Given the high number of independent moving parts, the
workflow between services tends to get complex. Also, distributed
tracing becomes difficult.

The orchestrator centrally manages the resiliency of the workflow and it
can become a single point of failure. On the other hand, for
choreography, the role is distributed between all services and
resiliency becomes less robust.

Each service isn\'t only responsible for the resiliency of its operation
but also the workflow. This responsibility can be burdensome for the
service and hard to implement. Each service must retry transient,
non-transient, and time-out failures, so that the request terminates
gracefully, if needed. Also, the service must be diligent about
communicating the success or failure of the operation so that other
services can act accordingly.

#### When to use this Pattern

Use the choreography pattern if you expect to update, remove, or add new
services frequently. The entire app can be modified with lesser effort
and minimal disruption to existing services.

Consider this pattern if you experience performance bottlenecks in the
central orchestrator.

This pattern is a natural model for the serverless architecture where
all services can be short lived, or event driven. Services can spin up
because of an event, do their task, and are removed when the task is
finished.

### Circuit Breaker Pattern

### Overview

Handle faults that might take a variable amount of time to recover from,
when connecting to a remote service or resource. This can improve the
stability and resiliency of an application.

#### Context and Problem

In a distributed environment, calls to remote resources and services can
fail due to transient faults, such as slow network connections,
timeouts, or the resources being overcommitted or temporarily
unavailable. These faults typically correct themselves after a short
period of time, and a robust cloud application should be prepared to
handle them by using a strategy such as the  [Retry pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/retry).

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

#### Solution

The Circuit Breaker pattern, popularized by Michael Nygard in his book, 
[Release It!](https://pragprog.com/book/mnee/release-it), can
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
    into the  **Open** state. At this point the proxy starts a timeout
    timer, and when this timer expires the proxy is placed into the 
    **Half-Open** state.

    > The purpose of the timeout timer is to give the system time to fix
    > the problem that caused the failure before allowing the
    > application to try to perform the operation again.

-   **Open**: The request from the application fails immediately and an
    exception is returned to the application.

-   **Half-Open**: A limited number of requests from the application are
    allowed to pass through and invoke the operation. If these requests
    are successful, it\'s assumed that the fault that was previously
    causing the failure has been fixed and the circuit breaker switches
    to the  **Closed** state (the failure counter is reset). If any
    request fails, the circuit breaker assumes that the fault is still
    present so it reverts back to the  **Open** state and restarts the
    timeout timer to give the system a further period of time to recover
    from the failure.

    > The **Half-Open**state is useful to prevent a recovering service
    > from suddenly being flooded with requests. As a service recovers,
    > it might be able to support a limited volume of requests until the
    > recovery is complete, but while recovery is in progress a flood of
    > work can cause the service to time out or fail again.

<img src="./attachments/463533310.png" alt="">


In the figure, the failure counter used by the  **Closed** state is time
based. It\'s automatically reset at periodic intervals. This helps to
prevent the circuit breaker from entering the  **Open** state if it
experiences occasional failures. The failure threshold that trips the
circuit breaker into the  **Open** state is only reached when a
specified number of failures have occurred during a specified interval.
The counter used by the  **Half-Open** state records the number of
successful attempts to invoke the operation. The circuit breaker reverts
to the  **Closed** state after a specified number of consecutive
operation invocations have been successful. If any invocation fails, the
circuit breaker enters the  **Open** state immediately and the success
counter will be reset the next time it enters the  **Half-Open** state.

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
the  **Open** state.

The pattern is customizable and can be adapted according to the type of
the possible failure. For example, you can apply an increasing timeout
timer to a circuit breaker. You could place the circuit breaker in the 
**Open** state for a few seconds initially, and then if the failure
hasn\'t been resolved increase the timeout to a few minutes, and so on.
In some cases, rather than the  **Open** state returning failure and
raising an exception, it could be useful to return a default value that
is meaningful to the application.

#### Issues and Considerations

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
breaker to the  **Open** state compared to the number of failures due to
the service being completely unavailable.

**Logging**. A circuit breaker should log all failed requests (and
possibly successful requests) to enable an administrator to monitor the
health of the operation.

**Recoverability**. You should configure the circuit breaker to match
the likely recovery pattern of the operation it\'s protecting. For
example, if the circuit breaker remains in the  **Open** state for a
long period, it could raise exceptions even if the reason for the
failure has been resolved. Similarly, a circuit breaker could fluctuate
and reduce the response times of applications if it switches from the 
**Open** state to the  **Half-Open** state too quickly.

**Testing Failed Operations**. In the  **Open** state, rather than using
a timer to determine when to switch to the  **Half-Open** state, a
circuit breaker can instead periodically ping the remote service or
resource to determine whether it\'s become available again. This ping
could take the form of an attempt to invoke an operation that had
previously failed, or it could use a special operation provided by the
remote service specifically for testing the health of the service, as
described by the  [Health Endpoint Monitoring pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/health-endpoint-monitoring).

**Manual Override**. In a system where the recovery time for a failing
operation is extremely variable, it\'s beneficial to provide a manual
reset option that enables an administrator to close a circuit breaker
(and reset the failure counter). Similarly, an administrator could force
a circuit breaker into the  **Open** state (and restart the timeout
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

**Replaying Failed Requests**. In the  **Open** state, rather than
simply failing quickly, a circuit breaker could also record the details
of each request to a journal and arrange for these requests to be
replayed when the remote resource or service becomes available.

**Inappropriate Timeouts on External Services**. A circuit breaker might
not be able to fully protect applications from operations that fail in
external services that are configured with a lengthy timeout period. If
the timeout is too long, a thread running a circuit breaker might be
blocked for an extended period before the circuit breaker indicates that
the operation has failed. In this time, many other application instances
might also try to invoke the service through the circuit breaker and tie
up a significant number of threads before they all fail.

#### When to use this Pattern

Use this pattern:

-   To prevent an application from trying to invoke a remote service or
    access a shared resource if this operation is highly likely to fail.

This pattern isn\'t recommended:

-   For handling access to local private resources in an application,
    such as in-memory data structure. In this environment, using a
    circuit breaker would add overhead to your system.
-   As a substitute for handling exceptions in the business logic of
    your applications.

### Claim-Check Pattern

#### Overview

Split a large message into a claim check and a payload. Send the claim
check to the messaging platform and store the payload to an external
service. This pattern allows large messages to be processed, while
protecting the message bus and the client from being overwhelmed or
slowed down. This pattern also helps to reduce costs, as storage is
usually cheaper than resource units used by the messaging platform.

This pattern is also known as Reference-Based Messaging, and was
originally 
[described](https://www.enterpriseintegrationpatterns.com/patterns/messaging/StoreInLibrary.html) in
the book  *Enterprise Integration Patterns*, by Gregor Hohpe and Bobby
Woolf.

#### Context and Problem

A messaging-based architecture at some point must be able to send,
receive, and manipulate large messages. Such messages may contain
anything, including images (for example, MRI scans), sound files (for
example, call-center calls), text documents, or any kind of binary data
of arbitrary size.

Sending such large messages to the message bus directly is not
recommended, because they require more resources and bandwidth to be
consumed. Large messages can also slow down the entire solution, because
messaging platforms are usually fine-tuned to handle huge quantities of
small messages. Also, most messaging platforms have limits on message
size, so you may need to work around these limits for large messages.

#### Solution

Store the entire message payload into an external service, such as a
database. Get the reference to the stored payload, and send just that
reference to the message bus. The reference acts like a claim check used
to retrieve a piece of luggage, hence the name of the pattern. Clients
interested in processing that specific message can use the obtained
reference to retrieve the payload, if needed.

<img src="./attachments/463533313.png" alt="">

#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

-   Consider deleting the message data after consuming it, if you don\'t
    need to archive the messages. Although blob storage is relatively
    cheap, it costs some money in the long run, especially if there is a
    lot of data. Deleting the message can be done synchronously by the
    application that receives and processes the message, or
    asynchronously by a separate dedicated process. The asynchronous
    approach removes old data with no impact on the throughput and
    message processing performance of the receiving application.

-   Storing and retrieving the message causes some additional overhead
    and latency. You may want to implement logic in the sending
    application to use this pattern only when the message size exceeds
    the data limit of the message bus. The pattern would be skipped for
    smaller messages. This approach would result in a conditional
    claim-check pattern.

#### When to use this Pattern

This pattern should be used whenever a message cannot fit the supported
message limit of the chosen message bus technology. For example, Event
Hubs currently has a limit of 256 KB (Basic Tier), while Event Grid
supports only 64-KB messages.

The pattern can also be used if the payload should be accessed only by
services that are authorized to see it. By offloading the payload to an
external resource, stricter authentication and authorization rules can
be put in place, to ensure that security is enforced when sensitive data
is stored in the payload.

### Command and Query Responsibility Segregation (CQRS) Pattern

#### Overview

The Command and Query Responsibility Segregation (CQRS) pattern
separates read and update operations for a data store. Implementing CQRS
in your application can maximize its performance, scalability, and
security. The flexibility created by migrating to CQRS allows a system
to better evolve over time and prevents update commands from causing
merge conflicts at the domain level.

#### Context and Problem

In traditional architectures, the same data model is used to query and
update a database. That\'s simple and works well for basic CRUD
operations. In more complex applications, however, this approach can
become unwieldy. For example, on the read side, the application may
perform many different queries, returning data transfer objects (DTOs)
with different shapes. Object mapping can become complicated. On the
write side, the model may implement complex validation and business
logic. As a result, you can end up with an overly complex model that
does too much.

Read and write workloads are often asymmetrical, with very different
performance and scale requirements.

<img src="./attachments/463533316.png" alt="">

-   There is often a mismatch between the read and write representations
    of the data, such as additional columns or properties that must be
    updated correctly even though they aren\'t required as part of an
    operation.

-   Data contention can occur when operations are performed in parallel
    on the same set of data.

-   The traditional approach can have a negative effect on performance
    due to load on the data store and data access layer, and the
    complexity of queries required to retrieve information.

-   Managing security and permissions can become complex, because each
    entity is subject to both read and write operations, which might
    expose data in the wrong context.

#### Solution

CQRS separates reads and writes into different models, using 
**commands** to update data, and  **queries** to read data.

-   Commands should be task based, rather than data centric. (\"Book
    hotel room\", not \"set ReservationStatus to Reserved\").
-   Commands may be placed on a queue for asynchronous processing,
    rather than being processed synchronously.
-   Queries never modify the database. A query returns a DTO that does
    not encapsulate any domain knowledge.

The models can then be isolated, as shown in the following diagram,
although that\'s not an absolute requirement.

<img src="./attachments/463533317.png" alt="">

Having separate query and update models simplifies the design and
implementation. However, one disadvantage is that CQRS code can\'t
automatically be generated from a database schema using scaffolding
mechanisms such as O/RM tools.

For greater isolation, you can physically separate the read data from
the write data. In that case, the read database can use its own data
schema that is optimized for queries. For example, it can store a 
[materialized
view](https://docs.microsoft.com/en-us/azure/architecture/patterns/materialized-view) of
the data, in order to avoid complex joins or complex O/RM mappings. It
might even use a different type of data store. For example, the write
database might be relational, while the read database is a document
database.

If separate read and write databases are used, they must be kept in
sync. Typically this is accomplished by having the write model publish
an event whenever it updates the database. Updating the database and
publishing the event must occur in a single transaction.

<img src="./attachments/463533318.png" alt="">

The read store can be a read-only replica of the write store, or the
read and write stores can have a different structure altogether. Using
multiple read-only replicas can increase query performance, especially
in distributed scenarios where read-only replicas are located close to
the application instances.

Separation of the read and write stores also allows each to be scaled
appropriately to match the load. For example, read stores typically
encounter a much higher load than write stores.

Some implementations of CQRS use the  [Event Sourcing
pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/event-sourcing).
With this pattern, application state is stored as a sequence of events.
Each event represents a set of changes to the data. The current state is
constructed by replaying the events. In a CQRS context, one benefit of
Event Sourcing is that the same events can be used to notify other
components --- in particular, to notify the read model. The read model
uses the events to create a snapshot of the current state, which is more
efficient for queries. However, Event Sourcing adds complexity to the
design.

Benefits of CQRS include:

-   **Independent scaling**. CQRS allows the read and write workloads to
    scale independently, and may result in fewer lock contentions.
-   **Optimized data schemas**. The read side can use a schema that is
    optimized for queries, while the write side uses a schema that is
    optimized for updates.
-   **Security**. It\'s easier to ensure that only the right domain
    entities are performing writes on the data.
-   **Separation of concerns**. Segregating the read and write sides can
    result in models that are more maintainable and flexible. Most of
    the complex business logic goes into the write model. The read model
    can be relatively simple.
-   **Simpler queries**. By storing a materialized view in the read
    database, the application can avoid complex joins when querying.

#### Issues and Considerations

Some challenges of implementing this pattern include:

-   **Complexity**. The basic idea of CQRS is simple. But it can lead to
    a more complex application design, especially if they include the
    Event Sourcing pattern.

-   **Messaging**. Although CQRS does not require messaging, it\'s
    common to use messaging to process commands and publish update
    events. In that case, the application must handle message failures
    or duplicate messages.

-   **Eventual consistency**. If you separate the read and write
    databases, the read data may be stale. The read model store must be
    updated to reflect changes to the write model store, and it can be
    difficult to detect when a user has issued a request based on stale
    read data.

#### When to use this Pattern

Consider CQRS for the following scenarios:

-   Collaborative domains where many users access the same data in
    parallel. CQRS allows you to define commands with enough granularity
    to minimize merge conflicts at the domain level, and conflicts that
    do arise can be merged by the command.

-   Task-based user interfaces where users are guided through a complex
    process as a series of steps or with complex domain models. The
    write model has a full command-processing stack with business logic,
    input validation, and business validation. The write model may treat
    a set of associated objects as a single unit for data changes (an
    aggregate, in DDD terminology) and ensure that these objects are
    always in a consistent state. The read model has no business logic
    or validation stack, and just returns a DTO for use in a view model.
    The read model is eventually consistent with the write model.

-   Scenarios where performance of data reads must be fine tuned
    separately from performance of data writes, especially when the
    number of reads is much greater than the number of writes. In this
    scenario, you can scale out the read model, but run the write model
    on just a few instances. A small number of write model instances
    also helps to minimize the occurrence of merge conflicts.

-   Scenarios where one team of developers can focus on the complex
    domain model that is part of the write model, and another team can
    focus on the read model and the user interfaces.

-   Scenarios where the system is expected to evolve over time and might
    contain multiple versions of the model, or where business rules
    change regularly.

-   Integration with other systems, especially in combination with event
    sourcing, where the temporal failure of one subsystem shouldn\'t
    affect the availability of the others.

This pattern isn\'t recommended when:

-   The domain or the business rules are simple.

-   A simple CRUD-style user interface and data access operations are
    sufficient.

Consider applying CQRS to limited sections of your system where it will
be most valuable.

### Compensating Transaction Pattern

#### Overview

Undo the work performed by a series of steps, which together define an
eventually consistent operation, if one or more of the steps fail.
Operations that follow the eventual consistency model are commonly found
in cloud-hosted applications that implement complex business processes
and workflows.

#### Context and Problem

Applications running in the cloud frequently modify data. This data
might be spread across various data sources held in different geographic
locations. To avoid contention and improve performance in a distributed
environment, an application shouldn\'t try to provide strong
transactional consistency. Rather, the application should implement
eventual consistency. In this model, a typical business operation
consists of a series of separate steps. While these steps are being
performed, the overall view of the system state might be inconsistent,
but when the operation has completed and all of the steps have been
executed the system should become consistent again.

> The  [Data Consistency Primer](https://msdn.microsoft.com/library/dn589800.aspx) provides
> information about why distributed transactions don\'t scale well, and
> the principles of the eventual consistency model.

A challenge in the eventual consistency model is how to handle a step
that has failed. In this case it might be necessary to undo all of the
work completed by the previous steps in the operation. However, the data
can\'t simply be rolled back because other concurrent instances of the
application might have changed it. Even in cases where the data hasn\'t
been changed by a concurrent instance, undoing a step might not simply
be a matter of restoring the original state. It might be necessary to
apply various business-specific rules (see the travel website described
in the Example section).

If an operation that implements eventual consistency spans several
heterogeneous data stores, undoing the steps in the operation will
require visiting each data store in turn. The work performed in every
data store must be undone reliably to prevent the system from remaining
inconsistent.

Not all data affected by an operation that implements eventual
consistency might be held in a database. In a service oriented
architecture (SOA) environment an operation could invoke an action in a
service, and cause a change in the state held by that service. To undo
the operation, this state change must also be undone. This can involve
invoking the service again and performing another action that reverses
the effects of the first.

#### Solution

The solution is to implement a compensating transaction. The steps in a
compensating transaction must undo the effects of the steps in the
original operation. A compensating transaction might not be able to
simply replace the current state with the state the system was in at the
start of the operation because this approach could overwrite changes
made by other concurrent instances of an application. Instead, it must
be an intelligent process that takes into account any work done by
concurrent instances. This process will usually be application specific,
driven by the nature of the work performed by the original operation.

A common approach is to use a workflow to implement an eventually
consistent operation that requires compensation. As the original
operation proceeds, the system records information about each step and
how the work performed by that step can be undone. If the operation
fails at any point, the workflow rewinds back through the steps it\'s
completed and performs the work that reverses each step. Note that a
compensating transaction might not have to undo the work in the exact
reverse order of the original operation, and it might be possible to
perform some of the undo steps in parallel.

> This approach is similar to the Sagas strategy discussed in  [Clemens Vasters' blog](https://vasters.com/clemensv/2012/09/01/Sagas.aspx).

A compensating transaction is also an eventually consistent operation
and it could also fail. The system should be able to resume the
compensating transaction at the point of failure and continue. It might
be necessary to repeat a step that\'s failed, so the steps in a
compensating transaction should be defined as idempotent commands. For
more information, see  [Idempotency Patterns](https://blog.jonathanoliver.com/idempotency-patterns/) on
Jonathan Oliver's blog.

In some cases it might not be possible to recover from a step that has
failed except through manual intervention. In these situations the
system should raise an alert and provide as much information as possible
about the reason for the failure.

#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

It might not be easy to determine when a step in an operation that
implements eventual consistency has failed. A step might not fail
immediately, but instead could block. It might be necessary to implement
some form of time-out mechanism.

-Compensation logic isn\'t easily generalized. A compensating
transaction is application specific. It relies on the application having
sufficient information to be able to undo the effects of each step in a
failed operation.

You should define the steps in a compensating transaction as idempotent
commands. This enables the steps to be repeated if the compensating
transaction itself fails.

The infrastructure that handles the steps in the original operation, and
the compensating transaction, must be resilient. It must not lose the
information required to compensate for a failing step, and it must be
able to reliably monitor the progress of the compensation logic.

A compensating transaction doesn\'t necessarily return the data in the
system to the state it was in at the start of the original operation.
Instead, it compensates for the work performed by the steps that
completed successfully before the operation failed.

The order of the steps in the compensating transaction doesn\'t
necessarily have to be the exact opposite of the steps in the original
operation. For example, one data store might be more sensitive to
inconsistencies than another, and so the steps in the compensating
transaction that undo the changes to this store should occur first.

Placing a short-term timeout-based lock on each resource that\'s
required to complete an operation, and obtaining these resources in
advance, can help increase the likelihood that the overall activity will
succeed. The work should be performed only after all the resources have
been acquired. All actions must be finalized before the locks expire.

Consider using retry logic that is more forgiving than usual to minimize
failures that trigger a compensating transaction. If a step in an
operation that implements eventual consistency fails, try handling the
failure as a transient exception and repeat the step. Only stop the
operation and initiate a compensating transaction if a step fails
repeatedly or irrecoverably.

> Many of the challenges of implementing a compensating transaction are
> the same as those with implementing eventual consistency. See the
> section Considerations for Implementing Eventual Consistency in the 
> [Data Consistency
> Primer](https://msdn.microsoft.com/library/dn589800.aspx) for
> more information.

#### When to use this Pattern

Use this pattern only for operations that must be undone if they fail.
If possible, design solutions to avoid the complexity of requiring
compensating transactions.

### Competing Consumers Pattern

#### Overview

Enable multiple concurrent consumers to process messages received on the
same messaging channel. This enables a system to process multiple
messages concurrently to optimize throughput, to improve scalability and
availability, and to balance the workload.

#### Context and Problem

An application running in the cloud is expected to handle a large number
of requests. Rather than process each request synchronously, a common
technique is for the application to pass them through a messaging system
to another service (a consumer service) that handles them
asynchronously. This strategy helps to ensure that the business logic in
the application isn\'t blocked while the requests are being processed.

The number of requests can vary significantly over time for many
reasons. A sudden increase in user activity or aggregated requests
coming from multiple tenants can cause an unpredictable workload. At
peak hours a system might need to process many hundreds of requests per
second, while at other times the number could be very small.
Additionally, the nature of the work performed to handle these requests
might be highly variable. Using a single instance of the consumer
service can cause that instance to become flooded with requests, or the
messaging system might be overloaded by an influx of messages coming
from the application. To handle this fluctuating workload, the system
can run multiple instances of the consumer service. However, these
consumers must be coordinated to ensure that each message is only
delivered to a single consumer. The workload also needs to be load
balanced across consumers to prevent an instance from becoming a
bottleneck.

#### Solution

Use a message queue to implement the communication channel between the
application and the instances of the consumer service. The application
posts requests in the form of messages to the queue, and the consumer
service instances receive messages from the queue and process them. This
approach enables the same pool of consumer service instances to handle
messages from any instance of the application. The figure illustrates
using a message queue to distribute work to instances of a service.

<img src="./attachments/463533327.png" alt="">

This solution has the following benefits:

-   It provides a load-leveled system that can handle wide variations in
    the volume of requests sent by application instances. The queue acts
    as a buffer between the application instances and the consumer
    service instances. This can help to minimize the impact on
    availability and responsiveness for both the application and the
    service instances, as described by the  [Queue-based Load Leveling
    pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/queue-based-load-leveling).
    Handling a message that requires some long-running processing
    doesn\'t prevent other messages from being handled concurrently by
    other instances of the consumer service.

-   It improves reliability. If a producer communicates directly with a
    consumer instead of using this pattern, but doesn\'t monitor the
    consumer, there\'s a high probability that messages could be lost or
    fail to be processed if the consumer fails. In this pattern,
    messages aren\'t sent to a specific service instance. A failed
    service instance won\'t block a producer, and messages can be
    processed by any working service instance.

-   It doesn\'t require complex coordination between the consumers, or
    between the producer and the consumer instances. The message queue
    ensures that each message is delivered at least once.

-   It\'s scalable. The system can dynamically increase or decrease the
    number of instances of the consumer service as the volume of
    messages fluctuates.

-   It can improve resiliency if the message queue provides
    transactional read operations. If a consumer service instance reads
    and processes the message as part of a transactional operation, and
    the consumer service instance fails, this pattern can ensure that
    the message will be returned to the queue to be picked up and
    handled by another instance of the consumer service.

#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

-   **Message ordering**. The order in which consumer service instances
    receive messages isn\'t guaranteed, and doesn\'t necessarily reflect
    the order in which the messages were created. Design the system to
    ensure that message processing is idempotent because this will help
    to eliminate any dependency on the order in which messages are
    handled. For more information, see  [Idempotency
    Patterns](https://blog.jonathanoliver.com/idempotency-patterns/) on
    Jonathon Oliver's blog.

    > Microsoft Azure Service Bus Queues can implement guaranteed
    > first-in-first-out ordering of messages by using message sessions.
    > For more information, see [Messaging Patterns Using
    > Sessions](https://msdn.microsoft.com/magazine/jj863132.aspx).

-   **Designing services for resiliency**. If the system is designed to
    detect and restart failed service instances, it might be necessary
    to implement the processing performed by the service instances as
    idempotent operations to minimize the effects of a single message
    being retrieved and processed more than once.

-   **Detecting poison messages**. A malformed message, or a task that
    requires access to resources that aren\'t available, can cause a
    service instance to fail. The system should prevent such messages
    being returned to the queue, and instead capture and store the
    details of these messages elsewhere so that they can be analyzed if
    necessary.

-   **Handling results**. The service instance handling a message is
    fully decoupled from the application logic that generates the
    message, and they might not be able to communicate directly. If the
    service instance generates results that must be passed back to the
    application logic, this information must be stored in a location
    that\'s accessible to both. In order to prevent the application
    logic from retrieving incomplete data the system must indicate when
    processing is complete.

    > If you\'re using Azure, a worker process can pass results back to
    > the application logic by using a dedicated message reply queue.
    > The application logic must be able to correlate these results with
    > the original message. This scenario is described in more detail in
    > the [Asynchronous Messaging
    > Primer](https://msdn.microsoft.com/library/dn589781.aspx).

-   **Scaling the messaging system**. In a large-scale solution, a
    single message queue could be overwhelmed by the number of messages
    and become a bottleneck in the system. In this situation, consider
    partitioning the messaging system to send messages from specific
    producers to a particular queue, or use load balancing to distribute
    messages across multiple message queues.

-   **Ensuring reliability of the messaging system**. A reliable
    messaging system is needed to guarantee that after the application
    enqueues a message it won\'t be lost. This is essential for ensuring
    that all messages are delivered at least once.

#### When to use this Pattern

Use this pattern when:

-   The workload for an application is divided into tasks that can run
    asynchronously.
-   Tasks are independent and can run in parallel.
-   The volume of work is highly variable, requiring a scalable
    solution.
-   The solution must provide high availability, and must be resilient
    if the processing for a task fails.

This pattern might not be useful when:

-   It\'s not easy to separate the application workload into discrete
    tasks, or there\'s a high degree of dependence between tasks.
-   Tasks must be performed synchronously, and the application logic
    must wait for a task to complete before continuing.
-   Tasks must be performed in a specific sequence.

> Some messaging systems support sessions that enable a producer to
> group messages together and ensure that they\'re all handled by the
> same consumer. This mechanism can be used with prioritized messages
> (if they are supported) to implement a form of message ordering that
> delivers messages in sequence from a producer to a single consumer.

### Compute Resource Consolidation Pattern

#### Overview

Consolidate multiple tasks or operations into a single computational
unit. This can increase compute resource utilization, and reduce the
costs and management overhead associated with performing compute
processing in cloud-hosted applications.

#### Context and Problem

A cloud application often implements a variety of operations. In some
solutions it makes sense to follow the design principle of separation of
concerns initially, and divide these operations into separate
computational units that are hosted and deployed individually (for
example, as separate App Service web apps, separate Virtual Machines, or
separate Cloud Service roles). However, although this strategy can help
simplify the logical design of the solution, deploying a large number of
computational units as part of the same application can increase runtime
hosting costs and make management of the system more complex.

As an example, the figure shows the simplified structure of a
cloud-hosted solution that is implemented using more than one
computational unit. Each computational unit runs in its own virtual
environment. Each function has been implemented as a separate task
(labeled Task A through Task E) running in its own computational unit.

<img src="./attachments/463533329.png" alt="">

Each computational unit consumes chargeable resources, even when it\'s
idle or lightly used. Therefore, this isn\'t always the most
cost-effective solution.

In Azure, this concern applies to roles in a Cloud Service, App
Services, and Virtual Machines. These items run in their own virtual
environment. Running a collection of separate roles, websites, or
virtual machines that are designed to perform a set of well-defined
operations, but that need to communicate and cooperate as part of a
single solution, can be an inefficient use of resources.

#### Solution

To help reduce costs, increase utilization, improve communication speed,
and reduce management it\'s possible to consolidate multiple tasks or
operations into a single computational unit.

Tasks can be grouped according to criteria based on the features
provided by the environment and the costs associated with these
features. A common approach is to look for tasks that have a similar
profile concerning their scalability, lifetime, and processing
requirements. Grouping these together allows them to scale as a unit.
The elasticity provided by many cloud environments enables additional
instances of a computational unit to be started and stopped according to
the workload. For example, Azure provides autoscaling that you can apply
to roles in a Cloud Service, App Services, and Virtual Machines. For
more information, see  [Autoscaling
Guidance](https://msdn.microsoft.com/library/dn589774.aspx).

As a counter example to show how scalability can be used to determine
which operations shouldn\'t be grouped together, consider the following
two tasks:

-   Task 1 polls for infrequent, time-insensitive messages sent to a
    queue.
-   Task 2 handles high-volume bursts of network traffic.

The second task requires elasticity that can involve starting and
stopping a large number of instances of the computational unit. Applying
the same scaling to the first task would simply result in more tasks
listening for infrequent messages on the same queue, and is a waste of
resources.

In many cloud environments it\'s possible to specify the resources
available to a computational unit in terms of the number of CPU cores,
memory, disk space, and so on. Generally, the more resources specified,
the greater the cost. To save money, it\'s important to maximize the
work an expensive computational unit performs, and not let it become
inactive for an extended period.

If there are tasks that require a great deal of CPU power in short
bursts, consider consolidating these into a single computational unit
that provides the necessary power. However, it\'s important to balance
this need to keep expensive resources busy against the contention that
could occur if they are over stressed. Long-running, compute-intensive
tasks shouldn\'t share the same computational unit, for example.

#### Issues and Considerations

Consider the following points when implementing this pattern:

**Scalability and elasticity**. Many cloud solutions implement
scalability and elasticity at the level of the computational unit by
starting and stopping instances of units. Avoid grouping tasks that have
conflicting scalability requirements in the same computational unit.

**Lifetime**. The cloud infrastructure periodically recycles the virtual
environment that hosts a computational unit. When there are many
long-running tasks inside a computational unit, it might be necessary to
configure the unit to prevent it from being recycled until these tasks
have finished. Alternatively, design the tasks by using a check-pointing
approach that enables them to stop cleanly, and continue at the point
they were interrupted when the computational unit is restarted.

**Release cadence**. If the implementation or configuration of a task
changes frequently, it might be necessary to stop the computational unit
hosting the updated code, reconfigure and redeploy the unit, and then
restart it. This process will also require that all other tasks within
the same computational unit are stopped, redeployed, and restarted.

**Security**. Tasks in the same computational unit might share the same
security context and be able to access the same resources. There must be
a high degree of trust between the tasks, and confidence that one task
isn\'t going to corrupt or adversely affect another. Additionally,
increasing the number of tasks running in a computational unit increases
the attack surface of the unit. Each task is only as secure as the one
with the most vulnerabilities.

**Fault tolerance**. If one task in a computational unit fails or
behaves abnormally, it can affect the other tasks running within the
same unit. For example, if one task fails to start correctly it can
cause the entire startup logic for the computational unit to fail, and
prevent other tasks in the same unit from running.

**Contention**. Avoid introducing contention between tasks that compete
for resources in the same computational unit. Ideally, tasks that share
the same computational unit should exhibit different resource
utilization characteristics. For example, two compute-intensive tasks
should probably not reside in the same computational unit, and neither
should two tasks that consume large amounts of memory. However, mixing a
compute-intensive task with a task that requires a large amount of
memory is a workable combination.

> Consider consolidating compute resources only for a system that\'s
> been in production for a period of time so that operators and
> developers can monitor the system and create a  *heat map* that
> identifies how each task uses differing resources. This map can be
> used to determine which tasks are good candidates for sharing compute
> resources.

**Complexity**. Combining multiple tasks into a single computational
unit adds complexity to the code in the unit, possibly making it more
difficult to test, debug, and maintain.

**Stable logical architecture**. Design and implement the code in each
task so that it shouldn\'t need to change, even if the physical
environment the task runs in does change.

**Other strategies**. Consolidating compute resources is only one way to
help reduce costs associated with running multiple tasks concurrently.
It requires careful planning and monitoring to ensure that it remains an
effective approach. Other strategies might be more appropriate,
depending on the nature of the work and where the users these tasks are
running are located. For example, functional decomposition of the
workload (as described by the  [Compute Partitioning
Guidance](https://msdn.microsoft.com/library/dn589773.aspx))
might be a better option.

#### When to use this Pattern

Use this pattern for tasks that are not cost effective if they run in
their own computational units. If a task spends much of its time idle,
running this task in a dedicated unit can be expensive.

This pattern might not be suitable for tasks that perform critical
fault-tolerant operations, or tasks that process highly sensitive or
private data and require their own security context. These tasks should
run in their own isolated environment, in a separate computational unit.

### Event Sourcing Pattern

#### Overview

Instead of storing just the current state of the data in a domain, use
an append-only store to record the full series of actions taken on that
data. The store acts as the system of record and can be used to
materialize the domain objects. This can simplify tasks in complex
domains, by avoiding the need to synchronize the data model and the
business domain, while improving performance, scalability, and
responsiveness. It can also provide consistency for transactional data,
and maintain full audit trails and history that can enable compensating
actions.

#### Context and Problem

Most applications work with data, and the typical approach is for the
application to maintain the current state of the data by updating it as
users work with it. For example, in the traditional create, read,
update, and delete (CRUD) model a typical data process is to read data
from the store, make some modifications to it, and update the current
state of the data with the new values---often by using transactions that
lock the data.

The CRUD approach has some limitations:

-   CRUD systems perform update operations directly against a data
    store, which can slow down performance and responsiveness, and limit
    scalability, due to the processing overhead it requires.

-   In a collaborative domain with many concurrent users, data update
    conflicts are more likely because the update operations take place
    on a single item of data.

-   Unless there\'s an additional auditing mechanism that records the
    details of each operation in a separate log, history is lost.

> For a deeper understanding of the limits of the CRUD approach, see 
> [CRUD, Only When You Can Afford
> It](https://blogs.msdn.microsoft.com/maarten_mullender/2004/07/23/crud-only-when-you-can-afford-it-revisited/).

#### Solution

The Event Sourcing pattern defines an approach to handling operations on
data that\'s driven by a sequence of events, each of which is recorded
in an append-only store. Application code sends a series of events that
imperatively describe each action that has occurred on the data to the
event store, where they\'re persisted. Each event represents a set of
changes to the data (such as  `AddedItemToOrder`).

The events are persisted in an event store that acts as the system of
record (the authoritative data source) about the current state of the
data. The event store typically publishes these events so that consumers
can be notified and can handle them if needed. Consumers could, for
example, initiate tasks that apply the operations in the events to other
systems, or perform any other associated action that\'s required to
complete the operation. Notice that the application code that generates
the events is decoupled from the systems that subscribe to the events.

Typical uses of the events published by the event store are to maintain
materialized views of entities as actions in the application change
them, and for integration with external systems. For example, a system
can maintain a materialized view of all customer orders that\'s used to
populate parts of the UI. As the application adds new orders, adds or
removes items on the order, and adds shipping information, the events
that describe these changes can be handled and used to update the 
[materialized
view](https://docs.microsoft.com/en-us/azure/architecture/patterns/materialized-view).

In addition, at any point it\'s possible for applications to read the
history of events, and use it to materialize the current state of an
entity by playing back and consuming all the events related to that
entity. This can occur on demand to materialize a domain object when
handling a request, or through a scheduled task so that the state of the
entity can be stored as a materialized view to support the presentation
layer.

The figure shows an overview of the pattern, including some of the
options for using the event stream such as creating a materialized view,
integrating events with external applications and systems, and replaying
events to create projections of the current state of specific entities.

<img src="./attachments/463533331.png" alt="">

The Event Sourcing pattern provides the following advantages:

-   Events are immutable and can be stored using an append-only
    operation. The user interface, workflow, or process that initiated
    an event can continue, and tasks that handle the events can run in
    the background. This, combined with the fact that there\'s no
    contention during the processing of transactions, can vastly improve
    performance and scalability for applications, especially for the
    presentation level or user interface.

-   Events are simple objects that describe some action that occurred,
    together with any associated data required to describe the action
    represented by the event. Events don\'t directly update a data
    store. They\'re simply recorded for handling at the appropriate
    time. This can simplify implementation and management.

-   Events typically have meaning for a domain expert, whereas 
    [object-relational impedance
    mismatch](https://en.wikipedia.org/wiki/Object-relational_impedance_mismatch) can
    make complex database tables hard to understand. Tables are
    artificial constructs that represent the current state of the
    system, not the events that occurred.

-   Event sourcing can help prevent concurrent updates from causing
    conflicts because it avoids the requirement to directly update
    objects in the data store. However, the domain model must still be
    designed to protect itself from requests that might result in an
    inconsistent state.

-   The append-only storage of events provides an audit trail that can
    be used to monitor actions taken against a data store, regenerate
    the current state as materialized views or projections by replaying
    the events at any time, and assist in testing and debugging the
    system. In addition, the requirement to use compensating events to
    cancel changes provides a history of changes that were reversed,
    which wouldn\'t be the case if the model simply stored the current
    state. The list of events can also be used to analyze application
    performance and detect user behavior trends, or to obtain other
    useful business information.

-   The event store raises events, and tasks perform operations in
    response to those events. This decoupling of the tasks from the
    events provides flexibility and extensibility. Tasks know about the
    type of event and the event data, but not about the operation that
    triggered the event. In addition, multiple tasks can handle each
    event. This enables easy integration with other services and systems
    that only listen for new events raised by the event store. However,
    the event sourcing events tend to be very low level, and it might be
    necessary to generate specific integration events instead.

> Event sourcing is commonly combined with the CQRS pattern by
> performing the data management tasks in response to the events, and by
> materializing views from the stored events.

#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

The system will only be eventually consistent when creating materialized
views or generating projections of data by replaying events. There\'s
some delay between an application adding events to the event store as
the result of handling a request, the events being published, and
consumers of the events handling them. During this period, new events
that describe further changes to entities might have arrived at the
event store.

> See the  [Data Consistency Primer](https://msdn.microsoft.com/library/dn589800.aspx) for information about eventual consistency.

The event store is the permanent source of information, and so the event
data should never be updated. The only way to update an entity to undo a
change is to add a compensating event to the event store. If the format
(rather than the data) of the persisted events needs to change, perhaps
during a migration, it can be difficult to combine existing events in
the store with the new version. It might be necessary to iterate through
all the events making changes so they\'re compliant with the new format,
or add new events that use the new format. Consider using a version
stamp on each version of the event schema to maintain both the old and
the new event formats.

Multi-threaded applications and multiple instances of applications might
be storing events in the event store. The consistency of events in the
event store is vital, as is the order of events that affect a specific
entity (the order that changes occur to an entity affects its current
state). Adding a timestamp to every event can help to avoid issues.
Another common practice is to annotate each event resulting from a
request with an incremental identifier. If two actions attempt to add
events for the same entity at the same time, the event store can reject
an event that matches an existing entity identifier and event
identifier.

There\'s no standard approach, or existing mechanisms such as SQL
queries, for reading the events to obtain information. The only data
that can be extracted is a stream of events using an event identifier as
the criteria. The event ID typically maps to individual entities. The
current state of an entity can be determined only by replaying all of
the events that relate to it against the original state of that entity.

The length of each event stream affects managing and updating the
system. If the streams are large, consider creating snapshots at
specific intervals such as a specified number of events. The current
state of the entity can be obtained from the snapshot and by replaying
any events that occurred after that point in time. For more information
about creating snapshots of data, see  [Snapshot on Martin Fowler's Enterprise Application Architecture website](https://martinfowler.com/eaaDev/Snapshot.html) and 
[Master-Subordinate Snapshot Replication](https://msdn.microsoft.com/library/ff650012.aspx).

Even though event sourcing minimizes the chance of conflicting updates
to the data, the application must still be able to deal with
inconsistencies that result from eventual consistency and the lack of
transactions. For example, an event that indicates a reduction in stock
inventory might arrive in the data store while an order for that item is
being placed, resulting in a requirement to reconcile the two operations
either by advising the customer or creating a back order.

Event publication might be \"at least once,\" and so consumers of the
events must be idempotent. They must not reapply the update described in
an event if the event is handled more than once. For example, if
multiple instances of a consumer maintain an aggregate an entity\'s
property, such as the total number of orders placed, only one must
succeed in incrementing the aggregate when an order placed event occurs.
While this isn\'t a key characteristic of event sourcing, it\'s the
usual implementation decision.

#### When to use this Pattern

Use this pattern in the following scenarios:

-   When you want to capture intent, purpose, or reason in the data. For
    example, changes to a customer entity can be captured as a series of
    specific event types such as  *Moved home*,  *Closed account*, or 
    *Deceased*.

-   When it\'s vital to minimize or completely avoid the occurrence of
    conflicting updates to data.

-   When you want to record events that occur, and be able to replay
    them to restore the state of a system, roll back changes, or keep a
    history and audit log. For example, when a task involves multiple
    steps you might need to execute actions to revert updates and then
    replay some steps to bring the data back into a consistent state.

-   When using events is a natural feature of the operation of the
    application, and requires little additional development or
    implementation effort.

-   When you need to decouple the process of inputting or updating data
    from the tasks required to apply these actions. This might be to
    improve UI performance, or to distribute events to other listeners
    that take action when the events occur. For example, integrating a
    payroll system with an expense submission website so that events
    raised by the event store in response to data updates made in the
    website are consumed by both the website and the payroll system.

-   When you want flexibility to be able to change the format of
    materialized models and entity data if requirements change,
    or---when used in conjunction with CQRS---you need to adapt a read
    model or the views that expose the data.

-   When used in conjunction with CQRS, and eventual consistency is
    acceptable while a read model is updated, or the performance impact
    of rehydrating entities and data from an event stream is acceptable.

This pattern might not be useful in the following situations:

-   Small or simple domains, systems that have little or no business
    logic, or nondomain systems that naturally work well with
    traditional CRUD data management mechanisms.

-   Systems where consistency and real-time updates to the views of the
    data are required.

-   Systems where audit trails, history, and capabilities to roll back
    and replay actions are not required.

-   Systems where there\'s only a very low occurrence of conflicting
    updates to the underlying data. For example, systems that
    predominantly add data rather than updating it.

### External Configuration Store Pattern

#### Overview

Move configuration information out of the application deployment package
to a centralized location. This can provide opportunities for easier
management and control of configuration data, and for sharing
configuration data across applications and application instances.

#### Context and Problem

The majority of application runtime environments include configuration
information that\'s held in files deployed with the application. In some
cases, it\'s possible to edit these files to change the application
behavior after it\'s been deployed. However, changes to the
configuration require the application be redeployed, often resulting in
unacceptable downtime and other administrative overhead.

Local configuration files also limit the configuration to a single
application, but sometimes it would be useful to share configuration
settings across multiple applications. Examples include database
connection strings, UI theme information, or the URLs of queues and
storage used by a related set of applications.

It\'s challenging to manage changes to local configurations across
multiple running instances of the application, especially in a
cloud-hosted scenario. It can result in instances using different
configuration settings while the update is being deployed.

In addition, updates to applications and components might require
changes to configuration schemas. Many configuration systems don\'t
support different versions of configuration information.

#### Solution

Store the configuration information in external storage, and provide an
interface that can be used to quickly and efficiently read and update
configuration settings. The type of external store depends on the
hosting and runtime environment of the application. In a cloud-hosted
scenario it\'s typically a cloud-based storage service, but could be a
hosted database or other system.

The backing store you choose for configuration information should have
an interface that provides consistent and easy-to-use access. It should
expose the information in a correctly typed and structured format. The
implementation might also need to authorize users' access in order to
protect configuration data, and be flexible enough to allow storage of
multiple versions of the configuration (such as development, staging, or
production, including multiple release versions of each one).

> Many built-in configuration systems read the data when the application
> starts up, and cache the data in memory to provide fast access and
> minimize the impact on application performance. Depending on the type
> of backing store used, and the latency of this store, it might be
> helpful to implement a caching mechanism within the external
> configuration store. For more information, see the [Caching
> Guidance](https://msdn.microsoft.com/library/dn589802.aspx).
> The figure illustrates an overview of the External Configuration Store
> pattern with optional local cache.

<img src="./attachments/463533333.png" alt="">

#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

Choose a backing store that offers acceptable performance, high
availability, robustness, and can be backed up as part of the
application maintenance and administration process. In a cloud-hosted
application, using a cloud storage mechanism is usually a good choice to
meet these requirements.

Design the schema of the backing store to allow flexibility in the types
of information it can hold. Ensure that it provides for all
configuration requirements such as typed data, collections of settings,
multiple versions of settings, and any other features that the
applications using it require. The schema should be easy to extend to
support additional settings as requirements change.

Consider the physical capabilities of the backing store, how it relates
to the way configuration information is stored, and the effects on
performance. For example, storing an XML document containing
configuration information will require either the configuration
interface or the application to parse the document in order to read
individual settings. It\'ll make updating a setting more complicated,
though caching the settings can help to offset slower read performance.

Consider how the configuration interface will permit control of the
scope and inheritance of configuration settings. For example, it might
be a requirement to scope configuration settings at the organization,
application, and the machine level. It might need to support delegation
of control over access to different scopes, and to prevent or allow
individual applications to override settings.

Ensure that the configuration interface can expose the configuration
data in the required formats such as typed values, collections,
key/value pairs, or property bags.

Consider how the configuration store interface will behave when settings
contain errors, or don\'t exist in the backing store. It might be
appropriate to return default settings and log errors. Also consider
aspects such as the case sensitivity of configuration setting keys or
names, the storage and handling of binary data, and the ways that null
or empty values are handled.

Consider how to protect the configuration data to allow access to only
the appropriate users and applications. This is likely a feature of the
configuration store interface, but it\'s also necessary to ensure that
the data in the backing store can\'t be accessed directly without the
appropriate permission. Ensure strict separation between the permissions
required to read and to write configuration data. Also consider whether
you need to encrypt some or all of the configuration settings, and how
this\'ll be implemented in the configuration store interface.

Centrally stored configurations, which change application behavior
during runtime, are critically important and should be deployed,
updated, and managed using the same mechanisms as deploying application
code. For example, changes that can affect more than one application
must be carried out using a full test and staged deployment approach to
ensure that the change is appropriate for all applications that use this
configuration. If an administrator edits a setting to update one
application, it could adversely impact other applications that use the
same setting.

If an application caches configuration information, the application
needs to be alerted if the configuration changes. It might be possible
to implement an expiration policy over cached configuration data so that
this information is automatically refreshed periodically and any changes
picked up (and acted on).

#### When to use this Pattern

This pattern is useful for:

-   Configuration settings that are shared between multiple applications
    and application instances, or where a standard configuration must be
    enforced across multiple applications and application instances.

-   A standard configuration system that doesn\'t support all of the
    required configuration settings, such as storing images or complex
    data types.

-   As a complementary store for some of the settings for applications,
    perhaps allowing applications to override some or all of the
    centrally-stored settings.

-   As a way to simplify administration of multiple applications, and
    optionally for monitoring use of configuration settings by logging
    some or all types of access to the configuration store.

### Federated Identity Pattern

#### Overview

Delegate authentication to an external identity provider. This can
simplify development, minimize the requirement for user administration,
and improve the user experience of the application.

#### Context and Problem

Users typically need to work with multiple applications provided and
hosted by different organizations they have a business relationship
with. These users might be required to use specific (and different)
credentials for each one. This can:

-   **Cause a disjointed user experience**. Users often forget sign-in
    credentials when they have many different ones.

-   **Expose security vulnerabilities**. When a user leaves the company
    the account must immediately be deprovisioned. It\'s easy to
    overlook this in large organizations.

-   **Complicate user management**. Administrators must manage
    credentials for all of the users, and perform additional tasks such
    as providing password reminders.

Users typically prefer to use the same credentials for all these
applications.

#### Solution

Implement an authentication mechanism that can use federated identity.
Separate user authentication from the application code, and delegate
authentication to a trusted identity provider. This can simplify
development and allow users to authenticate using a wider range of
identity providers (IdP) while minimizing the administrative overhead.
It also allows you to clearly decouple authentication from
authorization.

The trusted identity providers include corporate directories,
on-premises federation services, other security token services (STS)
provided by business partners, or social identity providers that can
authenticate users who have, for example, a Microsoft, Google, Yahoo!,
or Facebook account.

The figure illustrates the Federated Identity pattern when a client
application needs to access a service that requires authentication. The
authentication is performed by an IdP that works in concert with an STS.
The IdP issues security tokens that provide information about the
authenticated user. This information, referred to as claims, includes
the user's identity, and might also include other information such as
role membership and more granular access rights.

<img src="./attachments/463533335.png" alt="">

This model is often called claims-based access control. Applications and
services authorize access to features and functionality based on the
claims contained in the token. The service that requires authentication
must trust the IdP. The client application contacts the IdP that
performs the authentication. If the authentication is successful, the
IdP returns a token containing the claims that identify the user to the
STS (note that the IdP and STS can be the same service). The STS can
transform and augment the claims in the token based on predefined rules,
before returning it to the client. The client application can then pass
this token to the service as proof of its identity.

> There might be additional STSs in the chain of trust. For example, in
> the scenario described later, an on-premises STS trusts another STS
> that is responsible for accessing an identity provider to authenticate
> the user. This approach is common in enterprise scenarios where
> there\'s an on-premises STS and directory.

Federated authentication provides a standards-based solution to the
issue of trusting identities across diverse domains, and can support
single sign-on. It\'s becoming more common across all types of
applications, especially cloud-hosted applications, because it supports
single sign-on without requiring a direct network connection to identity
providers. The user doesn\'t have to enter credentials for every
application. This increases security because it prevents the creation of
credentials required to access many different applications, and it also
hides the user's credentials from all but the original identity
provider. Applications see just the authenticated identity information
contained within the token.

Federated identity also has the major advantage that management of the
identity and credentials is the responsibility of the identity provider.
The application or service doesn\'t need to provide identity management
features. In addition, in corporate scenarios, the corporate directory
doesn\'t need to know about the user if it trusts the identity provider.
This removes all the administrative overhead of managing the user
identity within the directory.

#### Issues and Considerations

Consider the following when designing applications that implement
federated authentication:

-   Authentication can be a single point of failure. If you deploy your
    application to multiple datacenters, consider deploying your
    identity management mechanism to the same datacenters to maintain
    application reliability and availability.

-   Authentication tools make it possible to configure access control
    based on role claims contained in the authentication token. This is
    often referred to as role-based access control (RBAC), and it can
    allow a more granular level of control over access to features and
    resources.

-   Unlike a corporate directory, claims-based authentication using
    social identity providers doesn\'t usually provide information about
    the authenticated user other than an email address, and perhaps a
    name. Some social identity providers, such as a Microsoft account,
    provide only a unique identifier. The application usually needs to
    maintain some information on registered users, and be able to match
    this information to the identifier contained in the claims in the
    token. Typically this is done through registration when the user
    first accesses the application, and information is then injected
    into the token as additional claims after each authentication.

-   If there\'s more than one identity provider configured for the STS,
    it must detect which identity provider the user should be redirected
    to for authentication. This process is called home realm discovery.
    The STS might be able to do this automatically based on an email
    address or user name that the user provides, a subdomain of the
    application that the user is accessing, the user's IP address scope,
    or on the contents of a cookie stored in the user's browser. For
    example, if the user entered an email address in the Microsoft
    domain, such as <user@live.com>, the STS will redirect the user to
    the Microsoft account sign-in page. On later visits, the STS could
    use a cookie to indicate that the last sign in was with a Microsoft
    account. If automatic discovery can\'t determine the home realm, the
    STS will display a home realm discovery page that lists the trusted
    identity providers, and the user must select the one they want to
    use.

#### When to use this Pattern

This pattern is useful for scenarios such as:

-   **Single sign-on in the enterprise**. In this scenario you need to
    authenticate employees for corporate applications that are hosted in
    the cloud outside the corporate security boundary, without requiring
    them to sign in every time they visit an application. The user
    experience is the same as when using on-premises applications where
    they\'re authenticated when signing in to a corporate network, and
    from then on have access to all relevant applications without
    needing to sign in again.

-   **Federated identity with multiple partners**. In this scenario you
    need to authenticate both corporate employees and business partners
    who don\'t have accounts in the corporate directory. This is common
    in business-to-business applications, applications that integrate
    with third-party services, and where companies with different IT
    systems have merged or shared resources.

-   **Federated identity in SaaS applications**. In this scenario
    independent software vendors provide a ready-to-use service for
    multiple clients or tenants. Each tenant authenticates using a
    suitable identity provider. For example, business users will use
    their corporate credentials, while consumers and clients of the
    tenant will use their social identity credentials.

This pattern might not be useful in the following situations:

-   All users of the application can be authenticated by one identity
    provider, and there\'s no requirement to authenticate using any
    other identity provider. This is typical in business applications
    that use a corporate directory (accessible within the application)
    for authentication, by using a VPN, or (in a cloud-hosted scenario)
    through a virtual network connection between the on-premises
    directory and the application.

-   The application was originally built using a different
    authentication mechanism, perhaps with custom user stores, or
    doesn\'t have the capability to handle the negotiation standards
    used by claims-based technologies. Retrofitting claims-based
    authentication and access control into existing applications can be
    complex, and probably not cost effective.

### Gatekeeper Pattern

#### Overview

Protect applications and services by using a dedicated host instance
that acts as a broker between clients and the application or service,
validates and sanitizes requests, and passes requests and data between
them. This can provide an additional layer of security, and limit the
attack surface of the system.

#### Context and Problem

Applications expose their functionality to clients by accepting and
processing requests. In cloud-hosted scenarios, applications expose
endpoints clients connect to, and typically include the code to handle
the requests from clients. This code performs authentication and
validation, some or all request processing, and is likely to accesses
storage and other services on behalf of the client.

If a malicious user is able to compromise the system and gain access to
the application's hosting environment, the security mechanisms it uses
such as credentials and storage keys, and the services and data it
accesses, are exposed. As a result, the malicious user can gain
unrestrained access to sensitive information and other services.

#### Solution

To minimize the risk of clients gaining access to sensitive information
and services, decouple hosts or tasks that expose public endpoints from
the code that processes requests and accesses storage. You can achieve
this by using a façade or a dedicated task that interacts with clients
and then hands off the request---perhaps through a decoupled
interface---to the hosts or tasks that\'ll handle the request. The
figure provides a high-level overview of this pattern.

<img src="./attachments/463533346.png" alt="">

The gatekeeper pattern can be used to simply protect storage, or it can
be used as a more comprehensive façade to protect all of the functions
of the application. The important factors are:

-   **Controlled validation**. The gatekeeper validates all requests,
    and rejects those that don\'t meet validation requirements.
-   **Limited risk and exposure**. The gatekeeper doesn\'t have access
    to the credentials or keys used by the trusted host to access
    storage and services. If the gatekeeper is compromised, the attacker
    doesn\'t get access to these credentials or keys.
-   **Appropriate security**. The gatekeeper runs in a limited privilege
    mode, while the rest of the application runs in the full trust mode
    required to access storage and services. If the gatekeeper is
    compromised, it can\'t directly access the application services or
    data.

This pattern acts like a firewall in a typical network topography. It
allows the gatekeeper to examine requests and make a decision about
whether to pass the request on to the trusted host (sometimes called the
keymaster) that performs the required tasks. This decision typically
requires the gatekeeper to validate and sanitize the request content
before passing it on to the trusted host.

#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

-   Ensure that the trusted hosts the gatekeeper passes requests to
    expose only internal or protected endpoints, and connect only to the
    gatekeeper. The trusted hosts shouldn\'t expose any external
    endpoints or interfaces.
-   The gatekeeper must run in a limited privilege mode. Typically this
    means running the gatekeeper and the trusted host in separate hosted
    services or virtual machines.
-   The gatekeeper shouldn\'t perform any processing related to the
    application or services, or access any data. Its function is purely
    to validate and sanitize requests. The trusted hosts might need to
    perform additional validation of requests, but the core validation
    should be performed by the gatekeeper.
-   Use a secure communication channel (HTTPS, SSL, or TLS) between the
    gatekeeper and the trusted hosts or tasks where this is possible.
    However, some hosting environments don\'t support HTTPS on internal
    endpoints.
-   Adding the extra layer to the application to implement the
    gatekeeper pattern is likely to have some impact on performance due
    to the additional processing and network communication it requires.
-   The gatekeeper instance could be a single point of failure. To
    minimize the impact of a failure, consider deploying additional
    instances and using an autoscaling mechanism to ensure capacity to
    maintain availability.

#### When to use this Pattern

This pattern is useful for:

-   Applications that handle sensitive information, expose services that
    must have a high degree of protection from malicious attacks, or
    perform mission-critical operations that shouldn\'t be disrupted.
-   Distributed applications where it\'s necessary to perform request
    validation separately from the main tasks, or to centralize this
    validation to simplify maintenance and administration.

### Gateway Aggregation Pattern

#### Overview

Use a gateway to aggregate multiple individual requests into a single
request. This pattern is useful when a client must make multiple calls
to different backend systems to perform an operation.

#### Context and Problem

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

<img src="./attachments/463533348.png" alt="">

#### Solution

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

<img src="./attachments/463533349.png" alt="">
![New-API-GW-Diagram](https://d1.awsstatic.com/serverless/New-API-GW-Diagram.c9fc9835d2a9aa00ef90d0ddc4c6402a2536de0d.png)
![](https://microservices.io/i/apigateway.jpg)
<img src="./attachments/463533529.png" alt="">
<img src="./attachments/463533530.png" alt="">

![](https://microservices.io/i/bffe.png)


#### Using an API gateway has the following benefits

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

#### Issues and Considerations

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
    [circuit breaking](https://docs.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker), 
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

#### When to use this Pattern

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

### Gateway Offloading Pattern

#### Overview

Offload shared or specialized service functionality to a gateway proxy.
This pattern can simplify application development by moving shared
service functionality, such as the use of SSL certificates, from other
parts of the application into the gateway.

#### Context and Problem

Some features are commonly used across multiple services, and these
features require configuration, management, and maintenance. A shared or
specialized service that is distributed with every application
deployment increases the administrative overhead and increases the
likelihood of deployment error. Any updates to a shared feature must be
deployed across all services that share that feature.

Properly handling security issues (token validation, encryption, SSL
certificate management) and other complex tasks can require team members
to have highly specialized skills. For example, a certificate needed by
an application must be configured and deployed on all application
instances. With each new deployment, the certificate must be managed to
ensure that it does not expire. Any common certificate that is due to
expire must be updated, tested, and verified on every application
deployment.

Other common services such as authentication, authorization, logging,
monitoring, or 
[throttling](https://docs.microsoft.com/en-us/azure/architecture/patterns/throttling) can
be difficult to implement and manage across a large number of
deployments. It may be better to consolidate this type of functionality,
in order to reduce overhead and the chance of errors.

#### Solution

Offload some features into an API gateway, particularly cross-cutting
concerns such as certificate management, authentication, SSL
termination, monitoring, protocol translation, or throttling.

The following diagram shows an API gateway that terminates inbound SSL
connections. It requests data on behalf of the original requestor from
any HTTP server upstream of the API gateway.

<img src="./attachments/463533351.png" alt="">

Benefits of this pattern include:

-   Simplify the development of services by removing the need to
    distribute and maintain supporting resources, such as web server
    certificates and configuration for secure websites. Simpler
    configuration results in easier management and scalability and makes
    service upgrades simpler.

-   Allow dedicated teams to implement features that require specialized
    expertise, such as security. This allows your core team to focus on
    the application functionality, leaving these specialized but
    cross-cutting concerns to the relevant experts.

-   Provide some consistency for request and response logging and
    monitoring. Even if a service is not correctly instrumented, the
    gateway can be configured to ensure a minimum level of monitoring
    and logging.

#### Issues and Considerations

-   Ensure the API gateway is highly available and resilient to failure.
    Avoid single points of failure by running multiple instances of your
    API gateway.
-   Ensure the gateway is designed for the capacity and scaling
    requirements of your application and endpoints. Make sure the
    gateway does not become a bottleneck for the application and is
    sufficiently scalable.
-   Only offload features that are used by the entire application, such
    as security or data transfer.
-   Business logic should never be offloaded to the API gateway.
-   If you need to track transactions, consider generating correlation
    IDs for logging purposes.

#### When to use this Pattern


Use this pattern when:

-   An application deployment has a shared concern such as SSL
    certificates or encryption.
-   A feature that is common across application deployments that may
    have different resource requirements, such as memory resources,
    storage capacity or network connections.
-   You wish to move the responsibility for issues such as network
    security, throttling, or other network boundary concerns to a more
    specialized team.

This pattern may not be suitable if it introduces coupling across
services.

### Gateway Routing Pattern

#### Overview

Route requests to multiple services using a single endpoint. This
pattern is useful when you wish to expose multiple services on a single
endpoint and route to the appropriate service based on the request.

#### Context and Problem

When a client needs to consume multiple services, setting up a separate
endpoint for each service and having the client manage each endpoint can
be challenging. For example, an e-commerce application might provide
services such as search, reviews, cart, checkout, and order history.
Each service has a different API that the client must interact with, and
the client must know about each endpoint in order to connect to the
services. If an API changes, the client must be updated as well. If you
refactor a service into two or more separate services, the code must
change in both the service and the client.

#### Solution

Place a gateway in front of a set of applications, services, or
deployments. Use application Layer 7 routing to route the request to the
appropriate instances.

With this pattern, the client application only needs to know about and
communicate with a single endpoint. If a service is consolidated or
decomposed, the client does not necessarily require updating. It can
continue making requests to the gateway, and only the routing changes.

A gateway also lets you abstract backend services from the clients,
allowing you to keep client calls simple while enabling changes in the
backend services behind the gateway. Client calls can be routed to
whatever service or services need to handle the expected client
behavior, allowing you to add, split, and reorganize services behind the
gateway without changing the client.

<img src="./attachments/463533353.png" alt="">

This pattern can also help with deployment, by allowing you to manage
how updates are rolled out to users. When a new version of your service
is deployed, it can be deployed in parallel with the existing version.
Routing lets you control what version of the service is presented to the
clients, giving you the flexibility to use various release strategies,
whether incremental, parallel, or complete rollouts of updates. Any
issues discovered after the new service is deployed can be quickly
reverted by making a configuration change at the gateway, without
affecting clients.

#### Issues and Considerations

-   The gateway service may introduce a single point of failure. Ensure
    it is properly designed to meet your availability requirements.
    Consider resiliency and fault tolerance capabilities when
    implementing.
-   The gateway service may introduce a bottleneck. Ensure the gateway
    has adequate performance to handle load and can easily scale in line
    with your growth expectations.
-   Perform load testing against the gateway to ensure you don\'t
    introduce cascading failures for services.
-   Gateway routing is level 7. It can be based on IP, port, header, or
    URL.

#### When to use this Pattern

Use this pattern when:

-   A client needs to consume multiple services that can be accessed
    behind a gateway.
-   You wish to simplify client applications by using a single endpoint.
-   You need to route requests from externally addressable endpoints to
    internal virtual endpoints, such as exposing ports on a VM to
    cluster virtual IP addresses.

This pattern may not be suitable when you have a simple application that
uses only one or two services.

### Geodes

#### Overview

The geode pattern involves deploying a collection of backend services
into a set of  **ge**ographical n **ode**s, each of which can service
any request for any client in any region. This pattern allows serving
requests in an  *active-active* style, improving latency and increasing
availability by distributing request processing around the globe.

<img src="./attachments/463533355.png" alt="">

#### Context and Problem

Many large-scale services have specific challenges around
geo-availability and scale. Classic designs often  *bring the data to
the compute* by storing data in a remote SQL server that serves as the
compute tier for that data, relying on scale-up for growth.

The classic approach may present a number of challenges:

-   Network latency issues for users coming from the other side of the
    globe to connect to the hosting endpoint
-   Traffic management for demand bursts that can overwhelm the services
    in a single region
-   Cost-prohibitive complexity of deploying copies of app
    infrastructure into multiple regions for a 24x7 service

Modern cloud infrastructure has evolved to enable geographic load
balancing of front-end services, while allowing for geographic
replication of backend services. For availability and performance,
getting data closer to the user is good. When data is geo-distributed
across a far-flung user base, the geo-distributed datastores should also
be colocated with the compute resources that process the data. The geode
pattern  *brings the compute to the data*.

#### Solution

Deploy the service into a number of satellite deployments spread around
the globe, each of which is called a  *geode*. The geode pattern
harnesses key features of Azure to route traffic via the shortest path
to a nearby geode, which improves latency and performance.  Each geode
is behind a global load balancer, and uses a geo-replicated read-write
service to host the data plane, ensuring cross-geode data consistency.
Data replication services ensure that data stores are identical across
geodes, so  *all* requests can be served from  *all* geodes.

The key difference between a deployment stamp and a geode is that geodes
never exist in isolation. There should always be more than one geode in
a production platform.

<img src="./attachments/463533356.png" alt="">

Geodes have the following characteristics:

-   Consist of a collection of disparate types of resources, often
    defined in a template.
-   Have no dependencies outside of the geode footprint and are
    self-contained. No geode is dependent on another to operate, and if
    one dies, the others continue to operate.
-   Are loosely coupled via an edge network and replication backplane.
    For example, you can use  [Azure Traffic Manager](https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview) or 
    [Azure Front Door](https://docs.microsoft.com/en-us/azure/frontdoor/front-door-overview) for
    fronting the geodes, while Azure Cosmos DB can act as the
    replication backplane. Geodes are not the same as clusters because
    they share a replication backplane, so the platform takes care of
    quorum issues.

The geode pattern occurs in big data architectures that use commodity
hardware to process data colocated on the same machine, and MapReduce to
consolidate results across machines. Another usage is near-edge compute,
which brings compute closer to the intelligent edge of the network to
reduce response time.

Services can use this pattern over dozens or hundreds of geodes.
Furthermore, the resiliency of the whole solution increases with each
added geode, since any geodes can take over if a regional outage takes
one or more geodes offline.

It\'s also possible to augment local availability techniques, such as
availability zones or paired regions, with the geode pattern for global
availability. This increases complexity, but is useful if your
architecture is underpinned by a storage engine such as blob storage
that can only replicate to a paired region. You can deploy geodes into
an intra-zone, zonal, or regional footprint, with a mind to regulatory
or latency constraints on location.

#### Issues and Considerations

Use the following techniques and technologies to implement this pattern:

-   Modern DevOps practices and tools to produce and rapidly deploy
    identical geodes across a large number of regions or instances.
-   Autoscaling to scale out compute and database throughput instances
    within a geode. Each geode individually scales out, within the
    common backplane constraints.
-   A front-end service like Azure Front Door that does dynamic content
    acceleration, split TCP, and Anycast routing.
-   A replicating data store like Azure Cosmos DB to control data
    consistency.
-   Serverless technologies where possible, to reduce always-on
    deployment cost, especially when load is frequently rebalanced
    around the globe. This strategy allows for many geodes to be
    deployed with minimal additional investment. Serverless and
    consumption-based billing technologies reduce waste and cost from
    duplicate geo-distributed deployments.

Consider the following points when deciding how to implement this pattern:

-   Choose whether to process data locally in each region, or to
    distribute aggregations in a single geode and replicate the result
    across the globe. The  [Azure Cosmos DB change feed
    processor](https://docs.microsoft.com/en-us/azure/cosmos-db/change-feed-processor) offers
    this granular control using its  *lease container* concept, and the 
    *leasecollectionprefix* in the corresponding  [Azure Functions
    binding](https://docs.microsoft.com/en-us/azure/cosmos-db/change-feed-functions).
    Each approach has distinct advantages and drawbacks.
-   Geodes can work in tandem, using the Azure Cosmos DB change feed and
    a real-time communication platform like SignalR. Geodes can
    communicate with remote users via other geodes in a mesh pattern,
    without knowing or caring where the remote user is located.
-   This design pattern implicitly decouples everything, resulting in an
    ultra-highly distributed and decoupled architecture. Decoupling is a
    good thing, but consider how to track different components of the
    same request as they might execute asynchronously on different
    instances. Get a good monitoring strategy in place.

#### When to use this Pattern

Use this pattern:

-   To implement a high-scale platform that has users distributed over a
    wide area.
-   For any service that requires extreme availability and resilience
    characteristics, because services based on the geode pattern can
    survive the loss of multiple service regions at the same time.

This pattern might not be suitable for

-   Architectures that have constraints so that all geodes can\'t be
    equal for data storage. For example, there may be data residency
    requirements, an application that needs to maintain temporary state
    for a particular session, or a heavy weighting of requests towards a
    single region. In this case, consider using deployment stamps in
    combination with a global routing plane that is aware of where a
    user's data sits.
-   Situations where there\'s no geographical distribution required.
    Instead, consider availability zones and paired regions for
    clustering.
-   Situations where a legacy platform needs to be retrofitted. This
    pattern works for cloud-native development only, and can be
    difficult to retrofit.
-   Simple architectures and requirements, where geo-redundancy and
    geo-distribution aren\'t required or advantageous.

### Health Endpoint Monitoring Pattern

#### Overview

Implement functional checks in an application that external tools can
access through exposed endpoints at regular intervals. This can help to
verify that applications and services are performing correctly.

#### Context and Problem

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

#### Solution

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

<img src="./attachments/463533358.png" alt="">

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

#### Issues and Considerations

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
    credentials. Some third-party alternatives are 
    [Pingdom](https://www.pingdom.com/), 
    [Panopta](https://www.panopta.com/), 
    [NewRelic](https://newrelic.com/), and 
    [Statuscake](https://www.statuscake.com/).

-   How to ensure that the monitoring agent is performing correctly. One
    approach is to expose an endpoint that simply returns a value from
    the application configuration or a random value that can be used to
    test the agent.

    > Also ensure that the monitoring system performs checks on itself,
    > such as a self-test and built-in test, to avoid it issuing false
    > positive results.

#### When to use this Pattern

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

### Index Table Pattern

#### Overview

Create indexes over the fields in data stores that are frequently
referenced by queries. This pattern can improve query performance by
allowing applications to more quickly locate the data to retrieve from a
data store.

#### Context and Problem

Many data stores organize the data for a collection of entities using
the primary key. An application can use this key to locate and retrieve
data. The figure shows an example of a data store holding customer
information. The primary key is the Customer ID. The figure shows
customer information organized by the primary key (Customer ID).

<img src="./attachments/463533360.png" alt="">

While the primary key is valuable for queries that fetch data based on
the value of this key, an application might not be able to use the
primary key if it needs to retrieve data based on some other field. In
the customers example, an application can\'t use the Customer ID primary
key to retrieve customers if it queries data solely by referencing the
value of some other attribute, such as the town in which the customer is
located. To perform a query such as this, the application might have to
fetch and examine every customer record, which could be a slow process.

Many relational database management systems support secondary indexes. A
secondary index is a separate data structure that\'s organized by one or
more nonprimary (secondary) key fields, and it indicates where the data
for each indexed value is stored. The items in a secondary index are
typically sorted by the value of the secondary keys to enable fast
lookup of data. These indexes are usually maintained automatically by
the database management system.

You can create as many secondary indexes as you need to support the
different queries that your application performs. For example, in a
Customers table in a relational database where the Customer ID is the
primary key, it\'s beneficial to add a secondary index over the town
field if the application frequently looks up customers by the town where
they reside.

However, although secondary indexes are common in relational systems,
most NoSQL data stores used by cloud applications don\'t provide an
equivalent feature.

#### Solution

If the data store doesn\'t support secondary indexes, you can emulate
them manually by creating your own index tables. An index table
organizes the data by a specified key. Three strategies are commonly
used for structuring an index table, depending on the number of
secondary indexes that are required and the nature of the queries that
an application performs.

The first strategy is to duplicate the data in each index table but
organize it by different keys (complete denormalization). The next
figure shows index tables that organize the same customer information by
Town and LastName.

<img src="./attachments/463533361.png" alt="">

This strategy is appropriate if the data is relatively static compared
to the number of times it\'s queried using each key. If the data is more
dynamic, the processing overhead of maintaining each index table becomes
too large for this approach to be useful. Also, if the volume of data is
very large, the amount of space required to store the duplicate data is
significant.

The second strategy is to create normalized index tables organized by
different keys and reference the original data by using the primary key
rather than duplicating it, as shown in the following figure. The
original data is called a fact table.

<img src="./attachments/463533362.png" alt="">

This technique saves space and reduces the overhead of maintaining
duplicate data. The disadvantage is that an application has to perform
two lookup operations to find data using a secondary key. It has to find
the primary key for the data in the index table, and then use the
primary key to look up the data in the fact table.

The third strategy is to create partially normalized index tables
organized by different keys that duplicate frequently retrieved fields.
Reference the fact table to access less frequently accessed fields. The
next figure shows how commonly accessed data is duplicated in each index
table.

<img src="./attachments/463533363.png" alt="">

With this strategy, you can strike a balance between the first two
approaches. The data for common queries can be retrieved quickly by
using a single lookup, while the space and maintenance overhead isn\'t
as significant as duplicating the entire data set.

If an application frequently queries data by specifying a combination of
values (for example, "Find all customers that live in Redmond and that
have a last name of Smith"), you could implement the keys to the items
in the index table as a concatenation of the Town attribute and the
LastName attribute. The next figure shows an index table based on
composite keys. The keys are sorted by Town, and then by LastName for
records that have the same value for Town.

<img src="./attachments/463533364.png" alt="">

Index tables can speed up query operations over sharded data, and are
especially useful where the shard key is hashed. The next figure shows
an example where the shard key is a hash of the Customer ID. The index
table can organize data by the nonhashed value (Town and LastName), and
provide the hashed shard key as the lookup data. This can save the
application from repeatedly calculating hash keys (an expensive
operation) if it needs to retrieve data that falls within a range, or it
needs to fetch data in order of the nonhashed key. For example, a query
such as "Find all customers that live in Redmond" can be quickly
resolved by locating the matching items in the index table, where
they\'re all stored in a contiguous block. Then, follow the references
to the customer data using the shard keys stored in the index table.

<img src="./attachments/463533365.png" alt="">


#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

-   The overhead of maintaining secondary indexes can be significant.
    You must analyze and understand the queries that your application
    uses. Only create index tables when they\'re likely to be used
    regularly. Don\'t create speculative index tables to support queries
    that an application doesn\'t perform, or performs only occasionally.

-   Duplicating data in an index table can add significant overhead in
    storage costs and the effort required to maintain multiple copies of
    data.

-   Implementing an index table as a normalized structure that
    references the original data requires an application to perform two
    lookup operations to find data. The first operation searches the
    index table to retrieve the primary key, and the second uses the
    primary key to fetch the data.

-   If a system incorporates a number of index tables over very large
    data sets, it can be difficult to maintain consistency between index
    tables and the original data. It might be possible to design the
    application around the eventual consistency model. For example, to
    insert, update, or delete data, an application could post a message
    to a queue and let a separate task perform the operation and
    maintain the index tables that reference this data asynchronously.
    For more information about implementing eventual consistency, see
    the  [Data Consistency
    Primer](https://msdn.microsoft.com/library/dn589800.aspx).

    > Microsoft Azure storage tables support transactional updates for
    > changes made to data held in the same partition (referred to as
    > entity group transactions). If you can store the data for a fact
    > table and one or more index tables in the same partition, you can
    > use this feature to help ensure consistency.

-   Index tables might themselves be partitioned or sharded.

#### When to use this Pattern

Use this pattern to improve query performance when an application
frequently needs to retrieve data by using a key other than the primary
(or shard) key.

This pattern might not be useful when:

-   Data is volatile. An index table can become out of date very
    quickly, making it ineffective or making the overhead of maintaining
    the index table greater than any savings made by using it.
-   A field selected as the secondary key for an index table is
    nondiscriminating and can only have a small set of values (for
    example, gender).
-   The balance of the data values for a field selected as the secondary
    key for an index table are highly skewed. For example, if 90% of the
    records contain the same value in a field, then creating and
    maintaining an index table to look up data based on this field might
    create more overhead than scanning sequentially through the data.
    However, if queries very frequently target values that lie in the
    remaining 10%, this index can be useful. You should understand the
    queries that your application is performing, and how frequently
    they\'re performed.

### Leader Election Pattern

#### Overview

Coordinate the actions performed by a collection of collaborating
instances in a distributed application by electing one instance as the
leader that assumes responsibility for managing the others. This can
help to ensure that instances don\'t conflict with each other, cause
contention for shared resources, or inadvertently interfere with the
work that other instances are performing.

#### Context and Problem

A typical cloud application has many tasks acting in a coordinated
manner. These tasks could all be instances running the same code and
requiring access to the same resources, or they might be working
together in parallel to perform the individual parts of a complex
calculation.

The task instances might run separately for much of the time, but it
might also be necessary to coordinate the actions of each instance to
ensure that they don't conflict, cause contention for shared resources,
or accidentally interfere with the work that other task instances are
performing.

For example:

-   In a cloud-based system that implements horizontal scaling, multiple
    instances of the same task could be running at the same time with
    each instance serving a different user. If these instances write to
    a shared resource, it\'s necessary to coordinate their actions to
    prevent each instance from overwriting the changes made by the
    others.
-   If the tasks are performing individual elements of a complex
    calculation in parallel, the results need to be aggregated when they
    all complete.

The task instances are all peers, so there isn\'t a natural leader that
can act as the coordinator or aggregator.

#### Solution

A single task instance should be elected to act as the leader, and this
instance should coordinate the actions of the other subordinate task
instances. If all of the task instances are running the same code, they
are each capable of acting as the leader. Therefore, the election
process must be managed carefully to prevent two or more instances
taking over the leader role at the same time.

The system must provide a robust mechanism for selecting the leader.
This method has to cope with events such as network outages or process
failures. In many solutions, the subordinate task instances monitor the
leader through some type of heartbeat method, or by polling. If the
designated leader terminates unexpectedly, or a network failure makes
the leader unavailable to the subordinate task instances, it\'s
necessary for them to elect a new leader.

There are several strategies for electing a leader among a set of tasks
in a distributed environment, including:

-   Selecting the task instance with the lowest-ranked instance or
    process ID.
-   Racing to acquire a shared, distributed mutex. The first task
    instance that acquires the mutex is the leader. However, the system
    must ensure that, if the leader terminates or becomes disconnected
    from the rest of the system, the mutex is released to allow another
    task instance to become the leader.
-   Implementing one of the common leader election algorithms such as
    the  [Bully Algorithm](https://www.cs.colostate.edu/~cs551/CourseNotes/Synchronization/BullyExample.html) or
    the  [Ring Algorithm](https://www.cs.colostate.edu/~cs551/CourseNotes/Synchronization/RingElectExample.html).
    These algorithms assume that each candidate in the election has a
    unique ID, and that it can communicate with the other candidates
    reliably.

#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

-   The process of electing a leader should be resilient to transient
    and persistent failures.
-   It must be possible to detect when the leader has failed or has
    become otherwise unavailable (such as due to a communications
    failure). How quickly detection is needed is system dependent. Some
    systems might be able to function for a short time without a leader,
    during which a transient fault might be fixed. In other cases, it
    might be necessary to detect leader failure immediately and trigger
    a new election.
-   In a system that implements horizontal autoscaling, the leader could
    be terminated if the system scales back and shuts down some of the
    computing resources.
-   Using a shared, distributed mutex introduces a dependency on the
    external service that provides the mutex. The service constitutes a
    single point of failure. If it becomes unavailable for any reason,
    the system won\'t be able to elect a leader.
-   Using a single dedicated process as the leader is a straightforward
    approach. However, if the process fails there could be a significant
    delay while it\'s restarted. The resulting latency can affect the
    performance and response times of other processes if they\'re
    waiting for the leader to coordinate an operation.
-   Implementing one of the leader election algorithms manually provides
    the greatest flexibility for tuning and optimizing the code.

#### When to use this Pattern

Use this pattern when the tasks in a distributed application, such as a
cloud-hosted solution, need careful coordination and there\'s no natural
leader.

> Avoid making the leader a bottleneck in the system. The purpose of the
> leader is to coordinate the work of the subordinate tasks, and it
> doesn\'t necessarily have to participate in this work
> itself---although it should be able to do so if the task isn\'t
> elected as the leader.

This pattern might not be useful if:

-   There\'s a natural leader or dedicated process that can always act
    as the leader. For example, it might be possible to implement a
    singleton process that coordinates the task instances. If this
    process fails or becomes unhealthy, the system can shut it down and
    restart it.
-   The coordination between tasks can be achieved using a more
    lightweight method. For example, if several task instances simply
    need coordinated access to a shared resource, a better solution is
    to use optimistic or pessimistic locking to control access.
-   A third-party solution is more appropriate. For example, the
    Microsoft Azure HDInsight service (based on Apache Hadoop) uses the
    services provided by Apache Zookeeper to coordinate the map and
    reduce tasks that collect and summarize data.

### Materialized View Pattern

#### Overview

Generate prepopulated views over the data in one or more data stores
when the data isn\'t ideally formatted for required query operations.
This can help support efficient querying and data extraction, and
improve application performance.

#### Context and Problem

When storing data, the priority for developers and data administrators
is often focused on how the data is stored, as opposed to how it\'s
read. The chosen storage format is usually closely related to the format
of the data, requirements for managing data size and data integrity, and
the kind of store in use. For example, when using NoSQL document store,
the data is often represented as a series of aggregates, each containing
all of the information for that entity.

However, this can have a negative effect on queries. When a query only
needs a subset of the data from some entities, such as a summary of
orders for several customers without all of the order details, it must
extract all of the data for the relevant entities in order to obtain the
required information.

#### Solution

To support efficient querying, a common solution is to generate, in
advance, a view that materializes the data in a format suited to the
required results set. The Materialized View pattern describes generating
prepopulated views of data in environments where the source data isn\'t
in a suitable format for querying, where generating a suitable query is
difficult, or where query performance is poor due to the nature of the
data or the data store.

These materialized views, which only contain data required by a query,
allow applications to quickly obtain the information they need. In
addition to joining tables or combining data entities, materialized
views can include the current values of calculated columns or data
items, the results of combining values or executing transformations on
the data items, and values specified as part of the query. A
materialized view can even be optimized for just a single query.

A key point is that a materialized view and the data it contains is
completely disposable because it can be entirely rebuilt from the source
data stores. A materialized view is never updated directly by an
application, and so it\'s a specialized cache.

When the source data for the view changes, the view must be updated to
include the new information. You can schedule this to happen
automatically, or when the system detects a change to the original data.
In some cases it might be necessary to regenerate the view manually. The
figure shows an example of how the Materialized View pattern might be
used.

<img src="./attachments/463533368.png" alt="">

#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

How and when the view will be updated. Ideally it\'ll regenerate in
response to an event indicating a change to the source data, although
this can lead to excessive overhead if the source data changes rapidly.
Alternatively, consider using a scheduled task, an external trigger, or
a manual action to regenerate the view.

In some systems, such as when using the Event Sourcing pattern to
maintain a store of only the events that modified the data, materialized
views are necessary. Prepopulating views by examining all events to
determine the current state might be the only way to obtain information
from the event store. If you\'re not using Event Sourcing, you need to
consider whether a materialized view is helpful or not. Materialized
views tend to be specifically tailored to one, or a small number of
queries. If many queries are used, materialized views can result in
unacceptable storage capacity requirements and storage cost.

Consider the impact on data consistency when generating the view, and
when updating the view if this occurs on a schedule. If the source data
is changing at the point when the view is generated, the copy of the
data in the view won\'t be fully consistent with the original data.

Consider where you\'ll store the view. The view doesn\'t have to be
located in the same store or partition as the original data. It can be a
subset from a few different partitions combined.

A view can be rebuilt if lost. Because of that, if the view is transient
and is only used to improve query performance by reflecting the current
state of the data, or to improve scalability, it can be stored in a
cache or in a less reliable location.

When defining a materialized view, maximize its value by adding data
items or columns to it based on computation or transformation of
existing data items, on values passed in the query, or on combinations
of these values when appropriate.

Where the storage mechanism supports it, consider indexing the
materialized view to further increase performance. Most relational
databases support indexing for views, as do big data solutions based on
Apache Hadoop.

#### When to use this Pattern

This pattern is useful when:

-   Creating materialized views over data that\'s difficult to query
    directly, or where queries must be very complex to extract data
    that\'s stored in a normalized, semi-structured, or unstructured
    way.
-   Creating temporary views that can dramatically improve query
    performance, or can act directly as source views or data transfer
    objects for the UI, for reporting, or for display.
-   Supporting occasionally connected or disconnected scenarios where
    connection to the data store isn\'t always available. The view can
    be cached locally in this case.
-   Simplifying queries and exposing data for experimentation in a way
    that doesn\'t require knowledge of the source data format. For
    example, by joining different tables in one or more databases, or
    one or more domains in NoSQL stores, and then formatting the data to
    fit its eventual use.
-   Providing access to specific subsets of the source data that, for
    security or privacy reasons, shouldn\'t be generally accessible,
    open to modification, or fully exposed to users.
-   Bridging different data stores, to take advantage of their
    individual capabilities. For example, using a cloud store that\'s
    efficient for writing as the reference data store, and a relational
    database that offers good query and read performance to hold the
    materialized views.

This pattern isn\'t useful in the following situations:

-   The source data is simple and easy to query.
-   The source data changes very quickly, or can be accessed without
    using a view. In these cases, you should avoid the processing
    overhead of creating views.
-   Consistency is a high priority. The views might not always be fully
    consistent with the original data.

### Pipes and Filters Pattern

#### Overview

Decompose a task that performs complex processing into a series of
separate elements that can be reused. This can improve performance,
scalability, and reusability by allowing task elements that perform the
processing to be deployed and scaled independently.

#### Context and Problem

An application is required to perform a variety of tasks of varying
complexity on the information that it processes. A straightforward but
inflexible approach to implementing an application is to perform this
processing as a monolithic module. However, this approach is likely to
reduce the opportunities for refactoring the code, optimizing it, or
reusing it if parts of the same processing are required elsewhere within
the application.

The figure illustrates the issues with processing data using the
monolithic approach. An application receives and processes data from two
sources. The data from each source is processed by a separate module
that performs a series of tasks to transform this data, before passing
the result to the business logic of the application.

<img src="./attachments/463533383.png" alt="">

Some of the tasks that the monolithic modules perform are functionally
very similar, but the modules have been designed separately. The code
that implements the tasks is closely coupled in a module, and has been
developed with little or no thought given to reuse or scalability.

However, the processing tasks performed by each module, or the
deployment requirements for each task, could change as business
requirements are updated. Some tasks might be compute intensive and
could benefit from running on powerful hardware, while others might not
require such expensive resources. Also, additional processing might be
required in the future, or the order in which the tasks performed by the
processing could change. A solution is required that addresses these
issues, and increases the possibilities for code reuse.

#### Solution

Break down the processing required for each stream into a set of
separate components (or filters), each performing a single task. By
standardizing the format of the data that each component receives and
sends, these filters can be combined together into a pipeline. This
helps to avoid duplicating code, and makes it easy to remove, replace,
or integrate additional components if the processing requirements
change. The next figure shows a solution implemented using pipes and
filters.

<img src="./attachments/463533384.png" alt="">

The time it takes to process a single request depends on the speed of
the slowest filter in the pipeline. One or more filters could be a
bottleneck, especially if a large number of requests appear in a stream
from a particular data source. A key advantage of the pipeline structure
is that it provides opportunities for running parallel instances of slow
filters, enabling the system to spread the load and improve throughput.

The filters that make up a pipeline can run on different machines,
enabling them to be scaled independently and take advantage of the
elasticity that many cloud environments provide. A filter that is
computationally intensive can run on high-performance hardware, while
other less demanding filters can be hosted on less expensive commodity
hardware. The filters don\'t even have to be in the same datacenter or
geographic location, which allows each element in a pipeline to run in
an environment close to the resources it requires. The next figure shows
an example applied to the pipeline for the data from Source 1.

<img src="./attachments/463533385.png" alt="">

If the input and output of a filter are structured as a stream, it\'s
possible to perform the processing for each filter in parallel. The
first filter in the pipeline can start its work and output its results,
which are passed directly on to the next filter in the sequence before
the first filter has completed its work.

Another benefit is the resiliency that this model can provide. If a
filter fails or the machine it\'s running on is no longer available, the
pipeline can reschedule the work that the filter was performing and
direct this work to another instance of the component. Failure of a
single filter doesn\'t necessarily result in failure of the entire
pipeline.

Using the Pipes and Filters pattern in conjunction with the 
[Compensating Transaction
pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/compensating-transaction) is
an alternative approach to implementing distributed transactions. A
distributed transaction can be broken down into separate, compensable
tasks, each of which can be implemented by using a filter that also
implements the Compensating Transaction pattern. The filters in a
pipeline can be implemented as separate hosted tasks running close to
the data that they maintain.

#### Issues and Considerations

You should consider the following points when deciding how to implement
this pattern:

-   **Complexity**. The increased flexibility that this pattern provides
    can also introduce complexity, especially if the filters in a
    pipeline are distributed across different servers.

-   **Reliability**. Use an infrastructure that ensures that data
    flowing between filters in a pipeline won\'t be lost.

-   **Idempotency**. If a filter in a pipeline fails after receiving a
    message and the work is rescheduled to another instance of the
    filter, part of the work might have already been completed. If this
    work updates some aspect of the global state (such as information
    stored in a database), the same update could be repeated. A similar
    issue might occur if a filter fails after posting its results to the
    next filter in the pipeline, but before indicating that it\'s
    completed its work successfully. In these cases, the same work could
    be repeated by another instance of the filter, causing the same
    results to be posted twice. This could result in subsequent filters
    in the pipeline processing the same data twice. Therefore filters in
    a pipeline should be designed to be idempotent. For more
    information, see  [Idempotency
    Patterns](https://blog.jonathanoliver.com/idempotency-patterns/) on
    Jonathan Oliver's blog.

-   **Repeated messages**. If a filter in a pipeline fails after posting
    a message to the next stage of the pipeline, another instance of the
    filter might be run, and it\'ll post a copy of the same message to
    the pipeline. This could cause two instances of the same message to
    be passed to the next filter. To avoid this, the pipeline should
    detect and eliminate duplicate messages.

    > If you\'re implementing the pipeline by using message queues (such
    > as Microsoft Azure Service Bus queues), the message queuing
    > infrastructure might provide automatic duplicate message detection
    > and removal.

-   **Context and state**. In a pipeline, each filter essentially runs
    in isolation and shouldn\'t make any assumptions about how it was
    invoked. This means that each filter should be provided with
    sufficient context to perform its work. This context could include a
    large amount of state information.

#### When to use this Pattern

Use this pattern when:

-   The processing required by an application can easily be broken down
    into a set of independent steps.

-   The processing steps performed by an application have different
    scalability requirements.

    > It\'s possible to group filters that should scale together in the
    > same process. For more information, see the 
    > [Compute Resource Consolidation pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/compute-resource-consolidation).

-   Flexibility is required to allow reordering of the processing steps
    performed by an application, or the capability to add and remove
    steps.

-   The system can benefit from distributing the processing for steps
    across different servers.

-   A reliable solution is required that minimizes the effects of
    failure in a step while data is being processed.

This pattern might not be useful when:

-   The processing steps performed by an application aren\'t
    independent, or they have to be performed together as part of the
    same transaction.

-   The amount of context or state information required by a step makes
    this approach inefficient. It might be possible to persist state
    information to a database instead, but don\'t use this strategy if
    the additional load on the database causes excessive contention.

### Priority Queue Pattern

#### Overview

Prioritize requests sent to services so that requests with a higher
priority are received and processed more quickly than those with a lower
priority. This pattern is useful in applications that offer different
service level guarantees to individual clients.

#### Context and Problem

Applications can delegate specific tasks to other services, for example,
to perform background processing or to integrate with other applications
or services. In the cloud, a message queue is typically used to delegate
tasks to background processing. In many cases the order requests are
received in by a service isn\'t important. In some cases, though, it\'s
necessary to prioritize specific requests. These requests should be
processed earlier than lower priority requests that were sent previously
by the application.

#### Solution

A queue is usually a first-in, first-out (FIFO) structure, and consumers
typically receive messages in the same order that they were posted to
the queue. However, some message queues support priority messaging. The
application posting a message can assign a priority and the messages in
the queue are automatically reordered so that those with a higher
priority will be received before those with a lower priority. The figure
illustrates a queue with priority messaging.

<img src="./attachments/463533387.png" alt="">

> Most message queue implementations support multiple consumers
> (following the  [Competing Consumers
> pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/competing-consumers)),
> and the number of consumer processes can be scaled up or down
> depending on demand.

In systems that don\'t support priority-based message queues, an
alternative solution is to maintain a separate queue for each priority.
The application is responsible for posting messages to the appropriate
queue. Each queue can have a separate pool of consumers. Higher priority
queues can have a larger pool of consumers running on faster hardware
than lower priority queues. The next figure illustrates using separate
message queues for each priority.

<img src="./attachments/463533388.png" alt="">

A variation on this strategy is to have a single pool of consumers that
check for messages on high priority queues first, and only then start to
fetch messages from lower priority queues. There are some semantic
differences between a solution that uses a single pool of consumer
processes (either with a single queue that supports messages with
different priorities or with multiple queues that each handle messages
of a single priority), and a solution that uses multiple queues with a
separate pool for each queue.

In the single pool approach, higher priority messages are always
received and processed before lower priority messages. In theory,
messages that have a very low priority could be continually superseded
and might never be processed. In the multiple pool approach, lower
priority messages will always be processed, just not as quickly as those
of a higher priority (depending on the relative size of the pools and
the resources that they have available).

Using a priority queuing mechanism can provide the following advantages:

-   It allows applications to meet business requirements that require
    prioritization of availability or performance, such as offering
    different levels of service to specific groups of customers.
-   It can help to minimize operational costs. In the single queue
    approach, you can scale back the number of consumers if necessary.
    High priority messages will still be processed first (although
    possibly more slowly), and lower priority messages might be delayed
    for longer. If you\'ve implemented the multiple message queue
    approach with separate pools of consumers for each queue, you can
    reduce the pool of consumers for lower priority queues, or even
    suspend processing for some very low priority queues by stopping all
    the consumers that listen for messages on those queues.
-   The multiple message queue approach can help maximize application
    performance and scalability by partitioning messages based on
    processing requirements. For example, vital tasks can be prioritized
    to be handled by receivers that run immediately while less important
    background tasks can be handled by receivers that are scheduled to
    run at less busy periods.

#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

Define the priorities in the context of the solution. For example, high
priority could mean that messages should be processed within ten
seconds. Identify the requirements for handling high priority items, and
the other resources that should be allocated to meet these criteria.

Decide if all high priority items must be processed before any lower
priority items. If the messages are being processed by a single pool of
consumers, you have to provide a mechanism that can preempt and suspend
a task that\'s handling a low priority message if a higher priority
message becomes available.

In the multiple queue approach, when using a single pool of consumer
processes that listen on all queues rather than a dedicated consumer
pool for each queue, the consumer must apply an algorithm that ensures
it always services messages from higher priority queues before those
from lower priority queues.

Monitor the processing speed on high and low priority queues to ensure
that messages in these queues are processed at the expected rates.

If you need to guarantee that low priority messages will be processed,
it\'s necessary to implement the multiple message queue approach with
multiple pools of consumers. Alternatively, in a queue that supports
message prioritization, it\'s possible to dynamically increase the
priority of a queued message as it ages. However, this approach depends
on the message queue providing this feature.

Using a separate queue for each message priority works best for systems
that have a small number of well-defined priorities.

Message priorities can be determined logically by the system. For
example, rather than having explicit high and low priority messages,
they could be designated as "fee paying customer," or "non-fee paying
customer." Depending on your business model, your system can allocate
more resources to processing messages from fee paying customers than
non-fee paying ones.

There might be a financial and processing cost associated with checking
a queue for a message (some commercial messaging systems charge a small
fee each time a message is posted or retrieved, and each time a queue is
queried for messages). This cost increases when checking multiple
queues.

It\'s possible to dynamically adjust the size of a pool of consumers
based on the length of the queue that the pool is servicing. For more
information, see the  [Autoscaling
Guidance](https://msdn.microsoft.com/library/dn589774.aspx).

#### When to use this Pattern

This pattern is useful in scenarios where:

-   The system must handle multiple tasks that have different priorities.
-   Different users or tenants should be served with different priority.

### Publisher-Subscriber Pattern

#### Overview

Enable an application to announce events to multiple interested
consumers asynchronously, without coupling the senders to the receivers.

**Also called**: Pub/sub messaging

#### Context and Problem

In cloud-based and distributed applications, components of the system
often need to provide information to other components as events happen.

Asynchronous messaging is an effective way to decouple senders from
consumers, and avoid blocking the sender to wait for a response.
However, using a dedicated message queue for each consumer does not
effectively scale to many consumers. Also, some of the consumers might
be interested in only a subset of the information. How can the sender
announce events to all interested consumers without knowing their
identities?

#### Solution

Introduce an asynchronous messaging subsystem that includes the
following:

-   An input messaging channel used by the sender. The sender packages
    events into messages, using a known message format, and sends these
    messages via the input channel. The sender in this pattern is also
    called the  *publisher*.

     Note

    A  *message* is a packet of data. An  *event* is a message that
    notifies other components about a change or an action that has taken
    place.

-   One output messaging channel per consumer. The consumers are known
    as  *subscribers*.

-   A mechanism for copying each message from the input channel to the
    output channels for all subscribers interested in that message. This
    operation is typically handled by an intermediary such as a message
    broker or event bus.

The following diagram shows the logical components of this pattern:

<img src="./attachments/463533390.png" alt="">

Pub/sub messaging has the following benefits:

-   It decouples subsystems that still need to communicate. Subsystems
    can be managed independently, and messages can be properly managed
    even if one or more receivers are offline.

-   It increases scalability and improves responsiveness of the sender.
    The sender can quickly send a single message to the input channel,
    then return to its core processing responsibilities. The messaging
    infrastructure is responsible for ensuring messages are delivered to
    interested subscribers.

-   It improves reliability. Asynchronous messaging helps applications
    continue to run smoothly under increased loads and handle
    intermittent failures more effectively.

-   It allows for deferred or scheduled processing. Subscribers can wait
    to pick up messages until off-peak hours, or messages can be routed
    or processed according to a specific schedule.

-   It enables simpler integration between systems using different
    platforms, programming languages, or communication protocols, as
    well as between on-premises systems and applications running in the
    cloud.

-   It facilitates asynchronous workflows across an enterprise.

-   It improves testability. Channels can be monitored and messages can
    be inspected or logged as part of an overall integration test
    strategy.

-   It provides separation of concerns for your applications. Each
    application can focus on its core capabilities, while the messaging
    infrastructure handles everything required to reliably route
    messages to multiple consumers.

#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

-   **Existing technologies.** It is strongly recommended to use
    available messaging products and services that support a
    publish-subscribe model, rather than building your own. In Azure,
    consider using  [Service Bus](https://docs.microsoft.com/en-us/azure/service-bus-messaging/) or 
    [Event Grid](https://docs.microsoft.com/en-us/azure/event-grid/).
    Other technologies that can be used for pub/sub messaging include
    Redis, RabbitMQ, and Apache Kafka.

-   **Subscription handling.** The messaging infrastructure must provide
    mechanisms that consumers can use to subscribe to or unsubscribe
    from available channels.

-   **Security.** Connecting to any message channel must be restricted
    by security policy to prevent eavesdropping by unauthorized users or
    applications.

-   **Subsets of messages.** Subscribers are usually only interested in
    subset of the messages distributed by a publisher. Messaging
    services often allow subscribers to narrow the set of messages
    received by:

    -   **Topics.** Each topic has a dedicated output channel, and each
        consumer can subscribe to all relevant topics.
    -   **Content filtering.** Messages are inspected and distributed
        based on the content of each message. Each subscriber can
        specify the content it is interested in.

-   **Wildcard subscribers.** Consider allowing subscribers to subscribe
    to multiple topics via wildcards.

-   **Bi-directional communication.** The channels in a
    publish-subscribe system are treated as unidirectional. If a
    specific subscriber needs to send acknowledgment or communicate
    status back to the publisher, consider using the  [Request/Reply
    Pattern](http://www.enterpriseintegrationpatterns.com/patterns/messaging/RequestReply.html).
    This pattern uses one channel to send a message to the subscriber,
    and a separate reply channel for communicating back to the
    publisher.

-   **Message ordering.** The order in which consumer instances receive
    messages isn\'t guaranteed, and doesn\'t necessarily reflect the
    order in which the messages were created. Design the system to
    ensure that message processing is idempotent to help eliminate any
    dependency on the order of message handling.

-   **Message priority.** Some solutions may require that messages are
    processed in a specific order. The  [Priority Queue
    pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/priority-queue) provides
    a mechanism for ensuring specific messages are delivered before
    others.

-   **Poison messages.** A malformed message, or a task that requires
    access to resources that aren\'t available, can cause a service
    instance to fail. The system should prevent such messages being
    returned to the queue. Instead, capture and store the details of
    these messages elsewhere so that they can be analyzed if necessary.

-   **Repeated messages.** The same message might be sent more than
    once. For example, the sender might fail after posting a message.
    Then a new instance of the sender might start up and repeat the
    message. The messaging infrastructure should implement duplicate
    message detection and removal (also known as de-duping) based on
    message IDs in order to provide at-most-once delivery of messages.

-   **Message expiration.** A message might have a limited lifetime. If
    it isn\'t processed within this period, it might no longer be
    relevant and should be discarded. A sender can specify an expiration
    time as part of the data in the message. A receiver can examine this
    information before deciding whether to perform the business logic
    associated with the message.

-   **Message scheduling.** A message might be temporarily embargoed and
    should not be processed until a specific date and time. The message
    should not be available to a receiver until this time.

#### When to use this Pattern

Use this pattern when:

-   An application needs to broadcast information to a significant
    number of consumers.

-   An application needs to communicate with one or more
    independently-developed applications or services, which may use
    different platforms, programming languages, and communication
    protocols.

-   An application can send information to consumers without requiring
    real-time responses from the consumers.

-   The systems being integrated are designed to support an eventual
    consistency model for their data.

-   An application needs to communicate information to multiple
    consumers, which may have different availability requirements or
    uptime schedules than the sender.

This pattern might not be useful when:

-   An application has only a few consumers who need significantly
    different information from the producing application.

-   An application requires near real-time interaction with consumers.

### Queue-Based Load Leveling Pattern

#### Overview

Use a queue that acts as a buffer between a task and a service it
invokes in order to smooth intermittent heavy loads that can cause the
service to fail or the task to time out. This can help to minimize the
impact of peaks in demand on availability and responsiveness for both
the task and the service.

#### Context and Problem

Many solutions in the cloud involve running tasks that invoke services.
In this environment, if a service is subjected to intermittent heavy
loads, it can cause performance or reliability issues.

A service could be part of the same solution as the tasks that use it,
or it could be a third-party service providing access to frequently used
resources such as a cache or a storage service. If the same service is
used by a number of tasks running concurrently, it can be difficult to
predict the volume of requests to the service at any time.

A service might experience peaks in demand that cause it to overload and
be unable to respond to requests in a timely manner. Flooding a service
with a large number of concurrent requests can also result in the
service failing if it\'s unable to handle the contention these requests
cause.

#### Solution

Refactor the solution and introduce a queue between the task and the
service. The task and the service run asynchronously. The task posts a
message containing the data required by the service to a queue. The
queue acts as a buffer, storing the message until it\'s retrieved by the
service. The service retrieves the messages from the queue and processes
them. Requests from a number of tasks, which can be generated at a
highly variable rate, can be passed to the service through the same
message queue. This figure shows using a queue to level the load on a
service.

<img src="./attachments/463533392.png" alt="">

The queue decouples the tasks from the service, and the service can
handle the messages at its own pace regardless of the volume of requests
from concurrent tasks. Additionally, there\'s no delay to a task if the
service isn\'t available at the time it posts a message to the queue.

This pattern provides the following benefits:

-   It can help to maximize availability because delays arising in
    services won\'t have an immediate and direct impact on the
    application, which can continue to post messages to the queue even
    when the service isn\'t available or isn\'t currently processing
    messages.

-   It can help to maximize scalability because both the number of
    queues and the number of services can be varied to meet demand.

-   It can help to control costs because the number of service instances
    deployed only have to be adequate to meet average load rather than
    the peak load.

    > Some services implement throttling when demand reaches a threshold
    > beyond which the system could fail. Throttling can reduce the
    > functionality available. You can implement load leveling with
    > these services to ensure that this threshold isn\'t reached.

#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

-   It\'s necessary to implement application logic that controls the
    rate at which services handle messages to avoid overwhelming the
    target resource. Avoid passing spikes in demand to the next stage of
    the system. Test the system under load to ensure that it provides
    the required leveling, and adjust the number of queues and the
    number of service instances that handle messages to achieve this.
-   Message queues are a one-way communication mechanism. If a task
    expects a reply from a service, it might be necessary to implement a
    mechanism that the service can use to send a response. For more
    information, see the  [Asynchronous Messaging Primer](https://msdn.microsoft.com/library/dn589781.aspx).
-   Be careful if you apply autoscaling to services that are listening
    for requests on the queue. This can result in increased contention
    for any resources that these services share and diminish the
    effectiveness of using the queue to level the load.

#### When to use this Pattern

This pattern is useful to any application that uses services that are
subject to overloading.

This pattern isn\'t useful if the application expects a response from
the service with minimal latency.

### Retry Pattern

#### Overview

Enable an application to handle transient failures when it tries to
connect to a service or network resource, by transparently retrying a
failed operation. This can improve the stability of the application.

#### Context and Problem

An application that communicates with elements running in the cloud has
to be sensitive to the transient faults that can occur in this
environment. Faults include the momentary loss of network connectivity
to components and services, the temporary unavailability of a service,
or timeouts that occur when a service is busy.

These faults are typically self-correcting, and if the action that
triggered a fault is repeated after a suitable delay it\'s likely to be
successful. For example, a database service that\'s processing a large
number of concurrent requests can implement a throttling strategy that
temporarily rejects any further requests until its workload has eased.
An application trying to access the database might fail to connect, but
if it tries again after a delay it might succeed.

#### Solution

In the cloud, transient faults aren\'t uncommon and an application
should be designed to handle them elegantly and transparently. This
minimizes the effects faults can have on the business tasks the
application is performing.

If an application detects a failure when it tries to send a request to a
remote service, it can handle the failure using the following
strategies:

-   **Cancel**. If the fault indicates that the failure isn\'t transient
    or is unlikely to be successful if repeated, the application should
    cancel the operation and report an exception. For example, an
    authentication failure caused by providing invalid credentials is
    not likely to succeed no matter how many times it\'s attempted.

-   **Retry**. If the specific fault reported is unusual or rare, it
    might have been caused by unusual circumstances such as a network
    packet becoming corrupted while it was being transmitted. In this
    case, the application could retry the failing request again
    immediately because the same failure is unlikely to be repeated and
    the request will probably be successful.

-   **Retry after delay**. If the fault is caused by one of the more
    commonplace connectivity or busy failures, the network or service
    might need a short period while the connectivity issues are
    corrected or the backlog of work is cleared. The application should
    wait for a suitable time before retrying the request.

For the more common transient failures, the period between retries
should be chosen to spread requests from multiple instances of the
application as evenly as possible. This reduces the chance of a busy
service continuing to be overloaded. If many instances of an application
are continually overwhelming a service with retry requests, it\'ll take
the service longer to recover.

If the request still fails, the application can wait and make another
attempt. If necessary, this process can be repeated with increasing
delays between retry attempts, until some maximum number of requests
have been attempted. The delay can be increased incrementally or
exponentially, depending on the type of failure and the probability that
it\'ll be corrected during this time.

The following diagram illustrates invoking an operation in a hosted
service using this pattern. If the request is unsuccessful after a
predefined number of attempts, the application should treat the fault as
an exception and handle it accordingly.

<img src="./attachments/463533394.png" alt="">

The application should wrap all attempts to access a remote service in
code that implements a retry policy matching one of the strategies
listed above. Requests sent to different services can be subject to
different policies. Some vendors provide libraries that implement retry
policies, where the application can specify the maximum number of
retries, the time between retry attempts, and other parameters.

An application should log the details of faults and failing operations.
This information is useful to operators. If a service is frequently
unavailable or busy, it\'s often because the service has exhausted its
resources. You can reduce the frequency of these faults by scaling out
the service. For example, if a database service is continually
overloaded, it might be beneficial to partition the database and spread
the load across multiple servers.

> [Microsoft Entity Framework](https://docs.microsoft.com/en-us/ef) provides
> facilities for retrying database operations. Also, most Azure services
> and client SDKs include a retry mechanism. For more information, see 
> [Retry guidance for specific services](https://docs.microsoft.com/en-us/azure/architecture/best-practices/retry-service-specific).

#### Issues and Considerations

You should consider the following points when deciding how to implement
this pattern.

The retry policy should be tuned to match the business requirements of
the application and the nature of the failure. For some noncritical
operations, it\'s better to fail fast rather than retry several times
and impact the throughput of the application. For example, in an
interactive web application accessing a remote service, it\'s better to
fail after a smaller number of retries with only a short delay between
retry attempts, and display a suitable message to the user (for example,
"please try again later"). For a batch application, it might be more
appropriate to increase the number of retry attempts with an
exponentially increasing delay between attempts.

An aggressive retry policy with minimal delay between attempts, and a
large number of retries, could further degrade a busy service that\'s
running close to or at capacity. This retry policy could also affect the
responsiveness of the application if it\'s continually trying to perform
a failing operation.

If a request still fails after a significant number of retries, it\'s
better for the application to prevent further requests going to the same
resource and simply report a failure immediately. When the period
expires, the application can tentatively allow one or more requests
through to see whether they\'re successful. For more details of this
strategy, see the  [Circuit Breaker pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker).

Consider whether the operation is idempotent. If so, it\'s inherently
safe to retry. Otherwise, retries could cause the operation to be
executed more than once, with unintended side effects. For example, a
service might receive the request, process the request successfully, but
fail to send a response. At that point, the retry logic might re-send
the request, assuming that the first request wasn\'t received.

A request to a service can fail for a variety of reasons raising
different exceptions depending on the nature of the failure. Some
exceptions indicate a failure that can be resolved quickly, while others
indicate that the failure is longer lasting. It\'s useful for the retry
policy to adjust the time between retry attempts based on the type of
the exception.

Consider how retrying an operation that\'s part of a transaction will
affect the overall transaction consistency. Fine tune the retry policy
for transactional operations to maximize the chance of success and
reduce the need to undo all the transaction steps.

Ensure that all retry code is fully tested against a variety of failure
conditions. Check that it doesn\'t severely impact the performance or
reliability of the application, cause excessive load on services and
resources, or generate race conditions or bottlenecks.

Implement retry logic only where the full context of a failing operation
is understood. For example, if a task that contains a retry policy
invokes another task that also contains a retry policy, this extra layer
of retries can add long delays to the processing. It might be better to
configure the lower-level task to fail fast and report the reason for
the failure back to the task that invoked it. This higher-level task can
then handle the failure based on its own policy.

It\'s important to log all connectivity failures that cause a retry so
that underlying problems with the application, services, or resources
can be identified.

Investigate the faults that are most likely to occur for a service or a
resource to discover if they\'re likely to be long lasting or terminal.
If they are, it\'s better to handle the fault as an exception. The
application can report or log the exception, and then try to continue
either by invoking an alternative service (if one is available), or by
offering degraded functionality. For more information on how to detect
and handle long-lasting faults, see the  [Circuit Breaker
pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker).

#### When to use this Pattern

Use this pattern when an application could experience transient faults
as it interacts with a remote service or accesses a remote resource.
These faults are expected to be short lived, and repeating a request
that has previously failed could succeed on a subsequent attempt.

This pattern might not be useful:

-   When a fault is likely to be long lasting, because this can affect
    the responsiveness of an application. The application might be
    wasting time and resources trying to repeat a request that\'s likely
    to fail.
-   For handling failures that aren\'t due to transient faults, such as
    internal exceptions caused by errors in the business logic of an
    application.
-   As an alternative to addressing scalability issues in a system. If
    an application experiences frequent busy faults, it\'s often a sign
    that the service or resource being accessed should be scaled up.

### Scheduler Agent Supervisor Pattern

#### Overview

Coordinate a set of distributed actions as a single operation. If any of
the actions fail, try to handle the failures transparently, or else undo
the work that was performed, so the entire operation succeeds or fails
as a whole. This can add resiliency to a distributed system, by enabling
it to recover and retry actions that fail due to transient exceptions,
long-lasting faults, and process failures.

#### Context and Problem

An application performs tasks that include a number of steps, some of
which might invoke remote services or access remote resources. The
individual steps might be independent of each other, but they are
orchestrated by the application logic that implements the task.

Whenever possible, the application should ensure that the task runs to
completion and resolve any failures that might occur when accessing
remote services or resources. Failures can occur for many reasons. For
example, the network might be down, communications could be interrupted,
a remote service might be unresponsive or in an unstable state, or a
remote resource might be temporarily inaccessible, perhaps due to
resource constraints. In many cases the failures will be transient and
can be handled by using the  [Retry
pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/retry).

If the application detects a more permanent fault it can\'t easily
recover from, it must be able to restore the system to a consistent
state and ensure integrity of the entire operation.

#### Solution

The Scheduler Agent Supervisor pattern defines the following actors.
These actors orchestrate the steps to be performed as part of the
overall task.

-   The  **Scheduler** arranges for the steps that make up the task to
    be executed and orchestrates their operation. These steps can be
    combined into a pipeline or workflow. The Scheduler is responsible
    for ensuring that the steps in this workflow are performed in the
    right order. As each step is performed, the Scheduler records the
    state of the workflow, such as \"step not yet started,\" \"step
    running,\" or \"step completed." The state information should also
    include an upper limit of the time allowed for the step to finish,
    called the complete-by time. If a step requires access to a remote
    service or resource, the Scheduler invokes the appropriate Agent,
    passing it the details of the work to be performed. The Scheduler
    typically communicates with an Agent using asynchronous
    request/response messaging. This can be implemented using queues,
    although other distributed messaging technologies could be used
    instead.

    > The Scheduler performs a similar function to the Process Manager
    > in the  [Process Manager pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/ProcessManager.html).
    > The actual workflow is typically defined and implemented by a
    > workflow engine that\'s controlled by the Scheduler. This approach
    > decouples the business logic in the workflow from the Scheduler.

-   The  **Agent** contains logic that encapsulates a call to a remote
    service, or access to a remote resource referenced by a step in a
    task. Each Agent typically wraps calls to a single service or
    resource, implementing the appropriate error handling and retry
    logic (subject to a timeout constraint, described later). If the
    steps in the workflow being run by the Scheduler use several
    services and resources across different steps, each step might
    reference a different Agent (this is an implementation detail of the
    pattern).

-   The  **Supervisor** monitors the status of the steps in the task
    being performed by the Scheduler. It runs periodically (the
    frequency will be system-specific), and examines the status of steps
    maintained by the Scheduler. If it detects any that have timed out
    or failed, it arranges for the appropriate Agent to recover the step
    or execute the appropriate remedial action (this might involve
    modifying the status of a step). Note that the recovery or remedial
    actions are implemented by the Scheduler and Agents. The Supervisor
    should simply request that these actions be performed.

The Scheduler, Agent, and Supervisor are logical components and their
physical implementation depends on the technology being used. For
example, several logical agents might be implemented as part of a single
web service.

The Scheduler maintains information about the progress of the task and
the state of each step in a durable data store, called the state store.
The Supervisor can use this information to help determine whether a step
has failed. The figure illustrates the relationship between the
Scheduler, the Agents, the Supervisor, and the state store.

<img src="./attachments/463533396.png" alt="">

> This diagram shows a simplified version of the pattern. In a real
> implementation, there might be many instances of the Scheduler running
> concurrently, each a subset of tasks. Similarly, the system could run
> multiple instances of each Agent, or even multiple Supervisors. In
> this case, Supervisors must coordinate their work with each other
> carefully to ensure that they don't compete to recover the same failed
> steps and tasks. The  [Leader Election
> pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/leader-election) provides
> one possible solution to this problem.

When the application is ready to run a task, it submits a request to the
Scheduler. The Scheduler records initial state information about the
task and its steps (for example, step not yet started) in the state
store and then starts performing the operations defined by the workflow.
As the Scheduler starts each step, it updates the information about the
state of that step in the state store (for example, step running).

If a step references a remote service or resource, the Scheduler sends a
message to the appropriate Agent. The message contains the information
that the Agent needs to pass to the service or access the resource, in
addition to the complete-by time for the operation. If the Agent
completes its operation successfully, it returns a response to the
Scheduler. The Scheduler can then update the state information in the
state store (for example, step completed) and perform the next step.
This process continues until the entire task is complete.

An Agent can implement any retry logic that\'s necessary to perform its
work. However, if the Agent doesn\'t complete its work before the
complete-by period expires, the Scheduler will assume that the operation
has failed. In this case, the Agent should stop its work and not try to
return anything to the Scheduler (not even an error message), or try any
form of recovery. The reason for this restriction is that, after a step
has timed out or failed, another instance of the Agent might be
scheduled to run the failing step (this process is described later).

If the Agent fails, the Scheduler won\'t receive a response. The pattern
doesn\'t make a distinction between a step that has timed out and one
that has genuinely failed.

If a step times out or fails, the state store will contain a record that
indicates that the step is running, but the complete-by time will have
passed. The Supervisor looks for steps like this and tries to recover
them. One possible strategy is for the Supervisor to update the
complete-by value to extend the time available to complete the step, and
then send a message to the Scheduler identifying the step that has timed
out. The Scheduler can then try to repeat this step. However, this
design requires the tasks to be idempotent.

The Supervisor might need to prevent the same step from being retried if
it continually fails or times out. To do this, the Supervisor could
maintain a retry count for each step, along with the state information,
in the state store. If this count exceeds a predefined threshold the
Supervisor can adopt a strategy of waiting for an extended period before
notifying the Scheduler that it should retry the step, in the
expectation that the fault will be resolved during this period.
Alternatively, the Supervisor can send a message to the Scheduler to
request the entire task be undone by implementing a  [Compensating
Transaction
pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/compensating-transaction).
This approach will depend on the Scheduler and Agents providing the
information necessary to implement the compensating operations for each
step that completed successfully.

> It isn\'t the purpose of the Supervisor to monitor the Scheduler and
> Agents, and restart them if they fail. This aspect of the system
> should be handled by the infrastructure these components are running
> in. Similarly, the Supervisor shouldn\'t have knowledge of the actual
> business operations that the tasks being performed by the Scheduler
> are running (including how to compensate should these tasks fail).
> This is the purpose of the workflow logic implemented by the
> Scheduler. The sole responsibility of the Supervisor is to determine
> whether a step has failed and arrange either for it to be repeated or
> for the entire task containing the failed step to be undone.

If the Scheduler is restarted after a failure, or the workflow being
performed by the Scheduler terminates unexpectedly, the Scheduler should
be able to determine the status of any inflight task that it was
handling when it failed, and be prepared to resume this task from that
point. The implementation details of this process are likely to be
system-specific. If the task can\'t be recovered, it might be necessary
to undo the work already performed by the task. This might also require
implementing a  [compensating
transaction](https://docs.microsoft.com/en-us/azure/architecture/patterns/compensating-transaction).

The key advantage of this pattern is that the system is resilient in the
event of unexpected temporary or unrecoverable failures. The system can
be constructed to be self-healing. For example, if an Agent or the
Scheduler fails, a new one can be started and the Supervisor can arrange
for a task to be resumed. If the Supervisor fails, another instance can
be started and can take over from where the failure occurred. If the
Supervisor is scheduled to run periodically, a new instance can be
automatically started after a predefined interval. The state store can
be replicated to reach an even greater degree of resiliency.

#### Issues and Considerations

You should consider the following points when deciding how to implement
this pattern:

-   This pattern can be difficult to implement and requires thorough
    testing of each possible failure mode of the system.

-   The recovery/retry logic implemented by the Scheduler is complex and
    dependent on state information held in the state store. It might
    also be necessary to record the information required to implement a
    compensating transaction in a durable data store.

-   How often the Supervisor runs will be important. It should run often
    enough to prevent any failed steps from blocking an application for
    an extended period, but it shouldn\'t run so often that it becomes
    an overhead.

-   The steps performed by an Agent could be run more than once. The
    logic that implements these steps should be idempotent.

#### When to use this Pattern

Use this pattern when a process that runs in a distributed environment,
such as the cloud, must be resilient to communications failure and/or
operational failure.

This pattern might not be suitable for tasks that don\'t invoke remote
services or access remote resources.

### Scheduler Agent Supervisor Pattern

#### Overview

Coordinate a set of distributed actions as a single operation. If any of
the actions fail, try to handle the failures transparently, or else undo
the work that was performed, so the entire operation succeeds or fails
as a whole. This can add resiliency to a distributed system, by enabling
it to recover and retry actions that fail due to transient exceptions,
long-lasting faults, and process failures.

#### Context and Problem

An application performs tasks that include a number of steps, some of
which might invoke remote services or access remote resources. The
individual steps might be independent of each other, but they are
orchestrated by the application logic that implements the task.

Whenever possible, the application should ensure that the task runs to
completion and resolve any failures that might occur when accessing
remote services or resources. Failures can occur for many reasons. For
example, the network might be down, communications could be interrupted,
a remote service might be unresponsive or in an unstable state, or a
remote resource might be temporarily inaccessible, perhaps due to
resource constraints. In many cases the failures will be transient and
can be handled by using the  [Retry
pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/retry).

If the application detects a more permanent fault it can\'t easily
recover from, it must be able to restore the system to a consistent
state and ensure integrity of the entire operation.

#### Solution

The Scheduler Agent Supervisor pattern defines the following actors.
These actors orchestrate the steps to be performed as part of the
overall task.

-   The  **Scheduler** arranges for the steps that make up the task to
    be executed and orchestrates their operation. These steps can be
    combined into a pipeline or workflow. The Scheduler is responsible
    for ensuring that the steps in this workflow are performed in the
    right order. As each step is performed, the Scheduler records the
    state of the workflow, such as \"step not yet started,\" \"step
    running,\" or \"step completed." The state information should also
    include an upper limit of the time allowed for the step to finish,
    called the complete-by time. If a step requires access to a remote
    service or resource, the Scheduler invokes the appropriate Agent,
    passing it the details of the work to be performed. The Scheduler
    typically communicates with an Agent using asynchronous
    request/response messaging. This can be implemented using queues,
    although other distributed messaging technologies could be used
    instead.

    > The Scheduler performs a similar function to the Process Manager
    > in the  [Process Manager pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/ProcessManager.html).
    > The actual workflow is typically defined and implemented by a
    > workflow engine that\'s controlled by the Scheduler. This approach
    > decouples the business logic in the workflow from the Scheduler.

-   The  **Agent** contains logic that encapsulates a call to a remote
    service, or access to a remote resource referenced by a step in a
    task. Each Agent typically wraps calls to a single service or
    resource, implementing the appropriate error handling and retry
    logic (subject to a timeout constraint, described later). If the
    steps in the workflow being run by the Scheduler use several
    services and resources across different steps, each step might
    reference a different Agent (this is an implementation detail of the
    pattern).

-   The  **Supervisor** monitors the status of the steps in the task
    being performed by the Scheduler. It runs periodically (the
    frequency will be system-specific), and examines the status of steps
    maintained by the Scheduler. If it detects any that have timed out
    or failed, it arranges for the appropriate Agent to recover the step
    or execute the appropriate remedial action (this might involve
    modifying the status of a step). Note that the recovery or remedial
    actions are implemented by the Scheduler and Agents. The Supervisor
    should simply request that these actions be performed.

The Scheduler, Agent, and Supervisor are logical components and their
physical implementation depends on the technology being used. For
example, several logical agents might be implemented as part of a single
web service.

The Scheduler maintains information about the progress of the task and
the state of each step in a durable data store, called the state store.
The Supervisor can use this information to help determine whether a step
has failed. The figure illustrates the relationship between the
Scheduler, the Agents, the Supervisor, and the state store.

<img src="./attachments/463533396.png" alt="">

> This diagram shows a simplified version of the pattern. In a real
> implementation, there might be many instances of the Scheduler running
> concurrently, each a subset of tasks. Similarly, the system could run
> multiple instances of each Agent, or even multiple Supervisors. In
> this case, Supervisors must coordinate their work with each other
> carefully to ensure that they don't compete to recover the same failed
> steps and tasks. The  [Leader Election
> pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/leader-election) provides
> one possible solution to this problem.

When the application is ready to run a task, it submits a request to the
Scheduler. The Scheduler records initial state information about the
task and its steps (for example, step not yet started) in the state
store and then starts performing the operations defined by the workflow.
As the Scheduler starts each step, it updates the information about the
state of that step in the state store (for example, step running).

If a step references a remote service or resource, the Scheduler sends a
message to the appropriate Agent. The message contains the information
that the Agent needs to pass to the service or access the resource, in
addition to the complete-by time for the operation. If the Agent
completes its operation successfully, it returns a response to the
Scheduler. The Scheduler can then update the state information in the
state store (for example, step completed) and perform the next step.
This process continues until the entire task is complete.

An Agent can implement any retry logic that\'s necessary to perform its
work. However, if the Agent doesn\'t complete its work before the
complete-by period expires, the Scheduler will assume that the operation
has failed. In this case, the Agent should stop its work and not try to
return anything to the Scheduler (not even an error message), or try any
form of recovery. The reason for this restriction is that, after a step
has timed out or failed, another instance of the Agent might be
scheduled to run the failing step (this process is described later).

If the Agent fails, the Scheduler won\'t receive a response. The pattern
doesn\'t make a distinction between a step that has timed out and one
that has genuinely failed.

If a step times out or fails, the state store will contain a record that
indicates that the step is running, but the complete-by time will have
passed. The Supervisor looks for steps like this and tries to recover
them. One possible strategy is for the Supervisor to update the
complete-by value to extend the time available to complete the step, and
then send a message to the Scheduler identifying the step that has timed
out. The Scheduler can then try to repeat this step. However, this
design requires the tasks to be idempotent.

The Supervisor might need to prevent the same step from being retried if
it continually fails or times out. To do this, the Supervisor could
maintain a retry count for each step, along with the state information,
in the state store. If this count exceeds a predefined threshold the
Supervisor can adopt a strategy of waiting for an extended period before
notifying the Scheduler that it should retry the step, in the
expectation that the fault will be resolved during this period.
Alternatively, the Supervisor can send a message to the Scheduler to
request the entire task be undone by implementing a  [Compensating Transaction pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/compensating-transaction).
This approach will depend on the Scheduler and Agents providing the
information necessary to implement the compensating operations for each
step that completed successfully.

> It isn\'t the purpose of the Supervisor to monitor the Scheduler and
> Agents, and restart them if they fail. This aspect of the system
> should be handled by the infrastructure these components are running
> in. Similarly, the Supervisor shouldn\'t have knowledge of the actual
> business operations that the tasks being performed by the Scheduler
> are running (including how to compensate should these tasks fail).
> This is the purpose of the workflow logic implemented by the
> Scheduler. The sole responsibility of the Supervisor is to determine
> whether a step has failed and arrange either for it to be repeated or
> for the entire task containing the failed step to be undone.

If the Scheduler is restarted after a failure, or the workflow being
performed by the Scheduler terminates unexpectedly, the Scheduler should
be able to determine the status of any inflight task that it was
handling when it failed, and be prepared to resume this task from that
point. The implementation details of this process are likely to be
system-specific. If the task can\'t be recovered, it might be necessary
to undo the work already performed by the task. This might also require
implementing a  [compensating transaction](https://docs.microsoft.com/en-us/azure/architecture/patterns/compensating-transaction).

The key advantage of this pattern is that the system is resilient in the
event of unexpected temporary or unrecoverable failures. The system can
be constructed to be self-healing. For example, if an Agent or the
Scheduler fails, a new one can be started and the Supervisor can arrange
for a task to be resumed. If the Supervisor fails, another instance can
be started and can take over from where the failure occurred. If the
Supervisor is scheduled to run periodically, a new instance can be
automatically started after a predefined interval. The state store can
be replicated to reach an even greater degree of resiliency.

#### Issues and Considerations

You should consider the following points when deciding how to implement
this pattern:

-   This pattern can be difficult to implement and requires thorough
    testing of each possible failure mode of the system.

-   The recovery/retry logic implemented by the Scheduler is complex and
    dependent on state information held in the state store. It might
    also be necessary to record the information required to implement a
    compensating transaction in a durable data store.

-   How often the Supervisor runs will be important. It should run often
    enough to prevent any failed steps from blocking an application for
    an extended period, but it shouldn\'t run so often that it becomes
    an overhead.

-   The steps performed by an Agent could be run more than once. The
    logic that implements these steps should be idempotent.

#### When to use this Pattern

Use this pattern when a process that runs in a distributed environment,
such as the cloud, must be resilient to communications failure and/or
operational failure.

This pattern might not be suitable for tasks that don\'t invoke remote
services or access remote resources.

### Sequential Convoy Pattern

#### Overview

Process a set of related messages in a defined order, without blocking
processing of other groups of messages.

#### Context and Problem

Applications often need to process a sequence of messages in the order
they arrive, while still being able to scale out to handle increased
load. In a distributed architecture, processing these messages in order
is not straightforward, because the workers can scale independently and
often pull messages independently, using a  [Competing Consumers
pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/competing-consumers).

For example, an order tracking system receives a ledger containing
orders and the relevant operations on those orders. These operations
could be to create an order, add a transaction to the order, modify a
past transaction, or delete an order. In this system, operations must be
performed in a first-in-first-out (FIFO) manner, but only at the order
level. However, the initial queue receives a ledger containing
transactions for many orders, which may be interleaved.

#### Solution

Push related messages into categories within the queuing system, and
have the queue listeners lock and pull only from one category, one
message at a time.

Here\'s what the general Sequential Convoy pattern looks like:

<img src="./attachments/463533398.png" alt="">

In the queue, messages for different categories may be interleaved, as
shown in the following diagram:

<img src="./attachments/463533399.png" alt="">

#### Issues and Considerations

#### When to use this Pattern

### Sharding Pattern

#### Overview

Divide a data store into a set of horizontal partitions or shards. This
can improve scalability when storing and accessing large volumes of
data.

#### Context and Problem

A data store hosted by a single server might be subject to the following
limitations:

-   **Storage space**. A data store for a large-scale cloud application
    is expected to contain a huge volume of data that could increase
    significantly over time. A server typically provides only a finite
    amount of disk storage, but you can replace existing disks with
    larger ones, or add further disks to a machine as data volumes grow.
    However, the system will eventually reach a limit where it isn\'t
    possible to easily increase the storage capacity on a given server.

-   **Computing resources**. A cloud application is required to support
    a large number of concurrent users, each of which run queries that
    retrieve information from the data store. A single server hosting
    the data store might not be able to provide the necessary computing
    power to support this load, resulting in extended response times for
    users and frequent failures as applications attempting to store and
    retrieve data time out. It might be possible to add memory or
    upgrade processors, but the system will reach a limit when it isn\'t
    possible to increase the compute resources any further.

-   **Network bandwidth**. Ultimately, the performance of a data store
    running on a single server is governed by the rate the server can
    receive requests and send replies. It\'s possible that the volume of
    network traffic might exceed the capacity of the network used to
    connect to the server, resulting in failed requests.

-   **Geography**. It might be necessary to store data generated by
    specific users in the same region as those users for legal,
    compliance, or performance reasons, or to reduce latency of data
    access. If the users are dispersed across different countries or
    regions, it might not be possible to store the entire data for the
    application in a single data store.

Scaling vertically by adding more disk capacity, processing power,
memory, and network connections can postpone the effects of some of
these limitations, but it\'s likely to only be a temporary solution. A
commercial cloud application capable of supporting large numbers of
users and high volumes of data must be able to scale almost
indefinitely, so vertical scaling isn\'t necessarily the best solution.

#### Solution

Divide the data store into horizontal partitions or shards. Each shard
has the same schema, but holds its own distinct subset of the data. A
shard is a data store in its own right (it can contain the data for many
entities of different types), running on a server acting as a storage
node.

This pattern has the following benefits:

-   You can scale the system out by adding further shards running on
    additional storage nodes.

-   A system can use off-the-shelf hardware rather than specialized and
    expensive computers for each storage node.

-   You can reduce contention and improve performance by balancing the
    workload across shards.

-   In the cloud, shards can be located physically close to the users
    that\'ll access the data.

When dividing a data store up into shards, decide which data should be
placed in each shard. A shard typically contains items that fall within
a specified range determined by one or more attributes of the data.
These attributes form the shard key (sometimes referred to as the
partition key). The shard key should be static. It shouldn\'t be based
on data that might change.

Sharding physically organizes the data. When an application stores and
retrieves data, the sharding logic directs the application to the
appropriate shard. This sharding logic can be implemented as part of the
data access code in the application, or it could be implemented by the
data storage system if it transparently supports sharding.

Abstracting the physical location of the data in the sharding logic
provides a high level of control over which shards contain which data.
It also enables data to migrate between shards without reworking the
business logic of an application if the data in the shards need to be
redistributed later (for example, if the shards become unbalanced). The
tradeoff is the additional data access overhead required in determining
the location of each data item as it\'s retrieved.

To ensure optimal performance and scalability, it\'s important to split
the data in a way that\'s appropriate for the types of queries that the
application performs. In many cases, it\'s unlikely that the sharding
scheme will exactly match the requirements of every query. For example,
in a multi-tenant system an application might need to retrieve tenant
data using the tenant ID, but it might also need to look up this data
based on some other attribute such as the tenant's name or location. To
handle these situations, implement a sharding strategy with a shard key
that supports the most commonly performed queries.

If queries regularly retrieve data using a combination of attribute
values, you can likely define a composite shard key by linking
attributes together. Alternatively, use a pattern such as 
[Index Table](https://docs.microsoft.com/en-us/azure/architecture/patterns/index-table) to
provide fast lookup to data based on attributes that aren\'t covered by
the shard key.

Sharding Strategies
-------------------

Three strategies are commonly used when selecting the shard key and
deciding how to distribute data across shards. Note that there doesn\'t
have to be a one-to-one correspondence between shards and the servers
that host them---a single server can host multiple shards. The
strategies are:

**The Lookup strategy**. In this strategy the sharding logic implements
a map that routes a request for data to the shard that contains that
data using the shard key. In a multi-tenant application all the data for
a tenant might be stored together in a shard using the tenant ID as the
shard key. Multiple tenants might share the same shard, but the data for
a single tenant won\'t be spread across multiple shards. The figure
illustrates sharding tenant data based on tenant IDs.

<img src="./attachments/463533401.png" alt="">

The mapping between the shard key and the physical storage can be based
on physical shards where each shard key maps to a physical partition.
Alternatively, a more flexible technique for rebalancing shards is
virtual partitioning, where shard keys map to the same number of virtual
shards, which in turn map to fewer physical partitions. In this
approach, an application locates data using a shard key that refers to a
virtual shard, and the system transparently maps virtual shards to
physical partitions. The mapping between a virtual shard and a physical
partition can change without requiring the application code be modified
to use a different set of shard keys.

**The Range strategy**. This strategy groups related items together in
the same shard, and orders them by shard key---the shard keys are
sequential. It\'s useful for applications that frequently retrieve sets
of items using range queries (queries that return a set of data items
for a shard key that falls within a given range). For example, if an
application regularly needs to find all orders placed in a given month,
this data can be retrieved more quickly if all orders for a month are
stored in date and time order in the same shard. If each order was
stored in a different shard, they\'d have to be fetched individually by
performing a large number of point queries (queries that return a single
data item). The next figure illustrates storing sequential sets (ranges)
of data in shard.

<img src="./attachments/463533402.png" alt="">

In this example, the shard key is a composite key containing the order
month as the most significant element, followed by the order day and the
time. The data for orders is naturally sorted when new orders are
created and added to a shard. Some data stores support two-part shard
keys containing a partition key element that identifies the shard and a
row key that uniquely identifies an item in the shard. Data is usually
held in row key order in the shard. Items that are subject to range
queries and need to be grouped together can use a shard key that has the
same value for the partition key but a unique value for the row key.

**The Hash strategy**. The purpose of this strategy is to reduce the
chance of hotspots (shards that receive a disproportionate amount of
load). It distributes the data across the shards in a way that achieves
a balance between the size of each shard and the average load that each
shard will encounter. The sharding logic computes the shard to store an
item in based on a hash of one or more attributes of the data. The
chosen hashing function should distribute data evenly across the shards,
possibly by introducing some random element into the computation. The
next figure illustrates sharding tenant data based on a hash of tenant
IDs.

<img src="./attachments/463533403.png" alt="">

To understand the advantage of the Hash strategy over other sharding
strategies, consider how a multi-tenant application that enrolls new
tenants sequentially might assign the tenants to shards in the data
store. When using the Range strategy, the data for tenants 1 to n will
all be stored in shard A, the data for tenants n+1 to m will all be
stored in shard B, and so on. If the most recently registered tenants
are also the most active, most data activity will occur in a small
number of shards, which could cause hotspots. In contrast, the Hash
strategy allocates tenants to shards based on a hash of their tenant ID.
This means that sequential tenants are most likely to be allocated to
different shards, which will distribute the load across them. The
previous figure shows this for tenants 55 and 56.

The three sharding strategies have the following advantages and considerations:

-   **Lookup**. This offers more control over the way that shards are
    configured and used. Using virtual shards reduces the impact when
    rebalancing data because new physical partitions can be added to
    even out the workload. The mapping between a virtual shard and the
    physical partitions that implement the shard can be modified without
    affecting application code that uses a shard key to store and
    retrieve data. Looking up shard locations can impose an additional
    overhead.
-   **Range**. This is easy to implement and works well with range
    queries because they can often fetch multiple data items from a
    single shard in a single operation. This strategy offers easier data
    management. For example, if users in the same region are in the same
    shard, updates can be scheduled in each time zone based on the local
    load and demand pattern. However, this strategy doesn\'t provide
    optimal balancing between shards. Rebalancing shards is difficult
    and might not resolve the problem of uneven load if the majority of
    activity is for adjacent shard keys.
-   **Hash**. This strategy offers a better chance of more even data and
    load distribution. Request routing can be accomplished directly by
    using the hash function. There\'s no need to maintain a map. Note
    that computing the hash might impose an additional overhead. Also,
    rebalancing shards is difficult.

Most common sharding systems implement one of the approaches described
above, but you should also consider the business requirements of your
applications and their patterns of data usage. For example, in a
multi-tenant application:

-   You can shard data based on workload. You could segregate the data
    for highly volatile tenants in separate shards. The speed of data
    access for other tenants might be improved as a result.

-   You can shard data based on the location of tenants. You can take
    the data for tenants in a specific geographic region offline for
    backup and maintenance during off-peak hours in that region, while
    the data for tenants in other regions remains online and accessible
    during their business hours.

-   High-value tenants could be assigned their own private, high
    performing, lightly loaded shards, whereas lower-value tenants might
    be expected to share more densely-packed, busy shards.

-   The data for tenants that need a high degree of data isolation and
    privacy can be stored on a completely separate server.

Scaling and data movement operations 
------------------------------------

Each of the sharding strategies implies different capabilities and
levels of complexity for managing scale in, scale out, data movement,
and maintaining state.

The Lookup strategy permits scaling and data movement operations to be
carried out at the user level, either online or offline. The technique
is to suspend some or all user activity (perhaps during off-peak
periods), move the data to the new virtual partition or physical shard,
change the mappings, invalidate or refresh any caches that hold this
data, and then allow user activity to resume. Often this type of
operation can be centrally managed. The Lookup strategy requires state
to be highly cacheable and replica friendly.

The Range strategy imposes some limitations on scaling and data movement
operations, which must typically be carried out when a part or all of
the data store is offline because the data must be split and merged
across the shards. Moving the data to rebalance shards might not resolve
the problem of uneven load if the majority of activity is for adjacent
shard keys or data identifiers that are within the same range. The Range
strategy might also require some state to be maintained in order to map
ranges to the physical partitions.

The Hash strategy makes scaling and data movement operations more
complex because the partition keys are hashes of the shard keys or data
identifiers. The new location of each shard must be determined from the
hash function, or the function modified to provide the correct mappings.
However, the Hash strategy doesn\'t require maintenance of state.

#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

-   Sharding is complementary to other forms of partitioning, such as
    vertical partitioning and functional partitioning. For example, a
    single shard can contain entities that have been partitioned
    vertically, and a functional partition can be implemented as
    multiple shards. For more information about partitioning, see the 
    [Data Partitioning
    Guidance](https://msdn.microsoft.com/library/dn589795.aspx).

-   Keep shards balanced so they all handle a similar volume of I/O. As
    data is inserted and deleted, it\'s necessary to periodically
    rebalance the shards to guarantee an even distribution and to reduce
    the chance of hotspots. Rebalancing can be an expensive operation.
    To reduce the necessity of rebalancing, plan for growth by ensuring
    that each shard contains sufficient free space to handle the
    expected volume of changes. You should also develop strategies and
    scripts you can use to quickly rebalance shards if this becomes
    necessary.

-   Use stable data for the shard key. If the shard key changes, the
    corresponding data item might have to move between shards,
    increasing the amount of work performed by update operations. For
    this reason, avoid basing the shard key on potentially volatile
    information. Instead, look for attributes that are invariant or that
    naturally form a key.

-   Ensure that shard keys are unique. For example, avoid using
    autoincrementing fields as the shard key. Is some systems,
    autoincremented fields can\'t be coordinated across shards, possibly
    resulting in items in different shards having the same shard key.

    > Autoincremented values in other fields that are not shard keys can
    > also cause problems. For example, if you use autoincremented
    > fields to generate unique IDs, then two different items located in
    > different shards might be assigned the same ID.

-   It might not be possible to design a shard key that matches the
    requirements of every possible query against the data. Shard the
    data to support the most frequently performed queries, and if
    necessary create secondary index tables to support queries that
    retrieve data using criteria based on attributes that aren\'t part
    of the shard key. For more information, see the  [Index Table
    pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/index-table).

-   Queries that access only a single shard are more efficient than
    those that retrieve data from multiple shards, so avoid implementing
    a sharding system that results in applications performing large
    numbers of queries that join data held in different shards. Remember
    that a single shard can contain the data for multiple types of
    entities. Consider denormalizing your data to keep related entities
    that are commonly queried together (such as the details of customers
    and the orders that they have placed) in the same shard to reduce
    the number of separate reads that an application performs.

    > If an entity in one shard references an entity stored in another
    > shard, include the shard key for the second entity as part of the
    > schema for the first entity. This can help to improve the
    > performance of queries that reference related data across shards.

-   If an application must perform queries that retrieve data from
    multiple shards, it might be possible to fetch this data by using
    parallel tasks. Examples include fan-out queries, where data from
    multiple shards is retrieved in parallel and then aggregated into a
    single result. However, this approach inevitably adds some
    complexity to the data access logic of a solution.

-   For many applications, creating a larger number of small shards can
    be more efficient than having a small number of large shards because
    they can offer increased opportunities for load balancing. This can
    also be useful if you anticipate the need to migrate shards from one
    physical location to another. Moving a small shard is quicker than
    moving a large one.

-   Make sure the resources available to each shard storage node are
    sufficient to handle the scalability requirements in terms of data
    size and throughput. For more information, see the section
    "Designing Partitions for Scalability" in the  [Data Partitioning
    Guidance](https://msdn.microsoft.com/library/dn589795.aspx).

-   Consider replicating reference data to all shards. If an operation
    that retrieves data from a shard also references static or
    slow-moving data as part of the same query, add this data to the
    shard. The application can then fetch all of the data for the query
    easily, without having to make an additional round trip to a
    separate data store.

    > If reference data held in multiple shards changes, the system must
    > synchronize these changes across all shards. The system can
    > experience a degree of inconsistency while this synchronization
    > occurs. If you do this, you should design your applications to be
    > able to handle it.

-   It can be difficult to maintain referential integrity and
    consistency between shards, so you should minimize operations that
    affect data in multiple shards. If an application must modify data
    across shards, evaluate whether complete data consistency is
    actually required. Instead, a common approach in the cloud is to
    implement eventual consistency. The data in each partition is
    updated separately, and the application logic must take
    responsibility for ensuring that the updates all complete
    successfully, as well as handling the inconsistencies that can arise
    from querying data while an eventually consistent operation is
    running. For more information about implementing eventual
    consistency, see the  [Data Consistency
    Primer](https://msdn.microsoft.com/library/dn589800.aspx).

-   Configuring and managing a large number of shards can be a
    challenge. Tasks such as monitoring, backing up, checking for
    consistency, and logging or auditing must be accomplished on
    multiple shards and servers, possibly held in multiple locations.
    These tasks are likely to be implemented using scripts or other
    automation solutions, but that might not completely eliminate the
    additional administrative requirements.

-   Shards can be geolocated so that the data that they contain is close
    to the instances of an application that use it. This approach can
    considerably improve performance, but requires additional
    consideration for tasks that must access multiple shards in
    different locations.

#### When to use this Pattern

Use this pattern when a data store is likely to need to scale beyond the
resources available to a single storage node, or to improve performance
by reducing contention in a data store.

The primary focus of sharding is to improve the performance and
scalability of a system, but as a by-product it can also improve
availability due to how the data is divided into separate partitions. A
failure in one partition doesn\'t necessarily prevent an application
from accessing data held in other partitions, and an operator can
perform maintenance or recovery of one or more partitions without making
the entire data for an application inaccessible. For more information,
see the  [Data Partitioning Guidance](https://msdn.microsoft.com/library/dn589795.aspx).


### Sidecar Pattern

#### Overview

Deploy components of an application into a separate process or container
to provide isolation and encapsulation. This pattern can also enable
applications to be composed of heterogeneous components and
technologies.

This pattern is named  *Sidecar* because it resembles a sidecar attached
to a motorcycle. In the pattern, the sidecar is attached to a parent
application and provides supporting features for the application. The
sidecar also shares the same lifecycle as the parent application, being
created and retired alongside the parent. The sidecar pattern is
sometimes referred to as the sidekick pattern and is a decomposition
pattern.

#### Context and Problem

Applications and services often require related functionality, such as
monitoring, logging, configuration, and networking services. These
peripheral tasks can be implemented as separate components or services.

If they are tightly integrated into the application, they can run in the
same process as the application, making efficient use of shared
resources. However, this also means they are not well isolated, and an
outage in one of these components can affect other components or the
entire application. Also, they usually need to be implemented using the
same language as the parent application. As a result, the component and
the application have close interdependence on each other.

If the application is decomposed into services, then each service can be
built using different languages and technologies. While this gives more
flexibility, it means that each component has its own dependencies and
requires language-specific libraries to access the underlying platform
and any resources shared with the parent application. In addition,
deploying these features as separate services can add latency to the
application. Managing the code and dependencies for these
language-specific interfaces can also add considerable complexity,
especially for hosting, deployment, and management.

#### Solution

Co-locate a cohesive set of tasks with the primary application, but
place them inside their own process or container, providing a
homogeneous interface for platform services across languages.

<img src="./attachments/463533405.png" alt="">

A sidecar service is not necessarily part of the application, but is
connected to it. It goes wherever the parent application goes. Sidecars
are supporting processes or services that are deployed with the primary
application. On a motorcycle, the sidecar is attached to one motorcycle,
and each motorcycle can have its own sidecar. In the same way, a sidecar
service shares the fate of its parent application. For each instance of
the application, an instance of the sidecar is deployed and hosted
alongside it.

Advantages of using a sidecar pattern include:

-   A sidecar is independent from its primary application in terms of
    runtime environment and programming language, so you don\'t need to
    develop one sidecar per language.

-   The sidecar can access the same resources as the primary
    application. For example, a sidecar can monitor system resources
    used by both the sidecar and the primary application.

-   Because of its proximity to the primary application, there's no
    significant latency when communicating between them.

-   Even for applications that don't provide an extensibility mechanism,
    you can use a sidecar to extend functionality by attaching it as its
    own process in the same host or sub-container as the primary
    application.

The sidecar pattern is often used with containers and referred to as a
sidecar container or sidekick container.

#### Issues and Considerations

-   Consider the deployment and packaging format you will use to deploy
    services, processes, or containers. Containers are particularly well
    suited to the sidecar pattern.
-   When designing a sidecar service, carefully decide on the
    interprocess communication mechanism. Try to use language- or
    framework-agnostic technologies unless performance requirements make
    that impractical.
-   Before putting functionality into a sidecar, consider whether it
    would work better as a separate service or a more traditional
    daemon.
-   Also consider whether the functionality could be implemented as a
    library or using a traditional extension mechanism.
    Language-specific libraries may have a deeper level of integration
    and less network overhead.

#### When to use this Pattern

Use this pattern when:

-   Your primary application uses a heterogeneous set of languages and
    frameworks. A component located in a sidecar service can be consumed
    by applications written in different languages using different
    frameworks.
-   A component is owned by a remote team or a different organization.
-   A component or feature must be co-located on the same host as the
    application
-   You need a service that shares the overall lifecycle of your main
    application, but can be independently updated.
-   You need fine-grained control over resource limits for a particular
    resource or component. For example, you may want to restrict the
    amount of memory a specific component uses. You can deploy the
    component as a sidecar and manage memory usage independently of the
    main application.

This pattern may not be suitable:

-   When interprocess communication needs to be optimized. Communication
    between a parent application and sidecar services includes some
    overhead, notably latency in the calls. This may not be an
    acceptable trade-off for chatty interfaces.
-   For small applications where the resource cost of deploying a
    sidecar service for each instance is not worth the advantage of
    isolation.
-   When the service needs to scale differently than or independently
    from the main applications. If so, it may be better to deploy the
    feature as a separate service.

### Static Content Hosting Pattern

#### Overview

Deploy static content to a cloud-based storage service that can deliver
them directly to the client. This can reduce the need for potentially
expensive compute instances.

#### Context and Problem

Web applications typically include some elements of static content. This
static content might include HTML pages and other resources such as
images and documents that are available to the client, either as part of
an HTML page (such as inline images, style sheets, and client-side
JavaScript files) or as separate downloads (such as PDF documents).

Although web servers are optimized for dynamic rendering and output
caching, they still have to handle requests to download static content.
This consumes processing cycles that could often be put to better use.

#### Solution

In most cloud hosting environments, you can put some of an
application\'s resources and static pages in a storage service. The
storage service can serve requests for these resources, reducing load on
the compute resources that handle other web requests. The cost for
cloud-hosted storage is typically much less than for compute instances.

When hosting some parts of an application in a storage service, the main
considerations are related to deployment of the application and to
securing resources that aren\'t intended to be available to anonymous
users.

#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

-   The hosted storage service must expose an HTTP endpoint that users
    can access to download the static resources. Some storage services
    also support HTTPS, so it\'s possible to host resources in storage
    services that require SSL.

-   For maximum performance and availability, consider using a content
    delivery network (CDN) to cache the contents of the storage
    container in multiple datacenters around the world. However, you\'ll
    likely have to pay for using the CDN.

-   Storage accounts are often geo-replicated by default to provide
    resiliency against events that might affect a datacenter. This means
    that the IP address might change, but the URL will remain the same.

-   When some content is located in a storage account and other content
    is in a hosted compute instance, it becomes more challenging to
    deploy and update the application. You might have to perform
    separate deployments, and version the application and content to
    manage it more easily---especially when the static content includes
    script files or UI components. However, if only static resources
    have to be updated, they can simply be uploaded to the storage
    account without needing to redeploy the application package.

-   Storage services might not support the use of custom domain names.
    In this case it\'s necessary to specify the full URL of the
    resources in links because they\'ll be in a different domain from
    the dynamically-generated content containing the links.

-   The storage containers must be configured for public read access,
    but it\'s vital to ensure that they aren\'t configured for public
    write access to prevent users being able to upload content.

-   Consider using a valet key or token to control access to resources
    that shouldn\'t be available anonymously. See the 
    [Valet Key pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/valet-key) for
    more information.

#### When to use this Pattern

This pattern is useful for:

-   Minimizing the hosting cost for websites and applications that
    contain some static resources.

-   Minimizing the hosting cost for websites that consist of only static
    content and resources. Depending on the capabilities of the hosting
    provider\'s storage system, it might be possible to entirely host a
    fully static website in a storage account.

-   Exposing static resources and content for applications running in
    other hosting environments or on-premises servers.

-   Locating content in more than one geographical area using a content
    delivery network that caches the contents of the storage account in
    multiple datacenters around the world.

-   Monitoring costs and bandwidth usage. Using a separate storage
    account for some or all of the static content allows the costs to be
    more easily separated from hosting and runtime costs.

This pattern might not be useful in the following situations:

-   The application needs to perform some processing on the static
    content before delivering it to the client. For example, it might be
    necessary to add a timestamp to a document.

-   The volume of static content is very small. The overhead of
    retrieving this content from separate storage can outweigh the cost
    benefit of separating it out from the compute resource.

### Strangler Pattern

#### Overview

Incrementally migrate a legacy system by gradually replacing specific
pieces of functionality with new applications and services. As features
from the legacy system are replaced, the new system eventually replaces
all of the old system\'s features, strangling the old system and
allowing you to decommission it.

#### Context and Problem

As systems age, the development tools, hosting technology, and even
system architectures they were built on can become increasingly
obsolete. As new features and functionality are added, the complexity of
these applications can increase dramatically, making them harder to
maintain or add new features to.

Completely replacing a complex system can be a huge undertaking. Often,
you will need a gradual migration to a new system, while keeping the old
system to handle features that haven\'t been migrated yet. However,
running two separate versions of an application means that clients have
to know where particular features are located. Every time a feature or
service is migrated, clients need to be updated to point to the new
location.

#### Solution

Incrementally replace specific pieces of functionality with new
applications and services. Create a façade that intercepts requests
going to the backend legacy system. The façade routes these requests
either to the legacy application or the new services. Existing features
can be migrated to the new system gradually, and consumers can continue
using the same interface, unaware that any migration has taken place.

<img src="./attachments/463533408.png" alt="">

This pattern helps to minimize risk from the migration, and spread the
development effort over time. With the façade safely routing users to
the correct application, you can add functionality to the new system at
whatever pace you like, while ensuring the legacy application continues
to function. Over time, as features are migrated to the new system, the
legacy system is eventually \"strangled\" and is no longer necessary.
Once this process is complete, the legacy system can safely be retired.

#### Issues and Considerations

-   Consider how to handle services and data stores that are potentially
    used by both new and legacy systems. Make sure both can access these
    resources side-by-side.
-   Structure new applications and services in a way that they can
    easily be intercepted and replaced in future strangler migrations.
-   At some point, when the migration is complete, the strangler façade
    will either go away or evolve into an adaptor for legacy clients.
-   Make sure the façade keeps up with the migration.
-   Make sure the façade doesn\'t become a single point of failure or a
    performance bottleneck.

#### When to use this Pattern

Use this pattern when gradually migrating a back-end application to a new architecture.

This pattern may not be suitable:

-   When requests to the back-end system cannot be intercepted.
-   For smaller systems where the complexity of wholesale replacement is low.

### Throttling Pattern

#### Overview

Control the consumption of resources used by an instance of an
application, an individual tenant, or an entire service. This can allow
the system to continue to function and meet service level agreements,
even when an increase in demand places an extreme load on resources.

#### Context and Problem

The load on a cloud application typically varies over time based on the
number of active users or the types of activities they are performing.
For example, more users are likely to be active during business hours,
or the system might be required to perform computationally expensive
analytics at the end of each month. There might also be sudden and
unanticipated bursts in activity. If the processing requirements of the
system exceed the capacity of the resources that are available, it\'ll
suffer from poor performance and can even fail. If the system has to
meet an agreed level of service, such failure could be unacceptable.

There\'re many strategies available for handling varying load in the
cloud, depending on the business goals for the application. One strategy
is to use autoscaling to match the provisioned resources to the user
needs at any given time. This has the potential to consistently meet
user demand, while optimizing running costs. However, while autoscaling
can trigger the provisioning of additional resources, this provisioning
isn\'t immediate. If demand grows quickly, there can be a window of time
where there\'s a resource deficit.

#### Solution

An alternative strategy to autoscaling is to allow applications to use
resources only up to a limit, and then throttle them when this limit is
reached. The system should monitor how it\'s using resources so that,
when usage exceeds the threshold, it can throttle requests from one or
more users. This will enable the system to continue functioning and meet
any service level agreements (SLAs) that are in place. For more
information on monitoring resource usage, see the  [Instrumentation and
Telemetry
Guidance](https://msdn.microsoft.com/library/dn589775.aspx).

The system could implement several throttling strategies, including:

-   Rejecting requests from an individual user who\'s already accessed
    system APIs more than n times per second over a given period of
    time. This requires the system to meter the use of resources for
    each tenant or user running an application. For more information,
    see the  [Service Metering
    Guidance](https://msdn.microsoft.com/library/dn589796.aspx).

-   Disabling or degrading the functionality of selected nonessential
    services so that essential services can run unimpeded with
    sufficient resources. For example, if the application is streaming
    video output, it could switch to a lower resolution.

-   Using load leveling to smooth the volume of activity (this approach
    is covered in more detail by the  [Queue-based Load Leveling
    pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/queue-based-load-leveling)).
    In a multi-tenant environment, this approach will reduce the
    performance for every tenant. If the system must support a mix of
    tenants with different SLAs, the work for high-value tenants might
    be performed immediately. Requests for other tenants can be held
    back, and handled when the backlog has eased. The  [Priority Queue
    pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/priority-queue) could
    be used to help implement this approach.

-   Deferring operations being performed on behalf of lower priority
    applications or tenants. These operations can be suspended or
    limited, with an exception generated to inform the tenant that the
    system is busy and that the operation should be retried later.

The figure shows an area graph for resource use (a combination of
memory, CPU, bandwidth, and other factors) against time for applications
that are making use of three features. A feature is an area of
functionality, such as a component that performs a specific set of
tasks, a piece of code that performs a complex calculation, or an
element that provides a service such as an in-memory cache. These
features are labeled A, B, and C.

<img src="./attachments/463533410.png" alt="">

> The area immediately below the line for a feature indicates the
> resources that are used by applications when they invoke this feature.
> For example, the area below the line for Feature A shows the resources
> used by applications that are making use of Feature A, and the area
> between the lines for Feature A and Feature B indicates the resources
> used by applications invoking Feature B. Aggregating the areas for
> each feature shows the total resource use of the system.

The previous figure illustrates the effects of deferring operations.
Just prior to time T1, the total resources allocated to all applications
using these features reach a threshold (the limit of resource use). At
this point, the applications are in danger of exhausting the resources
available. In this system, Feature B is less critical than Feature A or
Feature C, so it\'s temporarily disabled and the resources that it was
using are released. Between times T1 and T2, the applications using
Feature A and Feature C continue running as normal. Eventually, the
resource use of these two features diminishes to the point when, at time
T2, there is sufficient capacity to enable Feature B again.

The autoscaling and throttling approaches can also be combined to help
keep the applications responsive and within SLAs. If the demand is
expected to remain high, throttling provides a temporary solution while
the system scales out. At this point, the full functionality of the
system can be restored.

The next figure shows an area graph of the overall resource use by all
applications running in a system against time, and illustrates how
throttling can be combined with autoscaling.

<img src="./attachments/463533411.png" alt="">

At time T1, the threshold specifying the soft limit of resource use is
reached. At this point, the system can start to scale out. However, if
the new resources don\'t become available quickly enough, then the
existing resources might be exhausted and the system could fail. To
prevent this from occurring, the system is temporarily throttled, as
described earlier. When autoscaling has completed and the additional
resources are available, throttling can be relaxed.

#### Issues and Considerations

You should consider the following points when deciding how to implement
this pattern:

-   Throttling an application, and the strategy to use, is an
    architectural decision that impacts the entire design of a system.
    Throttling should be considered early in the application design
    process because it isn\'t easy to add once a system has been
    implemented.

-   Throttling must be performed quickly. The system must be capable of
    detecting an increase in activity and react accordingly. The system
    must also be able to revert to its original state quickly after the
    load has eased. This requires that the appropriate performance data
    is continually captured and monitored.

-   If a service needs to temporarily deny a user request, it should
    return a specific error code so the client application understands
    that the reason for the refusal to perform an operation is due to
    throttling. The client application can wait for a period before
    retrying the request.

-   Throttling can be used as a temporary measure while a system
    autoscales. In some cases it\'s better to simply throttle, rather
    than to scale, if a burst in activity is sudden and isn\'t expected
    to be long lived because scaling can add considerably to running
    costs.

-   If throttling is being used as a temporary measure while a system
    autoscales, and if resource demands grow very quickly, the system
    might not be able to continue functioning---even when operating in a
    throttled mode. If this isn\'t acceptable, consider maintaining
    larger capacity reserves and configuring more aggressive
    autoscaling.

#### When to use this Pattern

Use this pattern:

-   To ensure that a system continues to meet service level agreements.
-   To prevent a single tenant from monopolizing the resources provided by an application.
-   To handle bursts in activity.
-   To help cost-optimize a system by limiting the maximum resource levels needed to keep it functioning.

### Valet Key Pattern

#### Overview

Use a token that provides clients with restricted direct access to a
specific resource, in order to offload data transfer from the
application. This is particularly useful in applications that use
cloud-hosted storage systems or queues, and can minimize cost and
maximize scalability and performance.

#### Context and Problem

Client programs and web browsers often need to read and write files or
data streams to and from an application's storage. Typically, the
application will handle the movement of the data --- either by fetching
it from storage and streaming it to the client, or by reading the
uploaded stream from the client and storing it in the data store.
However, this approach absorbs valuable resources such as compute,
memory, and bandwidth.

Data stores have the ability to handle upload and download of data
directly, without requiring that the application perform any processing
to move this data. But, this typically requires the client to have
access to the security credentials for the store. This can be a useful
technique to minimize data transfer costs and the requirement to scale
out the application, and to maximize performance. It means, though, that
the application is no longer able to manage the security of the data.
After the client has a connection to the data store for direct access,
the application can\'t act as the gatekeeper. It\'s no longer in control
of the process and can\'t prevent subsequent uploads or downloads from
the data store.

This isn\'t a realistic approach in distributed systems that need to
serve untrusted clients. Instead, applications must be able to securely
control access to data in a granular way, but still reduce the load on
the server by setting up this connection and then allowing the client to
communicate directly with the data store to perform the required read or
write operations.

#### Solution

You need to resolve the problem of controlling access to a data store
where the store can\'t manage authentication and authorization of
clients. One typical solution is to restrict access to the data store's
public connection and provide the client with a key or token that the
data store can validate.

This key or token is usually referred to as a valet key. It provides
time-limited access to specific resources and allows only predefined
operations such as reading and writing to storage or queues, or
uploading and downloading in a web browser. Applications can create and
issue valet keys to client devices and web browsers quickly and easily,
allowing clients to perform the required operations without requiring
the application to directly handle the data transfer. This removes the
processing overhead, and the impact on performance and scalability, from
the application and the server.

The client uses this token to access a specific resource in the data
store for only a specific period, and with specific restrictions on
access permissions, as shown in the figure. After the specified period,
the key becomes invalid and won\'t allow access to the resource.

<img src="./attachments/463533413.png" alt="">

It\'s also possible to configure a key that has other dependencies, such
as the scope of the data. For example, depending on the data store
capabilities, the key can specify a complete table in a data store, or
only specific rows in a table. In cloud storage systems the key can
specify a container, or just a specific item within a container.

The key can also be invalidated by the application. This is a useful
approach if the client notifies the server that the data transfer
operation is complete. The server can then invalidate that key to
prevent further access.

Using this pattern can simplify managing access to resources because
there\'s no requirement to create and authenticate a user, grant
permissions, and then remove the user again. It also makes it easy to
limit the location, the permission, and the validity period---all by
simply generating a key at runtime. The important factors are to limit
the validity period, and especially the location of the resource, as
tightly as possible so that the recipient can only use it for the
intended purpose.

#### Issues and Considerations

Consider the following points when deciding how to implement this
pattern:

**Manage the validity status and period of the key**. If leaked or
compromised, the key effectively unlocks the target item and makes it
available for malicious use during the validity period. A key can
usually be revoked or disabled, depending on how it was issued.
Server-side policies can be changed or, the server key it was signed
with can be invalidated. Specify a short validity period to minimize the
risk of allowing unauthorized operations to take place against the data
store. However, if the validity period is too short, the client might
not be able to complete the operation before the key expires. Allow
authorized users to renew the key before the validity period expires if
multiple accesses to the protected resource are required.

**Control the level of access the key will provide**. Typically, the key
should allow the user to only perform the actions necessary to complete
the operation, such as read-only access if the client shouldn\'t be able
to upload data to the data store. For file uploads, it\'s common to
specify a key that provides write-only permission, as well as the
location and the validity period. It\'s critical to accurately specify
the resource or the set of resources to which the key applies.

**Consider how to control users' behavior**. Implementing this pattern
means some loss of control over the resources users are granted access
to. The level of control that can be exerted is limited by the
capabilities of the policies and permissions available for the service
or the target data store. For example, it\'s usually not possible to
create a key that limits the size of the data to be written to storage,
or the number of times the key can be used to access a file. This can
result in huge unexpected costs for data transfer, even when used by the
intended client, and might be caused by an error in the code that causes
repeated upload or download. To limit the number of times a file can be
uploaded, where possible, force the client to notify the application
when one operation has completed. For example, some data stores raise
events the application code can use to monitor operations and control
user behavior. However, it\'s hard to enforce quotas for individual
users in a multi-tenant scenario where the same key is used by all the
users from one tenant.

**Validate, and optionally sanitize, all uploaded data**. A malicious
user that gains access to the key could upload data designed to
compromise the system. Alternatively, authorized users might upload data
that\'s invalid and, when processed, could result in an error or system
failure. To protect against this, ensure that all uploaded data is
validated and checked for malicious content before use.

**Audit all operations**. Many key-based mechanisms can log operations
such as uploads, downloads, and failures. These logs can usually be
incorporated into an audit process, and also used for billing if the
user is charged based on file size or data volume. Use the logs to
detect authentication failures that might be caused by issues with the
key provider, or accidental removal of a stored access policy.

**Deliver the key securely**. It can be embedded in a URL that the user
activates in a web page, or it can be used in a server redirection
operation so that the download occurs automatically. Always use HTTPS to
deliver the key over a secure channel.

**Protect sensitive data in transit**. Sensitive data delivered through
the application will usually take place using SSL or TLS, and this
should be enforced for clients accessing the data store directly.

Other issues to be aware of when implementing this pattern are:

-   If the client doesn\'t, or can\'t, notify the server of completion
    of the operation, and the only limit is the expiration period of the
    key, the application won\'t be able to perform auditing operations
    such as counting the number of uploads or downloads, or preventing
    multiple uploads or downloads.

-   The flexibility of key policies that can be generated might be
    limited. For example, some mechanisms only allow the use of a timed
    expiration period. Others aren\'t able to specify a sufficient
    granularity of read/write permissions.

-   If the start time for the key or token validity period is specified,
    ensure that it\'s a little earlier than the current server time to
    allow for client clocks that might be slightly out of
    synchronization. The default, if not specified, is usually the
    current server time.

-   The URL containing the key will be recorded in server log files.
    While the key will typically have expired before the log files are
    used for analysis, ensure that you limit access to them. If log data
    is transmitted to a monitoring system or stored in another location,
    consider implementing a delay to prevent leakage of keys until after
    their validity period has expired.

-   If the client code runs in a web browser, the browser might need to
    support cross-origin resource sharing (CORS) to enable code that
    executes within the web browser to access data in a different domain
    from the one that served the page. Some older browsers and some data
    stores don\'t support CORS, and code that runs in these browsers
    might not be able to use a valet key to provide access to data in a
    different domain, such as a cloud storage account.

#### When to use this Pattern

This pattern is useful for the following situations:

-   To minimize resource loading and maximize performance and
    scalability. Using a valet key doesn\'t require the resource to be
    locked, no remote server call is required, there\'s no limit on the
    number of valet keys that can be issued, and it avoids a single
    point of failure resulting from performing the data transfer through
    the application code. Creating a valet key is typically a simple
    cryptographic operation of signing a string with a key.

-   To minimize operational cost. Enabling direct access to stores and
    queues is resource and cost efficient, can result in fewer network
    round trips, and might allow for a reduction in the number of
    compute resources required.

-   When clients regularly upload or download data, particularly where
    there\'s a large volume or when each operation involves large files.

-   When the application has limited compute resources available, either
    due to hosting limitations or cost considerations. In this scenario,
    the pattern is even more helpful if there are many concurrent data
    uploads or downloads because it relieves the application from
    handling the data transfer.

-   When the data is stored in a remote data store or a different
    datacenter. If the application was required to act as a gatekeeper,
    there might be a charge for the additional bandwidth of transferring
    the data between datacenters, or across public or private networks
    between the client and the application, and then between the
    application and the data store.

This pattern might not be useful in the following situations:

-   If the application must perform some task on the data before it\'s
    stored or before it\'s sent to the client. For example, if the
    application needs to perform validation, log access success, or
    execute a transformation on the data. However, some data stores and
    clients are able to negotiate and carry out simple transformations
    such as compression and decompression (for example, a web browser
    can usually handle GZip formats).

-   If the design of an existing application makes it difficult to
    incorporate the pattern. Using this pattern typically requires a
    different architectural approach for delivering and receiving data.

-   If it\'s necessary to maintain audit trails or control the number of
    times a data transfer operation is executed, and the valet key
    mechanism in use doesn\'t support notifications that the server can
    use to manage these operations.

-   If it\'s necessary to limit the size of the data, especially during
    upload operations. The only solution to this is for the application
    to check the data size after the operation is complete, or check the
    size of uploads after a specified period or on a scheduled basis.

References

-   [MS Doc - architecture patterns](https://docs.microsoft.com/en-us/azure/architecture/patterns/)


 



