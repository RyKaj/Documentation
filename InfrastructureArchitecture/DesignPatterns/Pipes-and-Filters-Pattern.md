###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Infrastructure Architecture](https://github.com/RyKaj/Documentation/tree/master/InfrastructureArchitecture/README.md) |
------------

Infrastructure Architecture - Pipes and Filters Pattern
=====================================================
 
Overview
--------

Decompose a task that performs complex processing into a series of
separate elements that can be reused. This can improve performance,
scalability, and reusability by allowing task elements that perform the
processing to be deployed and scaled independently.

Context and Problem
-------------------

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

<kbd>![](attachments/463533386/463533383.png)

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

Solution
--------

Break down the processing required for each stream into a set of
separate components (or filters), each performing a single task. By
standardizing the format of the data that each component receives and
sends, these filters can be combined together into a pipeline. This
helps to avoid duplicating code, and makes it easy to remove, replace,
or integrate additional components if the processing requirements
change. The next figure shows a solution implemented using pipes and
filters.

<kbd>![](attachments/463533386/463533384.png)


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

<kbd>![](attachments/463533386/463533385.png)


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

Issues and Considerations
-------------------------

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

When to use this Pattern
------------------------

Use this pattern when:

-   The processing required by an application can easily be broken down
    into a set of independent steps.

-   The processing steps performed by an application have different
    scalability requirements.

    > It\'s possible to group filters that should scale together in the
    > same process. For more information, see the  [Compute Resource
    > Consolidation
    > pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/compute-resource-consolidation).

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



 



