###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Agile](https://github.com/RyKaj/Documentation/tree/master/Agile/README.md) |
------------



Agile : Writing User Stories 
============================


What Are Agile User Stories?
============================

A user story is the smallest unit of work in an agile framework. It's an
end goal, not a feature, expressed from the software user's perspective.

The purpose of a user story is articulate how a piece of work will
deliver a particular value back to the customer. Note that \"customers\"
don\'t have to be external end users in the traditional sense, they can
also be internal customers or colleagues within your organization who
depend on your team.

User stories are a few sentences in simple language that outline the
desired outcome. They don\'t go into detail. Requirements are added
later, once agreed upon by the team.

Stories fit neatly into agile frameworks like scrum and kanban. In
scrum, user stories are added to sprints and "burned down" over the
duration of the sprint. Kanban teams pull user stories into their
backlog and run them through their workflow. It's this work on user
stories that help scrum teams get better at [estimation](https://www.atlassian.com/agile/project-management/estimation)
and sprint planning, leading to more accurate forecasting and greater
agility. Thanks to stories, kanban teams learn how to manage
work-in-progress (WIP) and can further refine their workflows.

User stories are also the building blocks of larger agile frameworks
like epics and initiatives. Epics are large work items broken down into
a set of stories, and multiple epics comprise an initiative. These
larger structures ensure that the day to day work of the development
team (on stores) contributes to the organizational goals built into
epics and initiatives.

Why Create User Stories?
========================

For development teams new to agile, user stories sometimes seem like an
added step. Why not just break the big project ( [the epic](https://www.atlassian.com/agile/project-management/epics))
into a series of steps and get on with it? But stories give the team
important context and associate tasks with the value those tasks bring.

User stories serve a number of key benefits:

-   **Stories keep the focus on the user.** A To Do list keeps the team
    focused on tasks that need checked off, but a collection of stories
    keeps the team focused on solving problems for real users.
-   **Stories enable collaboration.** With the end goal defined, the
    team can work together to decide how best to serve the user and meet
    that goal.
-   **Stories drive creative solutions.** Stories encourage the team to
    think critically and creatively about how to best solve for an end
    goal.
-   **Stories create momentum.** With each passing story the development
    team enjoys a small challenges and a small win, driving momentum. 
-   Keep yourself expressing business value
-   Avoid introducing detail too early that would prevent design options
    and inappropriately lock developers into one solution
-   Avoid the appearance of false completeness and clarity
-   Get to small enough chunks that invite negotiation and movement in
    the backlog
-   Leave the technical functions to the architect, developers, testers,
    and so on





Working with User Stories
=========================

Once a story has been written, it's time to integrate it into your
workflow. Generally a story is written by the product owner, product
manager, or program manager and submitted for review.

During a sprint or iteration planning meeting, the team decides what
stories they'll tackle that sprint. Teams now discuss the requirements
and functionality that each user story requires. This is an opportunity
to get technical and creative in the team's implementation of the story.
Once agreed upon, these requirements are added to the story.

Another common step in this meeting is to score the stories based on
their complexity or time to completion. Teams use t-shirt sizes, the
Fibonacci sequence, or planning poker to make proper estimations. A
story should be sized to complete in one sprint, so as the team specs
each story, they make sure to break up stories that will go over that
completion horizon.





How to Write User Stories
=========================

Consider the following when writing user stories:

**Definition of "Done"** --- The story is generally "done" when the user
can complete the outlined task, but make sure to define what that is.

**Outline subtasks or tasks** --- Decide which specific steps need to be
completed and who is responsible for each of them.

**User personas** --- For Whom? If there are multiple end users,
consider making multiple stories.

**Ordered Steps** --- Write a story for each step in a larger process.

**Listen to feedback** --- Talk to your users and capture the problem or
need in their words. No need to guess at stories when you can source
them from your customers.

**Time** --- Time is a touchy subject. Many development teams avoid
discussions of time altogether, relying instead on their estimation
frameworks. Since stories should be completable in one sprint, stories
that might take weeks or months to complete should be broken up into
smaller stories or should be considered their own epic.

As a rule of thumb, a good user story should adhere to the
**INVEST **acronym:

-   **I**ndependent -- user stories should not depend on each other so
    they can be developed in any order.
-   **N**egotiable -- Avoid too much detail; keep them flexible so the
    team can adjust how much of the story to implement.
-   **V**aluable -- the story should provide some value to its users.
-   **E**stimable -- the team must be able to estimate the story.
-   **S**mall -- user stories should be small enough to fit in a sprint;
    large stories are hard to estimate and plan.
-   **T**estable -- ensure what is being developed can be verified and
    tested adequately.

As mentioned earlier, pay particular attention to who the user of the
product is and avoid the generic role of "User". If you don't know who
the users and customers are and why they would want to use the product,
then you should **not** write any user stories.

**Narrative**

The first part of the user story is the Narrative. 2-3 sentences used to
describe the intent of the story. It is just a summary of the intent.

**Conversations**

The most crucial aspect of a user story is the conversations that should
happen continuously between the development team, customer, Product
Owner and other stakeholders to solidify the details of the user story.

**Acceptance Criteria**

Acceptance criteria represent the conditions of satisfaction which are
written as scenarios, usually in Gherkin (Given, When, Then)
format. Acceptance criteria also provide the Definition of Done for the
story.





User Story Template and Examples
================================

User stories only capture the essential elements of a requirement:

-   Who it is for?
-   What it expects from the system?
-   Why it is important (optional?)?

Here is a simple format of user story used by 70% of practitioners:

<kbd>![](https://cdn.visual-paradigm.com/guide/agile/what-is-user-story/02-user-story-w.png) </kbd>

**Role** - The user should be an actual human who interacts with the
system.

-   Be as specific as possible
-   The development team is NOT a user

**Action** - The behavior of the system should be written as an action.

-   Usually unique for each User Story
-   The \"system\" is implied and does not get written in the story
-   Active voice, not passive voice (\"I can be notified\")

**Benefits** - The benefit should be a real-world result that is
non-functional or external to the system.

-   Many stories may share the same benefit statement.
-   The benefit may be for other users or customers, not just for the
    user in the story.

\

User stories are often expressed in a simple sentence, structured as
follows:

**"As a \[persona\], I \[want to\], \[so that\]."**

Breaking this down: 

\"As a \[persona\]\": Who are we building this for? We're not just after
a job title, we're after the persona of the person. Max. Our team should
have a shared understanding of who Max is. We've hopefully interviewed
plenty of Max's. We understand how that person works, how they think and
what they feel. We have empathy for Max.

"Wants to": Here we're describing their intent --- not the features they
use. What is it they're actually trying to achieve? This statement
should be implementation free --- if you're describing any part of the
UI and not what the user goal is you\'re missing the point.

"So that": how does their immediate desire to do something this fit into
their bigger picture? What's the overall benefit they're trying to
achieve? What is the big problem that needs solving?

For example, user stories might look like:

As Max, I want to invite my friends, so we can enjoy this service
together.

As Sascha, I want to organize my work, so I can feel more in control. 

As a manager, I want to be able to understand my colleagues progress, so
I can better report our sucess and failures. 

This structure is not required, but it is helpful for defining done.
When that persona can capture their desired value, then the story is
complete. We encourage teams to define their own structure, and then to
stick to it.





Who Should Write User Stories?
==============================

In most cases, user stories are written by a **[Product Owner](https://www.testingexcellence.com/roles-responsibilities-product-owner-agile/)**
or Business Analyst and prioritized in the product backlog. However,
that's not to say that it is the responsibility of only the Product
Owner to write user stories. In fact, any team member can write user
stories, but it is the Product Owner's responsibility to ensure a
backlog of user stories exist and are prioritized.

What's important, is that user stories **should not** be treated like
requirements document which when written will get handed off to
development team for implementation.

User stories should be seen as a means of encouraging conversations
between the Product Owner and the development team, and thus should be
written collaboratively during the product backlog grooming sessions.

An advantage of involving the development team in writing user stories
is that if there are any technical constraints, they can be highlighted
well in advance. **[Testers can particularly add value](https://www.testingexcellence.com/can-testers-add-value-agile-projects/)**
in constructing effective acceptance criteria and plan in advance on
what needs to be tested and how.





How Detailed Should User Stories Be?
====================================

User stories focus on customer value.

The basic difference between user stories and other forms of
requirements specification is the level of detail. A user story is a
metaphor for the work being done, not a full description of the work. 
The actual work being done is fleshed out via collaboration revolving
around the user story as system development progresses.

If the description becomes too lengthy (more than what will fit on an
index card), you should revisit the user story. It is likely that you
are trying to include too much detail.

Remember that the purpose of a user story is to encourage collaboration.
It is not meant to document every aspect of the work, as it's normally
the case in traditional requirements statements.

Moreover, too much information in the description can lead to missing
information in acceptance criteria.

Before agreeing to work on a story, the team must understand the
acceptance criteria. These are essential for knowing what needs to be
done in order to satisfy the user story. Acceptance criteria should be
detailed enough to define when the user story is satisfied, yet not so
detailed as to quash collaboration.





What Size Should a User Story Be?
=================================

User stories focus on customer value.

The basic difference between user stories and other forms of
requirements specification is the level of detail. A user story is a
metaphor for the work being done, not a full description of the work. 
The actual work being done is fleshed out via collaboration revolving
around the user story as system development progresses.

If the description becomes too lengthy (more than what will fit on an
index card), you should revisit the user story. It is likely that you
are trying to include too much detail.

Remember that the purpose of a user story is to encourage collaboration.
It is not meant to document every aspect of the work, as it's normally
the case in traditional requirements statements.

Moreover, too much information in the description can lead to missing
information in acceptance criteria.

Before agreeing to work on a story, the team must understand the
acceptance criteria. These are essential for knowing what needs to be
done in order to satisfy the user story. Acceptance criteria should be
detailed enough to define when the user story is satisfied, yet not so
detailed as to quash collaboration.





What Size Should a User Story Be?
=================================

A story should be small enough to be coded and tested within an
iteration---ideally just a few days. When a story is too large, it is
called an epic. Backlog items tend to start as epics when they are lower
priority. For release planning , epics should be broken down into
smaller chunks, but not so small that you have moved into detailed
design.

Common Mistakes When Writing User Stories
=========================================

**Too formal or too much detail.** Product owners with good intentions
often try to write extremely detailed user stories.  If a team sees a
story at iteration planning that looks like an IEEE requirements
document, they often assume that all the details are there and will skip
the detailed conversation.

**Writing user stories for Technical tasks.** Much of the power of Agile
comes from having a working increment of software at the end of each
iteration.  If your stories are really just technical tasks, you often
do not end up with working software at the end of each iteration, and
you lose flexibility in prioritization.

**Skipping the conversation.** Stories are intentionally vague before
iteration planning.  If you skip the acceptance criteria conversation,
you risk moving in the wrong direction, missing edge cases or
overlooking customer needs.

References

-   [Atlassian - User Stories](https://www.atlassian.com/agile/project-management/user-stories)
-   [Testing Excellence - Definitive Guide Writing Good Agile User Stories](https://www.testingexcellence.com/definitive-guide-writing-good-agile-user-stories/)
-   [CA Technology - Writing Great User Story](https://docs.ca.com/en-us/ca-agile-central/saas/writing-great-user-story)
-   [Mountain Goat Software - User Stories](https://www.mountaingoatsoftware.com/agile/user-stories)
-   [Easy Agile - How to Write Good User Stories in Agile Software Development](https://blog.easyagile.com/how-to-write-good-user-stories-in-agile-software-development-d4b25356b604)
-   [Visual Paradigm - What is user story](https://www.visual-paradigm.com/guide/agile-software-development/what-is-user-story/)


