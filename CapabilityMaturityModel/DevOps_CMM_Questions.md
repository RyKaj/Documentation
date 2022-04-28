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
## DevOps Aspects
<table>
   <thead>
      <tr>
         <th style="text-align:center"><strong>Aspects</strong></th>
         <th style="text-align:center"><strong>Sub-aspects</strong></th>
         <th style="text-align:center"><strong>Evidence</strong></th>
         <th style="text-align:center"><strong>Evidence Type</strong></th>
         <th style="text-align:center"><strong>L1 STARTING</strong></th>
         <th style="text-align:center"><strong>L2 PRACTICING</strong></th>
         <th style="text-align:center"><strong>L3 SYSTEMATIC</strong></th>
         <th style="text-align:center"><strong>L4 MEASURING</strong></th>
         <th style="text-align:center"><strong>L5 INNOVATING</strong></th>
         <th style="text-align:center"><strong>Level</strong></th>
         <th style="text-align:center"><strong>Collaboration Notes</strong></th>
         <th style="text-align:center"><strong>Scoring Results</strong></th>
         <th style="text-align:center"><strong>Team</strong></th>
         <th style="text-align:center"><strong>Comment</strong></th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"><strong>Shift-left</strong></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p><a href="https://www.aquasec.com/cloud-native-academy/devsecops/shift-left-devops/#:~:text=The%20term%20%E2%80%9Cshift%20left%E2%80%9D%20refers,%2C%20security%2C%20and%20operations">https://www.aquasec.com/cloud-native-academy/devsecops/shift-left-devops/#:~:text=The%20term%20%E2%80%9Cshift%20left%E2%80%9D%20refers,%2C%20security%2C%20and%20operations</a>)</p>
            <p><a href="https://devops.com/devops-shift-left-avoid-failure/">https://devops.com/devops-shift-left-avoid-failure/</a></p>
            <p><a href="https://dzone.com/articles/the-shift-left-principle-and-devops-1">https://dzone.com/articles/the-shift-left-principle-and-devops-1</a></p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"><strong>Process</strong></td>
         <td style="text-align:center">
            <p><strong>Coding Policies</strong></p>
            <p></p>
            <p><strong>Note:</strong></p>
            <p>- <strong>SCM - Source Control Management</strong></p>
            <p>- <strong>Jenkins refer to reusable code a Shared Library</strong></p>
         </td>
         <td style="text-align:center">Is the build process scripts stored in SCM?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">Not using SCM</td>
         <td style="text-align:center">Scripts are only stored within the build process</td>
         <td style="text-align:center">Using SCM</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>Total Sub Aspects: 4</p>
            <p>Total Questions: 24</p>
            <p>Total Metrics: 3</p>
            <p>Total Sub Aspect Research: 3</p>
            <p>-----------------------------------------</p>
            <p>Total Sub Aspect Questions: 11</p>
            <p>Total Sub Aspect Metrics: 3</p>
            <p>Total Sub Aspect Research: 3</p>
            <p></p>
            <p>rephrase question <a href="https://github.com/atosorigin/DevOpsMaturityAssessment">https://github.com/atosorigin/DevOpsMaturityAssessment</a> - questions.json 310</p>
            <p><a href="https://www.perforce.com/blog/vcs/shared-code-at-scale">https://www.perforce.com/blog/vcs/shared-code-at-scale</a></p>
            <p><a href="https://medium.com/microsoftazure/devops-patterns-sharing-reusable-components-d351a9b4fdf9">https://medium.com/microsoftazure/devops-patterns-sharing-reusable-components-d351a9b4fdf9</a></p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is the reusable code centralized for all tribes and squad to use</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No reusable code is centralized.</td>
         <td style="text-align:center">All reusable code is centralized at tribe-level, some are centralized across tribes.</td>
         <td style="text-align:center">All reusable code is centralized and shared.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p><a href="https://medium.com/microsoftazure/devops-patterns-sharing-reusable-components-d351a9b4fdf9#:~:text=Shared%20Project,-The%20shared%20project&amp;text=That%20code%20is%20owned%20by,development%20teams%20in%20the%20organization">https://medium.com/microsoftazure/devops-patterns-sharing-reusable-components-d351a9b4fdf9#:~:text=Shared%20Project,-The%20shared%20project&amp;text=That%20code%20is%20owned%20by,development%20teams%20in%20the%20organization</a></p>
            <p><a href="https://medium.com/microsoftazure/devops-patterns-sharing-reusable-components-d351a9b4fdf9">https://medium.com/microsoftazure/devops-patterns-sharing-reusable-components-d351a9b4fdf9</a></p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is the reusable or non-reusable code only target for a specific squad to use?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">Code is only focus on a specific squad</td>
         <td style="text-align:center">Scripts is target for specific squad - could be refactor for all squads</td>
         <td style="text-align:center">Scripts are not target for a specific squad</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Do you have separate specific jobs to test the  reusable and non-reusable code - before the squad uses it &quot;Production&quot; (their SDLC).</p>
            <p></p>
            <p></p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>Note:</p>
            <p>- This question is focus on Groovy scripts</p>
            <p>- <a href="https://www.jenkins.io/doc/book/pipeline/development/">Pipeline Unit Testing Framework</a></p>
         </td>
         <td style="text-align:center">
            <p>No build process on unit test</p>
            <p>Build process is clone, clone job becomes the test environment.</p>
         </td>
         <td style="text-align:center">
            <p>- No dedicated build process to run test against reusable and non-reusable code test </p>
            <p>- Dedicated build process and but not centralize to run test against reusable and non-reusable code</p>
         </td>
         <td style="text-align:center">Dedicated build process and centralize to run test against reusable and non-reusable code</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>Does the reusable code have a centralize dedicated job(s) to run unit test</p>
            <p></p>
            <p><a href="https://www.jenkins.io/doc/book/pipeline/development/">https://www.jenkins.io/doc/book/pipeline/development/</a></p>
            <p></p>
            <p>Rephrased question:</p>
            <p>Is there a separate dedicated Shared Library (reusable and non-reusable code) to execute &quot;unit test&quot; before promoting the script to squad&#39;s jobs?</p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is the branching strategy protecting the version the squad uses - until script has been properly tested</td>
         <td style="text-align:center">
            <p>Question</p>
            <p>Note:</p>
            <p>Production - what all Jenkins instance and jobs reference</p>
         </td>
         <td style="text-align:center">No branching strategy</td>
         <td style="text-align:center">Branch is only develop and main/master</td>
         <td style="text-align:center">branching strategy separates script changes (feature branch), full unit test (develop branch), and branch squad will use as &quot;production&quot; (main branch)</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Are the scripts written generically and/or data driven vs hard coded values and constraint to pipeline parameters?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">Script is hard coded</td>
         <td style="text-align:center">Scripts are using map parameter and data driven/generic</td>
         <td style="text-align:center">Coded generically and data driven</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What is the percentage of reusable and non-reusable scripts aren&#39;t using master branch</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">100%</td>
         <td style="text-align:center">50-50</td>
         <td style="text-align:center">0%</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p><a href="https://cloud.google.com/architecture/devops/devops-tech-code-maintainability">https://cloud.google.com/architecture/devops/devops-tech-code-maintainability</a></p>
            <p></p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Does the squad have access to the dependencies repo&#39;s to to build?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No access</td>
         <td style="text-align:center">Some squad members only</td>
         <td style="text-align:center">All squad members</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>How many different versions of the same script in the library do we have in production. </p>
            <p></p>
            <p>How many of those different version are being used?</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">To many to track</td>
         <td style="text-align:center">&lt; 5 different versions</td>
         <td style="text-align:center">Single version</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"><a href="https://cloud.google.com/architecture/devops/devops-tech-code-maintainability">https://cloud.google.com/architecture/devops/devops-tech-code-maintainability</a></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Are the parameters scripted?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>What tools do you use to validate Jenkins Pipeline syntax?</p>
            <p></p>
            <p>Note:</p>
            <p>IDE: </p>
            <p>- VS Code - Jenkins Pipeline Linter </p>
            <p>- Eclipse - Jenkins Editor</p>
            <p>- Atom linter-jenkins package</p>
            <p>- Subline Text Jenkinsfile package</p>
            <p>CLI</p>
            <p>- <a href="https://github.com/koalaman/shellcheck">ShellCheck</a></p>
            <p>- s</p>
            <p></p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">None</td>
         <td style="text-align:center">Execute Job to generate syntax issues</td>
         <td style="text-align:center">Using IDE / CLI</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p><a href="https://www.jenkins.io/doc/book/pipeline/development/">https://www.jenkins.io/doc/book/pipeline/development/</a></p>
            <p><a href="https://www.jenkins.io/doc/book/blueocean/pipeline-editor/">https://www.jenkins.io/doc/book/blueocean/pipeline-editor/</a></p>
            <p><a href="https://www.jenkins.io/blog/2017/05/18/pipeline-dev-tools/">https://www.jenkins.io/blog/2017/05/18/pipeline-dev-tools/</a></p>
            <p></p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What is the script Duplication percentage?</td>
         <td style="text-align:center">
            <p>Metric</p>
            <p></p>
            <p>Note:</p>
            <p>How much can be consolidated to generic shared library script(s)</p>
            <p></p>
         </td>
         <td style="text-align:center">&gt; 40%</td>
         <td style="text-align:center">&lt; 40%</td>
         <td style="text-align:center">&lt; 30%</td>
         <td style="text-align:center">&lt; 20%</td>
         <td style="text-align:center">&lt; 10%</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"><a href="https://cloud.google.com/architecture/devops/devops-tech-code-maintainability">https://cloud.google.com/architecture/devops/devops-tech-code-maintainability</a></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What is the % code churn ( code reworked ) per sprint/request</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"><code> </code><a href="https://cloud.google.com/architecture/devops/devops-tech-code-maintainability">https://cloud.google.com/architecture/devops/devops-tech-code-maintainability</a></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">How long does  it take to make changes, test, and push to &quot;production&quot;</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center">&gt; 5 hr</td>
         <td style="text-align:center">&lt; 5 hr and &gt; 4 hr</td>
         <td style="text-align:center">&lt; 4hr and &gt; 3 hr</td>
         <td style="text-align:center">&lt; 3 hr and &gt; 2 hr</td>
         <td style="text-align:center">&lt; 1 hr</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"><a href="https://cloud.google.com/architecture/devops/devops-tech-code-maintainability">https://cloud.google.com/architecture/devops/devops-tech-code-maintainability</a></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What are the pipelines (Jobs name and full URL) that the squad uses?</td>
         <td style="text-align:center">
            <p>Research-Only</p>
            <p><strong>No Impact in CMM</strong></p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is the build process using Freestyle or Pipeline structure?</td>
         <td style="text-align:center">
            <p>Research-Only</p>
            <p><strong>No Impact in CMM</strong></p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Can you provide repo URL</p>
            <p>Can you provide the list of non-reusable and reusable</p>
         </td>
         <td style="text-align:center">
            <p>Research-Only</p>
            <p><strong>No Impact in CMM</strong></p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"><strong>Continuous Integration (CI) strategy</strong></td>
         <td style="text-align:center">
            <p>Is there documentation on the deployment steps?</p>
            <p><br>Can you provide the URL for us to review.</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No official documents</td>
         <td style="text-align:center">Not detailed enough</td>
         <td style="text-align:center">Documented for anyone to understand</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Total Sub Aspect Questions: 2</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Are there multiple documentation?</p>
            <p></p>
            <p>ie.. squad level, tribe level, organization wide?</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"><strong>Continuous Deployment (CD) strategy</strong></td>
         <td style="text-align:center">Is there documentation on the deployment steps?<br>Can you provide the URL for us to review.</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No official documents</td>
         <td style="text-align:center">Not detailed enough</td>
         <td style="text-align:center">Documented for anyone to understand</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Total Sub Aspect Questions: 2</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Are there multiple documentation?</p>
            <p></p>
            <p>ie.. squad level, tribe level, organization wide?</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"><strong>Environment strategy</strong></td>
         <td style="text-align:center">
            <p>For which of these is the configuration and management of environments automatically?</p>
            <p>- Virtual Machines</p>
            <p>- Networks</p>
            <p>- Operating System</p>
            <p>- Security Elements</p>
            <p>- The Application Stacks</p>
            <p>- The Applications</p>
         </td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>Note:</p>
            <p>- Identify if they are in POC or working on one.</p>
            <p>- Identify which environments they are using it.</p>
         </td>
         <td style="text-align:center">None / Unknown</td>
         <td style="text-align:center">Being used as part of the development</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>Total Sub Aspect Questions: 9</p>
            <p></p>
            <p><a href="https://aws.amazon.com/devops/what-is-devops/">https://aws.amazon.com/devops/what-is-devops/</a></p>
            <p>Question came from <a href="https://github.com/atosorigin/DevOpsMaturityAssessment">https://github.com/atosorigin/DevOpsMaturityAssessment</a> - questions.json</p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Do you offer self-service for squads members to provision an environment on-demand for their own needs?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center">Not yet, but each squad confirmed they&#39;ve got enough environments to fulfill their immediate needs.</td>
         <td style="text-align:center">Yes, this is an available option for all squad members.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Addresses concern of lack of/shared environments.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"><strong>31</strong></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What is the level of reliability (SLA) of test environments?</td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>Note:</p>
            <p>SLA - Service Level Agreement</p>
            <p></p>
         </td>
         <td style="text-align:center">&lt; 74%</td>
         <td style="text-align:center">75-89%</td>
         <td style="text-align:center">90+%</td>
         <td style="text-align:center">95+%</td>
         <td style="text-align:center">99+%</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Addresses unreliable environments.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">How would you complete this sentence: &quot;Squads have enough environments in ...% of their time during sprint&quot;.</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">&lt; 74%</td>
         <td style="text-align:center">75-89%</td>
         <td style="text-align:center">90+%</td>
         <td style="text-align:center">95+%</td>
         <td style="text-align:center">100%</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">100% thanks to self-service.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">How would you complete this sentence: &quot;The tribe has enough environments to deliver value after sprints in ...% of their time.&quot;</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">&lt; 74%</td>
         <td style="text-align:center">75-89%</td>
         <td style="text-align:center">90+%</td>
         <td style="text-align:center">95+%</td>
         <td style="text-align:center">100%</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Does the tribe have enough environments to do testing?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">None exists</td>
         <td style="text-align:center">
            <p>- Shared environments with other tribes/squads</p>
            <p>- Enough environments in normal operations.</p>
         </td>
         <td style="text-align:center">They always have enough environments thanks to self-service.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Environment for NFR testing.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Does the tribe have enough environments for stress/performance testing?</p>
            <p></p>
            <p>Note:</p>
            <p>Types of Performance Testing:</p>
            <p>- Capacity Testing</p>
            <p>- Load Testing</p>
            <p>- Volume Testing</p>
            <p>- Stress Testing</p>
            <p>- Soak Testing</p>
            <p>- Scalability Testing</p>
            <p>- Spike Testing</p>
            <p>- Configuration Testing</p>
            <p>- Availability &amp; Resilience Testing</p>
            <p></p>
            <p></p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">None exists</td>
         <td style="text-align:center">
            <p>- Shared environments with other tribes/squads</p>
            <p>- Enough environments in normal operations. (To cover all of the types of performance testing)</p>
         </td>
         <td style="text-align:center">They always have enough environments thanks to self-service.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>Environment for NFR testing.</p>
            <p><a href="https://www.stormforge.io/blog/types-performance-testing/">https://www.stormforge.io/blog/types-performance-testing/</a></p>
            <p></p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Does the tribe have enough environments for security testing?</p>
            <p></p>
            <p>Note:</p>
            <p>Types of Security Testing:</p>
            <p>- Vulnerability Scanning</p>
            <p>- Penetration Testing (Ethical Hacking)</p>
            <p>- Web Application Security Testing</p>
            <p>- API Security Testing</p>
            <p>- Configuration Scanning</p>
            <p>- Security Audits</p>
            <p>- Risk Assessment</p>
            <p>- Security Posture Assessment</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">None exists</td>
         <td style="text-align:center">
            <p>- Shared environments with other tribes/squads</p>
            <p>- Enough environments in normal operations.  (To cover all of the types of security testing</p>
         </td>
         <td style="text-align:center">They always have enough environments thanks to self-service.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>Environment for NFR testing.</p>
            <p></p>
            <p><a href="https://www.neuralegion.com/blog/security-testing/">https://www.neuralegion.com/blog/security-testing/</a></p>
            <p><a href="https://www.guru99.com/what-is-security-testing.html">https://www.guru99.com/what-is-security-testing.html</a></p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Does the tribe have enough environments for regulatory &amp; compliance testing?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">None exists</td>
         <td style="text-align:center">
            <p>- Shared environments with other tribes/squads</p>
            <p>- Enough environments in normal operations.  (To cover all of the types of regulatory testing)</p>
         </td>
         <td style="text-align:center">They always have enough environments thanks to self-service.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Environment for NFR testing.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is there a non-production environment that exactly replicates production server on build and configuration for performance, security, and regulatory &amp; compliance testing?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">
            <p>No</p>
            <p></p>
         </td>
         <td style="text-align:center">Sort of...</td>
         <td style="text-align:center">100% identical</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Sunny&#39;s suggestion</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is there a non-production environment that exactly replicates production server on hardware capabilities for performance, security, and regulatory &amp; compliance testing?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">
            <p>No</p>
            <p></p>
         </td>
         <td style="text-align:center">Sort of...</td>
         <td style="text-align:center">100% identical</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"><strong>Continuous Integration (CI) - Build Process</strong></td>
         <td style="text-align:center"><strong>Pipeline</strong></td>
         <td style="text-align:center">Is the Squad using CI to build and package their work?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center">Squad manually build and/or package part of the process</td>
         <td style="text-align:center">Yes, all own code are built and packaged by the CI</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>Total Sub Aspects: 5</p>
            <p>Total Questions: 13</p>
            <p>Total Metrics: 3</p>
            <p>-----------------------------------------</p>
            <p>Total Sub Aspect Questions: 10</p>
            <p>Total Sub Aspect Metrics: 3</p>
            <p>Total Sub Aspect Research: 0</p>
            <p></p>
            <p>Question came from <a href="https://app.comparativeagility.com/survey/DevOps">https://app.comparativeagility.com/survey/DevOps</a></p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Does each commit to squad&#39;s develop branch triggers build process?</td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>Note:</p>
            <p>Pending on branching strategy - Develop branch can be the central branch developer create &quot;feature&quot; branch off or is usually package for QA environment</p>
            <p></p>
         </td>
         <td style="text-align:center">No, does not trigger build</td>
         <td style="text-align:center">Manual execution of build process</td>
         <td style="text-align:center">Every commit to develop branch will trigger a build</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Question came from <a href="https://app.comparativeagility.com/survey/DevOps">https://app.comparativeagility.com/survey/DevOps</a></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>When developers coding standards are not met, does it break the build process?</p>
            <p></p>
            <p>Note: </p>
            <p>SQ Severity:</p>
            <p>- Blocker</p>
            <p>- Critical</p>
            <p>- Major</p>
            <p>- Minor</p>
            <p>- Info</p>
            <p></p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">
            <p>- Build does not break or coding standards are not verified</p>
            <p>- Coding metrics are set - not configured with in build process</p>
         </td>
         <td style="text-align:center">
            <p>- Coding standards are verified, only focus on Blockers issues </p>
            <p>- Coding standards are verified, only focus on Major or higher issues</p>
         </td>
         <td style="text-align:center">Coding standards are verified, any issue may break the build</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>Question came from <a href="https://github.com/atosorigin/DevOpsMaturityAssessment">https://github.com/atosorigin/DevOpsMaturityAssessment</a> - questions.json 257</p>
            <p></p>
            <p>Maybe duplicate to &quot;Is SonarQube  thresholds configured and does it fail the build process&quot;</p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>When coding security standards  are not met, does it break the build process?</p>
            <p></p>
            <p></p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>Question</p>
            <p>Note:</p>
            <p>Security Standards are set by InfoSec or InfoSec approved tools. Currently we are referring to SAST SonarQube to break the build</p>
         </td>
         <td style="text-align:center">Build does not break</td>
         <td style="text-align:center">Security standards are verified, major issues break the build</td>
         <td style="text-align:center">Security standards are verified, any issue may break the build</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>Question came from <a href="https://github.com/atosorigin/DevOpsMaturityAssessment">https://github.com/atosorigin/DevOpsMaturityAssessment</a> - questions.json 257</p>
            <p></p>
            <p></p>
            <p>Move this question to InfoSeec</p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">When any unit test case fails, does it break the build process?</td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
         </td>
         <td style="text-align:center">Does not break build</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Any failed unit test break the build</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">When unit test code coverage threshold is not met, does it break the build process?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">Does not break build</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Coding coverage are not met, break the build</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">When the build breaks, is it always the highest priority to resolve the builds issue?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">Broken builds is not top priority of team/committer is not always aware of it.</td>
         <td style="text-align:center">Will review the job within couple of days or when the squad informs them there is an issue with the job</td>
         <td style="text-align:center">
            <p>- Will review the job within the day</p>
            <p>- Top priority to resolve</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Question came from <a href="https://github.com/atosorigin/DevOpsMaturityAssessment">https://github.com/atosorigin/DevOpsMaturityAssessment</a> - questions.json 355</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is there adequate notifications in place to communicate the build status and failed build to the team?</td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>Note: </p>
            <p>- Automated emails from build process</p>
            <p>- Automated slack notification from build process</p>
            <p>- circuit</p>
         </td>
         <td style="text-align:center">No notification are sent - keeping the tab open and monitor the progress</td>
         <td style="text-align:center">E-mail or Slack with enough information including timestamp, build ID with a link, committer and commit message.</td>
         <td style="text-align:center">E-mail and Slack on both build successes and failures.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Question came from <a href="https://github.com/atosorigin/DevOpsMaturityAssessment">https://github.com/atosorigin/DevOpsMaturityAssessment</a> - questions.json 366</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Who is being notified on all build status?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No one, they need to check on the job through the browser</td>
         <td style="text-align:center">
            <p>Only one person</p>
            <p>Only one person from the team and one from squad</p>
         </td>
         <td style="text-align:center">The squad</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Can the squad see the overall (accumulative) health status of the build process? Other than the build tool.</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Can the tribe and other guilds/chapters see the overall (accumulative) health status of the build process?</p>
            <p>Other than the build tool.</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What is the build success rate</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center">&lt; 50%</td>
         <td style="text-align:center">&gt; 50% and &lt; 60%</td>
         <td style="text-align:center">&gt; 60% and &lt; 70%</td>
         <td style="text-align:center">&gt; 70% and &lt; 80%</td>
         <td style="text-align:center">&gt; 80%</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"><a href="https://confluence.pyrsoftware.ca/confluence/pages/createpage.action?spaceKey=ATX&amp;title=Metrics%252C+What+to+Measure%252C+Why+and+How&amp;linkCreation=true&amp;fromPageId=255682255">Metrics%2C What to Measure%2C Why and How</a></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What is the build time</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center">&gt; 60 mins</td>
         <td style="text-align:center">&lt; 60 mins and &gt; 45 mins</td>
         <td style="text-align:center">&lt; 45 mins and &gt; 35 mins</td>
         <td style="text-align:center">&lt; 30 mins and &gt; 25 mins</td>
         <td style="text-align:center">&lt; 10 mins</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p><a href="https://confluence.pyrsoftware.ca/confluence/pages/createpage.action?spaceKey=ATX&amp;title=Metrics%252C+What+to+Measure%252C+Why+and+How&amp;linkCreation=true&amp;fromPageId=255682255">Metrics%2C What to Measure%2C Why and How</a></p>
            <p></p>
            <p>Current Build times - <a href="https://grafana-inf-qa.pyrsoftware.ca/d/NIXWc1uik/jenkins-birds-eye-view-of-build-nodes?orgId=1">https://grafana-inf-qa.pyrsoftware.ca/d/NIXWc1uik/jenkins-birds-eye-view-of-build-nodes?orgId=1</a></p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"><strong>Test Automation</strong></td>
         <td style="text-align:center">Is Unit Test part of the build process?</td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>Note:</p>
            <p>This question is focus on Developers code</p>
            <p></p>
         </td>
         <td style="text-align:center">No - Unit Test Stage</td>
         <td style="text-align:center">Yes - Unit Test Stage (Sequential stage process)</td>
         <td style="text-align:center">Yes - Unit Test Stage (Parallel stage process)</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Total Sub Aspect Questions: 1</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"><strong>Automating Environments</strong></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Total Sub Aspect Questions: 0</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p><strong>Artifact Repository</strong></p>
            <p></p>
            <p><strong>Note:</strong></p>
            <p><strong>Company is using JFrog as their artifact repository?</strong></p>
         </td>
         <td style="text-align:center">Is the build package being uploaded by the build process and in an Artifact repository?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">Not using any artifact repository</td>
         <td style="text-align:center">Using legacy corporate artifact repository</td>
         <td style="text-align:center">Using current corporate artifact repository</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Total Sub Aspect Questions: 2</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Does the Build Process generate release notes automatically? (Auditor and ISO Compliance level acceptance)</td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>Note:</p>
            <p>Release notes is the technical documentation for the customer, regulator auditors, and ISO auditors on the changes to the product. </p>
            <p></p>
         </td>
         <td style="text-align:center">No release notes</td>
         <td style="text-align:center">
            <p>- Release Notes are manually generated</p>
            <p>- Gathering some data is automatic - updating release notes document is manual</p>
         </td>
         <td style="text-align:center">Release notes is generated in a fully automated way.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>OKR - Release Notes</p>
            <p><a href="https://jira.pyrsoftware.ca/jira/browse/ITSM-1739">ITSM-1739</a> - Getting issue details... STATUS </p>
            <p></p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p><del>Does InfoSec receive notification automatically when security standards  are not met?</del></p>
            <p></p>
            <p></p>
            <p>Do you inform InfoSec when you going to bypass SAST threshold.</p>
            <p>- L1 - No</p>
            <p>- L3 - Yes</p>
            <p></p>
            <p>What is your method of communication with InfoSec?</p>
            <p></p>
            <p>What SAST Severity would you inform InfoSec when bypassing SAST?</p>
            <p>- L1 - Never</p>
            <p>- L3 - All levels</p>
            <p>- L4 - Critical and Blocker</p>
            <p></p>
            <p>What SDLC stage do you inform InfoSec that you will be bypassing SAST threshold</p>
            <p>- L1 - Never</p>
            <p>- L2 - After deployment to Production</p>
            <p>- L3 -Before deployment to Production</p>
            <p>- L4 - Before or After Deployment to UAT</p>
            <p>- L5 - Before or After Deployment to QA</p>
            <p>How much lead time do you provide?</p>
            <p>- L1 - 0 min</p>
            <p>- L3 - 2 - 3 days from deployment date to _____ environment</p>
            <p>- L5 - &gt; 5 days of deployment date to ___ environment</p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>Note: </p>
            <p>- Automated emails from build process</p>
            <p>- Automated slack notification from build process</p>
         </td>
         <td style="text-align:center">No notifications</td>
         <td style="text-align:center">Manual email and/or manual slack notification</td>
         <td style="text-align:center">Automated email and/or slack notification</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>- Notification only when its a show stopper/ blocker. When threshold needs to be bypass/skipped </p>
            <p>&emsp;- SQ severity Critical or Blocker...</p>
            <p>- Only be notified after &quot;glass is broken&quot;. InfoSec might setup the process.</p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p><strong>SAST - Static Application Security Testing (e.g. Code Analysis / Integrated Analysis tool)</strong></p>
            <p></p>
            <p><strong>Note:</strong></p>
            <p><strong>This company is using SonarQube for SAST</strong></p>
         </td>
         <td style="text-align:center">Does the squad using a SAST tool to scan their code?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p><del>Question came from <a href="https://github.com/atosorigin/DevOpsMaturityAssessment">https://github.com/atosorigin/DevOpsMaturityAssessment</a> - questions.json 230</del></p>
            <p></p>
            <p><del>CWE - Security....</del></p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is the squad using a SAST tool to scan any binaries third party (not generated by the squads code)?</td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>Note:</p>
            <p>Binaries can come from other teams, or some sort of CDN. E.g. npm, nuget...</p>
         </td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"><del>Question came from <a href="https://github.com/atosorigin/DevOpsMaturityAssessment">https://github.com/atosorigin/DevOpsMaturityAssessment</a> - questions.json 237</del></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is the SAST tool thresholds configured for the squad</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No configured</td>
         <td style="text-align:center">Threshold exists but does not break the build.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>What is the Vulnerability  severity break down that SAST tool found?</p>
            <p></p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>Metric</p>
            <p>InfoSec</p>
            <p><strong>Results and Suggestions on improvement will come off InfoSec CMM</strong></p>
            <p>Note: </p>
            <p>SQ Severity:</p>
            <p>- Blocker</p>
            <p>- Critical</p>
            <p>- Major</p>
            <p>- Minor</p>
            <p>- Info</p>
            <p></p>
         </td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What is the Security Hotspots severity break down that  SAST tool found?</td>
         <td style="text-align:center">
            <p>Metric</p>
            <p>InfoSec</p>
            <p><strong>Results and Suggestions on improvement will come off InfoSec CMM</strong></p>
         </td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>Should we break it down by priority instead of total count</p>
            <p>Does the squad know who to report security issues to?</p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"><strong>Continuous Delivery (CD) process</strong></td>
         <td style="text-align:center"><strong>Build promotion</strong></td>
         <td style="text-align:center">
            <p>Non-Production</p>
            <p>Is the squad using a pipeline tool for Continuous Delivery. To automatically deploy to QA and UAT environments?</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No, &quot;cut/paste&quot; or cp SOURCE DIRECTORY</td>
         <td style="text-align:center">Package is deployed by CD tool - requires manual interaction</td>
         <td style="text-align:center">Package is deployed by CD tool - No manual interaction</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>Total Sub Aspects: 3</p>
            <p>Total Questions: 27</p>
            <p>Total Metrics: 16</p>
            <p>-----------------------------------------</p>
            <p>Total Sub Aspect Questions: 8</p>
            <p>Total Sub Aspect Metrics: 10</p>
            <p>Total Sub Aspect Research: 0</p>
            <p></p>
            <p>Question came from <a href="https://app.comparativeagility.com/survey/DevOps">https://app.comparativeagility.com/survey/DevOps</a></p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Production</p>
            <p>Is the squad using a pipeline tool for Continuous Delivery. To automatically deploy to Production?</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No, &quot;cut/paste&quot; or cp SOURCE DIRECTORY</td>
         <td style="text-align:center">Package is deployed by CD tool - requires manual interaction</td>
         <td style="text-align:center">Package is deployed by CD tool - No manual interaction</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Question came from <a href="https://app.comparativeagility.com/survey/DevOps">https://app.comparativeagility.com/survey/DevOps</a></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is the build package being rebuilt for each deployment or being pulled from Artifact repository?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">Each environment needs a fresh build.</td>
         <td style="text-align:center">Existing build artifacts are re-used from artifact repository for each environment.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Does anyone need to make any manual changes pre deployment or post deployment regardless of destination environment).</p>
            <p></p>
            <p>Notes:</p>
            <p>Changes can refer to config/ini file, some OS changes, some network changes, etc..</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">Yes - manual changes are required</td>
         <td style="text-align:center">Some manual changes pending on circumstances</td>
         <td style="text-align:center">No manual changes required</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Production Environment - When deploying is there any down time?</p>
            <p></p>
            <p>What is the average downtime per deployment?</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">
            <p>System is shut down - customer can not access the site</p>
            <p></p>
         </td>
         <td style="text-align:center">System is running - customers only have only limited</td>
         <td style="text-align:center">There&#39;s zero downtime regardless of what changes are required, no functional degradation, no noticeable impact on performance degradation.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Production Environment - What is the Deployment frequency</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center">Between once or twice per month or once or twice every six month</td>
         <td style="text-align:center">Between once or twice per week or once or twice per month</td>
         <td style="text-align:center">Once per sprint</td>
         <td style="text-align:center">Between once per day or once per week</td>
         <td style="text-align:center">On-demand (multiple deploys per day)</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"><a href="https://confluence.pyrsoftware.ca/confluence/pages/createpage.action?spaceKey=ATX&amp;title=Metrics%252C+What+to+Measure%252C+Why+and+How&amp;linkCreation=true&amp;fromPageId=255682255">Metrics%2C What to Measure%2C Why and How</a></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What is the Mean Time to Respond?</td>
         <td style="text-align:center">
            <p>Metric</p>
            <p>MTTR</p>
         </td>
         <td style="text-align:center">Between one week or one month</td>
         <td style="text-align:center">Less than 24 hours</td>
         <td style="text-align:center">Less than 12 hours</td>
         <td style="text-align:center">Less than 6 hours</td>
         <td style="text-align:center">Less than 1 hour</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What is the Mean Time to Acknowledge?</td>
         <td style="text-align:center">
            <p>Metric</p>
            <p>MTTA</p>
         </td>
         <td style="text-align:center">Between one week or one month</td>
         <td style="text-align:center">Less than 24 hours</td>
         <td style="text-align:center">Less than 12 hours</td>
         <td style="text-align:center">Less than 6 hours</td>
         <td style="text-align:center">Less than 1 hour</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"><strong>83</strong></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What is Mean Time to Resolve/Restore Service?</td>
         <td style="text-align:center">
            <p>Metric</p>
            <p>MTTR</p>
         </td>
         <td style="text-align:center">Between one week or one month</td>
         <td style="text-align:center">Less than 24 hours</td>
         <td style="text-align:center">Less than 12 hours</td>
         <td style="text-align:center">Less than 6 hours</td>
         <td style="text-align:center">Less than 1 hour</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p><a href="https://confluence.pyrsoftware.ca/confluence/pages/createpage.action?spaceKey=ATX&amp;title=Metrics%252C+What+to+Measure%252C+Why+and+How&amp;linkCreation=true&amp;fromPageId=255682255">Metrics%2C What to Measure%2C Why and How</a></p>
            <p></p>
            <p><strong>Mean time to recovery</strong> tells you how quickly you can get your systems back up and running.</p>
            <p>Add <strong>mean time to resolve</strong> to the mix and you start to understand the full scope of fixing and resolving issues beyond the actual downtime they cause.</p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What is Mean Time to Failure?</td>
         <td style="text-align:center">
            <p>Metric</p>
            <p>MTTF</p>
         </td>
         <td style="text-align:center">Between one week or one month</td>
         <td style="text-align:center">Less than 24 hours</td>
         <td style="text-align:center">Less than 12 hours</td>
         <td style="text-align:center">Less than 6 hours</td>
         <td style="text-align:center">Less than 1 hour</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p><a href="https://www.atlassian.com/incident-management/kpis/common-metrics#:~:text=MTTR%20">https://www.atlassian.com/incident-management/kpis/common-metrics#:~:text=MTTR%20</a>(mean%20time%20to%20recovery%20or%20mean%20time%20to%20restore,it%20becomes%20fully%20operational%20again.</p>
            <p></p>
            <p>Fold in <strong>mean time between failures</strong> and the picture gets even bigger, showing you how successful your team is at preventing or reducing future issues.</p>
            <p>And then add <strong>mean time to failure</strong> to understand the full lifecycle of a product or system.</p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Change Failure Count</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center">&gt;= 80%</td>
         <td style="text-align:center">&gt; 55% and &lt; 80%</td>
         <td style="text-align:center">&gt; 40% and &lt;= 55%</td>
         <td style="text-align:center">&gt; 15% and &lt;= 40%</td>
         <td style="text-align:center">&lt;= 15%</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p><a href="https://confluence.pyrsoftware.ca/confluence/pages/createpage.action?spaceKey=ATX&amp;title=Metrics%252C+What+to+Measure%252C+Why+and+How&amp;linkCreation=true&amp;fromPageId=255682255">Metrics%2C What to Measure%2C Why and How</a></p>
            <p></p>
            <p><strong>Change fail rate</strong> regarding how many times changes cause a deployment to fail as compared with the number of deployments</p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Change Failure Count</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center">&gt;= 80%</td>
         <td style="text-align:center">&gt; 55% and &lt; 80%</td>
         <td style="text-align:center">&gt; 40% and &lt;= 55%</td>
         <td style="text-align:center">&gt; 15% and &lt;= 40%</td>
         <td style="text-align:center">&lt;= 15%</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p><a href="https://confluence.pyrsoftware.ca/confluence/pages/createpage.action?spaceKey=ATX&amp;title=Metrics%252C+What+to+Measure%252C+Why+and+How&amp;linkCreation=true&amp;fromPageId=255682255">Metrics%2C What to Measure%2C Why and How</a></p>
            <p></p>
            <p><strong>Change fail rate</strong> regarding how many times changes cause a deployment to fail as compared with the number of deployments</p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Change Lead Time</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center">Between once or twice per month or once or twice every six month</td>
         <td style="text-align:center">Between once or twice per week or once or twice per month</td>
         <td style="text-align:center">
            <p>Between once per day or once per week</p>
            <p>On-demand (multiple deploys per day)</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">How long does it take to deploy to non-production environment</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center">&gt; 60 mins</td>
         <td style="text-align:center">&lt; 60 mins and &gt; 45 mins</td>
         <td style="text-align:center">&lt; 45 mins and &gt; 15 mins</td>
         <td style="text-align:center">&lt; 15 mins and &gt; 5 mins</td>
         <td style="text-align:center">&lt; 5 mins</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"><a href="https://confluence.pyrsoftware.ca/confluence/pages/createpage.action?spaceKey=ATX&amp;title=Metrics%252C+What+to+Measure%252C+Why+and+How&amp;linkCreation=true&amp;fromPageId=255682255">Metrics%2C What to Measure%2C Why and How</a></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">How long does it take to deploy to production environment</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center">&gt; 60 mins</td>
         <td style="text-align:center">&lt; 60 mins and &gt; 45 mins</td>
         <td style="text-align:center">&lt; 45 mins and &gt; 15 mins</td>
         <td style="text-align:center">&lt; 15 mins and &gt; 5 mins</td>
         <td style="text-align:center">&lt; 5 mins</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p><a href="https://confluence.pyrsoftware.ca/confluence/pages/createpage.action?spaceKey=ATX&amp;title=Metrics%252C+What+to+Measure%252C+Why+and+How&amp;linkCreation=true&amp;fromPageId=255682255">Metrics%2C What to Measure%2C Why and How</a></p>
            <p>Reference  <a href="file:///C:/confluence/display/RMS/PA%3ACO+Restart+Plan+-+2021.Build.07+-+SRE-13764">PA:CO Restart Plan - 2021.Build.07 - SRE-13764</a></p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>How do you roll back in case of a production deployment issue?</p>
            <p><del>If there is an deployment issue, will the deployment process automatically abort and rolled back without excessive friction</del></p>
            <p><del>Is it possible to roll back the application cleanly and reliably?</del></p>
            <p><del>What is the criteria to automatically rollback to previous version?</del></p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">Rollback is fully manual</td>
         <td style="text-align:center">Rollback process must be triggered manually, otherwise it&#39;s a fully automated process.</td>
         <td style="text-align:center">Rollback is fully automated including rollback trigger.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>Question came from <a href="https://app.comparativeagility.com/survey/DevOps">https://app.comparativeagility.com/survey/DevOps</a></p>
            <p>Question came from <a href="https://github.com/atosorigin/DevOpsMaturityAssessment">https://github.com/atosorigin/DevOpsMaturityAssessment</a> - questions.json 371</p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Can you deploy to production - at any time - on demand?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>Question came from <a href="https://app.comparativeagility.com/survey/DevOps">https://app.comparativeagility.com/survey/DevOps</a></p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Production Environment - Is the deployment pipeline using any advance deployment patterns: </p>
            <p>- Blue/Green</p>
            <p>- A/B Testing</p>
            <p>- Rolling Deployments</p>
            <p>- Canary</p>
            <p>- <del>Dark Launches</del></p>
            <p>- <del>Feature Toggles</del></p>
         </td>
         <td style="text-align:center">
            <p>Question</p>
            <p>Which process ___________</p>
            <p></p>
            <p>Note:</p>
            <p>- <strong>Blue/Green</strong></p>
            <p>It’s basically a technique for <em>releasing your application in a predictable</em> manner with an goal of <em>reducing any downtime associated with a release</em>. </p>
            <p></p>
            <p>- <strong>A/B testing</strong> </p>
            <p>is a way of <em>testing features in your application</em> for various reasons like usability, popularity, notice ability, etc, and how those factors influence the bottom line. </p>
            <p></p>
            <p>- <strong>Rolling Updates</strong></p>
            <p>is the concept of frequently delivering updates to applications.</p>
            <p>- <strong>Canary</strong> </p>
            <p>releases are a way of sending out a new version of your app into production that plays the role of a “canary” to get an idea of how it will perform (integrate with other apps, CPU, memory, disk usage, etc)</p>
            <p></p>
            <p><strong><del>Dark Launch</del></strong></p>
            <p><del>Releasing features to a subset of users</del></p>
            <p></p>
         </td>
         <td style="text-align:center">None</td>
         <td style="text-align:center">Yes - with some manual interaction</td>
         <td style="text-align:center">Yes - zero interaction</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p><a href="https://www.wsta.org/wp-content/uploads/2018/09/Best-Practices-for-DevOps-Advanced-Deployment-Patterns.pdf">https://www.wsta.org/wp-content/uploads/2018/09/Best-Practices-for-DevOps-Advanced-Deployment-Patterns.pdf</a></p>
            <p><a href="https://digital.ai/resources/all/advaced-deployment-patterns-WhitePaper">https://digital.ai/resources/all/advaced-deployment-patterns-WhitePaper</a></p>
            <p><a href="https://github.com/RyKaj/Documentation/blob/master/DevOps/Continuous-Deployment-Advance-Deployment-Patterns.md">https://github.com/RyKaj/Documentation/blob/master/DevOps/Continuous-Deployment-Advance-Deployment-Patterns.md</a></p>
            <p></p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"><strong>Test Automation</strong></td>
         <td style="text-align:center">Does the squad have an option to start a series of automated tests as they see fit</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>Total Sub Aspect Questions: 11</p>
            <p>Total Sub Aspect Metrics: 4</p>
            <p>Total Sub Aspect Research: 0</p>
            <p></p>
            <p>Question came from <a href="https://app.comparativeagility.com/survey/DevOps">https://app.comparativeagility.com/survey/DevOps</a></p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Will the test automation automatically execute when the deployment is successful to all various environments ( QA, UAT, Prod, DR ) ?</td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>Note:</p>
            <p>Skip next set of questions if the answer is NO here</p>
         </td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Is Smoke Test Automation part of the development process?</p>
            <p></p>
            <p>Note: </p>
            <p>Smoke Test - Checking if the deployment is stable or not.</p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>Note:</p>
            <p>Mark question skip if it is not applicable to the squad or the squad does not have those test cases at all.</p>
            <p></p>
            <p>Either options are acceptable</p>
            <p>- Executing Test Automation is a part of the scripts</p>
            <p>- the deployment process automatically or programmatically calls another Jenkins Job to execute Test Automation</p>
         </td>
         <td style="text-align:center">Squad has the tests, not integrated to Jenkins**</td>
         <td style="text-align:center">
            <p>Manually execute Test Automation - not hooked up in Jenkins</p>
            <p>Manually execute Jenkins job</p>
         </td>
         <td style="text-align:center">Jenkins job is automatically executed post deployment</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p><a href="https://testautomationu.applitools.com/test-automation-in-devops/">https://testautomationu.applitools.com/test-automation-in-devops/</a></p>
            <p></p>
            <p>Stopped Here</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Is Regression Test Automation part of the development process?</p>
            <p></p>
            <p>Note: </p>
            <p>Regression Test - Checking existing features has not changed unintentional</p>
            <p>- This would also be classified as End to End Testing</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">Squad has the tests, not integrated to Jenkins</td>
         <td style="text-align:center">
            <p>Manually execute Test Automation - not hooked up in Jenkins</p>
            <p>Manually execute Jenkins job</p>
         </td>
         <td style="text-align:center">Jenkins job is automatically executed post deployment</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>is API Test Automation part of the development process?</p>
            <p></p>
            <p>Note: </p>
            <p>To test the end points of the application</p>
            <p></p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">Squad has the tests, not integrated to Jenkins</td>
         <td style="text-align:center">
            <p>Manually execute Test Automation - not hooked up in Jenkins</p>
            <p>Manually execute Jenkins job</p>
         </td>
         <td style="text-align:center">Jenkins job is automatically executed post deployment</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Is Security Test Automation part of the development process?</p>
            <p></p>
            <p>Note: </p>
            <p>To cover functional and non-functional test for any vulnerabilities</p>
            <p></p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">
            <p>Squad has the tests, not integrated to Jenkins </p>
            <p>Manually execute Test Automation - not hooked up in JenL1: No test automation</p>
         </td>
         <td style="text-align:center">
            <p>Manually execute Test Automation - not hooked up in Jenkins</p>
            <p>Manually execute Jenkins job</p>
         </td>
         <td style="text-align:center">Jenkins job is automatically executed post deployment</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Is Performance Test Automation part of the development process?</p>
            <p></p>
            <p>Note: </p>
            <p>Test the responsiveness and stability when under load and stress</p>
            <p></p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">
            <p>Squad has the tests, not integrated to Jenkins </p>
            <p>Manually execute Test Automation - not hooked up in Jenkins</p>
         </td>
         <td style="text-align:center">Manually execute Jenkins job</td>
         <td style="text-align:center">Jenkins job is automatically executed post deployment</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Are automated test regularly run at least once per day and are part of the standard workflow</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Deployment to Production - Does the squad feel confident when all test automated pass. Those test cases will not be found by the customer</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center">Zero confidence</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">When any test automation has a test case failure. Is it likely to indicate a real defect?</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Are all environments (Dev, QA, UAT) configuration consistent with production environment?</p>
            <p></p>
            <p>Ie..</p>
            <p>If you think of variable driven process. It would not matter on the different permission names, server IP/Name, etc..</p>
            <p></p>
         </td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Non-Production</p>
            <p>What is the test case pass percentage?</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">&lt; 20</td>
         <td style="text-align:center">&lt; 40% and &gt; 20</td>
         <td style="text-align:center">&lt; 60% and &gt; 40</td>
         <td style="text-align:center">&lt; 80% and &gt; 60</td>
         <td style="text-align:center">&gt; 80%</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Metrics What to Measure Why and How</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Non-Production</p>
            <p>What is the defect escape rate?</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">&lt; 20</td>
         <td style="text-align:center">&lt; 40% and &gt; 20</td>
         <td style="text-align:center">&lt; 60% and &gt; 40</td>
         <td style="text-align:center">&lt; 80% and &gt; 60</td>
         <td style="text-align:center">&gt; 80%</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Metrics What to Measure Why and How</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Production</p>
            <p>What is the test case pass percentage?</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">&lt; 20</td>
         <td style="text-align:center">&lt; 40% and &gt; 20</td>
         <td style="text-align:center">&lt; 60% and &gt; 40</td>
         <td style="text-align:center">&lt; 80% and &gt; 60</td>
         <td style="text-align:center">&gt; 80%</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Metrics What to Measure Why and How</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Production</p>
            <p>What is the defect escape rate?</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">&lt; 20</td>
         <td style="text-align:center">&lt; 40% and &gt; 20</td>
         <td style="text-align:center">&lt; 60% and &gt; 40</td>
         <td style="text-align:center">&lt; 80% and &gt; 60</td>
         <td style="text-align:center">&gt; 80%</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">Metrics What to Measure Why and How</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"><strong>Automating Environments</strong></td>
         <td style="text-align:center">
            <p>Is lower environment infrastructure creation and configuration done via automation scripts?</p>
            <p></p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">
            <p>We do not address this issue by policy or published procedure.</p>
            <p>Teams can use whatever tools or approach suits them for provisioning lower environments.</p>
         </td>
         <td style="text-align:center">
            <p><code> </code>All environments are provisioned via our IT Service Management processes managed by SLA</p>
            <p>Standard lower environments are available via self service, with configuration or modification upon demand, and non-standard on </p>
         </td>
         <td style="text-align:center">Teams can access resources on demand and/or configured as specified via self-service.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>Total Sub Aspect Questions: 8</p>
            <p>Total Sub Aspect Metrics: 2</p>
            <p>Total Sub Aspect Research: 0</p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is higher environment infrastructure creation and configuration done via automation scripts?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">
            <p>We do not address this issue by policy or published procedure.</p>
            <p>Teams can use whatever tools or approach suits them for provisioning lower environments.</p>
         </td>
         <td style="text-align:center">
            <p>All environments are provisioned via our IT Service Management processes managed by SLA</p>
            <p>Standard lower environments are available via self service, with configuration or modification upon demand, and non-standard on request</p>
         </td>
         <td style="text-align:center">Teams can access resources on demand and/or configured as specified via self-service.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Does the squad have an efficient system in place to help them debug and understand various environment systems without depending on external teams or multiple tools.</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center">
            <p>Non useful information</p>
            <p>Little information, more investigation using other tools</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p>Maybe we need to break this down to production and non-production</p>
            <p>VSM perspective</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Can the squad see the overall (accumulative) health status of the deployment process on various environments?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">VSM perspective</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Can the tribe and other guilds, chapters see the overall (accumulative) health status of the deployment  process on various environments?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Can anyone (tribe, squad, guilds, chapters) see the overall (accumulative) status on Unit Test code coverage</td>
         <td style="text-align:center">Metric???</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Can anyone (tribe, squad, guilds, chapters) see the overall (accumulative) status on Security standards?</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Can anyone (tribe, squad, guilds, chapters) see the overall (accumulative) status on Test Automation ?</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center">No</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Yes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Is there dedicated testing environments for the squad</p>
            <p>Testing Environment examples:..</p>
            <p>- manual testing</p>
            <p>- automation testing</p>
            <p>- regression testing</p>
            <p>- performance testing</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">How long does it take to spin up a server for people/customers to use</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center">
            <p><a href="https://www.sciencedirect.com/science/article/pii/S0164121220301618#:~:text=Infrastructure%2Das%2Dcode%20">https://www.sciencedirect.com/science/article/pii/S0164121220301618#:~:text=Infrastructure%2Das%2Dcode%20</a>(IaC,configuration%20or%20interactive%20configuration%20tools.</p>
            <p>Zip file is from the above URL.</p>
            <p></p>
            <p><img src="Aspose.Words.7eaa38b6-9d26-412c-8a9c-bffda6f042f3.003.png" alt=""></p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What percentage of scripts success when provisioning an environment with zero interactions?</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">&lt; 50%</td>
         <td style="text-align:center">&gt; 51% - &lt; 60%</td>
         <td style="text-align:center">&gt; 61% - &lt; 70%</td>
         <td style="text-align:center">&gt; 71% - &lt; 80%</td>
         <td style="text-align:center">&gt; 81%</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>What is the Preliminary environment health check available for QA&#39;s different Environment</p>
            <p>- manual testing</p>
            <p>- automation testing</p>
            <p>- regression testing</p>
            <p>- performance testing</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">&lt; 20%</td>
         <td style="text-align:center">&lt; 80%</td>
         <td style="text-align:center">&gt; 80</td>
         <td style="text-align:center">&gt; 95%</td>
         <td style="text-align:center">&gt; 99.9%</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>What is the Preliminary environment health check available for UAT different Environment</p>
            <p>- manual testing</p>
            <p>- automation testing</p>
            <p>- regression testing</p>
            <p>- performance testing</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">&lt; 20%</td>
         <td style="text-align:center">&lt; 80%</td>
         <td style="text-align:center">&gt; 80</td>
         <td style="text-align:center">&gt; 95%</td>
         <td style="text-align:center">&gt; 99.9%</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"><strong>RK TechOps</strong></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What environments do you monitor</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>How do you test new systems?</p>
            <p>Manual or Automated?</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What monitoring tools do you use?</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">How often does the system crash or require reboot?</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"><strong>TechOps (Technical Operations)</strong></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"><strong>General Support (Sub section)</strong></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Do we know what service we are delivering?</td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>General procedures and processes exist and are well documented.</p>
         </td>
         <td style="text-align:center">There are little or no documented procedures or they are seldom followed</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">General processes are documented but followed only ad-hoc</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">All processes are documented and consistently followed by the entire team without variation from person to person</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Do we know what systems we are responsible for?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is everything above documented clearly and visible for people outside of the team/dept.</td>
         <td style="text-align:center">
            <p>Metric</p>
            <p></p>
            <p>Note:</p>
            <p>CMDB = Configuration Management Database </p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is the support policy clearly defined?</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Are team roles defined and understood?</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is the scope of our service defined?</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Responsible systems documented in the CMDB?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Research-Only</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"><strong>Incident and problem management (sub section)</strong></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Do you have a defined and documented prioritization matrix which covers impact and severity?</td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>The incident and problem management process is defined, measured and followed</p>
         </td>
         <td style="text-align:center">There is no incident and problem management process documented and the management of such is varied across the team</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">The incident and problem management process is documented and mostly followed</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">The incident and problem management process is documented, published and always followed by the team and SLAs adhered to</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Do you use an Major Incident Report (MIR) template documented?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What template document type are you currently using?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Do you have a 24/7 on-call for critical incident support roster in place?</p>
            <p>Is this information published for the team and outside the team?</p>
         </td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>Note:</p>
            <p>MIR = Manufacturer Incident Report</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Do you have a defined escalation process documented with defined roles and trigger points for major incident escalation?</p>
            <p>Is this information published for the team and outside the team?</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Do you have a defined and documented major incident communication process including audience, frequency &amp; content?</p>
            <p>Is this information published for the team and outside the team?</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Are incidents triaged with the correct severity/priority and assigned correctly?</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">MIRs are produced for major incidents (P0-P1) within 7 days of incident resolution</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Root Cause Analysis (RCA) is performed for major incidents and cause identified</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">All major incidents are resolved within 30 minutes</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">The major incident communications process is followed as documented</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Mean Time To Resolve (MTTR)</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Metrics What to Measure Why and How</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"><strong>147</strong></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What is the average time for IT service or other configuration item can perform its agreed function without interruption</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Metrics What to Measure Why and How</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center">
            <p><strong>Technical Operations (sub section)</strong></p>
            <p></p>
            <p><strong>Tooling</strong></p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Do you use Jira for all planned and unplanned work?</td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>The team has well developed tooling practices and integration</p>
         </td>
         <td style="text-align:center">Tooling use underdeveloped or non-existent with work done via email, DM (undocumented)</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Tooling use is part of the day to day operation of the team and covers all planned and unplanned work</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Communication, notification, monitoring and workflow tooling is adopted, integrated and consistently used by the entire team</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Do you have fully realized Jira dashboards (both internal and business facing) that represents the team&#39;s work?</td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>Note:</p>
            <p>DMS = Digital Management System. A software business process management solution which provides you with a centralize online hub to create, manage, share, track, and find digital assets, to mange the creative process.</p>
            <p>E.g. </p>
            <p>- Documents</p>
            <p>- Images</p>
            <p>- Audio content</p>
            <p>- Video</p>
            <p>- Animations</p>
            <p>- Media files</p>
            <p>- Graphics</p>
            <p>- Presentations</p>
            <p>- Any digital media that includes the right to use</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Do have and use integrated communications tools such as Slack, Page Duty etc?</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Are you using integrated into the team&#39;s Jira project and workflows?<br>e.g. Slack, Pager Duty, etc</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Does the teams confluence space clearly cover and understood by people outside of the team?</p>
            <p>- the teams process</p>
            <p>- teams information</p>
            <p>- specifications and other persistent data catalogue</p>
            <p></p>
            <p><del>Is your confluence space configured maturely, with processes, team information, specifications and other persistent data catalogued clearly?</del></p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Do you have a DMS catalog?</p>
            <p>What is the DMS tool name?</p>
         </td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center">
            <p><strong>Technical Operations (sub section)</strong></p>
            <p></p>
            <p><strong>Change Approval</strong></p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Can all production changes be approved for release within the team?</p>
            <p>If not - what type of changes that need approval outside the team?</p>
         </td>
         <td style="text-align:center">
            <p>Question</p>
            <p></p>
            <p>The change approval process is self sufficient and geared towards risk mitigation</p>
         </td>
         <td style="text-align:center">Changes are made to production with some risk management. Changes cause longer than planned outages and introduce production bugs</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Changes are made with risk mitigation in mind. They are documented and planned. Outages are within planned windows and few production bugs are introduced</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">All changes are documented, risk mitigation plans developed with rollback plans and monitoring in place.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Are production changes documented and steps are easy to follow?</p>
            <p>What production changes are required to on an daily, weekly, monthly, quarterly, yearly, etc... basis.</p>
            <p>What has been automated and what still needs to be automated?</p>
            <p></p>
         </td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Are production changes subject to peer review in Staging environment?</td>
         <td style="text-align:center">Research-Only</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Are production changes assessed, risk level identified, risk mitigation plan and rollback plan created prior to release?</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>I assume this question might be temporary until the DevOps process matures.</p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What is your documented release communication strategy?</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">This might now be in the proper area. This might fall under Release Management team or Delivery Manger role</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is there enough time allocated to the outage window to make production changes ( infrastructure, operating system update, network, proxy, etc..).</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Original question &quot;Are the Production changes  are completed within the allotted outage window&quot;</p>
            <p>This might now be in the proper area. This might fall under Release Management team or Delivery Manger role</p>
            <p></p>
            <p><a href="file:///C:/confluence/pages/createpage.action?spaceKey=ATX&amp;title=Metrics%252C+What+to+Measure%252C+Why+and+How&amp;linkCreation=true&amp;fromPageId=255682255">Metrics%2C What to Measure%2C Why and How</a> - Service Availability</p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What is the average allocated outage window?</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Are there any defects raise resulting in Production changes ( infrastructure, operating system update, network, proxy, etc..)?</p>
            <p>Is there any metrics tracking this?</p>
            <p>Can the metrics be pulled into a graphical representation?</p>
         </td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Is there any Rollback plans documented before each Production changes ( infrastructure, operating system update, network, proxy, etc..)?</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Number of releases without a rollback</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>( infrastructure, operating system update, network, proxy, etc..).</p>
            <p>Can we generate this metric from a tool?</p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Number of outages caused by a release and how long were the outages?</td>
         <td style="text-align:center">Research-Only</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>( infrastructure, operating system update, network, proxy, etc..).</p>
            <p>Can we generate this metric from a tool?</p>
         </td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Number of Incidents caused by a release</td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Can we generate this metric from a tool?</td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Question</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center">
            <p><strong>Technical Operations</strong> </p>
            <p><strong>(sub section)</strong></p>
            <p><strong>Monitoring</strong></p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>Do you have real-time monitoring dashboards?</p>
            <p></p>
         </td>
         <td style="text-align:center">
            <p>Research-Only</p>
            <p></p>
            <p>There is complete systems monitoring and alerting coverage</p>
         </td>
         <td style="text-align:center">There is little to no real-time monitoring. Monitoring is reactionary rather than preventative</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Monitoring of key, mission critical systems exist but coverage is limited and alerting underdeveloped</td>
         <td style="text-align:center"></td>
         <td style="text-align:center">100% of responsible systems have coverage with advanced notification and alerting integration.</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What real-time monitoring dashboards tools are you using?</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Do you have a solution to report key business and system metrics?</td>
         <td style="text-align:center">Metric</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Do you have monitoring linked to notification tooling (eg; Pager Duty, Slack)?</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">What monitoring notification tools are you using?</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Systems monitoring coverage</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
      <tr>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">Outages/System Degradation incidents prevented by monitoring and alerts</td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
         <td style="text-align:center">
            <p>- L1</p>
            <p>- L2</p>
            <p>- L3</p>
            <p>- L4</p>
            <p>- L5</p>
            <p>- Skipped</p>
         </td>
         <td style="text-align:center"></td>
         <td style="text-align:center"></td>
      </tr>
   </tbody>
</table>
