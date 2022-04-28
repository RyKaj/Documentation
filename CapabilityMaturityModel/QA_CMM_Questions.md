
# Levels
## CMM Levels
<table>
	<colgroup>
		<col  style="width: 30%" />
		<col  style="width: 70%" />
	</colgroup>
	<tbody>
		<tr>
			<th>Level</th>
			<th>Description</th>
		</tr>
		<tr>
			<td>L1 - Learning</td>
			<td>The Squad is using  _ad hoc_  methods for testing, so results are not repeatable and there is no quality standard.</td>
		</tr>		
		<tr>
			<td>L2 - Practicing </td>
			<td>The testing process is defined, so there might be test strategies, test plans, test cases, based on requirements. Testing does not start until products are completed, so the aim of testing is to compare products against requirements.</td>
		</tr>		
		<tr>
			<td>L3 - Systematic</td>
			<td>The testing process is integrated into a software life cycle, e.g. the  [V-model] "V-Model (software development)"). The need for testing is based on risk management, and the testing is carried out with some independence from the development area.</td>
		</tr>
		<tr>
			<td>L4 - Measuring</td>
			<td>The testing activities take place at all stages of the life cycle, including reviews of requirements and designs. Quality criteria are agreed upon for all products of an organization (internal and external).</td>
		</tr>
		<tr>
			<td>L5 - Innovation</td>
			<td>The testing process itself is tested and improved at each iteration. This is typically achieved with tool support, and also introduces aims such as defect prevention through the life cycle, rather than defect detection (zero defects).</td>
		</tr>				
	</tbody>
</table>

## QA Aspects
<h1 id="-qa-metrics-"><strong>QA Metrics</strong></h1>
<table>
<thead>
<tr>
<th style="text-align:left"><strong>Aspect</strong></th>
<th style="text-align:left"><strong>Metric</strong></th>
<th style="text-align:left"><strong>Description</strong></th>
<th style="text-align:left"><strong>L1 STARTING</strong></th>
<th style="text-align:left"><strong>L2 PRACTICING</strong></th>
<th style="text-align:left"><strong>L3 SYSTEMATIC</strong></th>
<th style="text-align:left"><strong>L4 MEASURING</strong></th>
<th style="text-align:left"><strong>L5 INNOVATING</strong></th>
<th style="text-align:left"><strong>Level</strong></th>
<th style="text-align:left"><strong>Current Value</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left"><strong>TEST PROCESS</strong></td>
<td style="text-align:left"><strong>Regression Time</strong></td>
<td style="text-align:left"><p>How long in hours (days) does regression take</p><p></p><p>Squad estimation</p></td>
<td style="text-align:left">&gt; 1 month</td>
<td style="text-align:left">&gt; 1 week</td>
<td style="text-align:left">&lt; 4 hours</td>
<td style="text-align:left">&lt; 2 hours</td>
<td style="text-align:left">&lt; 1 hour</td>
<td style="text-align:left"><p>- L1</p><p>- L2</p><p>- L3</p><p>- L4</p><p>- L5</p><p>- Skipped</p></td>
<td style="text-align:left"></td>
</tr>
<tr>
<td style="text-align:left"><p><strong>DEFECT MANAGEMENT</strong></p><p></p><p></p></td>
<td style="text-align:left"><p><strong>% of Defects in Production</strong></p><p></p><p></p></td>
<td style="text-align:left">The % of the defects that were missed/slipped during the QA testing<br><br># of production defects / <br>(# of pre-release defects + <br># of production defects)</td>
<td style="text-align:left">Defect leakage is not tracked</td>
<td style="text-align:left">Defect leakage &gt; 15%</td>
<td style="text-align:left">Defect leakage &lt; 5%</td>
<td style="text-align:left">Defect leakage &lt; 3%</td>
<td style="text-align:left">Defect leakage &lt; 1%</td>
<td style="text-align:left"><p>- L1</p><p>- L2</p><p>- L3</p><p>- L4</p><p>- L5</p><p>- Skipped</p></td>
<td style="text-align:left"></td>
</tr>
<tr>
<td style="text-align:left"></td>
<td style="text-align:left"><strong>Avg. time to fix a critical bug</strong></td>
<td style="text-align:left"><p>How long does it take to fix a critical bug</p><p></p><p>Based on JIRA status changes </p></td>
<td style="text-align:left">More than a week</td>
<td style="text-align:left">Few days</td>
<td style="text-align:left">A day</td>
<td style="text-align:left">half a day</td>
<td style="text-align:left">Few hours</td>
<td style="text-align:left"><p>- L1</p><p>- L2</p><p>- L3</p><p>- L4</p><p>- L5</p><p>- Skipped</p></td>
<td style="text-align:left"></td>
</tr>
<tr>
<td style="text-align:left"><strong>TEST CASE MANAGEMENT PROCESS</strong></td>
<td style="text-align:left"><strong>Requirement coverage</strong></td>
<td style="text-align:left">The % of stories that have test cases and test executions associated with them in the current sprint</td>
<td style="text-align:left">Test cases are mainly created retroactively</td>
<td style="text-align:left"><code> </code>&lt; 50%</td>
<td style="text-align:left">&gt; 90%</td>
<td style="text-align:left">&gt; 95%</td>
<td style="text-align:left">= 100%</td>
<td style="text-align:left"><p>- L1</p><p>- L2</p><p>- L3</p><p>- L4</p><p>- L5</p><p>- Skipped</p></td>
<td style="text-align:left"></td>
</tr>
<tr>
<td style="text-align:left"><p><strong>TEST AUTOMATION</strong></p><p></p><p></p></td>
<td style="text-align:left"><strong>Testing Coverage</strong></td>
<td style="text-align:left"><p>The % of the test cases covered with automation</p><p></p><p># of test cases with <em>Status = Automated</em> /<br>Total # of test cases</p></td>
<td style="text-align:left">Test coverage is not tracked or can&#39;t be calculated</td>
<td style="text-align:left">&gt; 20%</td>
<td style="text-align:left">&gt; 70%</td>
<td style="text-align:left">&gt; 80%</td>
<td style="text-align:left">&gt; 95%</td>
<td style="text-align:left"><p>- L1</p><p>- L2</p><p>- L3</p><p>- L4</p><p>- L5</p><p>- Skipped</p></td>
<td style="text-align:left"></td>
</tr>
<tr>
<td style="text-align:left"></td>
<td style="text-align:left"><strong>Code Coverage</strong></td>
<td style="text-align:left"><p>The % of lines of code covered with unit tests</p><p></p><p>Calculated by SonarQube (or similar tool)</p></td>
<td style="text-align:left">Code coverage is not tracked or can&#39;t be calculated</td>
<td style="text-align:left">&gt; 30%*</td>
<td style="text-align:left">&gt; 70%*</td>
<td style="text-align:left">&gt; 80%*</td>
<td style="text-align:left">&gt; 90%*</td>
<td style="text-align:left"><p>- L1</p><p>- L2</p><p>- L3</p><p>- L4</p><p>- L5</p><p>- Skipped</p></td>
<td style="text-align:left"></td>
</tr>
<tr>
<td style="text-align:left"></td>
<td style="text-align:left"><strong>Effort on maintenance</strong></td>
<td style="text-align:left"><p>The % of the effort is spent on test maintenance per sprint</p><p><br>Effort spent on test maintenance / <br>Total time in a sprint</p></td>
<td style="text-align:left">Either no tests or &gt; 50%</td>
<td style="text-align:left">15% &lt; effort &lt; 50%</td>
<td style="text-align:left">&lt; 15%</td>
<td style="text-align:left">&lt; 10%</td>
<td style="text-align:left">&lt; 5%</td>
<td style="text-align:left"><p>- L1</p><p>- L2</p><p>- L3</p><p>- L4</p><p>- L5</p><p>- Skipped</p></td>
<td style="text-align:left"></td>
</tr>
<tr>
<td style="text-align:left"><strong>TEST EXECUTION</strong></td>
<td style="text-align:left"><strong>Pass Rate of automation</strong></td>
<td style="text-align:left"><p>The % of passing tests in the automation builds</p><p></p><p># of passed tests / <br>total # of tests</p></td>
<td style="text-align:left">no tests</td>
<td style="text-align:left">&gt; 50% for E2E tests</td>
<td style="text-align:left">&gt; 90% for E2E tests</td>
<td style="text-align:left">&gt; 95% for E2E tests</td>
<td style="text-align:left">&gt; 99% for E2E tests</td>
<td style="text-align:left"><p>- L1</p><p>- L2</p><p>- L3</p><p>- L4</p><p>- L5</p><p>- Skipped</p></td>
<td style="text-align:left"></td>
</tr>
<tr>
<td style="text-align:left"></td>
<td style="text-align:left"><strong>Execution time of automation</strong></td>
<td style="text-align:left"><p>How long does it take for automation tests to execute</p><p></p><p>Calculated by Jenkins </p></td>
<td style="text-align:left">no tests</td>
<td style="text-align:left">any time is acceptable</td>
<td style="text-align:left">&lt; 6h<br>(able to execute nightly)</td>
<td style="text-align:left">&lt; 4h</td>
<td style="text-align:left">&lt; 1h</td>
<td style="text-align:left"><p>- L1</p><p>- L2</p><p>- L3</p><p>- L4</p><p>- L5</p><p>- Skipped</p></td>
</tr>
</tbody>
</table>
<p>Notes:</p>
<ul>
<li>* - not applicable for legacy code</li>
</ul>

