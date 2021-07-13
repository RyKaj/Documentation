###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [Software Development](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/README.md) | [Unit Test](https://github.com/RyKaj/Documentation/tree/master/SoftwareDevelopment/UnitTest/README.md) |
------------

# Information Technology : Test-Driven Development (TDD)

A process for when you write and run your tests. Following it makes it
possible to have a very high test-coverage. Test-coverage refers to the
percentage of your code that is tested automatically, so a higher number
is better. TDD also reduces the likelihood of having bugs in your tests,
which can otherwise be difficult to track down.

The TDD process consists of the following steps:

  - Tests are written before the code
  - Rely heavily on testing frameworks
  - All classes in the applications are tested
  - Quick and easy integration is made possible

It can take some effort to learn well, but spending the time can pay off
big. TDD projects often get a code-coverage of 90-100%, which means
maintaining the code and adding new features is easy. This is because
you have a large set of tests, so you can trust your code and changes
work, and didn’t break any other code either.

<kbd>![](attachments/463529105.jpg)</kbd>

**Writing Efficient Code for your Unit Tests**

<kbd>![](attachments/infographic.jpg)</kbd>

**Red Stage**: When there is a need to develop a unit of functionality, we need to break the development process into smaller tasks. Here are the steps that have to be performed in the Red Stage:
- Define the software functionalities into smaller units in order to break down the development unit into minute features.
- Create a test for the task and write tests so that the developer focuses on the implementation of the features. Keep the test design super simple and super minimalistic.
- Run all the tests and check whether the newly created test scenarios fail. This is required to test the newly implemented features in the product.

**Green Stage**: In the Green Stage, we produce the code for small units of tests created in the Red Stage. Here are the major steps performed in this stage:
- Write short and simple code for the previously defined test case(s).
- Test the features by running the tests and verify whether they pass (or fail).
- Run all the test cases again and make sure that all of them pass.

**Refactor Stage**: Refactor Stage is used to keep all the tests workable. This is ensured by:
- Refactoring the code by removing all the issues, thereby ensuring that all the tests are workable.
- Improving the test code without adding any new code to test further functionalities.


## The First Principle

F.I.R.S.T principles for clean tests

  - **Fast**: The best tests are fast enough. If tests run slowly, you’ll
	probably be discouraged from running them frequently.
  - **Independent**: Always strive to avoid test interdependence. At no
	time should a test depend on the state of preceding tests. This
	allows you to run tests individually, which is great for debugging
	in the event of a test break.
  - **Repeatable:**: Ideally, every test should be repeatable in different
	environments without being erroneous. If the tests do not rely on a
	database or network, then it should work in any environment as it
	only depends on the code to be tested. When such a test works in one
	environment and fails in another, then chances are the test or the
	method is set up wrongly.
  - **Self-validating:**: Each test should have a single Boolean output-
	either a pass or a fail. You do not have to check through the log
	files to identify whether the test result was valid or not.
  - **Timely:**: Unit tests should be created in a timely manner. In TDD,
	the ideal time for creating test code is before writing the
	production code.

## Each Test should have its own function

If you want to run multiple tests, for example, each test should have
its own function. This is where the one test-one function notion comes
into play. Consider the anatomy of this simple test:

<kbd>![](attachments/463530531.png)</kbd>

Lumping the two tests together is confusing because you’re not sure
whether the output from test one affects test two. Secondly, the
starting state of test two is not explicit. The test runs regardless of
the state test one finishes. There’s so much ambiguity to think about.
Now think of a situation where you lumped about 10 items in a single
test and something went wrong. It will be hard to identify which of the
10 items failed.

To fix this, we can set up two functions for each test as shown below

In this test, we have an explicit starting state for test B. Notice how
this makes the tests easier to read and analyze.

<kbd>![](attachments/463530532.png)</kbd>

**Myths and Facts**

<table>
	<colgroup>
		<col style="width: 50%" />
		<col style="width: 50%" />
	</colgroup>
	<tbody>
		<tr class="odd">
			<td>
				<p>
					<strong>Myths</strong>
				</p>
			</td>
			<td>
				<p>
					<strong>Facts</strong>
				</p>
			</td>
		</tr>
		<tr class="even">
			<td>
				<p>Test Driven Development Slows Teams Down</p>
			</td>
			<td>
				<p>t’s true that when you first start using TDD, you’ll go slower than if you didn’t — but that’s only transactionally and temporarily true. Think of it this way; if I develop a feature in 1 hour, but spend 6 hours debugging it, that’s worse than spending 6 hours developing the feature through TDD, and 0 hours debugging it. Once that feature written through TDD gets to test; I am  
					<em>confident</em> in it. I’m not as confident (or really confident at all) that the tester won’t find an issue if I hadn’t built the tests first. After six hours of debugging, it’s quite likely I missed something, I’m too far into the weeds to realize it, but a fresh set of eyes (our friendly neighborhood QA) will likely find it.
				</p>
				<p>Babies crawl before they walk, and they walk before they run; but no one ever suggests babies should start out running — there’s too many fundamentals that get missed if you try that.</p>
				<p>Another reality is that we all take it for granted that ‘hardening’ and ‘bug fixing’ sprints occur; and they occur far too often, by necessity. What you may not realize is that  
					<em>that time counts against development too</em>. It’s an opportunity cost — if you have to spend entire sprints “hardening” or “bug fixing”, then you aren’t able to spend those sprints delivering features and value — you’re effectively shoring up the value you’ve already tried to create.
				</p>
				<p>Instead of doing that, why  
					<em>not</em> build the feature through TDD?
				</p>
			</td>
		</tr>
		<tr class="odd">
			<td>
				<p>Test driven Development is a Testing methodology</p>
			</td>
			<td>
				<p>TDD is a  
					<em>development</em> methodology. It’s a way to develop software to achieve the following:
				</p>
				<ul>
					<li>Code that is designed to be testable</li>
					<li>Well understood code</li>
					<li>Well specified code</li>
					<li>easy to change code</li>
					<li>consistent and constant delivery</li>
				</ul>
				<p>The fact that there are tests is almost an accident of speech. When Test Driven Development was created, tests were the primary way to assert that behavior was a certain way; but we could have easily called it ‘example driven development’. TDD’s purpose is not to create tests; it’s to create code that’s easy to test and easy to change, and allow the creators to be confident  
					<em>when changing the code</em>.
				</p>
				<p>It is not a replacement for the normal QA process; and not a replacement for system based tests —  
					<em>though it can cut down drastically on the number of paths integration tests need to take to be useful</em>. This is especially true of the brand of TDD I teach: FauxO
					<br />
					<br />
					Test Driven Development ensures teams of humans can work together to deliver better software, faster than if they hadn’t used TDD.
				</p>
			</td>
		</tr>
		<tr class="even">
			<td>
				<p>Unit Tests are a Development Methodology</p>
			</td>
			<td>
				<p>Unit tests are a  
					<em>testing methodology</em>
					<strong>
						<em>, </em>
					</strong> not a  
					<em>development</em> methodology. The difference is subtle but important. You don’t create Unit tests to determine the path software ought to take; you create unit tests after the software is created to verify it does what you think it does — to double check your work.
				</p>
				<p>TDD, on the other hand, is a development methodology. it’s a way of developing software that puts the test first; and the implementation later. This allows you to specify the behavior you expect, before the behavior itself is written. Unit Testing takes the opposite approach; where the tests are written after the code.</p>
				<p>The reality is when you create the Unit Tests  
					<em>after</em> the code is written, the tests are more brittle and necessarily dependent upon all of the dependencies needed to run those tests.
				</p>
				<p>Unit Tests have their place — though I (and others) argue they should be shown the door in favor of good TDD practices and integration tests that don’t have to traverse every path through the application.</p>
			</td>
		</tr>
		<tr class="odd">
			<td>
				<p>Integration Tests + Unit Tests are Good Enough</p>
			</td>
			<td>
				<p>If you develop code with unit tests and integration tests, you’ll run into two problems pretty often:</p>
				<ol>
					<li>Your Integration tests necessarily have to cover lots of different paths through the application if your application wasn’t developed through TDD. This is untenable. JB Rainsberger famously said  
						<a href="https://www.youtube.com/watch?v=VDfX44fZoMc">Integration Tests are a Scam</a>, and it’s partly because of how we write code.
					</li>
					<li>Your Unit tests (again, without developing them through TDD), are bound to the implementation and dealing with all the dependencies you created because the pain of adding a dependency wasn’t apparent until you tried to write unit tests after the fact. That means if your implementation changes or your caller changes, your test could very well fail, even though nothing of substance changed. A common smell that this is the case is extensive use of Mocks and Stubs.</li>
				</ol>
				<p>In reality, Integration Tests + Unit tests are treated as good enough, when together, they’re about the most painful way you can test and develop software. (I believe in Integration tests — but they should be spared from having to go through the thousands of codepaths – that should be able to be handled through code that’s been developed through TDD.</p>
			</td>
		</tr>
		<tr class="even">
			<td>
				<p>The Goal of TDD is 100% test coverage</p>
			</td>
			<td>
				<p>This is another one of those instances where ‘test’ was an unfortunate characterization for TDD. If some TDD is good, and more is better, why not go with the most TDD? 100%?</p>
				<p>Besides being infeasible (Frameworks and the icky-real world structures like the Network, Disk, Databases and the system clock get in the way), there is a point of diminishing returns; and those returns hit right about the time you try to deal with the Network, Disk, Databases, and the System Clock in an extensive fashion. This is why “Outside-In” TDD comes across as a brittle to change -&gt; The Mocks and Stubs replace real-world implementations; and we frequently find ourselves wanting to change those implementations.</p>
				<p>Also, since TDD is a development methodology, it’s not trying to be a testing methodology — that’s a useful by-product of TDD, but it isn’t  
					<em>the goal</em>. The goal is code that is built to be easily changeable, well-understood, and its behavior specified.
				</p>
			</td>
		</tr>
		<tr class="odd">
			<td>
				<p>You should aspire for 100% test coverage</p>
			</td>
			<td>
				<p>The reality is if you work with very expensive equipment, the value of 100% test coverage outweighs its cost. If your software deals with safety or security, that’s also true. If you’re writing a banking back-end — that is very likely true; but for the rest of us; you want enough test-coverage that you’re confident in making changes; but not so much that the tests get in your way of making change (again, brittle tests make code hard to change).</p>
			</td>
		</tr>
		<tr class="even">
			<td></td>
			<td></td>
		</tr>
	</tbody>
</table>

**Pros and Cons of Behavior-Driven Development (BDD)**
<table>
	<colgroup>
		<col style="width: 50%" />
		<col style="width: 50%" />
	</colgroup>
	<tbody>
		<tr class="odd">
			<td>
				<p>
					<strong>Advantages</strong>
				</p>
			</td>
			<td>
				<p>
					<strong>Disadvantages</strong>
				</p>
			</td>
		</tr>			
		<tr class="even">
			<td>
				<p>
					<strong>Reduced cost of Development</strong> 
					The development process in TDD is divided into smaller chunks to simplify the detection of issues at the early stages of design and development.
				</p>
			</td>
			<td>
				<p>
					<strong>Bugs leading to faulty code: </strong>
					Tests could contain bugs which in turn results in faulty implementation. This can be averted by using the right BDD framework, performing detailed code review, and more.
				</p>
			</td>
		</tr>
		<tr class="odd">
			<td>
				<p>
					<strong>Focus on design and architecture: </strong> 
					Writing tests before the implementation makes the development process more seamless and efficient.
				</p>
			</td>
			<td>
				<p>
					<strong>Costly Architectural mistakes:</strong>
					If the generated test code is not in line with the desired architecture, it could result in huge losses.
				</p>
			</td>
		</tr>
		<tr class="even">
			<td>
				<p>
					<strong>Improved Code Coverage:</strong> 
					Through TDD, a well-designed system can achieve 100 percent code coverage.
				</p>
			</td>
			<td>
				<p>
					<strong>Slowness in development:</strong>
					Creating test cases before code development slows product development. In addition, framing test cases may take a huge time as the actual implementation is not available at that time.
				</p>
			</td>
		</tr>
		<tr class="odd">
			<td>
				<p>
					<strong>Code visibility:</strong> 
					Tests are written to verify smaller functionalities, making it easy to refactor and maintain the code.
				</p>
			</td>
			<td>
				<p>
					<strong>Requires prior experience:</strong>
					Prior experience with TDD is a must since many teams commit the mistake of not running tests at the Red Stage.
				</p>
			</td>
		</tr>
		<tr class="even">
			<td>
				<p>
					<strong>Detailed Documentation:</strong> 
					Since tests are written for verifying micro-level functionalities, writing documentation becomes an easy task.
				</p>
			</td>
			<td>
			</td>
		</tr>
	</tbody>
</table>