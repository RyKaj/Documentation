###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [DevOps](https://github.com/RyKaj/Documentation/tree/master/DevOps/README.md) |
------------

DevOps : Maturity Model
==============================================


Maturity Model

By definition, DevOps Maturity is described as a model that determines an organization’s standing in DevOps journey along with determining what more to be accomplished to achieve the desired results. Understanding DevOps adoption ‘as a continuous journey, not a destination’ stands crucial to achieving DevOps maturity.  The DevOps maturity model determines growth through continuous learning from both teams and organizational perspectives. More the capabilities and skills, more will be the ability to handle issues of scale and complexities.

Based in the C.A.L.M.S. definition of DevOps, the framework defines a set of capabilities and guidelines that when adopted, increases efficiency (speed, cost...), effectiveness (quality...) and happiness of the team.

*   **C**ulture
*   **A**utomation
*   **L**ean
*   **M**easurement
*   **S**haring

  

**Culture and Strategy**

DevOps has to be understood as a culture-driven approach that brings together different teams, driving them towards a common objective. Transition to DevOps means a transformation in the organization’s operating culture backed by a set of policies and process frameworks. So, that needs proper planning and perfect strategy

**Automation**

Automation is key to continuous delivery and continuous deployment mechanisms in DevOps process. By automating repetitive tasks, the automation process eases development, testing and production in a DevOps cycle, thus saving time and enhancing resource efficiency.

**Structure and Process**

Modern-day IT functioning is process-oriented and involves processes across all stages of the Software Development Life Cycle (SDLC). This has advanced in a DevOps environment, where every stage is a set of processes in line with corporate policies and business objectives.

**Collaboration and Sharing**

This is the most important aspect of [DevOps culture](https://www.veritis.com/solutions/devops/). Collaboration and sharing are key to DevOps and teams (on the same location or a different location) will need to align tools and resources towards achieving common goals and objectives.

**According to Forbes research, organizations, most commonly, find themselves in one of the following stages as part of their DevOps journey:**

*   **Unconscious incompetence:** Organizations fail to understand DevOps and its advantages
*   **Conscious incompetence:** Organizations still see siloed processes even after 12-18 months of DevOps journey with some automation
*   **Conscious competence:** After four years of DevOps journey and successful automation, organizations focus on collaboration across teams and streamline sharing mechanism
*   **Unconscious competence:** Here, organizations are all set with structured frameworks, in-depth collaboration, the concrete process for effective sharing

A perfect DevOps maturity model determines DevOps maturity in three ways:

*   Assessment of the current state of capabilities
*   Identifying areas of improvement
*   Outlining steps to achieve desired DevOps goals

In line with these three steps, the DevOps maturity block verifies maturity in build, deploy and test stages across application, data and infrastructure levels:

**DevOps Maturity for Application –** Determines DevOps maturity by the ease in code movement from Development to Production phase. Achieving this requires having builds, tests, code coverage, security scans and monitoring as automated components part of deployment pipeline.

**DevOps Maturity by Data –** Determines DevOps maturity by ability to clear path to automate changes to data and validate functionality on a regular basis, through DataOps.

**DevOps Maturity by Infrastructure –** Determines DevOps maturity by ability to ease infrastructure using capabilities around automation, streamlining and enabling self-service to provision environments, among other tasks.

![DevOps Maturity model involves five transformation stages](https://www.veritis.com/wp-content/uploads/2019/10/devops-maturity-model-involves-five-transformation-stages.jpg)

### Stage-1: Initial

Traditional environment with Dev and Ops separated is handled

### Stage-2: Managed

Beginning of change mindset focused on agility in Dev and initial automation in Ops, with emphasis on collaboration.

### Stage-3: Defined

Organization-wide transformation begins with defined processes and established automation.

### Stage-4: Measured

Better understanding of process and automation, followed by continuous improvement.

### Stage-5: Optimized

Achievements are visible, team gaps disappear, and employees gain recognition

While these 5 stages make a complete DevOps maturity model, it’s imperative for enterprises to keep checking their maturity at every stage, and eventually identify focus areas and ways to evolve in the overall journey

**What to Measure in a DevOps Maturity Model**

There are a set of parameters to be measured at every stage of DevOps Maturity Model to confirm an organization’s level of DevOps maturity. These measures ideally define the direction the organization is advancing in its DevOps journey. They are:

*   Number of completed projects and the release frequency should ideally high resulting in ROI
*   Percentage of successful deployments should maintain an edge over unsuccessful ones
*   Mean Time To Recovery (MTTR) from an unexpected incident/failure from the time of occurrence, should be nil or as low as possible
*   Lead time, from development of code to deployment in production should be satisfactory
*   Deployment frequency to determine the frequency of new code deployments

The stage-wise process and the above parameters define an organization’s DevOps maturity success.

Framework
---------

1.  The first step will be to do a self-assessment of the current status of your Product Team for each one of the identified capabilities.
    
2.  Define the desired end-point at the end of the next improvement cycle, a cycle can be a month, a quarter, a semester ... every team can define their improvement cycles although a good start would be to set quarterly targets to be able to define meaningful actions.
    
3.  Identify the actions you will need to achieve the desired end-point.
    

### Development

*  Capability
*  Crawl
*  Walk
*  Run
*  Use version control for all production artifacts
*  No version control
*  Source code or other assets under version control
*  Source code or other assets under version control and all production artifacts versioned and stored in the corresponding artifact repository
*  Automate deployment processes
*  Manual deployment process
*  Partially automated deployment process
*  Fully automated deployment process
*  Implement test automation
*  Manual test script execution
*  Partially automated testing (unit or regression or performance tests)
*  Fully automated testing (unit and regression and performance tests)
*  Implement infrastructure automation
*  Manual deployment process
*  Partially automated deployment process. Provisioning is done by the teams
*  Fully automated deployment (infrastructure-as-code). Platform Engineering provides base images
*  Support test data management
*  No test data management
*  Partially automated test data management (e.g. manually triggered import and export of test data)
*  Fully automated test data management incl. strategy (e.g. consumer data only in PROD)
*  Implement continuous delivery
*  No continuous delivery
*  Partially automated delivery pipeline (e.g. automated build, test process with the manual deployment)
*  Fully automated pipeline (automated build, test, deployment across environments)
*  Include NFR’s in Definition of Done
*  No NFR's used
*  Ad-hoc NFR checks
*  Standardised NFR checklist as acceptance criteria for successful releases
*  Shift left on security
*  No security aspects considered during development cycle
*  Security aspects considered during development cycle but shifted towards release (not a priority)
*  Security aspects included during development cycle from the very start
*  Build for resilience
*  No resilience build into system
*  Design infrastructure and code for failure
*  Design infrastructure and code for failure with fully automated error recovery (self-healing)
*  Enable team for troubleshooting
*  No control over development lifecycle (e.g. access to PROD)
*  Team has full control over development lifecycle (e.g. access to PROD), but no access to logs and tools relevant for troubleshooting
*  Team has full control over development lifecycle (e.g. access to PROD) and full access to logs and tools for troubleshooting

### Product & Processes

*  Capability
*  Crawl
*  Walk
*  Run
*  Gather and implement customer feedback
*  No customer (internal or external) feedback gathered in development cycles
*  Customer feedback (internal or external) gathered on an ad-hoc basis
*  Customer feedback (internal or external) gathered after all releases
*  Work in small batches and deploy more frequently
*  Big work batch size and releases on a monthly basis or longer
*  Work batch size optimized for weekly releases, but deployment frequency not in sync with business requirements (e.g lead time)
*  Work batch size optimized for frequent releases and deployment frequency in sync with business requirements (e.g. lead time)
*  Have a lightweight change approval process
*  Change approval needed from multiple parties outside the team
*  Change approval needed within the team
*  No change approval needed or change approval process totally automated
*  Integrate application data into Big Data Platform
*  No application data transferred at all
*  Partial business-relevant application data transferred to Big Data Platform or provided via API
*  All business-relevant application data transferred to Big Data Platform

### Management & Monitoring

*  Capability
*  Crawl
*  Walk
*  Run
*  Monitor application and infrastructure performance
*  No monitoring in place
*  Application or infrastructure performance monitored but no alerting in place
*  Application and infrastructure performance is monitored; alerting in place for relevant KPI's
*  Monitor software delivery performance
*  No metrics monitored
*  Selected metrics monitored
*  All key metrics monitored
*  Limit Work in Progress
*  More than 10 features in progress
*  Less than 10 features in progress
*  Not more than 5 features in progress

  

### Architecture

*  Capability
*  Crawl
*  Walk
*  Run
*  Use a loosely coupled architecture
*  Monolithic application with a high level of interdependencies
*  Re-architecture in progress moving from a monolithic solution to a microservice-based architecture
*  System has no or very few direct dependencies to other systems. And those dependencies are tied to open standards and not tied to technologies and frameworks (e.g. Java RPC)
*  Focus on independent deployability and testability
*  Dependent deployability and testability across teams
*  Some components can be deployed and tested independently but parts of the components still have dependencies across teams
*  Teams can deploy and test their systems independently
*  Use established Platform Engineering solutions as a default
*  Custom solutions used even though provided by Platform Engineering
*  All solution aligned with Platform Engineering, Solution and Domain Architecture, but exceptions were granted
*  All solutions aligned with Platform Engineering, Solution and Domain Architecture and no custom solutions used that are provided by Platform Engineering

**DevOps Maturity Linked to Security**

DevOps maturity is directly linked to DevOps security. As organizations progress in DevOps journey, competitive edge becomes a serious demand calling for faster release cycles and digital innovation demands a strong pitch.

This is where the challenge of security starts becoming more serious and which is why DevOps maturity calls for reconsidering of security practices.

Eventually, organizations will have to make security an integral part of their [DevOps process](https://www.veritis.com/solutions/devops/) and take it closer to all stages of application development.

At the maturity level, DevOps experts work with security personnel for early security integration across all parts of the Software Development Lifecycle.

This can happen through effective [DevSecOps implementation](https://www.veritis.com/solutions/devops/devsecops-services/). solutions like [Containerization](https://www.veritis.com/solutions/containerization-services/) can also help to some extent in addressing issues on a continuous basis by limiting the vulnerable resources.

Moreover, Security and DevOps teams can also collaborate in applying security policies and frameworks to all the [DevOps tools](https://www.veritis.com/solutions/devops/made-easier-with-devops-tools/) and resources.

### Business Benefits of DevOps Maturity

Giving a complete picture of an organization’s DevOps standing, the DevOps maturity model presents a wide range of business benefits:

*   Faster adaptability to change
*   Ability to tap opportunities
*   Identifying areas of fulfillment
*   Improved scalability
*   Operational efficiency
*   Increased delivery speeds
*   Enhanced quality

More such benefits are part of the DevOps Maturity model that gives you the ability to witness the full DevOps potential.

What are the Phases of DevOps Maturity

There are several phases to DevOps maturity; here are a few of the key phases you need to know.

Continuous Integration
----------------------

Continuous integration is the practice of quickly integrating newly developed code with the main body of code that is to be released. Continuous integration saves a lot of time when the team is ready to release the code.

![](https://miro.medium.com/max/700/0*X4lG2bqBrxA6eDfP.png)

DevOps didn’t come up with this term. Continuous integration is an agile engineering practice originating from the Extreme Programming methodology. The terms been around for a while, but DevOps has adopted this term because automation is required to successfully execute continuous integration. Continuous integration is often the first step down the path toward DevOps maturity.

The continuous integration process from a DevOps perspective involves checking your code in, compiling it into usable (often binary executable) code and running some basic validation testing.

Continuous Integration (CI) is a development practice of regularly merging their code changes into a shared repository where those updates are automatically tested. Code needs to be merged at least once a day. Each code check-in is then verified by an automated build to detect conflicting code early on. This way bugs can be detected quickly and without much effort. The most up-to-date and validated code is always readily available to developers.

So, you come to work and pull code into your private workspace. The coffee is being consumed and the work happens. When you are done, you commit your code changes to the central repository and Continuous Integration server takes it from here. The server is continuously monitoring for incoming code commits. When it receives one, it builds the system and runs unit and integration tests. Deployable artifacts are released for testing, the build version is assigned to your code and the whole team is informed about the successful build. If your build or tests fails, everyone is alerted and you have to fix the issue ASAP, so the process could continue.

Each developer is responsible for doing a complete build and passing all the tests. The main point of CI is that everyone is working on a known stable code base. Therefore, if your build fails, nothing has a higher priority than fixing the build.

Continuous Delivery
-------------------

Continuous delivery is an extension of continuous integration \[DevOps stage 2\]. It sits on top of continuous integration. When executing continuous delivery, you add additional automation and testing so that you don’t just merge the code with the main code line frequently, but you get the code nearly ready to deploy with almost no human intervention. It’s the practice of having the code base continuously in a ready-to-deploy state.

Continuous Delivery (CD) is the next logical step from CI. It is the practice of frequently building, testing and packaging code changes for a release into production. CD automates the release process so that new builds can be released at the click of a button. Such practice accelerates time to market and allows you to obtain user feedback more quickly.

With CD your code is not released straight to production, so you can still do manual user testing in the staging environment. This can be very handy if your business operates in a sensitive domain, like telecom and medical, where regulations require extensive testing to be made. Some of your customers may not want continuous updates to their systems. Finally, there may be some edge cases where code releases cannot be easily verified with automation – building automated tests can simply take unreasonably long time and still be error prone.

Continuous Deployment
---------------------

Continuous deployment, not to be confused with continuous delivery \[DevOps nirvana\], is the most advanced evolution of continuous delivery. It’s the practice of deploying all the way into production without any human intervention.

In a Continuous Deployment process, every validated build is automatically released. Once the developer commits his code change, there is zero manual intervention before it gets to production. You can now build even smaller and more frequent releases. This way you accelerate time to production, reduce complexity by not having a staging environment and no longer need to schedule your releases. Your feedback loop gets shorter, since you now get user feedback quicker.

Continuous Deployment is the golden goose of DevOps, but it is best applied after your DevOps team has nailed down its processes. For continuous deployment to work well, organizations need to have a rigorous and reliable automated testing environment. If you are not there yet, start with Continuous Delivery to have that extra safety step and transition gradually.

  

![continuous-delivery-vs-continous-deployment](https://devtipscurator.files.wordpress.com/2017/02/continuous-delivery-vs-continous-deployment.png?w=736)
![](https://miro.medium.com/max/700/0*NU_81jBIf1JTVNjT.jpg) 

Teams that utilize continuous delivery don’t deploy untested code; instead, newly created code runs through automated testing before it gets pushed out to production. The code release typically only goes to a small percentage of users and there’s an automated feedback loop that monitors quality and usage before the code is propagated further.

There are a very small number of companies that are truly practicing continuous deployment. Netflix, Etsy, Amazon, Pinterest, Flicker, IMVU and Google are popular examples of companies doing continuous deployment.

While DevOps nirvana is often not the end goal for most enterprises, they often focus on moving towards continuous delivery.

DevOps - Immature Teams vs Mature Teams

  

As a DevOps team matures, they often find that their environment fills with a growing number of moving parts. When all of these pieces are moving in concert, new features are released regularly and smoothly. This isn’t only true for technology. Mature DevOps teams have processes that work harmoniously with one another to make shipping code smoother. The same is not necessarily true for immature teams. Immature teams rely on faulty processes and poorly-configured architecture. These delay releases, suck up engineer time with tedious tasks, and cause the team to ship more bugs to customers.

Savvy teams seek ways to avoid these kinds of failures. As a team learns, it progresses through various states of DevOps maturity. Sometimes those tools to avoid failure will be technical in nature, but just as often they’ll be changes to process or lines of communication. A team can have the best tech in the world, but if they have bad processes, they’re still going to fail as often as they succeed.

<img src="./attachments/463532394.png" alt="">

  

**Release management** is the process of how a team coordinates the actual release of code to customers. Good code tends to pass through a variety of steps so that stakeholders throughout the business can verify its validity. Beyond simply designing and writing the code, code needs to go through testing, user acceptance, and compliance phases. These steps ensure that the code does what it says it does, that customers are happy with what it does, and that it doesn’t expose the company to risk.

**Test environment management** is the process of making sure that code is tested in an environment as close to release as possible. This means effectively building a miniature production environment while also ensuring that the security of the organization and its customers remains strong.

**Deployment planning** is about making sure that a release has all the necessary resources, both at launch and after release.

  

**Immature Teams**

Release Management
------------------

### How Do Immature Teams Do Release Management?

Anyone who’s worked in a big organization before innately understands immature release management. Usually, the process for release management is (in a word) slow. A feature will experience lengthy stops at each gate of the process. Oftentimes, a feature will sit in a queue, meaning that it’ll wait days or weeks before someone is able to evaluate the code’s fitness. Then, as is common with any bit of code, it’s likely that the gatekeeper will discover some issues. The developer responsible for those features is able to begin to correct the problems. Then, they’ll send it back through the gates. Again, at each stop along the way, the code will experience lengthy delays before a human actually looks at it.

Just like developers, operations staff suffer from this degree of manual process. Immature teams manually manage their technological resources. If a new feature requires some kind of new service, such as a message queue, operations staff are on the hook to deliver. That doesn’t just mean delivering a message queue to production, either. It means a message queue for testing environments, and a message queue for quality assurance. It means going through manual approval by the compliance team. Manual environment management can feel like putting out fires. Just when the team thinks everything is under control, some new environment is needed. The process starts all over again from the beginning.

Once those systems are set up, monitoring them is also a manual task. Operations staff need to manually collect metrics, and when those metrics are outside of acceptable parameters, they report that manually, too.

### Immature Teams Don’t Think Past the Release

Eventually, the wait between writing the code and releasing it becomes so lengthy that developers will probably need to combine it with some other group of features and bug fixes into a bigger release. This means the process starts all over. The result is significant frustration for technical and project management teams. No one can predict when a new feature will ship to customers. No one is ever sure which features or bug fixes will be part of a release.

What’s more, this kind of gating ignores a crucial part of release management: post-launch support. Clever readers will notice that the entirety of the release management process described above focuses on what happens before a release. Obviously, software isn’t released into a void. Customers have feedback. Their needs change. Bugs the testing team didn’t catch rear their heads. Immature teams have no plans for the way that they’ll deal with these issues.

Test Environment Management
---------------------------

### How Do Immature Teams Do Test Environment Management?

Test environment management is something that many immature teams don’t consider at all. Test environments need to be manually configured by an engineer every time something changes. This means that code can regularly find itself in an environment that looks nothing like the production environment. Critical services might lack important updates. Databases could use a very old schema or severely outdated data.

Some organizations will choose to simply copy their production database straight to their testing environment. This can lead to issues too; these databases will contain [personally-identifiable information](https://www.technology.pitt.edu/help-desk/how-to-documents/guide-identifying-personally-identifiable-information-pii) of customers. Protecting that important information is critical, so exposing it on a testing environment risks disclosing that information to unauthorized employees.

As noted previously, fully-manual testing processes are prone to long delays. People get busy. This is especially true of project gatekeepers in large organizations. Those gatekeepers can only test one thing at a time, which increases the time between writing code and testing it. The problem compounds when some new feature introduces a new dependency to the test environment. These delays pile up on top of each other. By the time code gets back to a developer, they’ve forgotten most of what they wrote, and the cost for putting that code back in its proper context is high. These costs go straight to the bottom line of the company, resulting in a longer time to develop new features and respond to shifting environments.

Deployment Planning
-------------------

Once again, this is something that immature teams rarely do. The development and project management teams will regularly toss new requirements over the wall to operations staff. They won’t discuss the feasibility or efficiency of architectural decisions. Decision-makers finalize decisions before consulting all the team’s technical experts on a topic. This means that it’s often difficult to correctly configure production environments for a release. An entirely manual configuration management strategy compounds these challenges.

The slow, painful process for getting a feature to release adds another layer of challenge to operational work. Because testing and user acceptance and compliance are manual and take unknown amounts of time, operations staff don’t know which features will be in a release. This makes it difficult to prepare an environment for a feature. It’s no good updating software packages or library versions if the new code to take advantage of those changes isn’t in the release.

All of this adds up to stressful deployment planning. A hallmark of this kind of disjointed planning is operations staff regularly needing to play the hero. Immature DevOps teams regularly see their operations staff working long hours or needing to manually prepare releases for hours ahead of time.

  

**Mature Teams**

Release Management
------------------

### How Do Mature Teams Do Release Management?

Mature teams approach release management from an entirely different perspective. For starters, their focus with release management is just as much on how to support new features after they’re released as in shepherding that code before it goes to customers. They have simple, straightforward processes for gathering user feedback and listening to customers about how their needs are changing.

Instead of large, unwieldy manual gates, mature DevOps teams seek to involve stakeholders earlier in the process. Stakeholders test and evaluate code soon after developers write it. This means that developers can create automated tests which help ensure that the code does what it’s designed to do as they work on it. Since that manual feedback comes earlier in the process, there is less confusion around the status of a project. Developers spend less time [context switching](https://simpleprogrammer.com/context-switching/) between different features because stakeholder feedback comes quickly and clearly. Because stakeholders are able to confirm the quality of code during the development process, quality gates are now automatic.

### Mature Teams Automate As Much As They Can

Operations staff are able to configure [CI/CD](https://www.redhat.com/en/topics/devops/what-is-ci-cd) systems to automatically move code quickly from finished to general availability. Developers don’t have to suffer through round after round of feedback before their code ships. What’s more, if a developer does launch code and learn only after shipping that there’s a flaw customers discovered, there are mechanisms in place to deal with that. Feedback is quickly gathered, and the developer can work on the code—while it’s fresh on their mind—to correct the mistake.

While CI/CD is beneficial for deployment, mature DevOps teams move past just building code and running automated tests. They automate everything, including the provisioning of their environments. This is usually done by some sort of solution in which infrastructure is designed through a [coding interface](https://docs.microsoft.com/en-us/azure/devops/learn/what-is-infrastructure-as-code). These tools ensure that infrastructure is correctly configured, no matter the environment. So if, for example, a new message queue is needed in four environments, it’s only a couple of lines of code away.

These teams also configure effective metric measurement and notification systems. Everything happens automatically, meaning that operations staff are free to work on bigger problems.

Test Environment Management
---------------------------

### How Do Mature Teams Manage Test Environment Management?

Mature teams, like with release management, automate as much as they can. For test environments, this means automating just about everything. Mature DevOps organizations leverage their CI/CD system to make setting up new testing environments a simple process. The same goes for tearing them down. This means that test environments are cheap. If a gatekeeper has the bandwidth to look at four different features in one day, operations can provide them four testing environments, one for each feature. The whole thing might take a few minutes.

Instead of using outdated databases, or leaving in rows which contain sensitive information, a mature DevOps team uses an automated script to create new testing databases. This script anonymizes data before it moves to the pre-production server, so sensitive information doesn’t leak. Much like test environments, these databases are trivial to stand up and tear down. Operations teams easily build new test environments, including a completely separate database, for every feature.

Deployment Planning
-------------------

A mature DevOps team turns that kind of thinking on its head. Their attitude is that operations staff should not need to be manually involved in a release. Instead, continuous delivery systems mean that as developers finish features, they’re deployed automatically. Planning phases for new features involve operations experts, so they’re never surprised by what architecture they need for a feature.

As features and releases become smaller, releases become more frequent. This is a boon to deployment planning, too. Because the releases are small and regular, there’s no need to do the hard work of a big, last-second integration of disparate features. The quick-release cadence also means that features themselves can be smaller. Project management doesn’t need to shove a dozen features into the same release when releases happen every week instead of every quarter.

Finally, moving more testing into automated tests means that the team ships fewer bugs to customers. This decreases long-term support costs and makes the lives of both developers and operations staff less stressful as a result.

  

  

  

  

  

  

  

  



