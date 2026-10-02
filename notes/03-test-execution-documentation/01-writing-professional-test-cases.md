# Writing Professional Test Cases

## What is a Test Case?

A **test case** is a documented set of conditions, test data, steps, and expected results used to verify whether a specific software behavior works as intended.

A test case should allow another tester to execute the same test and reach an objective conclusion about whether the software passed or failed.

---

## Why Write Professional Test Cases?

Professional test cases help QA teams:

* Verify requirements systematically
* Avoid missing important test conditions
* Make testing repeatable
* Document expected software behavior
* Record actual test results
* Identify defects clearly
* Support regression testing
* Provide evidence of test coverage
* Make testing easier for other team members to understand

A good test case should be:

* **Clear** — another tester should understand it without asking for clarification.
* **Specific** — it should test a clearly defined behavior.
* **Repeatable** — another tester should be able to execute it consistently.
* **Traceable** — it should be linked to a requirement or test scenario.
* **Objective** — the result should be measurable as Pass, Fail, Blocked, or another defined status.

---

## Test Case Structure

A professional test case commonly contains:

| Field           | Purpose                                   |
| --------------- | ----------------------------------------- |
| Test Case ID    | Unique identifier for the test case       |
| Title           | Short description of what is being tested |
| Requirement     | Requirement being verified                |
| Priority        | Importance of executing the test          |
| Precondition    | Conditions that must exist before testing |
| Test Data       | Data required to execute the test         |
| Steps           | Actions the tester performs               |
| Expected Result | What the system should do                 |
| Actual Result   | What the system actually did              |
| Status          | Result of execution                       |
| Postcondition   | State of the system after execution       |
| Notes           | Additional information                    |

---

### Example

```text
Test Case ID: TC_LOGIN_001

Title:
Verify that a registered user can log in with valid credentials.

Requirement:
R1

Priority:
High

Precondition:
A registered user account exists with valid credentials.

Test Data:
Email: user1@test.com
Password: <test account password>

Steps:
1. Open the Login page.
2. Enter the registered email address.
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

## Writing Good Test Case Titles

A test case title should describe the behavior being verified.

### Good

> Verify that a registered user can log in with valid credentials.

### Less useful

> Login test

The first title tells us exactly what behavior is being tested.

---

## Test Cases Should Be Traceable

A test case should normally be connected to a requirement.

For example:

```text
Requirement
R1 — Registered users can log in with valid credentials.

        ↓

Test Scenario
TS_LOGIN_001 — Verify that a registered user can log in with valid credentials.

        ↓

Test Case
TC_LOGIN_001 — Detailed steps for verifying the behavior.
```

This relationship becomes particularly important when creating a **Requirements Traceability Matrix (RTM)**.

---

## Test Cases and Test Design Techniques

Test cases should not be created randomly.

The test design techniques learned in Level 2 help determine which conditions and values should be tested.

For example, suppose:

> A password must contain at least 8 characters.

Using **Boundary Value Analysis**, we can test:

| Password Length | Expected |
| --------------: | -------- |
|               7 | Invalid  |
|               8 | Valid    |
|               9 | Valid    |

The requirement gives us the rule, while the test design technique helps us select useful test values.

---

## Example: Login Test Suite

A single login requirement can result in multiple test cases.

```text
R3 — Password must contain at least 8 characters.
              ↓
       TS_LOGIN_003
              ↓
       ┌──────┼──────┐
       ↓      ↓      ↓
      TC008  TC009  TC010
       7      8      9
```

This demonstrates an important principle:

> One requirement does not necessarily equal one test case.

A requirement may require multiple test cases to adequately verify its behavior.

---

## Good Test Case Practices

### 1. Keep the scope clear

A test case should focus on a specific behavior or condition.

Avoid combining unrelated behaviors into one test.

### 2. Use realistic test data

Test data should represent the condition being tested.

For example:

```text
Valid email:
user1@test.com

Invalid email:
user1test

Empty email:
""
```

### 3. Make expected results objective

Avoid vague statements such as:

> The system behaves correctly.

Prefer:

> The system displays an "Invalid email format" validation message and the user remains on the Login page.

The expected result should make it possible to determine objectively whether the test passed or failed.

### 4. Keep Actual Result separate from Expected Result

Before execution:

```text
Expected Result:
User is redirected to the dashboard.

Actual Result:
-

Status:
Not Run
```

After execution, record what actually happened.

For example:

```text
Expected Result:
User is redirected to the dashboard.

Actual Result:
User remains on the Login page and receives an "Invalid email or password" message.

Status:
Fail
```

Never change the Expected Result to match what the application actually did.

### 5. Use test design techniques

Use techniques such as:

* Equivalence Partitioning
* Boundary Value Analysis
* Decision Table Testing
* State Transition Testing
* Error Guessing
* Positive Testing
* Negative Testing

These techniques help create meaningful test coverage instead of simply generating large numbers of similar test cases.

---

## Test Case Quality Checklist

Before considering a test case complete, ask:

* [ ] Is the Test Case ID unique?
* [ ] Does the title clearly describe the behavior?
* [ ] Is the requirement identified?
* [ ] Is the priority appropriate?
* [ ] Are the preconditions clear?
* [ ] Is the required test data provided?
* [ ] Are the steps clear and executable?
* [ ] Is the expected result specific?
* [ ] Is Actual Result left empty until execution?
* [ ] Is the initial status set correctly?
* [ ] Is the postcondition documented where useful?
* [ ] Can another tester execute the test without clarification?
* [ ] Can the result objectively be classified as Pass or Fail?

---

## Key Takeaways

A professional test case is more than a list of steps.

It connects:

```text
Requirement
    ↓
Test Scenario
    ↓
Test Case
    ↓
Test Data
    ↓
Expected Result
    ↓
Actual Result
    ↓
Test Status
```

Good test cases are:

* Clear
* Specific
* Repeatable
* Traceable
* Objective
* Designed using appropriate test design techniques

The goal is not to create as many test cases as possible.

The goal is to create **useful test cases that provide meaningful coverage of the software requirements**.
