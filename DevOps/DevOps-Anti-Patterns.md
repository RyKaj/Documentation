DevOps :  Anti-Patterns  

###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [DevOps](https://github.com/RyKaj/Documentation/tree/master/DevOps/README.md) |
------------

DevOps :  Anti-Patterns
=============================================

Anti-Patterns: Department Structures

Dev and Ops Silos (Anti-Type A)
-------------------------------

This is the classic ‘throw it over the wall’ split between Dev and Ops. It means that story points can be claimed early (DONE means ‘feature-complete’, but not working in Production), and software operability suffers because Devs do not have enough context for operational features and Ops folks do not have time or inclination to engage Devs in order to fix the problems before the software goes live.

We likely all know this topology is bad, but I think there are actually worse topologies; at least with Anti-Type A (Dev and Ops Silos), we know there is a problem.

<img src="./attachments/451824402.png" alt=""></kbd>

DevOps Team Silo (Anti-Type B)
------------------------------

The DevOps Team Silo (Anti-Type B) typically results from a manager or exec deciding that they “need a bit of this DevOps thing” and starting a ‘DevOps team’ (probably full of people known as ‘a DevOp‘). The members of the DevOps team quickly form another silo, keeping Dev and Ops further apart than ever as they defend their corner, skills, and toolset from the ‘clueless Devs’ and ‘dinosaur Ops’ people.

The only situation where a separate DevOps silo really makes sense is when the team is temporary, lasting less than (say) 12 or 18 months, with the express purpose of bringing Dev and Ops closer together, and with a clear mandate to make the DevOps team superfluous after that time; this becomes what I have called a [Type 5 DevOps Topology](https://web.devopstopologies.com/#type-five).

<img src="./attachments/451824402.png" alt=""></kbd>

Dev Don't Need Ops (Anti-Type C)
--------------------------------

This topology is borne of a combination of naivety and arrogance from developers and development managers, particularly when starting on new projects or systems. Assuming that Ops is now a thing of the past (“we have the Cloud now, right?”), the developers wildly underestimate the complexity and importance of operational skills and activities, and believe that they can do without them, or just cover them in spare hours.

Such an Anti-Type C DevOps topology will probably end up needing either a [Type 3 (Ops as IaaS)](https://web.devopstopologies.com/#type-three) or a [Type 4 (DevOps-as-a-Service)](https://web.devopstopologies.com/#type-four) topology when their software becomes more involved and operational activities start to swamp ‘development’ (aka coding) time. If only such teams recognised the importance of Operations as a discipline as important and valuable as software development, they would be able to avoid much pain and unnecessary (and quite basic) operational mistakes.

<img src="./attachments/451824402.png" alt=""></kbd>

DevOps as Tools Team (Anti-Type D)
----------------------------------

In order to "become DevOps" without losing current dev teams velocity (read delivery of functional stories), a DevOps team is set up to work on the tooling required for deployment pipelines, configuration management, environment management, etc. Meanwhile Ops folks continue to work in isolation and Dev teams continue to throw them applications "over the wall".

Although the outcomes of this dedicated team can be beneficial in terms of an improved tool chain, its impact is limited. The fundamental problem of lack of early Ops involvement and collaboration in the application development lifecycle remains unchanged.

<img src="./attachments/451824402.png" alt=""></kbd>

Rebranded SysAdmin (Anti-Type E)
--------------------------------

This anti-type is typical in organizations with low engineering maturity. They want to improve their practices and reduce costs, yet they fail to see IT as a core driver of the business. Because industry successes with DevOps are now evident, they want to "do DevOps" as well. Unfortunately, instead of reflecting on the gaps in the current structure and relationships, they take the elusive path of hiring "DevOps engineers" for their Ops team(s).

DevOps becomes just a rebranding of the role previously known as SysAdmin, with no real cultural/organizational change taking place. This anti-type is becoming more and more widespread as unscrupulous recruiters jump on the bandwagon searching for candidates with automation and tooling skills. Unfortunately, it's the human communication skills that can make DevOps thrive in an organization.

<img src="./attachments/451824402.png" alt=""></kbd>

Ops Embedded in Dev Team (Anti-Type F)
--------------------------------------

The organization does not want to keep a separate Ops team, so development teams take responsibility for infrastructure, managing environments, monitoring, etc. However, doing so in a project or product-driven way means those items are subject to resource constraints and re-prioritizations which lead to subpar approaches and half-baked solutions.

In this anti-type the organization shows lack of appreciation for the importance and skills required for effective IT operations. In particular, the value of Ops is diminished because it's treated as an annoyance for Devs (as Ops is managed by a single Dev team manager with other priorities).

_Thanks to [Scott Prugh](https://twitter.com/ScottPrugh) for suggesting clarifications on how Anti-Type F differs from Type 2._

<img src="./attachments/451824402.png" alt=""></kbd>

Dev and DBA Silos (Anti-Type G)
-------------------------------

This is a form of [Anti-Type A (Dev and Ops Silos)](https://web.devopstopologies.com/#anti-type-a) which is prominent in medium-to-large companies where multiple legacy systems depend on the same core set of data. Because these databases are so vital for the business, a dedicated DBA team, often under the Ops umbrella, is responsible for their maintenance, performance tuning and disaster recovery. That is understandable. The problem is when this team becomes a gate keeper for any and every database change, effectively becoming an obstacle to small and frequent deployments (a core tenet of DevOps and Continuous Delivery).

Furthermore, just like Ops in [Anti-Type A](https://web.devopstopologies.com/#anti-type-a), the DBA team is not involved early in the application development, thus data problems (migrations, performance, etc) are found late in the delivery cycle. Coupled with the overload of supporting multiple applications databases, the end result is constant firefighting and mounting pressure to deliver.

<img src="./attachments/451824402.png" alt=""></kbd>

Anti-Pattern Philosophy

DevOps is a process
-------------------

Not exactly. It’s a philosophy. It’s a way of thinking. DevOps is supported by process and tools. DevOps according to [Gene Kim](https://twitter.com/RealGeneKim), is underpinned by 3 core principles known as the “Three Ways”.

The First Way emphasizes the performance of the entire system – the value stream. The Second Way is about shorting and amplifying feedback loops. The Third Way is about creating a culture that fosters continual learning and understanding.

Agile equals DevOps?
--------------------

If you’re asking this question, then you’re probably running some agile process. That’s good. You’ve got a software development process that compliments DevOps, but Agile doesn’t mean you’ve adopted DevOps.

DevOps is an agile enabler allowing operations to collaborate supporting a more continuous flow of work into IT Operations and out into production where customers can realize its value.

Rebrand your Ops/Dev/any team as the DevOps
-------------------------------------------

CIO: “I want to embrace DevOps over the coming year.”

MGR: “Already ready done, we changed the department signage this morning. We are so awesome we now have two DevOps teams.”

Yeah great. And I bet you now have lots of “DevOps” engineers walking round too. If you’re lucky they may sit next to each other at lunch.

Start a separate DevOps group
-----------------------------

Go on. I dare you. Done it? Well done. You’ve implemented DevOps. Actually what you just did is create yet another silo. Now you’ve got yourself another team you’ve got to try and integrate. Another team with walls to breakdown. Maybe you could go back and rebrand (see AP: x) and create 3 DevOps teams then you’d be super awesome.

DevOps is not about cherry picking some developers and some IT Operations people and silo’ing them off. You’ve got to embrace and embed.

Collapse the development team into the ops team or vice-versa. You need to fully break down the barriers / walls / guards between the teams and mould them into a single unit with shared goals and responsibilities.

The hostile takeover
--------------------

DevOps. So that’s a word that starts with “Dev”. That means development lead, because development comes first…… Problem?

DevMgr – “Er, we’re now doing DevOps. My guys need to learn the production systems.”

OpsMgr – “Er….ok. So who’s going to be developing the code?”

The word DevOps is clever. It’s a [portmanteau](http://en.wikipedia.org/wiki/Portmanteau). This means the combination of two words, to form a new word, which gives a new meaning. It even delivers some efficiency. It doesn’t mean we took the word operations and replaced it with the word development. So why would you try and adopt DevOps in that manner?

DevOps requires both groups to recognise their key skills. Share what needs to be shared to collaborate. Learn what needs to be learnt to improve. It does not mean retraining. It does not mean cross-skilling (however, this may be a welcome side-effect). It does mean providing feedback and visibility to improve.

DevOps is a buzzword
--------------------

If you think DevOps is a buzzword, then you’ve probably been using “The Cloud” as a misnomer too. DevOps is a word, you got that right. Actually, it’s a [portmanteau](http://portmanteaur.com/) of Development and IT Operations (I’ll collect my gold star from teacher later).

DevOps is more than just a cool buzz word. It’s a state of mind. You must embrace its values, you must help others embrace its values and you must continually improve yourself and help others to improve for it to be successful. Once you throw away the BS and start collaborating you might get people to think your catchy new word “DevOps” might actually be cool.

Sell DevOps as a silver bullet
------------------------------

DevOps is voodoo. You basically get your Development team and your IT Operations team together. They smoke some [peyote](http://en.wikipedia.org/wiki/Peyote) and then sacrifice a chicken. Once you’ve done that your organisation will be revolutionised.

You’ll be able to ship software faster than ever before. Configuration will be self-managing. Your deployment tools will become self-aware. Your development and IT Operations teams will have a new found harmony.

Get this….. DevOps is hard work! For most, it requires Culture Change! That’s one of the hardest things you’ll ever attempt. For seasoned development and IT Operations teams you’re about to try and turn their world up-side-down. Don’t try and do it overnight or you will fail.

DevOps does not equal “Developers managing Production”
------------------------------------------------------

I’ve had a few conversations lately, mainly with smaller start-ups or development houses, who tell me “yes, we work in a DevOps model”. What they really mean is “We pretty much have no Operations capability at all, and we rely on the Developers to build, deploy and manage all of the environments from Development to Test to Production. Mostly by hand. Badly”.

As someone from a predominately Operations background I find this quite frustrating!

Operations is a discipline, with its own patterns & practices, methodologies, models, tools, technology etc. Just because modern cloud hosting makes it easier to deploy servers without having to know one end of a SCSI cable from another doesn’t mean you “know” how to do Operations (just like my knowledge of SQL is enough to find out the information I need to know monitor and manage the environment but a long way from what’s required to develop a complex, high-performing website).

DevOps means Development and Operations working together collaboratively to put the Operations requirements about stability, reliability, performance into the Development practices, whilst at the same time bringing Development in the management of the Production environment (e.g. by putting them on-call, or by leveraging their development skills to help automate key processes).

It doesn’t mean a return to the laissez-faire “anything goes” model where developers have unfettered access to the Production environment 24x7x365 and can change things as and when they like.

Change control was invented for a reason, and whilst change control has becomes its own “cottage industry” involving ever more bureaucratic layers of “management by form filling” the basic discipline remains sound – think about what you want to change, automate it if you can, test it, understand what to do if it screws up (roll back plan), document the change, make sure everyone knows when, where and how you are making the change, and make sure the business owner approves.

When I took over the Operations of a high-volume UK website about 8 years ago I spend the first 3 weekend working fighting fires and troubleshooting Production issues.

My first action after that baptism of fire was to revoke access to production for all developers (over howls of protests). Availability and stability immediately went up. Deafening silence from Development – Invitations to beers from the Business owners.

Next step was to hire a build manager to take over the Build and Deployment automation, and a Release Manager to coordinate with the Business what was going into each release, when etc. End result – 99.98% availability, with more releases, being deployed within business hours without impacting the users, and a lower TCO. The Business was much happier, and so was the Development Manager, as he was losing far fewer developer-hours to fire-fighting Production issues, and hence the overall development velocity improved considerably. Win-Win.

Was that a DevOps anti-pattern? Did I create more silos? Probably… but in a fire-fight a battlefield commander doesn’t sit everyone down for a sharing circle on how they are going to address the mutual challenge of killing the other guy before he kills you. Sometimes a command & control model is the right one for the challenge you face (like getting some supressing fire on the target while you radio in for some air support or artillery!).

That said, once we had developed a measure of stability we did move partway to a more DevOps pattern – we had developers on-call 24×7 as 3rd line support, we virtualised our environment(s) and gave Developers more control over them, and we increased our use of automation.  
Organisationally we remained siloed however – we were incentivised in different ways (Operations emphasising availability, Development emphasising feature delivery), we remained in essentially a waterfall delivery model and Ops VS Dev was a constant struggle for manpower & resources. All the usual problems that the DevOps movement is trying to address.

In summary, what I am trying to get at is please don’t devalue the “DevOps” concept by saying you do DevOps when you don’t.

Unless you currently do both Development AND Operations separately, and do them well, AND you’re now trying to synthesise a better, more agile, more cloud-oriented way of working that takes the best part of BOTH disciplines… you aren’t doing DevOps!

DevOps is Development-driven release management
-----------------------------------------------

Let me get 2 things clear;

1.  DevOps is not development driven.
2.  DevOps is not IT Operations driven.

If you want a developer-driven environment, fine, go create one. Just don’t call it DevOps. It’s not.

We can’t do DevOps – We’re Unique
---------------------------------

Yes you are, you little beauty you! But you’re not special enough that you can’t adopt DevOps. I bet you’re the best developer out there; you code quicker than lighting, and deliver the sort of code that makes grown men cry with joy. No? Okay, so you’re the most awesome Ops Guy on planet. If [Chuck Norris](http://www.chucknorrisfacts.com/) were an IT Operations Engineer he’d be want to be you.

However, you and your organisation don’t have some unique factor that won’t allow you to adopt DevOps. So give it a go!

We can’t do DevOps – We’ve got the wrong people
-----------------------------------------------

Well why did you hire them? That’s right – they’re awesome! If you don’t think that, then you need to take a long hard look at yourself, then go and discover the real hidden talents in your team.

Someone told me recently that they couldn’t do DevOps because “they have the wrong developers or the wrong ops people…”. So they have developers who can’t code? I thought to myself, “my organisation has the wrong developers, people who can’t code, they run HR and Marketing!”

DevOps fosters a collaborative working relationship between Development and IT Operations. This collaboration can extend right through the organisation further enhancing working relationships between teams.

You don’t have the wrong people. You have the wrong thought process. Deal with it.

Collaboration when things go pear-shaped
----------------------------------------

Ok genius. You messed up. So what? We all do it. But now you want your IT Operations guys out of bed at 2am to clean-up something they know nothing about. They are IT Operations engineers – not the “fixer” like [Michael Clayton](http://www.imdb.com/title/tt0465538/). Waiting until an error occurs during a deployment for Development and IT Operations to collaborate sucks.

It’s too late for this problem….. but maybe not for the next. You have your Development team and your IT Operations team talking (or swearing at 2am) with each other, but at least they are talking. Keep the dialogue going. Get a retrospective review of what happened and how you can fix it going forward. If you have encountered this situation, then try and keep the dialogue going with between your teams. Open the communication channels with Development and IT Operations early. There’s hope for you yet!

Avoiding Tool Integration Like the Plague
-----------------------------------------

There is a prevalent notion, especially in larger enterprises, that integrating disparate tools is extremely expensive. That you’ll be locked for eternity maintaining glue code with high technical debt. That might have been true in the 2000s, but surely not today.

As long as you are integrating tools with clear and standard APIs, the orchestration code can be minimal and understandable by anyone familiar with API development (which all developers should be in 2017!).

Tooling integration cost is not zero, but it’s negligible when compared to the potential cost of not integrating. One-stop solutions might embed erroneous concepts. Any tool might. The problem is that the former will propagate them across the entire lifecycle.

<kbd>![Image title](https://dzone.com/storage/temp/4177775-screen-shot-2017-01-30-at-25229-pm.png) </kbd>

Instead, single-purpose, focused tools with a well-de ned API help reduce the blast radius of bad practices. And you can swap them easily when they don’t match your requirements anymore. A flexible toolchain standardizes practices, not tools. It supports certain capabilities, which are easy to locate and expand on, replacing particular components (tools) when required.

<kbd>![Image title](https://dzone.com/storage/temp/4177777-screen-shot-2017-01-30-at-25340-pm.png)  </kbd>

Another gain with individual tools: you can actually expect an answer from the vendor when you ask for a feature since they have a reduced feature set and faster change cycles. A vendor of a one-stop solution has a lot more requests in its backlog. Chances are, if you’re not a major client, your requests will get buried for months or even years.

Error Handling and Logging Behind Closed Doors
----------------------------------------------

Another hidden time-consuming anti-pattern in one-stop solutions derives from generic error messages or inaccessible logging. This tends to be especially painful with SaaS solutions.

Unfortunately, our industry is still plagued with the “abstraction everywhere bias”: a tendency to favor generic error messages (“VM could not be started” or “Deployment failed”) instead of spelling out what was the expected input or output and the difference to the actual result. Now add to the mix inaccessible logs for those failed operations, a common situation in one-stop solutions that provide only UI access to certain features or only let you access logs via queries.

The problem is these tools assume they have all the use cases and all the failure scenarios covered. That is untrue for any tool, or any software in fact. We will always need access to information to troubleshoot issues. The more information we have, the more likely we can correlate events and the causes.

<kbd>![Image title](https://dzone.com/storage/temp/4177783-screen-shot-2017-01-30-at-25650-pm.png)</kbd>

Think of all the time spent deciphering error messages, trying to guess what went wrong, or waiting for a vendor’s support to get back to you (if you hit the jackpot with a technical issue deep in the tool’s gut, good luck waiting for the support-to-engineering return trip time). That time alone is an order of magnitude higher than any individual tool integration time you’d have spent.

Environment-Driven Pipelines
----------------------------

This one is pretty self-explanatory. Tools that assume your pipeline is nothing but a sequence of environments where you deploy your system and run some tests.

A pipeline stage represents an activity in the delivery chain. It might require:

*   One environment: Typical for acceptance tests.
*   Zero environments: Typical for manual checks/analysis or approval requests.
*   Multiple environments: Typical for performance tests.

Thus pipeline stages should not be tightly coupled to environments. Assuming only the first option above leads to pipelines that contemplate only automatable activities, hiding other (often non-technical) activities that are part of delivery as well. In turn, this leads to lack of visibility on (real) bottlenecks and local optimization (technical steps) instead of global (cycle time).

<kbd>![Image title](https://dzone.com/storage/temp/4177787-screen-shot-2017-01-30-at-30135-pm.png)</kbd>

Flexing Is for Fitness, Not for Principles
------------------------------------------

Adopting core [Continuous Delivery principles](https://continuousdelivery.com/principles/) is hard and often requires mental and cultural shifts. Without them, the underlying practices become ceremonies, instead of actual improvements in delivery. Flexibility is fine for the gym, but not for core principles required for a (often radical) new way of working.

If the tools supporting the practices do not align with the principles, they end up unintentionally undermining the whole endeavor. In contrast, working with a set of single-purpose tools helps identify and address erroneous assumptions by any one tool.

Below are a couple of examples of misalignment between implementation and principles that we’ve seen in some out-of-the-box integrated tools.

Status: ???
-----------

A pipeline status should be binary. Red or green. Not orange. Not gray. Not blue. Recurring ambiguities in status inevitably lead to disengagement by development teams. This is the

CD equivalent to warnings at compilation time. If the first warnings are ignored by developer A, then developer B and developer C will ignore them, as well. Soon, everyone just assumes having 372 warnings is OK.

<kbd>![Image title](https://dzone.com/storage/temp/4177796-screen-shot-2017-01-30-at-30530-pm.png)</kbd>

Having an uncontested pipeline status is a prerequisite to the Continuous Delivery principle of “stopping the line” when a pipeline fails (then either x it quickly or revert the changes that broke it). Interestingly, this is also a prerequisite to getting rid of those nasty compilation warnings (try making the pipeline go red if there are compilation warnings).

Terminology Fail
----------------

Another plague in our industry is the proliferation of terminology. We have enough confusion as it is and quite frankly one-stop tool vendors are not helping. They, above all, should strive to align on common terminology, as they are informing their clients on the entire lifecycle. So, it better be correct. This is clearly complicated as those vendors have many different teams working on the integrated tools. But it is needed.

One puzzling example we have come across of terminology failures is calling a pipeline trigger from a successful build a “continuous deployment.”

<kbd>![Image title](https://dzone.com/storage/temp/4177799-screen-shot-2017-01-30-at-30640-pm.png)</kbd>

Another example are “release definitions” instead of “pipeline definitions” (the image above is a release definition configuration). Legacy terminology leads to legacy behaviors, thinking of releases and work batches instead of pipelines and frequent delivery of small, low-risk changes in production.

This might seem like just nitpicking, but the accumulation of all these misunderstandings leads to unknowingly misinformed organizations and teams.

Configurable Management
-----------------------

### Configurable Third-Party Software

Procuring software that cannot be externally configured. Software without an API or commandline interface that forces teams to use the GUI only

### Configuration Catalog  

 Configuration options are not documented. The catalog of applications and other assets is “tribal knowledge”.

### Mailline

Multiple branches per project

### Merge Daily

Merging every iternation once a week or less often than once a day

### Protected Configuration

Open text passwords and/or single machine or shared

### Repository

Some files are checked in, others, such as environment configuration or data changes, are not. Binaries – that can be recreated through the build and deployment process – are checked in.

### Short-Lived Branches

 Branches that last more than an iteration. Branches by product feature that live past a release.

### Single Command Environment

Forcing the developer to define and configure environment variables. Making the developer install numerous tools in order for the build/deployment to work.

### Single Path to Production

Parts of system are not versioned. Inability to get back to a previously configured software system

Configurable Integration
------------------------

### Build Threshold

Manual code reviews. Learning of code quality issues later in the development cycle.

### Commit Often

Source files are committed less frequently than daily due to the number of changes from the developer.

### Continuous Feedback

Notifications are not sent; notifications are ignored; CI system spams everyone with information they cannot use.

### Continuous Integration

Scheduled builds, nightly builds, building periodically, building exclusively on developer’s machines, not building at all.

### Stop the Line

Builds stay broken for long periods of time, thus preventing developers from checking out functioning code.

### Independent Build

Automated build relies on IDE settings. Builds are unable to be run from the command line.




