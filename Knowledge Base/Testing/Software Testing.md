# Goals

### _Validate that the software meets its goals
### _Search for defects that can be fixed to improve software quality
### _Facilitate refactoring and upgrades by validating that everything is still working after

### Types of Testing

#### _Unit testing, integration testing, smoke testing
#### _Functional testing
#### _Non-regression testing
#### _Acceptance testing
#### _Code Quality and Static Analysis
#### _Performance and Security Testing
#### _Report test results

### Automated

- Tests can be run frequently
- Tests should be independent from each other as much as possible
- Tests can be run in parallel
- Tests can be run in the same order
- Consume machine resources but little human time except to review
- the results of tests that fail
- Running tests frequently means that problems are found early and you usually know what small piece of code caused the problem
- Define different tests to run at different stages of the build chain

### Fastest

- unit tests — test a small piece of code (a function or method or command);
- run blazingly fast, and are often written by the person who wrote the code
- integration tests — validate integration between multiple sub-systems,
- including external sub-systems like a database
- smoke tests — validates basic functions of the system; also known as sanity checking

### Slower

- functional tests — validate the normal software behaviors against
the expectations and requirements
- non-regression tests — validates that the system still produces the same result
- acceptance tests — tests the full product from the perspective of
the end-user use cases and feelings. Probably includes _manual _testing

_Manual

- Is appropriate when test result is subjective, such as user experience testing
- May also be used when the cost of automation is excessive for some reason
- Should be performed rarely, and only on software that has passed all automated tests

### Testing Priority Levels

Tests at the _bottom run quickly and inexpensively and should be run very frequently
Tests at the _top take more time to run and are expensive; they should be run less frequently and only on software that has passed the tests lower on the pyramid.

| 1)  Manual                |
| 2)  Acceptance            |
| 3)  Non Regression        |
| 4)  Functional            |
| 5)  Smoke                 |
| 6)  Integration           |
| 7)  Unit                  |

*The Testing Portfolio*
Should have more low-level tests than high-level tests
[!] When low-level tests fail, it rarely makes sense to run higher-level tests
before fixing the problems detected by the low-level tests [!]
When a higher level test fails, consider that it detected a defect in the
lower-level tests as well as a defect in the code.

## Why is it important to test?

- Unit tests usually run every time you compile the code
- You can define whether functional and non-regression tests run if the unit tests fail
- Large, broad tests can be set up to run periodically, perhaps during non-work hours, rather than being run each time new code is committed

*Jenkins enables you to run large numbers of tests frequently and at appropriate stages in the build cycle

## Sources:

http://martinfowler.com/bliki/UnitTest.html
http://stackoverflow.com/questions/520064/what-is-unit-test-integration-test-smoke-test-regression-test
https://en.wikipedia.org/wiki/Software_testing
http://martinfowler.com/tags/testing.html
http://martinfowler.com/bliki/TestCoverage.html
http://martinfowler.com/bliki/TestDrivenDevelopment.html
https://adamcod.es/2014/05/15/test-doubles-mock-vs-stub.html

