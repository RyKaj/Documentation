###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Infrastructure Architecture](https://github.com/RyKaj/Documentation/tree/master/InfrastructureArchitecture/README.md) |
------------

Infrastructure Architecture - Access Token
========================================

 
Context
-------

You have applied the  [Microservice architecture](https://microservices.io/patterns/microservices.html) and  [API Gateway](https://microservices.io/patterns/apigateway.html) patterns. The application consists of numerous services. The API gateway is the single entry point for client requests. It authenticates requests, and forwards them to other services, which might in turn invoke other services.

Problem
-------

How to communicate the identity of the requestor to the services that handle the request?

Forces
------

-   Services often need to verify that a user is authorized to perform     an operation

Solution
--------

The  [API Gateway](https://microservices.io/patterns/apigateway.html) authenticates the request and passes an access token (e.g.  [JSON Web Token](https://jwt.io/)) that securely identifies the requestor in each request to the services. A service can include the access token in requests it makes to other services.

Examples
--------

See  [JSON Web Token](https://jwt.io/) for usage examples and supporting libraries.

