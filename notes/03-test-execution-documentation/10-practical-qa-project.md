# Practical QA Project

This practical project brings together the skills learned throughout **Level 1 — Manual QA Fundamentals**, **Level 2 — Test Design**, and **Level 3 — Test Execution & Documentation**.

The goal is to practice a realistic QA workflow from understanding requirements through test planning, test design, execution, defect reporting, and test reporting.

We will use an **e-commerce web application** called **Easy Buy** as our practice project.

---

# 1. Project Overview

### Project

**Easy Buy — E-commerce Web Application**

### Objective

Test the core functionality of an e-commerce application and identify defects before release.

The application allows users to:

* Register
* Log in
* Search for products
* View products
* Add products to a cart
* Update cart quantities
* Remove products
* Proceed to checkout
* Place orders
* View order history

The project focuses on practicing the QA process rather than testing every possible feature of a production e-commerce system.

---

# 2. QA Workflow

Throughout this project, we will follow this workflow:

```text
Requirements
     ↓
Test Plan
     ↓
Test Scenarios
     ↓
Test Cases
     ↓
Test Data
     ↓
Test Execution
     ↓
Pass / Fail / Blocked / Not Run
     ↓
Bug Reports
     ↓
Retesting
     ↓
Regression Testing
     ↓
Test Summary Report
     ↓
RTM
```

This is the workflow we have been learning throughout Level 3.

---

# 3. Project Requirements

We will use the following requirements.

## Login Requirements

### R1 — Valid Login

A registered user who enters a valid email address and correct password should be successfully logged in and redirected to the dashboard.

### R2 — Email Validation

The email field is required and must contain a valid email format.

### R3 — Password Validation

The password field is required and must contain at least 8 characters.

### R4 — Invalid Credentials

A user who enters invalid credentials should not be authenticated and should receive an appropriate error message.

---

# 4. Product Search Requirements

### R5 — Valid Search

When a user searches using a keyword, products matching the keyword should be displayed.

### R6 — No Search Results

When no products match the search keyword, the system should display an appropriate "No results" message.

### R7 — Empty Search

Submitting an empty search should not cause a system error.

---

# 5. Cart Requirements

### R8 — Add Product

A user should be able to add an available product to the shopping cart.

### R9 — Update Quantity

A user should be able to increase or decrease the quantity of a product in the cart.

### R10 — Remove Product

A user should be able to remove a product from the cart.

### R11 — Cart Total

The cart total should accurately reflect the prices and quantities of the products in the cart.

---

# 6. Checkout Requirements

### R12 — Proceed to Checkout

A user with at least one product in the cart should be able to proceed to checkout.

### R13 — Required Delivery Information

Required delivery information must be provided before an order can be placed.

### R14 — Valid Checkout

A user who provides valid checkout information should be able to place an order.

### R15 — Empty Cart Checkout

A user should not be able to proceed to checkout when the cart is empty.

---

# 7. Testing Scope

## In Scope

The project will cover:

### User Authentication

* Login
* Email validation
* Password validation
* Invalid credentials

### Product Search

* Valid searches
* No-result searches
* Empty searches
* Exploratory search conditions

### Shopping Cart

* Adding products
* Quantity changes
* Removing products
* Cart totals

### Checkout

* Checkout access
* Delivery information validation
* Order placement
* Empty-cart behavior

---

# 8. Out of Scope

The following areas are outside the current project scope:

* Password reset
* Payment gateway integration
* Actual payment processing
* Delivery processing
* Third-party logistics
* Email delivery
* SMS notifications

Out-of-scope features may be mentioned during exploratory testing if encountered, but they will not be part of the planned test coverage.

---

# 9. Testing Types

We will practice several testing types during this project.

## Functional Testing

Verify that application functionality behaves according to requirements.

Example:

> Verify that a user can add a product to the cart.

---

## Regression Testing

After changes or fixes, verify that previously working functionality still works.

Example:

> After fixing login, execute related login tests again.

---

## Exploratory Testing

Explore the application beyond the predefined test cases to discover unexpected behavior.

Example:

> Enter unusual search inputs and observe how the application responds.

---

## Negative Testing

Verify that the system handles invalid inputs and actions appropriately.

Example:

> Attempt to log in with an incorrect password.

---

## Smoke Testing

Perform a small set of critical tests to determine whether the application is stable enough for further testing.

Example:

```text
Open application
     ↓
Login
     ↓
Search product
     ↓
Add product to cart
     ↓
Open checkout
```

---

## Usability Testing

Observe whether the application is understandable and easy to use.

Example:

* Are error messages understandable?
* Are important buttons easy to find?
* Is navigation clear?

---

## Compatibility Testing

Verify behavior across supported environments.

For this project, examples include:

* Chrome
* Firefox
* Desktop
* Android

---

# 10. Test Design Techniques

We will apply the techniques learned in Level 2.

## Equivalence Partitioning

Divide input values into groups that are expected to behave similarly.

Example:

Password minimum length:

```text
Invalid:
< 8 characters

Valid:
≥ 8 characters
```

---

## Boundary Value Analysis

Test values around boundaries.

For the 8-character minimum:

```text
7 characters → Invalid
8 characters → Valid
9 characters → Valid
```

---

## Decision Table Testing

Useful when multiple conditions determine an outcome.

Example:

Checkout:

| Cart           | Delivery Information | Expected             |
| -------------- | -------------------- | -------------------- |
| Empty          | Valid                | Checkout unavailable |
| Product exists | Missing              | Validation message   |
| Product exists | Valid                | Order can be placed  |

---

## State Transition Testing

Useful for features whose behavior changes based on state.

Example:

```text
Cart Empty
    ↓
Add Product
    ↓
Cart Contains Product
    ↓
Remove Product
    ↓
Cart Empty
```

---

## Error Guessing

Use experience and common failure patterns to identify additional tests.

Examples:

* Empty values
* Special characters
* Very long input
* Unexpected input types
* Repeated clicks
* Rapid actions
* Invalid combinations

---

## Positive Testing

Verify that valid inputs produce the expected successful behavior.

Example:

> Log in using valid credentials.

---

## Negative Testing

Verify that invalid inputs or actions are handled correctly.

Example:

> Log in using an incorrect password.

---

# 11. Test Scenarios

We will begin by identifying high-level scenarios.

## Login

```text
TS_LOGIN_001
Verify that a registered user can log in with valid credentials.

TS_LOGIN_002
Verify that the system validates the email field.

TS_LOGIN_003
Verify that the system validates the password minimum length.

TS_LOGIN_004
Verify that a user cannot log in with invalid credentials.
```

---

## Product Search

```text
TS_SEARCH_001
Verify that products can be searched using a valid keyword.

TS_SEARCH_002
Verify that an appropriate message is displayed when no products match the search.

TS_SEARCH_003
Verify that submitting an empty search does not cause a system error.

TS_SEARCH_004
Explore how search handles special-character input.

TS_SEARCH_005
Explore how search handles numbers-only input.
```

The first three are directly tied to documented requirements.

The last two are exploratory/error-guessing scenarios because the current requirements do not explicitly define those behaviors.

---

## Cart

Example scenarios:

```text
TS_CART_001
Verify that a user can add a product to the cart.

TS_CART_002
Verify that a user can increase and decrease product quantity.

TS_CART_003
Verify that a user can remove a product from the cart.

TS_CART_004
Verify that the cart total is calculated correctly.
```

---

## Checkout

Example scenarios:

```text
TS_CHECKOUT_001
Verify that a user can proceed to checkout when the cart contains a product.

TS_CHECKOUT_002
Verify that required delivery information is validated.

TS_CHECKOUT_003
Verify that a user can place an order with valid checkout information.

TS_CHECKOUT_004
Verify that a user cannot proceed to checkout with an empty cart.
```

---

# 12. Test Case Design

Each scenario will be broken down into detailed test cases.

For example:

### Scenario

```text
TS_LOGIN_003
Verify that the system validates the password minimum length.
```

We can apply Boundary Value Analysis.

Requirement:

> Password must contain at least 8 characters.

Test cases:

```text
TC_LOGIN_008 → 7 characters
TC_LOGIN_009 → 8 characters
TC_LOGIN_010 → 9 characters
```

This demonstrates the relationship between:

```text
Requirement
     ↓
Scenario
     ↓
Test Design Technique
     ↓
Test Cases
```

---

# 13. Test Case Structure

Our test cases will use the structure learned in Level 3:

```text
Test Case ID
Title
Requirement
Priority
Precondition
Test Data
Steps
Expected Result
Actual Result
Status
Postcondition
Notes
```

Example:

```text
Test Case ID:
TC_LOGIN_001

Title:
Verify that a registered user can log in with valid credentials.

Requirement:
R1

Priority:
High

Precondition:
A registered user account exists.

Test Data:
Email: user1@test.com
Password: <test account password>

Steps:
1. Open the Login page.
2. Enter the registered email.
3. Enter the correct password.
4. Click Login.

Expected Result:
The user is successfully logged in and redirected to the dashboard.

Actual Result:
-

Status:
Not Run

Postcondition:
The user is logged in.

Notes:
-
```

---

# 14. Test Execution

After writing the test cases, we execute them.

During execution:

```text
Test Case
    ↓
Prepare Data
    ↓
Execute Steps
    ↓
Observe Application
    ↓
Record Actual Result
    ↓
Compare Expected vs Actual
    ↓
Assign Status
```

Possible statuses:

```text
Pass
Fail
Blocked
Not Run
```

---

# 15. Example Execution

Suppose we execute:

```text
TC_LOGIN_001
```

Expected:

> User is successfully logged in and redirected to the dashboard.

Actual:

> User is successfully logged in and redirected to the dashboard.

Therefore:

```text
Status:
Pass
```

If the application instead displays an authentication error:

```text
Actual:
The system displays "Invalid email or password"
and keeps the user on the Login page.

Status:
Fail
```

The failure should then be investigated.

---

# 16. Defect Reporting

When a failed test is confirmed to be a software defect, we create a bug report.

Example:

```text
BUG-LOGIN-001

Title:
Login rejects valid credentials and keeps the registered user on the Login page.

Expected:
The user is logged in and redirected to the dashboard.

Actual:
The system displays "Invalid email or password" and keeps the user on the Login page.

Related Test Case:
TC_LOGIN_001
```

The defect should contain enough information for another person to reproduce the issue.

---

# 17. Bug Lifecycle

We will practice a simplified defect lifecycle:

```text
New
 ↓
Assigned
 ↓
In Progress
 ↓
Fixed
 ↓
Ready for Retest
 ↓
Retest
 ↓
Verified
 ↓
Closed
```

Possible alternative states include:

```text
Rejected
Duplicate
Deferred
Reopened
Cannot Reproduce
```

The exact workflow depends on the project.

---

# 18. Retesting

When a developer fixes a confirmed defect, QA retests the original failing scenario.

Example:

```text
BUG-LOGIN-001
       ↓
Developer Fix
       ↓
TC_LOGIN_001
       ↓
Retest
```

If the issue is fixed:

```text
Expected = Actual
      ↓
Pass
```

If the problem remains:

```text
Expected ≠ Actual
      ↓
Fail
      ↓
Reopen Bug
```

---

# 19. Regression Testing

After important fixes, we may run related regression tests.

For example, after a login fix:

```text
TC_LOGIN_001
TC_LOGIN_002
TC_LOGIN_003
TC_LOGIN_004
TC_LOGIN_005
...
```

The exact regression scope should depend on the change and project risk.

The purpose is to check whether the fix introduced problems elsewhere.

---

# 20. Test Execution Report

After executing the tests, we summarize the results.

Example:

```text
Project:
Easy Buy

Test Cycle:
Release 1.0

Planned:
50

Executed:
38

Passed:
32

Failed:
6

Blocked:
4

Not Run:
8
```

We can calculate:

```text
Execution Coverage = 38 / 50 × 100 = 76%

Pass Rate = 32 / 38 × 100 ≈ 84%

Fail Rate = 6 / 38 × 100 ≈ 16%
```

These metrics describe the current execution results.

---

# 21. Defect Summary

We can also summarize defects.

Example:

```text
Total Defects: 6

Critical: 0
High: 2
Medium: 3
Low: 1

Open: 3
Fixed: 2
Closed: 1
```

The report should also identify important unresolved issues and areas that remain untested.

---

# 22. Requirements Traceability Matrix

Finally, we connect requirements to their test cases and results.

Example:

| Requirement | Test Case     | Status | Defect         |
| ----------- | ------------- | ------ | -------------- |
| R1          | TC_LOGIN_001  | Fail   | BUG-LOGIN-001  |
| R2          | TC_LOGIN_005  | Pass   | -              |
| R3          | TC_LOGIN_008  | Pass   | -              |
| R4          | TC_LOGIN_002  | Pass   | -              |
| R5          | TC_SEARCH_001 | Fail   | BUG-SEARCH-001 |

This allows us to trace:

```text
Requirement
    ↓
Test Case
    ↓
Execution Result
    ↓
Defect
```

---

# 23. Project Deliverables

By the end of this practical project, we should have practiced creating:

```text
01. Requirements
02. Test Plan
03. Test Scenarios
04. Test Cases
05. Test Data
06. Test Execution Results
07. Bug Reports
08. Retest Results
09. Regression Test Results
10. Test Execution Report
11. Test Summary Report
12. Requirements Traceability Matrix
```

These are useful artifacts to understand and discuss as part of a QA portfolio.

---

# 24. Suggested Project Folder Structure

The project can be organized like this:

```text
practical-project/
│
├── requirements/
│   └── easy-buy-requirements.md
│
├── test-plan/
│   └── easy-buy-test-plan.md
│
├── test-scenarios/
│   ├── login-scenarios.md
│   ├── search-scenarios.md
│   ├── cart-scenarios.md
│   └── checkout-scenarios.md
│
├── test-cases/
│   ├── login-test-cases.md
│   ├── search-test-cases.md
│   ├── cart-test-cases.md
│   └── checkout-test-cases.md
│
├── test-execution/
│   └── easy-buy-test-execution.md
│
├── bug-reports/
│   ├── BUG-LOGIN-001.md
│   └── BUG-SEARCH-001.md
│
├── reports/
│   ├── test-execution-report.md
│   └── test-summary-report.md
│
└── rtm/
    └── easy-buy-rtm.md
```

The exact GitHub structure can be adjusted as the project grows.

---

# 25. What We Have Already Practiced

Before this final project note, we practiced many of these activities individually.

We have already worked with:

* Professional test cases
* Test case structure
* Test scenarios vs test cases
* Test data
* Preconditions
* Postconditions
* Expected vs Actual Results
* Test execution
* Pass / Fail / Blocked / Not Run
* Bug reports
* Severity vs Priority
* Test execution metrics
* Test summary reports
* RTM

The practical project brings these pieces together.

---

# 26. What We Will Practice Next

We will now work through the Easy Buy project as if we were testing a real application.

The practical sequence will be:

### Step 1 — Review the Requirements

Understand exactly what the application is supposed to do.

### Step 2 — Create the Test Plan

Define:

* Scope
* Testing types
* Environment
* Roles
* Schedule
* Risks
* Entry and exit criteria

### Step 3 — Create Test Scenarios

Identify the high-level areas that need testing.

### Step 4 — Create Test Cases

Turn scenarios into detailed executable tests.

Apply Level 2 techniques where appropriate:

* Equivalence Partitioning
* Boundary Value Analysis
* Decision Tables
* State Transitions
* Error Guessing
* Positive/Negative Testing

### Step 5 — Prepare Test Data

Identify the data needed for execution.

### Step 6 — Execute the Tests

Record:

* Actual Result
* Status
* Evidence

### Step 7 — Report Defects

Create clear bug reports for confirmed defects.

### Step 8 — Retest Fixes

Execute failed tests again after fixes.

### Step 9 — Run Regression Tests

Check related functionality after changes.

### Step 10 — Create Test Reports

Summarize execution results and defects.

### Step 11 — Build the RTM

Connect:

```text
Requirements
     ↓
Scenarios
     ↓
Test Cases
     ↓
Results
     ↓
Defects
```

---

# 27. Practical QA Mindset

Throughout the project, don't think of QA as simply:

> "Click the buttons and see if they work."

Instead, think:

```text
What should the system do?
        ↓
What could go wrong?
        ↓
What conditions should I test?
        ↓
What test data do I need?
        ↓
What should I observe?
        ↓
What actually happened?
        ↓
Does it match the requirement?
        ↓
If not, why?
        ↓
How can I communicate the issue clearly?
```

This mindset is more important than memorizing QA terminology.

---

# 28. Final Level 3 Learning Outcome

By the end of this practical project, you should be able to take a simple set of software requirements and independently:

* Identify test scenarios.
* Design test cases.
* Select appropriate test data.
* Apply test design techniques.
* Define preconditions and postconditions.
* Execute test cases.
* Record Actual Results.
* Assign Pass, Fail, Blocked, or Not Run.
* Investigate failed tests.
* Write reproducible bug reports.
* Understand severity and priority.
* Retest fixed defects.
* Perform relevant regression testing.
* Calculate basic test execution metrics.
* Create test execution and summary reports.
* Build an RTM.
* Identify testing gaps and remaining risks.

The overall QA workflow is:

```text
Requirements
      ↓
Test Planning
      ↓
Test Scenarios
      ↓
Test Design
      ↓
Test Cases
      ↓
Test Data
      ↓
Test Execution
      ↓
Expected vs Actual
      ↓
Pass / Fail / Blocked / Not Run
      ↓
Bug Reporting
      ↓
Retesting
      ↓
Regression Testing
      ↓
Test Reporting
      ↓
RTM
```

---

# Key Takeaways

Level 3 is about turning your knowledge of testing into **professional QA work**.

You are no longer only asking:

> "What is testing?"

You are practicing:

> "Here is a requirement. How do I verify it?"

> "Here is a failed test. How do I document it?"

> "Here are 50 planned tests. What does the execution data tell me?"

> "Here is a defect. How do I reproduce and retest it?"

> "Here are 15 requirements. How do I prove that they have been tested?"

That is the purpose of this practical project.

The final goal is to move from:

```text
Learning QA concepts
```

to:

```text
Applying QA concepts to a realistic software project.
```

And that practical experience will become an important foundation for the next levels of your QA learning journey.
