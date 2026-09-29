# QA Learning Log

## August 23, 2026

### What I learned

Today I learned the fundamentals of Manual QA:

* QA vs Software Testing
* SDLC
* STLC
* Test Scenarios
* Test Cases
* Bug Lifecycle
* Severity vs Priority
* Functional vs Non-functional Testing
* Smoke Testing
* Sanity Testing
* Regression Testing
* Exploratory Testing
* Agile/Scrum and how QA works in a development team

### What clicked for me

I understood that testing isn't just about finding bugs.

A QA tester needs to understand what the software is supposed to do, think about what could go wrong, design tests, communicate defects clearly, and work with the rest of the team.

### What I practiced

I created login test cases and started thinking about positive, negative, and boundary scenarios.

### What I still need to understand

* Test design techniques
* Equivalence partitioning
* Boundary value analysis
* Decision tables
* State transition testing

### Next

Learn and practice test design techniques.

## August 31, 2026

### What I learned

Today I learned the fundamentals of Test Design:

* Why test design techniques are important
* Equivalence Partitioning (EP)
* Boundary Value Analysis (BVA)
* Decision Table Testing
* State Transition Testing
* Error Guessing
* Positive and Negative Testing

### What clicked for me

I understood that good testing isn't about randomly trying inputs.

Test design techniques help me decide what to test and why.

Instead of testing every possible input, I can identify representative test cases that give me better coverage with less unnecessary effort.

I also learned that different requirements call for different techniques:

* EP => divide inputs into valid and invalid groups
* BVA => focus on values around boundaries
* Decision Tables => test combinations of conditions and business rules
* State Transition => test how the system behaves when moving between states
* Error Guessing => use experience and intuition to predict likely failures
* Positive/Negative Testing => verify both expected and invalid behavior

### What I practiced

I practiced applying test design techniques to real requirements.

For example:

* Used EP + BVA for a product quantity range.
* Used a Decision Table for checkout conditions.
* Used State Transition Testing for payment states.
* Used Positive and Negative Testing for input validation.
* Thought about edge cases such as maximum order limits and actions that should not be allowed after an order reaches a certain state.

### What I still need to understand

* Writing professional test cases
* Choosing the right test cases from my test designs
* Test data
* Preconditions and postconditions
* Expected vs. actual results
* Test execution

### Next

Move from designing tests to writing and executing professional test cases.

## September 21, 2026

### What I learned

Today I started learning **Test Execution & Documentation**.

I learned about:

* Writing professional test cases
* Test case structure
* Test scenarios vs. test cases
* Test data
* Preconditions and postconditions
* Expected vs. actual results
* Test execution
* Test statuses: Pass, Fail, Blocked, and Not Run
* Bug reporting
* Test execution reports
* Test summary reports
* Requirements Traceability Matrix (RTM)

### What clicked for me

I understood that writing a test case is only part of the testing process.

A QA tester also needs to **execute the test, record what actually happened, compare it with the expected result, and document any differences clearly**.

I also understood the difference between a test scenario and a test case:

* A **test scenario** describes what needs to be tested at a high level.
* A **test case** describes how to test it in detail.

Test documentation makes testing **repeatable, measurable, and easier for the team to understand**.

### What I practiced

I practiced writing professional test cases with:

* Test case IDs
* Test case descriptions
* Preconditions
* Test data
* Test steps
* Expected results
* Actual results
* Test status

I also practiced executing test cases and recording whether they **Passed, Failed, were Blocked, or were Not Run**.

I created test scenarios and test cases for features such as:

* User Login
* Product Search

I also practiced documenting bugs found during test execution and linking them back to the relevant test cases and requirements.

### What I still need to understand

* Writing clear and reproducible bug reports
* Test execution and summary reports
* Requirements Traceability Matrix (RTM)
* How to organize test documentation for a real QA project
* How all these documents fit together during a testing cycle

### Next

Complete a practical QA project by creating and executing test documentation for a real-world application.

