###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Agile](https://github.com/RyKaj/Documentation/tree/master/Agile/README.md) |
------------



Agile : Estimation 
==================


User Story Points
=================

Agile story points estimation is not like Waterfall mythology just providing numeric value to represent duration in different units (hours, days, weeks, months) to complete the ticket.  Story points estimation is a comparative analysis to roughly estimate the product backlog items with relative sizing. The team members for estimation user stories include: Product Owner, Scrum Master, Developers, Testers, and Stakeholders (UAT sign off).

Traditional software teams give estimates in a time format: days, weeks, months. Many agile teams, however, have transitioned to story points. Story points rate the relative effort of work in a Fibonacci-like format: 0, 0.5, 1, 2, 3, 5, 8, 13, 20, 40, 100. It may sound counter-intuitive, but that abstraction is actually helpful because it pushes the team to make tougher decisions around the difficulty of work.

Fibonacci Sequence
------------------

*½, 1, 3, 5, 8, 13, 20, 40, 100, infinity, ?, coffee break*

A large number of stories can be estimated using this method. The idea here is not to arrive at an accurate estimate of time, the aim is to group the stories into those of similar sizes. In fact, the Fibonacci sequence forces us to take a ball-park approach. Since we are forced to find the nearest grouping, there will be 'winners and losers' and it will balance itself out in the end!

The reasoning behind using points rather than hours, is that it might be difficult to estimate in units of time at speed. Also the speed at which the team can deliver points of effort will depend on the skills of the individuals in the team. Team A might not be as fast as Team B but the relative size of the stories remains the same.

Here are few reasons to use story points:

-   Dates don't account for the non-project related work that inevitably creeps into our days: emails, meetings, and interviews that a team member may be involved in.
-   Dates have an emotional attachment to them. Relative estimation removes the emotional attachment.
-   Each team will estimate work on a slightly different scale, which means their velocity (measured in points) will naturally be different. This, in turn, makes it impossible to play politics using velocity as a weapon.
-   Once you agree on the relative effort of each story point value, you can assign points quickly without much debate. 
-   Story points reward team members for solving problems based on difficulty, not time spent. This keeps team members focused on shipping value, not spending time. 

A few steps to reach the final decision of relative sizing:

Analyze all users stories and identify the base or reference story. It is important for doing relative sizing. This story can be chosen from the current product backlog or the one, that we have done earlier. This story should be chosen as the reference story upon agreement of all members.

Pick another story from the current Product Backlog and the team members are free to discuss any questions or doubts with the Product Owner, while understanding the requirements of the story. Product Owner is responsible for clarifying all their queries and doubts.

Make a list of the things to be taken care while implementing the user story. These can be done by writing notes in the notes section of the tool or by adding bullet points on the story card. This is mostly done by the Scrum Master.

Stated below are few common questions among the participants:

-   Design: What is the prior and mandatory knowledge that we should     have before starting to work on it?
-   Coding: How much coding is required for implementing this user     story. Have we come across any similar user story previously?
-   Unit Testing: Are any mock objects required for doing unit testing     for this user story?
-   Integration Testing: Does this story impact the other     functionalities of the same module and other modules also?
-   Acceptance Testing: What are the points to be taken care to deliver the desired product as desired by the Customers?
-   Expertise: Does any of the participants have done similar story before and is an expert in it?

Do relative sizing for the story selected. If it requires same amount of work and effort, then assign it the same no. of points, as assigned to the reference story. If it requires more effort, assign it some higher value. If it requires less effort, assign it some lower value.

Reach a consensus with all the participants to finalize the relative size for selected user story as per the definition of done.

After relative sizing of all the product backlog items have been done, ensure that if all the user stories with same no. of points assigned to them, require same effort and size to be consistent.

Fibonacci Value Representation
------------------------------

|Fibonacci Value|Meaning / Definition||
|--- |--- |--- |
|0|A zero value indicates that nothing has to be done to finish the story. It's mostly used when a deployment is pending.||
|0.5|It's not zero, but it's a piece of cake that can be made with almost blind eyes.||
|1|It's a small story with very low complexity or effort.||
|2|Doubling up what a 1 means.||
|3|A little bit more than a 2.||
|5|This is an interesting card. There are some brainpower and effort involved to achieve this story. Widely used when the story starts to become serious.||
|8|Much more than a five, but still somehow manageable.||
|13|This number indicates that the user story is at a sharp edge to become too complex to be treated as just one story. Consider story splitting.||
|20|This card mostly just express some desperation of the team member. As a team, you should consider story splitting.||
|40|These cards mostly just express some desperation of the team member. As a team, you should consider story splitting.||
|100|These cards mostly just express some desperation of the team member. As a team, you should consider story splitting.||
|?|The question mark card shows up, that a developer has no clue how to estimate the story.||



Estimation Technique
====================

T-Shirt Sizing Technique
------------------------

-   Just as in the case of T-shirts, we see sizes: XS (Extra Small), S (Small), M (Medium), L (Large), XL (Extra Large). A similar approach is followed here. Items are estimated in T-shirt sizes.  Of course the size of the t-shirts are unisex.
-   This is a perfect technique to give a rough estimation of the large backlog of items.
-   Useful when quick and rough estimation needs to be done. Later these sizes can be converted into no's as per the requirement.
-   A relative size (mostly Medium) is decided after mutual discussion and agreement of the team members or estimators. Then, the no's are assigned to the items according to the relative size that is assigned to Medium size.
-   Disadvantage: What seems L to someone may seem to be XL for someone.
-   All estimators assign their own size to the items. After discussions and resolving the mismatches, a consensus is reached to get the final estimate.

There are many Agile estimating techniques that do not require putting an actual hours estimating on a Story.  A simple method is to separate them into Small, Medium, and Large stories. The team can use this technique to evaluate a large backlog in a short period of time and expand estimates to mimic T-shirt sizes: XS, S, M, L, XL, 2X, 3X, etc.

This estimating style is comparatively easy but does not quantify the work to be completed. Assigning a relative number to your estimates will be useful for computing velocity (how much work a particular team can accomplish in a sprint).

Story point represents the effort required to put that single Story production.

T-Shirt size to Fibonacci
-------------------------

|T-Shirt|Fibonacci|Notes|
|--- |--- |--- |
|S|1||
|M|5||
|L|8||
|XL|∞|Epic/Story needs to be broken down|



Planning Poker
--------------

Planning Poker is an agile estimating and planning technique that is consensus based. To start a poker planning session, the product owner or customer reads an agile user story or describes a feature to the estimators. 

Each estimator is holding a deck of Planning Poker cards with values like 0, 1, 2, 3, 5, 8, 13, 20, 40 and 100, which is the sequence we recommend. The values represent the number of story points, ideal days, or other units in which the team estimates.

The estimators discuss the feature, asking questions of the product owner as needed. When the feature has been fully discussed, each estimator privately selects one card to represent his or her estimate. All cards are then revealed at the same time.

If all estimators selected the same value, that becomes the estimate. If not, the estimators discuss their estimates. The high and low estimators should especially share their reasons. After further discussion, each estimator reselects an estimate card, and all cards are again revealed at the same time.

The poker planning process is repeated until consensus is achieved or until the estimators decide that agile estimating and planning of a particular item needs to be deferred until additional information can be acquired.

Rituals
=======

### How Does Poker Planning Work 

Someone will read the user story.

The estimator discuss the feature and, if needed, ask the product owner questions. When the estimators have finished their discussion, they each select one card privately to represent his or her estimate. The cards are then revealed simultaneously. If all the estimators select the same value, that number becomes the estimate. If their values differ, the estimators discuss their rational. Those who chose the highest or lowest value should share their reasoning with the group before each estimator selects another estimate card, repeating the process. The estimators continue the poker planning process until a consensus on the value is achieved. If they cannot agree, the estimators may opt to defer the agile estimating and planning of a particular item, pending additional information.

### When should Planning Poker (or Scrum Poker) be engaged

Most teams will hold a poker planning session shortly after an initial product backlog is written. These sessions, which can take several days, are used to create initial estimates which are useful in scoping or sizing the project. Because product backlog items -- often in user stories form -- will continue to be added throughout the project, most teams find it helpful to conduct subsequent agile estimating and planning sessions once per iteration.They are typically held a few days before the end of the iteration and immediately following a daily standup because the whole team is still together.

### Tips on Planning Poker in Scrum 

-   **Keep discussions productive:** A two-minute sand timer is a helpful tool used to teach teams how to estimate more rapidly. To use the timer, the timer is set when someone in the group starts a round. When the sand runs out, the next round of planning poker cards is played.

-   **Break out into smaller sessions:** It is ideal, whenever possible, to break a larger group down into smaller sub-teams. This is a good option for running sessions when there are many stories to be estimated; often occurring at the start of a new project.

-   **When to play:**  Typically, estimating teams need to play planning poker on two different occasions: during the first iterations before the project begins and when new stories are identified during an ongoing iteration.

### Reason Why Planning Poker is Great

-   It fosters collaboration by engaging the entire team.
-   It uses consensus estimates rather than single person estimates.
-   Through discussion of each user story, it exposes issues early in the project.

### Who should Vote

Too often, agile teams have everyone vote, regardless of their role in the project. Only those actively involved in the story should vote.

Managers don\'t Vote
--------------------

Managers usually want the work to take less time, so they often vote very low.  However, they have more experience than the average team member. By giving a manager veto power over the team consensus in one specific circumstance, they can then ask the team to consider something that may INCREASE the size.

Never allow managers to give low sizes or persuade the team to decrease its size because their opinion carries too much weight. A manager's views will act as an anchor and drag the size down as they vigorously defend their position

### Process Flow Chart 

![planning poker steps](https://www.softwaretestinghelp.com/wp-content/qa/uploads/2016/05/planning-poker-steps.jpg)

#### Online Planning Poker

-   <https://scrumpoker.online/>
-   <https://www.planitpoker.com/>
-   <https://www.planningpoker.com/>
-   <https://www.pointingpoker.com/>

Estimation
==========

Review Estimations
------------------

The Agile Project Manager will review estimating ideas, including the Keys to Estimation:

-   "A story is a promise to have a conversation" --- it does not specify all details that are needed to implement the story.
-   An estimation is not a promise to complete the work in a certain amount of time.
-   Team members should take no more than two minutes to estimate a story.
-   A story that takes more than one sprint is too long and must be broken up into smaller stories --- you won't know this until the estimation phase.
-   Do estimation in a short meeting (90 min) with engineers*and* story authors in the same room.
-   Avoid rating your abstract story units to calendar time until you can measure from the velocity of a [burndown chart](https://www.agilegovleaders.org/general-resources/burndown-charts/) for at least three sprints.

Concepts about Estimation
=========================

Estimations Theory
------------------

### Estimation is different from Tracking

In Scrum, there is a distinction between estimation and tracking. *Estimation* is typically performed against Primary Backlog Items (PBIs, usually stories), and is used to work out how long portions of the backlog might take to be delivered.  *Tracking* refers to monitoring the progress of a sprint, to be sure that all stories included in the sprint will be delivered.

Tracking is often performed by breaking down stories into tasks, and applying hour estimates to them during sprint planning, then monitoring the remaining time in a burndown during the sprint.

### How is estimation done in traditional development environment

In traditional development environments, estimation is done this way:

1.  A team estimates items in \'man-hours\' -- and these estimates are assumed to be accurate.
2.  The team then calculates the total number of man-hours for the backlog of a project.
3.  The team then divides the total number of man-hours by the number of people on the team, and the man-hours in a week. This becomes the forecast date for the project.

These estimates are often inaccurate because they don\'t consider the following:

-   The natural estimation characteristics of the team -- meaning, over- and under-estimation are not considered
-   Unexpected interruptions during the man-hours allocated to the items
-   The performance of the team members themselves over time

When the estimates become inaccurate, the team then exerts time and effort in trying to \'force\' the estimates to be accurate. This makes the man-hour approach difficult, if not impossible.

### Estimation in Scrum works is all about velocity 

In the Scrum world, teams don\'t try to achieve estimation accuracy. Instead, they aim to achieve \'reliable velocity\'.

*Velocity* is a measure of the number of estimation units that a team tends to complete from sprint to sprint. After their first few sprints, most teams will achieve a reasonably consistent velocity. Armed with velocity and estimates on the PBIs in the backlog, teams can predict more accurately how long portions of the backlog will take to complete.

The key is, the estimation unit doesn\'t matter -- as long as it becomes reasonably predictable from sprint to sprint. For example, teams can use \'ideal hour\' estimates, but it\'s neither necessary or expected that those hours will have any relationship to elapsed time. If a team has a \'man-hour\' capacity of 120h in each sprint but a velocity of 60h, that makes no difference because you can still use the 60h velocity to estimate the number of sprints that portions of the backlog will take to complete --- and therefore, the elapsed time.

Many people then start wondering where \'the other 60 hours\' went, thereby implying that there is something wrong with team productivity. But that\'s usually got nothing to do with it: a team\'s estimates merely represent their view of how hard items will be, taking into consideration the team\'s natural behavior (such as over- and under-estimation), as well as organizational overhead, etc. The velocity is all that matters from a planning perspective. 

Since the units are not related to time, most teams now choose to use story points as their estimation unit. A story point is an arbitrary number that measures the complexity of one story relative to others. In effect, story points clearly break the mental link with time.

### Inaccurate estimates are good, as long as they are equally inaccurate 

For a team\'s velocity to reach a stable state, the team must estimate each backlog item with the same level of accuracy. At the risk of repeating the obvious, the goal of velocity is to be able to look at a backlog of not particularly well-understood stories, and understand how many sprints it will take to complete. This requires a similar level of uncertainty for all of the estimates in the backlog.

There is a counter-intuitive implication here --- that teams should estimate each item once, and not change that estimate even if they discover new information about the item that makes them feel their Original Estimate was wrong. If the team were to go ahead and update estimates, this \'discovery of new information\' will happen regularly. This leads to the backlog having some items that have higher accuracy, but most that don\'t. This would pollute velocity because sprints with a larger percentage of high accuracy estimates will complete a different number of units compared to those with a lower percentage of high accuracy estimates. As a result, the velocity could not be used for its primary purpose --- that is, for estimating the number of sprints it will take for a team to complete a set of not-well-understood stories in the backlog. Therefore, it\'s critical to use the first estimates so that the team\'s velocity realistically represents their ability to *complete* a certain number of units of not-well-understood work far ahead into the future.

### But what about when teams realize they\'ve gotten it wrong 

Consider the following scenario:

-   Issue X has an Original Estimate of 5 days.
-   Before the next sprint is planned, the team realizes that the Original Estimate was too optimistic, and that the issue actually takes 15 days. 

Some people would argue that using the Original Estimate will endanger the sprint\'s success, because the team will take in what they think is 5 days of work into the next sprint when it\'s actually 15 days of work.

However, the inaccurate estimate of 5 days is unlikely to be an isolated occurrence. In fact, the estimates are always going to be wrong (some very little, some wildly so). This will often be discovered after the sprint has started rather than before. As long as the team estimates the same way across the whole backlog, this will work itself out over time. For example, if they always underestimate, they may find that for a 10-day sprint with 4 team members, they can only really commit to 20 days of their estimation unit. If they have established a stable velocity, then this has no effect. From a planning perspective, we can still reliably estimate how much work we\'ll get done in upcoming Sprints.

### But doesn\'t that break sprint commitment 

When the team is about to start a sprint, they can use the velocity as an indication of items from the backlog that they can realistically complete. The velocity here is based on the number of items they have successfully completed in the past. However, some people may question how this can be right when the Original Estimates won\'t include information about work that may have already been done, or information about how hard a particular item of work is.

As an example, consider the following scenario: 

-   An issue has an Original Estimate of 10 days.
-   The team works 5 days on the issue in the current sprint.
-   The team discovers a bad bug somewhere else in the project, and they decide that fixing that bug in the current sprint is far more important than completing issue X as planned.
-   The sprint gets finished, and the issue returns to the backlog.

In the next sprint, the team would be tempted to update the estimate for the issue to 5 days, and use that to make their decision whether or not to include it in the sprint. The implication is that they might not include enough work in the next sprint if they used the issue\'s Original Estimate of 10 days. However, the reason that the task was not completed previously is because of unplanned work --- and it\'s unrealistic to assume that this won\'t happen again in the future, perhaps even in the next sprint. Thus, the 10-day estimate is a realistic number to use in the absence of certainty. As a result, the cost of the unplanned work that may happen is eventually accounted for in the Original Estimate. Even if the work does turn out to be insufficient for the next sprint, the team will correct that by dragging more work into the sprint.

In the same example, consider if this were the only issue in that sprint and will be the only issue in the next. If the issue is completed in the second sprint, and we use the remaining estimate, then the velocity will be (0d + 5d) / 2 = 2.5d. However, the team can clearly complete more work than that in future sprints. If we use the Original Estimate, then the velocity will be (0d + 10d) / 2 = 5d. The use of the Original Estimate accounts for the fact that the team cannot commit to 10d in every sprint because unplanned work will likely make that impossible. It also realistically accounts for the fact that unplanned work will not happen in every sprint.

### Why not estimate on subtask and roll that up for Velocity and Commitment

Many teams break down stories into subtasks shortly before the sprint begins so they can use the stories for tracking. This raises the possibility of using the sum of the estimates on the subtasks as a way to decide which issues to commit to in the sprint (and potentially for velocity). 

As described above, tracking is really a separate process from estimation and velocity. The estimates that are applied to subtasks clearly have higher accuracy than those that were originally applied to the story. Using them for velocity would cause the velocity to have both high and low accuracy estimates, making it unusable for looking further out in the backlog where stories have only low accuracy estimates.

In addition, only items at the top of the backlog are likely to have been broken into tasks. Using task estimates for velocity means that the velocity value could only predict the time to complete the backlog up to the last story that has been broken into tasks.

Lastly, using subtask roll-up to decide sprint commitment is risky because, unlike velocity value, it doesn\'t consider the overhead of unplanned work and interruptions.

### Story points are highly recommitted - but use what works for your team

More and more industry leaders are moving away from hour estimates, and are now using the story point approach. This makes sense because in a sprint, the main questions to be answered are:

-   How much work can we realistically commit to completing this sprint?
-   How long will this part of the backlog take to deliver?

The story point approach based on original estimates can deliver the answers to these questions without the anxiety around \'accuracy\' that teams feel when asked to estimate in hours.

The Jira Software team itself uses the approach described in this article, and has established a reliable velocity that we use to plan work months in advance --- even when new work has been encountered during those months. We recommend this approach because while it is sometimes counter-intuitive, it is also powerful, fast, and simple. 

All of that said, one of the key precepts of agile is finding the way that works for you. So Jira Software does support the alternatives described above, including the use of remaining estimates for sprint commitment, hours for estimation, and hour estimates on sub-tasks.

Estimation: Waterfall Estimation vs Agile Story Points
------------------------------------------------------

### Time Spent Vs Accuracy

The longer we spend estimating a project, the more accurate the estimate will be. With a low-level, detailed estimation we are likely to get the  [most] accurate result possible. However, even then it is nearly impossible to create a quote that is 100% accurate and the time that is spent can come at a price. A lot of effort will go into this process, sometimes weeks of scoping and research and this cost will be factored into the overall price.

However, there are ways of arriving at an acceptable estimate. Consider the following:

-   A low-level, detailed, estimate might take 2 weeks of requirements gathering, boot camps, and could be 90% reliable -- at most.
-   A 2-hour, high-level, ball-park estimate might still be 80% reliable!

Was the 2-week investment of time and effort really worth it? It took 20 times longer to get the level of accuracy up from 80% to 90%. It all depends on how precise the estimate needs to be.

### Estimation Theory

![Estimation Approaches](https://www.netsolutions.com/insights/wp-content/uploads/2017/07/Table21.jpg)
![Service Provider](https://www.netsolutions.com/insights/wp-content/uploads/2017/07/Builder-Comparison-3111.jpg)

### Traditional Waterfall Approach

### Bottom-Up Estimation 

Following this, we might estimate each feature one at a time, consider testing, deployment, project management and other tasks that might not sit within the functional spec.  Finally, we arrive at a cost! But it's taken a lot of planning and research to get there.

This type of estimation process is sometimes referred to as 'Bottom-Up' and is usually what's required with the 'waterfall' methodology. We start with the smallest tasks at the bottom, in order to determine the cost of each feature. With waterfall, everyone agrees on what will be delivered, the schedule, and the end cost. Most of the detail has been thought through in advance, and there is a commitment to delivering all the features to the client for a single price.

One problem with this approach, is that the end-design solution may start to change as the work progresses. This might uncover problems or weaknesses with the original spec. Changes will result in additional costs to the client as they will likely result in additional effort which was not accounted for in the original agreed cost. These hidden costs might come as a shock to the client.

Another problem here is lack of contingency. If the cost/time and features are fixed, where is the wiggle-room? Quality will suffer. If the project is running behind schedule and the number of features is set in stone, the quality of code will suffer. This results in more bugs, and a code base that might not be as maintainable in the longer term.

![](https://www.swarmonline.com/wp-content/uploads/2018/01/bottom-up-estimating-300x253.png)

![Waterfall Golden Triangle](https://www.swarmonline.com/wp-content/uploads/2018/01/Waterfall-Golden-Triangle-300x276.png)

An Agile project will turn this 'Golden Triangle' on its head.

![Agile Golden Triangle](https://www.swarmonline.com/wp-content/uploads/2018/01/Agile-Golden-Triangle-300x276.png)

#### Agile Approach

Agile methodology at its core uses the technique of breaking down the work into small batch sizes and uses continuous market feedback to guide progress. Unlike the assembly line where the customer does not see the product till the end, in Agile, a small increment of the product is available for a "show and tell" at short intervals. Decisions can be made if the plan is adhered to, or if there are course corrections. Build what is needed not what was planned.

The cost involved in this methodology is essentially the cost of the dedicated team that comes together to deliver.

![Planning and Design Development](https://www.netsolutions.com/insights/wp-content/uploads/2017/07/211.jpg)

![Product Backlog](https://www.netsolutions.com/insights/wp-content/uploads/2017/07/311.jpg)

To offset these risks, it's essential that Agile teams:

-   calculate an accurate budget that takes into account all key elements required by the stakeholder, in terms of both cost and time commitments
-   establish processes that enable the budget to be flexible, in terms of swapping features/elements in and out following stakeholder feedback, so the project can remain Agile without going over budget

The discovery phase unfolds as follows:

##### 1. Stakeholder interviews 

The Business Analyst (BA) assigned to the discovery team revisits any existing documentation you share initially and extracts the gaps and queries. The BA then conducts regular workshops with the stakeholders, to discuss the gaps and clarify doubts in the system workflow. These workshops can be conducted over a call with the client, or with client visits to our premises, to have one-on-one sessions.

##### 2. Define high-level product backlog 

The BA, along with the Technical Architect, frames an initial outcome that the stakeholders are looking for, with a feasible solution or product. A high-level  [product backlog](https://www.scrum.org/resources/what-is-a-product-backlog) is defined in terms of epics and story titles, which describe the bare bones of the application. We then validate if the backlog addresses the scope of the project for you.

##### 3. Information architecture

Depending upon the complexity of the problem the application is intended to solve, a UX anchor is taken onboard along with the BA, for the discovery phase. The  [UX analyst's](https://www.netsolutions.com/user-experience)  prime deliverable is to understand not just you, but your customer as well. The UX analyst works on personas of the possible user group who might use the application, the ecosystem in which the personas will be using it, and touchpoints of the user personas with the system. The deliverables here would be ecosystem maps, personas, user journeys & storyboards. The primary deliverable from the UX anchor, would be to provide complete information architecture for the application, giving an overview of the system.

##### 4. Prioritization

The discovery team works on the high-level backlog, once validated by the stakeholder. The analysis is employed with the prioritization method, in order to decide which requirements to complete first, which ones can come later, and which ones to exclude. The backlog items are divided into 'must haves', 'should haves', 'could haves' & 'won't have':

-   The items with the highest business value and lowest effort involved are often the items that qualify the 'must haves' criteria.
-   The items that are of higher priority, and will need some effort to be delivered, are deemed, as 'should haves'.
-   All the backlog items that might be desirable in terms of scope, but are of lower business value are segmented, as 'could haves'.

The items that are agreed upon to be moved to later releases, are filtered out as 'won't haves' for now.

![Prioritization](https://www.netsolutions.com/insights/wp-content/uploads/2017/07/411.jpg)

##### 5. MVP backlog 

Based on the prioritization activity, the BA assembles the requirements as 'must-haves' to the backlog, and sections it as the requirements for achieving a  [Minimum Viable Product (MVP)](https://www.netsolutions.com/insights/how-to-build-an-mvp-minimum-viable-product-a-step-by-step-guide/). The MVP backlog might also contain a few items from the 'should haves' list, making sure that the product is sufficiently competitive in the market.

##### 6. Estimation 

The discovery team estimates the MVP backlog, to define the estimated cost and timeline for the first release.

This is followed by build, rinse, and repeat, until we arrive at an estimate that fits the business needs. This also allows flexibility to load and off-load features, as  [product development](https://www.netsolutions.com/product-engineering) starts. Remember, we committed to endorsing change, as we get closer to the horizon.

##### Deriving an estimate

Listed below are important techniques for estimating:

1.  Expert opinion
2.  Analogy
3.  Disaggregation

The team might agree a fixed cost and schedule with the client whilst building contingency into the number of features. Although this might seem scary for clients at first, there are many benefits. There is less need to research and devise a scope or functional spec and no need to put together a detailed estimate since the costs are agreed, based upon time and resource.

Projects are again divided into features or user stories. The functional spec might not need to exist in any detail. This means there is less time investment in the early stages, reducing the need for detailed research and requirements gathering and there is much more scope for the software design to evolve during the sprints.

The risks are identified early in the project when the velocity of the team can be calculated, perhaps at the end of the first sprint. This gives the business plenty time to shuffle stories around and according to feature priority and business value.

### Top-Down Estimation and Relative Sizing with Story Points 

In an agile project user stories are often estimated using 'effort points' based upon the Fibonacci sequence. It is called a top-down approach because we not interested in the detail of the tasks, instead we are much more interested in quick-fire estimates of higher level features, or even epics.

Typically the features are estimated by the entire team. Everyone is involved in the process, but it can happen much more rapidly with a 'poker planning session'. This could last an hour or two, rather than days/ weeks as with the traditional approach above. Having everybody involved means that the combined expertise of the whole team can be utilised. The precision decreases with larger features which might mean breaking the feature into smaller stories or tasks.

![top down estimate](https://www.swarmonline.com/wp-content/uploads/2018/01/top-down-estimating-300x253.png)




