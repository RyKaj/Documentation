[comment]: [Architecture](ReadMe.MD)

Infrastructure Architecture - Serverless Architecture
===================================================


 
![Diagram showing a comparison of virtual machines, containers, and
serverless
computing](https://docs.microsoft.com/en-us/learn/modules/principles-cloud-computing/media/2-vm-vs-container-vs-serverless.png)

Overview
--------

Serverless architectures are application designs that incorporate
third-party "Backend as a Service" (BaaS) services, and/or that include
custom code run in managed, ephemeral containers on a "Functions as a
Service" (FaaS) platform. By using these ideas, and related ones like
single-page applications, such architectures remove much of the need for
a traditional always-on server component. Serverless architectures may
benefit from significantly reduced operational cost, complexity, and
engineering lead time, at a cost of increased reliance on vendor
dependencies and comparatively immature supporting services.

Like many trends in software, there's no one clear view of what
Serverless is. For starters, it encompasses two different but
overlapping areas:

1.  Serverless was first used to describe applications that
    significantly or fully incorporate third-party, cloud-hosted
    applications and services, to manage server-side logic and state.
    These are typically "rich client" applications---think single-page
    web apps, or mobile apps---that use the vast ecosystem of
    cloud-accessible databases (e.g., Parse, Firebase), authentication
    services (e.g., Auth0, AWS Cognito), and so on. These types of
    services have been previously described as " [(Mobile) Backend as a
    Service](https://en.wikipedia.org/wiki/Mobile_backend_as_a_service)\",
    and I use  **\"BaaS\"** as shorthand in the rest of this article.
2.  Serverless can also mean applications where server-side logic is
    still written by the application developer, but, unlike traditional
    architectures, it's run in stateless compute containers that are
    event-triggered, ephemeral (may only last for one invocation), and
    fully managed by a third party. One way to think of this is
    "Functions as a Service" or  **\"FaaS\"**. (Note: The  [original
    source](https://twitter.com/marak/status/736357543598002176) for
    this name---a tweet by \@marak---is no longer publicly available.) 
    [AWS Lambda](https://aws.amazon.com/lambda/) is one
    of the most popular implementations of a Functions-as-a-Service
    platform at present, but there are many others, too.

BaaS and FaaS are related in their operational attributes (e.g., no
resource management) and are frequently used together. The large cloud
vendors all have "Serverless portfolios" that include both BaaS and FaaS
products---for example,  [here's Amazon's
Serverless](https://aws.amazon.com/serverless/) product
page. Google's Firebase BaaS database has explicit FaaS support through 
[Google Cloud Functions for
Firebase.](https://firebase.google.com/docs/functions/)

There is similar linking of the two areas from smaller companies too. 
[Auth0](https://auth0.com/) started with a BaaS product
that implemented many facets of user management, and subsequently
created the companion FaaS service 
[Webtask](https://webtask.io/). The company have taken
this idea even further with 
[Extend](https://auth0.com/extend/), which enables other
SaaS and BaaS companies to easily add a FaaS capability to existing
products so they can create a unified Serverless product.

UI-Driven Application
---------------------

Let's think about a traditional three-tier client-oriented system with
server-side logic. A good example is a typical ecommerce app---dare I
say an online pet store?

Traditionally, the architecture will look something like the diagram
below. Let's say it's implemented in Java or Javascript on the server
side, with an HTML + Javascript component as the client:

With this architecture the client can be relatively unintelligent, with
much of the logic in the system---authentication, page navigation,
searching, transactions---implemented by the server application.

With a Serverless architecture this may end up looking more like this:

This is a massively simplified view, but even here we see a number of
significant changes:

1.  We've deleted the authentication logic in the original application
    and have replaced it with a third-party BaaS service (e.g., Auth0.)
2.  Using another example of BaaS, we've allowed the client direct
    access to a subset of our database (for product listings), which
    itself is fully hosted by a third party (e.g., Google Firebase.) We
    likely have a different security profile for the client accessing
    the database in this way than for server resources that access the
    database.
3.  These previous two points imply a very important third: some logic
    that was in the Pet Store server is now within the client---e.g.,
    keeping track of a user session, understanding the UX structure of
    the application, reading from a database and translating that into a
    usable view, etc. The client is well on its way to becoming a 
    [Single Page
    Application](https://en.wikipedia.org/wiki/Single-page_application).
4.  We may want to keep some UX-related functionality in the server, if,
    for example, it's compute intensive or requires access to
    significant amounts of data. In our pet store, an example is
    "search." Instead of having an always-running server, as existed in
    the original architecture, we can instead implement a FaaS function
    that responds to HTTP requests via an API gateway (described later).
    Both the client and the server "search" function read from the same
    database for product data.

If we choose to use AWS Lambda as our FaaS platform we can port the
search code from the original Pet Store server to the new Pet Store
Search function without a complete rewrite, since Lambda supports Java
and Javascript---our original implementation languages.

1.  Finally, we may replace our "purchase" functionality with another
    separate FaaS function, choosing to keep it on the server side for
    security reasons, rather than reimplement it in the client. It too
    is fronted by an API gateway. Breaking up different logical
    requirements into separately deployed components is a very common
    approach when using FaaS.

Stepping back a little, this example demonstrates another very important
point about Serverless architectures. In the original version, all flow,
control, and security was managed by the central server application. In
the Serverless version there is no central arbiter of these concerns.
Instead we see a preference for  **choreography over orchestration**,
with each component playing a more architecturally aware role---an idea
also common in a microservices approach.

There are many benefits to such an approach. As Sam Newman notes in his 
*[Building
Microservices](https://samnewman.io/books/building_microservices/)*
 book, systems built this way are often "more flexible and amenable to
change," both as a whole and through independent updates to components;
there is better division of concerns; and there are also some
fascinating cost benefits, a point that Gojko Adzic discusses in  [this
excellent
talk](https://gojko.net/2017/10/05/serverless-design-gotocph.html).

Of course, such a design is a trade-off: it requires better distributed
monitoring (more on this later), and we rely more significantly on the
security capabilities of the underlying platform. More fundamentally,
there are a greater number of moving pieces to get our heads around than
there are with the monolithic application we had originally. Whether the
benefits of flexibility and cost are worth the added complexity of
multiple backend components is very context dependent.

Message-driven applications
---------------------------

A different example is a backend data-processing service.

Say you're writing a user-centric application that needs to quickly
respond to UI requests, and, secondarily, it needs to capture all the
different types of user activity that are occurring, for subsequent
processing. Think about an online advertisement system: when a user
clicks on an ad you want to very quickly redirect them to the target of
that ad. At the same time, you need to collect the fact that the click
has happened so that you can charge the advertiser. (This example is not
hypothetical---my former team at  [Intent
Media](http://www.intentmedia.com/) had exactly this
need, which they implemented in a Serverless way.)

Traditionally, the architecture may look as below. The "Ad Server"
synchronously responds to the user (not shown) and also posts a "click
message" to a channel. This message is then asynchronously processed by
a "click processor" application that updates a database, e.g., to
decrement the advertiser's budget.

In the Serverless world this looks as follows:

Can you see the difference? The change in architecture is much smaller
here compared to our first example---this is why asynchronous message
processing is a very popular use case for Serverless technologies. We've
replaced a long-lived message-consumer  *application* with a FaaS 
*function*. This function runs within the event-driven context the
vendor provides. Note that the cloud platform vendor supplies both the
message broker  *and* the FaaS environment---the two systems are closely
tied to each other.

The FaaS environment may also process several messages in parallel by
instantiating multiple copies of the function code. Depending on how we
wrote the original process this may be a new concept we need to
consider.

Unpacking \"Function as a Service\"
-----------------------------------

We\'ve mentioned FaaS a lot already, but it\'s time to dig into what it
really means. To do this let\'s look at the  [opening
description](https://aws.amazon.com/lambda/) for
Amazon\'s FaaS product: Lambda. I\'ve added some tokens to it, which
I'll expand on.

> AWS Lambda lets you run code without provisioning or managing
> servers.  **(1)** \... With Lambda, you can run code for virtually any
> type of application or backend service  **(2)** - all with zero
> administration. Just upload your code and Lambda takes care of
> everything required to run  **(3)** and scale  **(4)** your code with
> high availability. You can set up your code to automatically trigger
> from other AWS services  **(5)** or call it directly from any web or
> mobile app  **(6)**.

-   **Fundamentally, FaaS is about running backend code without managing
    your own server systems or your own long-lived server
    applications.** That second clause---long-lived server
    applications---is a key difference when comparing with other modern
    architectural trends like containers and PaaS (Platform as a
    Service).

If we go back to our click-processing example from earlier, FaaS
replaces the click-processing server (possibly a physical machine, but
definitely a specific application) with something that doesn't need a
provisioned server, nor an application that is running all the time.

-   FaaS offerings do not require coding to a specific framework or
    library. FaaS functions are regular applications when it comes to
    language and environment. For instance, AWS Lambda functions can be
    implemented "first class" in Javascript, Python, Go, any JVM
    language (Java, Clojure, Scala, etc.), or any .NET language. However
    your Lambda function can also execute another process that is
    bundled with its deployment artifact, so you can actually use any
    language that can compile down to a Unix process (see Apex, later in
    this article).

FaaS functions have significant architectural restrictions though,
especially when it comes to state and execution duration. We'll get to
that soon.

Let's consider our click-processing example again. The only code that
needs to change when moving to FaaS is the "main method" (startup) code,
in that it is deleted, and likely the specific code that is the
top-level message handler (the "message listener interface"
implementation), but this might only be a change in method signature.
The rest of the code (e.g., the code that writes to the database) is no
different in a FaaS world.

1.  Deployment is very different from traditional systems since we have
    no server applications to run ourselves. In a FaaS environment we
    upload the code for our function to the FaaS provider, and the
    provider does everything else necessary for provisioning resources,
    instantiating VMs, managing processes, etc.
2.  Horizontal scaling is completely automatic, elastic, and managed by
    the provider. If your system needs to be processing 100 requests in
    parallel the provider will handle that without any extra
    configuration on your part. The "compute containers" executing your
    functions are ephemeral, with the FaaS provider creating and
    destroying them purely driven by runtime need. Most importantly,
    with FaaS  **the vendor handles all underlying resource provisioning
    and allocation**---no cluster or VM management is required by the
    user at all.

Let's return to our click processor. Say that we were having a good day
and customers were clicking on ten times as many ads as usual. For the
traditional architecture, would our click-processing application be able
to handle this? For example, did we develop our application to be able
to handle multiple messages at a time? If we did, would one running
instance of the application be enough to process the load? If we are
able to run multiple processes, is autoscaling automatic or do we need
to reconfigure that manually? With a FaaS approach all of these
questions are already answered---you need to write the function ahead of
time to assume horizontal-scaled parallelism, but from that point on the
FaaS provider automatically handles all scaling needs.

1.  Functions in FaaS are typically triggered by event types defined by
    the provider. With Amazon AWS such stimuli include S3 (file/object)
    updates, time (scheduled tasks), and messages added to a message bus
    (e.g.,  [Kinesis](https://aws.amazon.com/kinesis/)).
2.  Most providers also allow functions to be triggered as a response to
    inbound HTTP requests; in AWS one typically enables this by way of
    using an API gateway. We used an API gateway in our Pet Store
    example for our "search" and "purchase" functions. Functions can
    also be invoked directly via a platform-provided API, either
    externally or from within the same cloud environment, but this is a
    comparatively uncommon use.

State
-----

FaaS functions have significant restrictions when it comes to local
(machine/instance-bound) state---i.e., data that you store in variables
in memory, or data that you write to local disk. You do have such
storage available, but you have no guarantee that such state is
persisted across multiple invocations, and, more strongly, you should
not assume that state from one invocation of a function will be
available to another invocation of the same function. FaaS functions are
therefore often described as stateless, but it's more accurate to say
that any state of a FaaS function that is required to be 
**persistent** needs to be  **externalized** outside of the FaaS
function instance.

For FaaS functions that are naturally stateless---i.e., those that
provide a purely functional transformation of their input to their
output---this is of no concern. But for others this can have a large
impact on application architecture, albeit not a unique one---the "
[Twelve-Factor app](http://12factor.net/)" concept has 
[precisely the same
restriction](http://12factor.net/processes). Such
state-oriented functions will typically make use of a database, a
cross-application cache (like Redis), or network file/object store (like
S3) to store state across requests, or to provide further input
necessary to handle a request.

Execution Duration
------------------

FaaS functions are typically limited in how long each invocation is
allowed to run. At present the "timeout" for an AWS Lambda function to
respond to an event is at most five minutes, before being terminated.
Microsoft Azure and Google Cloud Functions have similar limits.

This means that certain classes of long-lived tasks are not suited to
FaaS functions without re-architecture---you may need to create several
different coordinated FaaS functions, whereas in a traditional
environment you may have one long-duration task performing both
coordination and execution.

Startup Latency and \"Cold Starts\"
-----------------------------------

It takes some time for a FaaS platform to initialize an instance of a
function before each event. This startup latency can vary significantly,
even for one specific function, depending on a large number of factors,
and may range anywhere from a few milliseconds to several seconds. That
sounds bad, but let's get a little more specific, using AWS Lambda as an
example.

Initialization of a Lambda function will either be a "warm
start"---reusing an instance of a Lambda function and its host container
from a previous event---or a "cold start" ---creating a new container
instance, starting the function host process, etc. Unsurprisingly, when
considering startup latency, it's these cold starts that bring the most
concern.

Cold-start latency depends on many variables: the language you use, how
many libraries you're using, how much code you have, the configuration
of the Lambda function environment itself, whether you need to connect
to  [VPC](https://aws.amazon.com/vpc/) resources, etc.
Many of these aspects are under a developer's control, so it's often
possible to reduce the startup latency incurred as part of a cold start.

Equally as variable as cold-start duration is cold-start frequency. For
instance, if a function is processing 10 events per second, with each
event taking 50 ms to process, you'll likely only see a cold start with
Lambda every 100,000--200,000 events or so. If, on the other hand, you
process an event once per hour, you'll likely see a cold start for every
event, since Amazon retires inactive Lambda instances after a few
minutes. Knowing this will help you understand whether cold starts will
impact you on aggregate, and whether you might want to perform "keep
alives" of your function instances to avoid them being put out to
pasture.

Are cold starts a concern? It depends on the style and traffic shape of
your application. My former team at Intent Media has an asynchronous
message-processing Lambda app implemented in Java (typically the
language with the slowest startup time) which processes hundreds of
millions of messages per day, and they have no concerns with startup
latency for this component. That said, if you were writing a low-latency
trading application you probably wouldn't want to use cloud-hosted FaaS
systems at this time, no matter the language you were using for
implementation.

Whether or not you think your app may have problems like this, you
should test performance with production-like load. If your use case
doesn't work now you may want to try again in a few months, since this
is a major area of continual improvement by FaaS vendors.

For much more detail on cold starts, please see  [my article on the
subject](https://blog.symphonia.io/learning-lambda-part-8-addfab6b460d).

API Gateway
-----------

One aspect of Serverless that we brushed upon earlier is an "API
gateway." An API gateway is an HTTP server where routes and endpoints
are defined in configuration, and each route is associated with a
resource to handle that route. In a Serverless architecture such
handlers are often FaaS functions.

When an API gateway receives a request, it finds the routing
configuration matching the request, and, in the case of a FaaS-backed
route, will call the relevant FaaS function with a representation of the
original request. Typically the API gateway will allow mapping from HTTP
request parameters to a more concise input for the FaaS function, or
will allow the entire HTTP request to be passed through, typically as a
JSON object. The FaaS function will execute its logic and return a
result to the API gateway, which in turn will transform this result into
an HTTP response that it passes back to the original caller.

Amazon Web Services have their own API gateway (slightly confusingly
named " [API
Gateway](https://aws.amazon.com/api-gateway/)"), and
other vendors offer similar abilities. Amazon's API Gateway is a BaaS
(yes, BaaS!) service in its own right in that it's an external service
that you configure, but do not need to run or provision yourself.

Beyond purely routing requests, API gateways may also perform
authentication, input validation, response code mapping, and more. (If
your spidey senses are tingling as you consider whether this is actually
such a good idea, hold that thought! We\'ll consider this further
later.)

One use case for an API gateway with FaaS functions is creating
HTTP-fronted microservices in a Serverless way with all the scaling,
management, and other benefits that come from FaaS functions.

When I first wrote this article, the tooling for Amazon's API Gateway,
at least, was achingly immature. Such tools have improved significantly
since then. Components like AWS API Gateway are not quite "mainstream,"
but hopefully they're a little less painful than they once were, and
will only continue to improve.

Tooling
-------

The comment above about maturity of tooling also applies to Serverless
FaaS in general. In 2016 things were pretty rough; by 2018 we've seen a
marked improvement, and we expect tools to get better still.

A couple of notable examples of good "developer UX" in the FaaS world
are worth calling out. First of all is  [Auth0
Webtask](https://webtask.io/) which places significant
priority on developer UX in its tooling. Second is Microsoft, with
their  [Azure
Functions](https://azure.microsoft.com/en-us/services/functions/) product.
Microsoft has always put Visual Studio, with its tight feedback loops,
at the forefront of its developer products, and Azure Functions is no
exception. The ability it offers to debug functions locally, given an
input from a cloud-triggered event, is quite special.

An area that still needs significant improvement is monitoring. I
discuss that later on.

Open Source
-----------

So far I've mostly discussed proprietary vendor products and tools. The
majority of Serverless applications make use of such services, but there
are open-source projects in this world, too.

The most common uses of open source in Serverless are for FaaS tools and
frameworks, especially the popular  [Serverless
Framework](https://github.com/serverless/serverless),
which aims to make working with AWS API Gateway and Lambda easier than
using the tools provided by AWS. It also provides an amount of
cross-vendor tooling abstraction, which some users find valuable.
Examples of similar tools include 
[Claudia](https://github.com/claudiajs/claudia) and 
[Zappa](https://github.com/Miserlou/Zappa). Another
example is  [Apex](https://github.com/apex/apex), which
is particularly interesting since it allows you to develop Lambda
functions in languages other than those directly supported by Amazon.

The big vendors themselves aren't getting left behind in the open-source
tool party though. AWS's own deployment tool, SAM---the  [Serverless
Application
Model](https://docs.aws.amazon.com/lambda/latest/dg/serverless_app.html)---is 
[also open
source](https://github.com/awslabs/serverless-application-model).

One of the main benefits of proprietary FaaS is not having to be
concerned about the underlying compute infrastructure (machines, VMs,
even containers). But what if you  *want* to be concerned about such
things? Perhaps you have some security needs that can't be satisfied by
a cloud vendor, or maybe you have a few racks of servers that you've
already bought and don't want to throw away. Can open source help in
these scenarios, allowing you to run your own "Serverful" FaaS platform?

Yes, and there's been a good amount of activity in this area. One of the
initial leaders in open-source FaaS was IBM (with 
[OpenWhisk](https://openwhisk.apache.org/), now an
Apache project) and surprisingly---to me at least!---Microsoft, which
open sourced much of its  [Azure
Functions](https://azure.microsoft.com/en-us/services/functions/) platform.
Many other self-hosted FaaS implementations make use of an underlying
container platform, frequently Kubernetes, which makes a lot of sense
for many reasons. In this arena it's worth exploring projects like 
[Galactic Fog](http://www.galacticfog.com/), 
[Fission](https://fission.io/), and 
[OpenFaaS](https://github.com/openfaas/faas). This is a
large, fast-moving world, and I recommend looking at the work that the
Cloud Native Computing Federation (CNCF)  [Serverless Working
Group](https://github.com/cncf/wg-serverless) have done
to track it.

What is Serverless
------------------

So far in this article I\'ve described Serverless as being the union of
two ideas: Backend as a Service and Functions as a Service. I\'ve also
dug into the capabilities of the latter. For more precision about what I
see as the key attributes of a Serverless service (and why I consider
even older services like S3 to be Serverless), I refer you to another
article of mine:  [Defining
Serverless](https://blog.symphonia.io/defining-serverless-part-1-704d72bc8a32).

Before we start looking at the very important area of benefits and
drawbacks, I\'d like to spend one more quick moment on definition. Let's
define what Serverless isn\'t.

Comparison with PaaS 
--------------------

Given that Serverless FaaS functions are very similar to  [Twelve-Factor
applications](http://12factor.net/), are they just
another form of  [\"Platform as a
Service\"](https://en.wikipedia.org/wiki/Platform_as_a_service) (PaaS)
like  [Heroku](http://www.heroku.com/)? For a brief
answer I refer to Adrian Cockcroft.

In other words, most PaaS applications are not geared towards bringing
entire applications up and down in response to an event, whereas FaaS
platforms do  *exactly* this.

If I'm being a good Twelve-Factor app developer, this doesn't
necessarily impact how I program and architect my applications, but it
does make a big difference in how I operate them. Since we\'re all good
DevOps-savvy engineers, we\'re thinking about operations as much as
we're thinking about development, right?

The key operational difference between FaaS and PaaS is  *scaling*.
Generally with a PaaS you still need to think about how to scale---for
example, with Heroku, how many Dynos do you want to run? With a FaaS
application this is completely transparent. Even if you set up your PaaS
application to auto-scale you won't be doing this to the level of
individual requests (unless you have a very specifically shaped traffic
profile), so a FaaS application is much more efficient when it comes to
costs.

Given this benefit, why would you still use a PaaS? There are several
reasons, but tooling is probably the biggest. Also some people use PaaS
platforms like  [Cloud
Foundry](https://en.wikipedia.org/wiki/Cloud_Foundry) to
provide a common development experience across a hybrid public and
private cloud; at time of writing there isn't a FaaS equivalent as
mature as this.

Comparison with containers 
--------------------------

One of the reasons to use Serverless FaaS is to avoid having to manage
application processes at the operating-system level. PaaS services, like
Heroku, also provide this capability, and I've described above how PaaS
is different to Serverless FaaS. Another popular abstraction of
processes are containers, with 
[Docker](https://www.docker.com/) being the most visible
example of such a technology. Container hosting systems such as 
[Mesos](http://mesos.apache.org/) and 
[Kubernetes](http://kubernetes.io/), which abstract
individual applications from OS-level deployment, are increasingly
popular. Even further along this path we see cloud-hosting container
platforms like  [Amazon
ECS](https://aws.amazon.com/ecs/) and 
[EKS](https://aws.amazon.com/eks/), and  [Google
Container
Engine](https://cloud.google.com/container-engine) which,
like Serverless FaaS, let teams avoid having to manage their own server
hosts at all. Given the momentum around containers, is it still worth
considering Serverless FaaS?

Principally the argument I made for PaaS still holds with containers -
for Serverless FaaS  **scaling is automatically managed, transparent,
and fine grained**, and this is tied in with the automatic resource
provisioning and allocation I mentioned earlier. Container platforms
have traditionally still needed you to manage the size and shape of your
clusters.

I'd also argue that container technology is still not mature and stable,
although it is getting ever closer to being so. That's not to say that
Serverless FaaS is mature, of course, but picking which rough edges
you'd like is still the order of the day.

It's also important to mention that self-scaling container clusters are
now available within container platforms. Kubernetes has this built in
with \" [Horizontal Pod
Autoscaling](http://kubernetes.io/docs/user-guide/horizontal-pod-autoscaling/),\"
and services like  [AWS
Fargate](https://aws.amazon.com/fargate/) also make the
promise of "Serverless Containers."

As we see the gap of management and scaling between Serverless FaaS and
hosted containers narrow, the choice between them may just come down to
style and type of application. For example, it may be that FaaS is seen
as a better choice for an event-driven style with few event types per
application component, and containers are seen as a better choice for
synchronous-request--driven components with many entry points. I expect
in a fairly short period of time that many applications and teams will
use both architectural approaches, and it will be fascinating to see
patterns of such use emerge.

\#NoOps 
-------

Serverless doesn't mean \"No Ops\"---though it might mean "No sysadmin"
depending on how far down the Serverless rabbit hole you go.

"Ops" means a lot more than server administration. It also means---at
least---monitoring, deployment, security, networking, support, and often
some amount of production debugging and system scaling. These problems
all still exist with Serverless apps, and you're still going to need a
strategy to deal with them. In some ways Ops is harder in a Serverless
world because a lot of this is so new.

The sysadmin is still happening---you're just outsourcing it with
Serverless. That's not necessarily a bad (or good) thing---we outsource
a lot, and its goodness or badness depends on what precisely you're
trying to do. Either way, at some point the abstraction will likely
leak, and you'll need to know that human sysadmins somewhere are
supporting your application.

[Charity Majors](https://twitter.com/mipsytipsy) gave 
[a great talk on this
subject](https://www.youtube.com/watch?v=wgT5f0eBhD8) at
the first Serverlessconf. (You can also read her two write-ups on it: 
[WTF is
operations?](https://charity.wtf/2016/05/31/wtf-is-operations-serverless/) and 
[Operational Best
Practices](https://charity.wtf/2016/05/31/operational-best-practices-serverless/).)

Stored Procedures as a Service 
------------------------------

Another theme I've seen is that Serverless FaaS is "Stored Procedures as
a Service." I think that\'s come from the fact that many examples of
FaaS functions (including some I\'ve used in this article) are small
pieces of code that are tightly integrated with a database. If that\'s
all we could use FaaS for I think the name would be useful, but because
it is really just a subset of FaaS\'s capability, I don't think it's
useful to think about FaaS in these terms.

That being said, it's worth considering whether FaaS comes with some of
the same problems of stored procedures, including the technical debt
concern Camille mentions in the above-referenced tweet. There are many
lessons that come from using stored procedures that are worth reviewing
in the context of FaaS and seeing whether they apply. Consider that
stored procedures:

1.  Often require vendor-specific language, or at least vendor-specific
    frameworks / extensions to a language
2.  Are hard to test since they need to be executed in the context of a
    database
3.  Are tricky to version control or to treat as a first class
    application

While not all of these will necessarily apply to all implementations of
stored procs, they're certainly problems one might come across. Let's
see if they might apply to FaaS:

\(1\) is definitely not a concern for the FaaS implementations I've seen
so far, so we can scrub that one off the list right away.

For (2) since we're dealing with \"just code,\" unit testing is
definitely as easy as any other code. Integration testing is a different
(and legitimate) question though, and one which we'll discuss later.

For (3), again since FaaS functions are "just code" version control is
okay. Until recently application packaging was also a concern, but we're
starting to see maturity here, with tools like Amazon's  [Serverless
Application
Model](https://docs.aws.amazon.com/lambda/latest/dg/serverless_app.html) (SAM)
and the Serverless Framework that I mentioned earlier. At the beginning
of 2018 Amazon even launched a " [Serverless Application
Repository](https://aws.amazon.com/serverless/serverlessrepo/)"
(SAR) providing organizations with a way to distribute applications, and
application components, built on AWS Serverless services. (Read more on
SAR in my fittingly titled article  [Examining the AWS Serverless
Application
Repository](https://blog.symphonia.io/examining-the-aws-serverless-application-repository-9ef316e2fd4).)

Law of Serverless
-----------------

Law of Furthest Abstraction 
---------------------------

The "Law of Furthest Abstraction" says that you have no knowledge of the
underlying system where your code runs.

This is different from a PaaS. A PaaS hides the operating system, but
you still need to know about the runtime and you still need to have some
system knowledge.

For instance, Azure's PaaS is called " [App
Service](https://azure.microsoft.com/try/app-service/?WT.mc_id=personal-blog-buhollan)".
When you create an App Service instance, you need to tell it what sort
of App Service Plan you want to use. That service plan defines how much
memory and CPU your instance will receive. For instance, here's what the
B (Basic) tier App Service Plans look like...

![A listing of B tier service plans and resources granted with each
one](https://burkeholland.github.io/media/b-service-plans.png)
.confluence-external-resource .confluence-content-image-border
height="150"}

This means App Service is not Serverless.

A service in Azure that  **is** Serverless would be  [Azure
Functions](https://docs.microsoft.com/azure/azure-functions/functions-create-first-function-vs-code?WT.mc_id=personal-blog-buhollan).
Azure Functions has no concept of App Service Plans. You run your code
in Azure Functions and it will receive all the computing power that it
needs when it needs it. It's up to Azure Functions to figure that out.

How does that even work?!?

It works becdause of the second law of Serverless: The Law of Inherent
Scale.

### Law of Inherent Scale 

The Law of Inherent Scale says that scaling is an intrinsic attribute of
the technology; so much so that it just happens automatically.

With Azure Functions, scaling just occurs. And remember, scaling is both
out and back. It's not enough to be able to scale out, the service needs
to also be able to scale back;  **all the way to zero**. That last part
is important as you'll see when we get to the third and final law.

The way that Azure Functions accomplishes this is by adding servers as
your demand spikes, and removing them as the demand subsides. This
includes putting your app back on cold disk if it hasn't been called for
a period of time. It then has to rehydrate the application when the next
invocation occurs.

You can actually watch this happen in realtime by simulating some load
on an Azure Functions instance. Watch the GIF below and you can see the
number of servers increase as the CPU gets pegged.

![](https://burkeholland.github.io/media/function-scaling-demo.gif)
.confluence-external-resource .confluence-content-image-border
height="250"}

What about a PaaS though? Don't most PaaS's scale?

Yes, They do.

Let's look at Azure App Service again as an example. App Service can
scale out in one of two ways. One way is for you to manually add another
App Service instance (B tier for example). This would not be considered
"inherent scale" since it does not happen automatically.

The second way is something called "Auto scaling". This is where Azure
will automatically add new App Service instances for you as the load
increases. That  **is** inherent scale. However, you have to scale in
chunks - or rather by adding full App Service Plan instances. In other
words, you have to add another full B instance to scale out, even if you
don't need the entire amount of that compute. This means that you are
paying for compute whether you use it or not. This brings us to the
third and final Serverless Law - the "Law of Least Consumption".

### Law of Least Consumption 

The Law of Least Consumption says that you only pay for what you use.
Coincidentally, this also everyone's most favorite law. Money talks. But
it doesn't buy happiness. But it does buy jetski's and I've never seen
an unhappy person on a jetski.

Think about it like this: in your house, or your parents house, or
apartment or wherever you happen to live, you probably have running
water. But that water doesn't run all the time. It only runs when you
need it. You turn the faucet on to get water, and off when you aren't
using it. By the way, you can now get a faucet that is  [controlled by
Alexa](https://www.cnet.com/news/delta-to-make-faucets-that-work-with-amazon-alexa/).
Which is just what we need - robots in charge of the water supply.

Azure Functions is like a water faucet for compute. You only get charged
for what you use. That occurs in a few different ways...

1.  **Code storage** - you pay for the disk space that your code
    actually occupies on the server
2.  **Executions** - you pay per execution of your function
3.  **Execution time** - you pay for the amount of compute that your
    function uses.

You also receive 1 million free executions a month. That combined with
the miniscule cost of storage means that if your Azure Functions don't
get called, you don't pay anything. This makes a lot of a sense as a
customer. Just think of all the compute that we have paid for and wasted
all these years! You could be retired already! But probably not because
you'd blow all that extra money on jetski's.

The cloud can (and should) save us money by being able to target compute
by need and not just allocating it in "use it or lose it" buckets.

\

### Applying the Serverles Law 

Now that I have established an irrefutable framework to determine if
something is Serverless, we can apply these laws to any technology to
determine if it is or is NOT Serverless.

#### Azure Service that are Serverles 

-   Azure Static Sites
-   Logic Apps
-   Cosmos DB - Cosmos DB isn't quite Serverless just yet, but it's
    close. It conforms to law 1, but up until recently, you've had to
    buy database bandwidth in chunks which means it did not conform to
    laws 2 and 3. However, as of Ignite, the team announced "Auto
    Pilot". This is a feature which automatically adds throughput as the
    load requires it, but you still have to pay for a basic allocation.
    Once Cosmos DB allows you to start from absolute zero, it will
    comply with all 3 laws and can be considered "Serverless".
-   SQL Server - Believe it or not, SQL Server has a "Serverless"
    offering.

References

-   [Martin Fowler -
    Serverless](https://martinfowler.com/articles/serverless.html)
-   [Github - Awesome design
    patterns](https://github.com/DovAmir/awesome-design-patterns)
-   [Free Content Manning  - Patterns for solving problems i -serverless
    architectures](https://freecontent.manning.com/patterns-for-solving-problems-in-serverless-architectures/)
-   [Burke Holland - laws of
    serverless](https://burkeholland.github.io/posts/laws-of-serverless/)



 



