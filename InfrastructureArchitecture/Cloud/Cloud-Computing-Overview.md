###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Infrastructure Architecture](https://github.com/RyKaj/Documentation/tree/master/InfrastructureArchitecture/README.md) |
------------



Infrastructure Architecture - Cloud Computing Overview
====================================================


 
Overview
--------

An Overview Cloud computing is a computing paradigm, where a large pool
of systems are connected in private or public networks, to provide
dynamically scalable infrastructure for application, data and file
storage. With the advent of this technology, the cost of computation,
application hosting, content storage and delivery is reduced
significantly. Cloud computing is a practical approach to experience
direct cost benefits and it has the potential to transform a data center
from a capital-intensive set up to a variable priced environment. The
idea of cloud computing is based on a very fundamental principal of
reusability of IT capabilities. The difference that cloud computing
brings compared to traditional concepts of "grid computing",
"distributed computing", "utility computing" or "autonomic computing" is
to broaden horizons across organizational boundaries. Forester defines
cloud computing as: "A pool of abstracted, highly scalable, and managed
compute infrastructure capable of hosting end customer applications and
billed by consumption."

Cloud Computing Models Cloud Providers offer services that can be
grouped into three categories.

<kbd>![](https://miro.medium.com/max/963/1*F_EB3zGRdsahx01e8nLW4w.png) </kbd>

**Software as a Service (SaaS)**: In this model, a complete application
is offered to the customer, as a service on demand. A single instance of
the service runs on the cloud & multiple end users are serviced. On the
customers‟ side, there is no need for upfront investment in servers or
software licenses, while for the provider, the costs are lowered, since
only a single application needs to be hosted & maintained. Today SaaS is
offered by companies such as Google, Salesforce, Microsoft, Zoho, etc.

**Platform as a Service (Paas)**: Here, a layer of software, or
development environment is encapsulated & offered as a service, upon
which other higher levels of service can be built. The customer has the
freedom to build his own applications, which run on the provider‟s
infrastructure. To meet manageability and scalability requirements of
the applications, PaaS providers offer a predefined combination of OS
and application servers, such as LAMP platform (Linux, Apache, MySql and
PHP), restricted J2EE, Ruby etc. Google's App Engine,
[Force.com](http://Force.com), etc are some of the
popular PaaS examples.

**Infrastructure as a Service (Iaas)**: IaaS provides basic storage and
computing capabilities as standardized services over the network.
Servers, storage systems, networking equipment, data centre space etc.
are pooled and made available to handle workloads. The customer would
typically deploy his own software on the infrastructure. Some common
examples are Amazon, GoGrid, 3 Tera, etc.

Understanding Public and Private Clouds Enterprises can choose to deploy
applications on Public, Private or Hybrid clouds. Cloud Integrators can
play a vital part in determining the right cloud path for each
organization. Public Cloud are owned and operated by third parties; they
deliver superior economies of scale to customers, as the infrastructure
costs are spread among a mix of users, giving each individual client an
attractive low-cost "Pay-as-you-go" model. All customers share the same
infrastructure pool with limited configuration, security protections,
and availability variances. These are managed and supported by the cloud
provider. One of the advantages of a Public cloud is that they may be
larger than an enterprises cloud, thus providing the ability to scale
seamlessly, on demand. Private Cloud Private clouds are built
exclusively for a single enterprise. They aim to address concerns on
data security and offer greater control, which is typically lacking in a
public cloud.

There are two variations to a private cloud: On-premise & Private Cloud

1.  **On-premise** private clouds, also known as internal clouds are
	hosted within one's own data center. This model provides a more
	standardized process and protection, but is limited in aspects of
	size and scalability. IT departments would also need to incur the
	capital and operational costs for the physical resources. This is
	best suited for applications which require complete control and
	configurability of the infrastructure and security.
2.  Externally hosted **Private Cloud**: This type of private cloud is
	hosted externally with a cloud provider, where the provider
	facilitates an exclusive cloud environment with full guarantee of
	privacy. This is best suited for enterprises that don't prefer a
	public cloud due to sharing of physical resources.
3.  **Hybrid Cloud**: Hybrid Clouds combine both public and private
	cloud models. With a Hybrid Cloud, service providers can utilize 3rd
	party Cloud Providers in a full or partial manner thus increasing
	the flexibility of computing. The Hybrid cloud environment is
	capable of providing on-demand, externally provisioned scale. The
	ability to augment a private cloud with the resources of a public
	cloud can be used to manage any unexpected surges in workload.

Cloud Computing Benefits Enterprises would need to align their
applications, so as to exploit the architecture models that Cloud
Computing offers. Some of the typical benefits are listed below:

1.  **Reduced Cost** --- There are a number of reasons to attribute
	Cloud technology with lower costs. The billing model is pay as per
	usage; the infrastructure is not purchased thus lowering
	maintenance. Initial expense and recurring expenses are much lower
	than traditional computing.
2.  **Increased Storage** --- With the massive Infrastructure that is
	offered by Cloud providers today, storage & maintenance of large
	volumes of data is a reality. Sudden workload spikes are also
	managed effectively & efficiently, since the cloud can scale
	dynamically.
3.  **Flexibility** --- This is an extremely important characteristic.
	With enterprises having to adapt, even more rapidly, to changing
	business conditions, speed to deliver is critical. Cloud computing
	stresses on getting applications to market very quickly, by using
	the most appropriate building blocks necessary for deployment.

Cloud Computing Challenges Despite its growing influence, concerns
regarding cloud computing still remain. In our opinion, the benefits
outweigh the drawbacks and the model is worth exploring. Some common
challenges are:

1.  **Data Protection** --- Data Security is a crucial element that
	warrants scrutiny. Enterprises are reluctant to buy an assurance of
	business data security from vendors. They fear losing data to
	competition and the data confidentiality of consumers. In many
	instances, the actual storage location is not disclosed, adding onto
	the security concerns of enterprises. In the existing models,
	firewalls across data centers (owned by enterprises) protect this
	sensitive information. In the cloud model, Service providers are
	responsible for maintaining data security and enterprises would have
	to rely on them.
2.  **Data Recovery and Availability** --- All business applications
	have Service level agreements that are stringently followed.
	Operational teams play a key role in management of service level
	agreements and runtime governance of applications. In production
	environments, operational teams support Appropriate clustering and
	Fail over Data Replication System monitoring (Transactions
	monitoring, logs monitoring and others) Maintenance (Runtime
	Governance) Disaster recovery Capacity and performance management
	If, any of the above mentioned services is under-served by a cloud
	provider, the damage & impact could be severe.
3.  **Management Capabilities** --- Despite there being multiple cloud
	providers, the management of platform and infrastructure is still in
	its infancy. Features like Auto-scaling for example, are a crucial
	requirement for many enterprises. There is huge potential to improve
	on the scalability and load balancing features provided today.
4.  **Regulatory and Compliance Restrictions** --- In some of the
	European countries, Government regulations do not allow customer's
	personal information and other sensitive information to be
	physically located outside the state or country. In order to meet
	such requirements, cloud providers need to setup a data center or a
	storage site exclusively within the country to comply with
	regulations. Having such an infrastructure may not always be
	feasible and is a big challenge for cloud providers. With cloud
	computing, the action moves to the interface that is, to the
	interface between service suppliers and multiple groups of service
	consumers. Cloud services will demand expertise in distributed
	services, procurement, risk assessment and service negotiation areas
	that many enterprises are only modestly equipped to handle.

4 Main Cloud Deployment
-----------------------

<kbd>![](https://qph.fs.quoracdn.net/main-qimg-34fbe07d9311be4084f7b7b8a502a307) </kbd>
<kbd>![](https://erpsoftwareblog.com/cloud/wp-content/uploads/4-Primary-Cloud-Deployment-Models-Infographic-Turnkey-Technologies1.png) </kbd>

### Public Cloud {#CloudComputingOverview-PublicCloud}

The public cloud deployment model is what typically comes to mind when
we think about cloud computing. In this model, a public cloud provider,
such as Amazon Web Services (AWS) or Microsoft Azure, owns all the
infrastructure required to run an organization\'s IT workloads. Keeping
with the \"someone else\'s computer\" trope, hosting workloads in the
public cloud equates to renting as much computing power and storage
space as you need from someone else\'s giant, infinitely powered PC.

In a recent RightScale survey of 786 technical professionals from both
enterprise-level and small-to-medium businesses, 91% of respondents
reported hosting at least some of their workloads (applications,
document storage, etc.) in the public cloud.

Smaller organizations especially favor the public cloud over other
deployment models: 44% of SMB respondents reported using public cloud
exclusively, from either a single vendor or multiple.

This makes sense: hosting your workloads in the public cloud means you
don\'t need to worry about purchasing, supporting and maintaining any
costly infrastructure; instead, a giant corporation like Amazon or
Microsoft takes care of it all for you while your team works on actually
building things. The absence of an up-front cost removes a significant
barrier to entry for smaller organizations with ambitious development
goals. In the cloud, you only pay for what you need.

This turnkey approach applies to security and reliability as well.
Rather than hosting operations-critical or otherwise sensitive assets on
physical in-house servers (as you would in a traditional on-prem
environment), you\'re entrusting them to a highly secure data center
with more built-in redundancies than you could ever fathom. To give you
an idea, Microsoft\'s SLA guarantees at least 99.9% availability on the
vast majority of its paid services, and up to 99.99% for some critical
services such as DDoS protection.

That\'s more than enough for a large chunk of businesses. But even
99.99% availability is insufficient for some types of organizations,
especially in highly regulated fields like healthcare and
government---hence the remaining three cloud deployment models.

<kbd>![](https://www.sam-solutions.com/blog/wp-content/uploads/2017/08/a-cloud-provider@2x.png) </kbd>

### Private Cloud {#CloudComputingOverview-PrivateCloud}

As far as the end-user experience goes, there isn\'t much difference
between public and private clouds; all those essential characteristics
of cloud computing (resource pooling, on-demand self-service) we briefly
mentioned earlier apply to both.

Infrastructure-wise, a private cloud is essentially a smaller-scale
replica of the datacenters owned by public cloud vendors. Private cloud
deployments are much more expensive than their public cloud
counterparts, but they offer a variety of benefits that make the greater
up-front costs worthwhile.

Businesses rarely go the public cloud-only route: in the aforementioned
survey, only 3% of respondents used this model exclusively to host their
cloud workloads. However, 75% reported using private cloud to some
extent, hosting some workloads privately and entrusting others to public
cloud providers. This is what\'s referred to as a hybrid cloud.

<kbd>![](https://www.sam-solutions.com/blog/wp-content/uploads/2017/08/a-private-cloud@2x.png) </kbd>

### Hybird Cloud {#CloudComputingOverview-HybirdCloud}

As its name suggests, the hybrid cloud deployment model refers to a
combination of private and public clouds used to host an organization\'s
workloads.

For many, hybrid represents the best of both worlds, which explains why
a vast majority of businesses---69%, according to one survey---choose
this approach. (This isn\'t the same thing as a multi-cloud strategy,
which refers to relying on multiple cloud vendors in order to maximize
availability and cost).

Depending on your needs, there are some potential downsides to a hybrid
cloud deployment. Setting up a private cloud usually requires up-front
investment, negating some of the cost-saving benefits of going full
public. It also involves managing your own infrastructure to some
extent. However, if you have a lot of legacy to support yet still wish
to benefit from the public cloud for your other workloads, for instance,
hybrid is often the best-case scenario.

<kbd>![](https://www.sam-solutions.com/blog/wp-content/uploads/2017/08/hybrid-cloud@2x.png) </kbd>

### Community Cloud {#CloudComputingOverview-CommunityCloud}

For the sake of exhaustivity, I\'ve included all four NIST-defined cloud
deployment models in this article, but this last one is by far the least
applicable to most situations. It is, however, an interesting approach.

Basically, the community cloud is run like a cooperative. In a hybrid
cloud deployment, some of your workloads will be hosted in the public
cloud, while others are kept in privately owned and maintained
datacenters. The community cloud, on the other hand, combines aspects of
the public and private cloud in a single, unified environment.

Per  [Gartner\'s always-handy IT
glossary](https://www.gartner.com/it-glossary/community-cloud),
\"Community cloud computing refers to a shared cloud computing service
environment that is targeted to a limited set of organizations or
employees (such as banks or heads of trading firms).\" These groups of
organizations generally share a set of interests and requirements
(usually related to security, compliance and/or jurisdiction) that
can\'t be met by any of the public cloud vendors. Instead of each
building their own private cloud environment, they pool their resources
in order to build a single infrastructure able to support the needs of
each stakeholder. Use cases for community cloud deployments are limited,
but this model comes with highly advantageous cost savings for those to
which it applies.

<kbd>![](https://www.sam-solutions.com/blog/wp-content/uploads/2017/08/community-cloud@2x.png) </kbd>

<table>
	<colgroup>
		<col />
		<col />
		<col />
		<col />
		<col />
	</colgroup>
	<tbody>
		<tr>
			<th>
				<br />
			</th>
			<th>Public</th>
			<th>Private</th>
			<th>Community</th>
			<th>Hybird</th>
		</tr>
		<tr>
			<td>Easy of setup and use</td>
			<td>Easy</td>
			<td>Requires IT proficiency</td>
			<td>Requires IT proficiency</td>
			<td>Requires IT proficiency</td>
		</tr>
		<tr>
			<td>Data security and privacy</td>
			<td>Low</td>
			<td>High</td>
			<td>Comparatively high</td>
			<td>High</td>
		</tr>
		<tr>
			<td>Data Control</td>
			<td>Little to none</td>
			<td>High</td>
			<td>Comparatively high</td>
			<td>Comparatively high</td>
		</tr>
		<tr>
			<td>Reliability</td>
			<td>Vulnerable</td>
			<td>High</td>
			<td>Comparatively high</td>
			<td>High</td>
		</tr>
		<tr>
			<td>Scalability and flexibility</td>
			<td>High</td>
			<td>High</td>
			<td>Fixed capacity</td>
			<td>High</td>
		</tr>
		<tr>
			<td>Cost-effectiveness</td>
			<td>The cheapest one</td>
			<td>
				Cost-intensive, the most expensive one
			</td>
			<td>Cost is shared among community members</td>
			<td>
				Cheaper than a private model but more costly than a public one
			</td>
		</tr>
		<tr>
			<td>Demand for in-house hardware</td>
			<td>No</td>
			<td>Depends</td>
			<td>Depends</td>
			<td>Depends</td>
		</tr>
	</tbody>
</table>

References

-   [Medium - Cloud computing overview](https://medium.com/@nikitaag3110/cloud-computing-overview-1921bb5fd6ec)
-   [Quora - What are the different deployment models in Cloud computing](https://www.quora.com/What-are-the-different-deployment-models-in-Cloud-computing)
-   [Sharegate - cloud deployment models compared](https://sharegate.com/blog/cloud-deployment-models-compared)
-   [Solutions Review - cloud platforms understanding the 4 biggest cloud deployment models](https://solutionsreview.com/cloud-platforms/understanding-the-4-biggest-cloud-deployment-models/)
-   [Sam Solutions - four best cloud deployment models you need to know](https://www.sam-solutions.com/blog/four-best-cloud-deployment-models-you-need-to-know/)


