Infrastructure Architecture - Log Deployments and Changes
=======================================================

Context
-------

You have applied the  [Microservice architecture pattern](https://microservices.io/patterns/microservices.html).

Problem
-------

How to understand the behavior of an application and troubleshoot problems?

Forces
------

-   It useful to see when deployments and other changes occur since issues usually occur immediately after a change

Solution
--------

Log every deployment and every change to the (production) environment.

Examples
--------

A deployment tool can, for example, publish  [apseudo-metric](https://microservices.io/patterns/observability/application-metrics.html) whenever it deploys a new version of a service. This metric can then be displayed alongside other metrics enabling changes in application behavior to be correlated with deployments. See  [Tracking Every Release by Mike Brittain](https://codeascraft.com/2010/12/08/track-every-release/)

[AWS Cloud Trail](https://aws.amazon.com/cloudtrail/) provides logs of AWS API calls.

