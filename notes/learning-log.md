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
* Agile/Scrum

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
