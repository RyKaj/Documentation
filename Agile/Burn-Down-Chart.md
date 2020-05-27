###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Infrastructure Architecture](https://github.com/RyKaj/Documentation/tree/master/Agile/README.md) |
------------



Agile : Burn Down Chart 
=======================


A **burndown** chart shows the team's progress toward completing all of
the points they agreed to complete within a single sprint. This chart
starts with the total number of points the team has taken on for the
sprint, and tracks on a day-to-day basis how many of those points have
been completed and are ready for the sprint demo.

The burndown chart is usually maintained by the scrum master, and may be
updated on a daily basis, perhaps after the daily stand up, or on a
continuous basis if it's generated automatically by the tools the team
is using to maintain the scrum board. The primary audience for a
burndown chart is the team itself, although there may be data points on
a burndown chart that could be relevant to people outside the scrum
team.

A typical burndown chart starts with a straight diagonal line from the
top left to the bottom right, showing an "ideal" burndown rate for the
sprint. In practice, the point is not to match that ideal, but rather to
keep in mind how much of the sprint is left at any point in time, and
how much effort the team expects to be able to put toward the
development of the product on any particular day of the sprint.

Lines or columns on the burndown chart may be used to represent the
number of points of effort actually remaining in the sprint from
day-to-day, starting with the number of points the team has committed to
at the sprint planning. As work is completed, these columns should
become shorter until they reach zero.

Some teams also choose to track the daily work completed, either in
story points or in individual tasks toward completing stories. This can
be done with a line or stacked columns, tracking these daily metrics
against the burndown chart so they can be viewed in context.

There are very few legitimate reasons for a column to be taller on one
day than it was on the previous day. If a bug is discovered before the
end of the sprint, and a story that was marked as done or ready to demo
needs to be worked on again, columns may increase in size from one day
to the next. New stories introduced after the sprint has started may
also cause one day's column to be higher than the previous day's. A
pattern of rising columns on a burndown chart may indicate that the
scope of the work is exceeding the originally agreed sprint backlog,
which is definitely an anti-pattern in scrum.

![agile burndown chart](http://agilewarrior.files.wordpress.com/2013/06/how-quickly-burn-through-stories.png?w=540)

The burndown is a chart that shows how quickly you and your team are
burning through your customer\'s [user stories](http://www.agilenutshell.com/user_stories). It
shows the total effort against the amount of work we deliver each
iteration. Something like this:

![agile burndown chart](http://agilewarrior.files.wordpress.com/2013/06/burndown-3-details.png?w=540)

We can see the total effort on the left, our team velocity on the right.
But look what else this simple graphs gives us.

-   Work done each iteration
-   Work remaining
-   Work done so far
-   When we can expect to be done

All this from one graph!

Now what you see above is pretty ideal. A more realistic burndown looks
something more like this:

![agile burndown chart](http://agilewarrior.files.wordpress.com/2013/06/burndown-4-realistic.png?w=540)

It's never a straight line. The team never moves at exactly one fixed
velocity. And we discover things along the way (notice how it shows us
scope creep in the form of those 5 new reports).

And of course like all things in Agile, you are free to make things your
own. One tweak I like making to the burndown is displaying total work
done each iteration also. This let's me look at the chart, and
immediately get a sense of whether we are a quarter, a third, or ½ way
done the project.

![agile burndown chart](http://agilewarrior.files.wordpress.com/2013/06/burndown-5-workcomplete.png?w=540)

Common Pitfalls
---------------

Burndown charts only show the number of story points completed, they do
not indicate any changes in the scope of work as measured by total
points in the backlog.  As a result, it's difficult to tell whether
changes in the burndown chart can be attributed to backlog items
completed, or simply and increase (or much less likely) a decrease in
story points. The burn up chart resolves this issue by showing a
separate line for overall backlog size.

Neither the burndown or burnup chart provides any indication of which
product backlog items have been completed. This means that a team can
have a burndown chart that shows continued progress, but it does not
indicate whether the team is working on the correct things.  For this
reason, burndown and burnup charts can only provide an indication of
trends rather than giving explicit indication of whether a team is
delivering the right product backlog items.

### Beware Scope Creep

The scope of the sprint backlog should be respected by everyone. If new
stories are regularly being added to the sprint after the sprint has
started, the columns that reflect the amount of work left to be
completed in the sprint on any given day may rise above the level of the
previous day. This pattern is sometimes represented in a contrasting
color, to highlight the fact that the originally agreed to scope may be
creeping upward. If this happens frequently, it may reflect problems in
the process that are worth addressing in a sprint retrospective.

###### References

-   [CA Technology - Burn Down Chart](https://docs.ca.com/en-us/ca-agile-central/saas/reading-burndown-chart)
-   [Agile Nutshell - burndown](http://www.agilenutshell.com/burndown)
-   [Agile Alliance](https://www.agilealliance.org/glossary/burndown-chart)
-   [Sitepoint - Velocity and burndown charts](https://www.sitepoint.com/scrum-artifacts-velocity-and-burndown-charts/)

