###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Unit Test](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/UnitTest/README.md) |
------------


# Information Technology : Code Coverage


In general, code coverage is a measurement of how much of the production
code is executed while your automated tests are running. By running a
suite of tests and looking at code coverage data, you can get a general
sense of how much of your application is being tested.

There are many kinds of code coverage — the most common ones are line
coverage and branch coverage. Most tools focus on line coverage, which
just tells you if a specific line was covered. Branch is more granular,
as it tells you if *each path through the code* is covered.

Code coverage is an important metric, but remember that increasing it is
a means to an end. It's great for finding gaps in testing, but it's not
the only thing to focus on. Be careful not to spend too much effort
trying to achieve 100% coverage — it may not even be possible or
feasible, and really the quality of your tests is the important thing.
That being said, achieving at least 60% coverage for your projects is a
good starting point, and 80% or more is a good goal to set. Obviously,
it's up to you to decide what that goal should be.

> This type of analysis is  ***statement coverage*** . Many such tools also analyze  ***branch coverage*** , i.e. given a branching condition in the code, are all the evaluated possibilities reached by a test?

It's also valuable if you have automated tools that not only measure
code coverage but also keep track how much modified code is being
covered by tests, because this can provide visibility into whether
enough tests are being written along with changes in production code.

See here an example code coverage report:

<kbd>![](https://blog.parasoft.com/hs-fs/hubfs/Blogs/Two%20Big%20Traps%20of%20Code%20Coverage%20Image%202.png?width=1211&name=Two%20Big%20Traps%20of%20Code%20Coverage%20Image%202.png)<kbd>

Another thing to keep in mind is that, when writing new tests, be
careful of focusing on line coverage alone, as single lines of code can
result in multiple code paths, so make sure your tests validate these
code paths. Line coverage is a useful quick indicator, but it isn't the
only thing to look for.

The most obvious way to increase coverage is simply to add more tests
for more code paths, and more use-cases of the method under test. A
powerful way to increase coverage is to use parameterized tests.

Ironically,  **none of these tests verified the result** — they simply
called the functions. Yet that still counts as 100% coverage.

The idea of code coverage stems from the principle that no code should
enter production without some sort of test.

That might seem extreme if all your tests are “up close” white-box unit
tests. But if you zoom out a tad and write [component
tests](https://medium.com/@SoftwareReality/unit-tests-vs-component-tests-size-isnt-everything-eaded162c595)
instead, then more code can be covered by a single test. This makes high
levels of coverage more achievable:

<kbd>![](https://miro.medium.com/max/4255/1*yH1k3UAyaJ1bDYXkQh1dWA.jpeg)</kbd>

In the above diagram, the component test is focused on function `a`’s
interface and its output, while the unit tests are likely more focused
on the inner workings of `b` and `c`. They’re more zoomed-in, testing
lines of code in finer detail.

Both cases “cover the code with tests”, but in different ways and with
different emphases. The tests aren’t equal, so one “coverage score”
doesn’t make sense.

Another issue is that the project’s code coverage metric can easily be
increased by writing a
[zero-assertion](https://stackoverflow.com/questions/137399/unit-testing-without-assertions)
test case like the example at the start of this article.

  - An assertion-free test is like a tourist on an open-top bus, riding
	past the code at high speed, more concerned with his thermos of hot
	chocolate than with the sights whizzing past.
  - A test that does its job is more like a building inspector, checking
	each tourist attraction meticulously to verify that it isn’t about
	to fall down.

In other words…

> There’s code coverage and then there’s ***CODE COVERAGE***

So an overall percentage score is almost certainly misleading.

## Why Use Code Coverage

Here, are some prime reasons for using code coverage:

  - It helps you to measure the efficiency of test implementation
  - It offers a quantitative measurement.
  - It defines the degree to which the source code has been tested.

## Code Coverage Methods

### Statement Coverage

What is Statement Coverage?

Statement coverage is a white box test design technique which involves
execution of all the executable statements in the source code at least
once. It is used to calculate and measure the number of statements in
the source code which can be executed given the requirements.

Statement coverage is used to derive scenario based upon the structure
of the code under test.

<kbd>![](https://www.guru99.com/images/jsp/030116_0814_LearnStatem1.png)</kbd>

In [White Box Testing](https://www.guru99.com/white-box-testing.html),
the tester is concentrating on how the software works. In other words,
the tester will be concentrating on the internal working of source code
concerning control flow graphs or flow charts.

Generally in any software, if we look at the source code, there will be
a wide variety of elements like operators, functions, looping,
exceptional handlers, etc. Based on the input to the program, some of
the code statements may not be executed. The goal of Statement coverage
is to cover all the possible path's, line, and statement in the code.

Let's understand this with an example, how to calculate statement
coverage.

Scenario to calculate Statement Coverage for given source code. Here we
are taking two different scenarios to check the percentage of statement
coverage for each scenario.

**Example**

##### Source Code **  
**

>     Prints (int a, int b) {                       ------------  Printsum is a function 
>         int result = a+ b; 
>         If (result> 0)
>             Print ("Positive", result)
>         Else
>             Print ("Negative", result)
>         }

##### Scenario 1

If A = 3, B = 9

<kbd>![](https://www.guru99.com/images/1/102518_1122_CodeCoverag2.png)</kbd>

The statements marked in yellow color are those which are executed as
per the scenario

Number of executed statements = 5, Total number of statements = 7

Statement Coverage: 5/7 = 71%

<kbd>![](https://www.guru99.com/images/jsp/030116_0814_LearnStatem2.png)</kbd>

##### Scenario 2

If A = -3, B = -9

<kbd>![](https://www.guru99.com/images/1/102518_1122_CodeCoverag4.png)</kbd>

The statements marked in yellow color are those which are executed as
per the scenario.

Number of executed statements = 6

Total number of statements = 7

<kbd>![](https://www.guru99.com/images/jsp/030116_0814_LearnStatem6.png)</kbd>

Statement Coverage: 6/7 = 85%

<kbd>![](https://www.guru99.com/images/jsp/030116_0814_LearnStatem3.png)</kbd>

But overall if you see, all the statements are being covered by 2
<sup>nd</sup> scenario's considered. So we can conclude that overall
statement coverage is 100%.

<kbd>![](https://www.guru99.com/images/jsp/030116_0814_LearnStatem4.png)</kbd>

### Decision Coverage

Decision coverage reports the true or false outcomes of each Boolean
expression. In this coverage, expressions can sometimes get complicated.
Therefore, it is very hard to achieve 100% coverage.

That's why there are many different methods of reporting this metric.
All these methods focus on covering the most important combinations. It
is very much similar to decision coverage, but it offers better
sensitivity to control flow.

<kbd>![](https://www.guru99.com/images/1/102518_1122_CodeCoverag12.jpg)</kbd>

**Example**

##### Source Code

>     Demo(int a) {
>          If (a> 5)
>             a=a*3
>          Print (a)
>         }

##### Scenario 1

Value of a is 2

<kbd>![](https://www.guru99.com/images/1/102518_1122_CodeCoverag8.png)</kbd>

The code highlighted in yellow will be executed. Here the "No" outcome
of the decision If (a\>5) is checked.

Decision Coverage = 50%

##### Scenario 2

Value of a is 6

<kbd>![](https://www.guru99.com/images/1/102518_1122_CodeCoverag9.png)</kbd>

The code highlighted in yellow will be executed. Here the "Yes" outcome of the decision If (a\>5) is checked.

Decision Coverage = 50%

<table>
	<thead>
		<tr>
			<th>Test Case</th>
			<th>Value of A</th>
			<th>Output</th>
			<th>Decision Coverage</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>1</td>
			<td>2</td>
			<td>2</td>
			<td>50%</td>
		</tr>
		<tr>
			<td>2</td>
			<td>6</td>
			<td>18</td>
			<td>50%</td>
		</tr>
	</tbody>
</table>


### Branch Coverage

In the branch coverage, every outcome from a code module is tested. For
example, if the outcomes are binary, you need to test both True and
False outcomes.

It helps you to ensure that every possible branch from each decision
condition is executed at least a single time.

By using Branch coverage method, you can also measure the fraction of
independent code segments. It also helps you to find out which is
sections of code don't have any branches.

The formula to calculate Branch Coverage:

<kbd>![](https://www.guru99.com/images/1/102518_1122_CodeCoverag13.jpg)</kbd>

**Example**

##### Source Code

>     Demo(int a) {
>          If (a> 5)
>             a=a*3
>          Print (a)
>         }

<kbd>![](https://www.guru99.com/images/1/102518_1122_CodeCoverag10.png)</kbd>

Branch Coverage will consider unconditional branch as well

<table>
	<thead>
		<tr>
			<th>Test Case</th>
			<th>Value of A</th>
			<th>Output</th>
			<th>Decision Coverage</th>
			<th>Branch Coverage</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>1</td>
			<td>2</td>
			<td>2</td>
			<td>50%</td>
			<td>
				<strong>33%</strong>
			</td>
		</tr>
		<tr>
			<td>2</td>
			<td>6</td>
			<td>18</td>
			<td>50%</td>
			<td>
				<strong>67%</strong>
			</td>
		</tr>
	</tbody>
</table>


#### Advantages of Branch coverage:

Branch coverage Testing offers the following advantages:

  - Allows you to validate-all the branches in the code
  - Helps you to ensure that no branched lead to any abnormality of the
	program's operation
  - Branch coverage method removes issues which happen because of
	statement coverage testing
  - Allows you to find those areas which are not tested by other testing
	methods
  - It allows you to find a quantitative measure of code coverage
  - Branch coverage ignores branches inside the Boolean expressions

### Condition Coverage

Conditional coverage or expression coverage will reveal how the
variables or sub expressions in the conditional statement are evaluated.
In this coverage expressions with logical operands are only considered.

For example, if an expression has Boolean operations like AND, OR, XOR,
which indicated total possibilities.

Conditional coverage offers better sensitivity to the control flow than
decision coverage. Condition coverage does not give a guarantee about
full decision coverage

The formula to calculate Condition Coverage:

<kbd>![](https://www.guru99.com/images/1/102518_1122_CodeCoverag14.jpg)</kbd>

**Example**

<kbd>![](https://www.guru99.com/images/1/102518_1122_CodeCoverag11.png)</kbd>

For the above expression, we have 4 possible combinations

  - TT
  - FF
  - TF
  - FT

Consider the following input

X=3

Y=4

(x\<y)

TRUE

Condition Coverage is ¼ = 25%

A=3

B=4

(a\>b)

FALSE

### Finite State Machine (FSM) Coverage

Finite state machine coverage is certainly the most complex type of code
coverage method. This is because it works on the behavior of the design.
In this coverage method, you need to look for how many time-specific
states are visited, transited. It also checks how many sequences are
included in a finite state machine.

## Which Type of Code Coverage to Choose

This is certainly the most difficult answer to give. In order to select
a coverage method, the tester needs to check that the

  - code under test has single or multiple undiscovered defects
  - cost of the potential penalty
  - cost of lost reputation
  - cost of lost sale, etc.

The higher the probability that defects will cause costly production
failures, the more severe the level of coverage you need to choose.

## Code Coverage vs. Functional Coverage

<table>
	<thead>
		<tr>
			<th>
				<strong>Code Coverage</strong>
			</th>
			<th>
				<strong>Functional Coverage</strong>
			</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Code coverage tells you how well the source code has been exercised by your test bench.</td>
			<td>Functional coverage measures how well the functionality of the design has been covered by your test bench.</td>
		</tr>
		<tr>
			<td>Never use a design specification</td>
			<td>Use design specification</td>
		</tr>
		<tr>
			<td>Done by developers</td>
			<td>Done by Testers</td>
		</tr>
	</tbody>
</table>


## Advantages of Using Code Coverage

  - Helpful to evaluate a quantitative measure of code coverage
  - It allows you to create extra test cases to increase coverage
  - It allows you to find the areas of a program which is not exercised
	by a set of test cases

## Disadvantages of Using Code Coverage

  - Even when any specific feature is not implemented in design, code
	coverage still report 100% coverage.
  - It is not possible to determine whether we tested all possible
	values of a feature with the help of code coverage
  - Code coverage is also not telling how much and how well you have
	covered your logic
  - In the case when the specified function hasn't implemented, or a not
	included from the specification, then structure-based techniques
	cannot find that issue.

