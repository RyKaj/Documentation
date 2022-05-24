###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [DevOps](https://github.com/RyKaj/Documentation/tree/master/DevOps/README.md) |
------------

# DevOps : Kubernetes Design Patterns

<img src="./attachments/471992249.png" alt="" />



## Foundational Patterns

These patterns represent the principles and best practices that containerized applications must comply with in order to become good cloud-native citizens. Regardless of the application’s nature, you should aim to follow these guidelines. Adhering to these principles will help ensure that your applications are suitable for automation on Kubernetes.

### Health Probe Pattern

_Health Probe_ dictates that every container should implement specific APIs to help the platform observe and manage the application in the healthiest way possible. To be fully automatable, a cloud-native application must be highly observable by allowing its state to be inferred so that Kubernetes can detect whether the application is up and ready to serve requests. These observations influence the life-cycle management of Pods and the way traffic is routed to the application.

### Predictable Demands Pattern
_Predictable Demands_ explains why every container should declare its resource profile and stay confined to the indicated resource requirements. The foundation of successful application deployment, management, and coexistence on a shared cloud environment is dependent on identifying and declaring the application’s resource requirements and runtime dependencies. This pattern describes how you should declare application requirements, whether they are hard runtime dependencies or resource requirements. Declaring your requirements is essential for Kubernetes to find the right place for your application within the cluster.

### Automated Placement Patterns

_Automated Placement_ explains how to influence workload distribution in a multi-node cluster. Placement is the core function of the Kubernetes scheduler for assigning new Pods to nodes satisfying container resource requests and honoring scheduling policies. This pattern describes the principles of Kubernetes’ scheduling algorithm and the way to influence the placement decisions from the outside.

  

## Structural Patterns

Structural patterns are focused on the composition of building blocks to create higher-level complex resources. In microservice architecture, applications are packaged and deployed as containers. This approach makes it easier to scale applications with less overhead and more isolation. However, this makes it difficult to schedule and run related containers side-by-side, or sequentially in a cluster with thousands of nodes. For instance, if you want to run your frontend and backend containers together in a cluster, you need to find a mechanism so that you can always schedule them to the same nodes. Likewise, if you need to fill in configuration file templates before starting your application, there is a need to ensure that configuration handler containers are running before the application is.

In Kubernetes, containers are the building blocks that are encapsulated in pods. As a container orchestrator, Kubernetes provides built-in functionalities for organizing containers within pods. In this section, the sidecar and initialization structural design patterns for Kubernetes will be explained.

Having good cloud-native containers is the first step, but not enough. Reusing containers and combining them into Pods to achieve the desired outcome is the next step. The patterns in this category are focused on structuring and organizing containers in a Pod to satisfy different use cases. The forces that affect containers in Pods result in these patterns.

### Initialization Container Pattern


_Init Container_ introduces a separate life cycle for initialization-related tasks and the main application containers. Init Containers enable separation of concerns by providing a separate life cycle for initialization-related tasks distinct from the main application containers. This pattern introduces a fundamental Kubernetes concept that is used in many other patterns when initialization logic is required.

Initialization is a widespread pattern in every part of software engineering, including programming languages and operating systems. In order to handle the initialization of an application in Kubernetes, initialization containers are proposed. Initialization containers, namely **initContainers**, are part of a pod's definition. Separation of concerns is handled by separating the life cycles of containers:

*   Init containers
*   Main containers

Containers that are defined as initContainers are executed for completion one by one, and they are all expected to exit successfully. After successful completion, the main containers are started. Some of the example uses of startup containers are as follows:

*   To create configuration files
*   To wait and ensure dependency services are available
*   To create volumes and prepare files
*   To register services to discovery systems

In the following activity, a web server will be installed in Kubernetes. As expected, there should be at least one container running the web server. However, there is an additional requirement of changing the served files before the web server starts. The life cycle of these operations is separated into the initialization container and the main container. These containers could have different container images and executables; however, they are expected to work on a shared resource. Life cycle separation and working together issues are handled in the following activity, and the initialization pattern is implemented in Kubernetes.

### Sidecar Patterns


_Sidecar_ describes how to extend and enhance the functionality of a pre-existing container without changing it. This pattern is one of the fundamental container patterns that allows single-purpose containers to cooperate closely together.

Modern software applications often require external functionalities such as monitoring, logging, configuration, and networking. When these functionalities are tightly integrated into the application, they can run as a single process. However, this violates the isolation principle and creates an opportunity for a single point of failure. With this idea, containers in cloud-native applications are expected to follow the Unix philosophy:

*   Containers should have one task
*   Containers should work together
*   Containers should handle text streams

The Unix philosophy focuses on designing a small operating system with a clean service interface. To have such a system, simple, precise, clear, and modular software development should be undertaken, taking into consideration the developers and maintainers. Besides, the philosophy emphasizes that you should compose subsystems instead of creating a big, monolithic design.

With this idea, it is a conventional approach to separate the main application and run a couple of sidecars attached, which are provided for extra functionality. The main advantages of using a sidecar are as follows:

*   They have independent programming languages and runtime dependencies
*   They monitor the main application closely and minimize latency
*   They extend black box applications

In the following activity, a web-based game will be installed in Kubernetes. As expected, there should be at least one container running the web server. However, there is an additional requirement of continuous source code synchronization. With the Unix philosophy, it is expected to make containers with only one primary task. They should also work independently and together to achieve the necessary requirements. Finally, these containers should update their statuses, informing the console as log lines. All three of these points are covered in the following activity.

  

## Behavioural Patterns

In software development, behavioral design patterns focus on the communication and interaction between objects. Interaction and communication includes responsibility assignment, the encapsulation of behaviors, and the delegation of requests. With the microservice architecture, behavioral patterns focus on the communication between microservices and the interaction of services with orchestration tools.

For instance, let's consider the execution of a microservice that checks a user's quota daily. It can be implemented by an infinite loop that includes 24 hours of sleep and the execution of the quota check. Although it works, it consumes additional resources during sleep and creates an inefficient architecture. With the behavioral pattern of the "scheduled job pattern," orchestration tools could handle the scheduling of the microservice and ensure that it runs every 24 hours.

In Kubernetes, containers are encapsulated inside pods, which are the primary interest of behavioral patterns. Behavioral patterns are focused on the interaction and communication of the Kubernetes resources, namely pods, with the Kubernetes services. Communication and interaction within the controller system could include the distribution of pods to nodes, the scheduling of pods, or metadata distribution by the Kubernetes master and node components. The following behavioral patterns are covered in the following sections:

These patterns describe the life-cycle guarantees of the Pods ensured by the managing platform. Depending on the type of workload, a Pod might run until completion as a batch job or be scheduled to run periodically. It might run as a daemon service or singleton. Picking the right life-cycle management primitive will help you run a Pod with the desired guarantees.

*   The job pattern
*   The scheduled job pattern
*   The daemon service pattern
*   The singleton service pattern
*   The introspective pattern

### Batch Job Patterns


_Batch Job_ describes how to run an isolated, atomic unit of work until completion. This pattern is suited for managing isolated atomic units of work in a distributed environment.

The general use case of pods in Kubernetes is that they are used for long-running processes that are always up. To this aim, Kubernetes provides higher-level resources such as replication sets or deployments. These high-level resources manage the life cycles of pods by creating replicas, checking for health statuses, and controlling update mechanisms. On the other hand, there is a need for microservices that do one job and successfully exit upon completion. For instance, database initializations, backups, or converting a video should run once and exit without consuming any extra resources. For this requirement, Kubernetes provides a higher-level resource named Job. Kubernetes jobs represent an isolated work run until completion and are ideal for use cases that are required to only run once.

### Scheduled Job Pattern


Distributed systems and the microservices architecture do not rely on temporal events for running services; instead, they focus on triggers such as HTTP requests, new database entries, or messaging queues. However, scheduling a task and expecting it to run at specified intervals are common approaches that are part of the "Scheduled Job Pattern". Microservices for maintenance operations, sending daily emails, or checking for old files should be scheduled at fixed intervals and must run to meet business needs. Kubernetes provides the CronJob resource for creating scheduled tasks, and it ensures that these jobs are running.

### Daemon Service Pattern

Daemon applications are commonly used in operating systems and programming languages as long-running applications or threads that run as background processes. The names of the daemon applications are httpd, sshd, and containerd; the trailing letter indicates that the services are daemons. Within the microservice architecture, some services should run and scale without any relation to consumer usage. These applications should run on every node in the cluster to ensure the daemon application's requirements, such as:

*   **Cluster storage daemons**: glusterd, ceph.
*   **Log collection daemons**: fluentd, logstash.
*   **Node monitoring daemons**: collectd, Datadog agent, New Relic agent.

In Kubernetes, **DaemonSets** are designed for deploying ongoing background tasks that need to run on all or certain nodes. Without any further management considerations, Kubernetes handles running these daemon pods on the newly joined nodes in the cluster.

### Singleton Service Pattern

Running one – and only one – instance is a requirement for applications, since multiple instances could create instability. Although it seems to be against the scalable microservice architecture, there are some applications that are required to follow the singleton pattern:

*   Database instances and connectors
*   Configuration managers
*   Applications that do not scale yet

Kubernetes StatefulSet with a replica count of 1 ensures that only instances of the pod are running in the cluster. With this small configuration, singleton services can be created and used in a cloud-native environment. However, having only one instance of an application in the cluster comes with its drawbacks. For instance, handling the downtime of singleton applications should be handled with care. The primary concern for this issue is how to handle downtime due to the automatic update of Statefulset.

### Introspective Pattern

Applications that run on bare-metal clusters know precisely where they are running, the specification of the system, and their network information. This information helps them to work in a self-aware environment. For instance, these applications can align their resource usage, enhance their logs with more data, or send their node-related metric data. In the microservice architecture, applications are considered ephemeral with less dependency than the environment they are running on. However, self-awareness about runtime information, namely the introspective pattern, could increase the utility and discoverability of applications in distributed systems.

In Kubernetes, the Downward API ensures that the following environment and runtime data is provided for the pods:

*   **Environment:** Node name, namespace, CPU, and memory limitations.
*   **Networking:** Pod IP.
*   **Authorization:** Service account.

In the following activity, a simple but self-aware Kubernetes application will be created and installed. The application has all of the runtime information, which is provided by Kubernetes as environment variables. Being a single application, it logs all of these variables to the console. However, the pod definition that's developed throughout this activity shows you how to use the Downward API inside containers to implement an introspective pattern in Kubernetes.

### Deployment Strategies

Designing and developing cloud-native applications with the microservice architecture is essential for reliable and scalable applications of the future. Likewise, deploying and updating applications in the cloud is as critical as design and development. There are various techniques for delivering applications, and therefore choosing the right setup is essential to leverage the impact of change on the consumers. Using the right subset of Kubernetes resources and choosing an appropriate deployment strategy, scalable and reliable cloud-native applications are feasible.

In this section, the following deployment strategies are presented, and you are expected to complete these exercises so that they can see the Kubernetes resources in action:

*   Recreate strategy
*   Rolling update strategy
*   Blue/green strategy
*   A/B testing strategy

### Recreate Strategy

The recreate strategy is based on the idea of closing old version instances and then creating the next version's. With this strategy, it is inevitable to have downtime, depending on both the shutdown and start duration of applications. In Kubernetes, the recreate strategy can be used for creating deployment resources with the strategy of recreate.

### Stateful Service Patterns

_Stateful Service_ describes how to create and manage distributed stateful applications with Kubernetes. Such applications require features such as persistent identity, networking, storage, and ordinality. The StatefulSet primitive provides these building blocks with strong guarantees ideal for the management of stateful applications.

### Service Discovery Pattern

_Service Discovery_ explains how clients can access and discover the instances that are providing application services. For this purpose, Kubernetes provides multiple mechanisms, depending on whether the service consumers and producers are located on or off the cluster.

## Higher-Level Patterns

The patterns in this category are more complex and represent higher-level application management patterns. Some of the patterns here (such as Controller) are timeless, and Kubernetes itself is built on top of them.

### Controller Pattern

_Controller_ is a pattern that actively monitors and maintains a set of Kubernetes resources in a desired state. The heart of Kubernetes itself consists of a fleet of controllers that regularly watch and reconcile the current state of applications with the declared target state. This pattern describes how to leverage this core concept for extending the platform for our own applications.

### Operator Pattern

An _Operator_ is a Controller that uses a CustomResourceDefinitions to encapsulate operational knowledge for a specific application in an algorithmic and automated form. The Operator pattern allows us to extend the Controller pattern for more flexibility and greater expressiveness. There are an increasing number of [Operators](http://operatorhub.io/) for Kubernetes, and this pattern is turning into the major form of operating complex distributed systems.  

Kubernetes is the new application portability layer and the common denominator among everybody on the cloud. If you are a software developer or architect, the odds are that Kubernetes will become part of your life in one form or another. Learning about the Kubernetes patterns described here will change the way you think about this platform. I believe that Kubernetes and the concepts originating from it will become as fundamental as object-oriented programming concepts.

<img src="./attachments/471992250.png" alt="" />

  


  

References

*   [Developers Redhat - top 10 must know kubernetes design patterns](https://developers.redhat.com/blog/2020/05/11/top-10-must-know-kubernetes-design-patterns/)
*   [Subscription packtpub - kubernetes design patterns](https://subscription.packtpub.com/book/virtualization_and_cloud/9781789619270/1/ch01lvl1sec10/kubernetes-design-patterns)
*   [Kubernetes.io - what is kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/)
*   [Arungupta.me - docker container anti patterns](http://blog.arungupta.me/docker-container-anti-patterns/)
*   [https://vitalflux.com/container-design-patterns-kubernetes-pods-design](https://vitalflux.com/container-design-patterns-kubernetes-pods-design/)
*   [https://blog.sensu.io/how-kubernetes-works](https://blog.sensu.io/how-kubernetes-works)
*   [Magalix - Kkubernetes Scheduler 101](https://www.magalix.com/blog/kubernetes-scheduler-101)
*   [Magalix - Kubernetes deployments 101](https://www.magalix.com/blog/kubernetes-deployments-101)
*   [Magalix - Kubernetes cluster networking 101](https://www.magalix.com/blog/kubernetes-cluster-networking-101)
*   [Magalix -  Kubernetes pods 101 the cluster sailors](https://www.magalix.com/blog/kubernetes-pods-101-the-cluster-sailors)
*   [Magalix - Kubernetes 101 concepts and why it matters](https://www.magalix.com/blog/kubernetes-101-concepts-and-why-it-matters)
*   [Magalix  - kubernetes patterns application process management](https://www.magalix.com/blog/kubernetes-patterns-application-process-management-1) 
*   [Magalix -  kubernetes patterns capacity planning](https://www.magalix.com/blog/kubernetes-patterns-capacity-planning)
*   [Medium  - what is kubernetes](https://medium.com/microservices-for-net-developers/what-is-kubernetes-69281e4bc4b4)
*   [Medium sindhujacynixit - what benefits does kubernetes offer](https://medium.com/@sindhujacynixit/what-benefits-does-kubernetes-offer-c94192fb15b7)
*   [Medium - kubernetes components](https://medium.com/faun/kubernetes-components-ca583ddedeb6)
*   [Stackrox - 12 kubernetes configuration best practices](https://www.stackrox.com/post/2019/09/12-kubernetes-configuration-best-practices/)
*   [Onlineitguru - kubernetes training](https://onlineitguru.com/kubernetes-training.html)
*   [tnext.io - successful short kubernetes stories for devops architects](https://itnext.io/successful-short-kubernetes-stories-for-devops-architects-677f8bfed803)
*   [Linkedin -  sangambiradar14 kubernetes activity](https://www.linkedin.com/posts/sangambiradar14_kubernetes-activity-6627496268497285121-fBGU/)
*   [Octopus Deploy - advanced-deployment-patterns](https://octopus.com/advanced-deployment-patterns)
*   [Octopus Deploy  - blue green deployments](https://octopus.com/docs/deployment-patterns/blue-green-deployments)
*   [Octopus Deploy - Blue green red black](https://octopus.com/blog/blue-green-red-black)
*   [Octopus Deploy - Guide Failures](https://octopus.com/docs/deployment-process/releases/guided-failures)
*   [Dev.to David J. Eddy - Whats the difference ab testing vs bluegreen deployment](https://dev.to/david_j_eddy/whats-the-difference-ab-testing-vs-bluegreen-deployment-3p77)
*   [Testing Excellence - Difference between greenblue deployments ab testing and canary releases](https://www.testingexcellence.com/difference-between-greenblue-deployments-ab-testing-and-canary-releases/)
*   [Blazemeter - five blue green deployment best practices for a smooth release/](https://www.blazemeter.com/blog/five-blue-green-deployment-best-practices-for-a-smooth-release/)
*   [Martin Fowler - Blue Green Deployment](https://martinfowler.com/bliki/BlueGreenDeployment.html)
*   [Martin Fowler - Canary Release](https://martinfowler.com/bliki/CanaryRelease.html)
*   [Cloud Foundry Document - Using Blue-Green Deployment to Reduce Downtime and Risk](https://docs.cloudfoundry.org/devguide/deploy-apps/blue-green.html)
*   [Sweetibharti - red black deployment on aws](https://sweetibharti.wordpress.com/2016/11/11/red-black-deployment-on-aws/)
*   [Rollout - blue green deployment/](https://rollout.io/blog/blue-green-deployment/)
*   [Optimizely - ab testing](https://www.optimizely.com/optimization-glossary/ab-testing/)
*   [vwo - What is A/B Testing](https://vwo.com/ab-testing/)
*   [UnBounce - what is ab testing](https://unbounce.com/landing-page-articles/what-is-ab-testing/)
*   [How](https://blog.hubspot.com/marketing/how-to-do-a-b-testing) to do a AB Testing
*   [Techcrunch](https://techcrunch.com/2014/06/29/ethics-in-a-data-driven-world/) - The Morality of AB Testing
*   [Kubernetes - what is kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/)
*   [Opsmx - Setup automated release analysis spinnaker](https://blog.opsmx.com/setup-automated-release-analysis-spinnaker/)
*     
