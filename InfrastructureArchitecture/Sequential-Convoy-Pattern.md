








Infrastructure Architecture - Sequential Convoy Pattern
=====================================================


 
Overview
--------

Process a set of related messages in a defined order, without blocking
processing of other groups of messages.

Context and Problem
-------------------

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

Solution
--------

Push related messages into categories within the queuing system, and
have the queue listeners lock and pull only from one category, one
message at a time.

Here\'s what the general Sequential Convoy pattern looks like:

![](attachments/463533400/463533398.png)
.confluence-content-image-border height="150"}

In the queue, messages for different categories may be interleaved, as
shown in the following diagram:

![](attachments/463533400/463533399.png)
.confluence-content-image-border height="150"}

Issues and Considerations
-------------------------

When to use this Pattern
------------------------



 



