[comment]: [Architecture](ReadMe.MD)


Infrastructure Architecture - Database NOSQL Architect
====================================================
 
These solutions has a number of characteristics in common

-   Key value store
-   Run on large number of commodity machines
-   Data are partitioned and replicated among these machines
-   Relax the data consistency requirement. (because the  [CAP
    theorem](http://www.julianbrowne.com/article/viewer/brewers-cap-theorem) proves
    that you cannot get Consistency, Availability and Partitioning at
    the the same time)

The aim of this blog is to extract the underlying technologies that
these solutions have in common, and get a deeper understanding on the
implication to your application\'s design. I am not intending to compare
the features of these solutions, nor to suggest which one to use.

API Model
---------

The underlying data model can be considered as a large Hashtable
(key/value store).
\
The basic form of API access is

-   get(key) \-- Extract the value given a key
-   put(key, value) \-- Create or Update the value given its key
-   delete(key) \-- Remove the key and its associated value

More advance form of API allows to execute user defined function in the
server environment

-   execute(key, operation, parameters) \-- Invoke an operation to the
    value (given its key) which is a special data structure (e.g. List,
    Set, Map \.... etc).
-   mapreduce(keyList, mapFunc, reduceFunc) \-- Invoke a  [map/reduce
    function](http://horicky.blogspot.com/2008/11/hadoop-mapreduce-implementation.html) across
    a key range.

Machines layout
---------------

The underlying infratructure is composed of large number (hundreds or
thousands) of cheap, commoditized, unreliable machines connected through
a network. We call each machine a physical node (PN). Each PN has the
same set of software configuration but may have varying hardware
capacity in terms of CPU, memory and disk storage. Within each PN, there
will be a variable number of virtual node (VN) running according to the
available hardware capacity of the PN.

![](http://4.bp.blogspot.com/_j6mB7TMmJJY/SwogI5pkEEI/AAAAAAAAAXE/xhrfSf8dmI4/s320/p1.png)

Data Partitioning (Consistent Hashing)
--------------------------------------

Since the overall hashtable is distributed across many VNs, we need a
way to map each key to the corresponding VN.
\
One way is to use\
partition = key mod (total\_VNs)\
\
The disadvantage of this scheme is when we alter the number of VNs, then
the ownership of existing keys has changed dramatically, which requires
full data redistribution. Most large scale store use a \"consistent
hashing\" technique to minimize the amount of ownership changes.

![](http://1.bp.blogspot.com/_j6mB7TMmJJY/SwohQZ9HTAI/AAAAAAAAAXM/X9CAGfpnL2o/s320/p1.png)

In the consistent hashing scheme, the key space is finite and lie on the
circumference of a ring. The virtual node id is also allocated from the
same key space. For any key, its owner node is defined as the first
encountered virtual node if walking clockwise from that key. If the
owner node crashes, all the key it owns will be adopted by its clockwise
neighbor. Therefore, key redistribution happens only within the neighbor
of the crashed node, all other nodes retains the same set of keys.

Data Replication
----------------

To provide high reiability from individually unreliable resource, we
need to replicate the data partitions.

Replication not only improves the overall reliability of data, it also
helps performance by spreading the workload across multiple replicas.

![](http://4.bp.blogspot.com/_j6mB7TMmJJY/SwohcYWqCDI/AAAAAAAAAXU/oH0pDuht4vo/s320/P2.png)

While read-only request can be dispatched to any replicas, update
request is more challenging because we need to carefully co-ordinate the
update which happens in these replicas.

Membership Changes
------------------

Notice that virtual nodes can join and leave the network at any time
without impacting the operation of the ring.
\
When a new node joins the network

1.  The joining node announce its presence and its id to some well known
    VNs or just broadcast)
2.  All the neighbors (left and right side) will adjust the change of
    key ownership as well as the change of replica memberships. This is
    typically done synchronously.
3.  The joining node starts to bulk copy data from its neighbor in
    parallel asynchronously.
4.  The membership change is asynchronously propagate to the other
    nodes.

![](http://1.bp.blogspot.com/_j6mB7TMmJJY/Sw1b9Sv0fmI/AAAAAAAAAXc/4-YNzhA3LCQ/s320/p1.png)

Notice that other nodes may not have their membership view updated yet
so they may still forward the request to the old nodes. But since these
old nodes (which is the neighbor of the new joined node) has been
updated (in step 2), so they will forward the request to the new joined
node.
\
On the other hand, the new joined node may still in the process of
downloading the data and not ready to serve yet. We use the vector clock
(described below) to determine whether the new joined node is ready to
serve the request and if not, the client can contact another replica.
\
When an existing node leaves the network (e.g. crash)

1.  The crashed node no longer respond to gossip message so its
    neighbors knows about it.
2.  The neighbor will update the membership changes and copy data
    asynchronously

![](http://2.bp.blogspot.com/_j6mB7TMmJJY/Sw1jGP6y5tI/AAAAAAAAAXk/rM9k-jNcsKQ/s320/P2.png)

We haven\'t talked about how the virtual nodes is mapped into the
physical nodes. Many schemes are possible with the main goal that
Virtual Node replicas should not be sitting on the same physical node.
One simple scheme is to assigned Virtual node to Physical node in a
random manner but check to make sure that a physical node doesn\'t
contain replicas of the same key ranges.
\
Notice that since machine crashes happen at the physical node level,
which has many virtual nodes runs on it. So when a single Physical node
crashes, the workload (of its multiple virtual node) is scattered across
many physical machines. Therefore the increased workload due to physical
node crashes is evenly balanced.

### Client Consistency

Once we have multiple copies of the same data, we need to worry about
how to synchronize them such that the client can has a consistent view
of the data.
\
There is a number of client consistency models

1.  Strict Consistency (one copy serializability): This provides the
    semantics as if there is only one copy of data. Any update is
    observed instantaneously.
2.  Read your write consistency: The allows the client to see his own
    update immediately (and the client can switch server between
    requests), but not the updates made by other clients
3.  Session consistency: Provide the read-your-write consistency only
    when the client is issuing the request under the same session scope
    (which is usually bind to the same server)
4.  Monotonic Read Consistency: This provide the time monotonicity
    guarantee that the client will only see more updated version of the
    data in future requests.
5.  Eventual Consistency: This provides the weakness form of guarantee.
    The client can see an inconsistent view as the update are in
    progress. This model works when concurrent access of the same data
    is very unlikely, and the client need to wait for some time if he
    needs to see his previous update.

\
Depends on which consistency model to provide, 2 mechanisms need to be
arranged \...

-   How the client request is dispatched to a replica
-   How the replicas propagate and apply the updates

There are various models how these 2 aspects can be done, with different
tradeoffs.

Master Slave (or Single Master) Model
-------------------------------------

Under this model, each data partition has a single master and multiple
slaves. In above model, B is the master of keyAB and C, D are the
slaves. All update requests has to go to the master where update is
applied and then asynchronously propagated to the slaves. Notice that
there is a time window of data lost if the master crashes before it
propagate its update to any slaves, so some system will wait
synchronously for the update to be propagated to at least one slave.
\
Read requests can go to any replicas if the client can tolerate some
degree of data staleness. This is where the read workload is distributed
among many replicas. If the client cannot tolerate staleness for certain
data, it also need to go to the master.
\
Note that this model doesn\'t mean there is one particular physical node
that plays the role as the master. The granularity of \"mastership\"
happens at the virtual node level. Each physical node has some virtual
nodes acts as master of some partitions while other virtual nodes acts
as slaves of other partitions. Therefore, the write workload is also
distributed across different physical node, although this is due to
partitioning rather than replicas\
\
When a physical node crashes, the masters of certain partitions will be
lost. Usually, the most updated slave will be nominated to become the
new master.
\
Master Slave model works very well in general when the application has a
high read/write ratio. It also works very well when the update happens
evenly in the key range. So it is the predominant model of data
replication.
\
There are 2 ways how the master propagate updates to the slave; State
transfer and Operation transfer. In State transfer, the master passes
its latest state to the slave, which then replace its current state with
the latest state. In operation transfer, the master propagate a sequence
of operations to the slave which then apply the operations in its local
state.
\
The state transfer model is more robust against message lost because as
long as a latter more updated message arrives, the replica still be able
to advance to the latest state.
\
Even in state transfer mode, we don\'t want to send the full object for
updating other replicas because changes typically happens within a small
portion of the object. In will be a waste of network bandwidth if we
send the unchanged portion of the object, so we need a mechanism to
detect and send just the delta (the portion that has been changed). One
common approach is break the object into chunks and compute a  [hash
tree](http://en.wikipedia.org/wiki/Hash_tree) of the
object. So the replica can just compare their hash tree to figure out
which chunk of the object has been changed and only send those over.
\
In operation transfer mode, usually much less data need to be send over
the network. However, it requires a reliable message mechanism with
delivery order guarantee.

Multi-Master (or No Master) Model
---------------------------------

If there is hot spots in certain key range, and there is intensive write
request, the master slave model will be unable to spread the workload
evenly. Multi-master model allows updates to happen at any replica (I
think call it \"No-Master\" is more accurate).
\
If any client can issue any update to any server, how do we synchronize
the states such that we can retain client consistency and also
eventually every replica will get to the same state ? We describe a
number of different approaches in following \...

Quorum Based 2PC
----------------

To provide \"strict consistency\", we can use a traditional 2PC protocol
to bring all replicas to the same state at every update. Lets say there
is N replicas for a data. When the data is update, there is a
\"prepare\" phase where the coordinator ask every replica to confirm
whether each of them is ready to perform the update. Each of the replica
will then write the data to a log file and when success, respond to the
coordinator.
\
After gathering all replicas responses positively, the coordinator will
initiate the second \"commit\" phase and then ask every replicas to
commit and each replica then write another log entry to confirm the
update. Notice that there are some scalability issue as the coordinator
need to \"synchronously\" wait for quite a lot of back and forth network
roundtrip and disk I/O to complete.
\
On the other hand, if any one of the replica crashes, the update will be
unsuccessful. As there are more replicas, chance of having one of them
increases. Therefore, replication is hurting the availability rather
than helping. This make traditional 2PC not a popular choice for high
throughput transactional system.
\
A more efficient way is to use the quorum based 2PC (e.g. PAXOS). In
this model, the coordinator only need to update W replicas (rather than
all N replicas) synchronously. The coordinator still write to all the N
replicas but only wait for positive acknowledgment for any W of the N to
confirm. This is much more efficient from a probabilistic standpoint.
\
However, since no all replicas are update, we need to be careful when
reading the data to make sure the read can reach at least one replica
that has been previously updated successful. When reading the data, we
need to read R replicas and return the one with the latest timestamp.
\
For \"strict consistency\", the important condition is to make sure the
read set and the write set overlap. ie: W + R \> N

\
[![](http://4.bp.blogspot.com/_j6mB7TMmJJY/SwOHybHlzHI/AAAAAAAAATE/-NaXjP_S2H8/s400/P7.png)](http://4.bp.blogspot.com/_j6mB7TMmJJY/SwOHybHlzHI/AAAAAAAAATE/-NaXjP_S2H8/s1600/P7.png)

\
As you can see, the quorum based 2PC can be considered as a general 2PC
protocol where the traditional 2PC is a special case where W = N and R =
1. The general quorum-based model allow us to pick W and R according to
our tradeoff decisions between read and write workload ratio.
\
If the user cannot afford to pick W, R large enough, ie: W + R \<= N,
then the client is relaxing its consistency model to a weaker one.
\
If the client can tolerate a more relax consistency model, we don\'t
need to use the 2PC commit or quorum based protocol as above. Here we
describe a Gossip model where updates are propagate asynchronous via
gossip message exchanges and an auto-entropy protocol to apply the
update such that every replica eventually get to the latest state.

Vector Clock
------------

Vector Clock is a timestamp mechanism such that we can reason about
causal relationship between updates. First of all, each replica keeps
vector clock. Lets say replica i has its clock Vi. Vi\[i\] is the
logical clock which if every replica follows certain rules to update its
vector clock.

-   Whenever an internal operation happens at replica i, it will advance
    its clock Vi\[i\]
-   Whenever replica i send a message to replica j, it will first
    advance its clock Vi\[i\] and attach its vector clock Vi to the
    message
-   Whenever replica j receive a message from replica i, it will first
    advance its clock Vj\[j\] and then merge its clock with the clock Vm
    attached in the message. ie: Vj\[k\] = max(Vj\[k\], Vm\[k\])

![](http://2.bp.blogspot.com/_j6mB7TMmJJY/SwoSGODJQuI/AAAAAAAAAWs/OefcWLxdsmI/s320/p1.png)

A partial order relationship can be defined such that Vi \> Vj iff for
all k, Vi\[k\] \>= Vj\[k\]. We can use these partial ordering to derive
causal relationship between updates. The reasoning behind is

-   The effect of an internal operation will be seen immediately at the
    same node
-   After receiving a message, the receiving node knows the situation of
    the sending node at the time when the message is send. The situation
    is not only including what is happening at the sending node, but
    also all the other nodes that the sending node knows about.
-   In other words, Vi\[i\] reflects the time of the latest internal
    operation happens at node i. Vi\[k\] = 6 reflects replica i has
    known the situation of replica k up to its logical clock 6.

Notice that the term \"situation\" is used here in an abstract sense.
Depends on what information is passed in the message, the situation can
be different. This will affect how the vector clock will be advanced. In
below, we describe the \"state transfer model\" and the \"operation
transfer model\" which has different information passed in the message
and the advancement of their vector clock will also be different.
\
Because state is always flow from the replica to the client but not the
other way round, the client doesn\'t have an entry in the Vector clock.
The vector clock contains only one entry for each replica. However, the
client will also keep a vector clock from the last replica it contacts.
This is important for support the client consistency model we describe
above. For example, to support monotonic read, the replica will make
sure the vector clock attached to the data is \> the client\'s submitted
vector clock in the request.

Gossip (State Transfer Model)
-----------------------------

In a state transfermodel, each replica maintain a vector clock as well
as a state version tree where each state is neither \> or \< among each
other (based on vector clock comparison). In other words, the state
version tree contains all the conflicting updates.
\
At query time, the client will attach its vector clock and the replica
will send back a subset of the state tree which precedes the client\'s
vector clock (this will provide monotonic read consistency). The client
will then advance its vector clock by merging all the versions. This
means the client is responsible to resolve the conflict of all these
versions because when the client sends the update later, its vector
clock will precede all these versions.

![](http://2.bp.blogspot.com/_j6mB7TMmJJY/SwmXpttEVKI/AAAAAAAAAVc/BuDsgnTJoZM/s400/p1.png)

At update, the client will send its vector clock and the replica will
check whether the client state precedes any of its existing version, if
so, it will throw away the client\'s update.

![](http://2.bp.blogspot.com/_j6mB7TMmJJY/SwmX6waHqPI/AAAAAAAAAVk/48TsSr21pUU/s400/P2.png)

Replicas also gossip among each other in the background and try to merge
their version tree together.

![](http://2.bp.blogspot.com/_j6mB7TMmJJY/SwmYWE4O5sI/AAAAAAAAAV0/2QDGlh-JAGA/s320/P3.png)

Gossip (Operation Transfer Model)
---------------------------------

In an operation transfer approach, the sequence of applying the
operations is very important. At the minimum causal order need to be
maintained. Because of the ordering issue, each replica has to defer
executing the operation until all the preceding operations has been
executed. Therefore replicas save the operation request to a log file
and exchange the log among each other and consolidate these operation
logs to figure out the right sequence to apply the operations to their
local store in an appropriate order.
\
\"Causal order\" means every replica will apply changes to the
\"causes\" before apply changes to the \"effect\". \"Total order\"
requires that every replica applies the operation in the same sequence.
\
In this model, each replica keeps a list of vector clock, Vi is the
vector clock the replica itself and Vj is the vector clock when replica
i receive replica j\'s gossip message. There is also a V-state that
represent the vector clock of the last updated state.
\
When a query is submitted by the client, it will also send along its
vector clock which reflect the client\'s view of the world. The replica
will check if it has a view of the state that is later than the
client\'s view.

![](http://3.bp.blogspot.com/_j6mB7TMmJJY/SwmlOzM4YuI/AAAAAAAAAV8/vXWT2gsQvNc/s400/p1.png)

When an update operation is received, the replica will buffer the update
operation until it can be applied to the local state. Every submitted
operation will be tag with 2 timestamp, V-client indicates the client\'s
view when he is making the update request. V-\@receive is the replica\'s
view when it receives the submission.
\
This update operation request will be sitting in the queue until the
replica has received all the other updates that this one depends on.
This condition is reflected in the vector clock Vi when it is larger
than V-client

![](http://3.bp.blogspot.com/_j6mB7TMmJJY/Swmll8oYbqI/AAAAAAAAAWE/F_oI7WwWep0/s400/P2.png)

On the background, different replicas exchange their log for the queued
updates and update each other\'s vector clock. After the log exchange,
each replica will check whether certain operation can be applied (when
all the dependent operation has been received) and apply them
accordingly. Notice that it is possible that multiple operations are
ready for applying at the same time, the replica will sort these
operation in causal order (by using the Vector clock comparison) and
apply them in the right order.

![](http://4.bp.blogspot.com/_j6mB7TMmJJY/Swml33Xp04I/AAAAAAAAAWM/yCHvTCgTzF8/s400/P3.png)

The concurrent update problem at different replica can also happen.
Which means there can be multiple valid sequences of operation. In order
for different replica to apply concurrent update in the same order, we
need a total ordering mechanism.
\
One approach is whoever do the update first acquire a monotonic sequence
number and late comers follow the sequence. On the other hand, if the
operation itself is commutative, then the order to apply the operations
doesn\'t matter\
\
After applying the update, the update operation cannot be immediately
removed from the queue because the update may not be fully exchange to
every replica yet. We continuously check the Vector clock of each
replicas after log exchange and after we confirm than everyone has
receive this update, then we\'ll remove it from the queue.

Map Reduce Execution
--------------------

Notice that the distributed store architecture fits well into
distributed processing as well. For example, to process a  [Map/Reduce
operation](http://horicky.blogspot.com/2008/11/hadoop-mapreduce-implementation.html) over
an input key list.
\
The system will push the map and reduce function to all the nodes (ie:
moving the processing logic towards the data). The map function of the
input keys will be distributed among the replicas of owning those input,
and then forward the map output to the reduce function, where the
aggregation logic will be executed.

\
[![](http://4.bp.blogspot.com/_j6mB7TMmJJY/SwoeUzwoKrI/AAAAAAAAAW0/ch01mbMkRuk/s320/p1.png)](http://4.bp.blogspot.com/_j6mB7TMmJJY/SwoeUzwoKrI/AAAAAAAAAW0/ch01mbMkRuk/s1600/p1.png)

Handling Deletes 
----------------

In a multi-master replication system, we use Vector clock timestamp to
determine causal order, we need to handle \"delete\" very carefully such
that we don\'t lost the associated timestamp information of the deleted
object, otherwise we cannot even reason the order of when to apply the
delete.
\
Therefore, we typically handle delete as a special update by marking the
object as \"deleted\" but still keep its metadata / timestamp
information around. Around a long enough time that we are confident that
every replica has marked this object deleted, then we garbage collected
the deleted object to reclaim its space.

Storage Implementaton
---------------------

One strategy is to use make the storage implementation pluggable. e.g. A
local MySQL DB, Berkeley DB, Filesystem or even a in memory Hashtable
can be used as a storage mechanism.
\
Another strategy is to implement the storage in a highly scalable way.
Here are some techniques that I learn from 
[CouchDB](http://horicky.blogspot.com/2008/10/couchdb-implementation.html) and
Google BigTable.
\
CouchDB has a MVCC model that uses a copy-on-modified approach. Any
update will cause a private copy being made which in turn cause the
index also need to be modified and causing the a private copy of the
index as well, all the way up to the root pointer.

![](http://1.bp.blogspot.com/_j6mB7TMmJJY/SwjQAV_JShI/AAAAAAAAAU8/ndAucGpmwzI/s400/p1.png)

Notice that the update happens in an append-only mode where the modified
data is appended to the file and the old data becomes garbage. Periodic
garbage collection is done to compact the data. Here is how the model is
implemented in memory and disks

![](http://2.bp.blogspot.com/_j6mB7TMmJJY/SwjQd22AlMI/AAAAAAAAAVE/bUDkgpnPu5Q/s400/P2.png)

In Google BigTable model, the data is broken down into multiple
generations and the memory is use to hold the newest generation. Any
query will search the mem data as well as all the data sets on disks and
merge all the return results. Fast detection of whether a generation
contains a key can be done by checking a bloom filter.

![](http://3.bp.blogspot.com/_j6mB7TMmJJY/SwnJ4-X4GjI/AAAAAAAAAWk/Wy8cW8f8dwM/s400/p1.png)

When update happens, both the mem data and the commit log will be
written so that if the machine crashes before the mem data flush to
disk, it can be recovered from the commit log.

MongoDB Design Pattern
----------------------

MongoDB is a NoSQL document database. It\'s ideal for most use cases,
and where it doesn\'t work, you can still overcome some of its
limitations by using the following design patterns.

### Query Command Segregation Pattern

[![](https://3.bp.blogspot.com/-rOTILpreL1o/V1_X0cpsuDI/AAAAAAAANTw/U7P0N151mhQIwQ5UrV4ZClLgg5T94DibQCLcB/s400/segregate.png)
[![](https://3.bp.blogspot.com/-rOTILpreL1o/V1_X0cpsuDI/AAAAAAAANTw/U7P0N151mhQIwQ5UrV4ZClLgg5T94DibQCLcB/s1600/segregate.png)

Segregate responsibility to different nodes in the replica set. The
primary node may have priority 1 and may keep only indexes required for
insert and update. The queries can be executed on secondaries. This
pattern will increase write throughput on the "priority 1" servers
because fewer indexes need to be updated and inserted on writing to a
collection and secondaries benefit from having to update fewer indexes
and having a working set of memory that is optimized for their workload

### Application-Level Transactions Pattern

MongoDB does not support transactions and locking documents internally.
However, with application logic, a queue may be maintained.

### Bucketing Pattern

When the document has an array that grows over the period of time, use
the bucketing pattern. Example: Orders. The order lines can grow or may
be larger than the desired size of the document. The pattern is handled
programmatically and is triggered using a tolerance count.

### Relationship Pattern

Sometimes it\'s not feasible to embed entire document --- for example,
when we are modeling people. Use this pattern to build relationships.

1.  Determine if data \"belongs to\" a document --- is there a relation?

2.  Embed when possible, especially if the data is useful and exclusive
    (\"belongs in\").

3.  Always reference \_id values at minimum.

4.  Denormalize the useful parts of the relationship. Good candidates do
    not change value often, or ever, and are useful.

5.  Be mindful of updates to denormalized data and repair relationships

### Materialized Path Pattern

If you have a tree pattern of data model where the same object type is a
child of an object, you can use the materialized path pattern for more
efficient search/queries. A sample is given below.

![](https://1.bp.blogspot.com/-xiU2cUyIsSU/V1_cVnm-_0I/AAAAAAAANUI/qnliOY0DnH4WQigYgekIGcxl9lKFXh9OwCLcB/s400/tree.png)

Resiliency Design Patterns
--------------------------

Enabled by more efficient distributed consensus protocols, such as Paxos
and Raft, and new thinking, such as flexible database schema, NoSQL
databases have grown out of early adoption and are  [gaining
popularity](http://www.infoworld.com/article/3019332/database/oracle-remains-most-popular-database-but-mongodb-continues-to-rise.html) among
mainstream companies. Although many NoSQL vendors tout their products as
having unparalleled web-level scalability and capabilities such as
auto-failover, not all are created equal in terms of availability,
consistency, durability and recoverability. This is especially true if
you are running mission-critical applications using heterogeneous NoSQL
systems that include key-value (KV) pairs, column families (CF), and
document and graph databases across a geographically dispersed
environment.

It becomes imperative that a well-run enterprise optimizes its
management to achieve the highest operational efficiency and
availability. To accomplish this, an enterprise should not only empower
application developers with well-defined NoSQL database resilience
design patterns so that they can be relieved from preventable
infrastructure failure, but it should also provide a
guaranteed-availability Service Level Agreement (SLA) on these
resilience design patterns.

### NoSQL resiliency design pattern consideration

Given the enormous complexity associated with integrating an
enterprise-class infrastructure, such as eBay, developing meaningful and
usable NoSQL resilience pattern is more than just one dimension --- it
comprises a multitude of coherent and intricately interconnected cogs
such as these:

-   Use case qualification
-   Application persistence error handling
-   Technology stack and engineering framework
-   Data center infrastructure (for example, public/private/hybrid
    cloud) configuration and setup\<
-   NoSQL database-agnostic and -specific resilience abstraction\<
-   Operation and management best practice and standard operation
    procedure (SOP)

Since NoSQL databases are not panaceas, ill-suited applications can
disrupt operations and cause friction between stakeholders within the
organization. The first step toward defining a meaningful NoSQL database
resilience pattern is to ensure that only qualified use cases will use
it. With that, we recommend the following guidelines when qualifying new
NoSQL use cases.

![NoSQL qualifying guidelines](https://tech.ebayinc.com/assets/Uploads/Blog/2017/02/_resampled/ScaleWidthWzc1MF0/NoSQL-qualifying-guidelines.1.png)

### NoSQL resiliency design pattern approach

One main objective of a NoSQL resilience design pattern is that it
should support a wide range of use cases across different NoSQL
databases. To achieve this objective, we devised the following steps in
our approach:

1.  Identify a meaningful NoSQL database architectural abstraction based
    on the  [CAP theorem](https://fenix.tecnico.ulisboa.pt/downloadFile/1126518382178117/10.e-CAP-3.pdf), 
    [ACID/BASE properties](http://queue.acm.org/detail.cfm?id=1394128),
    and performance characteristics.
2.  Categorize and define types of different resilience patterns based
    on workload, performance, and consistency properties that are
    meaningful to applications.
3.  Define a standardized minimal NoSQL deployment pattern for common
    small-to-medium, non-mission critical use cases.
4.  Define an enhanced design pattern to support mission-critical use
    cases that require high availability, consistency, durability,
    scalability, and performance.
5.  Define other design patterns to support non-conforming use cases,
    for example, standalone without disaster recovery (DR), and
    application sharding.

Given that JSON has become the de facto standard data format for
web-centric e-commerce businesses like eBay, this blog will use two of
the top document-centric NoSQL databases (MongoDB and Couchbase) to
illustrate our proposed resilience design pattern.

![DB comparison](https://tech.ebayinc.com/assets/Uploads/Blog/2017/02/_resampled/ScaleWidthWzc1MF0/DB-comparison.2.png)

Although a tutorial on MongoDB and Couchbase is beyond the scope of this
blog, the high-level comparison between them in Table 1 helps illustrate
their differences. It also helps explain how these differences influence
respective resilience design patterns for each product.

 {.table-wrap}
Table 1. Comparison of MongoDB and Couchbase

MongoDB




Couchbase

\* Throughout this blog post, for convenience we designate one Couchbase
cluster per data center even though multiple clusters can be set up per
data center. However, nodes in the same Couchbase cluster do not span
across multiple data centers.

Name

Replica set/sharded cluster

"Cluster"\*

Architecture

Master-slave

Peer-to-peer

Replication

Master to slave (or primary to secondary) nodes

Local cluster

Primary to replica nodes

Multiple cluster

Bi- or uni-directional Cross Data Center Replication (XDCR)

Sharding

Optional

Built-in

Quorum

Read

Yes

No

Write

Yes

From the comparison above, we observe the following characteristics when
designing a resilience pattern design:

-   NoSQL databases tend to simplify their resilience pattern if they
    are based on peer-to-peer architecture.
-   NoSQL databases tend to complicate their resilience pattern if they
    lack quorum read/write, an important capability to support global
    read and write consistency.

Lastly, we found it helpful to organize resilience design patterns into
different categories, as shown in the Table 2. For brevity, we will
focus the examples on the following three categories: workload,
durability, and application sharding.

 {.table-wrap}
Table 2. Categories of Resilience Design Patterns

Category


Pattern

Workload

General purpose mixed read and write 

Performance

High performance read and/or write

Durability

100% durability

High local and/or cross data center durability 

High availability (HA)

High availability local read and write

High availability multi-data center read and write

High Read and write consistency

High local data center read and write consistency

High multi-data center read and write consistency

Others

Administration, backup and restore, application sharding

### Standard minimal deployment

As mentioned earlier, one key objective of NoSQL resilience design
patterns is to relieve applications and Operation of preventable
infrastructure failure. It is our opinion that, disregarding the size or
importance of applications, enterprise-class NoSQL clusters should be
able to handle node, cluster, site or network partition failure
gracefully with built-in preventive measures. Also, they should be able
to perform disaster recovery (DR) within reasonable bounds. This
assumption warrants the need of the "standard minimal deployments"
described below.

### MongoDB standard minimal deployment

According to our experience managing some of the largest 24×7
heterogeneous NoSQL clusters in the world, we recommend the following
"standard minimal deployment" best practice for enterprise-class MongoDB
deployments:

-   Whenever possible, nodes in the same MongoDB replica set will be
    provisioned in different fault domain to minimize any availability
    risk associated with node and network failure.
-   Standard MongoDB deployment (for example, type 1 in Table 3) always
    includes third data center with two or more secondary nodes. For
    applications that do not have traffic in a third data
    center, light-weight arbiter nodes should be used for cross-data
    center quorum voting during site or total data center failure.
-   With few exceptions (for example, type 2 below), a MongoDB replica
    set can be deployed in only one data center if applications do not
    require remote DR capability.

 {.table-wrap}
Table 3. MongoDB Standard Minimal Deployments

Deployment Type\<


MongoDB Replica Set Nodes Configuration\<

Description\<

Data Center 1

Data Center 2

Data Center 3

1

Standard deployment with built-in DR capability

Minimum three nodes, which include one primary and two secondary nodes

Minimum two secondary nodes

Minimum two secondary or arbiter nodes.This is to ensure that should any
one data center experience total failure, it is not excluded from quorum
voting for new primary node.

In selected high traffic or important use cases,
additional secondary nodes may be added in each data center. The purpose
is to increase application read resilience so that surviving nodes won't
be overwhelmed in case of one or more secondary nodes fail in any data
center.

2

Special qualified use case without DR

Three (one primary, two secondary nodes)

This deployment pattern is for use cases that do not require remote DR
since applications can rebuild the entire dataset from an external data
source.Furthermore, the lifespan of data can be relatively short-lived
and may expire in a matter of minutes, if not seconds. In selected high
traffic or important use cases, additional secondary nodes may be added
to the replica set to help increase resilience.

The following diagram illustrates the MongoDB "standard minimal
deployment" pattern.

[![Mongo
deploy](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/_resampled/ScaleWidthWzc1MF0/Mongo-deploy.2.png)
https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Mongo-deploy.2.png)

During primary node failover, one of the available secondary nodes in
either data center will be elected as the new primary node, as shown in
the following diagram.

[![Mongo before
failover](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/_resampled/ScaleWidthWzc1MF0/Mongo-before-failover.3.png)
(https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Mongo-before-failover.3.png)

During site or data center failure, one of the available secondary nodes
in other data centers will be elected as the new primary node, as shown
in the following diagram.

[![Mongo after
failover](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/_resampled/ScaleWidthWzc1MF0/Mongo-after-failover.4.png)
(https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Mongo-after-failover.4.png)

### Couchbase standard minimal deployment

With peer-to-peer architecture, Couchbase's "standard minimal
deployment" does not require a third data center since it does not
involve quorum voting when failing over to a new primary node. Arguably,
increasing minimal nodes from four to five or six or more per data
center can help strengthen operational viability should two or more
nodes in the same data center fail at the same time (itself an unlikely
scenario if they were provisioned in different fault domains in the
first place). With that, we feel that a minimal four nodes per data
center are sufficient for most Couchbase use cases to start with.

 {.table-wrap}
Table 4. Couchbase Standard Minimal Deployments

Deployment Type


Couchbase Replica Set Nodes Configuration

Description

Data Center 1

Data Center 2

Data Center 3 (Optional)

1

Standard deployment with built-in DR capability

4+ nodes

4+ nodes

4+ nodes

See description above

2

Special qualified use case without DR

4+ nodes

Same as MongoDB

The following diagram illustrates the Couchbase "standard minimal
deployment" pattern where each data center/cluster has two copies of the
same document (for example, P1 being the primary copy and R1 the
eventually consistent replica copy).

![Couchbase
deploy](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/_resampled/ScaleWidthWzc1MF0/Couchbase-deploy.5.png){height="250"}

During automatic node failover, the Couchbase client SDK in applications
will detect node failure and receive an updated failover cluster map
with a topology containing the new location of replica documents that
have been promoted to primary. This is shown in following diagram.

![Couchbase
failover](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/_resampled/ScaleWidthWzc1MF0/Couchbase-failover.6.png){height="250"}

Although Couchbase supports bidirectional Cross Data Center Replication
(XDCR) between geographically dispersed clusters, its current
implementation does not offer automatic cluster failover. To address
this limitation, Couchbase will support a new feature called
Multi-Cluster Awareness (MCA) in a future release (tentatively v4.x) to
provide this capability, as shown in following diagram.

![Couchbase
MCA](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/_resampled/ScaleWidthWzc1MF0/Couchbase.MCA_.7.png){height="250"}

### High-level MongoDB and Couchbase resilience capability comparison

Before we talk about the details of an individual resilience design
pattern for each product, it helps to understand the capability of
MongoDB and Couchbase in terms of high availability, consistency,
durability, and DR across local and multiple data centers. The following
table highlights their differences.

 {.table-wrap}
Table 5. Comparison of MongoDB and Couchbase Resilience Capabilities

NoSQL Database


Data center

High Availability

High Consistency

High Durability

DR

\* MCA (Multi-Cluster Awareness) and TbCR ( [Timestamp-based Conflict
Resolution](https://developer.couchbase.com/documentation/server/4.6/xdcr/xdcr-timestamp-based-conflict-resolution.html))
will be available in a future Couchbase v4.x release.

MongoDB

Local DC

No for Write\
Yes for Read

Yes

Yes

No

Multi DC

Yes

Couchbase

Local DC

No for Write\
Yes for Read

Yes

Yes

No

Multi DC

Yes with MCA\*

No

Yes with MCA and TbCR\*

Yes

From the above comparison, we observe one similarity between MongoDB and
Couchbase in their support for high-availability writes or the lack of.
This is because both products limit their writes to a single primary
node only. Nonetheless, Couchbase does plan to support high-availability
write for multiple data centers through its future Multi-Cluster
Awareness feature, which will help alleviate this limitation. This is
the reason why Couchbase's standard minimal deployment pattern requires
at minimum two data centers/clusters.

### MongoDB resilience design pattern examples

Before we show MongoDB's resilience design pattern examples, it is
important to understand how data loss can happen in MongoDB if
applications do not use a proper resilience design pattern.

### Non-synchronous writes

Let's assume that you have a MongoDB replica set comprised of three
nodes. The following operations illustrate how data loss can happen:

-   First, the application writes five documents and receives write
    confirmation from the primary node only.
-   The first three documents are replicated successfully at the second
    secondary node, and two documents are replicated at the third
    secondary node.

[![Mongo Non-Synchronous Writes
A](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Mongo-Non-Synchronous-Writes.a.8.png)
https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Mongo-Non-Synchronous-Writes.a.8.png)

-   The primary node fails before all five documents reach both of the
    two secondary nodes

[![Mongo Non-Synchronous Writes
B](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Mongo-Non-Synchronous-Writes.b.9.png)
(https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Mongo-Non-Synchronous-Writes.b.9.png)

-   Quorum voting re-elects the second secondary node as the new primary
    node because it receives the third document, that is, more recently
    than the third secondary node

[![Mongo Non-Synchronous Writes
C](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Mongo-Non-Synchronous-Writes.c.10.png)
(https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Mongo-Non-Synchronous-Writes.c.10.png)

-   The original primary node steps down to be a secondary and rolls
    back its fourth and fifth documents, since they didn't reach other
    two secondary nodes

[![Mongo Non-Synchronous Writes
D](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Mongo-Non-Synchronous-Writes.d.11.png)
(https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Mongo-Non-Synchronous-Writes.d.11.png)

-   In effect, the application loses the fourth and fifth documents even
    though it receives confirmation from the original primary node. The
    issue associated with this type of data loss (non-synchronous write)
    occurs because that application didn't apply the "quorum write"
    option to majority nodes in the same replica set.
-   In addition to "quorum write", one should also enable MongoDB's
    write-ahead logging 
    [journal](https://docs.mongodb.com/manual/core/journaling/) file
    to further increase primary node write durability.

Since non-synchronous write is just one type of issue that can happen to
applications, it is not sufficient to develop a pattern just to solve
it. Having various add-on patterns, like synchronous write and others,
on top of the MongoDB standard minimal deployment patterns helps enrich
the overall NoSQL database resilience capabilities.

### MongoDB write durability pattern

To achieve MongoDB replica-set-wide write durability, an application
should use MongoDB's 
[WriteConcern](https://docs.mongodb.com/manual/reference/write-concern/) = 
[Majority](https://docs.mongodb.com/manual/reference/write-concern/#writeconcern.) option,
where a write waits for confirmation from majority nodes across multiple
data centers. During primary node failover, one of the majority
secondary nodes having the latest committed write will be elected as the
new primary node.

One caveat of this pattern is that one should weigh the pros and cons
associated with waiting for cross-data center majority nodes
confirmation, since it may not suitable for applications that require
short latency.

![MongoDB Write Durability
Pattern](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/_resampled/ScaleWidthWzc1MF0/MongoDB-Write-Durability-Pattern.12.png){height="250"}

### MongoDB read intensive pattern

This pattern is for applications that require high availability
reads. With MongoDB's master-slave replication architecture and ability
to scale up to  [49 secondary
nodes](https://docs.mongodb.com/manual/core/replica-set-members/) across
multiple data centers, it inherently supports highly available
reads, provided that the number of healthy secondary nodes in any data
center are capable of handling read traffic if one or more fail. Note
that even though the current MongoDB replica set can scale up to 50
nodes, only 7 nodes can vote during primary node failover. The following
diagram illustrates this capability.

![MongoDB Read Intensive
Pattern](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/_resampled/ScaleWidthWzc1MF0/MongoDB-Read-Intensive-Pattern.13.png){width="555"
height="250"}

### MongoDB extreme high write pattern

Use cases requiring extreme high writes can use MongoDB optional
sharding since it allows horizontal write scaling across multiple
replica sets (shards). Each shard (or replica set) stores part of the
entire dataset as defined by a predefined  [shard
key](https://docs.mongodb.com/manual/sharding/#shard-keys) of
the collection. With a well-designed shard key, MongoDB automatically
distributes and balances read/write queries to designated shards.
Although MongoDB sharding provides horizontal scale-out write
capability, this pattern incurs consequent complexity and overhead and
should be used with caution:

-   An application should start with sharding using an appropriate shard
    key from the start instead of migrating from a single replica set as
    afterthought. This is because migrating a single replica set to a
    sharded cluster is a major undertaking from both development and
    operations perspectives.
-   We recommend starting with a predefined number of shards capable of
    handling capacity and traffic in the foreseeable future. This helps
    eliminate the overhead associated with rebalancing when adding new
    shards.
-   Note that MongoDB automatic shard balancing may introduce spikes
    during chunk migration and can potentially impact performance.
-   Developers needs to understand behavior and limitation on how 
    [mongos](https://docs.mongodb.com/manual/core/distributed-queries/),
    a software router process, on queries that do not include shard key,
    such as  [scatter gather
    operations](https://docs.mongodb.com/manual/core/distributed-queries/).
-   Developers should weigh the pros and cons of the overhead associated
    with running mongos as part of application servers vs. in separate
    nodes.

The following diagram illustrates this capability.

![MongoDB Extreme High Write
Pattern](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/_resampled/ScaleWidthWzc1MF0/MongoDB-Extreme-High-Write-Pattern.14.png){height="250"}

### Couchbase resilience design pattern examples

Although Couchbase does not support write-ahead logging or quorum write,
it achieves high durability through following mechanisms:

-   Local cluster durability ---  [ReplicateTo and
    PersistTo](https://developer.couchbase.com/documentation/server/current/sdk/durability.html) functions
-   Multi-cluster durability (to be released in a future v4.x release):
    -   Multi-Cluster Awareness (MCA) --- Without application logic,
        this feature allows application developers and DBA to define
        rules on how applications should behave in the event of complete
        data center/cluster failover.
    -   [Timestamp-based Conflict
        Resolution](https://developer.couchbase.com/documentation/server/4.6/xdcr/xdcr-timestamp-based-conflict-resolution.html) (TbCR) --- Based
        on a server-synced clock, this feature provides Last-Write-Win
        (LWW) capability on bidirectional replication update conflict
        resolution to ensure correct cross-data center/cluster write
        durability.

### Couchbase local cluster write durability pattern

For local cluster durability, Couchbase provides the following two
functions through its client SDK:

-   [ReplicateTo](https://developer.couchbase.com/documentation/server/current/sdk/durability.html) --- This
    function allows writes on the same document to be successfully
    replicated in memory for all copies in the local cluster. However,
    it does not guarantee writes to be persisted on disk, which may
    result in data loss if both primary and replica nodes fail before
    that happens.
-   [PersistTo](https://developer.couchbase.com/documentation/server/current/sdk/durability.html) --- For
    increased durability, applications can use this function so that
    writes will not only be successfully replicated in memory but also
    persisted on disk in the local cluster.

Note that even with the second PersistTo function, the current Couchbase
version still does not guarantee writes to be successfully replicated to
remote data centers/clusters. (This capability is explained in the next
section, " [Couchbase Multi-cluster write durability
pattern](https://tech.ebayinc.com/engineering/practical-nosql-resilience-design-pattern-for-the-enterprise/#Cbmcwdpattern).")
The following operations illustrate how both functions work.

1.  Assume that the Couchbase topology contains four nodes per data
    center/cluster with each storing two copies of the same document
    replicated through XDCR between clusters.
    ![Couchbase Local Cluster Write Durability Pattern
    A](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Couchbase-Local-Cluster-Write-Durability-Pattern.1.15.png){width="318"
    height="250"}
2.  The application in Data Center 1 writes documentP1 to nodeN1.
    ![Couchbase Local Cluster Write Durability Pattern
    B](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Couchbase-Local-Cluster-Write-Durability-Pattern.2.16.png){height="250"}
3.  BeforeP1 is replicated to the replica node in the local cluster or
    to the remote data center/cluster, nodeN1 fails, and as a result the
    application suffers data loss.
    ![Couchbase Local Cluster Write Durability Pattern
    C](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Couchbase-Local-Cluster-Write-Durability-Pattern.3.17.png){height="250"}
4.  BeforeP1 reaches the remote data center/cluster, even thoughP1 has
    been replicated successfully in memory to the local cluster replica
    nodeN4, if bothN1 andN4 nodes fail, the application still suffers
    data loss.
    ![Couchbase Local Cluster Write Durability Pattern
    D](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Couchbase-Local-Cluster-Write-Durability-Pattern.4.18.png){width="318"
    height="250"}
5.  Using the ReplicateTo function can circumvent the failure described
    in  [step
    3](https://tech.ebayinc.com/engineering/practical-nosql-resilience-design-pattern-for-the-enterprise/#step3)
    , and using the PersistTo function can circumvent the failure
    described in  [step
    4](https://tech.ebayinc.com/engineering/practical-nosql-resilience-design-pattern-for-the-enterprise/#step4)
    , as shown in the following figure.
    ![Couchbase Local Cluster Write Durability Pattern
    E](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Couchbase-Local-Cluster-Write-Durability-Pattern.5.19.png){height="250"}
6.  Lastly, for multi-data center/cluster durability, use the design
    pattern described in " [Couchbase multi-cluster write durability
    pattern](https://tech.ebayinc.com/Cbmcwdpattern).

### Couchbase multi-cluster write durability pattern

With its Multi-Cluster Awareness and Timestamp-based Conflict Resolution
features, Couchbase supports multi-cluster durability as shown below.

![Couchbase Multi Cluster Write Durability Pattern
A](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/_resampled/ScaleWidthWzc1MF0/Couchbase-Multi-Cluster-Write-Durability-Pattern.1.20.png){height="250"}

In the absence of write-ahead logging or quorum write, and even though
Couchbase provides sufficient support for local and multi-cluster
durability, one should still ask this question: what is the likelihood
that all primary and replica nodes fail in multiple data centers or even
worse that all data centers fail completely at the same time? These two
unlikely failure scenarios are shown in the following two diagrams. We
feel that the odds are next to zero if one follows this proposed
Couchbase durability design pattern.

![Couchbase Multi Cluster Write Durability Pattern
B](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/Couchbase-Multi-Cluster-Write-Durability-Pattern.2.21.png){height="250"}
![Couchbase Multi Cluster Write Durability Pattern
C](https://tech.ebayinc.com/assets/Uploads/Blog/2017/02/Couchbase-Multi-Cluster-Write-Durability-Pattern.2b.21b.png){width="97"
height="250"}

### Couchbase read/write intensive scalability pattern

With its peer-to-peer architecture and XDCR's bidirectional
multi-cluster/data center replication capability, Couchbase affords
users the flexibility to provision clusters with different sizes and
shapes tailored for specific traffic/capacity and usage patterns. This
flexibility is shown in the following diagram. On the other hand, the
cluster-sizing calculation exercise can become complicated. This is
especially true if it involves  [Multi-Dimensional
Scaling](https://www.couchbase.com/multi-dimensional-scalability-overview).

![](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/_resampled/ScaleWidthWzc1MF0/Couchbase-ReadWrite-Intensive-Scalability-Pattern.22.png){height="250"}

### Other NoSQL design pattern examples

#### NoSQL DB-agnostic application sharding pattern

The motivation behind this design pattern is that almost all large-scale
mission-critical use cases require high availability. According to our
experience, it doesn't matter which NoSQL database you use or how
comprehensive the best practice and SOP you follow, sometimes simple
mundane maintenance tasks can jeopardize the overall database
availability. The larger the size of database, the more severe the
damage it may suffer. This design pattern offers an alternative solution
using a divide-and-conquer approach, that is, by reducing the NoSQL
database cluster to a small and manageable size through the following
mechanisms:

-   Applications shard their data using modular, hash, round robin, or
    any other suitable algorithm.
-   The DBA and Operations provide a standard-size NoSQL cluster to host
    each application-level shard.
-   If needed, each application-level shard can further use built-in
    NoSQL vendor product sharding if it is available.

Using MongoDB as an example, the following diagram illustrates this
design pattern. One caveat associated with this pattern is that it
requires a middle-tier data access layer to help direct traffic, an
effort that must not be underestimated.

![NoSQL DB Agnostic Application Sharding
Pattern](https://tech.ebayinc.com/assets/Uploads/Blog/2017/01/_resampled/ScaleWidthWzc1MF0/NoSQL-DB-Agnostic-Application-Sharding-Pattern.23.png){height="250"}

#### Future work and direction

In this blog, we described the motivation, consideration, and approach
behind our proposed NoSQL resilience design pattern. We overviewed key
differences between MongoDB and Couchbase in the context of resilience
patterns. We also walked through three NoSQL resilience design pattern
examples and a DB-agnostic application sharding pattern. In conclusion,
we would like to suggest the following future work and direction on this
topic:

-   Provide end-to-end integration of proven NoSQL design patterns with
    application frameworks and also cloud provisioning and management
    infrastructure.
-   Formalize the above NoSQL design patterns as officially supported
    products rather than just engineering patterns.
-   Add other types of resilience patterns, such as high consistency.
-   Add support for other NoSQL databases, for example, Cassandra.
-   Collaborate with NoSQL vendors and develop new resilience patterns
    for new features and capabilities.

References

-   <https://github.com/DovAmir/awesome-design-patterns>
-   <https://dzone.com/articles/mongodb-design-patterns>
-   <https://dzone.com/articles/introduction-nosql-patterns>
-   <https://tech.ebayinc.com/engineering/practical-nosql-resilience-design-pattern-for-the-enterprise/>

 



