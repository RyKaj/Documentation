###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Quality Assurance (QA)](https://github.com/RyKaj/Documentation/tree/master/QA/README.md) |
------------


# Quality Assurance (QA) :Severity vs. Priority

## Severity

Severity is defined as the degree of impact a
[Defect](https://www.guru99.com/the-unconventional-guide-to-defect-management.md)
has on the development or operation of a component application being
tested.

Higher effect on the system functionality will lead to the assignment of
higher severity to the bug. [Quality Assurance](https://www.guru99.com/all-about-quality-assurance.md)
engineer usually determines the severity level of defect

## Priority

Priority is defined as the order in which a defect should be fixed.
Higher the priority the sooner the defect should be resolved.

Defects that leave the software system unusable are given higher
priority over defects that cause a small functionality of the software
to fail.

## Defect Severity and Priority Types

*In Software Testing, Defect severity can be categorized into four
class*

  - **Critical**: This defect indicates complete shut-down of the
	process, nothing can proceed further
  - **Major**: It is a highly severe defect and collapses the system.
	However, certain parts of the system remain functional
  - **Medium**: It causes some undesirable behavior, but the system is
	still functional
  - **Low**: It won't cause any major break-down of the system

*Defect priority can be categorized into three class*

  - **Low:** The Defect is an irritant but repair can be done once the
	more serious Defect has been fixed
  - **Medium:** During the normal course of the development activities
	defect should be resolved. It can wait until a new version is
	created
  - **High:** The defect must be resolved as soon as possible as it
	affects the system severely and cannot be used until it is fixed

## Tips for determining the Severity of a Defect

  - **Decide the frequency of occurrence:** In some cases, if the
	occurrence of a minor-defect is frequent in the code, it can be more
	severe. So from a user's perspective, it is more serious even though
	it is a minor defect.
  - **Isolate the defect:** Isolating the defect can help to find out
	its severity of the impact.

![](https://www.guru99.com/images/5-2015/050115_0552_PriorityVsS1.gif)

## Priority vs Severity: Key Difference

<table>
	<thead>
		<tr>
			<th>Priority</th>
			<th>Severity</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Defect Priority has defined the order in which the developer should resolve a defect</td>
			<td>Defect Severity is defined as the degree of impact that a defect has on the operation of the product</td>
		</tr>
		<tr>
			<td>
				<p>Priority is categorized into three types</p>
				<ul>
					<li>Low</li>
					<li>Medium</li>
					<li>High</li>
				</ul>
			</td>
			<td>
				<p>Severity is categorized into five types</p>
				<ul>
					<li>Critical</li>
					<li>Major</li>
					<li>Moderate</li>
					<li>Minor</li>
					<li>Cosmetic</li>
				</ul>
			</td>
		</tr>
		<tr>
			<td>Priority is associated with scheduling</td>
			<td>Severity is associated with functionality or standards</td>
		</tr>
		<tr>
			<td>Priority indicates how soon the bug should be fixed</td>
			<td>Severity indicates the seriousness of the defect on the product functionality</td>
		</tr>
		<tr>
			<td>Priority of defects is decided in consultation with the manager/client</td>
			<td>QA engineer determines the severity level of the defect</td>
		</tr>
		<tr>
			<td>Priority is driven by business value</td>
			<td>Severity is driven by functionality</td>
		</tr>
		<tr>
			<td>Its value is subjective and can change over a period of time depending on the change in the project situation</td>
			<td>Its value is objective and less likely to change</td>
		</tr>
		<tr>
			<td>High priority and low severity status indicates, defect have to be fixed on immediate bases but does not affect the application</td>
			<td>High severity and low priority status indicates defect have to be fixed but not on immediate bases</td>
		</tr>
		<tr>
			<td>Priority status is based on customer requirements</td>
			<td>Severity status is based on the technical aspect of the product</td>
		</tr>
		<tr>
			<td>During UAT the development team fix defects based on priority</td>
			<td>During SIT, the development team will fix defects based on the severity and then priority</td>
		</tr>
	</tbody>
</table>


Example of Defect Severity and Priority

![](https://www.guru99.com/images/5-2015/050115_0552_PriorityVsS2.png)

Let see an example of low severity and high priority and vice versa

  - **A very low severity with a high priority:** A logo error for any
	shipment website, can be of low severity as it not going to affect
	the functionality of the website but can be of high priority as you
	don't want any further shipment to proceed with the wrong logo.

  - **A very high severity with a low priority:** Likewise, for flight
	operating website, a defect in reservation functionality may be of
	high severity but can be a low priority as it can be scheduled to
	release in a next cycle.

## Defect Triage

Defect triage is a process that tries to do the re-balancing of the
process where the test team faces the problem of limited availability of
resources. So, when there are large number of the defect and limited
testers to verify them, defect triage helps to try to get as many
defects resolved based on defect parameters like severity and priority.

### How to determine Defect Triage

![](https://www.guru99.com/images/5-2015/050115_0552_PriorityVsS3.png)

Most systems use priority as the main criteria to assess the defect.
However, a good triage process considers the severity as well.

The triage process includes the following steps

  - Reviewing all the defects including rejected defects by the team
  - Initial assessment of the defects is based on its content and
	respective priority and severity settings
  - Prioritizing the defect based on the inputs
  - Assign the defect to correct release by product manager
  - Re-directs the defect to the correct owner/team for further action

## Guidelines that every tester should consider before selecting a severity

Severity parameter is assessed by the tester whereas the priority
parameter is assessed by the product manager or by the triage team. For
prioritizing the defect, it is imperative for a tester to choose the
right severity to avoid confusion with the development team.

  - Understand the concept of priority and severity well
  - Always assign the severity level based on the issue type as this
	will affect its priority
  - Understand how a particular scenario or [Test Case](https://www.guru99.com/test-case.md) would affect the
	end-user
  - Need to consider how much time it would take to fix the defect based
	on its complexity and time to verify the defect

References

  - [Guru99 - Defect Severity and Prioirty](https://www.guru99.com/defect-severity-in-software-testing.md)
