# Test Scenarios vs Test Cases

Test scenarios and test cases are both used to plan and document software testing, but they serve different purposes.

A simple way to remember the difference is:

> **A test scenario tells us what to test. A test case tells us how to test it.**

---

# What is a Test Scenario?

A **test scenario** is a high-level description of a functionality, behavior, or condition that needs to be tested.

It identifies **what we want to verify** without describing every step or test value.

### Example

```text
TS_LOGIN_001:
Verify that a registered user can log in with valid credentials.
```

The scenario tells us that login with valid credentials needs to be tested.

It does not specify:

* Which email to use
* Which password to use
* The exact steps
* The expected result in detail
* The execution status

Those details belong in the test case.

---

# What is a Test Case?

A **test case** is a detailed set of instructions and conditions used to verify a specific behavior.

It describes **how to perform the test** and what result is expected.

### Example

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
```

This test case provides everything needed to execute the scenario.

---

# Scenario vs Test Case

| Test Scenario                        | Test Case                                         |
| ------------------------------------ | ------------------------------------------------- |
| High-level                           | Detailed                                          |
| Describes what to test               | Describes how to test                             |
| Usually shorter                      | Contains multiple fields                          |
| Focuses on functionality or behavior | Focuses on a specific test condition              |
| Usually has fewer details            | Contains test data, steps, expected results, etc. |
| Helps identify testing scope         | Used directly during test execution               |

### Simple comparison

```text
Test Scenario
"What should we test?"

        ↓

Test Case
"Exactly how will we test it?"
```

---

# Example: Login

Suppose we have this requirement:

> **R1 — A registered user who enters valid credentials should be successfully logged in and redirected to the dashboard.**

We could create:

### Test Scenario

```text
TS_LOGIN_001:
Verify that a registered user can log in with valid credentials.
```

Then create the detailed test case:

```text
TC_LOGIN_001:
Verify that a registered user can log in with valid credentials.

Test Data:
Email: user1@test.com
Password: <test account password>

Steps:
1. Open the Login page.
2. Enter the registered email.
3. Enter the correct password.
4. Click Login.

Expected Result:
The user is logged in and redirected to the dashboard.
```

---

# One Scenario Can Have Multiple Test Cases

This is one of the most important concepts to understand.

A single test scenario may require multiple test cases.

For example:

```text
TS_LOGIN_002:
Verify that the system validates the email format during login.
```

This scenario could result in several test cases:

```text
TC_LOGIN_005
Invalid email format

TC_LOGIN_006
Empty email

TC_LOGIN_007
Email containing unsupported characters
```

The scenario identifies the general area:

> **Email validation**

The test cases explore specific conditions within that area.

---

# Test Design Techniques Help Create Test Cases

This is where our **Level 2 — Test Design** knowledge becomes useful.

Suppose the requirement says:

> The password must contain at least 8 characters.

We could create a scenario:

```text
TS_LOGIN_003:
Verify that the system validates the password according to the minimum length requirement.
```

Then use **Boundary Value Analysis** to determine useful test cases:

| Test Case    | Password Length | Expected |
| ------------ | --------------: | -------- |
| TC_LOGIN_008 |               7 | Invalid  |
| TC_LOGIN_009 |               8 | Valid    |
| TC_LOGIN_010 |               9 | Valid    |

The relationship becomes:

```text
Requirement
     ↓
Test Scenario
     ↓
Test Design Technique
     ↓
Test Cases
```

This prevents us from creating test cases randomly.

---

# Another Example: Product Search

Suppose we have:

> **R5 — Users should be able to search for products using keywords, and matching products should be displayed.**

A scenario could be:

```text
TS_SEARCH_001:
Verify that users can search for products using valid keywords.
```

We could then create multiple test cases:

```text
TC_SEARCH_001
Search using a complete product keyword.

TC_SEARCH_002
Search using a partial product keyword.

TC_SEARCH_003
Search using a keyword with different letter casing.
```

The scenario is broad enough to describe the area, while the test cases verify individual conditions.

---

# Test Scenario Types

Test scenarios can come from different sources.

## 1. Requirement-Based Scenarios

These are directly derived from documented requirements.

Example:

```text
Requirement:
Users can search for products using valid keywords.

Scenario:
Verify that users can search for products using valid keywords.
```

These are commonly called **requirement-based test scenarios**.

---

## 2. Exploratory / Error-Guessing Scenarios

Some scenarios are created from the tester's experience and understanding of potential failures rather than directly from a requirement.

Example:

```text
TS_SEARCH_004:
Verify how the system handles a search containing special characters.
```

The requirement may not explicitly mention special characters.

However, a tester may identify this as something worth investigating using **Error Guessing** or exploratory testing.

Another example:

```text
TS_SEARCH_005:
Verify how the system handles a search containing numbers only.
```

These scenarios can help discover unexpected behavior that requirements did not explicitly describe.

---

# Don't Make Every Test Condition a Separate Scenario

Consider this requirement:

> Password must contain at least 8 characters.

It would be unnecessary to create:

```text
TS_LOGIN_003:
Verify password with 7 characters.

TS_LOGIN_004:
Verify password with 8 characters.

TS_LOGIN_005:
Verify password with 9 characters.
```

These are better represented as **test cases** under one scenario:

```text
TS_LOGIN_003:
Verify that the system validates the password according to the minimum length requirement.

        ↓

TC_LOGIN_008 → 7 characters
TC_LOGIN_009 → 8 characters
TC_LOGIN_010 → 9 characters
```

This keeps test planning organized and avoids unnecessarily large numbers of scenarios.

---

# Scenario vs Test Case vs Test Step

These three concepts should not be confused.

### Test Scenario

> Verify that a registered user can log in with valid credentials.

### Test Case

> TC_LOGIN_001 — detailed test for valid login.

### Test Step

> Enter the registered email address.

The hierarchy is:

```text
Test Scenario
      ↓
  Test Case
      ↓
 Test Steps
```

---

# Relationship With Requirements

Test scenarios and test cases can be traced back to requirements.

For example:

```text
R1
Registered users can log in with valid credentials.
        ↓
TS_LOGIN_001
Verify that a registered user can log in with valid credentials.
        ↓
TC_LOGIN_001
Detailed valid-login test case.
        ↓
Execution
Pass / Fail / Blocked / Not Run
```

This traceability later becomes important when creating an **RTM — Requirements Traceability Matrix**.

---

# Test Scenarios and Test Cases in a QA Workflow

A simplified QA workflow looks like this:

```text
Requirements
      ↓
Test Scenarios
      ↓
Test Design
      ↓
Test Cases
      ↓
Test Execution
      ↓
Test Results
      ↓
Defects
      ↓
Test Reports
      ↓
RTM
```

Each stage has a different purpose.

---

# Common Mistakes

## Mistake 1: Treating a scenario as a test case

Example:

> Verify login functionality.

This is too high-level to execute.

A test case needs details such as:

* Test data
* Preconditions
* Steps
* Expected result

---

## Mistake 2: Making scenarios too detailed

Example:

> Verify that entering `user1@test.com`, entering the password, and clicking Login redirects the user to the dashboard.

This contains test-case-level information.

A cleaner scenario is:

> Verify that a registered user can log in with valid credentials.

---

## Mistake 3: Creating a scenario for every test value

For a minimum password length of 8:

Avoid:

```text
Scenario → 7 characters
Scenario → 8 characters
Scenario → 9 characters
```

Instead:

```text
Scenario → Password validation
                 ↓
             Test Cases
          7 / 8 / 9 characters
```

---

# Quick Comparison

| Question                    | Test Scenario                | Test Case                           |
| --------------------------- | ---------------------------- | ----------------------------------- |
| What is it?                 | High-level testing condition | Detailed test                       |
| Main purpose                | Define what to test          | Define how to test                  |
| Contains steps?             | Usually no                   | Yes                                 |
| Contains test data?         | Usually no                   | Yes                                 |
| Contains expected result?   | Usually high-level           | Yes                                 |
| Used during execution?      | Helps plan                   | Yes                                 |
| Can produce multiple tests? | Yes                          | No, it is itself an executable test |

---

# Key Takeaways

Remember these three statements:

> **A requirement tells us what the product should do.**

> **A test scenario tells us what we want to verify.**

> **A test case tells us exactly how we will verify it.**

The relationship can be represented as:

```text
Requirement
     ↓
Test Scenario
     ↓
Test Case
     ↓
Test Steps
     ↓
Expected Result
     ↓
Actual Result
     ↓
Status
```

A good QA tester does not simply create more test cases. They identify meaningful scenarios and then use appropriate test design techniques to create effective test cases.

The goal is **meaningful coverage**, not simply a large number of tests.
