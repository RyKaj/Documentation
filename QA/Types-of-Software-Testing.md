###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Quality Assurance (QA)](https://github.com/RyKaj/Documentation/tree/master/QA/README.md) |
------------

# Quality Assurance (QA) : Types of Software Testing


<kbd>![](https://www.guru99.com/images/1-2015/012715_0453_NonFunction4.png)</kbd>

## Functional Testing

Functional testing is a type of software testing whereby the system is tested against the functional requirements/specifications. Functions (or features) are tested by feeding them input and examining the output. Functional testing ensures that the requirements are properly satisfied by the application. The two most common (and mostly used at Pinnacle) are Scripted testing and Exploratory testing.

Functional Testing is defined as a type of testing which verifies that each  **function** of the software application operates in conformance with the requirement specification. This testing mainly involves black box testing and it is not concerned about the source code of the application.

Each and every functionality of the system is tested by providing appropriate input, verifying the output and comparing the actual results with the expected results.

This testing involves checking of User Interface, APIs, Database, security, client/ server applications and functionality of the Application Under Test. The testing can be done either manually or using automation

<kbd>![](https://www.guru99.com/images/FunctionalTestingProcessv1.png)</kbd>

## Beta / Acceptance Testing

An  [acceptance test](https://www.softwaretestinghelp.com/what-is-acceptance-testing/)  is performed by the client and verifies whether the end to end the flow of the system is as per the business requirements or not and if it is as per the needs of the end user. Client accepts the software only when all the features and functionalities work as expected.

It is the last phase of the testing, after which the software goes into production. This is also called User Acceptance Testing (UAT) / Staging environment.

Acceptance testing is a formal type of software testing that is performed by end user when the features have been delivered by developers. The aim of this testing is to check if the software confirms to their business needs and to the requirements provided earlier. Acceptance tests are normally documented at the beginning of the sprint (in agile) and is a means for testers and developers to work towards a common understanding and shared business domain knowledge.

This is a formal type of software testing that is carried out by end customers before releasing or handing over software to end users. Successful completion of Beta testing means customer acceptance of the software.

[Beta Testing](https://www.softwaretestinghelp.com/beta-testing/)  is a formal type of software testing which is carried out by the customer. It is performed in  **the Real Environment **before releasing the product to the market for the actual end users.

Beta testing is carried out to ensure that there are no major failures in the software or product and it satisfies the business requirements from an end-user perspective. Beta testing is successful when the customer accepts the software.

Usually, this testing is typically done by end-users or others. It is the final testing done before releasing an application for commercial purpose. Usually, the Beta version of the software or product released is limited to a certain number of users in a specific area.

So end user actually uses the software and shares the feedback to the company. Company then takes necessary action before releasing the software to the worldwide.

## Exploratory Testing

Exploratory Testing is informal testing performed by the testing team. The objective of this testing is to explore the application and looking for defects that exist in the application. Sometimes it may happen that during this testing major defect discovered can even cause system failure.

During exploratory testing, it is advisable to keep a track of what flow you have tested and what activity you did before the start of the specific flow.

[An exploratory testing technique](https://www.softwaretestinghelp.com/what-is-exploratory-testing/)  is performed without documentation and test cases.

In ET, the tester is designing his or her tests and executing them at the same time. Which is simultaneous learning, test design and test execution. As an exploratory tester, the next test is influenced by your previous actions, your observations of the product's behavior, and your own thought process.  
ET also assumes that a significant portion of the testing will be spent learning about the product. As you explore, you become more aware of how the product functions and its expected behavior. You can use that knowledge to design new and better tests. It also helps improve the analysis of the test's results.

### Why Do Exploratory Testing?

Executing scripted tests over and over will generally produce the same results. Exploratory testers use their cognitive abilities to continually improve the value of their work. They explore and adapt, they learn and adjust. ET is designed to make the most of our intellectual abilities.

ET also takes advantage of the differences between testers. Each tester's previous experience, skills, and thought process (among other things) causes him or her to view thing in a unique way. Different testers may come up with different ways to test the same function. It may be more beneficial to have three testers test the same function in three unique ways than it is to have all three test it in exactly same way.

When a tester is tasked to find bugs quickly, they need to be searching for bugs, not reading test cases. They need the freedom to follow promising leads, not the constraints of predefined instructions.

How Do I Get Started?

If there is one thing all new testers (including new exploratory testers) should do, it's to start by thinking about the product in general terms; try to see the big picture. Instead of initially focusing on one specific thing, first try to understand the context in which you are working.

Some questions to consider are:

*   Is this a product in development or is it already in production?
*   What is the purpose of the product?
*   Who are the users and how are they going to use it?

Jumping right in and banging on things might produce a bug or two, but if you hope to get the most out of ET, initial preparation and understanding your context is vital.

An exploratory tester would do something like this:

*   Get a notebook (or a digital word processor) to take notes as you go.
*   Explore the app as if you just downloaded it and want to use it yourself. If it is not an app you would typically use, then imagine you are the target market for the app.
*   Take a moment to really get in the mindset of a typical user. Some questions you can ask yourself are what is the goal of this app? Who would benefit from that? How do they benefit?

Once you get a feel for the app start going back to the areas that interested you and you thought might be a place of vulnerability in the app. This knowledge about vulnerability is going to come with experience. Don't worry if you don't have any experience yet because you are about to get some!

One by one, work through each area you've earlier identified, exploring every function in that area. Think of what a real user might do. Come up with with some use cases or scenarios and execute those. Then think of variations and execute those. Use the results of your tests to help you come up with new ideas.

Focus on one bug at a time, but always be on the lookout for hints of other bugs or suspicious areas. In your notebook, quickly make a note of these areas and how to get back to them. This way you can come back and explore each one later. You could very well end up with 4 or 5 bugs just from investigating the initial bug.

Once you've exhausted that area or function of the app, move on to your next point of interest. As you repeat this process, remember what you've learned so far and use that information to influence your tests.

## Interface Testing

Interface Testing is needed when a software provides support for one or more interfaces like “Graphical user interface”, “Command Line Interface” or “Application programming interface” to interact with its users or other software. Interfaces serve as the medium for software to accept input from a user and provide an output to the user. Approach for interface testing depends on the type of the interface being testing like GUI or API or CLI.

## Integration Testing

Testing of all integrated modules to verify the combined functionality after integration is  [termed as Integration Testing](https://www.softwaretestinghelp.com/what-is-integration-testing/) . Modules are typically code modules, individual applications, client and server applications on a network, etc. This type of testing is especially relevant to client/server and distributed systems.

Integration testing is one of the most common and important types of software testing. Once the individual units or components are tested by developers as working then testing team will run tests that will test the connectivity among these units/component or multiple units/components. There are different approaches for Integration testing namely, Top-down integration testing, Bottom-up integration testing and a combination of these two known as Sand witch testing.

## Performance Testing

This term is often used interchangeably with ‘stress' and ‘load' testing.  [Performance Testing](https://www.softwaretestinghelp.com/introduction-to-performance-testing-loadrunner-training-tutorial-part-1/)  is done to check whether the system meets the performance requirements. Different performance and load tools are used to do this testing.

Is a type of software testing and part of performance engineering that is performed to check some of the quality attributes of software like Stability, reliability, availability. Performance testing is carried out by performance engineering team. Unlike Functional testing, Performance testing is done to check non-functional requirements. Performance testing checks how well the software works in anticipated and peak workloads. There are different variations or sub types of performance like load testing, stress testing, volume testing, soak testing and configuration testing.

## Regression Testing

Testing an application as a whole for the modification in any module or functionality is termed as Regression Testing. It is difficult to cover all the system in  [Regression Testing](https://www.softwaretestinghelp.com/regression-testing-tools-and-methods/) , so typically  [automation testing tools](https://www.softwaretestinghelp.com/automation-testing-tutorial-1/)  are used for these types of testing.

Is a type of software testing that is carried out by software testers as functional regression tests and developers as Unit regression tests. The objective of regression tests is to find defects that got introduced to defect fix(es) or introduction of new feature(s). Regression tests are ideal candidates for automation.

## Sanity Testing

[Sanity Testing](https://www.softwaretestinghelp.com/smoke-testing-and-sanity-testing-difference/)  is done to determine if a new software version is performing well enough to accept it for a major testing effort or not. If an application is crashing for the initial use then the system is not stable enough for further testing. Hence a build or an application is assigned to fix it.

Is a type of testing that is carried out mostly by testers and in some projects by developers as well. Sanity testing is a quick evaluation of the software, environment, network, external systems are up & running, software environment as a whole is stable enough to proceed with extensive testing. Sanity tests are narrow and most of the time sanity tests are not documented.

## Scripted Testing

Scripted Testing (ST) is a two-step approach to testing. First the tests are written; they are planned, designed and documented. Second, the tests are executed. These two activities are done independently of each other and in many cases, the person who writes the tests is different than the person who executes them.

Generally, the tester executing the tests has some knowledge of the product, or the tests include the information needed to execute them (requirements). This is important because without that knowledge or information, the tester might not be able to execute the test or interpret its results.

## Smoke Testing

Whenever a new build is provided by the development team then the software testing team validates the build and ensures that no major issue exists.

The testing team ensures that the build is stable and a detailed level of testing is carried out further.  [Smoke Testing](https://www.softwaretestinghelp.com/smoke-testing-and-sanity-testing-difference/)  checks that no show stopper defect exists in the build which will prevent the testing team to test the application in detail.

If testers find that the major critical functionality is broken down at the initial stage itself then testing team can reject the build and inform accordingly to the development team. Smoke Testing is carried out to a detailed level of any functional or regression testing.

Is a type of testing that is carried out by software testers to check if the new build provided by the development team is stable enough i.e., major functionality is working as expected in order to carry out further or detailed testing. Smoke testing is intended to find “show stopper” defects that can prevent testers from testing the application in detail. Smoke testing carried out for a build is also known as build verification test.

## Stress Testing

This testing is done when a system is stressed beyond its specifications in order to check how and when it fails. This is performed under heavy load like putting large number beyond storage capacity, complex database queries, continuous input to the system or database load.

Is a type of performance testing, in which software is subjected to peak loads and even to a break point to observe how the software would behave at breakpoint. Stress testing also tests the behavior of the software with insufficient resources like CPU, Memory, Network bandwidth, Disk space etc. Stress testing enables to check some of the quality attributes like robustness and reliability.

## System Testing

Under  [System Testing technique](https://www.softwaretestinghelp.com/system-testing/) , the entire system is tested as per the requirements. It is a Black-box type testing that is based on overall requirement specifications and covers all the combined parts of a system.

This includes multiple software testing types that will enable to validate the software as a whole (software, hardware, and network) against the requirements for which it was built. Different types of tests (GUI testing, Functional testing, Regression testing, Smoke testing, load testing, stress testing, security testing, stress testing, ad-hoc testing etc.,) are carried out to complete system testing.

## Unit Testing

Is a type of testing that is performed by software developers. Unit testing follows white box testing approach where a developer will test units of source code like statements, branches, functions, methods, interface in OOP (object oriented programming). Unit testing usually involves in developing stubs and drivers. Unit tests are ideal candidates for automation. Automated tests can run as Unit regression tests on new builds or new versions of the software. There are many useful unit testing frames works like Junit, Nunit etc., available that can make unit testing more effective.

Testing of an individual software component or module is termed as  [Unit Testing](https://www.softwaretestinghelp.com/unit-testing/) . It is typically done by the programmer and not by testers, as it requires a detailed knowledge of the internal program design and code. It may also require developing test driver modules or test harnesses.

### Non-Functional Testing

Non-functional testing is defined as a type of Software testing to check non-functional aspects (performance, usability, reliability, etc) of a software application. It is designed to test the readiness of a system as per nonfunctional parameters which are never addressed by functional testing.

### Objectives of Non-functional testing

*   Non-functional testing should increase usability, efficiency, maintainability, and portability of the product.
*   Helps to reduce production risk and cost associated with non-functional aspects of the product.
*   Optimize the way product is installed, setup, executes, managed and monitored.
*   Collect and produce measurements, and metrics for internal research and development.
*   Improve and enhance knowledge of the product behavior and technologies in use.

### Characteristics of Non-functional testing

*   Non-functional testing should be measurable, so there is no place for subjective characterization like good, better, best, etc.
*   Exact numbers are unlikely to be known at the start of the requirement process
*   Important to prioritize the requirements
*   Ensure that quality attributes are identified correctly in Software Engineering.

### Non-functional testing Parameters

<kbd>![](https://www.guru99.com/images/1/022218_1114_WhatisNonFu2.png)</kbd>

## Compatibility Testing

It is a testing type in which it validates how software behaves and runs in a different environment, web servers, hardware, and network environment.  [Compatibility testing](https://www.softwaretestinghelp.com/software-compatibility-testing/)  ensures that software can run on a different configuration, different database, different browsers, and their versions. Compatibility testing is performed by the testing team.

Compatibility testing is one of the test types performed by the testing team. Compatibility testing checks if the software can be run on different hardware, operating system, bandwidth, databases, web servers, application servers, hardware peripherals, emulators, different configuration, processor, different browsers and different versions of the browsers etc.,

## Install Testing

[Installation and uninstallation testing](https://www.softwaretestinghelp.com/software-installationuninstallation-testing/)  is done on full, partial, or upgrade install/uninstall processes on different operating systems under different hardware or software environment.

## Load Testing

Load testing is a type of non-functional testing; load testing is done to check the behavior of the software under normal and over peak load conditions. Load testing is usually performed using automated testing tools. Load testing intends to find bottlenecks or issues that prevent software from performing as intended at its peak workloads.

It is a type of non-functional testing and the objective of Load testing is to check how much of load or maximum workload a system can handle without any performance degradation.

[Load testing helps](https://www.softwaretestinghelp.com/introduction-to-performance-testing-loadrunner-training-tutorial-part-1/)  to find the maximum capacity of the system under specific load and any issues that cause the software performance degradation. Load testing is performed using tools like [JMeter](https://www.softwaretestinghelp.com/jmeter-tutorials/) , LoadRunner, WebLoad, Silk performer etc.

## Recovery Testing

It is a type of testing which validates that how well the application or system recovers from crashes or disasters.

Recovery testing determines if the system is able to continue the operation after a disaster. Assume that application is receiving data through the network cable and suddenly that network cable has been unplugged.

Sometime later, plug the network cable; then the system should start receiving data from where it lost the connection due to network cable unplugged.

## Security Testing

It is a type of testing performed by a special team of testers. A system can be penetrated by any hacking way.

[Security Testing](https://www.softwaretestinghelp.com/how-to-test-application-security-web-and-desktop-application-security-testing-techniques/)  is done to check how the software or application or website is secure from internal and external threats. This testing includes how much software is secure from the malicious program, viruses and how secure and strong the authorization and authentication processes are.

It also checks how software behaves for any hackers attack and malicious programs and how software is maintained for data security after such a hacker attack.

Is a type of software testing carried out by a specialized team of software testers. The objective of security testing is to secure the software is to external or internal threats from humans and malicious programs. Security testing basically checks, how good is software’s authorization mechanism, how strong is authentication, how software maintains confidentiality of the data, how does the software maintain integrity of the data, what is the availability of the software in an event of an attack on the software by hackers and malicious programs is for Security testing requires good knowledge of application, technology, networking, security testing tools. With increased number of web applications, security testing has become more important than ever.

## Usability Testing

Under  [Usability Testing](https://www.softwaretestinghelp.com/usability-testing-guide/) , User-friendliness check is done. Application flow is tested to know if a new user can understand the application easily or not, Proper help documented if a user gets stuck at any point. Basically, system navigation is checked in this testing.

Is a type of software testing that is performed to understand how user-friendly the software is. Objective of usability testing is to allow end users to use the software, observe their behavior, their emotional response (whether users liked using software or were they stressed using it? etc.,) and collect their feedback on how the software can be made more useable or user friendly and incorporate the changes that make the software easier to use.

## Volume Testing

[Volume testing](https://www.softwaretestinghelp.com/what-is-volume-testing/)  is a type of non-functional testing performed by the performance testing team.

The software or application undergoes a huge amount of data and Volume Testing checks the system behavior and response time of the application when the system came across such a high volume of data. This high volume of data may impact the system’s performance and speed of the processing time.

Is a non-functional type of testing carried out by performance engineering team. Volume testing is one of the types of performance testing. Volume testing is carried out to find the response of the software with different sizes of the data being received or to be processed by the software. For e.g. If you were to be testing Microsoft word, volume testing would be to see if MS word can open, save and work on files of different sizes (10 to 100 MB).

## Compatibility Testing

## Compliance Testing

## Efficiency Testing

## Failover Testing

## Localization Testing

## Maintainability Testing

## Portability Testing

## Scalability Testing

## Reliability Testing

## Accessibility Testing

Accessibility testing, a subset of usability testing, involves performing tests via software to ensure people with disabilities are able to use a website without experiencing any sort of barriers. Essentially, accessibility testing is the process that must take place prior to addressing accessibility issues on any given website. This is necessary to ensure you’re meeting the [WCAG guidelines](https://www.telerik.com/blogs/the-wcag-accessibility-regulations-you-need-to-know).

For nearly any website, a combination of manual and automated accessibility testing should take place as early as possible during the design and development phase, as well as often throughout design and development.

### Why Perform Accessibility Testing?

Products, including websites, should be delivered to people of all types, including people with disabilities, to ensure inclusivity. For those with disabilities, assistive technologies are available to help them better leverage the internet. However, websites must be designed with these assistive technologies in mind—from screen magnification software to screen readers to speech recognition software and everything in between.

Accessibility testing helps to ensure websites are user-friendly and accessible to everyone, including people with disabilities who rely on assistive technologies. Ultimately, accessibility testing will ensure usability for all disabilities, including visual, auditory, speech, cognitive, and more, as well as usability for individuals who do not have a disability but can still benefit from websites being easier to read and navigate.

So why, aside from being inclusive, should you make sure your website is accessible through accessibility testing?

### Boost Visibility to a Greater Market

Chances are, your product and/or service would be of interest for persons with disabilities. Think about how much of the population has a disability of some sort. You don’t want to eliminate such a large portion of the population from becoming a potential customer.

### Lower Site Development and/or Maintenance Costs

If you make your website accessible from the beginning, you’ll spend much less money on development and/or maintenance in the long-run. It’s also much quicker to make changes as needed to a website that’s already accessible from the start. After all, compliance with applicable standards and guidelines will be mandatory eventually.

### Improve Usability on Different Browsers and/or Devices

Websites that are accessible will operate better on a variety of browsers and/or devices than those that aren’t accessible. They will work better for those in situationally challenging circumstances as well, such as noisy airports or natural lighting that causes glare.

## Common Disabilities

A disability is any condition of the mind or body that makes it difficult for the individual to perform certain activities or interact with society and/or the world around them. Disabilities are known for resulting in limitations in terms of participation and activity. There are many different types of disabilities, including but not limited to:

### 1\. Cognitive

Cognitive disabilities are the most common form of disability an individual can experience. They often result from conditions present at birth or conditions developed at some point in life, such as chemical imbalances, infections, traumatic injuries, and more. There are approximately 16 million people impacted by a cognitive disability in the United States, although two people with the same cognitive disability may experience entirely separate challenges.

Most individuals with a cognitive disability will require assistance, to some degree, to help them approach their day-to-day lives. Cognitive disabilities are classified in two ways: clinical and functional. The clinical category includes Down syndrome, autism, dementia, and traumatic brain injuries, as well as various other less severe conditions. The functional category, on the other hand, focuses on the individual’s abilities and challenges resulting from the disability, such as:

*   Memory
*   Problem-solving
*   Reading/verbal comprehension
*   Attention
*   Math comprehension
*   Visual comprehension

The functional category is particularly helpful to be aware of when developing websites. This allows us to review the types of barriers those with cognitive disabilities face—helping to ensure websites address those barriers in all technical and navigational aspects.

#### 2\. Blindness

Blindness is characterized as sightlessness or loss of vision. When we speak of blindness, we generally are referring to a total loss of vision, whereas partial blindness refers to low vision. Blindness has several potential causes, including but not limited to the following:

*   Glaucoma
*   Stroke
*   Diabetes
*   Macular degeneration
*   Accidents or injuries to the eye
*   Retinitis Pigmentosa

Approximately 285 million people are visually impaired to some degree worldwide. Of those 285 million people, 39 million are completely blind. Those who are blind use the internet with a range of assistive technologies, such as screen readers, braille devices, and keyboards.

When web developers don’t consider blindness while developing websites, those who are blind aren’t able to use those websites unless they’re gathering information from someone else.

#### 3\. Vision Disabilities

Vision disabilities, also known as visual impairment, refers to a decreased ability to see that cannot be solved with medication or glasses. Visual impairment can result from trauma, disease, as well as degenerative or congenital conditions. Some eye disorders leading to visual impairment include:

*   Glaucoma
*   Cataracts
*   Retinal degeneration
*   Albinism
*   Muscular problems
*   Infection
*   Diabetic retinopathy
*   And more

In addition, visual impairment can result from brain and nerve disorders. When this happens, it’s known as cortical visual impairment. As mentioned above, there are approximately 285 million people with visual impairment worldwide. Of those individuals, 246 million have low vision as opposed to being completely blind.

Similar to blindness, web developers must consider those with visual impairment as they often use various assistive technologies to access the web. Websites must be made accessible and able to support those assistive technologies.

#### 4\. Deafblindness

Deafblindness refers to having little or no sight and hearing. Those who are deafblind may experience varying degrees of sight and hearing impairment. A person may be deaf or blind at birth and lose the other sense at some point throughout life. A person who is born deaf/blind has congenital deafblindness, while a person who loses one or both of the senses at some point in life has acquired deafblindness.

Helen Keller is a very well-known example of someone who had deafblindness. There are approximately 35,000 – 40,000 individuals who are medically deafblind in the United States. Congenital deafblindness can be caused by the following:

*   Genetic conditions from birth, such as trisomy 13
*   Illness or infection, such as AIDs or rubella
*   Pregnancy-related problems, such as fetal alcohol syndrome
*   Complications related to prematurity

Those who end up with deafblindness at some point in life usually acquire it due to a variety of reasons:

*   Genetic conditions, such as usher syndrome
*   Meningitis
*   Illness
*   Age-related loss of sight and/or sound
*   Physical damage
*   Stroke
*   Brain damage

Those who are deafblind rely on various assistive technologies, such as braille displays or screen readers, to leverage the internet in life-changing ways. Web developers must consider those with deafblindness during the design phase of any given website.

#### 5\. Physical Impairments

A physical impairment refers to any disability that limits a person’s ability to remain mobile or active. Essentially, physical impairments impact functioning, mobility, stamina or dexterity. This can include:

*   Brain or spinal cord injuries
*   Cerebral palsy
*   Multiple sclerosis
*   Respiratory disorders
*   Epilepsy
*   And much more

Physical impairments significantly impact the individual’s ability to take part in various activities throughout day-to-day living. They usually fall into one of two main categories:

*   Congenital: The physical impairment occurred due to inherited genetic problems or other issues at birth.
*   Acquired: The physical impairment occurred due to an accident, disease or infection at some point in life.

Those with physical disabilities make up a large amount of the population. In fact, approximately 75 million people have some type of physical disability throughout the United States. Physical disabilities often include weakness and limitations in terms of muscular control. This means web developers must consider any design and/or functionality aspects that would be impossible with involuntary movements, tremors or lack of coordination.

### How to Do Accessibility Testing

The web is an incredibly important resource for everyone, including people with disabilities. It makes many aspects of life—from healthcare to recreation to employment—much easier than they would be without the web. The benefits of performing accessibility testing are clear, but where do you start? As web accessibility becomes a more prevalent topic, training programs are popping up all over the place to help teach individuals how to create accessible content.

Most training programs focus on the WCAG 2.1 guidelines, which provide various technical specifications and techniques for web developers to follow when it comes to creating accessible content. So how do you perform accessibility testing?

#### 1\. Start Learning about Accessibility

The first step to performing accessibility testing is learning how to create accessible content. After all, you don’t want to go through the process of testing something that isn’t even close to accessible. This [article](https://dynomapper.com/blog/27-accessibility-testing/556-where-to-learn-web-accessibility) about “where to learn web accessibility” is a great start. It reviews various resources to help web developers and businesses learn more about web accessibility, many of which are free of charge. Here are a few resources to consider:

*   **Google’s Introduction to Web Accessibility**

Google offers an introductory guide, as well as practice design labs and samples for those looking to learn web accessibility. There is no requirement of prerequisite knowledge, but it is helpful to have some background in web design. The course teaches what accessibility is, advanced accessibility techniques, and more important information to create usable and accessible websites.

*   **International Association of Accessibility Professionals Certification (IAAP)**

The IAAP offers a certification program that helps individuals add to their professional qualifications with proof of capabilities and/or knowledge of accessibility. The IAAP offers two types of certifications: a professional level credential and a technical level credential. You don’t have to be a member of the IAAP to take any certification course, and prior experience is not necessary but helpful.

*   **Microsoft’s Training Teachers to Author Accessible Content**

Microsoft offers an hour-long course, separated into ten modules, on web accessibility. A valid Microsoft account is necessary to complete the course on their website. Each module has course notes and a video provided to individuals taking the course. You will learn how to create and revise documents so everyone, including those with disabilities, can access them.

#### 2\. Perform Manual Testing

There are a lot of accessibility issues that might be missed with a computer program. [Manual testing](https://www.telerik.com/blogs/manual-accessibility-testing-keyboard-and-screen-reader-navigation) involves having human testers perform a range of tests to ensure the website is actually usable for individuals with disabilities. Similar to any type of editing or quality assurance, you’re able to get an entirely new viewpoint with each person who performs manual testing. Testers will look for:

*   Compatibility with various assistive technologies
*   Navigation that is simple and easy to understand
*   Content that is meaningful and clear/concise
*   Coordination with color adjustment plugins for various web browsers
*   And much more

Any testers used should be familiar with the latest standards when it comes to web accessibility. That means they must understand WCAG 2.1 to ensure they’re looking for the right factors that matter to people with disabilities.

#### 3\. Perform Automated Testing

Automated testing is the process of using software tools designed to find accessibility issues. These tools have evolved quite a bit over the past few years. It’s not difficult to find a range of tools available to help you adhere to accessibility guidelines. In fact, there are browser extensions, command-line tools, and much more. These tools should be used at the beginning of the design process and periodically throughout to catch issues before they go into production.

### Why Use Manual and Automated Testing?

Manual and automated testing should be used in combination with one another in order to ensure a thorough testing process that doesn’t miss anything important. Automated tools are great for finding:

*   Images without alt text
*   Content that doesn’t have headings
*   HTML code that isn’t valid
*   Form fields that are missing labels and/or descriptions
*   And much more

However, as much as technology has advanced, human intervention can help find issues that no software tool is able to pinpoint, such as:

*   Alt text that isn’t accurate given the context
*   Descriptions that aren’t clear or easy to understand
*   Headings that don’t make sense given the hierarchy
*   And much more

From a usability standpoint, something like a misleading alt tag makes a world of difference, even though it’s not findable with an automated tool.

### Automated Accessibility Testing Tools

As mentioned, there’s a wide range of software tools available for automated testing. The process of testing for accessibility should be ongoing throughout all stages of development. If you have the means, a continuous integration solution can be very beneficial. Some common tools for automated testing include:

#### 1\. Dyno Mapper

Dyno Mapper allows you to test entire websites for WCAG 1.0, 2.0, 2.1/Section 508 compliance, as well as various other guidelines:

*   BITV 1.0 (Level 2)
*   Stanca Act

The tool offers various features to ensure you’re able to fix any known errors in web content and design:

*   **The ability to visualize:** Use a browser to view accessibility tests with icons showing over the website image to indicate known, likely, and potential issues.
*   **Check public or private applications:** Check public or private applications with basic authentication, CMS authentication or custom form authentication.
*   **Perform ongoing automatic testing/monitoring:** Use the schedule feature to ensure automatic testing and reporting on a monthly basis.
*   **Receive notifications when issues arise:** If an issue is found, you will receive notifications sent to your email to alert you of known, likely, and potential issues.

#### 2\. SiteImprove

SiteImprove allows you to ensure your website is inclusive and usable for every visitor that comes your way. This helps you adhere to various global accessibility guidelines, including WCAG 2.1, with features such as:

*   **Accessibility diagnosis:** Use practical recommendations, your own criteria or the tool’s scoring system to decide which issues you want to fix first.
*   **On-page and in-code highlights:** View issues with on-page and in-code highlights that make it simpler than ever to fix errors.
*   **Quality assurance/accessibility dashboards:** See how far you’ve come in terms of accessibility with customizable dashboards and automated reports.

The tool lets you see every link, page, and media file at a glance—locating issues that could impact your site’s accessibility level.

#### 3\. Monsido

Monsido scans your website for any issues that may be stopping you from reaching ADA compliance with Section 508 and WCAG 2.1 standards. You’re able to leverage this tool to:

*   **Choose the compliance level you need:** Not all sectors have the same compliance requirements, so you’re able to check for WCAG 2.1 or Section 508 accessibility issues.
*   **Leverage a built-in help center:** A help center is available via an icon for times when you’re not quite sure how to fix an issue and would like some detailed information or instructions.
*   **View your accessibility status:** Compliance standards are organized by levels, such as A, AA, and AAA—allowing you to fix low-level issues first and foremost before putting time into high-level issues.
*   **Reach out for training sessions:** Take advantage of training and one-on-one support options available to you and your team to ensure you’re up-to-date on the latest best practices.

The tool will scan your domain on a weekly basis to help ensure compliance at all times. This information can be found in the dashboard wherein you can see a total count of issues and which pages they’re found on.

### Accessibility Testing Checklist

When it comes to accessibility testing, it might feel like there’s a lot of work to do, and while that’s true, a checklist can make the process a lot easier. Here’s an accessibility testing checklist to follow.

**TEXT**

*   Can users enlarge the text if needed?
*   Is there enough contrast between the text color and the background color?
*   Does the website use bold, underlined, and italics when needed?
*   Are the navigation items labeled clearly in a way that’s understandable?
*   Is the font easy to read, and if not, can the user override fonts for text displays?

**VIDEO AND AUDIO**

*   Do all video and audio clips used fit with the content shown on the page?
*   Are subtitles or transcripts available for any form of multimedia used?
*   Can video and audio clips be stopped once the page loads?
*   Are video and audio clips dangerous for those sensitive to light and sound?
*   Are users able to adjust audio or video controls as needed?

**COLOR AND CONTRAST**

*   Do background and foreground colors have enough contrast?
*   Is color-coding used as a means of conveying information or indicating actions?

**IMAGES**

*   Do all images used have a purpose (to convey information)?
*   Is the site loading slowly because of too many images?
*   Do all images have alternate text to go with them?
*   Are there low contrast/extremely bright colors that may be difficult to view?
*   Do any images flash, rotate or move without the ability to stop them?

**LANGUAGE**

*   Are you using a higher than average vocabulary?
*   Is the language clear and concise without confusing terms?
*   Are there links to explain words that might be advanced?

**FORMS**

*   Are text boxes within forms clearly labeled?
*   Are text boxes organized properly and predictably (name, address, city, etc.)?
*   Can forms be filled out using the keyboard to go from one box to the next?

**HEADINGS**

*   Are headings simple and descriptive so the meaning is clear to users?
*   Is there a linked table of contents on pages with a lot of information?

For more information on what to look for when accessibility testing, check out this complete [web accessibility testing checklist](https://dynomapper.com/blog/27-accessibility-testing/521-web-accessibility-checklist).

Application must support people with disabilities like -

<table class="wrapped confluenceTable">
	<colgroup>
		<col>
			<col>
			</colgroup>
			<tbody>
				<tr>
					<th style="text-align: left;">

**Type of Disability**

</th>
					<th style="text-align: left;">

**Disability Description**

</th>
				</tr>
				<tr>
					<td style="text-align: left;">

**Vision Disability**

</td>
					<td style="text-align: left;">

*   Complete Blindness or Color Blindness or Poor Vision
*   Visual problems like visual strobe and flashing effect problems

</td>
				</tr>
				<tr>
					<td style="text-align: left;">

**Physical Disability**

</td>
					<td style="text-align: left;">

*   Not able to use the mouse or keyboard with one hand.
*   Poor motor skills like hand movements and muscle slowness

</td>
				</tr>
				<tr>
					<td style="text-align: left;">

**Cognitive disability**

</td>
					<td style="text-align: left;">

*   Learning Difficulties or Poor Memory or not able to understand more complex scenarios

</td>
				</tr>
				<tr>
					<td style="text-align: left;">

**Literacy Disability**

</td>
					<td style="text-align: left;">

*   Reading Problems

</td>
				</tr>
				<tr>
					<td style="text-align: left;">

**Hearing Disability**

</td>
					<td style="text-align: left;">

*   Auditory problems like deafness and hearing impairments
*   Cannot able to hear or not able to hear clearly

</td>
				</tr>
			</tbody>
		</table>

## Maintenace

Maintenance Testing is done on the already deployed software. The deployed software needs to be enhanced, changed or migrated to other hardware. The Testing done during this enhancement, change and migration cycle is known as maintenance testing.

Once the software is deployed in operational environment it needs some maintenance from time to time in order to avoid system breakdown, most of the banking software systems needs to be operational 24*7*365\. So it is very necessary to do maintenance testing of software applications.

In maintenance testing, tester should consider 2 parts.

Any changes made in software should be tested thoroughly.

The changes made in software does not affect the existing functionality of the software, so regression testing is also done.

###### Tutorials

*   [https://www.softwaretestinghelp.com/system-testing](https://www.softwaretestinghelp.com/system-testing/)
*   [https://www.softwaretestinghelp.com/smoke-testing-and-sanity-testing-difference](https://www.softwaretestinghelp.com/smoke-testing-and-sanity-testing-difference/)

<h7>References</h7>

*   [Testing Excellence - Types of Software Testing – Complete List](https://www.testingexcellence.com/types-of-software-testing-complete-list/)
*   [Types Of Software Testing: Different Testing Types With Details](https://www.softwaretestinghelp.com/types-of-software-testing/)
*   [Reqtest - Sanity testing](https://reqtest.com/testing-blog/sanity-testing-2/)
*   [Guru99 - non-functional testing](https://www.guru99.com/non-functional-testing.html)
*   [Guru99  - functional testing](https://www.guru99.com/functional-testing.html)
*   [Guru99 - Accessibility testing](https://www.guru99.com/accessibility-testing.html)
*   [Telerik - An introduction to accessibility testing](https://www.telerik.com/blogs/an-introduction-to-accessibility-testing)
