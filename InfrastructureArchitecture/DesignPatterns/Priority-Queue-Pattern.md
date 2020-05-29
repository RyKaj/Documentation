###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Infrastructure Architecture](https://github.com/RyKaj/Documentation/tree/master/InfrastructureArchitecture/README.md) |
------------


Infrastructure Architecture - Priority Queue Pattern
==================================================


 
Overview
--------

Prioritize requests sent to services so that requests with a higher
priority are received and processed more quickly than those with a lower
priority. This pattern is useful in applications that offer different
service level guarantees to individual clients.

Context and Problem
-------------------

Applications can delegate specific tasks to other services, for example,
to perform background processing or to integrate with other applications
or services. In the cloud, a message queue is typically used to delegate
tasks to background processing. In many cases the order requests are
received in by a service isn\'t important. In some cases, though, it\'s
necessary to prioritize specific requests. These requests should be
processed earlier than lower priority requests that were sent previously
by the application.

Solution
--------

A queue is usually a first-in, first-out (FIFO) structure, and consumers
typically receive messages in the same order that they were posted to
the queue. However, some message queues support priority messaging. The
application posting a message can assign a priority and the messages in
the queue are automatically reordered so that those with a higher
priority will be received before those with a lower priority. The figure
illustrates a queue with priority messaging.

<kbd>![](attachments/463533389/463533387.png)

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

<kbd>![](attachments/463533389/463533388.png)

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

Issues and Considerations
-------------------------

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

When to use this Pattern
------------------------

This pattern is useful in scenarios where:

-   The system must handle multiple tasks that have different
    priorities.
-   Different users or tenants should be served with different priority.

