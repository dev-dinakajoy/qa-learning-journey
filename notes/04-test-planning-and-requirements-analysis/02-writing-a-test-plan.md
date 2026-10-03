# Writing a Test Plan

## What is a Test Plan?

A Test Plan is a document that describes the **scope, objectives, approach, resources, schedule, risks, and activities** involved in testing a software application.

It answers important questions such as:

* What are we testing?
* Why are we testing it?
* What is included?
* What is excluded?
* How will we test?
* Who will perform the testing?
* When will testing happen?
* What environments and data are required?
* What are the risks?
* When will testing be considered complete?

---

## Typical Test Plan Structure

A Test Plan may contain:

1. Test Plan ID
2. Introduction
3. Test Objectives
4. Scope
5. Out of Scope
6. Testing Types
7. Test Environment
8. Test Data
9. Entry Criteria
10. Exit Criteria
11. Risks and Mitigation
12. Test Approach
13. Roles and Responsibilities
14. Test Schedule
15. Test Deliverables

The exact structure may vary between organizations.

---

## Example: Food Delivery Application

### Test Plan ID

`TP-FDA-001`

### Test Objectives

Verify that users can:

* Register
* Log in
* Search for restaurants
* View menus
* Add food to their cart
* Place orders
* View order history

### In Scope

* Register
* Login
* Restaurant search
* Menu viewing
* Cart
* Order placement
* Order history

### Out of Scope

* Password reset
* Payment gateway
* Delivery processing

---

## Testing Types

The test plan may specify:

* Functional Testing
* Regression Testing
* Exploratory Testing
* Negative Testing
* Smoke Testing
* Usability Testing
* Compatibility Testing

---

## Test Environment

The environment describes where testing will take place.

Example:

* Chrome
* Firefox
* macOS
* Android
* Test database

---

## Entry Criteria

Entry criteria define the conditions that should be met **before testing can begin**.

Examples:

* Build is deployed to the test environment.
* Required features are implemented.
* Test environment is available.
* Requirements are approved.
* Test data is available.
* Critical dependencies are working.

---

## Exit Criteria

Exit criteria define the conditions that should be met before testing can be considered complete.

Examples:

* All planned test cases have been executed.
* Critical test cases have passed.
* No open Critical or Blocker defects remain.
* Major defects have been resolved or accepted.
* Regression testing is completed.
* Test results have been documented.

---

## Risks

A Test Plan should identify potential risks.

Example:

| Risk                            | Impact | Mitigation                    |
| ------------------------------- | ------ | ----------------------------- |
| Test environment unavailable    | High   | Prepare backup environment    |
| Requirements change frequently  | Medium | Review requirements regularly |
| Test data unavailable           | High   | Prepare test data early       |
| Developer build delayed         | High   | Adjust testing schedule       |
| Third-party service unavailable | High   | Use a sandbox or mock         |

---

## Test Deliverables

Test deliverables are documents or outputs produced during testing.

Examples:

* Test Plan
* Test Scenarios
* Test Cases
* Test Data
* Bug Reports
* RTM
* Test Execution Report
* Test Summary Report

---

## Key Takeaway

A Test Plan provides a structured view of the testing effort.

It tells the team:

> **What will be tested, how it will be tested, who will test it, when it will happen, what is needed, and what conditions determine completion.**
