Information Technology : Infrastructure as Code (IaC)  

###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [DevOps](https://github.com/RyKaj/Documentation/tree/master/DevOps/README.md) |
------------

Information Technology : Infrastructure as Code (IaC)
=====================================================

Created by Ryan Kajiura, last modified on Apr 07, 2020



Infrastructure as code likewise alluded to as IaC, is a kind of IT arrangement wherein designers or tasks groups naturally oversee and arrangement the innovation stack for an application through programming, instead of utilizing a manual procedure to arrange discrete equipment tools and working system. Infrastructure as code is once in a while referred to as a programmable or programming characterized framework.

The idea of infrastructure as code is like programming contents, which are utilized to robotize IT forms. In any case, contents are basically used to mechanize a progression of static advances that must be rehashed various occasions over numerous servers. Infrastructure as code utilizes more elevated level or illustrative language to code progressively flexible and versatile provisioning and organization forms. For instance, infrastructure-as-code capacities included with Ansible, an IT the board and set up the instrument, can introduce MySQL server, check that MySQL is running appropriately, make a client record and secret word, set up another database, and expel unneeded databases.

The code-based framework automation process intently takes after programming configuration rehearses in which engineers cautiously control code adaptations, test emphasis, and limit organization until the product is demonstrated and endorsed for creation.

Infrastructure as Code (IaC) is the management of infrastructure (networks, virtual machines, load balancers, and connection topology) in a descriptive model, using the same versioning as DevOps team uses for source code. Like the principle that the same source code generates the same binary, an IaC model generates the same environment every time it is applied. IaC is a key DevOps practice and is used in conjunction with [continuous delivery](https://docs.microsoft.com/en-us/azure/devops/learn/what-is-continuous-delivery).

Infrastructure as Code evolved to solve the problem of _environment drift_ in the release pipeline. Without IaC, teams must maintain the settings of individual deployment environments. Over time, each environment becomes a _snowflake_, that is, a unique configuration that cannot be reproduced automatically. Inconsistency among environments leads to issues during deployments. With snowflakes, administration and maintenance of infrastructure involves manual processes which were hard to track and contributed to errors.

_Idempotence_ is a principle of Infrastructure as Code. Idempotence is the property that a deployment command always sets the target environment into the same configuration, regardless of the environment’s starting state. Idempotency is achieved by either automatically configuring an existing target or by discarding the existing target and recreating a fresh environment.

Accordingly, with IaC, teams make changes to the environment description and version the configuration model, which is typically in well-documented code formats such as JSON. The release pipeline executes the model to configure target environments. If the team needs to make changes, they edit the source, not the target.

Infrastructure as Code enables DevOps teams to test applications in production-like environments early in the development cycle. These teams expect to provision multiple test environments reliably and on demand. Infrastructure represented as code can also be validated and tested to prevent common deployment issues. At the same time, the cloud dynamically provisions and tears down environments based on IaC definitions.

Teams who implement IaC can deliver stable environments rapidly and at scale. Teams avoid manual configuration of environments and enforce consistency by representing the desired state of their environments via code. Infrastructure deployments with IaC are repeatable and prevent runtime issues caused by configuration drift or missing dependencies. DevOps teams can work together with a unified set of practices and tools to deliver applications and their supporting infrastructure rapidly, reliably, and at scale.

  

**Advantages of Infrastructure as code**

Development engineers can utilize code to the arrangement and send servers and applications, instead of depending on framework chairmen in a DevOps domain. An engineer may compose an Infrastructure as-code procedure to the arrangement and send another application for quality confirmation or trial organization before tasks take over for live sending underway.

![](https://miro.medium.com/max/1024/1*kfH952dhVkjGFFioEX6-DQ.jpeg)

With the Infrastructure as code, it can experience a similar rendition control, robotized testing, and different strides of a persistent joining and consistent conveyance (CI/CD) pipeline that designers use for application code. An association may decide to join the Infrastructure as code with compartments, which dynamic the application from the foundation at the working framework level. Since the OS and equipment framework is provisioned consequently and the application is epitomized on it, these advances demonstrate correlative for differing sending targets, for example, test, organizing and creation.

In spite of its advantages, the foundation as code presents potential disservices. It requires extra instruments, for example, design the board framework, that could present expectations to absorb information and space for blunder. Any blunders can multiply rapidly through servers, so it is basic to screen adaptation control and perform complete prerelease testing.

On the off chance that heads change server designs outside of the set foundation as-code layout, there is potential for setup float. It’s essential to completely coordinate foundation as code into frameworks organization, IT activities and DevOps rehearses with well-archived approaches and techniques.

Approaches and techniques
-------------------------

Infrastructure as-code tool can be revelatory and basic.

An explanatory programming approach diagrams the ideal, planned condition of the foundation, yet doesn’t expressly list the means to arrive at that state. SQL is a normally known revelatory programming language. AWS CloudFormation formats, among others, are written in the decisive style of foundation as code.

Interestingly, a basic methodology characterizes directions that empower the framework to arrive at the ideal state. Item arranged dialects, for example, C++ and Java, can be utilized for basic programming. A device, for example, Chef can be utilized in a revelatory way, yet additionally vitally varying.

In the two methodologies, the framework as code is arranged on a layout, where the client determines the assets required for every server in the foundation. The format is utilized to either check that a framework is appropriately arranged or placed it in the proper arrangement. Formats can be built like a lot of layers of assets, for example, in AWS CloudFormation, which makes a stack.

**Training**

eBook

  

[![](rest/documentConversion/latest/conversion/thumbnail/469106907/1)](/download/attachments/451822353/ebook%20-%20Enterprise%20Cloud%20Strategy%20Infrastructure%20As%20A%20Service.pdf?version=1&modificationDate=1586257964930&api=v2)

  

URLs

  

  

  

IT Documentation on IaC

  

  

  

<

Up to Parent Page

\>

* * *

Last Modified By

[Eddyson Peny](    /display/~eddysonp
)

Last Update

Sep 17, 2019 14:57

Contributors

*   [Eddyson Peny](/display/~eddysonp) 19 (246 days ago)

Reviewed / Approved By

jQuery(document).ready(function() { jQuery("#paAcknowledgeToggle").click(function() { var current = jQuery(".ackTable").attr("class"); var currentsplit = new Array(); currentsplit = current.split(" "); for(i=0; i<currentsplit.length; i++) { if(currentsplit\[i\] == "visible") { jQuery(".ackTable").addClass("invisible"); jQuery(".ackTable").removeClass("visible"); jQuery("#paAcknowledgeToggle").attr("value","Show Acknowledgers"); } if(currentsplit\[i\] == "invisible") { jQuery(".ackTable").addClass("visible"); jQuery(".ackTable").removeClass("invisible"); jQuery("#paAcknowledgeToggle").attr("value","Hide Acknowledgers"); } } }); }); .patable { border: solid; background: #ffffff; font-size:8pt; } p.patable { padding-left:75px; padding-right:0.5em; margin:2px; border:none; } p.patablehr { font-size:10pt; background: #dddddd; font-weight:bold; padding-left:64px; padding-top:4px; padding-bottom:4px; margin:2px; vertical-align:middle; } p.patableac { padding-left:85px; } p.patitle { font-size:12pt; background: #cccccc; font-weight:bold; padding-left:64px; padding-top:4px; padding-bottom:4px; margin:2px; vertical-align:middle; } .visible { display: block; } .invisible { display: none; } div#statusnote{ font-style: italic; text-align: right; font-size: x-small; } div#pageapproval{ overflow: auto; border-width: 1px; } #paAcknowledgeToggle { font-size: 11px; }

 ![](download/resources/net.customware.confluence.plugin.pageapproval:pageapproval/img/pagenotapproved.png) Not approved 

User

Approval Date

Role

Alexis van der Biest

![](download/resources/net.customware.confluence.plugin.pageapproval:pageapproval/img/forbidden.gif)

Kelvin Loke

Mon Sep 23 08:02:20 BST 2019

Project Code Name

**Vision**

Ticket

[SAS-301](https://support.pinnaclesports.com/browse/SAS-301?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

  

* * *

Project Vision:  
Representation of the SME collective working towards the next generation pinnacle DevSecOps . A group of integrated system design to work side by side with our Ops teams, offloading some of the monitoring, troubleshooting, configurations and deployments, improving team performance while minimizing human errors.

  

Vision also Focus on the standardization of IAC in Pinnacle environment. This includes but its not limited to deployment methods, documentation and coded behaviors version control.

.rwui\_text\_box.rwui\_id\_4780f6ae-de77-4879-a2a5-7fed0ec180c2 {background-color: #F8F8E3;}.rwui\_text\_box.rwui\_id\_4780f6ae-de77-4879-a2a5-7fed0ec180c2 \* {color: #6A4920;}.rwui\_text\_box.rwui\_id\_4780f6ae-de77-4879-a2a5-7fed0ec180c2 span.rwui\_icon {color: #6A4920;}

**Objectives:**

*   What is IAC?
*   Company benefit
*   Project Phases (2019 and 2020 Road-maps)
*   Proposed technology stack and justification
*   Wanted final state
*   Future Improvements on Technology stack

**MAIN CONTENT**

What si IAC?

**Infrastructure as code** is the process of managing and provisioning resourced through machine-readable definition files, rather than physical hardware configuration or interactive configuration tools.

  

There are 2 types of main approaches:  
•Declarative (functional): defines the desired state and the system executes what needs to happen to achieve that desired state.  
•Imperative (procedural): defines specific commands that need to be executed in the appropriate order to end with the desired conclusion.

  

Environment aware level: determines the correct desired state before the system executes what needs to happen automatically.

Company Benefits

  

*   **Speed and simplicity:** Spinning up new VMs, environments and server update cycles can be done within an significant shorter ETA.
*   **Consistency:** Guarantee of consistency among all cluster members when promoting new resources. With Code standardizing we removing the potential human error factor coming from server builds SOPs.
*   **Minimization of risk:** Removal of lead engineers dependencies and lack of documentation. version-controlled code to keep track of new infra configuration changes.
*   **Increased efficiency:** RSS can be easily deployed automatically. Capability for continuous Integration and deployment techniques while minimizing the introduction of human errors, fast and easy spinning down of environments when they’re not in use.
*   **Cost savings:** T1 & T2 engineers will spend less time performing manual work, and more time executing higher-value tasks.

.rwui\_text\_box.rwui\_id\_33f9999f-8588-4098-b515-c4769f23c0b4 {background-color: #F8F8E3;}.rwui\_text\_box.rwui\_id\_33f9999f-8588-4098-b515-c4769f23c0b4 \* {color: #6A4920;}.rwui\_text\_box.rwui\_id\_33f9999f-8588-4098-b515-c4769f23c0b4 span.rwui\_icon {color: #6A4920;}

Project Phases

*   **Phase 1: Methodology and POC**
    *   **Core Documentations**

Task

Card

ETA

Status

Comment

Define the wanted state

Define base technology stack

[SAS-304](https://support.pinnaclesports.com/browse/SAS-304?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

  

Completed

  

Target Scope Environments Data collection West

[SAS-305](https://support.pinnaclesports.com/browse/SAS-305?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

  

Completed

Provided by Judd

Define the Change management procedure

[SAS-306](https://support.pinnaclesports.com/browse/SAS-306?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

  

Completed

Approved by Kelvin

Change Management using dedicated Kanban Board

N/A, To be Agreed On

  

  

  

Version control trough source control + editor selection

[SAS-307](https://support.pinnaclesports.com/browse/SAS-307?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

5/10/2019

In Progress

  

Vision Change management automation

[SAS-317](https://support.pinnaclesports.com/browse/SAS-317?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

11/10/2019

In Progress

  

*   *   **Vision CI Environment build-out**

Task

Card

ETA

Status

Comment

Build:

CI Ansible

CI networking (IP Block and LB functionality)

CI Zabbix

[SAS-308](https://support.pinnaclesports.com/browse/SAS-308?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

  

TBD

  

In Progress

  

Ansible CI is now deployed.

Zabbix instance deployed, still in progress of fine tuning triggers, Pending Judd

  

CI IOC Console and/or Dashboard Creation

[SAS-311](https://support.pinnaclesports.com/browse/SAS-311?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

TBD

In Progress

Pending on assistance confirmation from East for code modification in order to set ETA.

CI cluster stress test tool

[SAS-314](https://support.pinnaclesports.com/browse/SAS-314?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

TBD

Open

Pending Judd, in order to set ETA

*   *   **Vision Behavioral Coding and base line approval**

Task

Card

ETA

Status

Comment

POC Ansible with supporting technologies, including Octopus and Jenkins

N/A

  

  

  

Vision Logging, notification schemes (Email and IM)

[SAS-313](https://support.pinnaclesports.com/browse/SAS-313?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

25/10/2019

Opens

Pending brainstorming session to decide how to incorporation slack notifications and Jira ticket creation/update to behaviors codes

Automatic Linux VM template updates

[SAS-309](https://support.pinnaclesports.com/browse/SAS-309?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

20/9/2019

In Progress

Behavior ready, pending submit for approval

Automatic deployment of Arcadia products

[SAS-310](https://support.pinnaclesports.com/browse/SAS-310?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

26/9/2019

in Progress

Algorithm Ready, Pending code testing and submission for approval

POC Full IAC functionalities on Arcadia CI

[SAS-312](https://support.pinnaclesports.com/browse/SAS-312?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

25/10/2019

Open

Pending on Haywire on premise migration and Automatic deployment behavior approval.

Haywire Post Deployment Test Tool

[SAS-331](https://support.pinnaclesports.com/browse/SAS-331?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

TBD

On Hold

Pending Judd, in order to set ETA

  

*   *   *   *   *   *   **Phase 2: Production**
                        *   **Production IOC Console integration**
                        *   **On Demand wanted state changes From IOC console**
                        *   **Automatic security patch based on update cycle  
                            **
                        *   **Fine-tune Zabbix detection**

Technology Stack

![](attachments/451818195/451820492.png)

Wanted State

Environment aware IAC:

*   *   *   *   *   *   An orchestrator periodically review all cluster on all environments and own the execution of playbooks.
                    *   Orchestrator will automatically increase and decrease cluster size based on ideal or on demand wanted state (defined or trough AI).
                    *   Orchestrator execute all basic troubleshooting tasks, isolate server and escalate to IOC if cant solve.
                    *   Orchestrator perform periodical windows update cycles on all MS and Linux clusters as per the security policies, transparent to business. T2 continues to lead standalone and critical servers.
                    *   IAC integrated in the development cycle will perform releases and all post deployment validations.
                    *   IAC to communicate with T1 and T2 on every infra change performed.

Future Possibilities and Technology stack expansion

**Future possibilities for the road map**
-----------------------------------------

With IAC fully in function T2 Teams can focus on automate the rest of all repetitive tasks, Code, technology in use and deployment method

  

**Example of manual tasks that can be automated:**

*   *   *   *   *   *   Network fail-over tests
                    *   Services fail-over tests
                    *   Cloud/Hybrid deployments
                    *   Releases
                    *   Systems accounts reviews
                    *   service restarts
                    *   clear cache
                    *   etc

  

**Technology Stack expansions**
-------------------------------

*   *   *   *   *   *   kubernetes
                    *   docker

**References**

  

* * *

  

Revisions

.aui td { white-space:nowrap; }

Version

Date

Comment

**[Current Version](/display/ITI/viewpage.action?pageId=451818195) (v. 19)**

**Sep 17, 2019 14:57**

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 18](/display/ITI/viewpage.action?pageId=451826466)

Sep 17, 2019 14:56

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 17](/display/ITI/viewpage.action?pageId=451826465)

Sep 17, 2019 14:53

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 16](/display/ITI/viewpage.action?pageId=451826464)

Sep 17, 2019 14:46

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 15](/display/ITI/viewpage.action?pageId=451826462)

Sep 17, 2019 10:21

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 14](/display/ITI/viewpage.action?pageId=451826337)

Sep 13, 2019 16:31

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 13](/display/ITI/viewpage.action?pageId=451825893)

Sep 13, 2019 16:31

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 12](/display/ITI/viewpage.action?pageId=451825892)

Sep 13, 2019 16:29

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 11](/display/ITI/viewpage.action?pageId=451825890)

Sep 13, 2019 15:33

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 10](/display/ITI/viewpage.action?pageId=451825871)

Sep 13, 2019 12:57

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 9](/display/ITI/viewpage.action?pageId=451825828)

Sep 06, 2019 10:57

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 8](/display/ITI/viewpage.action?pageId=451824332)

Aug 22, 2019 17:02

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 7](/display/ITI/viewpage.action?pageId=451821625)

Aug 21, 2019 09:57

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 6](/display/ITI/viewpage.action?pageId=451820505)

Aug 21, 2019 09:55

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 5](/display/ITI/viewpage.action?pageId=451820504)

Aug 21, 2019 09:52

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 4](/display/ITI/viewpage.action?pageId=451820500)

Aug 21, 2019 09:50

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 3](/display/ITI/viewpage.action?pageId=451820495)

Aug 12, 2019 15:39

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 2](/display/ITI/viewpage.action?pageId=451818257)

Aug 12, 2019 14:35

**[Eddyson Peny](    /display/~eddysonp
)**

[v. 1](/display/ITI/viewpage.action?pageId=451818228)

Aug 12, 2019 14:30

**[Eddyson Peny](    /display/~eddysonp
)**

  

* * *

  

  

  

  

  

  

  

  

  

  

  

  

  

References

*   [Medium - Implementing devops with terraform and azure pipelines](https://medium.com/ocp-digital-factory/implementing-devops-with-terraform-and-azure-pipelines-9860198bebaa)
*   [Medium nanduribalajee - what is infrastructure as a code](https://medium.com/@nanduribalajee/what-is-infrastructure-as-a-code-ed9cafa87bbc)
*   [MS Doc - What is infrastructure as code](https://docs.microsoft.com/en-us/azure/devops/learn/what-is-infrastructure-as-code)
*     
    

  

  

  

Attachments:
------------

![](images/icons/bullet_blue.gif) [ebook - Enterprise Cloud Strategy Infrastructure As A Service.pdf](attachments/451822353/469106907.pdf) (application/pdf)  



