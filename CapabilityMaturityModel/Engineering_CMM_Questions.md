

## Meeting Information
<table>
	<colgroup>
		<col  style="width: 30%" />
		<col  style="width: 70%" />
	</colgroup>
	<tbody>
		<tr>
			<td>Squad</td>
			<td></td>
		</tr>
		<tr>
			<td>Location</td>
			<td></td>
		</tr>		
		<tr>
			<td>Date & Time</td>
			<td></td>
		</tr>		
		<tr>
			<td>Attendees</td>
			<td></td>
		</tr>		
	</tbody>
</table>

## Rules
- Scoring
	- Evidence type Questions:  With boolean (Yes/No) answers have a score of 1 or 0 points. 
	- Evidence type Metric: Refer to notes within that cell
- The average score is calculated for each Aspect.
- Recommendations are based on conclusions and results from this document, for later to create a Engineering Health Check document to prioritized together with the squad. 

# Levels
## CMM Levels
<table>
	<colgroup>
		<col  style="width: 30%" />
		<col  style="width: 70%" />
	</colgroup>
	<tbody>
		<tr>
			<td>Level</td>
			<td>Description</td>
		</tr>
		<tr>
			<td>L1 - Learning</td>
			<td>
				<ul>
					<li>Squad characterized by little systematic methods</li>
					<li>The Squad is using ad hoc or standard practice might have existed are abandoned during crisis.</li>
                    <li>No key process areas</li>
                    <li>Unstable environment for software development</li>
                    <li>No basis for predicting product quality or time for completion</li>
				</ul>
			</td>
		</tr>		
		<tr>
			<td>L2 - Practicing </td>
			<td>
				<ul>
					<li>Squad are characterized by individual control</li>
					<li>Focuses on established basic project management policy</li>
                    <li>Configuration Management: Focus is on maintaining the performance of the software product</li>
                    <li>Requirements Management: Review and feedback which results in some changes in the requirements set.  Consists of accommodation of those modified requirements</li>
                    <li>Software Quality: Guarantees a good quality software product by following certain criteria and quality standard guidelines while development</li>
				</ul>
			</td>
		</tr>
		<tr>
			<td>L3 - Systematic</td>
			<td>
				<ul>
					<li>Squad institutionalize process, code review, inter-squad coordination, software product engineering, integrated software management, training programs, and organization process defined and focus</li>
					<li>Documentation of standards guidelines and procedures are defined and followed</li>
                    <li>Code Reviews on architecture design pattern, application design patterns, code format.</li>
                    <li>Inter-team coordination and collaboration: Interacting between different squads and departments</li>
                    <li>Organization & Squad Process definition: focus on the development and maintenance of standard development process</li>
					<li>Organization & Squad Process focus: Activities and practices that should be followed to improve the process capabilities of an organization</li>
					<li>Training Programs: Focus on enhancement of knowledge and skills for the Squad and insures an increase in work efficiency</li>
				</ul>
			</td>
		</tr>
		<tr>
			<td>L4 - Measuring</td>
			<td>
				<ul>
					<li>Organization & Squad incorporate process measurement and apply quality management as well as process measurement and analysis</li>
					<li>Quantitative quality goals are set for the Organization & Squad on the software product and process</li>
                    <li>Quality threshold are defined and set</li>
                    <li>Measurements are set to help the Organization & Squad to predict the product and process quality with some limits defined quantitatively</li>
                    <li>Established plans and strategies to development quantitative analysis and understanding of the product quality</li>
					<li>Organization & Squad Process focus: Activities and practices that should be followed to improve the process capabilities of an organization</li>
					<li>Focus on controlling the project velocity</li>
				</ul>
			</td>
		</tr>
		<tr>
			<td>L5 - Innovation</td>
			<td>
				<ul>
					<li>Squad obtain feedback for improvement through Change Management, technology innovation, and defect prevention</li>
					<li>Process Change Management: Squads continuous improvement, productivity, quality and cycle time</li>
                    <li>Technology Change Management: Identification new technology to improve the product quality and decrease product development time</li>
                    <li>Defect Prevention: Identification of causes of defects and to prevent them from recurring in future Stories by improving project and defined process</li>
				</ul>
			</td>
		</tr>				
	</tbody>
</table>
  
## Development Aspects
<table>
	<colgroup>
		<col  style="width: 20%" />
		<col  style="width: 30%" />
		<col  style="width: 20%" />
		<col  style="width: 30%" />
	</colgroup>
	<tbody>
		<tr>
			<td>Source Code Management (SCM)</td>
			<td>
				<ul>
					<li>Branch lifetime  (or non develop, master/main) branch exists/before it is removed</li>
					<li>Duration it takes to merge (after code review approval, feature branch to develop branch, includes merge issue duration) on per request</li>
				</ul>
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td></td>
			<td>
				<ul>
					<li>( Rejected Pull Requests (PR) ) Percentage code rejection against (feature) branch on squad over a sprint</li>
					<li>Percentage code not getting reviewed against (feature) branch on squad over a sprint</li>
					<li>( Code Churn - Rework ) Percentage code refactor is dong on rejection per sprint</li>
					<li>Resolution to Resolve (RTR) - Average time taken to resolve pull requests, merge and decline</li>
				</ul>
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>Technical Standards</td>
			<td>
				<ul>
					<li>dentify is there an established code principle that reduces dependencies and its repeatable</li>
				</ul>
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>Technical Process</td>
			<td>
				<ul>
					<li>Agile Software Development process or methodology (any options below). Are you following any methodology and gates in place that measures it.</li>
				</ul>
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>Technical Debt</td>
			<td>
				<ul>
					<li>( Code Churn / Technical Debt Ratio - Rework ) Percentage code refactor to resolve defects (QA to Production found)</li>
					<li>( Code Churn - Rework ) Percentage code being Added, Deleted/Comment Out, and refactored on average per sprint to complete the Stories in the sprint</li>
				</ul>
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>Collaboration (Tools)</td>
			<td>
				<ul>
					<li>Is there a fluid process to communicate, demonstrate, and collaborate with non-sqaud or non-tribe members ( that would impact their work like external SME...  ie: Architect, Security, Database, Network, Monitoring, Data Engineers - no db interaction, ...  )</li>
				</ul>
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>Self-Improvements</td>
			<td>
				<ul>
					<li>What is the Cyclomatic Complexity / Code Complexity index value</li>
					<li>What is the Code Duplication percentage</li>
				</ul>
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>Coding Policy</td>
			<td>
				<ul>
					<li>Policy Documentation</li>
				</ul>
			</td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td>Confluence / Documentation</td>
			<td>
				<ul>
					<li>Standard, process, architecture, documentation</li>
				</ul>
			</td>
			<td></td>
			<td></td>
		</tr>											
	</tbody>
</table>




------- need to update below...


## Questionary
<table>
	<colgroup>
		<col  style="width: 12%" />
		<col  style="width: 12%" />
		<col  style="width: 12%" />
		<col  style="width: 12%" />
		<col  style="width: 12%" />
		<col  style="width: 12%" />
		<col  style="width: 12%" />
		<col  style="width: 12%" />
		<col  style="width: 12%" />
		<col  style="width: 12%" />
	</colgroup>
	<tbody>
		<tr>
			<td>Aspects</td>
			<td>Description</td>
			<td>Basic Statement (L1)</td>
			<td>Acceptable Statement (L3)</td>
			<td>Excellent Statement (L5)</td>
			<td>Evidence Type</td>
			<td>Evidence</td>
			<td>Question</td>
			<td>Acceptable</td>
			<td>Excellent</td>
			<td>Team</td>
			<td>Comments</td>	
		</tr>
		<tr>
			<td>Test Process (level 2 (2/8 points) </td>
			<td>The process examines the quality of the "end products" and the final outcome. Set up test process on the project, QA involvement into SDLC activates, visibility and transparency around testing activates</td>
			<td>The testing process is clear inside the QA team, at least manual testing is a part of DoD, QAs are a part of SCRUM ceremonies. Testing activities start in parallel with development (test cases creation, data preparation, etc).</td>
			<td>The testing process is fully clear for the whole team, including QAs, devs, POs, etc. Testing (including automation tests) is s part of DoD for feature stories. QAs participate in all SCRUM ceremonies, where required. The testing effort is a part of the total estimation of stories.</td>
			<td>Excellent Statement (L5)</td>
			<td>Evidence Type</td>
			<td>Evidence</td>
			<td>Question</td>
			<td colspan=4>
				<table>
					<tr>
						<td>Question</td>
						<td>Is Testing a part of DoD for each feature story?</td>
						<td>What is your definition of done?  
                            Do you test every single feature before considering it as done?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Is There a QA manager/lead who drives the testing process?</td>
						<td>How do you organize the QA work? Is it part of the standard team ceremonies? Do you follow the same estimation process, standup reports...?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Do QA team members participate in Agile ceremonies?</td>
						<td>Are the QA part of all the Agile ceremonies, like poker planning, 3 amigos...?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Does QA team member start working on a story in parallel to the developer and communicate with developers & POs to provide feedback and align testing scope/plan?</td>
						<td>When a new Sprint starts, what does a QA member usually do? Feature file description, add a new test to Xray, is this done in parallel with a developer? Is there communication with the developer / PO?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Is The testing effort a part of the total estimation of stories?</td>
						<td>When the team is doing the estimation before the sprint planning, do you consider the effort of testing as part of the estimation? all testing, manual, automation, including functional and non-functional?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Is the Testing process defined and transparent allowing other squad members to step in when needed?</td>
						<td>If the manual QA needs help because they are overloaded, can the Developers, or PO help with some test? Do they follow the process defined (Use Xray execution, upload results ...)</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Is there a Test Plan prepared for each release?</td>
						<td>Do you have a dedicated test plan or execution per release/sprint? so every new feature developed in the sprint is added to the master plan?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Is there a test coverage review meeting (3 amigos) held for each release?</td>
						<td>How do you keep the balance between automation and manual? Do you review your test coverage per release?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>										
				</table>	
			</td>
		</tr>
		<tr>
			<td>Test Strategy</td>
			<td>Overall test strategy on the project, clear understanding of how testing runs and integrated into SDLC process</td>
			<td>Test strategy is partially documented and the squad is partially following it</td>
			<td>Test strategy is documented and the squad is partially following it</td>
			<td>Test Strategy is documented and fully followed by the squad. STLC is fully integrated with the SDLC</td>
			<td colspan=4>
				<table>
					<tr>
						<td>Question</td>
						<td>Is Testing a part of DoD for each feature story?</td>
						<td>What is your definition of done?  
                            Do you test every single feature before considering it as done?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Are selected tools in line with tools used for the whole organization?</td>
						<td>What tools are you using for your testing both for manual and automation pieces?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Is Test reporting and visibility on the testing process clear for all team members?</td>
						<td>Who is responsible for creating Test reports? Is it done manually or in an automated way? Does everyone from the team have access to the reports?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Is Exploratory testing in place?</td>
						<td>Do you have exploratory testing? If yes - how often and who is involved in this process?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Does Regression testing happen regularly?</td>
						<td>Could you, please, describe your Regression testing process?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
                </table>
            </td>
		</tr>
		<tr>
			<td>Test Case Management process</td>
			<td>Process of creating, updating, executing test cases, list of test cases executing on different stages</td>
            <td>Test cases are not written for testing.</td>
			<td>There is a Test Case Management Tool, which is aligned with what is used for the whole organization. At least 80% of stories are covered with test cases. All test cases are split by test suites for Smoke and Regression executions.</td>
			<td>There is a Test Case Management Tool, which is aligned with what is used for the whole organization. All stories are covered with test cases, which are split by test suites for Smoke and Regression executions. A traceability matrix is created and there is a place to look at what stories are covered by which test cases.</td>
			<td colspan=4>
				<table>
					<tr>
						<td>Question</td>
						<td>Is there a single source of truth for manual test cases (Xray)?</td>
						<td>Do you use Xray to document testing scenarios, prepare the test plans, and record executions?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Does the requirement traceability matrix exist?</td>
						<td>How do you track what functionalities are covered with tests and what are missing? Do you have a traceability matrix?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>What is your level of test coverage?</td>
						<td>How many features are covered with tests? </td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Do the PO or developers review the tests?</td>
						<td>Is there someone besides the QA team who reviews test cases? Devs, POs?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Do you have the test category "Smoke" and "Regression" defined?</td>
						<td>How do you categorized and split tests? Do you have Smoke, Regression test suites defined?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
                </table>
            </td>
		</tr>
		<tr>
			<td>Defect Management</td>
			<td>Process of defect creation, handling opened defects</td>
            <td>Defects are not tracked, therefore the team does not triage or perform root analysis of the defects found.</td>
			<td>Defects are tracked in Jira to the original feature's requirement. There isn't a ceremony for defects triage and prioritization is not according to the impact</td>
			<td>Defects are tracked in Jira to the original feature's requirement. The team triages the defects and give the right priority according to the impact</td>
			<td colspan=4>
				<table>
					<tr>
						<td>Question</td>
						<td>Do you track found defects into a bug tracking system?</td>
						<td>When you find a bug, what do you do? how do you track the life cycle of the bug?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Do you link in Jira, defects to a feature's requirement?</td>
						<td>Do you link in Jira, defects to a feature's requirement?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Do you have a template for defects creation process?</td>
						<td>Do you have a template for defects creation process? 
                            What fields are mandatory?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Are all mandatory fields, like Priority, Environment, Device, Build #, etc are filled in during defect creation?</td>
						<td>Is there a list of all mandatory fields for defects creation defined and followed?
                            Are all mandatory fields, like Priority, Environment, Device, Build #, etc are filled in during defect creation?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Are there any retrospectives (actions items/root cause analyses) done on defects area?
                            For instance: the most problematic functionality, area with the most invalid bugs, etc.</td>
						<td>Are there any retrospectives (actions items/root cause analyses) done on defects area?
                            For instance: the most problematic functionality, area with the most invalid bugs, etc.</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Do you have a process for defects triage?</td>
						<td>How does the team know what is the most important bug to fix? How do you give the severity or priorities to the bug? Does the team review this?
                            How often do you review your bug backlog? Do you treat them as a normal feature or do they have different ceremonies to triage them?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>What is the average time to fix the critical bug?.</td>
						<td>If a bug is found in UAT/Staging how long does it take to put it back into the team backlog? If the bug is found during the sprint how long does it take?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>How many bugs are closed as invalid?</td>
						<td>Sometimes bugs raise by QA do not contain enough information, or are not a real bug (For example QA misunderstood the requirement), how often does it happen?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>                                        
                </table>
            </td>
		</tr>
		<tr>
			<td>QA Metrics</td>
			<td>Process of measuring the effectiveness of QA process, visibility on the testing activities, and product stability</td>
            <td>QA metrics are not measured.</td>
			<td>QA metrics for Defect Managements and Test Automation are measured.</td>
			<td>QA metrics for Defect Managements and Test Automation are measured in an automated way. Also, some action items are built based on Metric results.</td>
			<td colspan=4>
				<table>
					<tr>
						<td>Question</td>
						<td>Are Metrics around the Defect management area measured?</td>
						<td>How do you track your QA progress? Are there any metrics/dashboards for the Defect Management area?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Are Metrics around the Test Automation area measured?</td>
						<td>Are there any metrics/dashboards for the Test Automation area?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Are metrics measured in an automated way?</td>
						<td>If yes for previous, how are you creating your dashboards?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Is Retro and action plan based on metrics results happening?</td>
						<td>Based on metrics that you are receiving - are there any action items created?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
                </table>
            </td>
		</tr>
		<tr>
			<td>Test Automation and Quality Gates</td>
			<td>The level of maturity in test automation area, including quality gates, following testing pyramid.</td>
            <td>There is not automation tests or metrics that measure the level of coverage</td>
			<td>There are automation tests and they run as part of the CI pipeline, but results and metrics are not used to influence the pipeline and prevent code changes with not enough quality changes to be merged into the main branch.</td>
			<td>There are automation tests that run continuously and prevent code changes with regression to be merged into the main source code branch</td>
			<td colspan=4>
				<table>
					<tr>
						<td>Question</td>
						<td>Does In-Sprint automation present?</td>
						<td>Do you cover each feature with automation tests and automation tests are a part of DoD and done in the same sprint as feature item?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Do you calculate the code coverage for every build? </td>
						<td>When was the last time you measure the code coverage? Is it done automatically as part of the CI pipeline? A drop in the code coverage makes the build fail? </td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Do you create unit tests for new functionalities and it is a part of DoD?</td>
						<td>Are Unit tests mandatory to consider a given functionality ready to be tested? 	</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>What are your tests type distribution according to the test pyramid?</td>
						<td>Do you have Unit test, integration test (Tests where you mock your dependencies), and E2E where you test everything together? How often do you execute them?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Do you have some smoke automated tests running on UAT/Prod continuously after each release?</td>
						<td>Are you reusing your test to keep them running continuously in production and notify the team when something is not working as expected?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Are Quality Gates established, defined, and followed for each stage/environment?</td>
						<td>What are the quality gates that the team follows in order to decide if a given release can be promoted from and environment to the next?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Metric</td>
						<td>Is Automation testing a part of the testing strategy?</td>
						<td>Do you have any automation tests?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Metric</td>
						<td>Coverage for unit tests</td>
						<td>Do you have Unit test? If yes what is the code coverage? </td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>                                        
                </table>
            </td>
		</tr>
		<tr>
			<td>Test Execution and Reporting</td>
			<td>There are either no automation tests, or all automation tests are executed locally, there is no reporting for automation tests. Only automation QA could execute tests and know where to find the results.</td>
            <td>The majority of the tests are integrated into pipelines and executed on a regular basis. The pass rate for automation tests is close to 90%. QAs and developers have access to view the test results of test execution.</td>
			<td>There is a Test Case Management Tool, which is aligned with what is used for the whole organization. At least 80% of stories are covered with test cases. All test cases are split by test suites for Smoke and Regression executions.</td>
			<td>Automation tests are integrated into pipelines and executed on a regular basis. Automation tests are split for Smoke and Regression test suites and the pass rate is close to 99%. There is a single source of truth for manual and automation test cases, where everyone from the team is able to view the test results.</td>
			<td colspan=4>
				<table>
					<tr>
						<td>Question</td>
						<td>Are all automated tests integrated into the pipelines and executed on a regular basis?</td>
						<td>How often do you run your automation test?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Are automation tests split between Smoke and Regression test suites?</td>
						<td>Are automation tests split between Smoke and Regression test suites?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>What is the average pass rate for your automation?</td>
						<td>How often does the build fail because of a failure in a given test? When it fails, does it usually fail because of environmental issues or flaky tests?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Are Manual and Automation test aggregated under the same report (Xray)?</td>
						<td>Do you upload the automation result also to Xray?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Do you have an automation test report tool with a test results timeline?</td>
						<td>What do you do with the automation results report? Do you have an automation test report portal </td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Who has access to check the test results of test execution in reports?</td>
						<td>How does the team know when a test is failing (automation and manual)? Does the team have access to the testing results?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>                    
                </table>
            </td>
		</tr>
		<tr>
			<td>Non-Functional Testing</td>
			<td>Presence of non-functional testing on the project, including performance and security testing. Accessing the state of Non-Functional Requirements, data load model, etc.</td>
            <td>There are not Non-functional testing done manually neither automate, non-functional requirements are not collected during the analysis phase.</td>
			<td>The team collects non-functional requirements and include them as the non-functional test in the testing plan. Automation is used to cover these tests but in a not dedicated environment where results and metrics are not available therefore conclusions are not generated after execution.</td>
			<td>Automation tests cover the non-functional aspect of the product, there is a dedicated performance test environment used where the test suite is executed as part of the CI/CD pipeline, metrics are available therefore, the results and conclusions are generated after tests executions in a consistent manner. </td>
			<td colspan=4>
				<table>
					<tr>
						<td>Question</td>
						<td>Is performance testing a part of the testing process?</td>
						<td>When all the functionalities are tested and covered do you do any kind of non-functional test like performance before releasing to UAT, Staging, or Prod?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Does Non-Functional Requirements(NFR) exist?</td>
						<td>How do you collect the non-functional requirements? </td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Are Performance tests correlated to end-user scenarios?</td>
						<td>Do you run real performance tests correlated to end-user actions? Do you have a baseline to compare with the results?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Do you have a security test suite?</td>
						<td>Do you have any automation security tests? Apart from static code analysis?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Do you correlate performance test results with standard metrics and logs?</td>
						<td>When running the performance test? Are you able to collect the metrics (memory consumption, cpu ..) and logs from the servers under the test?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Do you run any of the NFT as part of the pipeline?</td>
						<td>How often do you run these tests? are they part of your pipeline?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Do the results from the NFT influence the CI/CD pipeline?</td>
						<td>What do you do with the results from these tests? Can they invalidate or block the progression of a given release in your pipeline?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>                                                            
                </table>
            </td>
		</tr>
		<tr>
			<td>Test Environments</td>
			<td>Set up of test environments, their usage and determine whether test envs are blockers for the usage</td>
            <td>There aren't dedicated environments for functional and non-functional testing. Functional testing is happening on either Dev environments, or on upper environments. Only some specific people could deploy the specific builds to the environments.</td>
			<td>There is a dedicated environment for functional testing, there is a place where non-functional could happen. There is no dependency on 3rd party unstable services. Anyone from the team can deploy and update environments for any specific build during 1 hour.</td>
			<td>There is a dedicated environment for functional and non-functional testing. There is no dependency on 3rd party unstable services. Anyone from the team can deploy and update environments for any specific build during 15 minutes.</td>
			<td colspan=4>
				<table>
					<tr>
						<td>Question</td>
						<td>Is there any environment for functional QA activities?</td>
						<td>Where do you run your manual test? Do you have a dedicated environment for it? How do you ensure a given version of your app is there for testing?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Is there any environment for performance testing?</td>
						<td>Do you have a dedicated environment to run non-functional tests such as performance tests?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Are there any dependencies on 3rd party unstable services/ environment?</td>
						<td>What do you do with 3rd party dependencies in your test environment? Does your test environment suffer from unstable 3rd party services?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Is the test environment dedicated/isolated to the team?</td>
						<td>What is the governance to not overlap with other test activities? How do you prepare and clean up the environment? Are you able to create an environment on the fly?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Can everyone from the team deploy any branch to QA environments?</td>
						<td>Could deployment to QA environment be done by any team member?
                            Is there some automation job in Jenkins for it?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Do you assert the expected state of the environment before running your test?</td>
						<td>Before running your test, do you have a pre-step that ensures or prepares the environment into a given state to make sure your test is predictable and stable? for example, running a set of smoke tests</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
                    <tr>
                        <td>Metric</td>
                        <td>How much time does it take to deploy and update environments for a specific build?</td>
                        <td>How long it takes to prepare the environment?</td>
                        <td></td>
                        <td></td>
                        <td></td>
                        <td></td>
                    </tr>
                </table>
            </td>
		</tr>
		<tr>
			<td>Knowledge Transfer</td>
			<td>How knowledge transfer and documentation regarding the Quality Assurance part is organized</td>
            <td>There is a limited number of documentation for QA, no single source of truth, there is no documented and described on-boarding process for newcomers, only automation QA is aware of test automation tools, expertise and approach</td>
			<td>The majority of QA areas are covered by documentation, however, it is stored in different places. The onboarding process is established, the basic checklist is created. Automation QAs and developers are aware of the process and able to execute needed tests</td>
			<td>Documentation for QA process is created, everything is stored in Confluence and well structurally organized. A fully detailed onboarding process is established and documented in Confluence. The whole engineering team, including manual QAs are aware of the test automation approach and ability to execute it</td>
			<td colspan=4>
				<table>
					<tr>
						<td>Question</td>
						<td>Is Documentation created and stored in Confluence?</td>
						<td>How do you track your documentation? Do you use Confluence?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Are you updating your documentation on a regular basis?</td>
						<td>Is your documentation up-to-date?
                            How do you keep it up-to-date?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>How effective your documentation is?</td>
						<td>Does your documentation work and viewed regularly?
                            How many views do you have on average for your documents?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Is the onboarding process for newcomers is established and documented?</td>
						<td>Do you have a formal process for updating documentation, is this documented anywhere?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
					<tr>
						<td>Question</td>
						<td>Are best practices for test automation expertise, test tools are shared inside the team?</td>
						<td>Are there some online training, recorded sessions, guilds for best practices sessions for test automation expertise, test tools, etc inside the team?</td>
						<td></td>
						<td></td>
						<td></td>
						<td></td>
					</tr>
                </table>
            </td>
		</tr>
	</tbody>
</table>
