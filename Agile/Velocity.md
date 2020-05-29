###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Agile](https://github.com/RyKaj/Documentation/tree/master/Agile/README.md) |
------------


Agile : Velocity 
================


**Velocity** is how a scrum team measures the amount of work they can complete in a typical sprint. Velocity is measured historically, from one sprint to the next. By tracking the number of story points the team can complete according to their own definition of done, they can build up a reliable and predictable sense of how long it will take them to complete new stories based on their relative point value.

Keeping track of the velocity is the responsibility of the scrum master. At the end of each sprint demo, the scrum master should calculate the number of points that were estimated for the stories that were accepted as done during that sprint. This number should be added as a data point on the velocity chart for that sprint.

Velocity charts tend to start out jumping around from very high numbers to very low numbers, as the team learns how much work they can do in a sprint, and how to estimate stories. The longer a team works together, the better they get at estimating stories consistently relative to each other. That skill leads to a better sense of how many stories, and how many points, the team can accomplish in a single sprint.

Over time, if the composition of the team stays consistent, a velocity chart that started off very erratic will start to find itself averaging toward a consistent value. Unlike many charts in a business environment, the point of the velocity chart isn't to see a constant increase, but rather to see the values converging around a consistent horizontal line. That line represents the amount of work the team can realistically and sustainably accomplish in a single sprint.



People outside the scrum process may be confused about the nature of the velocity chart. From a management perspective, there may be an impulse to favor an increase in the amount of work a team is doing, and look for velocity to grow over time. But a velocity chart is intended to trend toward a horizontal average. You may hear executives talking about trying to increase the team's velocity, or celebrating a sprint in which the velocity was higher than typical sprints. Get ahead of these conversations by reminding everyone that the point of velocity tracking is to improve the team's ability to estimate how much work they can get done consistently and reliably. A velocity chart that shows a constant increase (or decrease) over time usually reflects a problem in the process.



Cumulative Flow Diagram
=======================

What is a Cumulative Flow Diagram? 
----------------------------------

One of charts that give you a quick overview of what's happening in a project or product work is Cumulative Flow Diagram (CFD). On one hand, in CFD you can find typical information about status of work: how much work is done, ongoing and in backlog, what is the pace of progress, etc. This is the basic stuff. On the other hand, once you understand the chart, it will help you to spot all sorts of issues that a team may be facing. This is where Cumulative Flow Diagram shows its real value.

Before we move to all the specific cases let me start with the basic stuff though (feel free to scroll down if you're familiar with this part).

The mechanism of Cumulative Flow Diagram is very simple. On a vertical axis we have a number of tasks. On a horizontal one we have a timeline. The curves are basically a number of items in any possible state shown in a time perspective. The whole trick is that they are shown cumulatively.

If the green curve shows stuff that is done it will naturally grow over time -- that's simple. If the blue line shows tasks that are in progress, and we have stable amount of work in progress it will still go up as it adds to the green line. In other words work in progress would be represented by the gap between the blue and the green lines... We'll come back to that in a while.

Any line on CFD represents a specific stage. In the simplest example we'd have items that are to be done, stuff that is ongoing and things that are done.

For the sake of the rest of this article I'm going to use a simple process as a reference.

We have a backlog, items that are in development or testing and stuff that is done. For the sake of Cumulative Flow Diagram examples it doesn't matter whether tasks in development are ongoing or done and waiting for testing. However, as we will find later, there may be some indicators that would make tracking these two stages separately valuable.

CFD is one of the most advanced [analytics for Lean management](https://kanbanize.com/kanban-resources/kanban-analytics/). It provides a concise visualization of the three most important metrics of your flow:

-   Cycle time
-   Throughput
-   Work in progress

Its main purpose is to show you how stable your flow is and help you understand where you need to focus in order to make your process more predictable. It gives you both quantitative and qualitative insight into both past and existing problems and can visualize massive amounts of data.

<kbd>![ALTTEXT](https://kanbanize.com/wp-content/uploads/website-images/kanban-resources/cumulative-flow-diagram-kanbanize.png)


How to read a Cumulative Flow Diagram (CFD) 
-------------------------------------------

The chart tracks the total number of work items that are in the columns of the \'In Progress\' section on your Kanban board each day.

The horizontal axis of the CFD represents the time frame for which the chart is visualizing data. The vertical axis shows the cumulative number of cards that are in the workflow at the various points in time.

The differently colored bands that divide sections of the upward flow are the different stages of your workflow as they appear on the Kanban board itself. The bands always go up or sideways in accordance to the assignments that go through your process.

The top line of each band on the cumulative flow chart represents the entry point of tasks in the respective stage of your Kanban board while the bottom one shows when it leaves it. If a line becomes flat, that means nothing is arriving in the corresponding stage or nothing is leaving it.

Using a CFD, you can get an idea of how long is the approximate cycle time of your tasks in just a single glance.

This is possible by measuring the horizontal distance between the top line of the first stage on the cumulative flow diagram and the bottom line of the last in progress stage.

The number of days/weeks/months that have passed is the approximate average cycle time of your team's assignments for the time frame.

> ***The distance between the lines of a CFD will show you the problems of your workflow.***

<kbd><img src="./attachments/451819532.jpg" alt="">

Team Velocity
-------------

For each Kanban board there is a Cumulative Flow Diagram. [How to can be found here - https://goo.gl/yh3ZNH](https://goo.gl/yh3ZNH)

To view the project\'sCumulative Flow Diagram

1.  Go to the Kanban board
2.  On the Left navigation - click Reports
3.  Click Cumulative Flow Diagram.

[Keep in mind that these build-in reports within the project can not be saved.]

### How should it look?

The best diagram you want to see is an evenly rising one, with bands
staying more-less even, except for the \"completed tasks\" ban, which
shall be continuously getting taller, as the number of tasks done is
hopefully always growing.

<kbd>![Cumulative Flow Diagram by Kanban Tool](https://static.kanbantool.com/kanban+landing/kanban-cumulative-flow-diagram/kanban-tool-cumulative-flow-diagram.png)

### What to look out for

What you don\'t want to see is a sudden rise within any band of tasks.
This will undoubtedly point to an issue.

From successive accumulation of tasks in a certain band you can also
foresee bottlenecks - and by this make an effort to try to stop them.

Another thing you do not want to see is the band related to tasks \"in
progress\" widen vertically - as this means that the number of tasks
being handled at present is too large and therefore the whole project
will most likely be delayed.

### Benefits

The CFD only requires 3 basic things from the process - a Backlog, an
\'In Progress\' column and a Done section - using this division allows
you to see the information in the diagram well. Therefore, any team that
utilizes this kind of workflow division can benefit from Cumulative Flow
information. Whether you use **Scrum**, **Kanban** or any other custom
project management method, as long as you organize it in task groups,
the CFD will be helpful to you.

###### References

-   [CA Technology Breaking Stories Down](https://docs.ca.com/en-us/ca-agile-central/saas/breaking-stories-down)
-   [Sitepoint - Velocity and burndown charts](https://www.sitepoint.com/scrum-artifacts-velocity-and-burndown-charts/)

###### Attachments: 

[How to Read CFD.jpg](attachments/451819528/451819532.jpg) 
