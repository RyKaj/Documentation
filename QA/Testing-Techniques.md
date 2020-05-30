###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Quality Assurance (QA)](https://github.com/RyKaj/Documentation/tree/master/QA/README.md) |
------------


# Quality Assurance (QA) : Testing Techniques


## Alpha Testing

Alpha testing is a type of testing in which users are invited to the
development center where the software is being built.  The developers
note the actions that a user takes during this testing. Any deviation of
the system from normal behavior is noted and the developers rectify all
the issues found within the system.

Alpha testing is carried out just before beta testing and after the
[acceptance testing](https://reqtest.com/testing-blog/ultimate-guide-to-user-acceptance-testing/)
is done.  In-house members of the software company who are not part of
the project team do the alpha testing. These alpha testers are usually
developers and quality assurance team members from other project teams.

<kbd>![Alpha Testing](https://reqtest.com/wp-content/uploads/2019/07/Alpha-Testing-Basics-big.png)</kbd>

### Two phases of alpha testing:

**Phase 1**

In the first phase, software engineers do the testing. They use debugger
software to improve the process. The main aim is to find all the bugs as
quickly as possible.

**Phase 2**

Quality assurance team conducts the second phase of this testing. This
phase includes the black box as well as [white box
testing](https://reqtest.com/testing-blog/white-box-testing-example/).

The main purpose of doing alpha testing is to discover bugs that escaped
the previous tests. Alpha testing help to detect and fix bugs that exist
in the system just before releasing it for beta testing.

### Advantages

Here are the advantages of doing alpha testing:

  - This testing gives you an insight into the quality of the software
    at an early stage.
  - It helps to uncover bugs that can pose a serious threat.
  - During this testing, the real-time behavior of the users and the
    environment is imitated.
  - It helps to deliver good quality software for [beta testing](https://reqtest.com/testing-blog/beta-testing-tutorial/).

## Beta Testing

In Beta Testing, the software is distributed as a beta version to a
limited set of users outside the company. This helps to get the software
tested by end-users in a real environment. These users are called beta
testers; they test the software in a real-world scenario. They provide
feedback to the developers to help them fix any issues before the
software is released to the market.

The beta testers check and validate the functionality, usability,
reliability, security, and compatibility of the software. Beta Testing
helps to ensure there is a lesser number of faults and bugs in the
software. Beta testing helps to increase end-user satisfaction from the
software.

<kbd>![what is beta testing](https://reqtest.com/wp-content/uploads/2019/07/Beta-Testing-Tutorial-big.jpg)</kbd>

During pre-release, the software is already extensively tested by the QA
team and verified by the [Quality Analyst](https://reqtest.com/testing-blog/qa-analyst/). The testing in a
live environment from the user perspective is still missing. Beta
testing is used for pre-release testing of the software.

Professional testers often fail to test the real user’s interaction with
the software in the testing phase. Real users are different from
professional testers. Users can uncover more bugs and defects in the
software after its release in the market. It is expensive to resolve the
bugs after the release. It is suggested to address the potential error
in the software before the release of the product.

It focuses on pre-release testing to ensure quality and customer
satisfaction of the software.

It helps to check the real-world compatibility of the software as it is
checked on various platforms and for a wide range of devices, OS, and
browsers.

There are specific platforms where the software code breaks as the
platform wasn’t covered in the testing phase. Beta testing helps to fix
and improve the product to be fit and compatible with all possible
platforms.

The problems are identified at the end-user level; the problems that
impact the user experience. Beta testing helps to reduce business risk
due to customer dissatisfaction.

Beta testing is of two types open and closed beta. The products have to
go through these two tests based on numbers of beta users.

**Open beta:** This beta testing has a large group of people and
interested individuals as beta testers. They report bugs and also
provide feedback and suggestion on additional features that software
should include in the released version.

**Closed beta:** This beta testing has a selected group of people on an
invitation-only basis as beta testers.

### How to develop a Beta Testing strategy?

The beta testing strategy must include:
  - The business objectives of the software
  - The schedule for the entire phases of beta testing, cycles, duration of each cycle.
  - Test Plan
  - Testing approach to be followed by participants
  - Use of tools to measure productivity, feedback, & rating
  - Rewards and incentives to the participants
  - How to end the beta testing phase

### How to write a Beta Test Plan?

A beta test plan can be created in various ways based on the depth of
the testing product.

The test plan contains the following attributes:

**Objective**: It defines the objective of the project to help beta
testers understand the outcome and the reason for beta testing even
after extensive internal testing.

**Scope**: It defines the areas to cover in testing and which are not to
test areas in the software. It also provides data to be used for
testing.

**Test approach**: It includes the focus areas and the parameters
against which software is tested such as functionality, user experience,
and responsiveness. It also provides information on how to log bugs with
proof, a screenshot or a video. A [bug tracking tool with screen capture](https://reqtest.com/features/capture-screenshot-tool/) can ease
off logging defects as it streamlines the process.

**Schedule**: It defines the timeline of the product, its start and end
date with time, number of cycles and time of the cycle.

**Tools:** It includes which tools will be used for bug tracking.

**Budget:** Creating an incentive plan for beta testers based on the
allocated budget.

**Feedback:**  Collecting and gathering feedback and evaluating the
software

**Review:** The entry and exit criteria for beta testing

**Entry**

  - Beta testing starts right after [Alpha testing](https://reqtest.com/testing-blog/alpha-testing-basics/).
  - Product’s beta version is ready to be tested.
  - User manuals are ready and published containing all the list of
    known issues.
  - Maintaining a log of bugs, feedback using a tool which can help in
    documentation as well.

**Exit**

  - No critical bugs on desired platforms
  - Bugs identified are fixed
  - Summary report of the testing
  - Signing off beta testing

### Advantages

  - The software is tested by the end-users before releasing it in the
    market. It allows the development team to know what end users like
    in the software.
  - Customers can easily test software at their end to provide feedback.
  - Beta testers detect bugs and issues which were missed by the testing
    team which ensures high performance.
  - High quality of the software is released to the market.
  - Early users generate interest before the launch of the software.
  - It is a [cost-effective method to detect errors](https://reqtest.com/testing-blog/how-to-reduce-the-cost-of-bugs/).

## Blackbox Testing

The black box is a powerful technique to check the application under
test from the user’s perspective. Black box testing is used to test the
system against external factors responsible for software failures. This
testing approach focuses on the input that goes into the software, and
the output that is produced. The testing team does not cover the inside
details such as code, server logic, and development method.

Black box testing is based on the requirements and checks the system to
validate against predefined requirements.

Various parameters checked in black box testing are:

  - Accurate actions performed by users
  - System’s interaction with the inputs
  - The response time of the system
  - Use of data structures Issues in the user interface
  - Usability issues
  - Performance issues
  - Abrupt application failure, unable to start or finish

<kbd>![](https://reqtest.com/wp-content/uploads/2019/08/black-box-testing-big.png)</kbd>

### Boundary Value Analysis

It is the widely used black-box testing, which is also the basis for
equivalence testing. Boundary value analysis tests the software with
test cases with extreme values of test data. BVA is used to identify the
flaws or errors that arise due to the limits of input data.

For example: Taking inputs for a test case data for an age section
should accept a valid data of anything between 1-100. According to BVP
analysis, the software will be tested against four test data as -1, 1,
100, and 101 to check the system’s response using the boundary values.

### Equivalence partitioning

This test case designing techniques checks the input and output by
dividing the input into equivalent classes. The data must be tested at
least once to ensure maximum test coverage of data. It is the exhaustive
form of testing, which also reduces the redundancy of inputs.

For example: Taking inputs for a test case data for the example
mentioned above will have three classes from which one data will be
tested.

Valid class: 1 to 100 (any number), Invalid class: -1 (checking the
lowest of lowest), Invalid class: 101(highest of highest).

### State Transition Testing

This testing technique uses the inputs, outputs, and the state of the
system during the testing phase. It checks the software against the
sequence of transitions or events among the test data.

Based on the type of software that is tested, it checks for the
behavioral changes of a system in a particular state or another state
while maintaining the same inputs.

For example, A login page will let you input username and password until
three attempts. Each incorrect password will be sent the user to the
login page. After the third attempt, the user will be sent to an error
page. This state transition method considers the various states of the
system and the inputs to pass only the right sequence of the testing.

### Decision Table Testing

This approach creates test cases based on various possibilities. It
considers multiple test cases in a [decision table](https://reqtest.com/requirements-blog/a-guide-to-using-decision-tables/)
format where each condition is checked and fulfilled, to pass the test
and provide accurate output. It is preferred in case of various input
combinations and multiple possibilities.

For example, A food delivery application will check various payment
modes as input to place the order — decision making based on the table.

Case1: If the end-user has a card, then the system will not check for
cash or coupon and will take action to place the order.

Case2: If the end-user has a coupon will not be checked for a card or
cash and action will be taken.

Case3: if the end-user has cash, the action will be taken.

Case4: If the end-user doesn’t have anything, then action will not be
taken.

### Graph-Based Testing

It is similar to a decision-based test case design approach where the
relationship between links and input cases are considered.

### **Error Guessing Technique**

This method of designing test cases is about guessing the output and
input to fix any errors that might be present in the system. It depends
on the skills and judgment of the tester.

Comparison testing

This method uses the two different versions of the same software to
compare and validate the results.

## Exploratory Testing

This process of testing software gives complete freedom to the tester to
set guidelines and process to test the software.

This is a creative form of testing where a tester’s competency, skills,
and comprehension is used to explore the software. It is a continuous
process which uncovers defects.

Let’s take an example to understand exploratory testing. An e-commerce
portal is under development and the final rounds of testing are going
on. There is a new payment option “e-wallet” added into the payment
section of the portal.

The test manager has a high-level plan to perform exploratory testing.
He asks a tester who has thoroughly tested the payment gateway earlier
to perform exploratory testing on the new payment option. The tester
from his previous experience of what could possibly go wrong in the
payment option, test the new e-wallet option thoroughly.

<kbd>![](https://reqtest.com/wp-content/uploads/2019/06/Exploratory-Testing-big.png)</kbd>

The tester records his testing session through a [screen capture tool](https://reqtest.com/features/capture-screenshot-tool/). He reports
a bug with a video screen capture of the bug to the developer. The
developer is able to reproduce the bug with the help of the video with
voice over attached in the bug reported.

Here we cover three critical aspects of exploratory testing first there
is a high-level plan to perform the testing and to be able to track what
should be covered in the tests. Secondly, the tester uses his own
competency and past experience to test the application as per his own
knowledge of the software under test. Thirdly, a tool was used for
effectively performing exploratory testing.

### Benefits

Here are the benefits of performing exploratory testing:

#### Quick Testing

Exploratory testing works well when you have a time crunch which stops
you from writing detailed test cases to define the testing process. You
can start exploring the software and provide feedback quickly.

#### Rapid feedback 

The exploratory testing process helps in getting quick feedback from
stakeholders as well even before the application is released. Explorers
can deal with any critical situation as they have in-depth knowledge of
software gained through previous iterations of testing. Exploratory
testing helps to refine the functionality and enhances the overall
software reliability. It reduces the risk of leaving any critical
defects at the last point of software release.

#### Supports Agile 

It blends well with [agile methodology](https://reqtest.com/agile-blog/agile-methodology-tutorial/)
and DevOps. It can sustain changes in requir

### Can be performed in five stages

#### 1- Classification Of Bugs

  - It includes grouping the standard type of bugs as done in the
    previous projects.
  - Searching the root cause of the problem or issue.
  - Finding new ideas to check the application with risk analysis.

#### 2- Creating A Test Charter 

Test charter is a statement document of exploratory testing which
defines the goal of the test session.

It explains three vital points:

  - What to test
  - How to test
  - What factors should be considered

The charter also describes the starting point of testing and defines how
the end user will use the system.

#### 3- Creating A Time Box 

A time box is a time frame which sets the time limit of the testing
session. It has a start date and time with end date and time.

  - The method includes testers to be working together for e.g., 90 minutes.
  - Nobody should interrupt them in those 90 minutes session.

The idea behind keeping the time box is to keep tester work to a decided
timeline.

#### 4- Results 

  - It involves finding and reporting defects
  - Analysis and learning from testing
  - Analysis of coverage areas

#### 5- Examining Results

  - It works on compiling the output results
  - Evaluating results with the charter
  - Checking any need of any additional testing
  - Analyze results before taking decisions related to quality and risk

### The Right Approach to Exploratory Testing

There are three different approaches to perform and evaluate any
software using exploratory Testing.

#### 1\. Scenario-based Exploratory Testing

This type of exploratory testing is based on a particular scenario or
functionality which is tested. A tester can explore and find defects for
different structures and situations using this technique. The tester can
come up with a different test scenario to cover various situations.

#### 2\. Strategy Based Exploratory Testing

The strategy based testing is defined by various other factors such as
risk evaluation, equivalence technique, and [boundary value technique](https://reqtest.com/testing-blog/what-is-boundary-value-analysis-and-equivalence-partitioning/).
The tester implements multiple procedures to check and improve the
efficiency of the application under test.

#### 3\. Freestyle Exploratory Testing

As the name suggests this type of testing that doesn’t have a defined
structure. It is implemented when the tester has to perform smoke
testing. It lacks approach, a scenario like other forms of testing. A
tester has to explore the entire website or application to find defects
without any structured plan.

## Greybox Testing

For the uninitiated, Grey Box testing refers to the (apparent)
*Amalgamation* of White Box and Black Box testing.

[**White Box testing**](https://reqtest.com/testing-blog/white-box-testing-example/)
gives the tester a clear view of how the system ‘hangs together’ – that
is, how the various components and subsystems integrate and share
information. The tester is therefore able to look for and test specific
functionality and scenarios to give the system a good shake.

> *“Grey Box Testing Brings The Principles Of Both White Box And Black Box Testing Together.”*

**Black Box testing** is necessarily a situation where the tester
understands the needs the system is required to meet, and the Input and
Output requirements. And goes about testing these, while being oblivious
to the internal workings of the system.

Black Box testing can be seen as a means to test the basic functionality
that a system or software product is expected to fulfil, and should be
good enough to move a product to the next phase of development if you
are in iterative development mode.

White Box testing will help you test for the exceptional scenarios,
catch those difficult to catch bugs and help get the product ready for
release.

Grey Box Testing brings the principles of both White Box and Black Box
testing together. It refers to situations where the tester is only
exposed to intricate details about specific system components and
functionality that they are required to test and validate, while the
rest of the system can remain a Black box. It can at times refer to
situations where your **primary focus is in catching bugs with one or a
few system components**, and not necessarily the rest.

In simple terms,

**Grey Box Testing = White Box Testing + Black Box Testing**

Grey Box Testers generally have **access to design documents,
architecture diagrams** and other supporting information to give them an
idea of the internal workings of a system or system component.

### Why is Grey Box Testing important?

  - Testing happens from the point of view of the user – i.e., the
    consumer of your product. This is one of the benefits of Black box
    testing and carries over to Grey box testing.
  - Testing *Also* happens from the point of view of the developer –
    with some characteristics of White Box testing still intact, the
    Tester is able to see the system from the vantage point used by the
    one that designed it, and uncover more – sometimes uncommon but
    potentially very embarrassing – bugs.
  - Combined with other Testing efforts in a project, Grey Box testing
    comes in quite handy when you’re trying to clean up code. Like my
    example demonstrated above, you don’t know when an unseemly bug
    could rear up its head.
  - **Two brains are better than one**. Especially when those of a
    developer *And* a tester come together to catch bugs. That is the
    benefit Grey Box testing provides – by allowing the tester use the
    system design documents to design Test cases.
  - Fundamental benefit – this is Black box and White box testing
    combined into one. Need I say more?

## GUI Testing

Graphical User-interface Testing or GUI testing is a process of testing
the user interface of an application. In this article, you will learn
about the basics of GUI testing and how to do GUI testing and its
benefits.

A graphical user interface includes all the elements such as menus,
checkbox, buttons, colors, fonts, sizes, icons, content, and images. GUI
testing is done to check the functionality and usability of design
elements as a user for an application under test.

## Why do you need GUI testing?

Modern applications are beyond the desktop they are either mobile based
or cloud-based applications. They need to be more user-friendly as per
customer demand. The application interface and user experience play a
significant role in application success as it is released to the market.
A GUI testing team always pays close attention to each detail in visual
dynamics to ensure end-user satisfaction and ease.

<kbd>![GUI testing](https://reqtest.com/wp-content/uploads/2019/05/UI-testing-big.png)</kbd>

It tests the various aspects of the user interface, such as:

  - Visual Design
  - Functionality
  - Security
  - Compliance
  - Usability
  - Performance

### Benefits of using GUI testing are:

  - It releases an error-free application software
  - It increases the efficiency of software
  - Improves software quality

### What we check in GUI Testing?

It extensively checks the user-interface of the application under test.

  - Testing the size, position, height, width of the visual elements
  - Verifying and testing the error messages are displayed or not
  - Testing different sections of the display screen
  - Verifying the usability of carousel arrows
  - Checking the navigation elements at the top of the page
  - Checking the message displayed, frequency and content
  - Verifying the functionality of proper filters and ability to
    retrieve results.
  - Checking alignment of radio buttons, drop downs
  - Verifying the title of each section and their correctness
  - Cross-checking the colors and its synchronization with the theme

GUI Testing Approaches

There are three approaches to GUI testing:

#### Manual Testing

This approach involves human tester, where each screen is manually
checked to validate each functionality by creating and [executing test cases](https://reqtest.com/testing-blog/test-management-planning-execution/).
It is a useful approach when part of UI or a feature is ready, the
probability of defects is more at the initial stage, and human
intervention is required.

It is convenient to use where the UI is unstable and go through a lot of
changes. It is viable for quick checks which can be done at any moment.
Moreover, [manual testing requires expertise](https://reqtest.com/testing-blog/manual-testing-strategy/)
and skills to validate design elements which are not possible without a
human tester.

#### Record and Replay Testing

GUI record and replay tools are used to test applications for their user
interface. Using such tools, testers run an application and record the
user interaction with the app. A script runs to track and save the user
actions, including cursor movements, which can be replayed several times
to find the issues in the interface.

It also supports [automated regression testing](https://reqtest.com/testing-blog/regression-testing-types-techniques-tools/).
It is can be used for cross-browser testing. It is a convenient and
lightweight solution for testing. It doesn’t work well where you have
lots of iterations in the GUI of the applications. Recapturing and
replaying test cases to check functionality is time-consuming, and
tracking their updated version is a cumbersome process.

#### Model-based testing

In this type of GUI testing, a model is created to understand and
evaluate the system’s behavior. This approach is useful in 
[creating accurate test cases](https://reqtest.com/tutorials/how-to-create-test-cases-in-reqtest/)
using system requirements. It is a structured, thorough, measurable form
of testing.

There are three essential aspects of model-based GUI testing:

  - Automatically generated test cases from the model
  - Manually derived test cases from the model
  - Model and requirements coverage metrics

There are tools which could automatically generate test based on the
model.

Things to consider for model-based testing:

  - Create the model
  - Determine the information as inputs in the system
  - Verifying the expected output
  - Execute tests
  - Checking and validating actual vs. expected
  - Take further action on the model

You can even derive test cases for GUI in two ways:

Charts: The charts display the state of the system and check the state
after some input.

Decision Tables: This helps in deciding the results for each input

Model-Based testing is preferred as the technique aligns with
requirements which define even the undesirable states a GUI can attain.

An automated test case generator produces test cases to cover all the
paths between start to finish stage. The number of test cases generated
automatically is large and it requires a lot of time to execute.

You need to implement a test case selection algorithm to reject all
inadequate scenarios for test cases. It means you need a test case
filter to select the required test cases as the set is too big and will
consume more time.

The above problem has one solution, opting for a manual approach to
finalize test cases. The process can be integrated with the automatic
generation of test scripts after tester manually shortlist the test
cases.

So if we conclude saying model-based testing makes GUI testing easy then
yes it does. Only when it is used for a well-designed process where it
is easy to generate a test set by performing dummy testing and running
test cases. But it is not appropriate where a test set consumes a lot of
time in execution. Efforts are required in building a model and short
listing the test cases using an algorithm and test script generation,
which makes it expensive.

## Whitebox Testing

This being a refresher of sorts, let us begin by defining the technique.

White box testing refers to a scenario where (as opposed to 
[**black box testing**](https://en.wikipedia.org/wiki/Black-box_testing) ), the
tester deeply understands the inner workings of the system or system
component being tested.

Gaining a deep understanding of the system or component is possible when
the tester understands these at program- or code-level. So almost all
the time, the tester needs to either understand or have access to the
source code that makes up the system – usually in the form of
specification documents.

Armed with the level of technical detail that is normally visible only
to a developer, a Tester will then be able to design and execute test
cases that cover all possible scenarios and conditions that the system
component is designed to handle.

We’ll see how this is done in our example later.

By performing testing at the most granular level of the system, you are
able to build a robust system that works exactly as expected, and ensure
it will not throw up any surprises whatsoever.

The key principles that assist you in executing white box tests
successfully are:

  - **Statement Coverage** – ensure every single line of code is tested.
  - **Branch Coverage** – ensure every branch (e.g. true or false) is tested.
  - **Path Coverage** – ensure all possible paths are tested.

And we know path coverage is favoured above branch coverage for the
sheer comprehensiveness it provides.

### When is White Box Testing appropriate?

You know by now, that such intensive testing is not for everyone or
every situation.

The rigour that white box Testing employs is quite useful – yes, but not
all the time.

white box Testing is usually reserved for mission critical systems and
components, because, well, such systems simply deserve the attention to
detail that this technique can bring.

> “The rigour that white box Testing employs is quite useful – yes, but not all the time.”

#### Mission Critical

By mission critical, we mean for instance the Core Banking system that
provides the IT backbone to operate a Bank. The core banking system will
house all transactions and corresponding customer data, and helps run
the bank day-to-day.

Another example could be IT systems that help governments-run defence
operations.

Any system that provides such critical utility to a company,
organisation or government needs to be bug-free. **Any level of bugs or
downtime is unacceptable for such systems**, as they perform extremely
vital functions for the stakeholders involved.

It could quite literally mean a difference between life and death if
such systems do not work as expected:

  - Customers could be cut off from accessing their money when in life
    changing situations – say when they’re trying to pay for a loved
    one’s emergency treatment at a hospital.
  - An entire country’s security could be compromised by a malfunctioning IT system.

So where critical systems and components are involved, it is necessary
to ensure they are bug-free (well, almost). And making a mission
critical system bug-free in turn depends on employing extensive testing.

White box testing isn’t the be-all and end-all for critical systems
quality assurance. It is, however, **one of the central and
indispensable techniques**.

### Why is White Box Testing indispensable?

Simply because of what it is designed to do – i.e., test all possible
scenarios that a system can encounter. By testing at the source
code-level, a tester will be able to run through every single
permutation and combination that the program can theoretically spew out.

When testing happens at such granular level, this then brings any
possible defects out in the open. And your team will have an opportunity
to evaluate whether some or all of them need to be fixed.

### Step-by-Step White Box Testing Example

With that, let’s sink our teeth into a simple example of white box
testing. For this purpose, let’s consider the following sample journey:

A customer needs to transfer money to a friend who lives abroad. They’re
going to use the mobile banking service provided by their bank to do
this.

#### Step 1: Identify the feature, component, program to be tested

Zero in on what you want to test.

When it comes to white box testing, the smaller your target system
component, the better it is. Given what we’re trying to achieve – test
all possible scenarios and cases for a given feature – individually
testing individual features helps you focus on a small enough area of
the code.

A narrower focus also implies the ability to be more thorough. Remember,
in a lot of the cases, you’re doing white box testing mainly because
that specific system, feature, component is critical and needs to be
tested through and through **to guarantee it works as expected** .

> “A narrower focus also implies the ability to be more thorough.”

So, you should try and identify the smallest logical module or component
for the system being tested, and work on this first. When you’re
finished testing this module, you can move on to the next one.

**Taking on a larger scope**

Yes – it is possible that you’d take on white box testing for entire
systems. Where the system involved is critical, draping it in white box
testing will give you a high degree of confidence about code quality and
resilience.

However, you need to weigh the effort involved versus the benefits
derived. white box Testing is often labour intensive and will consume
considerable resource. So it is important to balance effort with need.

> “White box Testing is often labour intensive and will consume considerable resource. So it is important to balance effort with need.”

#### Step 2: Plot all possible paths in a flowgraph

This step covers a big portion of your preparation to plan and execute
white box Testing successfully.

As with any effort – be it development or testing – understanding
‘Scope’ is paramount.

And, we already know that Path Coverage provides a comprehensive
solution to Test coverage.

Here, we’re trying to understand all the possible paths that can be
tested for a given feature, component, module… Identifying all possible
paths helps in writing test cases to cover each one of them. And the
best way to do this, is to draw a flowgraph that brings out these paths.

Consider the example below:

<kbd>![Sample Journey Flowchart](https://reqtest.com/wp-content/uploads/2017/02/Sample-Journey1.png)</kbd>

Obviously, transferring funds from your bank account isn’t this simple.
Sure, for some of us it can feel like it, but that’s because we don’t
normally face the exceptions that quite a few others encounter when
attempting to move money.

Having said that, this *Simple* flowgraph will do nicely to demonstrate
white box Testing.

To complete the flowgraph, you may need to refer to the following:

  - User journeys, use cases
  - Program specifications
  - Technical specifications, pseudocode

#### Step 3: Identify all possible paths from the flowgraph

Now, as you can see from Figure 1, there are two possible paths for this
journey:

1.  1, 2, 3, 5, 6, 7 and
2.  1, 2, 3, 4, 6, 7

Being a simple example, only two paths exist to this journey.
Nevertheless, you get the idea. Identify every permutation and
combination for how the journey could flow from start to end. Identify
any midway drop off points. And you’re all set.

#### Step 4: Write Test Cases to cover every single path on the flowgraph

When you have all available paths plotted on the flowgraph, then go
ahead and write test cases to test each of these paths.

When you have a bunch of test cases that you are confident will cover
every single path, you’re ready to go to the execution phase.

#### Step 5: Execute, rinse, repeat

You’re now ready to execute white box Testing for the identified system,
component or module. And you have the flowgraph and Test Cases necessary
to complete Testing.

That, in simple terms, is how you plan and execute white box Testing.

You can also refer to this blog, which does a good job of explaining how
to approach white box testing too.

## Testing Technique Comparison

### Alpha vs Beta Testing

[Alpha testing](https://reqtest.com/testing-blog/alpha-testing-basics/)
is in-house testing where a testing lab is set up for developers and
testers (who were not a part of the software development project team)
to test the application.

[Beta testing](https://reqtest.com/testing-blog/beta-testing-tutorial/)
is an approach to get feedback from a sample of users from outside the
company. This testing helps to get the application get tested in a real
environment.

<kbd>![Alpha vs beta testing](https://reqtest.com/wp-content/uploads/2019/08/Alpha-vs-beta-big.png)</kbd>


| Alpha Testing                                                                                                                            | Beta Testing                                                                                              |
| ---------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| This testing involves both [white box and black-box testing](https://reqtest.com/testing-blog/black-box-testing-vs-white-box-testing/) . | This testing only involves black box testing.                                                             |
| The employees of the software development company where the software is being built, conduct alpha testing.                              | External users who are not part of the software development company perform beta testing.                 |
| The alpha testing takes place at developers end.                                                                                         | The beta testing takes place at the users’ end and with the platform of their choice.                     |
| Reliability and security of the software are not covered in alpha testing.                                                               | In beta testing, the reliability, security, and robustness of the software are checked.                   |
| Alpha testing helps to test the quality of the software before passing the software for beta testing.                                    | Beta testing helps to evaluate the software whether it is ready to be released to the full market or not. |
| For alpha testing, a test lab is required with setting up the test environment.                                                          | In beta testing, there is no such requirement of the testing environment or lab set up.                   |
| The execution cycle of alpha testing may extend to a longer duration.                                                                    | Beta testing comparatively requires lesser time to execute.                                               |
| Developers can quickly address the issues or bugs found during alpha testing.                                                            | The issues found in beta testing are resolved in the future version of the software.                      |


## Blackbox vs Whitebox

  - **White-box testing** is important to catch defects at unit level
    early on during the development stage, preventing small problems
    from snowballing into catastrophic errors after the code has been
    integrated into the main system.

  - **Black-box testing**, on the other hand, ensures that all the
    different software modules work well at a system level after having
    been integrated together.

|                          | Blackbox Testing                                                                    | Whitebox Testeing                                                               |
| ------------------------ | ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| *Definition*             | Software testing method where the internal structure of the system is **not known** | Software testing method where the internal structure of the system is **known** |
| Use for                  | Verifying input methods and outputs of the system.                                  | Verifying internal structure of system’s components                             |
| Performed by             | Testers                                                                             | Developers                                                                      |
| Applicable To            | Systems and Acceptance testing                                                      | Unit testing                                                                    |
| Perspective              | User                                                                                | Developer                                                                       |
| Introspection            | No                                                                                  | Yes                                                                             |
| Coding Knowledge         | No                                                                                  | Yes                                                                             |
| Implementation Knowledge | No                                                                                  | Yes                                                                             |
| Test Cases               | Based on requirements                                                               | Based on detailed design                                                        |


## Usability

Usability Testing is a non-functional testing technique to evaluate how
easily the end users can use a product or a service.  The goal of
usability testing is to detect any usability problems by collecting
qualitative and quantitative data to determine the satisfaction of
representative users with the product.

This testing helps to gain insights from the users to find out whether
the users’ expectations are met or not.  It helps to check if the user
can perform the functionality offered by the product easily. The
reactions and feedback of representative users allow finding out that if
the product is on the right track.

Usability testing identifies the areas where the user struggle with the
product. It helps to make recommendations for improvements.  A
successful usability testing will result in improvement in the design of
the product.

The stakeholders and development team members watch, listen, collect
data and take notes during usability testing.  As this testing involves
real users, it provides insights on performance, error rate and task
success. Usability testing helps the developers and designers to develop
a solution that supports workflow and tasks.

<kbd>![usability testing big](https://reqtest.com/wp-content/uploads/2019/05/usability-testing-big.png)</kbd>

### When to do Usability Testing?

You can perform usability testing at various development stages:

#### Low fidelity prototype

A wireframe or a mock version of a product or website that allows
testing before the development starts.

####  High-fidelity prototype

An interactive system that includes representative data and imitates the
user experience the end users will get with the finished product.

#### Alpha and Beta versions

Remote participants for a usability test can access these versions.

####  Release version

A product released to customers that can help to test the workflow of
the product from beginning to end.

#### Comparative or A/B

There are multiple versions of a design that helps to measure the
difference in performance and satisfaction.

### Steps to perform usability testing

  - [Create a test plan](https://reqtest.com/testing-blog/how-to-write-a-test-plan-2/)
  - Facilitate the test
  - Analyze case data
  - Create a test report

#### Creating a test plan

The first step would be to [create a test plan that will help you to perform good](https://reqtest.com/testing-blog/software-test-plan-template-2/)
usability testing. Here are the tasks for creating a test plan:

#### Define the scope of work

You have to decide which areas of your product you want to test. Create
a list of all the areas and ensure to not go beyond 12 areas to test.

####  Recruit users

The next very critical step is to recruit users who will give you
insight into usability. Select the users on the basis of their
demographics or psychographics. Psychographics considers the cognitive
background that covers whether the selected users usually perform the
proposed scenarios or not.

You should recruit at least 5 users and a maximum of 15 users per user
persona. The 5 users per segment will give you enough insights on the
user behavior.

####  Identify objectives

You should have a clear picture of what you want to accomplish with the
usability test. You should also know what you want to 
[demonstrate to your stakeholders](https://reqtest.com/requirements-blog/how-to-identify-stakeholders/).

#### Establish metrics

For a fact-based description of the performance, you need metrics which
help you to make informed design decisions. The important metrics are
time on a task, task performance, success rate, speed, expectation
matching, and goal fulfillment. There could be many more metrics on the
basis of your project.

#### Facilitate the test

To facilitate the test you need to perform the following:

  - Ask your users about their thoughts and feeling as and when they interact with the solution
  - Take notes irrespective of whether they are structured or unstructured
  - Record the session
  - Let the user take the lead
  - Don’t make conclusions early on during the session
  - It’s important to know how your user perceives the solution

Usability testing gives the following results:

Quantitative information- Time on tasks, success and failure rates,
effort (\#clicks, perception of progress)

Qualitative information-Stress responses, subjective satisfaction,
perceived effort or difficulty

References

  - [Reqtest - Back box
    testing](https://reqtest.com/testing-blog/black-box-testing/)
  - [Reqtest - Alpha vs beta
    testing](https://reqtest.com/testing-blog/alpha-vs-beta-testing/)
  - [https://reqtest.com/testing-blog/white-box-testing-example](https://reqtest.com/testing-blog/white-box-testing-example/)
  - [https://reqtest.com/testing-blog/alpha-testing-basics](https://reqtest.com/testing-blog/alpha-testing-basics/)
  - [https://reqtest.com/testing-blog/beta-testing-tutorial](https://reqtest.com/testing-blog/beta-testing-tutorial/)
  - [https://reqtest.com/testing-blog/quick-guide-on-exploratory-testing](https://reqtest.com/testing-blog/quick-guide-on-exploratory-testing/)
  - [https://reqtest.com/testing-blog/gui-testing-tutorial](https://reqtest.com/testing-blog/gui-testing-tutorial/)
  - [https://reqtest.com/testing-blog/what-is-usability-testing](https://reqtest.com/testing-blog/what-is-usability-testing/)
  - [https://reqtest.com/testing-blog/grey-box-testing](https://reqtest.com/testing-blog/grey-box-testing/)

