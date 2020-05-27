[comment]: [Architecture](ReadMe.MD)

Infrastructure Architecture - Disaster Recovery
=============================================

Overview
--------

When disaster strikes - more often than not, unexpectedly - the
consequences for your business can be unpredictable. They may include a
loss of revenue, damaged business reputation, destruction of the
production center, interrupted service delivery, and a loss of
credibility with your customers.

To avoid the risk of putting the business in danger, it is essential to
prepare yourself in advance by designing an effective [disaster recovery](https://www.nakivo.com/vm-disaster-recovery/) (DR)
plan. One of the main components of a DR plan is the secondary site
(also known as DR site), which will be used for data storage and rapid
recovery in case disaster strikes. This blog post discusses the role of
DR sites in the recovery process and how they can improve business
continuity.

Disaster Recovery Site
----------------------

A disaster recovery site is a location used by an organization for
restoring its IT infrastructure and business-critical operations when a
primary production center is affected by a natural or man-made disaster.
Disaster Recovery sites are often built in a remote location so as to
ensure that the disaster which has affected the main site will not
affect the secondary site as well. Creating a DR site allows an
organization to continue conducting operations and delivering services
without disruption, until the primary location is restored.

Types of Disaster Recovery Sites
--------------------------------

There are three types of backup sites: cold sites, warm sites, and hot
sites. Let's look at what each of the sites represents and what
differentiates them from one another.

Cold site

A cold site is a backup facility with little or no hardware equipment
installed. A cold site is essentially an office space with basic
utilities such as power, cooling system, air conditioning, and
communication equipment, etc. A cold site is the most cost-effective
option among the three disaster recovery sites. However, due to the fact
that a cold site doesn't have any pre-installed equipment, it takes a
lot of time to properly set it up so as to fully resume business
operations. In case of a disaster, an organization would require help
from IT personnel to migrate necessary servers and make them functional
in order to take on the workload of the primary site.

### Hot site

A hot site is a backup facility which represents a mirrored copy of the
primary production center. A hot site is equipped with all the necessary
hardware, software, and network connectivity, which allows you to
perform near real-time backup or replication of the critical data. This
way the production workload can be failed over to a DR site in a few
minutes or hours, thus ensuring minimal downtime and zero data loss. A
hot site is expected to be always online and running without disruption
so as to ensure data synchronization between the sites.

A hot site is the most expensive option among the three. Thus, it is
important to ensure that this type of a DR site is located far enough
from the production center. This way you can decrease the possibility of
a hot site being affected by the same disaster as the primary site.

### Warm site

A warm site is considered the middle ground between the cold site and
the hot site. A warm site is a backup facility that has the network
connectivity and the necessary hardware equipment already pre-installed.
However, a warm site cannot perform on the same level as the production
center because they are not equipped in the same way. Therefore, a warm
site has less operational capacity than the primary site. Moreover, data
synchronization between the primary and the secondary sites is performed
daily or weekly, which can result in minor data loss. A warm site is
perfect for organizations which operate with less critical data and can
tolerate a short period of downtime. This type of a DR site is the
second most expensive option.

Below you can see the main features of disaster recovery sites and how
they compare.

![](attachments/463534692/463534690.jpg)

![](attachments/463534692/463534691.jpg)

References

-   <https://www.nakivo.com/blog/overview-disaster-recovery-sites/>
-   <https://www.linkedin.com/posts/thomasmaurer2_azure-microsoftazure-hybridcloud-activity-6649280309571407872-OA4S/>



 



