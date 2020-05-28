DevOps :  Workflow  

###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [DevOps](https://github.com/RyKaj/Documentation/tree/master/DevOps/README.md) |
------------

DevOps :  Workflow
========================================

Created by Ryan Kajiura, last modified on Nov 04, 2019



  

**Sequential Diagrams**

Feature Branch

![](attachments/462586629/462586632.png)

Hotfix Branch

![](attachments/462586629/462586633.png)

  

Source File - Visio 2016

[![](download/resources/com.atlassian.confluence.plugins.confluence-view-file-macro:view-file-macro-resources/images/placeholder-small-file.png)DevOps Workflow.vsdx](/download/attachments/462586629/DevOps%20Workflow.vsdx?version=1&modificationDate=1572884514567&api=v2)

**Happy Path - Auditor Demo**

HappyPath is a project to demo to the auditors on how the flow works.

Happy Path Info

### Bitbucket

DevOpsHappyPath - [http://stash.pinnaclesports.com/projects/CUS/repos/devopshappypath/browse](http://stash.pinnaclesports.com/projects/CUS/repos/devopshappypath/browse)

### Team City

#### Build Configuration: ITDev - DevOpsHappyPath Develop

[http://build.pinnaclesports.com/admin/editBuild.html?id=buildType:Customer\_DevOpsHappyPathDevelop](http://build.pinnaclesports.com/admin/editBuild.html?id=buildType:Customer_DevOpsHappyPathDevelop)

#### Build Configuration: ITDev - DevOpsHappyPath Release

[http://build.pinnaclesports.com/admin/editBuild.html?id=buildType:Customer\_ITDevDevOpsHappyPathRelease](http://build.pinnaclesports.com/admin/editBuild.html?id=buildType:Customer_ITDevDevOpsHappyPathRelease)

### Octopus

Devops Happy Path  - [http://octopus.pinnacle.com/octopus/app#/projects/devops-happy-path/overview](http://octopus.pinnacle.com/octopus/app#/projects/devops-happy-path/overview)

Environment URL
---------------

### Development

[http://admindev.pinnacle.com/devops](http://admindev.pinnacle.com/devops)

### CI (Quality Assurance)

[http://adminci.pinnacle.com/devops](http://adminci.pinnacle.com/devops)

### Staging (UAT)

[http://adminx.pinnacle.com/devops](http://adminx.pinnacle.com/devops)

### Production

[http://admin.pinnacle.com/devops](http://adminx.pinnacle.com/devops)

**ISMS Document References**

  

[ISMS-POL-12 Change Management Policy](https://wiki.pinnacle.com/display/LaC/ISMS-POL-12+Change+Management+Policy)

ISMS-POL-12 Change Management Policy

Document Code

ISMS-POL-12

Version

2.2

ISO 27001

\*

*   Add filter
*   Reset column sorting
*   Export to PDF
*   Export to CSV
*   Export to Word
*   Copy the filter URL
*   Modify Settings

*   [Documentation](https://docs.stiltsoft.com/display/TableFilter/How+to+use+Table+filter+macro?from=tf-view)
*   [What's new](https://docs.stiltsoft.com/display/TableFilter/Table+Filter+and+Charts+5.1.0?from=tf-view)

ISO 27001 Control = ≠Total Unique Issues:

Hide columns = ≠Issue Type

Showing the first all rows

Start adding filters in the filter tools menu.

The filter is disabled at the moment.

*   Export to PDF
*   Export to CSV
*   Export to Word

*   [Documentation](https://docs.stiltsoft.com/display/TableFilter/How+to+use+Table+filter+macro?from=tf-view)
*   [What's new](https://docs.stiltsoft.com/display/TableFilter/Table+Filter+and+Charts+5.1.0?from=tf-view)

Oops, it seems that you need to place a table or a macro generating a table within the Table Filter macro.

The table is being loaded. Please wait for a bit ...

[Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

ISO 27001 Control

Issue Type

Showing **0** of **0** statistics.  
[View in Jira](https://support.pinnaclesports.com/secure/IssueNavigator.jspa?reset=true&mode=hide&jqlQuery=key%3DISMS-21)

(function ($) { AJS.toInit(function () { var script = $('#tf-init-script-1559566514650\_1411860973-377488576-541605295'); if (!true) { //dd обрезается Panel / section macro script.parents('.panel, .alertPanel, .infoPanel, .innerCell').css('overflow', 'visible'); } script.remove(); //происходила повторная инициализация при открытии редактора var sorts = \[\]; var init = function () { var tf = new TableFilter({ showNRows: "all", limitHeight: "", heightValue: "", numbering: "", sorts: TableUtils.unescapeStrings(sorts), datepattern: "dd M yy", separator: ".", id: "1559566514650\_1411860973", pageId: "377488576", sparkline: false, sparkName: TableUtils.unescapeString("Sparkline"), order: "0,1", isOR: "AND", ddSeparator: TableUtils.unescapeString(""), fixedCols: "", totalrow: "", totalcol: "", isLockEnabled: false, worklog: "", updateSelectOptions: false, totalColName: TableUtils.unescapeString(""), totalRowName: TableUtils.unescapeString(""), thousandSeparator: "", tabs: false, sessionId: 541605295 }) if (tf == null) return; if ($('div.wiki-content.view-template').length) { tf.comboBoxDiv.find('button').removeAttr('aria-disabled'); tf.saveBtn.remove(); } }; var check = function () { if (window.TableFilter) { $('.tablefilter-outer-wrapper\[data-id="1559566514650\_1411860973"\]\[data-pageid="377488576"\]\[data-sessionid="541605295"\] #comboBoxDiv-1559566514650\_1411860973').show(); init(); } else { $('.tablefilter-outer-wrapper\[data-id="1559566514650\_1411860973"\]\[data-pageid="377488576"\]\[data-sessionid="541605295"\] #comboBoxDiv-1559566514650\_1411860973').hide(); setTimeout(check, 100); } } check(); }); })(AJS.$)

Document Status

[ISMS-21](https://support.pinnaclesports.com/browse/ISMS-21?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

Last Modified By

[Rod Mills](    /display/~rodm
)

Last Modified Date

Sep 13, 2019 07:14

Contributors

[Rod Mills](/display/~rodm) 8 (251 days ago),[Eduardo Vlieg](/display/~eduardov) 1 (1176 days ago),[Luis Embalo](/display/~luise) 1 (1028 days ago)

SME

IOC Team Lead

Reviewed By

Business Analysis Manager  
Development Manager  
Head of Security

Approved By

Head of Development  
Head of Infrastructure  
IT Operations Manager

Confidentiality Level

Medium  

  

  

Change History
==============

Revisions

.aui td { white-space:nowrap; }

Version

Date

Comment

**[Current Version](/display/LaC/viewpage.action?pageId=377488576) (v. 10)**

**Sep 13, 2019 07:14**

**[Rod Mills](    /display/~rodm
)**

[v. 9](/display/LaC/viewpage.action?pageId=451825698)

Jun 03, 2019 03:58

**[Rod Mills](    /display/~rodm
)**

[v. 8](/display/LaC/viewpage.action?pageId=446677805)

Jun 03, 2019 03:58

**[Rod Mills](    /display/~rodm
)**

[v. 7](/display/LaC/viewpage.action?pageId=446677804)

Jun 03, 2019 03:54

**[Rod Mills](    /display/~rodm
)**:  
Reverted from v. 5

[v. 6](/display/LaC/viewpage.action?pageId=446677802)

Jun 03, 2019 03:48

**[Rod Mills](    /display/~rodm
)**

[v. 5](/display/LaC/viewpage.action?pageId=446677798)

Jun 12, 2018 05:25

**[Rod Mills](    /display/~rodm
)**

[v. 4](/display/LaC/viewpage.action?pageId=416092844)

Jun 08, 2018 09:46

**[Rod Mills](    /display/~rodm
)**

[v. 3](/display/LaC/viewpage.action?pageId=416092364)

Mar 28, 2018 01:08

**[Rod Mills](    /display/~rodm
)**

[v. 2](/display/LaC/viewpage.action?pageId=405745079)

Jul 28, 2017 04:27

**[Luis Embalo](    /display/~luise
)**

[v. 1](/display/LaC/viewpage.action?pageId=384633916)

Mar 02, 2017 07:31

**[Eduardo Vlieg](    /display/~eduardov
)**

  

Table of Contents
=================

Table of Contents

/\*<!\[CDATA\[\*/ div.rbtoc1590083011223 {padding: 0px;} div.rbtoc1590083011223 ul {list-style: disc;margin-left: 0px;} div.rbtoc1590083011223 li {margin-left: 0px;padding-left: 0px;} /\*\]\]>\*/

*   1 [Change History](#DevOpsWorkflow-ChangeHistory)
*   2 [Table of Contents](#DevOpsWorkflow-TableofContents)
*   3 [1\. Purpose, scope and users](#DevOpsWorkflow-1.Purpose,scopeandusers)
*   4 [2\. Reference Documents](#DevOpsWorkflow-2.ReferenceDocuments)
*   5 [3\. Change Advisory Board (CAB)](#DevOpsWorkflow-3.ChangeAdvisoryBoard(CAB))
*   6 [4\. Change Categories](#DevOpsWorkflow-4.ChangeCategories)
*   7 [5\. Change categories Sportsbook](#DevOpsWorkflow-5.ChangecategoriesSportsbook)
*   8 [6\. Roles and Responsibilities](#DevOpsWorkflow-6.RolesandResponsibilities)
*   9 [7\. Change Management](#DevOpsWorkflow-7.ChangeManagement)
*   10 [8\. Managing records kept on the basis of this document](#DevOpsWorkflow-8.Managingrecordskeptonthebasisofthisdocument)
*   11 [9. Document management](#DevOpsWorkflow-9.Documentmanagement)

  

1\. Purpose, scope and users
============================

Change Management is the process responsible for controlling and managing requests to effect changes to IT assets to promote business benefit or support operational needs while minimizing the risk of disruption to services. Change Management also controls and manages the implementation of those changes that are subsequently given approval.

Change Management ensures that changes:

*   Are justified.
*   Are carried out without jeopardizing IT service quality and security level.
*   Are properly recorded, classified, and documented.
*   Have been carefully tested in a test environment.
*   Can be undone by running rollback procedures if the system functions incorrectly after implementation.
*   Are reviewed to determine if they achieved their business objectives.

Change Management serves as a single point of control for changes to IT assets. Changes to the IT assets within the _Information Security Management System_ (ISMS) scope must go through the Change Management process.

That scope includes:

*   Hardware/Desktop – Installation, modification, removal or relocation of computing equipment.
*   External service providers - infrastructure, payment and supporting applications.
*   Software – Installation, patching, upgrade or removal of software products including operating systems, access methods, commercial off-the-shelf (COTS) packages.
*   Databases – Changes to databases or files such as additions, reorganizations and major maintenance.
*   Business applications – internally developed packages and utilities, Application changes being promoted to production as well as the integration of new application systems and the removal of obsolete elements.
*   Moves, Adds, Changes and Deletes – Changes to system configuration.
*   Network equipment and security tools, including firewalls.
*   Schedule Changes – Requests for creation, deletion, or revision to job schedules, backup schedules or other regularly scheduled jobs managed by Pinnacle’s IT organization.
*   Communication tools – Installation, modification, uninstallation, or relocation of equipment and services.
*   Datacenter hosting providers.

  

Users of this document are employees that will fulfill one of the roles defined below as part of the Change Management process.

**Role**

**Typical Pinnacle function performing role**

 Asset Owner

For instance, the Customer Management Applications are owned by Head of Customer Operations and the ASIDB is owned by the Database Manager. Refer to _Inventory of Assets_ for a complete list.

Change Initiator

Anyone in the organization authorized by an Asset Owner to request changes for his/her asset

Change Manager

IOC Team Lead, Lead Business Analyst or Project Portfolio Manager

Change Analyst

Business Analyst or System Engineer

Change Advisory Board (CAB)

A project CAB should consist of at least the following roles:

*   Asset Owner
*   Project Sponsor (i.e. Executive stakeholder)
*   Change Manager

Change Implementer

IT Development team or Infrastructure team.

Technical Quality Assurance Tester

Embedded QA testers in the various development teams or IOC engineers

Business Quality Assurance Tester

Change Initiators and/or persons appointed by Change Initiators, e.g. end-users directly impacted by the change

Release and Deployment Manager

Integrated Operations Center (IOC)

Steering Committee

Committee consisting of the CEO, various members of the executive team and senior management team, including Project Portfolio Manager.

  

2\. Reference Documents
=======================

*   ISMS-POL-11-Secure Development Policy
*   ISMS-POL-21-Statement of Applicability
*   ISO/IEC 27001 standard, clauses A.12.1.2, A.14.2.4

  

3\. Change Advisory Board (CAB)
===============================

Pinnacle has appointed several employees that are authorized to approve or reject changes. Pinnacle has defined several CABs, formed of two or more of such employees. The CAB formation depends on the type of asset (e.g. software, database, hardware etc.). If necessary, a new CAB will be formed on a project basis.

  

4\. Change Categories
=====================

Pinnacle defines three categories of change:

1.  **Emergency changes:** arise when an unexpected error or threat occurs, such as when a flaw in the infrastructure related to services needs to be addressed immediately (e.g. security threat).
2.  **Recurring changes:** are changes to a service or to the IT infrastructure where the implementation process and the risks are known upfront. These changes are managed according to policies that the IT organization already has in place, and are typically recurring in nature (e.g. weekly update of Geo-IP records).
3.  **Normal changes:** are those changes that must go through the Change Management process before being approved and implemented (e.g. new application features or replacement of physical servers).

  
The change category determines the type of approval needed:

  

*   **Emergency Change:** written approval from the _Asset Owner_ is sufficient due to the urgency.
*   **Recurring change:** a one-time approval by the _Asset Owner_ is sufficient. After this approval, the recurring changes can be implemented without requiring additional approvals.
*   **Normal change:** should be formally requested and approved through a CAB according to the Change Management process as described in the subsequent sections of this document.

All changes must be documented in an appropriate manner for audit purposes, i.e. a list of all changes. Proof that controls (initiation, testing, and approval) have been followed for each change/release must also be registered and stored to support audit purpose. For emergency changes, the required documentation will take place retroactively.

Information to be backed up is information that requires a quick restore if needed in order to maintain business continuity.

  

5\. Change categories Sportsbook
================================

Development of risk management applications requires a special blend of industry knowledge and software development experience, the company has chosen to employee third party consultants to aid in the development of these applications. Our consultants categorize their Changes as follows:

1.  Incident - Linked to support Jira Ticket
2.  Bugfix - Bugs that are discovered before any complain recorded
3.  Improvement - Technical improvements
4.  Feature - New features requested by Pinnacle

For the company to stay ahead of competing sportsbooks it requires:

*   Rapid and frequent releases to production, sometimes multiple times throughout the day
*   To keep up with change requests a select number of development team members have been granted the right to deploy changes.
*   Increased automation for application development and production management

In an effort to be compliant with audit controls and at the same type maintain a high level of development turn out, certain controls have been put in place to protect against unauthorized changes to production systems. Consequently, the following controls have been adopted.

*   Approval for major changes needs to be provided by the Head of trading
*   Traceable authorizations for promotion of code to production through CM tool
*   Role-based access controls for developers to automated deployment application
*   Access to production systems by development staff is restricted
*   File integrity monitoring (and alerting) on changes to production code versus the traditional focus on critical operating system executable
*   File access monitoring on the source code itself with appropriate alerting

From a monitoring perspective access and changes to files on production systems will create an alert Network and Security team and/or the security officer for further investigation.

From a process perspective, the increased communication and collaboration inherently creates an environment whereby an unscheduled or unauthorized change is more likely to be noticed. Furthermore, daily deployments, coupled with necessary roll-back procedures allow the potential impact of an unauthorized change to be reduced.

  

6\. Roles and Responsibilities
==============================

The following roles shall be implemented for the correct implementation of the Change Management process.

**Role**

 **Main duties, some of which may be delegated**

**Typical Pinnacle function performing role**

 Asset Owner

*   Ensures that changes to their respective assets are suitable, and that required confidentiality, integrity or availability protection levels are maintained during and after changes. Refer to _Information Classification Policy_

For instance, the _Customer Management Applications_ are owned by _Head of Customer Operations_ and the _ASIDB_ is owned by the _Database Manager_. Refer to _Inventory of Assets_ for a complete list

Change Initiator

*   Recognizes and identifies the need for change
*   Submits request for changes
*   Provides business objectives/stakeholder requirements
*   Signs off on User Acceptance of the changes
*   Ensures that a post-implementation review of the change performance is performed

Anyone in the organization authorized by an _Asset Owner_ to request changes for their asset

Change Manager

*   Receives and prioritizes change requests
*   Creates a change plan outlining the scope, needed resources, and timeline
*   Keeps a thorough record of the outcome of each change

Project Manager or Business Analyst Lead

Change Analyst

*   Determines the risk, impact, and constraints for requested changes
*   Makes recommendations to support approval or rejection of change by a _Change Advisory Board_ (see next row)
*   Elicits, documents and analyzes change requirements
*   Determines success criteria

Business Analyst or Systems Engineer

Change Advisory Board (CAB)

*   Authorizing or rejecting a change, and scheduling when the prospective change will be deployed

Selected persons from multiple teams related to the steps in a change implementation

Change Implementer

*   Builds or configures change

_IT Development team_ or _Systems and Corporate Services_

Technical Quality Assurance Tester

*   Performs technical QA, e.g. functional testing, regression testing, and testing of security and other quality requirements

Embedded QA testers in the various development teams or IOC engineers

Business Quality Assurance Tester

*   Performs _User Acceptance Testing_ (UAT), i.e. testing whether the stakeholder/end-user requirements are met

Change Initiators and/or persons appointed by Change Initiators, e.g. end users directly impacted by the change

Release and Deployment Manager

*   Deploys the solution on the production (live) environment
*   Ensures that rollback plans are in place, and executed when necessary

Integrated Operations Center (IOC)

  

7\. Change Management
=====================

The following formal Change Management process does not apply to emergency and recurring changes, but only to normal changes.

Create request for change:

*   Only employees authorized by _Asset Owners_ (i.e. Change Initiator role) can request normal changes.
*   Change Initiators must submit requests for all normal changes via a formal Request for Change (RFC) and must describe the business objectives and justification.

Review request for change:

*   Change Managers must prioritize and keep track of all normal change requests.
*   Change Analysts must assess the risk and impact of requested changes.
*   Change Analyst must provide recommendations to support the CAB decision-making.

Approve request for change:

*   Change Managers must identify the appropriate CAB for each normal change. If necessary, a new CAB must be formed.
*   A formed CAB should consist of at least the following roles:
    *   Asset Owner
    *   Project Sponsor (i.e. Executive stakeholder)
    *   Change Manager

*   The CAB must issue a technical and business approval for all changes. A financial approval is additionally needed if the change involves a capital investment.
*   Change Initiators must sign off all change requirements before implementation may commence.
*   Change Initiators must sign off on User Acceptance of the changes before deployment into production may commence.

*   **Financial approval**: indicates that the cost of a change has been assessed, accepted by Executive Management based on certain criteria and expectations, and that it is either within approved budgetary limits or meets cost-benefit criteria that may have been set for change approval.
*   **Technical approval** (including security): is an assurance that the Change is feasible, sensible and can be performed without causing inappropriate harm to the services provided to the business. If the technical experts are required to provide cost estimates (as is the case in many organizations), then this phase needs to precede financial approval.
*   **Business approval**: is necessary to ensure that the _Asset Owners_ and _Business Managers_ are content with the change proposals and the impact on their business requirements.

Plan a change:

*   Change Managers must create a change plan outlining the needed resources and timeline.
*   Change Managers must create a stakeholder engagement plan, and a communication plan.
*   Change Analysts must elicit, document, and analyse change requirements (functional requirements, quality requirements and acceptance criteria). Requirements should be elicited from _Subject Matter Experts_ (SME) where necessary (such as from a Security SME). 
*   _Technical Quality Assurance Testers_ must write test plans to be used for technical QA, e.g. functional testing, regression testing, and testing of security and other quality requirements.
*   _Business Quality Assurance Testers_ must write test plans to be used for _User Acceptance Testing._
*   The _Release and Deployment Manager_ must make a rollback plan to follow in case a change is not successful.

Implement a change:

*   Change Implementers must define the technical requirements in alignment with the functional and quality requirements provided by Change Analysts.
*   Change Implementers must build or configure the requested change.
*   Change Managers must execute the engagement plan, and the communication plan.
*   _Technical Quality Assurance Testers_ must perform technical QA testing in accordance with their test plans.
*   _Business Quality Assurance Testers_ must perform User Acceptance Testing in accordance with their test plans.
*   The _Release and Deployment Manager_ must deploy change releases to production only after having received documented approval to be able to do so.

Review change performance:

*   Change Initiators must ensure that a post-implementation evaluation of the change (i.e. validate outcome) takes place and must endeavour to identify possible improvements. Some parts of the evaluation may be delegated to Change Analysts.
*   A change can be only closed after the outcome has been validated.

Adjust:

*   As long as the Technical Quality Assurance criteria are not met, the Change Implementers must adjust the implemented change.
*   As long as the Business Quality Assurance criteria are not met, the Change Analysts and/or Change Implementers must adjust the change requirements and/or implemented change.
*   The _Release and Deployment Manager_ sees to it that the rollback plan is executed, in case that the results have a negative impact on the business or do not meet acceptance criteria.

  

8\. Managing records kept on the basis of this document
=======================================================

**Record name**

**Storage location**

**Person responsible for storage**

**Controls for record protection**

**Retention time**

Change management policy

Document repository

IT Operation Manager

Folder access permissions

5 years

  

9. Document management
======================

This document is valid as of the _Date of version_ recorded on page 1 of this document.

The head of Development is the owner of this document, who must check and, if necessary, update the document at least once a year.

When evaluating the effectiveness and adequacy of this document, at least the following metrics need to be considered:

*   Percentage of normal changes not passing through the formal Change Management process (or a specific Change Management phase).
*   Number of implemented changes that failed to produce the desired results.

  

  

  

  

  

[ISMS-PRO-13A Change Management Procedure](https://wiki.pinnacle.com/display/LaC/ISMS-PRO-13A+Change+Management+Procedure)

ISMS-POL-12 Change Management Policy

  

Document Code

ISMS-PRO-13A

Version

2.7

ISO 27001

\*

*   Add filter
*   Reset column sorting
*   Export to PDF
*   Export to CSV
*   Export to Word
*   Copy the filter URL
*   Modify Settings

*   [Documentation](https://docs.stiltsoft.com/display/TableFilter/How+to+use+Table+filter+macro?from=tf-view)
*   [What's new](https://docs.stiltsoft.com/display/TableFilter/Table+Filter+and+Charts+5.1.0?from=tf-view)

ISO 27001 Control = ≠Total Unique Issues:

Hide columns = ≠Issue Type

Showing the first all rows

Start adding filters in the filter tools menu.

The filter is disabled at the moment.

*   Export to PDF
*   Export to CSV
*   Export to Word

*   [Documentation](https://docs.stiltsoft.com/display/TableFilter/How+to+use+Table+filter+macro?from=tf-view)
*   [What's new](https://docs.stiltsoft.com/display/TableFilter/Table+Filter+and+Charts+5.1.0?from=tf-view)

Oops, it seems that you need to place a table or a macro generating a table within the Table Filter macro.

The table is being loaded. Please wait for a bit ...

[Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

ISO 27001 Control

Issue Type

Showing **0** of **0** statistics.  
[View in Jira](https://support.pinnaclesports.com/secure/IssueNavigator.jspa?reset=true&mode=hide&jqlQuery=key%3DISMS-23)

(function ($) { AJS.toInit(function () { var script = $('#tf-init-script-1563214888017\_1417738207-384633622--256402169'); if (!true) { //dd обрезается Panel / section macro script.parents('.panel, .alertPanel, .infoPanel, .innerCell').css('overflow', 'visible'); } script.remove(); //происходила повторная инициализация при открытии редактора var sorts = \[\]; var init = function () { var tf = new TableFilter({ showNRows: "all", limitHeight: "", heightValue: "", numbering: "", sorts: TableUtils.unescapeStrings(sorts), datepattern: "dd M yy", separator: ".", id: "1563214888017\_1417738207", pageId: "384633622", sparkline: false, sparkName: TableUtils.unescapeString("Sparkline"), order: "0,1", isOR: "AND", ddSeparator: TableUtils.unescapeString(""), fixedCols: "", totalrow: "", totalcol: "", isLockEnabled: false, worklog: "", updateSelectOptions: false, totalColName: TableUtils.unescapeString(""), totalRowName: TableUtils.unescapeString(""), thousandSeparator: "", tabs: false, sessionId: -256402169 }) if (tf == null) return; if ($('div.wiki-content.view-template').length) { tf.comboBoxDiv.find('button').removeAttr('aria-disabled'); tf.saveBtn.remove(); } }; var check = function () { if (window.TableFilter) { $('.tablefilter-outer-wrapper\[data-id="1563214888017\_1417738207"\]\[data-pageid="384633622"\]\[data-sessionid="-256402169"\] #comboBoxDiv-1563214888017\_1417738207').show(); init(); } else { $('.tablefilter-outer-wrapper\[data-id="1563214888017\_1417738207"\]\[data-pageid="384633622"\]\[data-sessionid="-256402169"\] #comboBoxDiv-1563214888017\_1417738207').hide(); setTimeout(check, 100); } } check(); }); })(AJS.$)

Document Status

[ISMS-23](https://support.pinnaclesports.com/browse/ISMS-23?src=confmacro) \- [Authenticate](https://wiki.pinnacle.com/plugins/servlet/applinks/oauth/login-dance/authorize?applicationLinkID=484b7744-c2a3-3df5-98d1-1f126c7d4299) to see issue details

Last Modified By

[Rod Mills](    /display/~rodm
)

Last Modified Date

Jul 15, 2019 14:25

Contributors

[Rod Mills](/display/~rodm) 10 (310 days ago),[Luis Embalo](/display/~luise) 4 (1025 days ago)

SME

IOC Team Lead

Reviewed By

Business Analysis Manager  
Development Manager  
Head of Security

Approved By

Head of Development  
Head of Infrastructure  
IT Operations Manager

Confidentiality Level

Medium

  

Change History
==============

Revisions

.aui td { white-space:nowrap; }

Version

Date

Comment

**[Current Version](/display/LaC/viewpage.action?pageId=384633622) (v. 14)**

**Jul 15, 2019 14:25**

**[Rod Mills](    /display/~rodm
)**

[v. 13](/display/LaC/viewpage.action?pageId=451812169)

Jul 15, 2019 14:24

**[Rod Mills](    /display/~rodm
)**

[v. 12](/display/LaC/viewpage.action?pageId=451812167)

Jul 15, 2019 14:23

**[Rod Mills](    /display/~rodm
)**

[v. 11](/display/LaC/viewpage.action?pageId=451812166)

Jun 11, 2018 09:31

**[Rod Mills](    /display/~rodm
)**

[v. 10](/display/LaC/viewpage.action?pageId=416092638)

Jun 11, 2018 09:25

**[Rod Mills](    /display/~rodm
)**

[v. 9](/display/LaC/viewpage.action?pageId=416092630)

Jun 08, 2018 09:17

**[Rod Mills](    /display/~rodm
)**

[v. 8](/display/LaC/viewpage.action?pageId=416092323)

Jun 08, 2018 08:29

**[Rod Mills](    /display/~rodm
)**

[v. 7](/display/LaC/viewpage.action?pageId=416092304)

Apr 17, 2018 02:31

**[Rod Mills](    /display/~rodm
)**

[v. 6](/display/LaC/viewpage.action?pageId=410583733)

Apr 16, 2018 02:32

**[Rod Mills](    /display/~rodm
)**

[v. 5](/display/LaC/viewpage.action?pageId=410583475)

Apr 09, 2018 01:58

**[Rod Mills](    /display/~rodm
)**

[v. 4](/display/LaC/viewpage.action?pageId=405746532)

Jul 31, 2017 00:56

**[Luis Embalo](    /display/~luise
)**

[v. 3](/display/LaC/viewpage.action?pageId=384634135)

Jul 28, 2017 04:34

**[Luis Embalo](    /display/~luise
)**

[v. 2](/display/LaC/viewpage.action?pageId=384633932)

Jul 28, 2017 04:15

**[Luis Embalo](    /display/~luise
)**

[v. 1](/display/LaC/viewpage.action?pageId=384633893)

Jul 27, 2017 03:21

**[Luis Embalo](    /display/~luise
)**

  

Table of Contents
=================

Table of Contents

/\*<!\[CDATA\[\*/ div.rbtoc1590083013365 {padding: 0px;} div.rbtoc1590083013365 ul {list-style: disc;margin-left: 0px;} div.rbtoc1590083013365 li {margin-left: 0px;padding-left: 0px;} /\*\]\]>\*/

*   1 [Change History](#DevOpsWorkflow-ChangeHistory)
*   2 [Table of Contents](#DevOpsWorkflow-TableofContents)
*   3 [1\. Purpose, scope and users](#DevOpsWorkflow-1.Purpose,scopeandusers)
*   4 [2\. Reference Documents](#DevOpsWorkflow-2.ReferenceDocuments)
*   5 [3\. Procedure](#DevOpsWorkflow-3.Procedure)
    *   5.1 [3.1.            Emergency Change procedure](#DevOpsWorkflow-3.1.EmergencyChangeprocedure)
    *   5.2 [3.2            Recurring Change flow](#DevOpsWorkflow-3.2RecurringChangeflow)
    *   5.3 [3.3            Recurring Change procedure](#DevOpsWorkflow-3.3RecurringChangeprocedure)
    *   5.4 [3.4.            Normal Change flow](#DevOpsWorkflow-3.4.NormalChangeflow)
    *   5.5 [3.5.            Normal Change procedure](#DevOpsWorkflow-3.5.NormalChangeprocedure)
*   6 [4\. Changes to the Sportsbook platform](#DevOpsWorkflow-4.ChangestotheSportsbookplatform)
    *   6.1 [4.1.            Incident Change Procedure](#DevOpsWorkflow-4.1.IncidentChangeProcedure)
    *   6.2 [4.2.            Bug Fix Change Procedure](#DevOpsWorkflow-4.2.BugFixChangeProcedure)
    *   6.3 [4.3.            Feature or Improvement Change Procedure](#DevOpsWorkflow-4.3.FeatureorImprovementChangeProcedure)
*   7 [5\. Managing records kept on the basis of this document](#DevOpsWorkflow-5.Managingrecordskeptonthebasisofthisdocument)
*   8 [6. Document management](#DevOpsWorkflow-6.Documentmanagement)

  

1\. Purpose, scope and users
============================

All changes to IT assets need to be requested, approved and implemented according to defined procedures, in accordance with the _Change Management Policy_. This document describes the high-level procedure[\[1\]](file:///C:/Users/alexisb/Qsync/7.Audit%20docs/Procedures/ISMS-PRO-13A%20Change%20Management%20Procedure%20V2.8.docx#_ftn1) for each category of change i.e. emergency, recurring and normal changes. More specifically, it describes per the sequence of activities pertaining to the process, the responsibilities per activity and the way to carry out these activities.

Users of this document are employees that will fulfill one of the roles in the Change Management process. See _Change Management Policy_ for more information.

**Role**

**Typical Pinnacle function performing role**

 Asset Owner

For instance, the Customer Management Applications are owned by Head of Customer Operations and the ASIDB is owned by the Database Manager. Refer to _Inventory of Assets_ for a complete list.

Change Initiator

Anyone in the organization authorized by an Asset Owner to request changes for his/her asset

Change Manager

IOC Team Lead, Lead Business Analyst or Project Portfolio Manager

Change Analyst

Business Analyst or System Engineer

Change Advisory Board (CAB)

A project CAB should consist of at least the following roles:

*   Asset Owner
*   Project Sponsor (i.e. Executive stakeholder)
*   Change Manager

Change Implementer

IT Development team or Infrastructure team.

Technical Quality Assurance Tester

Embedded QA testers in the various development teams or IOC engineers

Business Quality Assurance Tester

Change Initiators and/or persons appointed by Change Initiators, e.g. end-users directly impacted by the change

Release and Deployment Manager

Integrated Operations Center (IOC)

Steering Committee

Committee consisting of the CEO, various members of the executive team and senior management team, including Project Portfolio Manager.

  

* * *

[\[1\]](file:///C:/Users/alexisb/Qsync/7.Audit%20docs/Procedures/ISMS-PRO-13A%20Change%20Management%20Procedure%20V2.8.docx#_ftnref1) Per ISO 9000:2005, a procedure is a “specified way to carry out an activity or a process”

  

2\. Reference Documents
=======================

*   ISO/IEC 27001 standard, clauses A.12.1.2 and A.14.2.4
*   ISMS-POL-13 Change Management Policy
*   ISMS-PRO-23 Incident Management Procedure

  

3\. Procedure
=============

3.1.            Emergency Change procedure
------------------------------------------

**Activity**

**Description**

**Role responsible for activity**

Report issue to IOC

When an unexpected error or threat occurs to an IT asset, the End User / Reporter contacts IOC to report the incident.

End User / Reporter

Incident Management Procedure SEV-1

If urgent changes to IT Assets are required due to an incident, IOC categorizes the incident as Severity-1 (Sev-1). Emergency changes are handled according to the Sev-1 flow documented in the Incident Management Procedure. IOC will notify the Asset Owner of the occurrence and of the resolution. See Incident Management Procedure for more information.

IOC

  

3.2            Recurring Change flow
------------------------------------

![](attachments/384633622/451812161.png)

  

3.3            Recurring Change procedure
-----------------------------------------

**Activity**

**Description**

**Role responsible for activity**

Identify necessity for recurring change

When a Change Manager or Change Initiator identifies the necessity for a recurring change to a Pinnacle information asset, he/she will notify the Asset Owner.

Change Manager

Change Initiator

Authorize change in Authorization tool

If the Asset Owner agrees with the change, he/she grants the required permissions in the Authorization tool to one or more implementers to implement the change on a recurring basis.

Asset Owner

Create master entry in CM tool

After authorization, the Asset Owner creates a single master entry for the recurring change in Jira. This entry includes the:

*   Change description
*   Authorization list
    *   Date of authorization
    *   Authorized implementer(s)
*   Change start date
*   Recurrence schedule

Asset Owner

Update recurring changes list

If the used CM tool does not provide the capability to track a list of all changes, the Asset Owner is responsible for updating a changes list for audit purposes. He/she needs to add a reference to the master entry per change.

Asset Owner

Write SOP

After the recurring change is authorized and the master entry has been created, the assigned Change Analyst writes the Standard Operating Procedure (SOP). The SOP should include the following:

*   Scope and applicability: describe the purpose of the process, its limits, and how it's used. Include standards, regulatory requirements, roles and responsibilities, and inputs and outputs.
*   Methodology and procedures: list all the steps with necessary details, including what equipment needed. Cover sequential procedures and decision factors.
*   Cautions and interferences: Cover what could go wrong, what to look out for, and what may interfere with the final, ideal product.

Change Analyst

Write test plan

After the SOP has been written, an assigned Technical QA Tester writes a test plan for the SOP.

Technical QA Tester

 Test SOP

The technical QA Tester will test the SOP according to the test plan to determine if it can be successfully executed. Only after successful testing will the recurring changes be scheduled into production.

If testing of the SOP was unsuccessful, the Change Analyst is notified to make the necessary updates to the SOP.

Technical QA Tester

Update master entry in CM tool

After successful testing of the SOP, the Change Analyst updates the master entry with a reference to the SOP.

Change Analyst

Execute change

The authorized Implementer will execute the recurring changes in accordance with the recurrence schedule, according to the SOP.

If exceptions occur during execution of the change, the Incident Management Procedure will be triggered.

Change Implementer

Update change log in CM tool

For each recurrence (i.e. executed change), the Implementer updates the change log in Jira. The log entry includes:

*   Change date
*   Change executor
*   Any Incidents/Exceptions that occurred

Change Implementer

  

3.4.            Normal Change flow
----------------------------------

![](attachments/384633622/451812162.png)

  

3.5.            Normal Change procedure
---------------------------------------

**Activity**

**Description**

**Role responsible for activity**

Submit Request for Change (RFC)

When an Asset Owner or a Change Initiator recognizes and identifies a need for a normal change to a Pinnacle information asset, he/she submits an RFC with at a minimum the following information:

*   Name change Initiator
*   Name of asset requiring change
*   Name of Asset Owner
*   Description of the change required
*   Reason/Business Justification for the Change
*   Priority indication (urgent, high, medium, low)
*   Date change is required by

Asset Owner

Change Initiator

Verify Change Initiator authorization

The Change Manager checks if the Change Initiator is authorized by the Asset Owner to request changes for his/her asset. The Change Manager will only process RFCs initiated by authorized persons.

Change Manager

Verify completeness and correctness of RFC

The Change Manager checks if the minimum set of information to be provided has been provided in the RFC and if the RFC form was filled in correctly. If the RFC is incomplete or incorrect, the Change Initiator is requested to adapt the RFC. When adapted, the Change Initiator returns the RFC to the Change Manager.

Change Manager

Document RFC in Jira (our Change Management tool)

The Change Manager creates a Jira ticket on the Project Portfolio board for the RFC and copies the provided information onto the Jira ticket.

Change Manager

Prioritize RFCs

The Change Manager monitors all submitted RFCs via Jira on a daily basis. The Change Manager will assess the priority to decide which changes will be discussed and performed first. The Change Manager assigns an initial priority (Low, Medium, High) based on information provided in the RFC. The priority of RFCs will be decided in collaboration with the Change Initiator and/or CAB and/or Steering Committee if necessary.

Change Manager

Assess risk and impact of change

The Change Analyst(s) need to assess the constraints, the risks and the impact to the business. Such as risks to business continuity and impact on resource planning as a consequence of the change.

Where necessary, the Change Analyst(s) will make recommendations to support the Steering Committee or CAB with its approval decisions.

Change Analyst(s)

Identify CAB or form new CAB

After the Change Analyst has completed the risk and impact assessment, the Change Manager will identify the appropriate CAB based on the type of asset subject to change and relevancy. If there is no existing CAB that is fitting, the Change Manager ensures that a new CAB is formed on a project basis. The Change Manager coordinates that a meeting is planned for the approval of the RFC by the SC or CAB.

Change Manager

Issue or deny Technical and business approval

The SC or CAB needs to make a go/no-go decision for the RFC. For a go decision, they must issue both a technical and business approval. The change will be further planned and analyzed for implementation only if approved.

_Technical approval_

If found that the change is feasible, sensible and can be performed without causing inappropriate harm to the services provided to the business, the SC or CAB members issue a technical approval.

_Business approval_

If found that the change satisfies the business requirements, at least the Asset Owner issues the business approval (and if applicable, other Business Representatives impacted by the change that also form part of the CAB).

In some cases, to better support decision-making, the Change Analyst in coordination with technical Subject Matter Experts (e.g. Security or other Technical Experts) need to provide additional supporting information.

If a technical or business approval is not issued, the SC or CAB rejects the change.

CAB

Issue or deny Financial approval

In case the change involves a capital investment, a go/no-go decision will additionally depend on a financial approval. In this case, at least the Executive Member of the SC or CAB needs to assess the cost of the change. If the change is within approved budgetary limits or meets set cost-benefit criteria, she/he issues a financial approval.

CAB

Document reason for rejection

In case the RFC has been rejected, the Change Manager will register the reason in the Jira ticket and close the Jira ticket.

Change Manager

Create change and communication plan

If the change request has been approved, the Change Manager can start with the planning which will be executed throughout the engagement:

*   The Change Manager creates a change plan outlining the scope, needed resources and timeline
*   The Change Manager creates a stakeholder engagement plan and a communication plan

Change Manager

Analyze change requirements

If the change request has been approved, Change Analysts will analyze and document the change requirements.

Where needed, they will elicit additional information from the Change Initiator (e.g. business objectives/stakeholder requirements) and Subject Matter Experts (e.g. Security SME to review security aspects or Legal SME to analyze legal requirements).

The Change Analysts document the following requirements and criteria as part of the RFC:

*   Functional requirements
*   Quality requirements
*   Acceptance criteria

Change Analyst

Sign-off change requirements

The Change Initiator obtains all documented change requirements and assesses if they meet the agreed business objectives and if they are in alignment with the stakeholder requirements. If so, the Change Initiator signs-off the change requirements.  

The implementation phase can only commence if all change requirements are signed-off. The Change Analysts will re-evaluate and update the documentation accordingly as needed to obtain a sign-off.

Change Initiator

Create Jira tickets on change implementer boards

The Change Analyst creates Jira tickets in the backlog of the change implementer boards and links them to the project ticket on the project portfolio board.

Change Analyst

Define technical requirements

The Change Implementer obtains the functional and quality requirements documentation from the Change Analyst. In alignment with these requirements, the Change Implementer defines and documents the technical requirements (e.g. software development requirements or technical infrastructure requirements).

Change Implementer

Write test plans for technical QA

Based on the documented change requirements (both business and technical) and defined acceptance criteria, the Technical QA Tester writes test plans to be used for technical QA, independently from the Change Implementer.

This includes:

*   Plans for functional testing
*   Plans for regression testing
*   Plans for security testing
*   Plans to test other quality requirements

Technical QA Tester

Write test plans for User Acceptance Testing (UAT)

In parallel with the writing the technical QA tests, the Business QA Tester writes User Acceptance test plans to be used to test if stakeholder/end-user requirements were met. These are the tests that will be used for acceptance sign-off by the Change Initiator.

Support from Change Analysts may be sought to help with writing the test plans.

Business QA Tester

Build or configure change

After sign-off of the change requirements, the assigned Change Implementer starts building or configuring the required change, according to the documented requirements. The nature of the implementation will depend on the type of asset and change. While Business Software might be primarily development (build) driven, changes to Hardware might be primarily configuration driven.

Change Implementer

Create rollback plan

The Change Implementer makes a rollback plan to follow in case a change is not successful.

Change Implementer

Perform technical QA testing

After the change is built or configured, the Technical Quality Assurance Testers perform technical QA testing in accordance with their test plans. If the change failed testing, the Technical QA Tester creates one or more tickets of type “bug” on the change implementer board. These tickets need to be resolved by the Change Implementer.

Technical QA Tester

Perform User Acceptance Testing

After the change is built or configured, if the technical QA testing succeeded, the Business Quality Assurance Testers perform User Acceptance Testing in accordance with their test plans. If the change did not meet acceptance criteria, the Business Quality Assurance Testers creates one or more tickets of type “UAT issue” within Jira on the Change Implementer board. These tickets need to be resolved by the Change Implementer.

Business QA Tester

Sign-off UAT

The Change Initiator obtains the documented UAT results from the Business QA Tester and is informed of the results. If the Change Initiator accepts the change, he/she needs to sign-off on the results.

Change Initiators must sign off on User Acceptance of the changes before deployment into production can commence.

Change Initiator

Request Deployment into production

After sign-off of the UAT by the Change Initiator, the Change Implementer creates a release ticket in Jira on the Release Board.  This ticket at a minimum must contain:

*   Impact of the change
*   Goal of the change
*   Change implementer
*   Reference to the ticket on the change implementer board in Jira

Change Implementer

Deploy into production

The Release and Deployment Manager will ensure that the QA has been signed off and then coordinates the release of the change into the production environment.

After deployment has been successfully completed, he/she records the following in the Jira release ticket:

*   Deployment date and duration
*   Who deployed the release

Release and Deployment Manager

Execute rollback plan

In case a deployed change is not successful, the Release and Deployment Manager executes the rollback plan and communicates this to the Change Manager. After completion, he/she records the following in the Jira release ticket:

*   Rollback date and duration
*   Issues encountered

Release and Deployment Manager

Close Change

The Change Manager will close the change in Jira after all required documentation for audit purposes has been gathered and the Post-Implementation evaluation has been completed.

Change Manager

  

4\. Changes to the Sportsbook platform
======================================

4.1.            Incident Change Procedure
-----------------------------------------

![](attachments/384633622/451812163.jpg)

**Activity**

**Description**

**Role responsible for activity**

Receive Incident Ticket through Jira

IOC will receive the ticket about the incident through Jira

Technical QA Tester

Collect additional incident information

IOC will collect as much details as possible about this incident for the change implementer

Technical QA Tester

Investigate Incident

With the information gathered the change implementer will troubleshoot the incident, the change implementer will try to recreate this incident during troubleshooting

Change Implementer

Develop fix

The Change Implementer will develop a fix for the incident at hand to repair the situation

Change Implementer

Release to DEV

The fix will be released in the DEV environment by the change implementer

Change Implementer

Test SOP

The technical QA Tester will test the SOP to conquer the fix indeed resolved the incident at hand.

Only after successful testing will the fix be scheduled into UAT and production. If testing of the SOP was unsuccessful, the change implementer will be notified to correct the behaviour

Technical QA Tester

Create Jira RBP Ticket

Change Implementer creates a release ticket in Jira on the Release Board. This ticket at a minimum must contain:

*   Impact of the change
*   Goal of the change
*   Change implementer
*   Reference to the ticket on the change implementer board in Jira
*   Octopus deployment URL

TeamCity project build URL

Change Implementer

Release to UAT

The feature will be released to UAT by the IOC.

If successful, it will be pushed through to production after, if unsuccessful, the change implementer will be notified of the unusual behaviour and will have to keep troubleshooting

Release and Deployment Manager

Release to Production

The feature will be released to Production by the IOC.

If successful, the Jira ticket will be closed by IOC, if unsuccessful, the change implementer will be notified of the unusual behaviour and will have to keep troubleshooting, at the same time a revert will take place to remove the fix from production

Release and Deployment Manager

  

4.2.            Bug Fix Change Procedure
----------------------------------------

![](attachments/384633622/451812164.jpg)

**Activity**

**Description**

**Role responsible for activity**

Identify high priority bugs in roadmap overview

IOC will receive the ticket about the incident through Jira

Technical QA Tester

Investigate Incident

With the information gathered the change implementer will troubleshoot the incident, the change implementer will try to recreate this incident during troubleshooting

Change Implementer

Develop fix

The Change Implementer will develop a fix for the incident at hand to repair the situation

Change Implementer

Release to DEV

The fix will be released in the DEV environment by the change implementer

Change Implementer

Test SOP

The technical QA Tester will test the SOP to conquer the fix indeed resolved the incident at hand.

Only after successful testing will the fix be scheduled into UAT and production. If testing of the SOP was unsuccessful, the change implementer will be notified to correct the behaviour

Technical QA Tester

Create Jira RBP Ticket

Change Implementer creates a release ticket in Jira on the Release Board. This ticket at a minimum must contain:

*   Impact of the change
*   Goal of the change
*   Change implementer
*   Reference to the ticket on the change implementer board in Jira
*   Octopus deployment URL
*   TeamCity project build URL

Change Implementer

Release to UAT

The feature will be released to UAT by the IOC.

If successful, it will be pushed through to production after, if unsuccessful, the change implementer will be notified of the unusual behavior and will have to keep troubleshooting

Release and Deployment Manager

Release to Production

The feature will be deployed to Production by the IOC.

If successful, the Jira ticket will be closed by IOC, if unsuccessful, the change implementer will be notified of the unusual behavior and will have to keep troubleshooting, at the same time a revert will take place to remove the fix from production

Release and Deployment Manager

  

4.3.            Feature or Improvement Change Procedure
-------------------------------------------------------

![](attachments/384633622/451812165.jpg)  

**Activity**

**Description**

**Role responsible for activity**

Identify change priority in roadmap

Go through the team’s roadmap overview and develop feature according to the business priority

Change Manager/Asset Owner

Gather business requirements

Perform the due diligence for chosen feature

Change Analyst

Write SOP

The assigned Change Analyst writes the Standard Operating Procedure (SOP).

The SOP should include the following:

*   Scope and applicability: describe the purpose of the process, its limits, and how it's used. Include standards, regulatory requirements, roles and responsibilities, and inputs and outputs.
*   Methodology and procedures: list all the steps with necessary details, including what equipment needed. Cover sequential procedures and decision factors.

Caution: Cover what could go wrong, what to look out for, and what may interfere with the final, ideal product.

Change Analyst

Write test case

Based on the documented change requirements (both business and technical) and defined acceptance criteria, the Technical QA Tester writes test plans to be used for technical QA, independently from Change Implementers. This includes:

*   Plans for functional testing
*   Plans for regression testing
*   Plans for security testing
*   Plans to test other quality requirements.

Technical QA Tester

Develop Feature

Once all the information has been gathered and the SOP written, the development team will start to code the feature.

Change Implementer

Deploy to DEV

When the development team believes that feature is up to standard It will deployed to the development environment for testing.

Change Implementer

Test SOP

The technical QA Tester will test the SOP according to the test plan to determine if it can be successfully executed. Only after successful testing will the recurring changes be scheduled into production.

If testing of the SOP was unsuccessful, the Change Analyst is notified to make the necessary updates to the SOP or the development team is notified to correct the wrong behaviour.

Technical QA Tester

Create Jira RBP Ticket

Change Implementer creates a release ticket in Jira on the Release Board. This ticket at a minimum must contain:

*   Impact of the change
*   Goal of the change
*   Change implementer
*   Reference to the ticket on the change implementer board in Jira
*   Octopus deployment url
*   TeamCity project build url

Change Implementer

Release to UAT

The feature will be released to UAT by the IOC.

If successful, it will be pushed through to production after, if unsuccessful, the change implementer will be notified of the unusual behaviour and will have to troubleshoot and fix the feature.

Release and Deployment Manager

Release to Production

The feature will be released to Production by the IOC.

If successful, the Jira ticket will be closed by IOC, if unsuccessful, the change implementer will be notified of the unusual behaviour and will have to troubleshot and fix the feature at the same time a revert will take place to remove the new feature from production

Release and Deployment Manager

  

5\. Managing records kept on the basis of this document
=======================================================

**Record name**

**Storage location**

**Person responsible for storage**

**Controls for record protection**

**Retention time**

Change Management procedure

Document repository

IT Operation Manager

Folder access permissions

5 years

  

6. Document management
======================

The owner of this document is _Head of Development_ who must check, and, if necessary, update the document at least once a year.

When evaluating the effectiveness and adequacy of this document, the following criteria need to be considered:

*   Number of users with more/less privileges than required for their job role
*   Number of user accounts created by using this process
*   Number of exceptions approved per department manager/asset owner

  

  

  

  

  

  

  

  

  

  

Attachments:
------------

![](images/icons/bullet_blue.gif) [DevOps Workflow - Sequential Feature.png](attachments/462586629/462586632.png) (image/png)  
![](images/icons/bullet_blue.gif) [DevOps Workflow - Sequential Hotfix.png](attachments/462586629/462586633.png) (image/png)  
![](images/icons/bullet_blue.gif) [DevOps Workflow.vsdx](attachments/462586629/462586642.vsdx) (application/octet-stream)  



