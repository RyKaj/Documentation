###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Infrastructure Architecture](https://github.com/RyKaj/Documentation/tree/master/InfrastructureArchitecture/README.md) |
------------

Infrastructure Architecture - Microservice Architecture Style
===========================================================


 
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

Constraints Imposed by Microservice Style
-----------------------------------------

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

Consider Challenges Versus Benefits
-----------------------------------

Each architectural constraint has its own associated
challenges/benefits, so it's important to understand and balance both.
Before adopting any style of architecture, you have to ask yourself if
the benefits outweigh the challenges for the application you are
considering.

In the table below, we take a look at the benefits versus challenges of
microservice style applications.

<table>
	<colgroup>
		<col />
		<col />
	</colgroup>
	<tbody>
		<tr>
			<th>
				<strong>Benefits</strong>
			</th>
			<th>
				<strong>Challenges</strong>
			</th>
		</tr>
		<tr>
			<td>Enables the continuous delivery and deployment of large, complex applications.</td>
			<td>There is an additional complexity of creating a distributed system.</td>
		</tr>
		<tr>
			<td>Improved maintainability: Each service is relatively small so it’s easier to understand and change.</td>
			<td>
				Implementing requests that span multiple services is more difficult.
				<p style="margin-left: 0.0px;">Maintaining data consistency between service(s) is a challenge.</p>
			</td>
		</tr>
		<tr>
			<td>Better Testability: services are smaller and faster to test.</td>
			<td>Testing the interactions between services is more difficult.</td>
		</tr>
		<tr>
			<td>Better deployability: services can be deployed independently.</td>
			<td>Increased operational and deployment complexity of deploying and managing a system comprised of many different services.</td>
		</tr>
		<tr>
			<td>Each team can develop, test, deploy and scale their services independently of all of the other teams.</td>
			<td>Implementing requests that span multiple services requires careful coordination between the teams.</td>
		</tr>
		<tr>
			<td>Improved fault isolation.</td>
			<td>Inter-service communication and dealing with partial failure implementation is challenging.</td>
		</tr>
		<tr>
			<td>Eliminates long-term commitment to a technology stack.</td>
			<td>Overhead of multiple JVM runtimes (or equivalent) and increase in memory consumption needs to be taken care of.</td>
		</tr>
	</tbody>
</table>


Scenarios Where You Can Consider Going for Microservice
-------------------------------------------------------

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



 



