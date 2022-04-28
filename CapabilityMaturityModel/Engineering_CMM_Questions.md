<!--
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
-->

## Development Aspects
<h1 id="-questionnaire-"><strong>Questionnaire</strong></h1>
<table>
   <thead>
      <tr>
         <th style="text-align:left"><strong>Aspect</strong></th>
         <th style="text-align:left"><strong>Questions</strong></th>
         <th style="text-align:left"><strong>Evidence Type</strong></th>
         <th style="text-align:left"><strong>L1 STARTING</strong></th>
         <th style="text-align:left"><strong>L2 PRACTICING</strong></th>
         <th style="text-align:left"><strong>L3 SYSTEMATIC</strong></th>
         <th style="text-align:left"><strong>L4 MEASURING</strong></th>
         <th style="text-align:left"><strong>L5 INNOVATING</strong></th>
         <th style="text-align:left"><strong>Levels</strong></th>
         <th style="text-align:left"><strong>Comments</strong></th>
         <th style="text-align:left"><strong>Collaboration Notes</strong></th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td style="text-align:left">
            <p><strong>Source Code Management (SCM) / Version Control</strong></p>
            <p></p>
            <p><strong>Note:</strong></p>
            <p>- <strong>Some squad might reference the term &quot;project&quot; as a branch reference.</strong></p>
         </td>
         <td style="text-align:left">
            <p>Does the squad use and share a central source control for the application</p>
            <p><br><br><br></p>
         </td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- Not using any SCM</p>
            <p>- Branches (excluding master/main, develop) are kept around</p>
            <p>- Only commits when everything is completed</p>
            <p><br><br><br><br><br><br></p>
         </td>
         <td style="text-align:left">- Using other community or unauthorized SCM</td>
         <td style="text-align:left">
            <p>- Maintains all code in SCM</p>
            <p>- Branching strategy protects the &quot;release&quot; branch from untested changes</p>
            <p>- Squad has a dedicated central CSM repository</p>
            <p>- Branches (excluding master/main, develop) exist until related change is deployed to production</p>
            <p>- Occasional commits</p>
            <p>- Stories are developed in separate branches</p>
            <p><br><br><br><br></p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- Frequent commits within the day</p>
            <p>- Merge duration is at its optimal to be most efficient for the process</p>
            <p><br><br><br></p>
         </td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>5 questions
         </td>
         <td>
            4 metrics</p>
            <p></p>
         </td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Do you have to use SCM to share all code changes</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">Sharing files using slack, email, shared drive, or USB...etc</td>
         <td style="text-align:left">Passing code snippets using slack, email, shared drive, or USB...etc</td>
         <td style="text-align:left">
            <p>- Code is only shared through Squad&#39;s SCM dedicated repository based on branch or commit id</p>
            <p>- Using SCM collaboration tools (using Fork or Cherry-Pick)</p>
            <p>- Using other plugin/add-on for secure collaboration</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>Cherry Pick - <a href="https://www.atlassian.com/git/tutorials/cherry-pick">https://www.atlassian.com/git/tutorials/cherry-pick</a></p>
            <p>Fork - <a href="https://guides.co/g/bitbucket-101/11161">https://guides.co/g/bitbucket-101/11161</a></p>
            <p></p>
         </td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>Is the branching strategy protecting the release branch</p>
            <p>Note:<br>There are different industry best practice branching patterns. As long as the team is following one of them and it is protecting the &quot;release&quot; branch.</p>
         </td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">People are not aware of best practices to protect the release branch</td>
         <td style="text-align:left">People can commit to the branch that is also used to deployed to environments</td>
         <td style="text-align:left">
            <p>- People can directly commit to the branch that is being deployed to environments - CI reference what branch commit ID to build from</p>
            <p>- People can not directly commit to the branch that is being deployed to environments - CI pulls latest commit from branch</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p><a href="https://cycode.com/blog/how-to-setup-branch-protection-rules-2/">https://cycode.com/blog/how-to-setup-branch-protection-rules-2/</a></p>
            <p>Branching Strategy</p>
            <p>- <a href="https://martinfowler.com/articles/branching-patterns.html">https://martinfowler.com/articles/branching-patterns.html</a></p>
            <p>- <a href="https://www.perforce.com/blog/vcs/best-branching-strategies-high-velocity-development#:~:text=A%20release%20branching%20strategy%20involves,release%20branching%20strategy%20is%20required">best-branching-strategies-high-velocity-development</a></p>
            <p>- <a href="https://docs.microsoft.com/en-us/azure/devops/repos/git/git-branching-guidance?view=azure-devops">https://docs.microsoft.com/en-us/azure/devops/repos/git/git-branching-guidance?view=azure-devops</a></p>
            <p>- <a href="https://launchdarkly.com/blog/git-branching-strategies-vs-trunk-based-development/">https://launchdarkly.com/blog/git-branching-strategies-vs-trunk-based-development/</a></p>
            <p>- <a href="https://nvie.com/posts/a-successful-git-branching-model/">https://nvie.com/posts/a-successful-git-branching-model/</a></p>
            <p>- <a href="https://www.gitkraken.com/learn/git/best-practices/git-branch-strategy">https://www.gitkraken.com/learn/git/best-practices/git-branch-strategy</a></p>
         </td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>Do you put the Jira key in your commit comments?</p>
            <p>Note:<br>Ie.. Jira Smart Commit</p>
         </td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">Not referencing Jira Key in Commit comments</td>
         <td style="text-align:left">Some squad members reference Jira Key in there commit comment</td>
         <td style="text-align:left">
            <p>- Main commit comment has Jira reference</p>
            <p>- All commit comment has Jira ticket reference</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- links was sent in slack channel </p>
            <p>&emsp;- Research was one - <a href="https://thestarsgroup.slack.com/archives/C028EUX1YBH/p1627044853028000">https://thestarsgroup.slack.com/archives/C028EUX1YBH/p1627044853028000</a></p>
         </td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Do you follow the &quot;1 story = 1 branch&quot; principle?</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">n Story/feature : 1 Branch - all the time</td>
         <td style="text-align:left">2 Story/feature : 1 Branch - occasionally have multiple stories in on branch</td>
         <td style="text-align:left">1 Story/feature : 1 Branch - constantly</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>What git client do you use?</p>
            <p>What add-on/plug-ins do you use?</p>
         </td>
         <td style="text-align:left">
            <p>Research-Only</p>
            <p><strong>No Impact in CMM</strong></p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">What is the average Feature branch life?</td>
         <td style="text-align:left">
            <p>Metric</p>
            <p></p>
         </td>
         <td style="text-align:left">Branches are never deleted</td>
         <td style="text-align:left">Branches are removed periodically</td>
         <td style="text-align:left">More than 2 s or &gt;= sprint duration )</td>
         <td style="text-align:left">&lt; 5 days (or &lt; 50% of sprint duration)</td>
         <td style="text-align:left">&lt; 2 day (or &lt; 20% of sprint duration)</td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">How often do you commit?</td>
         <td style="text-align:left">Metric</td>
         <td style="text-align:left">When the work is done</td>
         <td style="text-align:left">Occasionally commit - based on Story complexity</td>
         <td style="text-align:left">Systematically, every 1-2 days</td>
         <td style="text-align:left">Once a day</td>
         <td style="text-align:left">More than once a day</td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">How long does it take on average to merge a commit once PR is approved?</td>
         <td style="text-align:left">
            <p>Metric</p>
            <p></p>
         </td>
         <td style="text-align:left">&gt; 2d</td>
         <td style="text-align:left">&lt; 2d</td>
         <td style="text-align:left">&lt; 8h</td>
         <td style="text-align:left">&lt; 4h</td>
         <td style="text-align:left">&lt; 1hr</td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">What is the % code churn ( code reworked ) per sprint</td>
         <td style="text-align:left">Metric</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"><strong>Code Review<br><br><br>The process of assuring code quality via code reviews.</strong></td>
         <td style="text-align:left">
            <p>Is Code Review being done for code merging?</p>
            <p>Is the quality gate process integrated with pull request in Source Control Management?</p>
         </td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left"><br><br></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- The Code Review process is set and clearly understood.</p>
            <p>- Squad is not fully adhering to the process.</p>
            <p>- Code rework after review could be high.</p>
            <p>- Code review doesn&#39;t take too long.</p>
            <p>- Squad is fully adhering to the process.</p>
            <p>- Code refactoring after review is minimal</p>
            <p>- Code review responses are fast, requests complete quickly.</p>
            <p><br></p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p><br></p>
            <p></p>
         </td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">8 questions</td>
         <td>3 metrics</td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Is the squad doing code review before deploying to QA</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">Not doing code review</td>
         <td style="text-align:left">Occasionally doing code review</td>
         <td style="text-align:left">Doing code review</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Are the pull request comments constructive, descriptive, and useful in helping the developer improve their skills?</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">Never</td>
         <td style="text-align:left">
            <p>- occasionally </p>
            <p>- &lt; 80% of the time</p>
         </td>
         <td style="text-align:left">- all the time</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Is the quality gate process integrated with pull request in Source Control Management?</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">No thresholds or quality gates configured</td>
         <td style="text-align:left">
            <p>- Threshold has been set, not enforced</p>
            <p>- Quality gate tools are only collecting data - not enforced </p>
            <p>- Threshold has been adjusted to maintain, optimized high quality. </p>
         </td>
         <td style="text-align:left">Quality gate tools are enforced. Fails the process when threshold is not met.</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left"><del>Are pull request usually an impediment to the delivery of flow</del></td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- <del>Pull Request is the bottleneck within the process</del></p>
            <p>- <del>Pull Request slows down the process</del></p>
         </td>
         <td style="text-align:left">
            <p>- <del>Testing the code is later within the sprint instead of sooner</del></p>
            <p>- <del>Pull request does not slow down process</del></p>
         </td>
         <td style="text-align:left">- <del>Pull request is address quickly that does not effect downstream process</del></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left"><del>How does the code reviewer priorities the request</del></td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left"><del>No priority when code review request has received request</del></td>
         <td style="text-align:left"><del>Treat code review request as normal priority - complete current task before code review others</del></td>
         <td style="text-align:left"><del>Treat code review request as first priority</del></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Do you validate business logic as part of code review process?</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">Does not do business logic review</td>
         <td style="text-align:left">Skims business logic</td>
         <td style="text-align:left">Review business logic</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>Do you depend on external SMEs to complete code review?</p>
            <p></p>
            <p>Note: </p>
            <p>SME - <a href="https://en.wikipedia.org/wiki/Subject-matter_expert">Subject Matter Expert</a></p>
         </td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">No code review being done</td>
         <td style="text-align:left">
            <p>- All code review is done with external SME</p>
            <p>- 50/50 code review is done with external SME</p>
         </td>
         <td style="text-align:left">
            <p>- 80/20 - 20% is done by external SME</p>
            <p>- All code review is done within the squad</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">What is the average cycle time for a pull request</td>
         <td style="text-align:left">Metric</td>
         <td style="text-align:left">&gt; 24 hr</td>
         <td style="text-align:left">&lt; 24 hr</td>
         <td style="text-align:left">&lt; 4 hr</td>
         <td style="text-align:left">&lt; 1.5 hr</td>
         <td style="text-align:left">&lt; 1 hr</td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>How many code review revision is required.</p>
            <p>Note:<br>1 cycle = Reviewee submit &gt; Reviewer &gt; Reviewee needs to make changes</p>
         </td>
         <td style="text-align:left">Metric</td>
         <td style="text-align:left">&gt; 5+ cycles</td>
         <td style="text-align:left">&gt; 5 cycles</td>
         <td style="text-align:left">&lt; 3 cycles</td>
         <td style="text-align:left">&lt; 2 cycles</td>
         <td style="text-align:left">&lt; 1 cycles</td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left">
            <p><strong>Code Analysis / Integrated Analysis tool<br><br><br>Shows how rigorously the team enforces coding standards</strong></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
         </td>
         <td style="text-align:left">
            <p>Does your coding standard include or enforce the usage of local Lint - Static Analysis</p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
         </td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- Does not use any Lint on local IDE</p>
            <p>- Use different local IDE Lint, not ways executing every time before commit</p>
            <p>- Occasionally execute local IDE Lint, randomly resolve some issues before committing</p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
         </td>
         <td style="text-align:left">Executing local IDE Lint only addressing Critical and Blockers.</td>
         <td style="text-align:left">
            <p>Execute local IDE Lint and resolve all issues before committin</p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
         </td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>3 questions
         </td>
         <td>
            5 metrics</p>
            <p></p>
         </td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>Do you create/track (Jira tickets) on Static Analysis issues identified during scan</p>
            <p>Note: </p>
            <p>SQ Severity:</p>
            <p>- Blocker</p>
            <p>- Critical</p>
            <p>- Major</p>
            <p>- Minor</p>
            <p>- Info</p>
         </td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- Does not log in or have an account to SonarQube</p>
            <p>- Squad members log in to SonarQube to review - no other actions taken</p>
         </td>
         <td style="text-align:left">
            <p>Tracks Blocker and Critical only in Jira</p>
            <p>Tracks Major in Jira</p>
            <p>Tracks Minor in Jira</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Does the Continuous Integration ( CI ) process fail when quality gate threshold is surpassed</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- CI step is not configured / step does not exist</p>
            <p>- CI step is configured, but not enabled</p>
         </td>
         <td style="text-align:left">
            <p>- CI step executes only collects data </p>
            <p>- SonarQube threshold configured - CI not enforced</p>
         </td>
         <td style="text-align:left">CI threshold is enforced - quality gates enabled</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>Does your coding standard include or enforce the Git hook to validate pre-commit</p>
            <p>Note:</p>
            <p>- Syntax check scan before commit </p>
            <p>- configuration - <a href="https://pre-commit.com/">https://pre-commit.com/</a></p>
         </td>
         <td style="text-align:left">Metric</td>
         <td style="text-align:left">Squad does not know about Git hook pre-commit</td>
         <td style="text-align:left">
            <p>- Squad does not include or enforce Git hook pre-commit</p>
            <p>- Not all squad members have this installed on their system</p>
            <p>- Squad members occasionally bypass/skip the validation </p>
         </td>
         <td style="text-align:left">
            <p>- Pre-commit hook is configured to the squad&#39;s work</p>
            <p>- Execute automatically / programmatically</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>How often does a build fail (on CI - based on code) after a change?</p>
            <p>Note:<br>Any status is not success would be classified as failure (Example.. Aborted, Unstable)</p>
         </td>
         <td style="text-align:left">Metric</td>
         <td style="text-align:left">&gt; 50%</td>
         <td style="text-align:left">&lt; 49%</td>
         <td style="text-align:left">&lt; 30%</td>
         <td style="text-align:left">&lt; 20%</td>
         <td style="text-align:left">&lt; 10%</td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>What is the Cyclomatic Complexity / Code Complexity index value</p>
            <p></p>
            <p>Note:<br>To reduce the complexity without compromise business rules or logic</p>
         </td>
         <td style="text-align:left">Metric</td>
         <td style="text-align:left">&gt; 100</td>
         <td style="text-align:left">&gt; 80 - &lt;= 100</td>
         <td style="text-align:left">&gt; 60 - &lt;= 80</td>
         <td style="text-align:left">&gt; 40 - &lt;= 60</td>
         <td style="text-align:left">&lt; 40</td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>What is the Cognitive Complexity value</p>
            <p>Note:<br>Cognitive tells you how difficult your code will be to read and understand</p>
         </td>
         <td style="text-align:left">Metric</td>
         <td style="text-align:left">&gt;= 50</td>
         <td style="text-align:left">&gt; 30 &lt; 50</td>
         <td style="text-align:left">&gt; 20 &lt;= 30</td>
         <td style="text-align:left">&gt; 10 &lt; 20</td>
         <td style="text-align:left">&lt; 10</td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">What is the Code Duplication percentage</td>
         <td style="text-align:left">Metric</td>
         <td style="text-align:left">&gt; 40%</td>
         <td style="text-align:left">&lt; 40%</td>
         <td style="text-align:left">&lt; 30%</td>
         <td style="text-align:left">&lt; 20%</td>
         <td style="text-align:left">&lt; 10%</td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">What is percentage of code smell</td>
         <td style="text-align:left">Metric</td>
         <td style="text-align:left">Does not log in or have an account to SonarQube</td>
         <td style="text-align:left">Squad members log in to SonarQube to review - no other actions taken</td>
         <td style="text-align:left">0 Blockers &amp; Critical</td>
         <td style="text-align:left">(0 Blockers &amp; Critical 0) and Majors</td>
         <td style="text-align:left">(0 Blockers &amp; Critical * 0 Major) and 0 Minors</td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left">
            <p><strong>Technical Standards</strong></p>
            <p><strong>Awareness of design principles and their day-to-day application.</strong></p>
            <p><strong>To reduce time wasted on:</strong></p>
            <p>- <strong>Maintenance efforts</strong></p>
            <p>- <strong>Compilation issues on  code modification or error-handling</strong></p>
            <p><br><br><strong>Notes:</strong></p>
            <p><a href="https://stackoverflow.blog/2021/11/01/why-solid-principles-are-still-the-foundation-for-modern-software-architecture/"><strong>SOLID</strong></a></p>
            <p>- <strong>Single Responsibility Principle (SRP)</strong></p>
            <p>- <strong>Open/Close Principle (OCP)</strong></p>
            <p>- <strong>Liskov Substitution Principle (LSP)</strong></p>
            <p>- <strong>Interface Segregation Principle (ISP)</strong></p>
            <p>- <strong>Dependency Inversion Principle (DIP)</strong></p>
            <p><strong>GOF - Gang of Four</strong></p>
            <p>- <strong>Design Patterns</strong></p>
            <p><strong>GRASP - General Responsibility Assignment Software Patterns</strong></p>
            <p>- <strong>Design Patterns</strong></p>
            <p><strong>Clean Coding</strong> </p>
            <p>- <strong>Can code be read and enhanced by a developer other than original author (without spending a lot of time trying to understand it)</strong></p>
         </td>
         <td style="text-align:left">
            <p>What design patterns does the squad use?</p>
            <p><strong>Design Principle</strong>: </p>
            <p>____________</p>
         </td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- Squad is NOT using any principles </p>
            <p>- Squad uses different principles - &quot;developer choice&quot;</p>
         </td>
         <td style="text-align:left">
            <p>- All Squad sort of follows the same principles</p>
            <p>- Documented in their coding standards</p>
         </td>
         <td style="text-align:left">All Squad fully follows the same principles</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>1 questions
         </td>
         <td>
            0 metrics</p>
            <p></p>
            <p></p>
         </td>
      </tr>
      <tr>
         <td style="text-align:left">
            <p><strong>Technical Process</strong></p>
            <p><strong>Agile Software Development process or methodology (any options below).</strong></p>
            <p><strong>Any quality gates in place, metrics are being tracked</strong></p>
            <p><strong>What are the threshold of those gates.</strong></p>
            <p><strong>Note:</strong></p>
            <p><strong>Anything under L3 should be flagged as high priority for further investigation</strong></p>
            <p></p>
            <p><strong>Pair Programming or XP (Extreme Programming)</strong></p>
            <p>- <strong>Communication</strong></p>
            <p>- <strong>Simplicity</strong></p>
            <p>- <strong>Feedback</strong></p>
            <p>- <strong>Respect</strong></p>
            <p>- <strong>Courage</strong></p>
            <p><strong>TDD - Test Driven Development</strong></p>
            <p>- <strong>Develop unit of function</strong></p>
            <p>- <strong>Produce the code for small units of test</strong></p>
            <p>- <strong>Maintain workable test</strong></p>
            <p><strong>BDD - Behaviour Driven Development or ATDD - Acceptance Test Driven Development</strong></p>
            <p>- <strong>Discussing Features</strong></p>
            <p>- <strong>Write Scenarios</strong></p>
            <p>- <strong>Code Development</strong></p>
            <p>- <strong>Passing the Scenarios</strong></p>
            <p>- <strong>Refactor of Code</strong></p>
            <p></p>
            <p>**<br><br><br><br></p>
         </td>
         <td style="text-align:left">
            <p>What methodology does the squad use?</p>
            <p><strong>Methodology</strong>: </p>
            <p>__________________</p>
         </td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">Squad is not using (any methodology)</td>
         <td style="text-align:left">
            <p>- Squad uses different principles - &quot;developer choice&quot;</p>
            <p>- Occasionally follow methodology</p>
         </td>
         <td style="text-align:left">
            <p>- Documented in their coding standards</p>
            <p>- Fully using this methodology</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Are the engineers contributing to the evaluation of performance testing results?</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- Not doing any performance testing</p>
            <p>- Only doing performance test if time permits</p>
            <p></p>
         </td>
         <td style="text-align:left">
            <p>- Periodically contribute to performance test</p>
            <p>- Only doing performance test on areas that was found in Production</p>
         </td>
         <td style="text-align:left">Development  &amp; QA work together on everything including working out performance testing strategy, choosing tool suite, implementing any required plumbing code, analyzing results, drawing conclusions, maintaining related tech debt, informing architects about outcome</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left"><del>Do you work on dependencies first during sprint to enable parallel development?</del></td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left"><del>Works on first ticket at the top of the list or takes lowest hanging fruit</del></td>
         <td style="text-align:left"><del>Periodically works on dependency first</del></td>
         <td style="text-align:left"><del>Always works on dependency first</del></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"><strong>Technical Debt Management (TDM)<br><br>How is technical debt being addressed.</strong> <br><br><br></td>
         <td style="text-align:left">Do you know what <a href="https://confluence.pyrsoftware.ca/confluence/display/ATX/Playbook+Glossary#PlaybookGlossary-tocT">technical debt</a> is?</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- Never heard of the term</p>
            <p>- Heard of the term, does not understand the meaning</p>
         </td>
         <td style="text-align:left">
            <p>- Heard and understand the term. Unknown if the squad has technical debt</p>
            <p>- Squad knows they have technical dept</p>
         </td>
         <td style="text-align:left">Knowledge on the term and is trying to address it</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"><br></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>6 questions
         </td>
         <td>
            1 metrics </p>
            <p></p>
         </td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Are you tracking technical debt?</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- Not tracking</p>
            <p>- Squad knows some of the issues stored in their memory</p>
         </td>
         <td style="text-align:left">
            <p>- Has it written down on paper or in memory</p>
            <p>- Some squad members create ticket, others still write it down on paper</p>
         </td>
         <td style="text-align:left">- All squad members create Jira tickets</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Are you (tech backlog) refinement with your technical debt?</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- Not grooming</p>
            <p>- Review the list - no actions</p>
         </td>
         <td style="text-align:left">- Priorities couple of tickets with no solid methodology</td>
         <td style="text-align:left">- Each tech debt item is tracked as a Jira ticket and they&#39;re all prioritized</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Are you addressing in the technical debt within your sprint?</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- Not addressing any tickets</p>
            <p>- Blue-moon addressing ticket(s)</p>
         </td>
         <td style="text-align:left">
            <p>- Periodically 1 ticket have been added to the sprint</p>
            <p>- Periodically &gt; 1 ticket have been added to the sprint</p>
         </td>
         <td style="text-align:left">- Min. 1 ticket are added to each sprint</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">How quickly can the technical debt be fixed (on average)</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">&gt; 24 hr</td>
         <td style="text-align:left">&lt; 24 hr</td>
         <td style="text-align:left">&lt; 16 hr</td>
         <td style="text-align:left">&lt; 8 hr</td>
         <td style="text-align:left">&lt; 4 hr</td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>Potential this can be a metric?</p>
            <p>- The life of a branch?</p>
            <p>- Jira ticket (status changes or other updates)</p>
         </td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>Do you classify the type of technical debt?</p>
            <p>- Accidental - Reckless</p>
            <p>- Deliberate - Reckless</p>
            <p>- Accidental - Prudent</p>
            <p>- Deliberate - Prudent</p>
         </td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">No classifications</td>
         <td style="text-align:left">
            <p>- Jira ticket has a field for classification, tickets may not all been classified</p>
            <p>- Jira ticket is being prioritized based on made up classification</p>
         </td>
         <td style="text-align:left">Jira ticket is being prioritized based on quadrant classification</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>From <a href="https://miro.com/app/board/o9J_l7EIMPk=/">Miro</a> board:</p>
            <p><img src="Aspose.Words.373558dd-be62-49f6-a336-890fc455af18.003.jpeg" alt=""></p>
            <p>Improving process to reduce</p>
            <p>- Q3 &quot;Accidental - Reckless&quot;</p>
            <p>- Q2 &quot;Deliberate - Reckless&quot;</p>
            <p>- Q4 &quot;Accidental - Prudent&quot;</p>
            <p>- Q1 &quot;Deliberate - Prudent&quot;</p>
            <p></p>
            <p>Martin Fowlers tech debt quadrant</p>
            <p><a href="https://martinfowler.com/bliki/TechnicalDebtQuadrant.html">https://martinfowler.com/bliki/TechnicalDebtQuadrant.html</a></p>
            <p><a href="https://www.stepsize.com/blog/complete-guide-to-technical-debt">https://www.stepsize.com/blog/complete-guide-to-technical-debt</a></p>
            <p><a href="https://www.whitesourcesoftware.com/resources/blog/staying-on-top-of-your-organization-s-technical-debt/">https://www.whitesourcesoftware.com/resources/blog/staying-on-top-of-your-organization-s-technical-debt/</a></p>
            <p></p>
         </td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">What is the average % code churn ( code reworked ) on resolving technical debt issues</td>
         <td style="text-align:left">Metric</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">Information could be pulled from Grafana - Needs to be hooked up</td>
      </tr>
      <tr>
         <td style="text-align:left"><strong>Collaboration (Tools) <br><br>Is there a fluid process for collaboration with both squad internal &amp; external people.</strong><br></td>
         <td style="text-align:left">
            <p>Are you using the corporation standard Jira ticketing system to track all work and priorities order?</p>
            <p></p>
         </td>
         <td style="text-align:left">
            <p>Question</p>
            <p>(default)</p>
         </td>
         <td style="text-align:left">
            <p>- Not using Jira</p>
            <p>- Using Jira only to update status on assigned tickets</p>
         </td>
         <td style="text-align:left">
            <p>Occasionally add comments on progress and communication</p>
            <p></p>
         </td>
         <td style="text-align:left">
            <p>- Link other Jira tickets and Confluence (not just paste url in comments or description areas)</p>
            <p>- Regularly add comments for visibility</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>Squad frequently shares knowledge internally and fully utilizes different types of collaboration tools on top of corporate standard tools.</p>
            <p><br><br><br></p>
         </td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>5 questions
         </td>
         <td>
            0 metrics</p>
            <p></p>
            <p></p>
         </td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Are you using the corporation standard video conference tool</td>
         <td style="text-align:left">
            <p>Question</p>
            <p>(default)</p>
         </td>
         <td style="text-align:left">
            <p>- Using legacy corporate or unauthorized tools </p>
            <p>- Not using Zoom or Slack</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">Is using Zoom or Slack</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Are you using the corporation standard &quot;instant message&quot; tool</td>
         <td style="text-align:left">
            <p>Question</p>
            <p>(default)</p>
         </td>
         <td style="text-align:left">
            <p>Using legacy corporate or unauthorized tools </p>
            <p>Not using Slack</p>
         </td>
         <td style="text-align:left">Is using Slack</td>
         <td style="text-align:left">Using addon/plugin to increase productivity on corporate standard tools</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>Is the squad using any apps/tools to collaborate</p>
            <p>- Ie, Miro, IDE that allows collaboration (ie.. <a href="https://visualstudio.microsoft.com/services/live-share/">Visual Studio Live Share</a> ).</p>
         </td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">Not using any other tools</td>
         <td style="text-align:left"></td>
         <td style="text-align:left">They are using other collaboration on demand</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>Do you do any squad knowledge sharing sessions?</p>
            <p>- Lunch N&#39; Learn</p>
            <p>- Brown Bag</p>
            <p>- Hack-a-thon&#39;s</p>
         </td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">Never shared</td>
         <td style="text-align:left">Team is sharing occasionally (once or twice a year)</td>
         <td style="text-align:left">Team is sharing quarterly or monthly</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"><strong>Coding Policy<br><br><br>Policy documentation is a set of files that describe the project, guidelines for contribution, and other standards and processes.</strong></td>
         <td style="text-align:left">
            <p>Does <a href="http://ReadMe.md">ReadMe.md</a> file exist?</p>
            <p>- Does table of content exists</p>
            <p>- Installation/Getting Started</p>
            <p>- local system installation and setup</p>
            <p>- prerequisite libraries</p>
            <p>- Build status</p>
            <p>- Project/Solution structure</p>
            <p>- Execute Unit Test</p>
            <p><br></p>
         </td>
         <td style="text-align:left">
            <p>Question</p>
            <p>Description: <br>ReadMe - A file that introduce and explains about the project. It contains information that is commonly required to understand about the project.</p>
         </td>
         <td style="text-align:left">
            <p>- File does not exist</p>
            <p>- Squad does not know what this file does</p>
         </td>
         <td style="text-align:left">File exists - maybe outdated, may not be using it</td>
         <td style="text-align:left">
            <p>Information is always up to date</p>
            <p><br><br><br></p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>Does CODEOWNERS file exist?</p>
            <p>- Is Default owner set</p>
            <p>- Is the file automatically updated or manually updated</p>
            <p>- Is the pull request required to merge?</p>
         </td>
         <td style="text-align:left">
            <p>Question</p>
            <p>Description: CodeOwner - A file to define individuals or squads that are responsible for the code in the repository.</p>
            <p>A simple way to automatically assign reviewers to a pull request</p>
         </td>
         <td style="text-align:left">
            <p>- File does not exist</p>
            <p>- Squad does not know what this file does</p>
         </td>
         <td style="text-align:left">File exists - maybe outdated, may not be using it</td>
         <td style="text-align:left">Fully configured</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>Does <a href="http://contributing.md">contributing.md</a> file exist?</p>
            <p>- Does table of content exists</p>
            <p>- Does code conduct section exists</p>
            <p>- Does reporting defects section exists</p>
            <p>- Does coding style section exists</p>
         </td>
         <td style="text-align:left">
            <p>Question</p>
            <p>Description: Contributor - A file that explains how people should contribute to the repo.</p>
         </td>
         <td style="text-align:left">
            <p>- File does not exist</p>
            <p>- Squad does not know what this file does</p>
         </td>
         <td style="text-align:left">File exists - maybe outdated, may not be using it</td>
         <td style="text-align:left">Fully configured</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Does .gitignore file exists</td>
         <td style="text-align:left">
            <p>Question</p>
            <p>Description: gitignore - A file that manages the repo on what files and folders to ignore</p>
         </td>
         <td style="text-align:left">
            <p>- File does not exist</p>
            <p>- Squad does not know what this file does</p>
         </td>
         <td style="text-align:left">- File exists - maybe outdated, may not be using it (unwanted files are in the repo)</td>
         <td style="text-align:left">Fully configured - Repo does not have any unwanted files</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Is the squad adhering to the security policy standards</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">Unaware there is a corporate security standard</td>
         <td style="text-align:left">
            <p>Not following security standards</p>
            <p>File exists - maybe outdated, may not be using it</p>
            <p>Squads copy/clone standard document into their space</p>
         </td>
         <td style="text-align:left">Squad reference corporate security standar</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"><strong>Documentation<br><br>Standards, process, architecture, and procedure documentation</strong></td>
         <td style="text-align:left">What kind of documentation does the squad have?</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- No documentation</p>
            <p>- Squad does not own documentation. Some aspects are covered</p>
         </td>
         <td style="text-align:left">
            <p>Document covers the key aspects</p>
            <p>- Coding Standards</p>
            <p>- Best practices</p>
            <p>- Application Architect</p>
            <p>- On boarding</p>
            <p>- Operational Support</p>
         </td>
         <td style="text-align:left">
            <p>- Documentation is regularly updated</p>
            <p>- Squad owns the documentation</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>7 questions
         </td>
         <td>
            0 metrics</p>
            <p></p>
         </td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Are industry standard coding policies documented for the squad?</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- No documentation</p>
            <p>- Squad is using another squad&#39;s documentation, reference in the other squad&#39;s confluence space - Bookmarked</p>
         </td>
         <td style="text-align:left">Squad copy/clone another confluence page</td>
         <td style="text-align:left">
            <p>- In the squad confluence space reference by in hyperlink</p>
            <p>- In the squad confluence space reference by &quot;include page&quot; </p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">Does the squad follow the coding standard?</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- Squad members are not even aware of document</p>
            <p>- Squad members are aware, but follow only occasionally</p>
         </td>
         <td style="text-align:left">- Usually following it</td>
         <td style="text-align:left">Always followed, continuously helping out each other to follow the standard properly.</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>Is there a document to help onboard a new member?</p>
            <p>Note: </p>
            <p>(Or act as a secondary backup from another squad)</p>
         </td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- No documentation</p>
            <p>- Documentation exists with limited information. New members still need to ask lots of questions or inquire how to setup local system, what ticket request to gain proper access/permissions </p>
            <p></p>
         </td>
         <td style="text-align:left">
            <p>- Only needs to ask question for access/permissions </p>
            <p>- New members only need minor clarifications</p>
         </td>
         <td style="text-align:left">New members do not need to inquire or refer to procedures to gain access/permissions to tools/sites they need to engage. Does not need any assistance to setup local environment</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>How is the on boarding document structured?</p>
            <p>- checklist</p>
            <p>- probation periods - 30, 60, 90</p>
         </td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>- No documentation</p>
            <p>- Document exists in their space. Content is not organized.</p>
         </td>
         <td style="text-align:left">Content might be organized, but no expectation set</td>
         <td style="text-align:left">
            <p>- Break down on expectations for 30-60-90 days </p>
            <p>- Squad&#39;s document includes Tribes documentation.</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">What is the process to updating the on-boarding document</td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">
            <p>No documentation</p>
            <p>Does not have any process to update documentation </p>
         </td>
         <td style="text-align:left">Document is reviewed before new member starts</td>
         <td style="text-align:left">Document is being updated by new staff on-boarding feedback.</td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
      <tr>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>Is the Security coding standard included within the squads Development Coding Standards?</p>
            <p><strong>Not copying the original confluence page to the squad space. Expect hyperlink reference or using the macro &quot;include page&quot;</strong></p>
         </td>
         <td style="text-align:left">Question</td>
         <td style="text-align:left">No documentation (from InfoSec or industry best practice sites)</td>
         <td style="text-align:left">
            <p>- Bookmark on local system internal (InfoSec) or external (Industry best practice). Not all squad members has reference</p>
            <p>- copy/clone another confluence page </p>
         </td>
         <td style="text-align:left">
            <p>- In the squad confluence space reference by in hyperlink</p>
            <p>- In the squad confluence space reference by &quot;include page&quot; </p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
         <td style="text-align:left">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:left"></td>
         <td style="text-align:left"></td>
      </tr>
   </tbody>
</table>
