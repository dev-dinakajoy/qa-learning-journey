# Test Case Structure

A professional test case follows a consistent structure so that another tester can understand and execute it without needing additional clarification.

A typical test case contains:

1. Test Case ID
2. Title
3. Requirement
4. Priority
5. Precondition
6. Test Data
7. Steps
8. Expected Result
9. Actual Result
10. Status
11. Postcondition
12. Notes

Not every organization uses exactly the same fields, but these provide a useful structure for manual QA testing.

---

# 1. Test Case ID

The **Test Case ID** is a unique identifier assigned to a test case.

### Example

```text
TC_LOGIN_001
TC_LOGIN_002
TC_SEARCH_001
```

A good ID usually makes it easy to identify the feature being tested.

For example:

```text
TC_LOGIN_001
     ↓
   Login
```

```text
TC_SEARCH_001
     ↓
  Search
```

### Why it matters

Test Case IDs allow QA teams to:

* Identify test cases quickly
* Reference tests in bug reports
* Track test execution
* Build an RTM
* Discuss specific tests with developers and other testers

---

# 2. Title

The title briefly describes what the test verifies.

### Good

> Verify that a registered user can log in with valid credentials.

### Too vague

> Login test

### Too detailed

> Open the login page, enter email, enter password, click login, and check if the dashboard appears.

The detailed actions belong in the **Steps** field.

### Good title formula

A useful pattern is:

> **Verify that [actor/system] can/cannot [behavior] under [condition].**

Examples:

```text
Verify that a registered user can log in with valid credentials.

Verify that a user cannot log in with an incorrect password.

Verify that users can search for products using valid keywords.
```

---

# 3. Requirement

The **Requirement** identifies the requirement that the test case verifies.

### Example

```text
Requirement: R1
```

Where R1 might be:

> A registered user who enters valid credentials should be successfully logged in and redirected to the dashboard.

### Why it matters

Requirement mapping provides traceability:

```text
Requirement
     ↓
Test Scenario
     ↓
Test Case
```

It also allows the QA team to determine whether requirements have been adequately tested.

---

# 4. Priority

**Priority** indicates how important it is to execute the test case.

A simple scale might be:

* **High**
* **Medium**
* **Low**

### High

Tests important functionality or functionality that should be tested early.

Examples:

* User login
* Checkout
* Order placement
* Payment-related functionality

### Medium

Important functionality that is not necessarily the highest risk.

Examples:

* Product search
* Product filtering
* Cart quantity updates

### Low

Less critical functionality.

Examples:

* Minor UI details
* Optional features
* Non-critical visual behavior

Priority is about **how urgently the test should be executed**, not how severe a defect would be if the test failed.

---

# 5. Precondition

A **precondition** describes what must be true before the test can be executed.

### Example

```text
Precondition:
A registered user account exists with valid credentials.
```

For a product search test:

```text
Precondition:
The Products page is accessible and products are available.
```

For a checkout test:

```text
Precondition:
The user is logged in and has at least one product in the cart.
```

### Why preconditions matter

Without clear preconditions, a tester may not know what needs to be prepared before execution.

---

# 6. Test Data

**Test Data** is the information required to execute the test.

Example:

```text
Email: user1@test.com
Password: <test account password>
```

For search:

```text
Keyword: phone
```

For Boundary Value Analysis:

```text
Password length: 7 characters
```

Test data should correspond to the condition being tested.

---

# 7. Steps

The **Steps** describe the actions the tester performs.

Good steps should be:

* Clear
* Sequential
* Specific
* Easy to reproduce

### Example

```text
1. Open the Login page.
2. Enter the registered email address.
3. Enter the correct password.
4. Click Login.
```

Avoid vague steps such as:

> Log in normally.

Another tester should not have to guess what "normally" means.

---

# 8. Expected Result

The **Expected Result** describes what the system should do when the test is executed successfully.

Example:

> The user is successfully logged in and redirected to the dashboard.

For validation:

> The system displays an "Invalid email format" validation message and the user remains on the Login page.

### Good expected results are:

* Specific
* Observable
* Measurable
* Based on requirements

Avoid:

> The system works correctly.

That is too vague.

---

# 9. Actual Result

The **Actual Result** records what actually happened when the test was executed.

Before execution:

```text
Actual Result: -
```

After execution:

```text
Actual Result:
The system displays "Invalid email or password" and the user remains on the Login page.
```

### Important rule

Never modify the Expected Result to match the Actual Result.

The Expected Result represents the **required behavior**.

The Actual Result represents the **observed behavior**.

---

# 10. Status

The **Status** indicates the outcome or current execution state of the test.

Common statuses include:

### Not Run

The test has not yet been executed.

```text
Status: Not Run
```

### Pass

The actual result matches the expected result.

```text
Status: Pass
```

### Fail

The actual result does not match the expected result.

```text
Status: Fail
```

### Blocked

The test cannot be executed because a dependency or required condition is unavailable.

Example:

> Payment service is unavailable, so checkout payment testing cannot proceed.

```text
Status: Blocked
```

These statuses become particularly important during **Test Execution** and **Test Summary Reporting**.

---

# 11. Postcondition

A **postcondition** describes the state of the system after the test has been executed.

Example:

```text
Postcondition:
The user is logged in.
```

For an unsuccessful login:

```text
Postcondition:
The user remains on the Login page.
```

Postconditions are especially useful when a test changes the application's state.

For example:

```text
Add product to cart
        ↓
Postcondition:
Product is present in the shopping cart.
```

---

# 12. Notes

The **Notes** field contains additional information that may help the tester.

Examples:

```text
Notes:
Test requires a registered user account.
```

Or:

```text
Notes:
Verify that the error message does not expose sensitive authentication information.
```

If there is nothing important to add:

```text
Notes: -
```

---

# Complete Example

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

Postcondition:
The user is logged in.

Notes:
-
```

---

# Test Case Structure at a Glance

```text
Test Case
│
├── ID
├── Title
├── Requirement
├── Priority
├── Precondition
├── Test Data
├── Steps
├── Expected Result
├── Actual Result
├── Status
├── Postcondition
└── Notes
```

Each field answers a different question:

| Field           | Question it answers                            |
| --------------- | ---------------------------------------------- |
| Test Case ID    | Which test is this?                            |
| Title           | What are we testing?                           |
| Requirement     | Why are we testing it?                         |
| Priority        | How important is this test?                    |
| Precondition    | What must be true before testing?              |
| Test Data       | What data do we need?                          |
| Steps           | How do we perform the test?                    |
| Expected Result | What should happen?                            |
| Actual Result   | What actually happened?                        |
| Status          | Did the test pass, fail, or not run?           |
| Postcondition   | What state is the system left in?              |
| Notes           | Is there anything else the tester should know? |

---

# Key Takeaways

A well-structured test case should allow another tester to answer:

> **What am I testing?**

> **Why am I testing it?**

> **What do I need before starting?**

> **What data should I use?**

> **What steps should I perform?**

> **What should happen?**

> **What actually happened?**

> **What was the result?**

> **What state is the system in afterward?**

A consistent test case structure makes test execution easier, improves communication within the QA team, and provides the information needed for defect reporting, test reporting, and requirements traceability.
