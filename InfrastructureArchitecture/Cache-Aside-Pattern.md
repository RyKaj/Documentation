








Infrastructure Architecture - Cache-Aside Pattern
===============================================


 
Overview
--------

Load data on demand into a cache from a data store. This can improve
performance and also helps to maintain consistency between data held in
the cache and data in the underlying data store.

Context and Problem
-------------------

Applications use a cache to improve repeated access to information held
in a data store. However, it\'s impractical to expect that cached data
will always be completely consistent with the data in the data store.
Applications should implement a strategy that helps to ensure that the
data in the cache is as up-to-date as possible, but can also detect and
handle situations that arise when the data in the cache has become
stale.

Solution
--------

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

![](attachments/463533304/463533303.png)
.confluence-thumbnail .confluence-content-image-border height="150"}

If an application updates information, it can follow the write-through
strategy by making the modification to the data store, and by
invalidating the corresponding item in the cache.

When the item is next required, using the cache-aside strategy will
cause the updated data to be retrieved from the data store and added
back into the cache.

Issues and Considerations
-------------------------

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

When to use this Pattern
------------------------

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



 



