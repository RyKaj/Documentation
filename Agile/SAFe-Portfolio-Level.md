###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Agile](https://github.com/RyKaj/Documentation/tree/master/Agile/README.md) |
------------




Information Technology : SAFe Portfolio Level 
=============================================




The Portfolio Level contains the principles, practices, and roles needed
to initiate and govern a set of development Value Streams. This is where
strategy and investment funding are defined for value streams and their
Solutions. This level also provides Agile portfolio operations and Lean
governance for the people and resources needed to deliver solutions. The
portfolio level aligns enterprise strategy to portfolio execution by
organizing the Lean-Agile Enterprise around the flow of value through
one or more value streams. Delivering the basic budgeting and necessary
governance mechanisms, including Lean Budget Guardrails, it help assures
that the Value Streams and its trains are focused on building the right
things with the appropriate level of investments to these solutions in
order for the portfolio to meet its strategic objectives. In the
small-to-midsize enterprise, one SAFe Portfolio can typically govern the
entire technical solution set. In larger enterprises---usually those
with more than 500 to 1,000 technical practitioners---there can be
multiple SAFe portfolios, typically one for each line of business, or as
otherwise structured around the business organization and funding model.

|Roles/Teams|Events|Artifacts|
|--- |--- |--- |
|* Enterprise Architect|* Strategic Investment Planning|* Strategic Themes|
|* Program Portfolio Mgmt|* Kanban Portfolio(Epic) Planning|* Enterprise|
|* Epic Owners||* Portfolio Backlog|
|||* Portfolio Kanban|
|||* Non-Functional Requirements|
|||* Epic and Enabler|
|||* Value Stream|
|||* Budgets(CapEx and OpEx)|



-   Highest level of interest/ concern /involvement/ in SAFe is  **SAFe
    Portfolio**
-   The portfolio provides the basic blocks for organizing the
    Lean-Agile Enterprise flow of value via one or more Value Streams.
-   The portfolio helps to develop systems and solutions which are
    described in strategic themes (links a SAFe portfolio to the
    changing business strategy of an enterprise).
-   To meet strategic objectives, portfolio level encapsulates these
    elements. It provides basic budgeting and other governance
    mechanisms. This way it assures that the investment in the value
    streams provides the returns necessary for the enterprise.
-   A portfolio is connected to business bi-directionally:
    -   In order to guide the Portfolio to the larger changing business
        objectives, it provides strategic themes.
    -   Another direction indicates the constant flow of portfolio
        values.
-   Program Portfolio Management acts as stakeholders, and they are
    accountable to deliver the business results.
-   SAFe Portfolio Level contains people, processes and necessary build
    systems and solutions that an enterprise needs to meet its strategic
    objectives.
-   Value Streams are the primary objectives in Portfolio, with which
    funding for the people and other resources required to build the
    Solutions.
-   Important key concepts used here are:
    -   Connection to the Enterprise,
    -   Program Portfolio Management,
    -   Managing the Flow of Portfolio Epics.

Working with Portfolio Backlog
------------------------------

Everything begins much earlier than the actual planning. In order to
work productively on the Commitment during the planning, you have to
have something to commit for. To ensure this, I have to "load" business
owners with work on probable initiatives (or, in SAFe terminology,
Epics, but hereinafter I'm going to use our usual term) as early as
possible. Ideally, this process should be completely divorced from the
iterative nature of quarterly planning and go its own Kanban way. We
took SAFe Portfolio Kanban as a basis:

![](https://habrastorage.org/r/w1560/webt/_p/qb/kj/_pqbkjcztxxv5drjbiubf8bkmgk.png)

We have a separate JIRA project with three issue types: Epics, Business
Initiatives and Architectural Initiatives; as well as the corresponding
Kanban Board. The algorithm for the Initiative's Business Owner is
simple: he adds an issue to this project, and it goes to Backlog by
default, which is the first status of our Kanban flow ---  **Funnel:**

![](https://habrastorage.org/r/w1560/webt/nd/ha/f3/ndhaf3kb3ujmxj29j0qs6xpjzkc.png)

Here the Initiatives not yet ready for Review are stored. The Business
Owner works on the content of the Initiative until he feels ready for
the next step. The minimum required at this stage is to have filled-in
fields of Problem Statement, Desired Outcome and Measure of Success, as
well as a slightly more detailed, but simple and clear presentation. At
this stage it is important to leave aside technical solutions and focus
on business parameters. When all data is collected, Business Owner moves
the task to the next status ---  **Reviewing.**

We conduct Reviews on a weekly basis for both Business and Architectural
Initiatives. Ideally this is a five-minute presentation with subsequent
Q&As. As a result of the Review a decision is taken about what happens
to the Initiative next. It can:

-   be returned to Funnel for revision,
-   be abolished without a chance for further life (in this case I use a
    special  **Out-of-Date** status hidden on the Kanban Board),
-   be approved and moved to the next stage ---  **Analyzing.**

At this stage we --- Yippee!!! --- can finally engage IT guys: analysts,
architects, leads, anyone. By "we" I mean myself as a Release Train
Engineer. But ideally it should also be Business Owners, who have
already gained some experience and autonomy necessary for engaging the
right teams and independently launching analytics. Again, I am writing
about the ideal case here. In fact the level of self-organization of our
colleagues is floating, and in some cases they ask for help of a
specially appointed facilitator, but I try to step back from this
practice.

The purpose of this stage is preliminary analytics, or, as we call it,
Pre-discovery. As a result we should get a minimum that would allow us
to commit: proposed solutions, risks and dependencies, non-functional
and infrastructure requirements, user maps, architectural schemes. In
addition, we ask the teams to give a preliminary estimation in story
points at the feature level --- this will allow us to determine
priorities at the end of the quarter.

A personal Kanban Board is created at this stage for each Initiative, in
which features and stories can be seen, with a preliminary link to a
specific iteration, which is provided by a separate JIRA workflow. So by
changing the status we can assign the issue to some iteration. Swimlanes
in Kanban Boards are configured by development teams. Since our JIRA
ecosystem is rather complicated, during Pre-discovery and Discovery we
create tasks in separate projects in order not to litter the Teams'
backlogs:

![](https://habrastorage.org/r/w1560/webt/ug/sq/be/ugsqbekca0gmm_r3qy6q4rl1_sc.png)


Also at the Pre-discovery stage, we involve Architects or, as it's been
often practiced lately, their trusted people --- "EA Ambassadors". Their
task is to convey the vision of the architectural department to all the
participants, to help find the best solution, and finally to approve
this solution with the company's Head of Enterprise Architecture.
When all the people involved believe that the Initiative has been
analyzed enough and is ready for the next step, it is moved to the next
status ---  **Portfolio Backlog.**
At this stage it is important to conduct a WSJF prioritization (
[Weighted Shortest Job
First](https://en.wikipedia.org/wiki/Shortest_job_next#Weighted_shortest_job_first)
). To do this, we have a big meeting 3 weeks before the planning, which,
unfortunately, up to now has always lasted many hours. During this
meeting members of the Management Board evaluate the Business Value,
Time Criticality, Risk Reduction and Opportunity Enablement with the
help of Fibonacci-aligned planning poker:

![](https://habrastorage.org/r/w1560/webt/oa/uu/tf/oauutfrn4oy4gmj_iex_mzcgrno.png)

To be able to track the history of Initiatives, for each of them I add a
label in JIRA with quarter data: 2018Q4, 2019Q1, etc.
Looking ahead, let me describe all the possible statuses. After the
final commitment at PI Planning, Initiatives successfully taken into
work are moved to the  **Implementing** status, while those 'not fitted'
receive  **Parked** status and might be considered for the next
quarters. Delivered initiatives are moved to the  **Done** status.
As a result, we have the following picture on the Kanban Board:

![](https://habrastorage.org/r/w1560/webt/jj/ww/ov/jjwwovbdgbyuddjwmnv9fzb3gza.png)

Of course, we are not even in the middle of our way yet, but at the
moment I can already note that thanks to the Portfolio Backlog
implementationBusiness owners have begun to work through their
Initiatives in detail and thoroughly prepare for the Review.

-   The Reviews have become more meticulous in a good way.
-   Teams have more time for Pre-discovery.
-   I do not lose old Initiatives --- I can always go back to the
    Parked, not delivered or forgotten Initiatives and work on them
    further.

### Tools used at this stage: {#SAFePortfolioLevel-Toolsusedatthisstage:}

-   Atlassian Jira Software Server
-   Plugin Colors for Jira --- for highlighting Business and
    Architectural Initiatives
-   The ' *Structure --- Project Management at Scale*' plugin --- to
    visualize the structure made of Initiatives and features belonging
    to them, and their WSJF prioritization
-   Atlassian Confluence --- source of internal documentation
-   Lucidchart and its plugins for Jira and Confluence --- for diagrams
    drawing

Preparation for PI Planning
---------------------------

A month before PI Planning is when the busiest time comes. Too many
things need to be taken into account, and in order not to leave anything
out, I have to create a multipage "logistic" Google Form. Let me
describe the most important tabs from this Form and the activities
around them.
**Feedback.** A few days after each PI Planning we conduct a
Retrospective, which helps us not to forget what conclusions we came to
and how we need to adjust the course. This is an important part in terms
of continuous improvement.
**Technical preparation.** With transition to remote planning, specific
requests have appeared, such as quality of Internet connection
(prioritization and optimization of routes for JIRA and Confluence) and
video- and audio presence (we use the Logitec Group kits, Jabbra
microphones and personal headphones in various combinations, webcams,
Zoom software for video conferencing).
**Facilitators.** It's a list of employees responsible for facilitation
in each of the working groups, indicating their location and a link to
the permanent Zoom-channel of the working group.
**Audience.** The complete list of all invitees.
**Checklist.** The full list of important tasks with deadlines and
responsible persons. To give you some insight below you can find several
examples of the most typical and vital tasks relevant for each PI
Planning: training of Facilitators (a training manual has been prepared
with all the necessary steps such as organizing a working team, timing
the meetings and decomposing the Initiative into a list of features);
update of working groups' location plans for each office; control of the
Velocity update for all development teams; ordering meals; creating
reports from previous quarters; printouts of lists of Initiatives and
schedules.

PI Planning and the process of Commitment
-----------------------------------------

After all the preparatory running around, this moment finally comes ---
the start of PI Planning. In two days we have to discover all
Initiatives, make sure that the information is sufficient and commit.
After a few pep talks the working groups go to their places and get to
business. At the moment the number of groups is distributed among the
three offices as 4x4x2, and remote users are connected to the required
group via a dedicated Zoom channel.
Upon completion of the Discovery on each of these Initiatives, the
facilitator makes sure that all the necessary data, such as Acceptance
Criteria, technical solution, risks, dependencies, the necessity of a
new infrastructure, is available and marks the Initiative with the 'IT
Session Finished' checkbox for easy tracking of the progress. After that
the working group can move on to the next Initiative.
After a dozen of PI Plannings the feeling of being under constant stress
and time pressure, which was with us from the very beginning, has
significantly faded, and now it's all more like work as usual. In the
afternoon on the first and second days of the Planning it's the time for
unhurried commitment according to priorities. To perform a commitment, I
have several separate structures. The first one is a structure
containing a list of features and stories scheduled for the commitment:

![](https://habrastorage.org/r/w1560/webt/jw/b9/du/jwb9dufutnxjl0cceuedtqdigcc.png)


Unfortunately, this structure on the screenshot contains only tasks that
did not fit into the commitment of the current quarter, so the sample is
unrepresentative. In any case, in the search field I can select the
Initiative needed in order of priority by number, which is put in a
separate field for each feature and story, change the issues' status
from Planned to Committed and put them to the desired iteration, thereby
committing for them:

![](https://habrastorage.org/r/w1560/webt/ux/i5/hs/uxi5hsw4ahbf4vqtvse03x0z2mc.png)


As a result, the issue will disappear from this structure and appear in
a new, which reflects the growing commitment:

![](https://habrastorage.org/r/w1560/webt/6q/qh/af/6qqhaf8c7gsne22kaw78jfaw9xe.png)


As you can see on the screenshot, in this structure the stories fall
into the folder of the development team to which they belong and are
grouped by iteration. Here, I see the total Velocity of the team in the
folder name, and in addition in the Commitment column, the over
commitment is automatically determined and highlighted for each team, by
using a custom formula.
Of course, if the first and highest priority Initiatives are included
into a commitment mostly easily, soon, as more and more teams fill their
backlogs to the end, there could be respective problems with some of the
initiatives, after certain arguments and discussions, being postponed
(parked) as a result.
At the end of this rather straightforward process the teams swear to
deliver their commitment on the company's flag (ok, not really) and
hurry to their homes (well, again, not really, mostly they flee to some
bar to celebrate).

### Tools used at this stage: 

-   Atlassian Jira Software Server
-   The 'Structure --- Project Management at Scale' plugin -- to monitor
    the Discovery process and during the execution of the commitment.

Cloning issues into the working JIRA ecosystem of the Company
-------------------------------------------------------------

While everyone is drinking, the RTE is working on creating commitments
in the form in which it could be distributed to the development teams'
backlogs and monitored throughout the quarter. To do this, I use the
'Bulk Clone Professional for Jira' plugin --- it adds an item doing
collective cloning to the Bulk Change menu and has such necessary
features as links cloning, updating links between newly created clones,
updating Epic links, adding Summary prefix and automatic labeling:

![](https://habrastorage.org/r/w1560/webt/pp/5u/j7/pp5uj7lre2_7zsogsv7mgp_d2fw.png)

I add status as a prefix, because at the planning stage the statuses
reflect the planned iteration of completion. As a result I can see right
away in the Summary when we are planning to finish the feature or
story.
At first, I clone absolutely all issues into a separate Global Backlog
project, since we keep epics in it, and I need to have actual epic-story
connections in newly cloned tasks. And already as a second step, I make
JQL-requests for each development team separately and move the stories
into the working projects of the teams.
As a result, I create a structure that reflects the current Commitment
and consists of final stories, which I then use for monitoring:

![](https://habrastorage.org/r/w1560/webt/9y/xa/ep/9yxaeplzfj05z1sgqydu8w4j4dy.png)

In general, the advantages of this approach are the following:

-   It is easier for an IT guy to type new features and stories rather
    than to write them down with a highlighter on a sticky note.
-   Many things, such as capacity remains and WSJF update depending on
    the stories estimations, are calculated automatically using custom
    formulas.
-   Thanks to cloning, the original Commitment is preserved for history
    and we can always return to it.
-   It saves us both time and energy at the stage of planning
    preparation --- paper handling takes energy.
-   Of course, it's great that we no longer need to add issues to JIRA
    by typing in sticky notes.

### Tools used at this stage: 

-   Atlassian Jira Software Server
-   The '*Bulk Clone Professional for Jira*' Plugin-- for cloning
    features and stories into working JIRA projects.
-   The '*Structure --- Project Management at Scale*' plugin -- for the
    creation of the final Commitment structure.