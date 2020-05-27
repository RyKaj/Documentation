###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Infrastructure Architecture](https://github.com/RyKaj/Documentation/tree/master/InfrastructureArchitecture/README.md) |
------------



Infrastructure Architecture Cloud Architecture
==============================================
 


Patterns are a widely used concept in computer science to describe good solutions to reoccurring problems in an abstract form. Such conceptual solutions can then be applied in concrete use cases regardless of used technologies, such as software, middleware, or programming languages. [Cloud computing fundamentals](http://www.cloudcomputingpatterns.org/#cloud_computing_fundamentals)  describe cloud service models and cloud deployment types analogous to the [NIST cloud definition](http://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-145.pdf) 
. These patterns extend this definition by covering the conditions under which a certain service model and deployment type should be used for a cloud application. [Cloud offerings](http://www.cloudcomputingpatterns.org/#cloud_offerings)  describe the functionality offered by cloud providers to be used by an application for processing of workload, communication, and data storage. Again, these patterns cover the conditions under which an offering should be selected, aswell as the implications on the application. [Cloud application architectures](http://www.cloudcomputingpatterns.org/#cloud_application_architectures)  describe the general structure of the cloud application and specific application components for user interfaces, processing, and data handling. [Cloud application management](http://www.cloudcomputingpatterns.org/#cloud_application_management)  describes how these applications can be managed during runtime using additional management components, which rely on functionality provided by the application itself, cloud offerings, and the cloud environment. [Composite cloud applications](http://www.cloudcomputingpatterns.org/#composite_cloud_applications)  cover frequent combinations of patterns from all other categories in various use cases.

Computing Fundamentals
----------------------

### Community Cloud

IT resources are provided as a service to a group of customers trusting each other in order to enable collaborative elastic use of a static resource pool.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Community Cloud](http://www.cloudcomputingpatterns.org/icons/community_cloud_icon.png)      *How can the cloud properties -- on demand self-service, broad network access, pay-per-use, resource pooling, and rapid elasticity -- be provided to exclusively to a group of customers forming a community of trust?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/community_cloud/#context "Permalink") 

Whenever companies collaborate, they commonly have to access shared applications and data to do business. While these companies trust each other due to established contracts etc., the handled data and application functionality may be very sensitive and critical to their business.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/community_cloud/#solution "Permalink")

IT resources required by all collaborating partners are offered in a controlled environment accessible only by the community of companies that generally trust each other.

![Community Cloud](http://www.cloudcomputingpatterns.org/sketches/community_cloud_sketch.png) 
 

#### Continuously Changing Workload

IT resources with a utilization that grows or shrinks constantly over time experience Continuously Changing Workload.


#### [Context Permalink](http://www.cloudcomputingpatterns.org/continuously_changing_workload/#context "Permalink") 

Many applications experience a long term change in workload.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/continuously_changing_workload/#solution "Permalink")  

Continuously Changing Workload is characterized by an ongoing continuous growth or decline of the utilization. Elasticity of clouds enables applications experiencing Continuously Changing Workload to provision or decommission resources with the same rate as the workload changes.

![Unpredictable Workload](http://www.cloudcomputingpatterns.org/sketches/continuously_changing_workload_sketch.png) 
 

### Hybird Cloud

Different clouds and static data centers are integrated to form a homogeneous hosting environment.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Hybrid Cloud](http://www.cloudcomputingpatterns.org/icons/hybrid_cloud_icon.png)      *How can the cloud properties -- on demand self-service, broad network access, pay-per-use, resource pooling, and rapid elasticity -- be provided across clouds and other environments?*
  ---------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/hybrid_cloud/#context "Permalink") 

A company is likely to use a large set of applications to support its business, which have versatile requirements making different Cloud Deployment Models suitable to host them.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/hybrid_cloud/#solution "Permalink")   

[Private Clouds](http://www.cloudcomputingpatterns.org/private_cloud/), [Public Clouds](http://www.cloudcomputingpatterns.org/public_cloud/), [Community Clouds](http://www.cloudcomputingpatterns.org/community_cloud/), and static data centers are integrated to deployed applications to the hosting environment best suited for their requirements while interconnection of these environments.

![Hybrid Cloud](http://www.cloudcomputingpatterns.org/sketches/hybrid_cloud_sketch.png) 
 

### Infrastructure as a Service (IaaS)

Providers share physical and virtual hardware IT resources between customers to enable self-service, rapid elasticity, and pay-per-use pricing.



#### [Context Permalink](http://www.cloudcomputingpatterns.org/infrastructure_as_a_service/#context "Permalink") 

In the scope of [Periodic Workloads](http://www.cloudcomputingpatterns.org/peridodic_workload)  with reoccurring peaks and the special case of [Once-in-a-lifetime Workloads](http://www.cloudcomputingpatterns.org/once_in_a_lifetime_workload) with one dramatic increase in workload, IT resources have to be provisioned flexibly.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/infrastructure_as_a_service/#solution "Permalink")


A provider offers physical and virtual hardware, such as servers, storage and networking infrastructure that can be provisioned and decommissioned quickly through a self-service interface.

![Infrastructure as a Service (IaaS)](http://www.cloudcomputingpatterns.org/sketches/infrastructure_as_a_service_sketch.png) 
 

### Platform as a Service (PaaS)

Providers share IT resources providing an application hosting environment between customers to enable self-service, rapid elasticity, and pay-per-use pricing.



#### [Context Permalink](http://www.cloudcomputingpatterns.org/platform_as_a_service/#context "Permalink") 

If many customers require similar hosting environments for their applications, there are many redundant installations resulting in an inefficient use of the overall cloud.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/platform_as_a_service/#solution "Permalink")


A cloud provider offers managed operating systems and middleware. Management operations are handled by the provider, such as the elastic scaling and failure resiliency of hosted applications.

![Platform as a Service (PaaS)](http://www.cloudcomputingpatterns.org/sketches/platform_as_a_service_sketch.png) 
 

### Software as a Service (SaaS)

Providers share IT resources providing human-usable application software between customers to enable self-service, rapid elasticity, and pay-per-use pricing.


  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------
  ![Software as a Service (SaaS)](http://www.cloudcomputingpatterns.org/icons/software_as_a_service_icon.png)      *How can customers share a provider-supplied software application so that it can be used on-demand with a pay-per-use pricing model?*
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/software_as_a_service/#context "Permalink") }

Small and medium enterprises may not have the manpower and know-how to develop custom software applications. Other applications have become commodity and are used by many companies, for example, office suites, collaboration software, or communications software.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/software_as_a_service/#solution "Permalink")

A provider offers a complete software application to customers who may use it on-demand via a self-service interface.

![Software as a Service (SaaS)](http://www.cloudcomputingpatterns.org/sketches/software_as_a_service_sketch.png) 
 

### Once In a Lifetime Workload

IT resources with an equal utilization over time disturbed by a strong peak occurring only once experience Once-in-a-lifetime Workload.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------
  ![Once-in-a-lifetime Workload](http://www.cloudcomputingpatterns.org/icons/once_in_a_lifetime_workload_icon.png)      *How can equal utilization with a one-time peak be characterized and how can applications experiencing this workload benefit from cloud computing?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/once_in_a_lifetime_workload/#context "Permalink") 

As a special case of [Periodic
Workload](http://www.cloudcomputingpatterns.org/periodic_workload/), the peaks of periodic utilization can occur only once in a very long timeframe. Often, this peak is known in advance as it correlates to a certain event or task.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/once_in_a_lifetime_workload/#solution "Permalink") 

The elasticity of a cloud is used to obtain IT resources necessary. The provisioning and decommissioning of IT resources can often be realized as a manual task, because it is performed at a known point in time.

![Once-in-a-lifetime Workload](http://www.cloudcomputingpatterns.org/sketches/once_in_a_lifetime_workload_sketch.png) 
 

### Periodic Workload

IT resources with a peaking utilization at reoccurring time intervals experience periodic workload.
 
  ------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Periodic Worload](http://www.cloudcomputingpatterns.org/icons/periodic_workload_icon.png)      *How can a periodically peaking utilization over time be characterized and how can applications experiencing this workload benefit from cloud computing?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/periodic_workload/#context "Permalink")  

In our real lives, periodic tasks and routines are very common. For example, monthly paychecks, monthly telephone bills, yearly car checkups, weekly status reports, or the daily use of public transport during rush hour, all these tasks and routines occur in well-defined intervals.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/periodic_workload/#solution "Permalink") 

From a customer perspective the cost-saving potential in scope of Periodic Workload is to use a provider with a pay-per-use pricing model allowing the decommissioning of resources during non-peak times.

![Periodic Workload](http://www.cloudcomputingpatterns.org/sketches/periodic_workload_sketch.png) 
 

### Private Cloud

IT resources are provided as a service exclusively to one customer in order to meet high requirements on privacy, security, and trust while enabling elastic use of a static resource pool as good as possible.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Private Cloud](http://www.cloudcomputingpatterns.org/icons/private_cloud_icon.png)      *How can the cloud properties -- on demand self-service, broad network access, pay-per-use, resource pooling, and rapid elasticity -- be provided in environments with high privacy, security and trust requirements?*
  ------------------------------------------------------------------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/private_cloud/#context "Permalink")  

Many factors, such as legal limitations, trust, and security regulations, motivate dedicated, company-internal hosting environments only accessible by employees and applications of a single company.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/private_cloud/#solution "Permalink") 

Cloud computing properties are enabled in a company-internal data center. Alternatively, the Private Cloud may be hosted exclusively in  the data center of an external provider, then referred to as outsourced Private Cloud. Sometimes, [Public Cloud](http://www.cloudcomputingpatterns.org/private_cloud/)  providers also offer means to create an isolated portion of their cloud made accessible to only one customer: a virtual Private Cloud.

![Private Cloud](http://www.cloudcomputingpatterns.org/sketches/private_cloud_sketch.png) 
 

### Public Cloud

IT resources are provided as a service to a very large customer group in order to enable elastic use of a static resource pool.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Public Cloud](http://www.cloudcomputingpatterns.org/icons/public_cloud_icon.png)      *How can the cloud properties -- on demand self-service, broad network access, pay-per-use, resource pooling, and rapid elasticity -- be provided to a large customer group?*
  ---------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/public_cloud/#context "Permalink")  

A provider offering IT resources according to [IaaS](http://www.cloudcomputingpatterns.org/infrastructure_as_a_service/), [PaaS](http://www.cloudcomputingpatterns.org/platform_as_a_service/), or [SaaS](http://www.cloudcomputingpatterns.org/software_as_a_service/)  has to maintain physical data centers. IT resources, nevertheless, shall be made accessible dynamically.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/public_cloud/#solution "Permalink")

The hosting environment is shared between many customers possibly reducing the costs for an individual customer. Leveraging economies of scale enables a dynamic use of resources, because workload peaks of some customers occur during times of low workload of other customers.

![Public Cloud](http://www.cloudcomputingpatterns.org/sketches/public_cloud_sketch.png) 
 

### Static Workload

IT resources with an equal utilization over time experience Static Workload.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------
  ![Static Workload](http://www.cloudcomputingpatterns.org/icons/static_workload_icon.png)      *How can an equal utilization be characterized and how can applications experiencing this workload benefit from cloud computing?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/static_workload/#context "Permalink") 

Static Workloads are characterized by a more-or-less flat utilization profile over time within certain boundaries.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/static_workload/#solution "Permalink") 

An application experiencing Static Workload is less likely to benefit from an elastic cloud that offers a pay-per-use billing, because the number of required resources is constant.

![Static Workload](http://www.cloudcomputingpatterns.org/sketches/static_workload_sketch.png) 
 

### Unpredictable Workload

IT resources with a random and unforeseeable utilization over time experience unpredictable workload.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------------------------------------------------------------------------------------------------------------------------
  ![Unpredictable Workload](http://www.cloudcomputingpatterns.org/icons/unpredictable_workload_icon.png)      *How can random and unforeseeable utilization be characterized and how can applications experiencing this workload benefit from cloud computing?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/unpredictable_workload/#context "Permalink")

Random workloads are a generalization of [Periodic Workloads](http://www.cloudcomputingpatterns.org/periodic_workload/)  as they require elasticity but are not predictable. Such workloads occur quite often in the real world.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/unpredictable_workload/#solution "Permalink") 

Unplanned provisioning and decommissioning of IT resources is required. The necessary provisioning and decommissioning of IT resources is, therefore, automated to align the resource numbers to changing workload.

![Unpredictable Workload](http://www.cloudcomputingpatterns.org/sketches/unpredictable_workload_sketch.png) 
 

Cloud Offerings
---------------

### Environments

#### Elastic Infrastructure

Hosting of virtual servers, disk storage, and configuration of network connectivity is offered via a self-service interface over a network.
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/elastic_infrastructure/#context "Permalink")  

An application experiences [Periodic Workload](http://www.cloudcomputingpatterns.org/periodic_workload/), [Once-in-a-lifetime Workload](http://www.cloudcomputingpatterns.org/once_in_a_lifetime_workload), [Unpredictable Workload](http://www.cloudcomputingpatterns.org/unpredictable_workload/), or [Continuously Changing Workload](http://www.cloudcomputingpatterns.org/continuously_changing_workload/), the number of IT resources, such as servers, should be adjusted dynamically. In scope of the [IaaS](http://www.cloudcomputingpatterns.org/infrastructure_as_a_service/)  service model, the applications' runtime infrastructure, thus, must support dynamic provisioning and decommissioning of virtual servers, disk storage and network connectivity.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/elastic_infrastructure/#solution "Permalink") 

An Elastic Infrastructure provides preconfigured virtual server images, storage and network connectivity that may be provisioned by customers using a self-service interface. Monitoring information is provided to inform about resource utilization required for traceable billing and automation of management tasks.

![Elastic Infrastructure](http://www.cloudcomputingpatterns.org/sketches/elastic_infrastructure_sketch.png) 
 

#### Elastic Platform

Middleware for the execution of custom applications, their communication, and data storage is offered via a self-service interface over a network.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------------------------------------------------------------------------------------
  ![Elastic Platform](http://www.cloudcomputingpatterns.org/icons/elastic_platform_icon.png)      *How do Cloud Offerings providing Execution Environments behave and how should they be used in applications?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/elastic_platform/#context "Permalink")  

One of the fundamental cloud properties is the sharing of resources among a large number of customers to leverage economy of scale. Extending resource sharing between customers to the operating systems and middleware increases the beneficial effects of economies of scale as the utilization of these resources can be increased.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/elastic_platform/#solution "Permalink") 

Application components of different customers are hosted on shared middleware provided and maintained by the provider. Customers may deploy custom application components to this middleware using a self-service interface. This unification enables resource sharing and an automation of certain management tasks on the provider side, for example, provisioning of applications, update management.

![Elastic Platform](http://www.cloudcomputingpatterns.org/sketches/elastic_platform_sketch.png) 
 

#### Environment-base Availability

A cloud provider guarantees the availability of the environment hosting individual nodes, such as virtual servers or hosted application components.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Environment-based Availability](http://www.cloudcomputingpatterns.org/icons/environment_based_availability_icon.png)      *How can providers express availability in an environmental-centric fashion, so that customers may estimate the availability of hosted applications?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/environment_based_availability/#context "Permalink") 

A cloud provider offers an [Elastic Infrastructure](http://www.cloudcomputingpatterns.org/elastic_infrastructure/)  or an [Elastic Platform](http://www.cloudcomputingpatterns.org/elastic_platform/)  on which customers may deploy application components. The availability of this environment has to be expressed so that customers may match their requirements.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/environment_based_availability/#solution "Permalink")  

The provider assures availability for the provided environment, thus, for the availability of the [Elastic Platform](http://www.cloudcomputingpatterns.org/elastic_platform/) 
or the [Elastic Infrastructure](http://www.cloudcomputingpatterns.org/elastic_infrastructure/)  as a whole, for example, the availability for at-least-once provisioned component or virtual server and the availability to provision replacements in case of failures is assured. There is no notion of availability for individual application components or virtual servers deployed in this environment.

![Environment-based Availability](http://www.cloudcomputingpatterns.org/sketches/environment_based_availability_sketch.png) 
 

#### Node-based Availability

A cloud provider guarantees the availability of individual nodes, such as individual virtual servers, middleware components or hosted application components.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------
  ![Node-based Availability](http://www.cloudcomputingpatterns.org/icons/node_based_availability_icon.png)      *How can providers express availability in a node-centric fashion, so that customers may estimate the availability of hosted applications?*
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/node_based_availability/#context "Permalink") 

A provider offers an [Elastic Infrastructure](http://www.cloudcomputingpatterns.org/elastic_infrastructure/)  or an [Elastic Platform](http://www.cloudcomputingpatterns.org/elastic_platform/)  and needs a means to express the availability for the offerings from which the customer may then compute the availability of the hosted application. First, conditions are defined that have to be fulfilled by an available offering. Second, the timeframe needs to be expressed for which the provider assures this availability.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/node_based_availability/#solution "Permalink")  

The provider assures availability for each hosted application component, which is defined to be available if it is reachable and performs its function as advertised, i.e., it provides correct results. This timeframe is often expressed as a percentage. An availability of 99.95%, thus, means that a hosted component will be available during 99.95% of the time it is hosted at the provider.

![Node-based Availability](http://www.cloudcomputingpatterns.org/sketches/node_based_availability_sketch.png) 
 

### Processing Offerings

#### Execution Environment

To avoid duplicate implementation of functionality, application components are deployed to a hosting environment providing middleware services as well as often used functionality.
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/execution_environment/#context "Permalink") 

Applications often use similar functions, for example, to access networking interfaces, display user interfaces, access storage of the server etc. In this case, each application implements similar components that could be shared with other applications. Sharing such common functionality between applications would also result in a better utilization of the environment.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/execution_environment/#solution "Permalink") 

Common functionality is summarized in an Execution Environment providing functionality in platform libraries to be used in custom application implementations and in the form of the middleware. The environment, thus, executes custom application components and provides common functionality for data storages, communication etc.

![Execution Environment](http://www.cloudcomputingpatterns.org/sketches/execution_environment_sketch.png) 
 

#### Hypervisor

To enable the elasticity of clouds, the time required to provision and decommission servers is reduced through hardware virtualization.

 
  ------------------------------------------------------------------------------------------------------------------------------------------ -----------------------------------------------------------------------------------------------------
  ![Hypervisor](http://www.cloudcomputingpatterns.org/icons/hypervisor_icon.png)      *How can virtual hardware that has been abstracted from physical hardware be used in applications?*
  ------------------------------------------------------------------------------------------------------------------------------------------ -----------------------------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/hypervisor/#context "Permalink") 

If multiple applications are deployed on a physical server they may have to consider the other applications in their configuration. For example, if applications require the same network ports, access the same directories in the local file system etc. This sharing of common underlying physical hardware between different applications shall be simplified while also reducing dependencies of the application on the physical server.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/hypervisor/#solution "Permalink")  

A Hypervisor abstracts the hardware of a shared physical server into virtualized hardware. On this virtual hardware, different operating systems and middleware are installed to host applications sharing the physical server while being isolated from each other regarding the use of physical hardware, such as central processing units (CPU), memory, disk storage, and networking.

![Hypervisor](http://www.cloudcomputingpatterns.org/sketches/hypervisor_sketch.png) 
 

#### Map Reduce

Large data sets to be processed are divided into smaller data chunks and distributed among processing application components. Individual results are later consolidated.
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/map_reduce/#context "Permalink") 

Cloud applications often have to handle very large amounts of data, which have to be processed efficiently. As [Distributed Applications](http://www.cloudcomputingpatterns.org/distributed_application/)  are designed to scale out, data processing should be distributed among multiple application component instances in a similar means. Afterwards, results of these distributed components have to be consolidated.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/map_reduce/#solution "Permalink")  

A large data set to be processed is split up and mapped to multiple application components handling data processing. Data Processing Components simultaneously execute the query to be performed on the assigned data chunks. Afterwards, the individual results of all Processing Components are consolidated or reduced into one result data set. During this reduction, additional functions, such calculations of sums, average values etc. may be used.

![Map Reduce](http://www.cloudcomputingpatterns.org/sketches/map_reduce_sketch.png) 
 

### Storage Offerings

#### Block Storage

Centralized storage is integrated into servers as a local hard drive managed by the operating system to enable access to this storage via the local file system.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------ --------------------------------------------------------------------------------------------
  ![Block Storage](http://www.cloudcomputingpatterns.org/icons/block_storage_icon.png)      *How can central storage be accessed as a local drive by servers and hosted applications?*
  ------------------------------------------------------------------------------------------------------------------------------------------------ --------------------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/block_storage/#context "Permalink") 

Virtual and non-virtualized servers offered as [Infrastructure as a Service
(IaaS)](http://www.cloudcomputingpatterns.org/infrastructure_as_a_service/) 
can be managed significantly easier if they do not store any state information locally, i.e., on their (virtual) hard drives. This eases their provisioning, decommissioning, and failure handling.

### [Solution Permalink](http://www.cloudcomputingpatterns.org/block_storage/#solution "Permalink") 

Centralized storage is accessed by servers as if it was a local hard drive, also referred to as block device.

![Block
Storage](http://www.cloudcomputingpatterns.org/sketches/block_storage_sketch.png) 
 

#### Blob Storage

Data is provided in form of large files that are made available in a file system-like fashion by Storage Offerings that provides elasticity.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------
  ![Blob Storage](http://www.cloudcomputingpatterns.org/icons/blob_storage_icon.png)      *How can large files be stored, organized and made available over a network?*
  ---------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/blob_storage/#context "Permalink") 

Distributed cloud applications often need to handle large data elements, also referred to as binary large objects (blob). Examples are virtual server images managed in an [Elastic Infrastructure](http://www.cloudcomputingpatterns.org/elastic_infrastructure/), pictures, or videos.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/blob_storage/#solution "Permalink") 

Data elements are organized in a folder hierarchy similar to a local file system. Each data element is given a unique identifier comprised of its location in the folder hierarchy and a file name. This unique identifier is passed to the storage offerings to retrieve a file over a network.

![Blob
Storage](http://www.cloudcomputingpatterns.org/sketches/blob_storage_sketch.png) 
 

#### Eventual Consistency

If data is stored at different locations (replicas) to improve response time and avoid data loss in case of failures. Performance and the availability of data in case of network partitioning are enabled by ensuring data consistency eventually and not at all times.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Eventual Consistency](http://www.cloudcomputingpatterns.org/icons/eventual_consistency_icon.png)      *How can data be distributed among replicas with focus on increased availability and performance, while being resilient towards connectivity problems?*
  -------------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/eventual_consistency/#context "Permalink") 

Using multiple replicas of data is vital to ensure resiliency of a storage offering towards resource failures. Keeping all these replicas in a consistent state, however, requires a significant overhead as multiple or all data replicas have to be accessed during read and write operations.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/eventual_consistency/#solution "Permalink")  

The consistency of data is relaxed. This reduces the number of replicas that have to be accessed during read and write operations. Data alterations are eventually transferred to all replicas by propagating them asynchronously over the connection network.

![Eventual Consistency](http://www.cloudcomputingpatterns.org/sketches/eventual_consistency_sketch.png) 
 

#### Key-Value Storage

Semi-structured or unstructured data is stored with limited querying support but high-performance, availability, and flexibility.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------
  ![Key-Value Storage](http://www.cloudcomputingpatterns.org/icons/key_value_storage_icon.png)      *How can key-value elements be stored to support scale out and an adjustable data structure?*
  -------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/key_value_storage/#context "Permalink") 

To ensure availability and performance, a data storage offering shall be distributed among different IT resources and locations. Furthermore, changes of requirements or the fact that customers share a storage offering and have different requirements, raises the demand for a flexible data structure. as data structure validation during queries requires high-performance connectivity between distributed resources storing the data elements.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/key_value_storage/#solution "Permalink")

Pairs of identifiers (key) and associated data (value) are stored. No database schema or only a very limited one are supported to enforce a data structure. The expressiveness of queries is reduced significantly in favor of scalability and configurability: semi-structured on unstructured data can be scaled out among many IT resources without the need to access many of them for the evaluation of expressive queries.

![Key-Value Storage](http://www.cloudcomputingpatterns.org/sketches/key_value_storage_sketch.png) 
 

#### Relational Database

Data is structured according to a schema that is enforced during data manipulation and enables expressive queries of handled data.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------------ --------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Relational Database](http://www.cloudcomputingpatterns.org/icons/relational_database_icon.png)      *How can data elements be stored so that relations between them can be expressed and expressive queries are enabled to retrieve required information effectively?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------ --------------------------------------------------------------------------------------------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/relational_database/#context "Permalink") 

Handled data is often comprised of large numbers of similar data elements. These data elements have certain dependencies among each other. If such structured data is queried, clients make certain assumptions about the data structure and the consistency of relations between the retrieved data elements.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/relational_database/#solution "Permalink") 

Data elements are stored in tables where each column represents an attribute of a data element. Table columns may have dependencies in the way that entries in one table column must also be present in a corresponding column of a different table. These dependencies are enforced during data manipulations.

![Relational Database](http://www.cloudcomputingpatterns.org/sketches/relational_database_sketch.png) 
 

#### Strict Consistency

Data is stored at different locations (replicas) to improve response time and to avoid data loss in case of failures while consistency of replicas is ensured at all times.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------
  ![Strict Consistency](http://www.cloudcomputingpatterns.org/icons/strict_consistency_icon.png)      *How can data be distributed among replicas to increase availability, while ensuring data consistency at all times?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/strict_consistency/#context "Permalink") 

To ensure failure tolerance, a storage offering duplicates data among multiple replicas. These replicas store the same set of data, so in case any of these replicas is lost, data may still be obtained and recovered from the other replicas.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/strict_consistency/#solution "Permalink")  

Data is duplicated among several replicas to increase availability. A subset of data replicas is accessed by read and write operations. The ratio of the number of replicas accessed during read (r) and write (w) operations guarantees consistency: n \< r + w

![Strict Consistency](http://www.cloudcomputingpatterns.org/sketches/strict_consistency_sketch.png) 
 

### Communication Offerings

#### At-least-once Delivery

In case of failures that lead to message loss or take too long to
recover from, messages are retransmitted to assure they are delivered at least once.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------ -------------------------------------------------------------------------------------------------------------------
  ![At-least-once Delivery](http://www.cloudcomputingpatterns.org/icons/at_least_once_delivery_icon.png)      *How can communication partners or a Message-oriented Middleware ensure that messages are received successfully?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------ -------------------------------------------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/at_least_once_delivery/#context "Permalink")

Sometimes, message duplicity can be coped with by the application using a [Message-oriented Middleware](http://www.cloudcomputingpatterns.org/message_oriented_middleware/). Therefore, for scenarios where message duplicates are uncritical, it shall still be ensured that messages are received.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/at_least_once_delivery/#solution "Permalink")  

For each message retrieved by a receiver an acknowledgement is sent back to the message sender. In case this acknowledgement is not received after a certain time frame, the message is resend.

![At-least-once Delivery](http://www.cloudcomputingpatterns.org/sketches/at_least_once_delivery_sketch.png) 
 

#### Exactly-once Delivery

For many critical systems duplicate messages are inacceptable. The messaging system ensures that each message is delivered exactly once by filtering possible message duplicates automatically.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------
  ![Exactly-once Delivery](http://www.cloudcomputingpatterns.org/icons/exactly_once_delivery_icon.png)      *How can it be assured that a message is delivered only exactly once to a receiver?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/exactly_once_delivery/#context "Permalink") 

Message duplicity is a very critical design issue for [Distributed Applications](http://www.cloudcomputingpatterns.org/distributed_application/)  and or application components that exchange messages via a [Message-oriented Middleware](http://www.cloudcomputingpatterns.org/message_oriented_middleware/).

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/exactly_once_delivery/#solution "Permalink")

Upon creation, each message is associated with a unique message identifier. This identifier is used to filter message duplicates during their traversal from sender to receiver.

![Exactly-once Delivery](http://www.cloudcomputingpatterns.org/sketches/exactly_once_delivery_sketch.png) 
 

#### Message-oriented Middleware

Asynchronous message-based communication is provided while hiding complexity resulting from addressing, routing, or data formats from communication partners to make interaction robust and flexible.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------
  ![Message-oriented Middleware](http://www.cloudcomputingpatterns.org/icons/message_oriented_middleware_icon.png)      *How can communication partners exchange information asynchronously with a communication partner?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/message_oriented_middleware/#context "Permalink")

The application components of a [Distributed 
Application](http://www.cloudcomputingpatterns.org/distributed_application/)  are hosted on multiple cloud resources and have to exchange information with each other. Often, the integration with other cloud applications and non-cloud applications is also required.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/message_oriented_middleware/#solution "Permalink") 

Communication partners exchange information asynchronously using messages. The message-oriented middleware handles the complexity of addressing, availability of communication partners and message format transformation.

![Message-oriented Middleware](http://www.cloudcomputingpatterns.org/sketches/message_oriented_middleware_sketch.png) 
 

#### Timeout-based Delivery

Clients acknowledge message receptions to ensure that messages are received properly.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------------------------------------------------------
  ![Timeout-based Delivery](http://www.cloudcomputingpatterns.org/icons/timeout_based_delivery_icon.png)      *How can it be ensured that messages are only deleted from a message queue if they have been received successfully at least once?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/timeout_based_delivery/#context "Permalink") 

In addition to ensuring that messages are not lost while they are traversing a [Message-oriented Middleware](http://www.cloudcomputingpatterns.org/message_oriented_middleware/)  it may, thus, also be required to assure that they are actually received by a client before they are deleted from a message queue.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/timeout_based_delivery/#solution "Permalink")  

To assure that a message is properly received, it is not deleted immediately after it has been read by a client, but is only marked as being invisible. In this state a message may not be read by another client. After a client has successfully read a message, it sends an acknowledgement to the message queue upon which reception the message is deleted.

![Timeout-based Delivery](http://www.cloudcomputingpatterns.org/sketches/timeout_based_delivery_sketch.png) 
 

#### Transaction-based Delivery

Clients retrieve messages under a transactional context to ensure that messages are received by a handling component.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------
  ![Transaction-based Delivery](http://www.cloudcomputingpatterns.org/icons/transaction_based_delivery_icon.png)      *How can it be ensured that messages are only deleted from a message queue if they have been received successfully?*
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/transaction_based_delivery/#context "Permalink")  

While a [Message-oriented Middleware](http://www.cloudcomputingpatterns.org/message_oriented_middleware/) 
can control traversing messages, it may be necessary to assure that messages are actually received successfully from a message queue by the client.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/transaction_based_delivery/#solution "Permalink") 

The [Message-oriented Middleware](http://www.cloudcomputingpatterns.org/message_oriented_middleware/) 
and the client reading a message from a queue participate in a transaction. All operations involved in the reception of a message are, therefore, performed under one transactional context guaranteeing ACID behavior.

![Transaction-based Delivery](http://www.cloudcomputingpatterns.org/sketches/transaction_based_delivery_sketch.png) 
 

#### Virtual Networking

Networking resources are virtualized to empower customers to configure networks, firewalls, and remote access using a self-service interface.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------
  ![Virtual Networking](http://www.cloudcomputingpatterns.org/icons/virtual_networking_icon.png)      *How can network connectivity between IT resources hosted in a cloud be configured dynamically and on-demand?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------
 

##### [Context Permalink](http://www.cloudcomputingpatterns.org/virtual_networking/#context "Permalink")  

Application components deployed on [Elastic 
Infrastructures](http://www.cloudcomputingpatterns.org/elastic_infrastructure/)  and [Elastic Platforms](http://www.cloudcomputingpatterns.org/elastic_platform/)  rely on physical network hardware to communicate with each other and the outside world. On this networking layer, different customers shall be isolated from each.

##### [Solution Permalink](http://www.cloudcomputingpatterns.org/virtual_networking/#solution "Permalink") 

Physical networking resources, such as networking interface cards, switches, routers etc. are abstracted to virtualized ones. These Virtual Networking resources may share the same physical networking resources. Configuration is handled by customers through self-service interfaces.

![Virtual Networking](http://www.cloudcomputingpatterns.org/sketches/virtual_networking_sketch.png) 
 

Application Architectures
-------------------------

### Application Component Proxy

An application component is made available in an environment from where it cannot be accessed directly by deploying an Application Component Proxy. The communication between this proxy and the application component is initiated and maintained from the environment where communication is unrestricted.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------
  ![Application Component Proxy](http://www.cloudcomputingpatterns.org/icons/application_component_proxy_icon.png)      *How can an application component be accessed if direct access to its hosting environment is restricted?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/application_component_proxy/#context "Permalink")  

Application components of a [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/)  are deployed in different Cloud Environments that form a [Hybrid Cloud](http://www.cloudcomputingpatterns.org/hybrid_cloud/). These environments often have different privacy, security, and trust properties. The communication between environments is often restricted through the use of firewalls. However, application components hosted in unrestricted environments may have to access application components hosted in a restricted environment.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/application_component_proxy/#solution "Permalink")  

The interface of a restricted application component is duplicated to form a proxy component. Synchronous and asynchronous communication with this proxy component is initiated and maintained from the restricted environment that may access the unrestricted environment directly.

![Application Component Proxy](http://www.cloudcomputingpatterns.org/sketches/application_component_proxy_sketch.png) 
 

### Batch Processing Component

Requests are delayed until environmental conditions make their processing feasible.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------
  ![Batch Processing Component](http://www.cloudcomputingpatterns.org/icons/batch_processing_component_icon.png)      *How can asynchronous processing requests be delayed to be handled when conditions for their processing are optimal?*
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/batch_processing_component/#context "Permalink") 

[Distributed Applications](http://www.cloudcomputingpatterns.org/distributed_application/)  assing processing functionality to different components to them independently. If such [Processing Components](http://www.cloudcomputingpatterns.org/processing_component/)  are accessed asynchronously, certain conditions may make it unfeasible to process the requests immediately: seldom accesses to processing functionality, powerful Processing Component instances accessed continuously, and environmental conditions, such as resource costs.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/batch_processing_component/#solution "Permalink")

Asynchronous processing requests are accepted at all times, but stored them until conditions are optimal for their processing. Based on the number of stored requests, environmental conditions, and custom rules, components are instantiated to handle the requests. Requests are only processed under non-optimal conditions if they cannot be delayed any longer.

![Batch Processing Component](http://www.cloudcomputingpatterns.org/sketches/batch_processing_component_sketch.png) 
 

### Data Abstractor

The data provided to users or other application components is abstracted to inherently support eventually consistent data storage through the use of abstractions and approximations.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Data Abstractor](http://www.cloudcomputingpatterns.org/icons/data_abstractor_icon.png)      *How can eventually consistent data be presented, so that possible inconsistencies are hidden from other application components and application users?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/data_abstractor/#context "Permalink")

If a [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/)  using eventually consistent [Storage Offerings](http://www.cloudcomputingpatterns.org/cloud_offerings/#storage_offerings)  is designed for consistent data, data consistency could be reassured by application components, such as the [Data Access Component](http://www.cloudcomputingpatterns.org/data_access_component/). However, this can void the benefits introduced by eventually consistency regarding performance and availability.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/data_abstractor/#solution "Permalink") 

The style of data representation is adjusted to allow retrieved data to be eventually consistent. The data representation always reflects that the consistent state is unknown by approximating values or abstracting them into more general ones, such as progress bars, traffic lights, or change tendencies (increase / decrease).

![Data Abstractor](http://www.cloudcomputingpatterns.org/sketches/data_abstractor_sketch.png) 
 

### Data Access Component

Functionality to store and access data elements is provided by special components that isolate complexity of data access, enable additional data consistency, and ensure adjustability of handled data elements to meet different customer requirements.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Data Access Component](http://www.cloudcomputingpatterns.org/icons/data_access_component_icon.png)      *How can the complexity of data storage due to access protocols and data consistency be hidden and isolated while ensuring data structure configurability?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/data_access_component/#context "Permalink") 

Handling the complexity of accessing data, i.e., handling of authorization, querying for data, failure handling etc. tightly couples application components to the used storage offering and complicates the implementation of these components as a lot of the idiosyncrasies of data handling have to be respected by them. Instead, different data sources should be integrated to provide a unified data access to other application components. Also, data may be stored at different cloud providers that have to be integrated as well.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/data_access_component/#solution "Permalink") 

Access to different data sources is integrated by a Data Access Component. This component coordinates all data manipulation. In case a storage offering shall be replaced or the interface of a storage offering changes, the Data Access Component is the only component that has to be adjusted.

![Data Access Component](http://www.cloudcomputingpatterns.org/sketches/data_access_component_sketch.png) 
 

### Dedicated Component

Components providing critical functionality shall be provided exclusively to tenants while still allowing other components to be shared between tenants.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------------ -------------------------------------------------------------------------------------------------------
  ![Dedicated Component](http://www.cloudcomputingpatterns.org/icons/dedicated_component_icon.png)      *How can application components that cannot be shared be integrated into a multi-tenant application?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------ -------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/dedicated_component/#context "Permalink") 

A [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/)  is offered to multiple tenants. These tenants share IT resources required by applications provided to them.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/dedicated_component/#solution "Permalink") 

Dedicated application components are provided exclusively for each tenant using the application.

![Dedicated Component](http://www.cloudcomputingpatterns.org/sketches/dedicated_component_sketch.png) 
 

### Distributed Application

A cloud application divides provided functionality among multiple application components that can be scaled out independently.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------
  ![Distributed Application](http://www.cloudcomputingpatterns.org/icons/distributed_application_icon.png)      *How can application functionality be decomposed to be handled by separate application components?*
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/distributed_application/#context "Permalink")

Applications have to respect the distribution and the scaling-out support of cloud environments in their architecture to efficiently benefit from it. Cloud applications, therefore, should to rely on multiple, possibly redundant IT resources. This can especially be the case if the cloud provider assures [Environment-based Availability](http://www.cloudcomputingpatterns.org/environment_based_availability/) 
-- the availability of the complete environment and not of single IT resources hosted in it.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/distributed_application/#solution "Permalink")

The functionality of the application is divided into multiple independent components that provide a certain function. This componentization of application functionality introduces a logical decomposition of the application. These logical components are subsumed to multiple tiers to denote that they shall be deployed together physically, i.e., on one server (cluster).

![Distributed Application](http://www.cloudcomputingpatterns.org/sketches/distributed_application_sketch_1.png) 
 

Layer-based decomposition divides the application into separate logical layers. Components are restricted to access components of the same layer or one layer below.

![Distributed Application](http://www.cloudcomputingpatterns.org/sketches/distributed_application_sketch_2.png) 
 

Process-based decomposition focuses on the business processes supported by the application. These processes are comprised out of activities that are executed in a specific order. Functionality is divided into components with respect to the supported business activity.

![Distributed Application](http://www.cloudcomputingpatterns.org/sketches/distributed_application_sketch_3.png) 
 

Pipes-and-filters-based decomposition focues on for data-centric processing of an application. Each filter provides a certain function that is performed on input data and produces output data after processing. Multiple filters are interconnected with pipes, i.e, through messaging.

### Idempotent Processor

Application functions detect duplicate messages and inconsistent data or are designed to be immune to these conditions.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------
  ![Idempotent Processor](http://www.cloudcomputingpatterns.org/icons/idempotent_processor_icon.png)      *How can an application component cope with message duplicates or data inconsistencies that could lead to duplicate function execution?*
  -------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/idempotent_processor/#context "Permalink")

In case of [Storage 
Offerings](http://www.cloudcomputingpatterns.org/cloud_offerings/#storage_offerings)  displaying [Eventual Consistency](http://www.cloudcomputingpatterns.org/eventual_consistency/), application components can possibly read obsolete information that has already been processed. Still, the component may choose to process the data again as changes cannot be seen. The same problem arises, if application components of a [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/)  exchange information asynchronously via a [Message-oriented Middleware](http://www.cloudcomputingpatterns.org/message_oriented_middleware/)  assuring [At-least-once Delivery](http://www.cloudcomputingpatterns.org/at_least_once_delivery/). In this case duplicate messages can lead to duplicate processing.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/idempotent_processor/#solution "Permalink") 

The Idempotent Processor ensures that duplicate messages and inconsistent data do not affect application functionality either through inconsistency detection identifying message duplicates and data inconsistencies or through idempotent semantics of application functions enabling them to be erroneously executed multiple times with the same outcome.

![Idempotent Processor](http://www.cloudcomputingpatterns.org/sketches/idempotent_processor_sketch.png) 
 

### Integration Provider

Integration functionality such as messaging and shared data is hosted by a separate provider to enable integrate of otherwise separated hosting environments.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Integration Provider](http://www.cloudcomputingpatterns.org/icons/integration_provider_icon.png)      *How can application components that reside in different environments, possibly belonging to different companies, be integrated through a third-party provider?*
  -------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/integration_provider/#context "Permalink")

When companies collaborate or one company has to integrate applications of different regional offices, different applications or the components of a [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/)  are distributed among different hosting environments. Communication between these environments may be restricted and enabling communication may be hindered by corporate regulations.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/integration_provider/#solution "Permalink")

The Distributed Applications or their components communicate using integration components offered by a third party provider.

![Integration Provider](http://www.cloudcomputingpatterns.org/sketches/integration_provider_sketch.png) 
 

### Loose Coupling

A communication intermediary separates application functionality from concerns of communication partners regarding their location, implementation platform, the time of communication, and the used data format.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------
  ![Loose Coupling](http://www.cloudcomputingpatterns.org/icons/loose_coupling_icon.png)      *How can dependencies between Distributed Applications and between individual components of these applications be reduced?*
  -------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/loose_coupling/#context "Permalink")

Information exchange between applications and their individual components as well as associated management tasks, such as scaling, failure handling, or update management can be simplified significantly if application components can be treated individually and the dependencies among them are kept to a minimum.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/loose_coupling/#solution "Permalink")

Communicating components and multiple integrated applications are decoupled from each other by interacting through a broker. This broker encapsulates the assumptions that communication partners would otherwise have to make about one other and, thus, ensures separation of concerns.

![Loose Coupling](http://www.cloudcomputingpatterns.org/sketches/loose_coupling_sketch.png) 
 

### Message Mover

Messages are moved automatically between different cloud providers to provide unified access to application components using messaging.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------------------------------------------------------------------------------------------------
  ![Message Mover](http://www.cloudcomputingpatterns.org/icons/message_mover_icon.png)      *How can message queues of different providers be integrated without an impact on the application components using them?*
  ------------------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/message_mover/#context "Permalink")

The application components comprising a [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/)  often exchange data using messages. If used message queues reside in different cloud environments that form a [Hybrid Cloud](http://www.cloudcomputingpatterns.org/hybrid_cloud/)  accessibility to queues of one environment may be restricted for application components that are deployed in another environment.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/message_mover/#solution "Permalink")

A Message Mover is used to integrate message queues hosted in different environments by receiving messages from one queue and transferring it to a queue in other environments.

![Message Mover](http://www.cloudcomputingpatterns.org/sketches/message_mover_sketch.png) 
 

### Multi-Component Image

Virtual servers host multiple application components that may not be active at all times to reduce provisioning and decommissioning operations.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------
  ![Multi-Component Image](http://www.cloudcomputingpatterns.org/icons/multi_component_image_icon.png)      *How can a virtual server provide the functionality of multiple application components to be used flexibly in applications?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/multi_component_image/#context "Permalink")

A [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/)  may deploy its application components among virtual servers provided by an [Elastic Infrastructure](http://www.cloudcomputingpatterns.org/elastic_infrastructure/). The individual application components may, however, not fully utilize the servers if only one component is hosted per server. Therefore, mapping each application component to a single server may lead to underutilization.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/multi_component_image/#solution "Permalink")

Multiple application components (possibly including middleware) are hosted on a single virtual server to ensure that running virtual servers may be used for different purposes without making provisioning or decommissioning operations necessary.

![Multi-Component Image](http://www.cloudcomputingpatterns.org/sketches/multi_component_image_sketch.png) 
 

### Processing Component

Possibly long running processing functionality is handled by separate components to enable elastic scaling. Processing functionality is further made configurable to support different customer requirements.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Processing Component](http://www.cloudcomputingpatterns.org/icons/processing_component_icon.png)      *How can processing be scaled out elastically among distributed resources while being configurable regarding the supported functions to meet different customers' requirements?*
  -------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/processing_component/#context "Permalink")

The processing functionality offered by an application shall be handled by different application component instances that operate independently. Instances of these components have to be added and removed easily to the application as part of scaling operations.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/processing_component/#solution "Permalink")

Processing functionality is split into separate function blocks and assigned to independent Processing Components. Each processing component is scaled out independently and is implemented in a stateless fashion as described in the [Stateless Component](http://www.cloudcomputingpatterns.org/stateless_component/)  pattern. Scaling is handled by an [Elastic Queue](http://www.cloudcomputingpatterns.org/elastic_queue/). Data required for processing is provided with requests or by [Storage Offerings](http://www.cloudcomputingpatterns.org/cloud_offerings/#storage_offerings).

![Processing Component](http://www.cloudcomputingpatterns.org/sketches/processing_component_sketch.png) 
 

### Restricted Data Access Component

Data provided to clients from different environments is adjusted based on access restrictions.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------
  ![Restricted Data Access Component](http://www.cloudcomputingpatterns.org/icons/restricted_data_access_component_icon.png)      *How can an application component alter provided data based on access restrictions imposed on different environments?*
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/restricted_data_access_component/#context "Permalink")

A [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) may host application components at different providers to match the individual requirements of components with best fitting providers. One factor may be that application components experience different workload. Other differentiating factors of the used environments may be assured privacy, security, and trust. These differences may, however, impact the data that may be accessible in an environment.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/restricted_data_access_component/#solution "Permalink")

Data storage restrictions and access privileges are defined for each data element. Access to these data elements is provided by separate Restricted Data Access Components that interpret the information associated with data elements. It adjusts data accordingly through deletion or obfuscation during every access.

![Restricted Data Access Component](http://www.cloudcomputingpatterns.org/sketches/restricted_data_access_component_sketch.png) 
 

### Shared Component

A component is accessed by multiple tenants to leverage economies of scale.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------------------------------------------------------------------------------------
  ![Shared Component](http://www.cloudcomputingpatterns.org/icons/shared_component_icon.png)      *How can an application component be shared between multiple tenants enabling some individual configuration?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/shared_component/#context "Permalink")

A [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) is offered to multiple tenants. These tenants share IT resources required by applications provided to them. The provisioning of application component instances shall be optimized by limiting the portion of the application stack and the number of application components deployed exclusively for one tenant.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/shared_component/#solution "Permalink")

A Shared Component provides functionality that is equal for all tenants accessing the component. All tenants can be treated as a uniform user group to which a common user experience and service level is guaranteed.

![Shared Component](http://www.cloudcomputingpatterns.org/sketches/shared_component_sketch.png) 
 

### Stateful Component

Multiple instances of a scaled-out application component synchronize their internal state to provide a unified behavior.
 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------
  ![Stateful Component](http://www.cloudcomputingpatterns.org/icons/stateful_component_icon.png)      *How can applications components that are scaled-out maintain a synchronized internal state?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/stateful_component/#context "Permalink")

To benefit from a distributed cloud runtime environment, components of a [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) are deployed to multiple cloud resources and their instances are scaled-out. Some of these application components may need to maintain an internal state, thus, the challenge arises that individual instances of application components should contain the same internal state, so that they present a unified behavior.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/stateful_component/#solution "Permalink")

The internal state maintained by application component instances is replicated among all instances. Only small portions of shared information are used, for example, a configuration file stored centrally or configurations send by clients with every request.

![Stateful Component](http://www.cloudcomputingpatterns.org/sketches/stateful_component_sketch.png) 
 

### Stateless Component

State is handled external of application components to ease their scaling-out and to make the application more tolerant to component failures.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------------ -------------------------------------------------------------------------------
  ![Stateless Component](http://www.cloudcomputingpatterns.org/icons/stateless_component_icon.png)      *How can elasticity and robustness of an application component be increased?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------ -------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/stateless_component/#context "Permalink") 

The components of a [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) are deployed among multiple cloud resources to benefit from this distributed runtime environment through scaling out.The most significant factor complicating addition and removal of component instances in this scope is the internal state maintained by them. In case of failure, this information may even be lost.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/stateless_component/#solution "Permalink")

Application components are implemented in a fashion that they do not have an internal state. Instead, their state and configuration is stored externally in [Storage Offerings](http://www.cloudcomputingpatterns.org/cloud_offerings/#storage_offerings) or provided to the component with each request.

![Stateless Component](http://www.cloudcomputingpatterns.org/sketches/stateless_component_sketch.png) 
 

### Tenant-isolated Component

A component shared between tenants avoids influences between tenants regarding assured performance, available storage capacity, and accessibility of functionality and data.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Tenant-isolated Component](http://www.cloudcomputingpatterns.org/icons/tenant_isolated_component_icon.png)      *How can an application component be shared between multiple tenants enabling individual configuration and tenant-isolation regarding performance, data volume, and access privileges?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/tenant_isolated_component/#context "Permalink")

A [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) is offered to multiple tenants. These tenants share IT resources required by applications provided to them. However, the sharing of application components is hindered by three factors. First, tenants may have unique requirements and, thus, expect application components to be configurable to their individual needs. Second, tenants may not trust each other. Third, tenants expect an application to behave as if a single tenant was the only one accessing it.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/tenant_isolated_component/#solution "Permalink") 

Components on all layers of the application stack are specifically developed to be used by different tenants. Especially, they ensure isolation between tenants by controlling tenant access, processing performance used, and separation of stored data.

![Tenant-isolated Component](http://www.cloudcomputingpatterns.org/sketches/tenant_isolated_component_sketch.png) 
 

### Transaction-based Processor

Components receive messages or read data and process the obtained information under a transactional context to ensure that all received messages are processes and all altered data is consistent after processing, respectively.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Transaction-based Processor](http://www.cloudcomputingpatterns.org/icons/transaction_based_processor_icon.png)      *How can an application component ensure that all messages it receives are processed successfully and altered data is persisted successfully after processing?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/transaction_based_processor/#context "Permalink")

A [Message-oriented
Middleware](http://www.cloudcomputingpatterns.org/message_oriented_middleware/) can
use [Transaction-based
Delivery](http://www.cloudcomputingpatterns.org/transaction_based_delivery/) of
messages to ensure that messages are received successfully by a client.
However, using this approach no assurances can be made regarding the
processing of that received message.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/transaction_based_processor/#solution "Permalink") 

Transaction-based Delivery subsumes reading the message from a queue and deleting it from a queue in one transaction. The Transaction-based Processor extends the transactional context to the processing of the message in the receiver. Analogous, if interacting with a storage offering, the Transaction-based Processor reads, processes and writes data in one transactional context.

![Transaction-based Processor](http://www.cloudcomputingpatterns.org/sketches/transaction_based_processor_sketch.png) 
 

### Timeout-based Message Processor

Clients acknowledge message receptions and processing to ensure that all messages are handled by an application. If a message is not acknowledged after a certain timeout, it is processed by a different client.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ ----------------------------------------------------------------------------------------------------------------------------------------
  ![Timeout-based Message Processor](http://www.cloudcomputingpatterns.org/icons/timeout_based_message_processor_icon.png)      *How can an application process messages while guaranteeing that all messages handled by the application are processed at-least-once?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ ----------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/timeout_based_message_processor/#context "Permalink") 

A [Message-oriented Middleware](http://www.cloudcomputingpatterns.org/message_oriented_middleware/) uses [Timeout-based Delivery](http://www.cloudcomputingpatterns.org/timeout_based_delivery/) to ensure that messages are received successfully by at least one client. Additionally, it shall be assured by the application that a message has also been properly processed after its reception.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/timeout_based_message_processor/#solution "Permalink") 

Instead of sending an acknowledgement right after receiving a message, a timeout-based message processor sends this acknowledgement after it has successfully processed the message.

![Timeout-based Message Processor](http://www.cloudcomputingpatterns.org/sketches/timeout_based_message_processor_sketch.png) 
 

### User Interface Component

Interactive synchronous access to applications is provided to humans, while application-internal interaction is realized asynchronously when possible to ensure Loose Coupling. Furthermore, the user interface should be customizable to be used by different customers.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------
  ![User Interface Component](http://www.cloudcomputingpatterns.org/icons/user_interface_component_icon.png)      *How can User Interface Components be accessed interactively by humans while being configurable and decoupled from the remaining application?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [ContextPermalink](http://www.cloudcomputingpatterns.org/user_interface_component/#context "Permalink")

User Interface Component instances part of a [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) have to be added and removed easily from the application without affecting the user experience. The dependencies on other application components should, therefore, be reduced as much as possible.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/user_interface_component/#solution "Permalink")

The User Interface Component serves as a bridge between the synchronous access of the human user and the asynchronous communication used with other application components. State information held externally, as described by the [Stateless Component](http://www.cloudcomputingpatterns.org/stateless_component/) pattern. It is, therefore, attached to requests, may be held in a part of the user interface that is deployed on the user's access device, or may be obtained from external storage. Instances of User Interface Components are scaled based on the number of synchronous requests to is as described by the [Elastic Load Balancer](http://www.cloudcomputingpatterns.org/elastic_load_balancer/) pattern.

![User Interface Component](http://www.cloudcomputingpatterns.org/sketches/user_interface_component_sketch.png) 
 

Application Management
----------------------

### Elastic Load Balancer

The number of synchronous accesses to an elastically scaled-out application is used to determine the number of required application component instances.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------
  ![Elastic Load Balancer](http://www.cloudcomputingpatterns.org/icons/elastic_load_balancer_icon.png)      *How can the number of required application component instances be determined based on monitored synchronous accesses?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/elastic_load_balancer/#context "Permalink")

Application components of a [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) shall be scaled out automatically. Requests sent to an application shall be used as an indicator for the currently experienced workload from which the required number of components instances shall be deducted.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/elastic_load_balancer/#solution "Permalink") 

Based on the number of synchronous requests handled by a load balancer and possibly other utilization information, the required number of required component instances is determined.

![Elastic Load Balancer](http://www.cloudcomputingpatterns.org/sketches/elastic_load_balancer_sketch.png) 
 

### Elastic Queue

The number of asynchronous accesses via messaging to an elastically scaled-out application is used to adjust the number of required application component instances.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------------------------------------------
  ![Elastic Queue](http://www.cloudcomputingpatterns.org/icons/elastic_queue_icon.png)      *How can the number of required application component instances be adjusted based on monitored asynchronous accesses?*
  ------------------------------------------------------------------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/elastic_queue/#context "Permalink")

A [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) is comprised of multiple application components that are accessed asynchronously and deployed to an [Elastic Infrastructure](http://www.cloudcomputingpatterns.org/elastic_infrastructure/) or an [Elastic Platform](http://www.cloudcomputingpatterns.org/elastic_platform/). The required provisioning and decommissioning operations to scale this application should be performed in an automated fashion.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/elastic_queue/#solution "Permalink")

Queues that are used to distribute asynchronous requests among multiple application components instances are monitored. Based on the number of enqueued messages the Elastic Queue adjusts the number of application component instances handling these requests.

![Elastic Queue](http://www.cloudcomputingpatterns.org/sketches/elastic_queue_sketch.png) 
 

### Elasticity Manager

The utilization of IT resources on which an elastically scaled-out application is hosted, for example, virtual servers is used to determine the number of required application component instances.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------
  ![Elasticity Manager](http://www.cloudcomputingpatterns.org/icons/elasticity_manager_icon.png)      *How can the number of required application component instances be determined based on the utilization of hosting IT resources?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------
 

### [Context Permalink](http://www.cloudcomputingpatterns.org/elasticity_manager/#context "Permalink")

Application components of a [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) hosted on an [Elastic Infrastructure](http://www.cloudcomputingpatterns.org/elastic_infrastructure/) or [Elastic Platform](http://www.cloudcomputingpatterns.org/elastic_platform/) shall be scaled-out. The instances of applications components, thus, shall be provisioned and decommissioned automatically based on the current workload experienced by the application.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/elasticity_manager/#solution "Permalink")

The utilization of cloud resources on which application component instances are deployed is monitored. This could be, for example, the CPU load of a virtual server. This information is used to determine the number of required instances.

![Elasticity Manager](http://www.cloudcomputingpatterns.org/sketches/elasticity_manager_sketch.png) 
 

### Elasticity Management Process

Application component instances are added automatically to an application to cope with increasing workload. If the workload decreases application component instances are removed respectively.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Elasticity Management Process](http://www.cloudcomputingpatterns.org/icons/elasticity_management_process_icon.png)      *How can the number of resources to which application components are scaled-out be adjusted efficiently to the currently experienced workload and anticipated future workload?*
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 

### [Context Permalink](http://www.cloudcomputingpatterns.org/elasticity_management_process/#context "Permalink")

A [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) uses [Elasticity Managers](http://www.cloudcomputingpatterns.org/elasticity_manager/), [Elastic Queues](http://www.cloudcomputingpatterns.org/elastic_queue/), or [Elastic Load Balancers](http://www.cloudcomputingpatterns.org/elastic_load_balancer/) to ensure an elastic scaling of application components. To handle this task adequately, the current resource demand has to be obtained automatically from the application and has to be reflected in provisioning and decommissioning of cloud resources.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/elasticity_management_process/#solution "Permalink")

An Elasticity Management Process analyzes the utilization of application component instances in intervals, when a system manager requests it, or if certain conditions are observed by the monitoring component. Based on this information, the current workload of the application is computed and reflected by adjusting used resources.

![Elasticity Management Process](http://www.cloudcomputingpatterns.org/sketches/elasticity_management_process_sketch.png) 
 

### Feature Flag Management Process

If the cloud cannot provide required resources in time, the features provided by application components are degraded gracefully to replace or disable unimportant ones in order to keep vital features operational.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Feature Flag Management Process](http://www.cloudcomputingpatterns.org/icons/feature_flag_management_process_icon.png)      *How can the performance of an application degrade gracefully, if the experienced workload increases but additional cloud resources are unavailable or take too long to provision?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/feature_flag_management_process/#context "Permalink") 

While the elasticity of clouds generally allows a tight alignment of resource numbers to the experienced workload, the time it takes to provision new resources remains as a limiting factor. If the workload increases too drastically, it may take too long to provision new resources. Furthermore, cloud providers often do not guarantee concrete provisioning times.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/feature_flag_management_process/#solution "Permalink")

Less important application functionality provided by application component instances is disabled or replaced with a less demanding implementation, if the cloud provider cannot fulfill current workload demands. When resources can eventually be provisioned again, the application components return to normal operation.

![Feature Flag Management Process](http://www.cloudcomputingpatterns.org/sketches/feature_flag_management_process_sketch.png) 
 

### Managed Configuration

Scaled-out application components should use a centrally stored configuration to provide a unified behavior that can be adjusted simultaneously.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------
  ![Managed Configuration](http://www.cloudcomputingpatterns.org/icons/managed_configuration_icon.png)      *How can the configuration of scaled out application component instances be controlled in a coordinated fashion?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/managed_configuration/#context "Permalink")

Application components of a [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) often have configuration parameters. Storing configuration information together with the application component implementation can be unpractical as it results in more overhead in case of configuration changes. Each running instance of the application component must be updated separately. Component images stored in [Elastic Infrastructures](http://www.cloudcomputingpatterns.org/elastic_infrastructure/) or [Elastic Platforms](http://www.cloudcomputingpatterns.org/elastic_platform/) also have to be updated upon configuration change.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/managed_configuration/#solution "Permalink")

Configurations are stored in a central [Storage Offering](http://www.cloudcomputingpatterns.org/cloud_offerings/#storage_offerings), commonly, a [Relational Database](http://www.cloudcomputingpatterns.org/relational_database/), [Key-Value Storage](http://www.cloudcomputingpatterns.org/key_value_storage/), or [Blob Storage](http://www.cloudcomputingpatterns.org/blob_storage/) from where it is accessed by all running component instances either by accessing the storage periodically or by sending messages to the components.

![Managed Configuration](http://www.cloudcomputingpatterns.org/sketches/managed_configuration_sketch.png) 
 

### Provider Adapter

Provider interfaces are encapsulated and mapped to unified interfaces used in applications to separate concerns of interactions with the provider from application functionality.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------ -----------------------------------------------------------------------------------------------------
  ![Provider Adapter](http://www.cloudcomputingpatterns.org/icons/provider_adapter_icon.png)      *How can the dependencies of an application component on a provider-specific interface be managed?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------ -----------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/provider_adapter/#context "Permalink")

Cloud providers offer many interfaces that can be used in application components of a [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/). If a component directly interacts with these interfaces, its implementation becomes strongly interleaved with the specific functions offered and the protocols used.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/provider_adapter/#solution "Permalink")

The Provider Adapter encapsulates all provider-specific implementations required for authentication, data formatting etc. in an abstract interface. The Provider Adapter , thus, ensures separation of concerns between application components accessing provider functionality and application components providing application functionality. It may also offer synchronous provider-interfaces to be accessed asynchronously via messages and vice versa.

![Provider Adapter](http://www.cloudcomputingpatterns.org/sketches/provider_adapter_sketch_1.png) 
 

![Provider Adapter](http://www.cloudcomputingpatterns.org/sketches/provider_adapter_sketch_2.png) 
 

### Resiliency Management Process

Application components are checked for failures and replaced automatically without human intervention.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------
  ![Resiliency Management Process](http://www.cloudcomputingpatterns.org/icons/resiliency_management_process_icon.png)      *How can the overall availability of an application be ensured automatically even if individual application component instances fail?*
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/resiliency_management_process/#context "Permalink")

A
[Watchdog](http://www.cloudcomputingpatterns.org/watchdog/) allows to monitor application components and react to failures. To handle this task, the component functionality must be verified and failing components must be replaced with newly provisioned components in a coordinated fashion.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/resiliency_management_process/#solution "Permalink")

This process is triggered by the monitoring functionality or by the[Watchdog](http://www.cloudcomputingpatterns.org/watchdog/) if it detects a component failure. Additionally, the Resiliency Management Process periodically verifies application component health. If a failure is detected, the faulty application component instance is decommissioned and replaced by a newly provisioned instance.

![Resiliency Management Process](http://www.cloudcomputingpatterns.org/sketches/resiliency_management_process_sketch.png) 
 

### Standby Pooling Process

Application component instances should be kept on standby to increase provisioning speed and utilize billing time-slots efficiently.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------
  ![Standby Pooling Process](http://www.cloudcomputingpatterns.org/icons/standby_pooling_process_icon.png)      *How can defined provisioning times for application component instances be ensured while utilizing pay-per-use resources in an optimal fashion?*
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/standby_pooling_process/#context "Permalink")  {#CloudArchitecture-ContextPermalink.59}

Even though application component instances may be provisioned and decommissioned dynamically, it usually requires some time to actually provision and decommission them. If a cloud application, however, experiences drastic and quick workload changes, these provisioning times may limit its capability to obtain the required resources quickly enough. Decommissioning of component instances immediately when no longer needed may also be ineffective, if cloud resources are charged for fixed time-slots.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/standby_pooling_process/#solution "Permalink")  {#CloudArchitecture-SolutionPermalink.59}

Instead of decommissioning application component instances instantly when they are unused, they are assigned to a standby list They are decommissioned only when the time-slot they have been paid for has been utilized and they are still not needed. The standby list may always contain a certain number of component instances to ensure timely provisioning.

![Standby Pooling Process](http://www.cloudcomputingpatterns.org/sketches/standby_pooling_process_sketch_1.png) 
 

![Standby Pooling Process](http://www.cloudcomputingpatterns.org/sketches/standby_pooling_process_sketch_2.png) 
 

### Update Transition Process

When a new application component version, middleware versions etc. become available, running application components are updated seamlessly.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ --------------------------------------------------------------------------------------
  ![Update Transition Process](http://www.cloudcomputingpatterns.org/icons/update_transition_process_icon.png)      *How can application components of a Distributed Application be updated seamlessly?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ --------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/update_transition_process/#context "Permalink")

During the runtime of a [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/), new versions of used middleware, operating systems, or application components may become available. A seamless switch from the old to the new version of application components shall be enabled.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/update_transition_process/#solution "Permalink")  

The new component version is created. Additional application component instances of the new version are provisioned. These components are executed simultaneously with the application components of the old version. If necessary, load balancing is then switched to the component instances of the new version. If the application components access a queue, this step is unnecessary. Finally, the old application component instances are decommissioned.

![Update Transition Process](http://www.cloudcomputingpatterns.org/sketches/update_transition_process_sketch.png) 
 

### Watchdog

Applications cope with failures automatically by monitoring and replacing application component instances if the provider-assured availability is insufficient.

 
  -------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------
  ![Watchdog](http://www.cloudcomputingpatterns.org/icons/watchdog_icon.png)      *How can applications automatically detect failing application components and handle their replacement?*
  -------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/watchdog/#context "Permalink") 

If a [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) is comprised of many application components it is dependent on the availability of all component instances. To enable high availability under such conditions, applications have to rely on redundant application component instances and the failure of these instances has to be detected and coped with automatically.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/watchdog/#solution "Permalink") 

Individual application components rely on external state information by implementing the [Stateless Component](http://www.cloudcomputingpatterns.org/stateless_component/) pattern. Components are scaled out and multiple instances of them are deployed to redundant resources. The component instances are monitored by a separate Watchdog component and replaced in case of failures.

![Watchdog](http://www.cloudcomputingpatterns.org/sketches/watchdog_sketch.png) 
 

Cloud Applications
------------------

### Content Distribution Network

Applications component instances and data handled by them are globally distributed to meet the access performance required by a global user group.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------------------------------------------------------------------
  ![Content Distribution Network](http://www.cloudcomputingpatterns.org/icons/content_distribution_network_icon.png)      *How can timely access to an application be ensured for a globally distributed user group?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/content_distribution_network/#context "Permalink")

If the application provides multimedia content to users, for example, streamed videos and music the amount of data to be served increases drastically. If such multimedia content is located too far from the user accessing it, the communication delay of the distribution network may hinder the timely access to data. Therefore, storing content in only one centralized location, i.e., one cloud or data center is unfeasible.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/content_distribution_network/#solution "Permalink")

Content replicas are established in different physical locations of one or multiple clouds. During this distribution of replicas, the topology of distribution networks is considered to ensure locality for all users. Replicas are updated from a central location.

![Content Distribution Network](http://www.cloudcomputingpatterns.org/sketches/content_distribution_network_sketch.png) 
 

### Hybrid Application Functions

Some application functionality provided by user interfaces, processing, and data handling is experiencing varying workload and is hosted in an elastic cloud while other application functionality of the same type is hosted in a static environment.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ -------------------------------------------------------------------------------------------------------------------------------------------------
  ![Hybrid Application Functions](http://www.cloudcomputingpatterns.org/icons/hybrid_application_functions_icon.png)      *How can arbitrary functionality of an application be distributed among static data centers and elastic clouds best matching its requirements?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ -------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/hybrid_application_functions/#context "Permalink")

Application components comprising a [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) experience varying workloads on all layers of the application stack: [User Interface Components](http://www.cloudcomputingpatterns.org/user_interface_component/), [Processing Components](http://www.cloudcomputingpatterns.org/processing_component/), and [Data Access Components](http://www.cloudcomputingpatterns.org/data_access_component/). All of these components provide functionality to the user group of the application, but this user group accesses functionality differently. In addition to the workload requirements other issues, such as legal and corporate regulations or requirements on security, privacy, and trust may limit the environments to which an application component may be provisioned.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/hybrid_application_functions/#solution "Permalink")

Application components are grouped regarding similar requirements and are deployed into best fitting environments. Interdependencies between the components are reduced by exchanging data using asynchronous messaging to ensure [Loose Coupling](http://www.cloudcomputingpatterns.org/loose_coupling/). Depending on the accessed function, a load balancer redirects user accesses to the different environments seamlessly.

![Hybrid Application Functions](http://www.cloudcomputingpatterns.org/sketches/hybrid_application_functions_sketch.png) 
 

### Hybrid Backend

Backend functionality comprised of data intensive processing and data storage is experiencing varying workloads and is hosted in an elastic cloud while the rest of an application is hosted in a static data center.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Hybrid Backend](http://www.cloudcomputingpatterns.org/icons/hybrid_backend_icon.png)      *How can Processing Components that experience varying workload and need access to large amounts of data be hosted in an elastic environment while the remainder of the application is hosted in a static environment?*
  -------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/hybrid_backend/#context "Permalink") 

A [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) provides processing functionality that experiences varying workload behavior. Mainly, [Static Workload](http://www.cloudcomputingpatterns.org/static_workload/) has to be handled, but some Processing Components experience [Periodic Workload](http://www.cloudcomputingpatterns.org/periodic_workload/), [Unpredictable Workload](http://www.cloudcomputingpatterns.org/unpredictable_workload/), or [Continuously Changing Workload](http://www.cloudcomputingpatterns.org/continuously_changing_workload/). Application components providing the respective processing functionality  experiencing varying workload should, therefore, be hosted in an elastic environment. However, these components have to access large amounts of data during their execution making them highly dependent on the availability and the timely access to such data.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/hybrid_backend/#solution "Permalink") 

The Processing Components experiencing varying workloads are hosted in an elastic cloud together with the data accessed during their operation. Processing Components in the elastic cloud are triggered from the static environment through asynchronous messages exchanged via message queues provided by a [Message-oriented Middleware](http://www.cloudcomputingpatterns.org/message_oriented_middleware/). A [Data Access Component](http://www.cloudcomputingpatterns.org/data_access_component/) in the static environment ensures that data required by elastic Processing Components is stored in Storage Offerings The location where this data is stored may then be passed to the elastic Processing Components during their enactment via messages. Data that is not required by the backend functionality may still be stored in [Stateful Components](http://www.cloudcomputingpatterns.org/stateful_component/) hosted in the static data center.

![Hybrid Backend](http://www.cloudcomputingpatterns.org/sketches/hybrid_backend_sketch.png) 
 

### Hybrid Backup

Data is periodically extracted from an application to be archived in an elastic cloud for disaster recovery purposes.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------------------------------------------------
  ![Hybrid Backup](http://www.cloudcomputingpatterns.org/icons/hybrid_backup_icon.png)      *How can data be archived in a remote environment while the remainder of the application is hosted in a static environment?*
  ------------------------------------------------------------------------------------------------------------------------------------------------ ------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/hybrid_backup/#context "Permalink")

Many applications are used by small and medium businesses which do not have the required IT skills to host and maintain their own highly available infrastructure. Especially, requirements regarding business  resiliency -- the ability to recover from an error -- and business continuity -- the ability to operate during an error -- are challenging. Furthermore, there are laws and regulations making businesses liable to archive data and keep it accessible for audits, often over very long periods of time.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/hybrid_backup/#solution "Permalink")

A [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) is hosted in a local static environment of the company. Data handled by [Stateful Components](http://www.cloudcomputingpatterns.org/stateful_component/) is periodically extracted and replicated to a cloud storage offering.

![Hybrid Backup](http://www.cloudcomputingpatterns.org/sketches/hybrid_backup_sketch.png) 
 

### Hybrid Data

Data of varying size is hosted in an elastic cloud while the remainder of an application resides in a static environment.

 
  -------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Hybrid Data](http://www.cloudcomputingpatterns.org/icons/hybrid_data_icon.png)      *How can a data handling functionality that experiences varying workload be hosted in an elastic cloud while the rest of the application is located in a static data center?*
  -------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/hybrid_data/#context "Permalink")

A [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) handles data whose size varies drastically over time. Large amounts of data may, thus, be generated periodically and are then deleted again, may increase and decrease randomly, or may display a general increase or decrease over time. Especially, during these changes, the user number and their accesses to the application can be static resulting in [Static Workload](http://www.cloudcomputingpatterns.org/static_worklaod/) on the remainder of the application components.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/hybrid_data/#solution "Permalink")

Data whose varying size makes it unsuitable for hosting in a static environment is handled by Storage Offerings in an elastic cloud. At this location data is either accessed by [Data Access Components](http://www.cloudcomputingpatterns.org/data_access_component/) that are hosted in the static environment or by Data Access Components hosted in the elastic environment.

![Hybrid Data](http://www.cloudcomputingpatterns.org/sketches/hybrid_data_sketch.png) 
 

### Hybrid Development Environment

A production runtime environment is replicated and mocked in an elastic environment where new applications can be developed and tested.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------
  ![Hybrid Development Environment](http://www.cloudcomputingpatterns.org/icons/hybrid_development_environment_icon.png)      *How can an application use different computing environments during its development, test, and production stages?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/hybrid_development_environment/#context "Permalink")

Applications have different requirements on the runtime environment during their development, test, and production phase. During development, hardware requirements are often uncertain, so hardware resources should be flexible to extend resources if necessary. During the test phase, diverse test systems may be needed to verify the proper functioning of the application on different operating systems or when being accessed using different client software, i.e., different browsers. Large numbers of resources may also be required to perform load tests. During the productive use other factors, such as security and availability may be of greater importance than resource flexibility.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/hybrid_development_environment/#solution "Permalink")

The production environment of the application is simulated in the development and test environment through the use of equivalent addressing, similar mocking data, and equivalent functionality provided by the environment. Migration of developed applications is ensured through transformation of application components or compatibility of runtimes. Some testing resources are provided exclusively in the development environment to verify the application behavior under different circumstances.

![Hybrid Development Environment](http://www.cloudcomputingpatterns.org/sketches/hybrid_development_environment_sketch.png) 
 

### Hybrid Multimedia Web Application

Website content is largely provided from a static environment. 
Multimedia files that cannot be cached efficiently are provided from a large distributed elastic environment for high-performance access.

 
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------
  ![Hybrid\_Multimedia\_Web\_Application](http://www.cloudcomputingpatterns.org/icons/hybrid_multimedia_web_application_icon.png)      *How can non-cacheable content be integrated efficiently in a website that is accessed by a large globally distributed user group?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/hybrid_multimedia_web_application/#context "Permalink")

A [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) provides a website accessed by a large globally distributed user group. While most of the website is comprised of static content, there is also a significant amount of multimedia content, such as videos or music that has to be streamed to users.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/hybrid_multimedia_web_application/#solution "Permalink")

Static website content is hosted in a static environment from where it is accessed by users. The streaming content is provided by an elastic cloud environment where it is accessed from the application's [User Interface Component](http://www.cloudcomputingpatterns.org/user_interface_component/). The static content is provided to users' client software and in this static content, the multimedia content is referenced. Retrieval of this streaming content is often handled directly by the users' browser software.

![Hybrid\_Multimedia\_Web\_Application](http://www.cloudcomputingpatterns.org/sketches/hybrid_multimedia_web_application_sketch.png) 
 

### Hybrid Processing

Processing functionality that experiences varying workload is hosted in an elastic cloud while the remainder of an application resides in a static environment.

 
  -------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Hybrid Processing](http://www.cloudcomputingpatterns.org/icons/hybrid_processing_icon.png)      *How can Processing Components that experiences varying workload be hosted in an elastic cloud while the remainder of an application is hosted in a static data center?*
  -------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/hybrid_processing/#context "Permalink")

A [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) provides processing functionality that experience different workload behavior. The user group accessing the application is, thus, predictable in size, but accesses the functions provided by the application differently. While most of the functions are used equally over time and, therefore, experience [Static Workload](http://www.cloudcomputingpatterns.org/static_worklaod/), some [Processing Components](http://www.cloudcomputingpatterns.org/processing_component/) experience [Periodic Workload](http://www.cloudcomputingpatterns.org/periodic_worklaod/), [Unpredictable Workload](http://www.cloudcomputingpatterns.org/unpredictable_workload/), or [Continuously Changing Workload](http://www.cloudcomputingpatterns.org/continuously_changing_workload/).

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/hybrid_processing/#solution "Permalink")

The [Processing Components](http://www.cloudcomputingpatterns.org/processing_component/) experiencing varying workloads are provisioned in an elastic cloud. [Loose Coupling](http://www.cloudcomputingpatterns.org/loose_coupling/) is ensured by exchanging information between the hosting environments asynchronously via messages.

![Hybrid Processing](http://www.cloudcomputingpatterns.org/sketches/hybrid_processing_sketch.png) 
 

### Hybrid User Interface

Varying workload from a user group interacting asynchronously with an application is handled in an elastic environment while the remainder of an application resides in a static environment.

 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ![Hybrid User Interface](http://www.cloudcomputingpatterns.org/icons/hybrid_user_interface_icon.png)      *How can a user interface for asynchronous interaction be hosted in a cloud while being integrated with an application otherwise hosted in a static data center?*
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/hybrid_user_interface/#context "Permalink")

An application serves user groups with different workload behavior. One user group generates [Static Workload](http://www.cloudcomputingpatterns.org/static_workload/), while another user group generates [Periodic Workload](http://www.cloudcomputingpatterns.org/periodic_workload/), [Once-in-a-lifetime Workload](http://www.cloudcomputingpatterns.org/once_in_a_lifetime_workload/), [Unpredictable Workload](http://www.cloudcomputingpatterns.org/unpredictable_workload/), or [Continuously Changing Workload](http://www.cloudcomputingpatterns.org/continuously_changing_workload/). Since the predictability of the user group size and workload behavior differs, it shall be ensured that unexpected peak workloads do not affect the performance of the application while each user group is handled by the most suitable cloud environment.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/hybrid_user_interface/#solution "Permalink")

The [User Interface Component](http://www.cloudcomputingpatterns.org/user_interface_component/) serving users generating varying workload is hosted in an elastic cloud environment. Other application components that are hosted in a static environment. The user interface deployed in the elastic cloud is integrated with the remainder of the application in a decoupled fashion using messaging to ensure [Loose Coupling](http://www.cloudcomputingpatterns.org/loose_coupling/).

![Hybrid User Interface](http://www.cloudcomputingpatterns.org/sketches/hybrid_user_interface_sketch.png) 
 

### Three-Tier Cloud Application

The presentation, business logic, and data handling is realized as separate tiers to scale stateless presentation and compute-intensive processing independently of the data tier, which is harder to scale and often handled by the cloud provider.


  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ ----------------------------------------------------------------------------------------------------------------------------------
  ![Three-Tier Cloud Application](http://www.cloudcomputingpatterns.org/icons/three_tier_cloud_application_icon.png)      *How can presentation logic, business logic, and data handling be decomposed into separate tiers that are scaled independently?*
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ ----------------------------------------------------------------------------------------------------------------------------------
 

#### [Context Permalink](http://www.cloudcomputingpatterns.org/three_tier_cloud_application/#context "Permalink")

A [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) is decomposed into application components to scale individual application functions independently. There can be many differentiating factors of application tiers. For example, if [Processing Components](http://www.cloudcomputingpatterns.org/processing_components/) are more computation intensive or are used less frequently than [User Interface Components](http://www.cloudcomputingpatterns.org/user_interface_components/),
aligning the elastic scaling of these two components by summarizing their implementation in one tier can be inefficient. This issue arises every time components experiences different [Application Workloads](http://www.cloudcomputingpatterns.org/cloud_computing_fundamentals/#application_workloads). The number of provisioned component instances cannot be aligned well to the different workloads if they are summarized to coarse grained tiers.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/three_tier_cloud_application/#solution "Permalink")

The application is decomposed into three tiers, where each tier is elastically scaled independently. The presentation tier is comprised of a load balancer and an application component that implements the [Stateless Component](http://www.cloudcomputingpatterns.org/stateless_component/) pattern and [User Interface Component](http://www.cloudcomputingpatterns.org/user_interface_component/) pattern. The business logic tier is comprised of an application component implementing the [Stateless Component](http://www.cloudcomputingpatterns.org/stateless_component/) pattern in addition to the [Processing Component](http://www.cloudcomputingpatterns.org/processing_component/) pattern.

![Three-Tier Cloud Application](http://www.cloudcomputingpatterns.org/sketches/three_tier_cloud_application_sketch.png)

### Two-Tier Cloud Application

Presentation and business logic is bundled to one stateless tier that is easy to scale. This tier is separated from the data tier that is harder to scale and often handled by a provider-supplied storage offering.

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------
  ![Two-Tier Cloud Application](http://www.cloudcomputingpatterns.org/icons/two_tier_cloud_application_icon.png)  *How can application functionality be separated from data handling to scale them independently?*
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------


#### [Context Permalink](http://www.cloudcomputingpatterns.org/two_tier_cloud_application/#context "Permalink")

A [Distributed Application](http://www.cloudcomputingpatterns.org/distributed_application/) is decomposed into application components to scale individual application functions independently. In this scope, data handling functionality is significantly harder to scale than [Stateless Components](http://www.cloudcomputingpatterns.org/stateless_components/), because [Stateful Components](http://www.cloudcomputingpatterns.org/stateful_components/) have to coordinate state information between instances. Therefore, the application shall be decomposed in a fashion that separates the easy-to-scale functionality from the hard-to-scale functionality.

#### [Solution Permalink](http://www.cloudcomputingpatterns.org/two_tier_cloud_application/#solution "Permalink")

Application functionality is decomposed into data handling functionality, provided by one or several [Storage Offerings](http://www.cloudcomputingpatterns.org/cloud_offerings/#storage_offerings), and application components handling presentation and business logic. This separation enables the two tiers to elastically scale independently with their workloads.

![Two-Tier Cloud Application](http://www.cloudcomputingpatterns.org/sketches/two_tier_cloud_application_sketch.png)

References

-   [Google Cloud Solution Architecture
    Reference](https://gcp.solutions/) 
-   [Microsoft - Azure patterns](https://docs.microsoft.com/en-us/azure/architecture/patterns/) 
-   [Cloud Computing Patterns](http://www.cloudcomputingpatterns.org/) 
-   [Medium faun - scaling applications in the cloud](https://medium.com/faun/scaling-applications-in-the-cloud-52bb6dfbac4e) 
