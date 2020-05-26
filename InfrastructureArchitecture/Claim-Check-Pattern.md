








Infrastructure Architecture - Claim-Check Pattern
===============================================


 
Overview
--------

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

Context and Problem
-------------------

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

Solution
--------

Store the entire message payload into an external service, such as a
database. Get the reference to the stored payload, and send just that
reference to the message bus. The reference acts like a claim check used
to retrieve a piece of luggage, hence the name of the pattern. Clients
interested in processing that specific message can use the obtained
reference to retrieve the payload, if needed.

![](attachments/463533314/463533313.jpg){.confluence-embedded-image
.confluence-content-image-border height="150"}

Issues and Considerations
-------------------------

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

When to use this Pattern
------------------------

This pattern should be used whenever a message cannot fit the supported
message limit of the chosen message bus technology. For example, Event
Hubs currently has a limit of 256 KB (Basic Tier), while Event Grid
supports only 64-KB messages.

The pattern can also be used if the payload should be accessed only by
services that are authorized to see it. By offloading the payload to an
external resource, stricter authentication and authorization rules can
be put in place, to ensure that security is enforced when sensitive data
is stored in the payload.



 



