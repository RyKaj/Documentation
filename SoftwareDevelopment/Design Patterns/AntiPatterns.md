<div id="main" class="aui-page-panel">

<div id="main-header">

<div id="breadcrumb-section">

1.  [Information Technology](index.html)
2.  [3.0 Sofware Development
    Lifecycle](3.0-Sofware-Development-Lifecycle_380470491.html)
3.  [Design Patterns](Design-Patterns_451820045.html)
4.  [1.0 Design Pattern - Programming
    Language](1.0-Design-Pattern---Programming-Language_451820065.html)

</div>

# Information Technology : AntiPatterns

</div>

<div id="content" class="view">

AntiPatterns, like their design pattern counterparts, define an industry
vocabulary for the common defective processes and implementations within
organizations. A higher-level vocabulary simplifies communication
between software practitioners and enables concise description of
higher-level concepts.

An AntiPattern is a literary form that describes a commonly occurring
solution to a problem that generates decidedly negative consequences.
The AntiPattern may be the result of a manager or developer not knowing
any better, not having sufficient knowledge or experience in solving a
particular type of problem, or having applied a perfectly good pattern
in the wrong context.

AntiPatterns provide real-world experience in recognizing recurring
problems in the software industry and provide a detailed remedy for the
most common predicaments. AntiPatterns highlight the most common
problems that face the software industry and provide the tools to enable
you to recognize these problems and to determine their underlying
causes.

Furthermore, AntiPatterns present a detailed plan for reversing these
underlying causes and implementing productive solutions. AntiPatterns
effectively describe the measures that can be taken at several levels to
improve the developing of applications, the designing of software
systems, and the effective management of software projects.

Good software structure is essential for system extension and
maintenance. Software development is a chaotic activity, therefore the
implemented structure of systems tends to stray from the planned
structure as determined by architecture, analysis, and design.

Software refactoring is an effective approach for improving software
structure.

The resulting structure does not have to resemble the original planned
structure.

The structure changes because programmers learn constraints and
approaches that alter the context of the coded solutions. When used
properly, refactoring is a natural activity in the programming process.

For example, the solution for the Spaghetti Code AntiPattern defines a
software development process that incorporates refactoring. Refactoring
is strongly recommended prior to performance optimization. Optimizations
often involve compromises to program structure. Ideally, optimizations
affect only small portions of a program. Prior refactoring helps
partition optimized code from the majority of the software.

Development AntiPatterns utilize various formal and informal refactoring
approaches. The following summaries provide an overview of the
Development AntiPatterns found in this chapter and focus on the
development AntiPattern problem. Included are descriptions of both
development and mini-AntiPatterns. The refactored solutions appear in
the appropriate AntiPattern templates that follow the summaries.

## The Blob

Procedural-style design leads to one object with a lion’s share of the
responsibilities, while most other objects only hold data or execute
simple processes. The solution includes refactoring the design to
distribute responsibilities more uniformly and isolating the effect of
changes.

The Blob is found in designs where one class monopolizes the processing,
and other classes primarily encapsulate data. This AntiPattern is
characterized by a class diagram composed of a single complex controller
class surrounded by simple data classes. The key problem here is that
the majority of the responsibilities are allocated to a single class.

In general, the Blob is a procedural design even though it may be
represented using object notations and implemented in object-oriented
languages. A procedural design separates process from data, whereas an
object-oriented design merges process and data models, along with
partitions.

The Blob contains the majority of the process, and the other objects
contain the data. Architectures with the Blob have separated process
from data; in other words, they are procedural-style rather than
object-oriented architectures.

![](https://sourcemaking.com/files/v2/content/antipatterns/Blob%20-%202-2x.png)

The Blob can be the result of inappropriate requirements allocation. For
example, the Blob may be a software module that is given
responsibilities that overlap most other parts of the system for system
control or system management.

The Blob is also frequently a result of iterative development where
proof-of-concept code evolves over time into a prototype, and
eventually, a production system. This is often exacerbated by the use of
primarily GUI-centric programming languages, such as Visual Basic, that
allow a simple form to evolve its functionality, and therefore purpose,
during incremental development or prototyping.

The allocation of responsibilities is not repartitioned during system
evolution, so that one module becomes predominant. The Blob is often
accompanied by unnecessary code, making it hard to differentiate between
the useful functionality of the Blob Class and no-longer-used code (see
the Lava Flow AntiPattern).

### Symptoms And Consequences

  - Single class with a large number of attributes, operations, or both.
    A class with 60 or more attributes and operations usually indicates
    the presence of the Blob
  - A disparate collection of unrelated attributes and operations
    encapsulated in a single class. An overall lack of cohesiveness of
    the attributes and operations is typical of the Blob.
  - A single controller class with associated simple, data-object
    classes.
  - An absence of object-oriented design. A program main loop inside the
    Blob class associated with relatively passive data objects. The
    single controller class often nearly encapsulates the applications
    entire functionality, much like a procedural main program.
  - A migrated legacy design that has not been properly refactored into
    an object-oriented architecture.
  - The Blob compromises the inherent advantages of an object-oriented
    design. For example, The Blob limits the ability to modify the
    system without affecting the functionality of other encapsulated
    objects. Modifications to the Blob affect the extensive software
    within the Blob's encapsulation. Modifications to other objects in
    the system are also likely to have impact on the Blob's software.
  - The Blob Class is typically too complex for reuse and testing. It
    may be inefficient, or introduce excessive complexity to reuse the
    Blob for subsets of its functionality.
  - The Blob Class may be expensive to load into memory, using excessive
    resources, even for simple operations.

### Typical Causes

  - *Lack of an object-oriented architecture.* The designers may not
    have an adequate understanding of object-oriented principles.
    Alternatively, the team may lack appropriate abstraction skills.
  - *Lack of (any) architecture.* The absence of definition of the
    system components, their interactions, and the specific use of the
    selected programming languages. This allows programs to evolve in an
    ad hoc fashion because the programming languages are used for other
    than their intended purposes.
  - *Lack of architecture enforcement.* Sometimes this AntiPattern grows
    accidentally, even after a reasonable architecture was planned. This
    may be the result of inadequate architectural review as development
    takes place. This is especially prevalent with development teams new
    to object orientation.
  - *Too limited intervention.* In iterative projects, developers tend
    to add little pieces of functionality to existing working classes,
    rather than add new classes, or revise the class hierarchy for more
    effective allocation of responsibilities.
  - *Specified disaster.* Sometimes the Blob results from the way
    requirements are specified. If the requirements dictate a procedural
    solution, then architectural commitments may be made during
    requirements analysis that are difficult to change. Defining system
    architecture as part of requirements analysis is usually
    inappropriate, and often leads to the Blob AntiPattern, or worse.

### Known Exceptions

The Blob AntiPattern is acceptable when wrapping legacy systems. There
is no software partitioning required, just a final layer of code to make
the legacy system more accessible.

### Refactored Solution

As with most of the AntiPatterns in this section, the solution involves
a form of refactoring. The key is to move behavior away from the Blob.
It may be appropriate to reallocate behavior to some of the encapsulated
data objects in a way that makes these objects more capable and the Blob
less complex. The method for refactoring responsibilities is described
as follows:

1.  Identify or categorize related attributes and operations according
    to contracts. These contracts should be cohesive in that they all
    directly relate to a common focus, behavior, or function within the
    overall system. For example, a library system architecture diagram
    is represented with a potential Blob class called LIBRARY.
    
    In the example shown in figure 1, the LIBRARY class encapsulates the
    sum total of all the system's functionality. Therefore, the first
    step is to identify cohesive sets of operations and attributes that
    represent contracts. In this case, we could gather operations
    related to catalog management, like Sort\_Catalog and
    Search\_Catalog.
    
    We could also identify all operations and attributes related to
    individual items, such as Print\_Item, Delete\_Item, and so on.
    
    ![](https://sourcemaking.com/files/v2/content/antipatterns/Blob2%20-%203-2x.png)  
    Figure 1
    
    ![](https://sourcemaking.com/files/v2/content/antipatterns/Blob2%20-%204-2x.png)  
    Figure 2

2.  The second step is to look for "natural homes" for these
    contract-based collections of functionality and then migrate them
    there. In this example, we gather operations related to catalogs and
    migrate them from the LIBRARY class and move them to the CATALOG
    class.
    
    We do the same with operations and attributes related to items,
    moving them to the ITEM class. This both simplifies the LIBRARY
    class and makes the ITEM and CATALOG classes more than simple
    encapsulated data tables. The result is a better object-oriented
    design.
    
    ![](https://sourcemaking.com/files/v2/content/antipatterns/Blob2%20-%205-2x.png)  
    Figure 3

3.  The third step is to remove all "far-coupled," or redundant,
    indirect associations. In the example, the ITEM class is initially
    far-coupled to the LIBRARY class in that each item really belongs to
    a CATALOG, which in turn belongs to a LIBRARY.

4.  Next, where appropriate, we migrate associates to derived classes to
    a common base class. In the example, once the far-coupling has been
    removed between the LIBRARY and ITEM classes, we need to migrate
    ITEMs to CATALOGs, as shown in figure 4.
    ![](https://sourcemaking.com/files/v2/content/antipatterns/Blob2%20-%206-2x.png)  
    Figure 4

5.  Finally, we remove all transient associations, replacing them as
    appropriate with type specifiers to attributes and operations
    arguments.
    
    In our example, a Check\_Out\_Item or a Search\_For\_Item would be a
    transient process, and could be moved into a separate transient
    class with local attributes that establish the specific location or
    search criteria for a specific instance of a check-out or search.

### Variations

Sometimes, with a system composed of the Blob class and its supporting
data objects, too much work has been invested to enable a refactoring of
the class architecture. An alternative approach may be available that
provides an "80%" solution.

Instead of a bottom-up refactoring of the entire class hierarchy, it may
be possible to reduce the Blob class from a controller to a coordinator
class. The original Blob class manages the system's functionality; the
data classes are extended with some of their own processing.

The data classes operate at the direction of the modified coordinator
class. This process may allow the retention of the original class
hierarchy, except for the migrations of processing functionality from
the Blob class to some of the encapsulated data classes.

Riel identifies two major forms of the Blob AntiPattern. He calls these
two forms God Classes:*Behavioral Form* and*Data Form*

The Behavioral Form is an object that contains a centralized process
that interacts with most other parts of the system. The Data Form is an
object that contains shared data used by most other objects in the
system. Riel introduces a number of object-oriented heuristics for
detect ing and refactoring God Class designs.

### Applicability To Other Viewpoints And Scales

Both architectural and managerial viewpoints play key roles in the
initial prevention of the Blob AntiPattern. Avoidance of the Blob may
require ongoing policing of the architecture to assure adequate
distribution of responsibilities.

It is through an architectural viewpoint that an emerging Blob is
recognized. With a mature object-oriented analysis and design process,
and an alert manager who understands the design, developers can prevent
the cultivation of a Blob.

The most important factor is that, in most cases, it's much less
expensive to create appropriate design than to rework design after
implementation. Up-front investment in good architecture and team
education can ensure a project against the Blob and most other
AntiPatterns.

Ask any insurance salesperson, and he or she may tell you that most
insurance is purchased *after* it was needed by people who are poorer
but wiser.

#### Example

A GUI module that is intended to interface to a processing module
gradually takes on the processing functionality of background-processing
modules. An example of this is a PowerBuilder screen for customer data
entry/retrieval. The screen can:

1.  Display data.

2.  Edit data.

3.  Perform simple type validation. The developer then adds
    functionality to what was intended to be the decision engine:

4.    - Complex validation.
      - Algorithms that use the validated data to assess next actions.

5.  The developer then gets new requirements to:

6.    - Extend the GUI to three forms.
      - Make it script-driven (including the development of a script
        engine).
      - Add new algorithms to the decision engine.

The developer extends the current module to incorporate all of this
functionality. So instead of developing several modules, a single module
is developed. If the intended application is architected and designed,
it is easier to maintain and extend.

![](https://sourcemaking.com/files/v2/content/antipatterns/Blob3%20-%201-2x.png)
![](https://sourcemaking.com/files/v2/content/antipatterns/Blob3%20-%202-2x.png)

## Continuous Obsolescence

Technology is changing so rapidly that developers have trouble keeping
up with the current versions of software and finding combinations of
product releases that work together.

Given that every commercial product line evolves through new product
releases, the situation has become increasingly difficult for developers
to cope with. Finding compatible releases of products that successfully
interoperate is even harder.

![](https://sourcemaking.com/files/sm/images/obsolete.jpg)

Java is a well-known example of this phenomenom, with new versions
coming out every few months. For example, by the time a book on Java 1.X
goes to press, a new Java Development Kit obsoletes the information.
Java is not alone; many other technologies also participate in
Continuous Obsolescence.

The most flagrant examples are products that embed the year in their
brand names, such as Product98. In this way, these products flaunt the
progression of their obsolescence. Another example is the progression of
Microsoft dynamic technologies:

  - DDE
  - OLE 1.0
  - OLE 2.0
  - COM
  - ActiveX
  - DCOM
  - COM?

From the technology marketers' perspective, there are two key factors:
*mindshare* and *marketshare.* Rapid innovation requires the dedicated
attention of consumers to stay current with the latest product features,
announcements, and terminology.

For those following the technology, rapid innovation contributes to
mindshare; in other words, there is always new news about technology X.
Once a dominant marketshare is obtained, the suppliers' primary income
is through obsolescence and replacement of earlier product releases. The
more quickly technologies obsolesce (or are perceived as obsolete), the
higher the income.

### Refactored Solution

An important stabilizing factor in the technology market is *open
systems standards.* A consortium standard is the product of an industry
concensus that requires time and investment.

Joint marketing initiatives build user awareness and acceptance as the
technologies move into the mainstream. There is an inherent inertia in
this process that benefits consumers, for once a vendor product is
conformant to a standard, the manufacturer is unlikely to change the
conformant features of the product.

The advantages of a rapidly obsolescing technology are transitive.
Architects and developers should depend upon interfaces that are stable
or that they control. Open systems standards give a measure of stability
to an otherwise chaotic technology market.

### Variations

The Wolf Ticket Mini-AntiPattern describes various approaches that
consumers can use to influence product direction toward improved product
quality.

## Lava Flow

  - **AntiPattern Name:** Lava Flow
  - **Also Known As:** Dead Code
  - **Most Frequent Scale:** Application
  - **Refactored Solution Name:** Architectural Configuration Management
  - **Refactored Solution Type:** Process
  - **Root Causes:** Avarice, Greed, Sloth
  - **Unbalanced Forces:** Management of Functionality, Performance,
    Complexity
  - **Anecdotal Evidence:** "Oh *that\!* Well Ray and Emil (they're no
    longer with the company) wrote that routine back when Jim (who left
    last month) was trying a workaround for Irene's input processing
    code (she's in another department now, too). I don't think it's used
    anywhere now, but I'm not really sure. Irene didn't really document
    it very clearly, so we figured we would just leave well enough alone
    for now. After all, the bloomin' thing works doesn't it?\!"

### Background

In a data-mining expedition, we began looking for insight into
developing a standard interface for a particular kind of system. The
system we were mining was very similar to those we hoped would
eventually support the standard we were working on. It was also a
research-originated system and highly complex. As we delved into it, we
interviewed many of the developers concerning certain components of the
massive number of pages of code printed out for us.

Over and over, we got the same answer: "I don't know what that class is
for; it was written before I got here." We gradually realized that
between 30 and 50 percent of the actual code that comprised this complex
system was not understood or documented by any one currently working on
it.

Furthermore, as we analyzed it, we learned that the questionable code
really served no purpose in the current system; rather, it was there
from previous attempts or approaches by long-gone developers. The
current staff, while very bright, was loath to modify or delete code
that they didn't write or didn't know the purpose of, for fear of
breaking something and not knowing why or how to fix it.

At this point, we began calling these blobs of code "lava," referring to
the fluid nature in which they originated as compared to the basaltlike
hardness and difficulty in removing it once it had solidified. Suddenly,
it dawned on us that we had identified a potential AntiPattern.

Nearly a year later, and after several more data-mining expeditions and
interface design efforts, we had encountered the same pattern so
frequently that we were routinely referring to Lava Flow throughout the
department.

![](https://sourcemaking.com/files/sm/images/antipatterns/img_29.jpg)

### General Form

The Lava Flow AntiPattern is commonly found in systems that originated
as research but ended up in production. It is characterized by the
lavalike "flows" of previous developmental versions strewn about the
code landscape, which have now hardened into a basaltlike, immovable,
generally useless mass of code that no one can remember much, if
anything, about.

This is the result of earlier (perhaps Jurassic) developmental times
when, while in a research mode, developers tried out several ways of
accomplishing things, typically in a rush to deliver some kind of
demonstration, thereby casting sound design practices to the winds and
sacrificing documentation.

> 
> 
> ``` 
> // This class was written by someone earlier (Alex?) to manager the indexing
> // or something (maybe). It's probably important. Don't delete. I don't think it's
> // used anywhere - at least not in the new MacroINdexer module which may
> // actually replace whatever this was used for.
> class
> IndexFrame
> extends
> Frame {
>   
> // IndexFrame constructor
> // ---------------------------
> public
> IndexFrame(
> String
> index_parameter_1)
> {
> // Note: need to add additional stuff here...
> super (str);
> }
> // ---------------------------
>                 
> ```

The result is several fragments of code, wayward variable classes, and
procedures that are not clearly related to the overall system. In fact,
these flows are often so complicated in appearance and spaghettilike
that they seem important, but no one can really explain what they do or
why they exist.

Sometimes, an old, gray-haired hermit developer can remember certain
details, but typically, everyone has decided to "leave well enough
alone" since the code in question "doesn't really cause any harm, and
might actually be critical, and we just don't have time to mess with
it."

Though it can be fun to dissect these flows and study their
anthropology, there is usually not enough time in the schedule for such
meanderings. Instead, developers usually take the expedient route and
neatly work around them.

This AntiPattern is, however, incredibly common in innovative design
shops where proof-of-concept or prototype code rapidly moves into
production. It is poor design, for several key reasons:

  - Lava Flows are expensive to analyze, verify, and test. All such
    effort is expended entirely in vain and is an absolute waste. In
    practice, verification and test are rarely possible.
  - Lava Flow code can be expensive to load into memory, wasting
    important resources and impacting performance.
  - As with many AntiPatterns, you lose many of the inherent advantages
    of an object-oriented design. In this case, you lose the ability to
    leverage modularization and reuse without further proliferating the
    Lava Flow globules.

### Symptoms And Consequences

  - Frequent unjustifiable variables and code fragments in the system.
  - Undocumented complex, important-looking functions, classes, or
    segments that don't clearly relate to the system architecture.
  - Very loose, "evolving" system architecture.
  - Whole blocks of commented-out code with no explanation or
    documentation.
  - Lots of "in flux" or "to be replaced" code areas.
  - Unused (dead) code, just left in.
  - Unused, inexplicable, or obsolete interfaces located in header
    files.
  - If existing Lava Flow code is not removed, it can continue to
    proliferate as code is reused in other areas.
  - If the process that leads to Lava Flow is not checked, there can be
    exponential growth as succeeding developers, too rushed or
    intimidated to analyze the original flows, continue to produce new,
    secondary flows as they try to work around the original ones, this
    compounds the problem.
  - As the flows compound and harden, it rapidly becomes impossible to
    document the code or understand its architecture enough to make
    improvements.

### Typical Causes

  - R\&D code placed into production without thought toward
    configuration management.
  - Uncontrolled distribution of unfinished code. Implementation of
    several trial approaches toward implementing some functionality.
  - Single-developer (lone wolf) written code.
  - Lack of configuration management or compliance with process
    management policies.
  - Lack of architecture, or non-architecture-driven development. This
    is especially prevalent with highly transient development teams.
  - Repetitive development process. Often, the goals of the software
    project are unclear or change repeatedly. To cope with the changes,
    the project must rework, backtrack, and develop prototypes. In
    response to demonstration deadlines, there is a tendency to make
    hasty changes to code on the fly to deal with immediate problems.
    The code is never cleaned up, leaving architectural consideration
    and documentation postponed indefinitely.
  - Architectural scars. Sometimes, architectural commitments that are
    made during requirements analysis are found not to work after some
    amount of development. The system architecture may be reconfigured,
    but these inline mistakes are seldom removed. It may not even be
    feasible to comment-out unnecessary code, especially in modern
    development environments where hundreds of individual files comprise
    the code of a system. "Who's going to look in all those files? Just
    link em in\!"

### Known Exceptions

Small-scale, throwaway prototypes in an R\&D environment are ideally
suited for implementing the Lava Flow AntiPattern. It is essential to
deliver rapidly, and the result is not required to be sustainable.

### Refactored Solution

There is only one sure-fire way to prevent the Lava Flow AntiPattern:
Ensure that sound architecture precedes production code development.
This architecture must be backed up by a configuration management
process that ensures architectural compliance and accommodates "mission
creep" (changing requirements).

If architectural consideration is shortchanged up front, ultimately,
code is developed that is not a part of the target architecture, and is
therefore redundant or dead. Over time, dead code becomes problematic
for analysis, testing, and revision.

In cases where Lava Flow already exists, the cure can be painful. An
important principle is to avoid architecture changes during active
development. In particular, this applies to computational architecture,
the software interfaces defining the systems integration solution.
Management must postpone development until a clear architecture has been
defined and disseminated to developers.

Defining the architecture may require one or more system discovery
activities. System discovery is required to locate the components that
are really used and necessary to the system. System discovery also
identifies those lines of code that can be safely deleted. This activity
is tedious; it can require the investigative skills of an experienced
software detective.

As suspected dead code is eliminated, bugs are introduced. When this
happens, resist the urge to immediately fix the symptoms without fully
understanding the cause of the error. Study the dependencies. This will
help you to better define the target architecture.

To avoid Lava Flow, it is important to establish system-level software
interfaces that are stable, well-defined, and clearly documented.
Investment up front in quality software interfaces can produce big
dividends in the long run compared to the cost of jackhammering away
hardened globules of Lava Flow code.

Tools such as the Source-Code Control System (SCCS) assist in
configuration management. SCCS is bundled with most Unix environments
and provides a basic capability to record histories of updates to
configuration-controlled files.

### Example

We recently participated in a data-mining expedition site where we
attempted to identify evolutionary interfaces that resulted from
preliminary interface architectures that we originated and were in the
process of updating.

The system we mined was targeted because the developers had utilized our
initial architecture in a unique way that fascinated us: Essentially,
they constructed a quasi-event service out of our generic
interapplication framework.

As we studied their system, we encountered large segments of code that
baffled us. These segments didn't seem to contribute to the overall
architecture that we had expected to find. They were somewhat incohesive
and only very sparsely documented, if at all.

When we asked the current developers about some of these segments, the
reply was, "Oh that? Well we're not using that approach anymore. Reggie
was trying something, but we came up with a better way. I guess some of
Reggie's other code may depend on that stuff though, so we didn't delete
anything." As we looked deeper into the matter, we learned that Reggie
was no longer even at the site, and hadn't been there for some time, so
the segments of code were several months old.

After two days of code examination, we realized that the majority of the
code that comprised the system was most likely similar to that code that
we already examined: completely Lava Flow in nature.

We gleaned very little that helped us articulate how their architecture
actually was constructed; therefore, it was nearly impossible to mine.
At this point, we essentially gave up trying to mine the code and
instead focused on the current developer's explanations of what was
"really" going on, hoping to somehow codify their work into interface
extensions that we could incorporate into our upcoming revisions to our
generic interapplication framework.

One solution was to isolate the single, key person who best understood
the system they had developed, and then to jointly write IDL with that
person. On the surface, the purpose of the IDL we were jointly writing
was to support a crisis demonstration that was weeks away.

By utilizing the Fire Drill Mini-AntiPattern, we were able to get the
systems developers to validate our IDL by using it to rapidly build a
CORBA wrapper for their product for the demonstration. Many people lost
a lot of sleep, but the demonstration went well. There was, of course,
one side effect to this solution: We ended up with the interface, in
IDL, which we had set out to discover in the first place.

### Related Solutions

In today's competitive world, it is often desirable to minimize the time
delay between R\&D and production. In many industries, this is critical
to a company's survival. Where this is the case, inoculation against
Lava Flow can sometimes be found in a customized
configuration-management (CM) process that puts certain limiting
controls in place at the prototyping stage, similar to "hooks" into a
real, production-class develop ment without the full restraining impact
on the experimental nature of R\&D.

Where possible, automation can play a big role here, but the key lies in
the customization of a quasi-CM process that can be readily scaled into
a full-blown CM control system once the product moves into a production
environment. The issue is one of balance between the costs of CM in
hampering the creative process and the cost of rapidly gaining CM
control of the development once that creative process has birthed
something useful and marketable.

This approach can be facilitated by periodic mapping of a prototyping
system into an updated system architecture, including limited, but
standardized inline documentation of the code.

### Applicability To Other Viewpoints And Scales

The architectural viewpoint plays a key role in preventing Lava Flows
initially. Managers can also play a role in early identification of Lava
Flows or the circumstances that can lead to Lava Flows. These managers
must also have the authority to put the brakes on when Lava Flow is
first identified, postponing further development until a clear
architecture can be defined and disseminated.

As with most AntiPatterns, prevention is always cheaper than correction,
so up-front investment in good architecture and team education can
typically ensure a project against this and most other AntiPatterns.
While this initial cost does not show immediate returns, it is certainly
a good investment.

## Ambiguous Viewpoint

### AntiPattern Problem

Object-oriented analysis and design (OOA\&D) models are often presented
without clarifying the viewpoint represented by the model. By default,
OOA\&D models denote an implementation viewpoint that is potentially the
least useful. Mixed viewpoints don't allow the fundamental separation of
interfaces from implementation details, which are one of the primary
benefits of the object-oriented paradigm.

![Ambiguous
Viewpoint](https://sourcemaking.com/files/sm/images/arrows.jpg)

### Refactored Solution

There are three fundamental viewpoints for OOA\&D models: the business
viewpoint, the specification viewpoint, and the implementation
viewpoint. The business viewpoint defines the user's model of the
information and processes. This is a model that domain experts can
defend and explain (commonly called an analysis model). Analysis models
are some of the most stable models of the information system and are
worthwhile to maintain.

Models can be less useful if they don't focus on the required
perspective(s). A perspective applies filters to the information. For
example, defining a class model for a telephone exchange system will
vary significantly depending upon the focus provided by the following
perspectives:

  - Telephone user, who cares about the ease of making calls and
    receiving itemized bills.
  - Telephone operator, who cares about connecting users to required
    numbers.
  - Telephone accounting department, which cares about the formulae for
    billing and records of all calls made by users.

Some of the same classes will be identified, but not many; where there
are, the methods will not be the same.

The specification viewpoint focuses on software interfaces. Because
objects (as abstract data types) are intended to hide implementation
details behind interfaces, the specification viewpoint defines the
exposed abstractions and behaviors in the object system. The
specification viewpoint defines the software boundaries between objects
in the system.

The implementation viewpoint defines the internal details of the
objects. Implementation models are often called design models in
practice. To be an accurate model of the software, design models must be
maintained continuously as the software is developed and modified. Since
an out-of-date model is useless, only selected design models are
pertinent to maintain; in particular, those design models that depict
complex aspects of the system.

## Functional Decomposition

  - **AntiPattern Name:** Functional Decomposition
  - **Also Known As:** No Object-Oriented AntiPattern "No OO"
  - **Most Frequent Scale:** Application
  - **Refactored Solution Name:** Object-Oriented Reengineering
  - **Refactored Solution Type:** Process
  - **Root Causes:** Avarice, Greed, Sloth
  - **Unbalanced Forces:** Management of Complexity, Change
  - **Anecdotal Evidence:** "This is our ‘main' routine, here in the
    class called LISTENER."

### Background

Functional Decomposition is good in a procedural programming
environment. It's even useful for understanding the modular nature of a
larger-scale application.

Unfortunately, it doesn't translate directly into a class hierarchy, and
this is where the problem begins. In defining this AntiPattern, the
authors started with Michael Akroyd's original thoughts on this topic.
We have reformatted it to fit in with our template, and extended it
somewhat with explanations and diagrams.

## General Form

This AntiPattern is the result of experienced, nonobject-oriented
developers who design and implement an application in an object-oriented
language. When developers are comfortable with a "main" routine that
calls numerous subroutines, they may tend to make every subroutine a
class, ignoring class hierarchy altogether (and pretty much ignoring
object orientation entirely).

The resulting code resembles a structural language such as Pascal or
FORTRAN in class structure. It can be incredibly complex, as smart
procedural developers devise very clever ways to replicate their
time-tested methods in an object-oriented architecture.

![](https://sourcemaking.com/files/sm/images/big.jpg)

You will most likely encounter this AntiPattern in a C shop that has
recently gone to C++, or has tried to incorporate CORBA interfaces, or
has just implemented some kind of object tool that is supposed to help
them. It's usually cheaper in the long run to spend the money on
object-oriented training or just hire new programmers who think in
objects.

### Symptoms And Consequences

  - Classes with "function" names such as Calculate\_Interest or
    Display\_Table may indicate the existence of this AntiPattern.
  - All class attributes are private and used only inside the class.
  - Classes with a single action such as a function.
  - An incredibly degenerate architecture that completely misses the
    point of object-oriented architecture.
  - Absolutely no leveraging of object-oriented principles such as
    inheritance and polymorphism. This can be extremely expensive to
    maintain (if it ever worked in the first place; but never
    underestimate the ingenuity of an old programmer who's slowly losing
    the race to technology).
  - No way to clearly document (or even explain) how the system works.
    Class models make absolutely no sense.
  - No hope of ever obtaining software reuse.
  - Frustration and hopelessness on the part of testers.

### Typical Causes

  - *Lack of object-oriented understanding.* The implementers didn't
    "get it." This is fairly common when developers switch from
    programming in a nonobject-oriented programming language to an
    object-oriented programming language. Because there are
    architecture, design, and implementation paradigm changes,
    object-orientation can take up to three years for a company to fully
    achieve.
  - *Lack of architecture enforcement.* When the implementers are
    clueless about object orientation, it doesn't matter how well the
    architecture has been designed; they simply won't understand what
    they're doing. And without the right supervision, they will usually
    find a way to fudge something using the techniques they do know.
  - *Specified disaster.* Sometimes, those who generate specifications
    and requirements don't necessarily have real experience with
    object-oriented systems. If the system they specify makes
    architectural commitments prior to requirements analysis, it can and
    often does lead to AntiPatterns such as Functional Decomposition.

### Known Exceptions

The Functional Decomposition AntiPattern is fine when an object-oriented
solution is not required. This exception can be extended to deal with
solutions that are purely functional in nature but wrapped to provide an
object-oriented interface to the implementation code.

### Refactored Solution

If it is still possible to ascertain what the basic requirements are for
the software, define an analysis model for the software, to explain the
critical features of the software from the user's point of view. This is
essential for discovering the underlying motivation for many of the
software constructs in a particular code base, which have been lost over
time. For all of the steps in the Functional Decomposition AntiPattern
solution, provide detailed documentation of the processes used as the
basis for future maintenance efforts.

Next, formulate a design model that incorporates the essential pieces of
the existing system. Do not focus on improving the model but on
establishing a basis for explaining as much of the system as possible.

Ideally, the design model will justify, or at least rationalize, most of
the software modules. Developing a design model for an existing code
base is enlightening; it provides insight as to how the overall system
fits together. It is reasonable to expect that several parts of the
system exist for reasons no longer known and for which no reasonable
speculation can be attempted.

For classes that fall outside of the design model, use the following
guidelines:

1.  If the class has a single method, try to better model it as part of
    an existing class. Frequently, classes designed as helper classes to
    another class are better off being combined into the base class they
    assist.
2.  Attempt to combine several classes into a new class that satisfies a
    design objective. The goal is to consolidate the functionality of
    several types into a single class that captures a broader domain
    concept than the previous finer-grained classes. For example, rather
    than have classes to manage device access, to filter information to
    and from the devices, and to control the device, combine them into a
    single device controller object with methods that perform the
    activities previously spread out among several classes.
3.  If the class does not contain state information of any kind,
    consider rewriting it as a function. Potentially, some parts of the
    system may be best modeled as functions that can be accessed
    throughout various parts of the system without restriction.

Examine the design and find similar subsystems. These are reuse
candidates. As part of program maintenance, engage in refactoring of the
code base to reuse code between similar subsystems (see the Spaghetti
Code solution for a detailed description of software refactoring).

### Example

Functional Decomposition is based upon discrete functions for the
purpose of data manipulation, for example, the use of Jackson Structured
Programming. Functions are often methods within an object-oriented
environment. The partitioning of functions is based upon a different
paradigm, which leads to a different grouping of functions and
associated data.

The simple example in figure below shows a functional version of a
customer loan scenario:

![](https://sourcemaking.com/files/v2/content/antipatterns/Functional%20Decomposition%20-%201-2x.png)

1.  Adding a new customer.
2.  Updating a customer address.
3.  Calculating a loan to a customer.
4.  Calculating the interest on a loan.
5.  Calculating a payment schedule for a customer loan.
6.  Altering a payment schedule.

Next figure then shows the object-oriented view of a customer loan
application. The previous functions map to object methods.

![](https://sourcemaking.com/files/v2/content/antipatterns/Functional%20Decomposition%20-%202-2x.png)

### Related Solutions

If too much work has already been invested in a system plagued by
Functional Decomposition, you may be able to salvage things by taking an
approach similar to the alternative approach addressed in the Blob
AntiPattern.

Instead of a bottom-up refactoring of the whole class hierarchy, you may
be able to extend the "main routine" class to a "coordinator" class that
manages all or most of the system's functionality.

Function classes can then be "massaged" into quasi-object-oriented
classes by combining them and beefing them up to carry out some of their
own processing at the direction of the modified "coordinator" class.
This process may result in a class hierarchy that is more workable

### Applicability To Other Viewpoints And Scales

Both architectural and managerial viewpoints play key roles in either
initial prevention or ongoing policing against the Functional
Decomposition AntiPattern. If a correct object-oriented architecture was
initially planned and the problem occurred in the development stages,
then it is a management challenge to enforce the initial architecture.

Likewise, if the cause was a general lack of incorrect architecture
initially, then it is still a management challenge to recognize this,
put the brakes on, and get architectural help—the sooner the cheaper.

## Poltergeists

  - **AntiPattern Name:** Poltergeists
  - **Also Known As:** Gypsy , Proliferation of Classes , and Big DoIt
    Controller Class
  - **Most Frequent Scale:** Application
  - **Refactored Solution Name:** Ghostbusting
  - **Refactored Solution Type:** Process
  - **Root Causes:** Sloth, Ignorance
  - **Unbalanced Force:** Management of Functionality, Complexity
  - **Anecdotal Evidence:** "I'm not exactly sure what this class does,
    but it sure is important\!"

### Background

When Michael Akroyd presented the Gypsy AntiPattern at Object World West
in 1996, he likened the transient appearance and then discrete vanishing
of the gypsy class to a "Gypsy

Wagon" that is there one day and gone the next. As we studied Akroyd's
model, we wanted to convey more of the Gypsy's invoking function in the
overall AntiPattern name. Thus, we felt that since poltergeists
represent "restless ghosts" that cause "bump-in-the-night types of
phenomena," that term better represented the "pop in to make something
happen" concept of this AntiPattern while retaining the "here now then
suddenly vanished" flavor of the initial Gypsy name.

![](https://sourcemaking.com/files/v2/content/antipatterns/poltergeist-2x.png)

In the LISP language, as in many others, certain pure-evil programmers
exist who take great glee in leveraging the "side effects" of certain
language functions to mysteriously perform key functionality in their
systems. Analysis and understanding of such systems is virtually
impossible, and any attempt at reuse is considered insane.

Like the Poltergeist "controller" class, the use of "side effects" to
accomplish any principle task in an implementation is an incorrect
utilization of the language or architecture tool, and should be avoided.

### General Form

Poltergeists are classes with limited responsibilities and roles to play
in the system; therefore, their effective life cycle is quite brief.
Poltergeists clutter software designs, creating unnecessary
abstractions; they are excessively complex, hard to understand, and hard
to maintain.

This AntiPattern is typical in cases where designers familiar with
process modeling but new to object-oriented design define architectures.
In this AntiPattern, it is possible to identify one or more ghostlike
apparition classes that appear only briefly to initiate some action in
another more permanent class. Akroyd calls these classes "Gypsy Wagons"
Typically, Gypsy Wagons are invented as controller classes that exist
only to invoke methods of other classes, usually in a predetermined
sequence. They are usually obvious because their names are often
suffixed by \_manager or \_controller.

The Poltergeist AntiPattern is usually intentional on the part of some
greenhorn architect who doesn't really understand the object-oriented
concept. Poltergeist classes constitute bad design artifacts for three
key reasons:

1.  They are unnecessary, so they waste resources every time they
    "appear."
2.  They are inefficient because they utilize several redundant
    navigation paths.
3.  They get in the way of proper object-oriented design by needlessly
    cluttering the object model.

### Symptoms And Consequences

  - Redundant navigation paths.
  - Transient associations.
  - Stateless classes.
  - Temporary, short-duration objects and classes.
  - Single-operation classes that exist only to "seed" or "invoke" other
    classes through temporary associations.
  - Classes with "control-like" operation names such as
    start\_process\_alpha.

### Typical Causes

  - *Lack of object-oriented architecture.* "The designers don't know
    object orientation."
  - *Incorrect tool for the job.* Contrary to popular opinion, the
    object-oriented approach isn't necessarily the right solution for
    every job. As a poster once read, "There is no right way to do the
    wrong thing." That is to say, if object orientation isn't the right
    tool, there's no right way to implement it.
  - *Specified disaster.* As in the Blob, management sometimes makes
    architectural committments during requirements analysis. This is
    inappropriate, and often leads to problems like this AntiPattern.

### Known Exceptions

There are no exceptions to the Poltergeists AntiPattern.

### Refactored Solution

Ghostbusters solve Poltergeists by removing them from the class
hierarchy altogether. After their removal, however, the functionality
that was "provided" by the poltergeist must be replaced. This is easy
with a simple adjustment to correct the architecture.

The key is to move the controlling actions initially encapsulated in the
Poltergeist into the related classes that they invoked. This is
explained in detail in the next section.

### Example

In order to more clearly explain the Poltergeist, consider the
peach-canning example in figure below. We see that the class
PEACH\_CANNER\_CONTROLLER is a Poltergeist because:

![](https://sourcemaking.com/files/v2/content/antipatterns/Poltergeist%20-%201-2x.png)

  - It has redundant navigation paths to all other classes in the
    system.
  - All of its associations are transient.
  - It has no state.
  - It is a temporary, short-duration class that pops into existence
    only to invoke other classes through temporary associations.

In this example, if we remove the Poltergeist class, the remaining
classes lose the ability to interact. There is no longer any ordering of
processes. Thus, we need to place such interaction capability into the
remaining hierarchy. Notice that certain operations are added to each
process such that the individual classes interact and process results.

![](https://sourcemaking.com/files/v2/content/antipatterns/Poltergeist%20-%202-2x.png)

### Related Solutions

The "80% solution" discussed in the Blob AntiPattern results in
something that looks very similar to a Poltergeist. The "coordinator"
class presented still manages all or most of the system's functionality
and typically exhibits many of the features of a Poltergeist.

### Applicability To Other Viewpoints And Scales

Occurs when developers are designing a system as they implement it
(typically by the seat of their pants\!) although certainly it may come
as a result of failure to properly architect a system. Whether this
presents evidence that Poltergeists are really a case of failed
management is left to the reader.

As with most development AntiPatterns, both architectural and managerial
viewpoints play key roles in initial prevention and ongoing policing
against them. It's through an architectural viewpoint that an emerging
AntiPattern is often recognized, and through effective management that
it is properly addressed when not prevented outright.

Managers should take great care to ensure that object-oriented
architectures are evaluated by qualified object-oriented architects as
early as possible and then on an ongoing basis to prevent novice-induced
errors such as this AntiPattern. Pay the price for good architecture up
front\!

## Boat Anchor

A Boat Anchor is a piece of software or hardware that serves no useful
purpose on the current project. Often, the Boat Anchor is a costly
acquisition, which makes the purchase even more ironic.

The reasons for acquiring a Boat Anchor are usually compelling at the
time. For example, a policy or programmatic relationship may require the
purchase and usage of a particular piece of hardware or software. This
is a starting assumption (or constraint) of the software project.
Another compelling reason is when a key manager is convinced of the
utility of the acquisition.

A sales practice called "very important person (VIP) marketing" targets
the sales pitch at senior decision makers who have buying authority. VIP
marketing often focuses on chief executive officers of small- to
medium-size corporations. A commitment to the product is made without
proper technical evaluation.

![](https://sourcemaking.com/files/sm/images/anchor.jpg)

The consequences for managers and software developers are that
significant effort may have to be devoted to making the product work.

After a significant investment of time and resources, the technical
staff realizes that the product is useless in the current context, and
abandons it for another technical approach. Eventually, the Boat Anchor
is set aside and gathers dust in some corner (if it's hardware).

### Refactored Solution

Good engineering practice includes the provision for technical backup,
an alternative approach that can be instituted with minimal software
rework. The selection of technical backup is an important
risk-mitigation strategy.  
  
Technical backups should be identified for most infrastructure
technologies (upon which most software depends), and for other
technologies in high-risk areas. Technical backups should be evaluated
along with critical-path technologies in the selection process.
Prototyping with evaluation licenses (available from most vendors) is
recommended for both critical-path and back-up technologies.

### Related AntiPatterns

Rational decision making is explained in the solution to the Irrational
Management AntiPattern. Rational decision making can be used as an
objective technology selection process to identify Boat Anchors prior to
acquisition. The solution to the Smoke and Mirrors AntiPattern describes
the practices for prepurchase technology evaluation, including review of
product documentation and train-before-you-buy.

## Golden Hammer

  - **AntiPattern Name:** Golden Hammer
  - **Also Known As:** Old Yeller, Head-in-the sand
  - **Most Applicable Scale:** Application
  - **Refactored Solution Name:** Expand your horizons
  - **Refactored Solution Type:** Process
  - **Root Causes:** Ignorance, Pride, Narrow-Mindedness
  - **Unbalanced Forces:** Management of Technology Transfer
  - **Anecdotal Evidence:** "I have a hammer and everything else is a
    nail." "Our database is our architecture." "Maybe we shouldn't have
    used Excel macros for this job after all."

### Background

This is one of the most common AntiPatterns in the industry. Frequently,
a vendor, specifically a database vendor, will advocate using its
growing product suite as a solution to most of the needs of an
organization. Given the initial expense of adopting a specific database
solution, such a vendor often provides extensions to the technology that
are proven to work well with its deployed products at greatly reduced
prices.

### General Form

A software development team has gained a high level of competence in a
particular solution or vendor product, referred to here as the Golden
Hammer. As a result, every new product or development effort is viewed
as something that is best solved with it. In many cases, the Golden
Hammer is a mismatch for the problem, but minimal effort is devoted to
exploring alternative solutions.

This AntiPattern results in the misapplication of a favored tool or
concept. Developers and managers are comfortable with an existing
approach and unwilling to learn and apply one that is better suited.
This is typified by the common "our database is our architecture"
mind-set, particularly common in the world's banking community.

![](https://sourcemaking.com/files/sm/images/hammer.jpg)

Frequently, an advocate will propose the Golden Hammer and its
associated product suite as a solution to most of the needs of an
organization. Given the initial expense of adopting a specific solution,
Golden Hammer advocates will argue that future extensions to the
technology, which are designed to work with their existing products,
will minimize risk and cost.

### Symptoms And Consequences

  - Identical tools and products are used for wide array of conceptually
    diverse products.
  - Solutions have inferior performance, scalability, and so on when
    compared to other solutions in the industry.
  - System architecture is best described by a particular product,
    application suite, or vendor tool set.
  - Developers debate system requirements with system analysts and end
    users, frequently advocating requirements that are easily
    accommodated by a particular tool and steering them away from areas
    where the adopted tool is insufficient.
  - Developers become isolated from the industry. They demonstrate a
    lack of knowledge and experience with alternative approaches.
  - Requirements are not fully met, in an attempt to leverage existing
    investment.
  - Existing products dictate design and system architecture.
  - New development relies heavily on a specific vendor product or
    technology.

### Typical Causes

  - Several successes have used a particular approach.
  - Large investment has been made in training and/or gaining experience
    in a product or technology.
  - Group is isolated from industry, other companies.
  - Reliance on proprietary product features that aren't readily
    available in other industry products.
  - "Corncob" proposing the solution (see Corncob AntiPattern).

### Known Exceptions

The Golden Hammer AntiPattern sometimes works:

1.  If the product that defines the architectural constraints is the
    intended strategic solution for the long term; for example, using an
    Oracle database for persistent storage and wrapped stored procedures
    for secure access to data.
2.  If the product is part of a vendor suite that provides for most of
    the software needs.

### Refactored Solution

This solution involves a philosophical aspect as well as a change in the
development process. Philosophically, an organization needs to develop a
commitment to an exploration of new technologies.

Without such a commitment, the lurking danger of overreliance on a
specific technology or vendor tool set exists. This solution requires a
two-pronged approach: A greater commitment by management in the
professional development of their developers, along with a development
strategy that requires explicit software boundaries to enable technology
migration.

Software systems need to be designed and developed with well-defined
boundaries that facilitate the replaceability of individual software
components. A component should insulate the system from proprietary
features in its implementation.

If the system is developed using explicit software boundaries, the
interfaces that make up the boundaries become points at which the
software used in the implementation may be replaced with a new
implementation, without affecting the other components in the system. An
industry standard, such as the OMG IDL specification, is an invaluable
tool for incorporating rigid software boundaries between components.

In addition, software developers need to be up to date on technology
trends, both within the organization's domain and in the software
industry at large. This can be accomplished through several activities
that encourage the interchange of technical ideas. For example,
developers can establish groups to discuss technical developments
(design patterns, emerging standards, new products) that may impact the
organization in the future.

They can also form book study clubs to track and discuss new
publications that describe innovative approaches to software
development. In practice, we have found the book study club paradigm to
be a very effective way to exchange ideas and new approaches.

Even without full management buyin, developers can establish informal
networks of technology-minded people to investigate and track new
technologies and solutions. Industry conferences are also a great way to
contact people and vendors and stay informed as to where the industries
are headed and what new solutions are available to developers.

On the management side, another useful step is to adopt a commitment to
open systems and architectures. Without it, developers often acquire the
attitude that achieving short-term results by any means necessary is
acceptable. Though this may be desirable in the short term, future
results become problematic because rather than building upon a solid
foundation of past successes, effort is expended reworking past software
to conform to new challenges.

Flexible, reusable code requires an investment in its initial
development, otherwise long-term benefits will not be achieved Also, the
danger of overreliance on a specific technology or vendor tool set is a
potential risk in the product or project development. In-house research
programs that develop proof-of-concept prototypes are effective for
testing the feasibility of incorporating less risky open technologies
into a development effort.

Another management-level way of eliminating or avoiding the Golden
Hammer AntiPattern is to encourage the hiring of people from different
areas and from different backgrounds. Teams benefit from having a
broader experience base to draw upon in developing solutions. Hiring a
database team whose members all have experience in using the same
database product greatly limits the likely solution space, in comparison
to a similar team whose experience encompasses a wide range of database
technology solutions.

Finally, management must actively invest in the professional development
of software developers, as well as reward developers who take initiative
in improving their own work.

### Variations

A common variation of Golden Hammer occurs when a developer uses a
favorite software concept obsessively. For example, some developers
learn one or two of the GoF patterns and apply them to all phases of
software analysis, design, and implementation.

Discussions about intent or purpose are insufficient to sway them from
recognizing the applicability of the design pattern's structure and
force-fitting its use throughout the entire development process.
Education and mentoring is required to help people become aware of other
available approaches to software system construction.

### Example

A common example of the Golden Hammer AntiPattern is a database-centric
environment with no additional architecture except that which is
provided by the database vendor. In such an environment, the use of a
particular database is assumed even before object-oriented analysis has
begun. As such, the software life cycle frequently begins with the
creation of an entity-relationship (E-R) diagram that is produced as a
requirements document with the customer.

This is frequently destructive, because the E-R diagram ultimately is
used to specify the database requirements; and detailing the structure
of a subsystem before understanding and modeling the system presumes
that the impact of the actual customer requirements on the system design
is minimal.

Requirements gathering should enable system developers to understand the
user needs to the extent that the external behavior of the solution
system is understood by the user as a black box Conceivably, many
systems are built to satisfy user requirements without utilizing a
database at all. However, with the Golden Hammer AntiPattern in force,
such possibilities are discounted up front, leading to every problem
incorporating a database element.

Over time, the organization may develop several database-centric
products that could have been implemented as independent systems. The
database evolves into the basis for interconnectivity between
applications, and it manages distribution and shared access to data. In
addition, many implementation problems are addressed through using
database proprietary features that commit future migrations to parallel
the development of a technology of the implementation database.

At some point, it may be necessary to interoperate with systems that
either do not share the same database-centric architecture or are
implemented using a different database that may not permit unrestricted
access to their information. Suddenly, development becomes extremely
expensive as unique, special-purpose connections are built to "bridge"
between unique systems. If, however, some thought is given to the
problem before the situation gets too far out of hand, a common
framework can be developed, where products chosen for particular areas
are selected based on standard interface specifications, such as CORBA,
DCOM, or TCP/IP.

Another example is an insurance company with several stovepipe legacy
systems that decided in its move to client/server that Microsoft Access
should be the key part of the solution for persistence. The entire front
end of the call-center system was architected around an early version of
this product. Thereafter, the system's future was fully constrained by
the development path of the database product because of a bad
architecture decision. Needless to say, the system lasted less than six
months.

### Related Solutions

  - *Lava Flow.* This AntiPattern results when the Golden Hammer
    AntiPattern is applied over the course of several years and many
    projects. Typically, older sections based on earlier versions of the
    Golden Hammer are delegated to remote, seldom-used parts of the
    overall application. Developers become reluctant to modify these
    sections, which build up over time and add to the overall size of
    the application while implementing functions that are seldom, if
    ever, used by the customer.
  - *Vendor Lock-In.* Vendor lock-in is when developers actively receive
    vendor support and encouragement in applying the Golden Hammer
    AntiPattern. A software project is actively committed to relying
    upon a single vendor's approach in designing and implementing an
    object-oriented system.

## Dead End

A Dead End is reached by modifying a reusable component, if the modified
component is no longer maintained and supported by the supplier. When
these modifications are made, the support burden transfers to the
application system developers and maintainers. Improvements in the
reusable component cannot be easily integrated, and support problems may
be blamed on the modification.

The supplier may be a commercial vendor, in which case this AntiPattern
is also known as Commercial off-the-shelf (COTS) Customization. When
subsequent releases of the product become available, the special
modifications will have to be made again, if possible. If fact, it may
not be possible to upgrade the customized component, for various reasons
such as cost and staff turnover.

The decision to modify a reusable component by a system's integrator is
often seen as a workaround for the vendor's product inadequacies. As a
short-term measure, this helps a product development progress, rather
than slow it down.

The longer-term support burden becomes untenable when trying to deal
with the future application versions and the "reusable component"
vendor's releases. The only time we saw this work was when the system's
integrator arranged with the reusable component vendor that the SI
modifications would be included in the next release of the vendor
product. It was pure luck that their objectives were the same.

### Refactored Solution

Avoid COTS Customization and modifications to reusable software.
Minimize the risk of a Dead End by using mainstream platforms and COTS
infrastructure, and upgrading according to the supplier's release
schedule.

When customization is unavoidable, use an isolation layer (see [Vendor
Lock-In](https://sourcemaking.com/antipatterns/vendor-lock-in)). Use
isolation layers and other techniques to separate dependencies from the
majority of the application software from customizations and proprietary
interfaces.

A Dead End may be an acceptable solution in testbeds that support basic
research such as throwaway code, and significant benefits are realized
through the customization.

## Spaghetti Code

  - **AntiPattern Name:** Spaghetti Code
  - **Most Applicable Scale:** Application
  - **Refactored Solution Name:** Software Refactoring, Code Cleanup
  - **Refactored Solution Type:** Software
  - **Root Causes:** Ignorance, Sloth
  - **Unbalanced Forces:** Management of Complexity, Change
  - **Anecdotal Evidence:** "Ugh\! What a mess\!" "You *do* realize that
    the language supports more than one function, right?" "It's easier
    to rewrite this code than to attempt to modify it." "Software
    engineers don't write spaghetti code." "The quality of your software
    structure is an investment for future modification and extension."

### Background

The Spaghetti Code AntiPattern is the classic and most famous
AntiPattern; it has existed in one form or another since the invention
of programming languages. Nonobject-oriented languages appear to be more
susceptible to this AntiPattern, but it is fairly common among
developers who have yet to fully master the advanced concepts underlying
object orientation.

![](https://sourcemaking.com/files/sm/images/spagett.jpg)

### General Form

Spaghetti Code appears as a program or system that contains very little
software structure. Coding and progressive extensions compromise the
software structure to such an extent that the structure lacks clarity,
even to the original developer, if he or she is away from the software
for any length of time.

If developed using an object-oriented language, the software may include
a small number of objects that contain methods with very large
implementations that invoke a single, multistage process flow.

Furthermore, the object methods are invoked in a very predictable
manner, and there is a negligible degree of dynamic interaction between
the objects in the system. The system is very difficult to maintain and
extend, and there is no opportunity to reuse the objects and modules in
other similar systems.

### Symptoms And Consequences

  - After code mining, only parts of object and methods seem suitable
    for reuse. Mining Spaghetti Code can often be a poor return on
    investment; this should be taken into account before a decision to
    mine is made.
  - Methods are very process-oriented; frequently, in fact, objects are
    named as processes.
  - The flow of execution is dictated by object implementation, not by
    the clients of the objects.
  - Minimal relationships exist between objects.
  - Many object methods have no parameters, and utilize class or global
    variables for processing.
  - The pattern of use of objects is very predictable.
  - Code is difficult to reuse, and when it is, it is often through
    cloning. In many cases, however, code is never considered for reuse.
  - Object-oriented talent from industry is difficult to retain.
  - Benefits of object orientation are lost; inheritance is not used to
    extend the system; polymorphism is not used.
  - Follow-on maintenance efforts contribute to the problem.
  - Software quickly reaches a point of diminishing returns; the effort
    involved in maintaining an existing code base is greater than the
    cost of developing a new solution from the ground up.

### Typical Causes

  - Inexperience with object-oriented design technologies.
  - No mentoring in place; ineffective code reviews.
  - No design prior to implementation.
  - Frequently the result of developers working in isolation.

### Known Exceptions

The Spaghetti Code AntiPattern is reasonably acceptable when the
interfaces are coherent and only the implementation is spaghetti. This
is somewhat like wrapping a nonobject-oriented piece of code. If the
lifetime of the component is short and cleanly isolated from the rest of
the system, then some amount of poor code may be tolerable.

The reality of the software industry is that software concerns usually
are subservient to business concerns, and, on occasion, business success
is contingent on delivering a software product as rapidly as possible.
If the domain is not familiar to the software architects and developers,
it may be better to develop products to gain an understanding of the
domain with the intention of designing products with an improved
architecture at some later date

### Refactored Solution

Software refactoring (or code cleanup) is an essential part of software
development Seventy percent or more of software cost is due to
extensions, so it is critical to maintain a coherent software structure
that supports extension.

When the structure becomes compromised through supporting unanticipated
requirements, the ability of the code to support extensions becomes
limited, and eventually, nonexistent. Unfortunately, the term "code
cleanup" does not appeal to pointy-haired managers, so it may be best to
discuss this issue using an alternative term such as "software
investment."

After all, in a very real sense, code cleanup is the maintenance of
software investment. Well-structured code will have a longer life cycle
and be better able to support changes in the business and underlying
technology.

Ideally, code cleanup should be a natural part of the development
process. As each feature (or group of features) is added to the code,
code cleanup should follow what restores or improves the code structure.
This can occur on an hourly or daily basis, depending on the frequency
of the addition of new features.

Code cleanup also supports performance enhancement. Typically,
performance optimization follows the 90/10 rule, where only 10 percent
of the code needs modification in order to achieve 90 percent of the
optimal performance. For single-subsystem or application programming,
performance optimization often involves compromises to code structure.

The first goal is to achieve a satisfactory structure; the second is to
determine by measurement where the performance-critical code exists; the
third is to carefully introduce necessary structure compromises to
enhance performance. It is sometimes necessary to reverse the
performance enhancement changes in software to provide for essential
system extensions. Such areas merit additional documentation, in order
to preserve the software structure in future releases.

### Kill Spaghetti Code AntiPattern through prevention

The best way to resolve the Spaghetti Code AntiPattern is through
prevention; that is, to think, then develop a plan of action before
writing. If, however, the code base has already degenerated to the point
that it is unmaintainable, and if reengineering the software is not an
option, there are still steps that can be taken to avoid compounding the
problem.

First, in the maintenance process, whenever new features are added to
the Spaghetti Code code base, do not modify the Spaghetti Code simply by
adding code in a similar style to minimally meet the new requirement.
Instead, always spend time refactoring the existing software into a more
maintainable form. Refactoring the software includes performing the
following operations on the existing code:

1.  Gain abstract access to member variables of a class using accessor
    functions. Write new and refactored code to use the accessor
    functions.
2.  Convert a code segment into a function that can be reused in future
    maintenance and refactoring efforts. It is vital to resist
    implementing the Cut-and-Paste AntiPattern. Instead, use the
    Cut-and-Paste *refactored* solution to repair prior implementations
    of the Cut-and-Paste AntiPattern.
3.  Reorder function arguments to achieve greater consistency throughout
    the code base. Even consistently bad Spaghetti Code is easier to
    maintain than inconsistent Spaghetti Code.
4.  Remove portions of the code that may become, or are already,
    inaccessible. Repeated failure to identify and remove obsolete
    portions of code is one of the major contributors to the Lava Flow
    AntiPattern.
5.  Rename classes, functions, or data types to conform to an enterprise
    or industry standard and/or maintainable entity. Most software tools
    provide support for global renaming.

In short, commit to actively refactoring and improving Spaghetti Code to
as great an extent as resources allow whenever the code base needs to be
modified. It's extremely useful to apply unit and system testing tools
and applications to ascertain that refactoring does not immediately
introduce any new defects into the code base.

Empirical evidence suggests that the benefits of refactoring the
software greatly outweigh the risk that the extra modifications may
generate new defects.

#### Other prevention methods

If prevention of Spaghetti Code is an option, or if you have the luxury
of fully engineering a Spaghetti Code application, the following
preventative measures may be taken:

1.  Insist on a proper object-oriented analysis process to create the
    domain model, regardless of how well the domain is understood. It is
    crucial that any moderate-or large-size project develop a domain
    model as the basis of design and development.
    
    If the domain is fully understood to the point that a domain model
    is not needed, counter with "If that's true, then the time to
    develop one would be negligible." If it actually is, then politely
    admit you were mistaken. Otherwise, the time that it takes justifies
    how badly it was needed.

2.  After developing a domain model that explains the system
    requirements and the range of variability that must be addressed,
    develop a separate design model.
    
    Though it is valid to use the domain model as a starting point for
    design, the domain model must be maintained as such in order to
    retain useful information that would otherwise be lost if permitted
    to evolve directly into a design model. The purpose of the design
    model is to extract the commonality between domain objects and
    abstract in order to clarify the necessary objects and relationships
    in the system.
    
    Properly performed, it establishes the bounds for software
    implementation. Implementation should be performed only in order to
    satisfy system requirements, either explicitly indicated by the
    domain model or anticipated by the system architect or senior
    developers.

3.  In the development of the design model, it is important to ensure
    that objects are decomposed to a level where they are fully
    understood by developers. It is the developers, not the designers,
    who must believe the software modules are easy to implement.

4.  Once a first pass has been made at both the domain and design model,
    begin implementation based upon the plan established by the design.
    The design does not have to be complete; the goal is that the
    implementation of software components should always be according to
    some predefined plan.
    
    Once development begins, proceed to incrementally examine other
    parts of the domain model and design other parts of the system. Over
    time, the domain model and the design model will be refined to
    accommodate discoveries in the requirements gathering, design
    decisions, and to cope with implementation issues.
    
    Again, Spaghetti Code is far less likely to occur if there is an
    overall software process in which the requirements and design are
    specified in advance of the implementation, instead of occurring
    concurrently.

#### Example

This is a frequent problem demonstrated by people new to object-oriented
development, who map system requirements directly to functions, using
objects as a place to group related functions. Each function contains an
entire process flow that completely implements a particular task.

For example, the code segment that follows contains functions such as
initMenus(), getConnection(), and executeQuery(), which completely
execute the specified operation. Each object method contains a single
process flow that performs all of the steps in sequence needed to
perform the task.

The object retains little or no state information between successive
invocations; rather, the class variables are temporary storage locations
to handle intermediate results of a single process flow.

#### Related Solutions

  - *Analysis Paralysis.* This AntiPattern is the result of taking the
    solution to its logical extreme. Rather than developing code ad hoc
    without a design to guide the overall structure of the code,
    Analysis Paralysis produces a detailed design without ever reaching
    a point at which implementation can commence.
  - *Lava Flow.* This AntiPattern frequently contains several examples
    of Spaghetti Code that discourage the refactoring of the existing
    code base. With Lava Flow, the code base had a logical purpose at
    some point in its life cycle, but portions became obsolescent, yet
    remained as part of the code base.

## Input Kludge

Software that fails straightforward behavioral tests may be an example
of an Input Kludge, which occurs when ad hoc algorithms are employed for
handling program input.

For example, if the program accepts free text input from the user, an ad
hoc algorithm will mishandle many combinations of legal and illegal
input strings. The anecdotal evidence for an Input Kludge goes like
this: "End users can break new programs within moments of touching the
keyboard."

![](https://sourcemaking.com/files/sm/images/input.jpg)

### Refactored Solution

For nondemonstration software, use production-quality input algorithms.
For example, lexical analysis and parsing software is readily available
as freeware. Programs such as *lex* and *yacc* enable robust handling of
text comprised of regular expressions and context-free language
grammars. Employing these technologies for production-quality software
is recommended to ensure proper handling of unexpected inputs.

### Variation

Many software defects arise due to unexpected combinations of
user-accesible features. Employing a *feature matrix* is recommended for
sophisticated applications with graphical user interfaces.

A feature matrix is state information in the program used to enable and
disable features prior to user actions. When the user invokes a feature,
the feature matrix indicates which other features must be disabled in
order to avoid conflicts. For example, a feature matrix is often used to
highlight and unhighlight menu commands prior to displaying the menu.

### Background

Programmers are trained to avoid input combinations that cause program
and system crashes. In a hands-on training course on OpenDoc, we used a
preliminary alpha release of the technology that was not yet
sufficiently robust for production-quality development. In other words,
it was easy to crash the entire operating system with seemingly correct
sequences of input commands and mouse operations.

The students spent the first day experiencing numerous system crashes
and waiting for system reboot. After attending the "crashing labs," we
wondered whether the release was robust enough to enable any kind of
sophisticated software development. By the end of the week, we had
learned to work around the limitations and perform programming tasks and
input operations that went well beyond our expectations formed the first
day. We had internalized the input sequences that avoided system
crashes.

## Walking Through a Minefield

Using today's software technology is analogous to walking through a
high-technology mine field. This mini-AntiPattern is also known as
Nothing Works or Do You Believe in Magic?

Numerous bugs occur in released software products; in fact, experts
estimate that original source code contains two to five bugs per line of
code. This means that the code will require two or more changes per line
to remove all defects. Without question, many products are released well
before they are ready to support operational systems. A knowledgeable
software engineer states that, "There are no real systems, not even
ours."

![](https://sourcemaking.com/files/sm/images/antipatterns/img_37.jpg)

The location and consequences of software defects are unrelated to their
apparent causes, and even a minor bug can be catastrophic. For example,
operating systems (UNIX, Windows, etc.) contain many known and unknown
security defects that make them vulnerable to attack; furthermore, the
Internet has dramatically increased the likelihood of system attack.

End users encounter software bugs frequently. For example, approximately
one in seven correctly dialed telephone numbers is not completed by the
telephone system (a software-intensive application). And note, the rate
of complaint is low compared to the frequency of software failures.

The purpose of commercial software testing is to limit risk, in
particular, support costs For shrink-wrapped software products, each
time an end user contacts a vendor for technical support, most or all of
the profit margin is spent answering the call.

With simpler systems of the past, we were lucky. When a software bug
occurred, the likely outcome was that nothing happened. With today's
systems, including computer-controlled passenger trains and spacecraft
control systems, the outcome of a bug can be catastrophic. Already,
there have been half a dozen major software failures where financial
losses exceeded $100 million.

### Refactored Solution

Proper investment in software testing is required to make systems
relatively bug-free. In some progressive companies, the size of testing
staff exceeds programming staff The most important change to make to
testing procedures is configuration control of test cases.

A typical system can require five times as much test-case software as
production software. Test software is often more complex than production
software because it involves the explicit management of execution timing
to detect many bugs.

When test software detects a bug, it is more likely to be the result of
a bug in the test than in the code being tested. Configuration control
enables the management of test software assets; for example, to support
regression testing.

Other effective approaches for testing include automation of test
execution and test design. Manual test execution is labor-intensive, and
there is no proven basis for the effectiveness of manual testing.

In contrast, automatic test execution enables running tests in concert
with the build cycle. Regression tests can be executed without manual
intervention, ensuring that software modifications do not cause defects
in previously tested behaviors. Test design automation supports the
generation of rigorous test suites, and dozens of good tools are
available to support test design automation.

### Variations

Formal verification is used in a number of applications to ensure an
error-free design Formal verification involves prov-ing (in a
mathematical sense) the satisfaction of requirements. Unfortunately,
computer scientists trained to perform this form of analysis are
relatively rare. In addition, the results of formal analysis are
expensive to generate and may be subjective. Consequently, in general,
we do not recommend this approach as feasible for most organizations.

Software inspection is an alternative approach that has been shown to be
effective in a wide range of organizations Software inspection is a
formal process for review of code and documentation products.

It involves careful review of software documentation in search of
defects; for example, it is recommended that each inspector search for
approximately 45 minutes per page of documentation. The defects
discovered by multiple inspectors are then listed during an inspection
logging meeting.

The document editor can remove defects for subsequent review by the
inspection team. Quality criteria are established for initial acceptance
of the document by the inspection team and completion of the inspection
process. Software inspection is a particularly useful process because it
can be applied at any phase of development, from the writing of initial
requirements documents through coding.

### Background

"Do you believe in magic?" is a question sometimes posed by savvy
computer professionals. If you believe that today's software systems are
robust, you certainly do believe in magic.

The reality of today's software technology is analogous to an intriguing
short story in Stephen Gaskin's *Mind at Play* In the story, people are
driving shiny new cars and living comfortable lives. However, there is
one man who wants to see the world as it really exists. He approaches an
authority figure who can remove all illusions from his perception.

Then, when he looks at the world, he sees people walking in the streets
pretending to be driving fancy cars. In other words, the luxurious
lifestyles were phony. In the end, the man recants, and asks to be
returned to his prior state of disillusionment.

In one view, today's technology is very much like the Gaskin story. It
is easy to believe that we are using mature software technologies on
powerful, robust platforms. In fact, this is an illusion; software bugs
are pervasive, and there are no robust platforms underneath.

## Cut-and-Paste Programming

  - **AntiPattern Name:** Cut-and-Paste Programming
  - **Also Known As:** Clipboard Coding, Software Cloning, Software
    Propagation
  - **Most Applicable Scale:** Application
  - **Refactored Solution Name:** Black Box Reuse
  - **Refactored Solution Type:** Software
  - **Root Causes:** Sloth
  - **Unbalanced Forces:** Management of Resources, Technology Transfer
  - **Anecdotal Evidence:** "Hey, I thought you fixed that bug already,
    so why is it doing this again?" "Man, you guys work fast. Over
    400,000 lines of code in three weeks is outstanding progress\!"

### Background

Cut-and-Paste Programming is a very common, but degenerate form of
software reuse which creates maintenance nightmares. It comes from the
notion that it's easier to modify existing software than program from
scratch. This is usually true and represents good software instincts.
However, the technique can be easily over used.

### General Form

This AntiPattern is identified by the presence of several similar
segments of code interspersed throughout the software project. Usually,
the project contains many programmers who are learning how to develop
software by following the examples of more experienced developers.

However, they are learning by modifying code that has been proven to
work in similar situations, and potentially customizing it to support
new data types or slightly customized behavior. This creates code
duplication, which may have positive short-term consequences such as
boosting line count metrics, which may be used in performance
evaluations.

Furthermore, it's easy to extend the code as the developer has full
control over the code used in his or her application and can quickly
meet short-term modifications to satisfy new requirements.

### Symptoms And Consequences

  - The same software bug reoccurs throughout software despite many
    local fixes.
  - Lines of code increase without adding to overall productivity.
  - Code reviews and inspections are needlessly extended.
  - It becomes difficult to locate and fix all instances of a particular
    mistake.
  - Code is considered self-documenting.
  - Code can be reused with a minimum of effort.
  - This AntiPattern leads to excessive software maintenance costs.
  - Software defects are replicated through the system.
  - Reusable assets are not converted into an easily reusable and
    documented form.
  - Developers create multiple unique fixes for bugs with no method of
    resolving the variations into a standard fix.
  - Cut-and-Paste Programming form of reuse deceptively inflates the
    number of lines of code developed without the expected reduction in
    maintenance costs associated with other forms of reuse.

### Typical Causes

  - It takes a great deal of effort to create reusable code, and
    organization emphasizes short-term payoff more than long-term
    investment.
  - The context or intent behind a software module is not preserved
    along with the code.
  - The organization does not advocate or reward reusable components,
    and development speed overshadows all other evaluation factors.
  - There is a lack of abstraction among developers, often accompanied
    by a poor understanding of inheritance, composition, and other
    development strategies.
  - The organization insists that code must be a perfect match to the
    new task to allow it to be reused. Code is duplicated to address
    perceived inadequacies in meeting what is thought to be a unique
    problem set.
  - Reusable components, once created, are not sufficiently documented
    or made readily available to developers.
  - A "not-invented-here" syndrome is in operation in the development
    environment.
  - There is a lack of forethought or forward thinking among the
    development teams.
  - Cut-and-Paste AntiPattern is likely to occur when people are
    unfamiliar with new technology or tools; as a result, they take a
    working example and modify it, adapting it to their specific needs.

### Known Exceptions

The Cut-and-Paste Programming AntiPattern is acceptable when the sole
aim is to get the code out of the door as quickly as possible. However,
the price paid is one of increased maintenance.

### Refactored Solution

Cloning frequently occurs in environments where white-box reuse is the
predominant form of system extension. In white-box reuse, developers
extend systems primarily though inheritance. Certainly, inheritance is
an essential part of object-oriented development, but it has several
drawbacks in large systems.

First, subclassing and extending an object requires some knowledge of
how the object is implemented, such as the intended constraints and
patterns of use indicated by the inherited base classes. Most
object-oriented languages impose very few restrictions, types of
extensions can be implemented in a derived class and lead to nonoptimal
use of subclassing.

In addition, typically, white-box reuse is possible only at application
compile time (for compiled languages), as all subclasses must be fully
defined before an application is generated.

On the other hand, black-box reuse has a different set of advantages and
limitations and is frequently a better option for object extension in
moderate and large systems. With black-box reuse, an object is used
as-is, through its specified interface. The client is not allowed to
alter how the object interface is implemented.

The key benefit of black-box reuse is that, with the support of tools,
such as interface definition languages, the implementation of an object
can be made independent of the object's interface. This enables a
developer to take advantage of late binding by mapping an interface to a
specific implementation at run time. Clients can be written to a static
object interface yet benefit over time by more advanced services that
support the identical object interface.

Of course, the drawback is that the supported services are limited to
those supported by the same interface. Changes to the interface
typically must be made at compile time, similar to interface or
implementation changes in white-box reuse.

The distinction between white-box and black-box reuse mirrors the
difference between object-oriented programming (OOP) and
component-oriented programming (COP), where the white-box subclassing is
the traditional signature of OOP and the dynamic late binding of
interface to implementation is a staple in COP.

Restructuring software to reduce or eliminate cloning requires modifying
code to emphasize black-box reuse of duplicated software segments. In
the case where Cut-and-Paste Programming has been used extensively
throughout the lifetime of a software project, the most effective method
of recovering your investment is to refactor the code base into reusable
libraries or components that focus on black-box reuse of functionality.

If performed as a single project, this refactoring process is typically
difficult, long, and costly, and requires a strong system architect to
oversee and execute the process and to mediate discussions on the merits
and limitations of the various extended versions of software modules.

Effective refactoring to eliminate multiple versions involves three
stages: code mining, refactoring, and configuration management. Code
mining is the systematic identification of multiple versions of the same
software segment. The refactoring process involves developing a standard
version of the code segment and reinserting it into the code base.

Configuration management is a set of policies drawn up to aid in the
prevention of future occurrences of Cut-and-Paste Programming. For the
most part, this requires monitoring and detection policies (code
inspections, reviews, validation), in addition to educational efforts.
Management buy-in is essential to ensure funding and support throughout
all three stages.

### Example

There is one piece of code that we suspect has been cloned repeatedly
throughout several organizations and probably is still cloned today.
This piece of code has been observed several hundred times across dozens
of organizations. It is a code file that implements a linked-list class
without the use of templates or macros.

Instead, the data structure stored by the linked list is defined in a
header file, so each linked list is customized to operate only on the
specified data structure. Unfortunately, the original author of the code
(rumor has it he was originally a LISP programmer) introduced a flaw in
the linked-list code: It failed to free the memory of an item when it
was deleted; instead, it just rearranged the pointers.

On occasion, this code has been modified to fix this defect; however,
more often than not, it still exists. It's clearly the same code set;
the variable names, the instructions, and even the formatting is exactly
the same in each and every case. Even the file is typically named
\<prefix\>link.c, where the prefix is one or two letters that
cryptically refer to the data structure managed by the list.

### Related Solutions

Spaghetti Code often contains several instances of the Cut-and-Paste
Programming AntiPattern. Because Spaghetti Code is not structured for
easy component reuse, in many cases, Cut-and-Paste Programming is the
only means available for reusing existing segments of code.

Of course, this leads to unnecessary code bloat and a maintenance
nightmare, but empirical evidence suggests that Spaghetti Code without
Cut-and-Paste Programming is typically an even worse mess than instances
that make use of Cut-and-Paste Programming.

Cloning can be minimized in new development through the implementation
of a software reuse process or organization Some degree of cloning is
inevitable in large software development; however, when it occurs, there
must be a formalized process for merging clones into a common baseline

## Mushroom Management

Also known as Pseudo-Analysis and Blind Development, Mushroom Management
is often described by this phrase: "Keep your developers in the dark and
feed them fertilizer."

An experienced system architect recently stated, "Never let software
developers talk to end users." Furthermore, without end-user
participation, "The risk is that you end up building the wrong system."

![](https://sourcemaking.com/files/sm/images/dev.jpg)

In some architecture and management circles, there is an explicit policy
to isolate system developers from the system's end users. Requirements
are passed second-hand through intermediaries, including architects,
managers, or requirements analysts. Mushroom Management assumes that
requirements are well understood by both end users and the software
project at project inception. It is assumed that requirements are
stable.

There are several mistaken assumptions in Mushroom Management:

  - In reality, requirements change frequently and drive about 30
    percent of development cost. In a Mushroom Management project, these
    changes are not discovered until system delivery. User acceptance is
    always a significant risk, which becomes critical in Mushroom
    Management.
  - The implications of requirements documents are rarely understood by
    end users, who can more easily visualize the meaning of requirements
    when they experience a prototype user interface. The prototype
    enables end users to articulate their real needs in contrast to the
    prototype's characteristics.
  - When developers don't understand the overall requirements of a
    product, they rarely understand the required component interaction
    and necessary interfaces. Because of this, poor design decisions are
    made and often result in stovepipe components with weak interfaces
    that do not fulfill the functional requirements.

Mushroom Management affects developers by creating an environment of
uncertainty. Often, the documented requirements are not sufficiently
detailed, and there is no effective way to obtain clarification.

In order to do their job, developers must make assumptions, which may
lead to pseudo-analysis, that is, object-oriented analysis that takes
place without end-user participation. Some Mushroom Management projects
eliminate analysis altogether and proceed directly from high-level
requirements to design and coding.

## Refactored Solution

Risk-driven development is a spiral development process based upon
prototyping and user feedback. Risk-driven development is a
specialization of iterative-incremental development process (see the
Analysis Paralysis AntiPattern). In this case, every increment is an
external iteration.

In other words, every project increment includes extensions to
user-interface functionality. The increment includes a user-interface
experiment, including hands-on experience. The experiment assesses the
acceptability and usability of each extension, and the results of the
experiment influence the direction of the project through the selection
of the next iteration.

Because the project frequently assesses user acceptance, and uses this
input to influence the software, the risk of user rejection is
minimized.

Risk-driven development is most applicable to applications, which are
user-interface-intensive and require relatively simple infrastructure
support. Personal computer applications that depend upon local files for
storage infrastructure are strong candidates for risk-driven
development.

## Variations

Including a domain expert on the development team is a very effective
way to have domain input on project decisions. Whenever there is a
domain-specific question, team members have expertise on-hand. An
important risk in this approach, however, is that the domain expert
represents only one opinion from the domain community.

References

  - [Source Making -
    antipatterns](https://sourcemaking.com/antipatterns)

</div>

</div>

<div id="footer" role="contentinfo">

<div class="section footer-body">

</div>

</div>
