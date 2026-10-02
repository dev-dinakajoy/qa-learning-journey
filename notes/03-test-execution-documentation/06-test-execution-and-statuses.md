# Test Execution and Statuses

Writing test cases is only part of the QA process.

After test cases are designed, QA testers need to **execute them**, record what actually happened, compare the results with the expected behavior, and assign an appropriate status.

This process is called **Test Execution**.

---

# 1. What Is Test Execution?

**Test Execution** is the process of running test cases against the software and recording the results.

During execution, the tester:

1. Selects the test cases to execute.
2. Reviews the preconditions and test data.
3. Performs the test steps.
4. Observes the application behavior.
5. Records the Actual Result.
6. Compares Actual Result with Expected Result.
7. Assigns a status.
8. Reports defects when necessary.

The basic flow is:

```text
Test Case
    ↓
Prepare Environment & Test Data
    ↓
Execute Steps
    ↓
Observe Behavior
    ↓
Record Actual Result
    ↓
Compare Expected vs Actual
    ↓
Assign Status
    ↓
Report Defect if Necessary
```

---

# 2. Test Execution Is Different From Test Design

Test design answers:

> **What should we test?**

Test execution answers:

> **What happened when we tested it?**

For example:

### During Test Design

You create:

```text
TC_LOGIN_001

Verify that a registered user can log in with valid credentials.
```

Expected:

> The user is successfully logged in and redirected to the dashboard.

At this point:

```text
Status: Not Run
```

### During Test Execution

You actually open the application, enter the credentials, and click Login.

Suppose the application displays:

> "Invalid email or password"

and keeps the user on the Login page.

You record:

```text
Actual Result:
The system displays "Invalid email or password" and the user remains on the Login page.

Status:
Fail
```

---

# 3. Before Executing a Test

Before starting execution, verify that the test can actually be performed.

Check:

### Environment

* Is the correct application/build available?
* Is the test environment accessible?
* Is the required browser/device available?
* Are required services running?

### Preconditions

* Does the required user account exist?
* Is the user logged in if necessary?
* Is the required product available?
* Is the required data available?

### Test Data

* Do you have the required credentials?
* Are the input values correct?
* Are boundary values prepared?
* Are invalid values available for negative testing?

### Test Case

* Are the steps clear?
* Is the expected behavior defined?
* Is the requirement known?

If something essential is missing, you may not be able to execute the test.

---

# 4. Test Execution Statuses

The most common statuses we will use are:

* **Not Run**
* **Pass**
* **Fail**
* **Blocked**

These statuses tell the team what happened to each test case.

---

# 5. Not Run

**Not Run** means the test case has not yet been executed.

Example:

```text
Test Case:
TC_CHECKOUT_001

Status:
Not Run
```

This might happen because:

* Testing has not started yet.
* The test is scheduled for a later phase.
* There was not enough time to execute it.
* The tester prioritized other tests.
* The test is outside the current execution scope.

### Important

Not Run does **not** mean the test passed or failed.

We simply don't have an execution result yet.

---

# 6. Pass

A test is **Pass** when the actual behavior satisfies the expected behavior.

Example:

### Expected

> The user is successfully logged in and redirected to the dashboard.

### Actual

> The user is successfully logged in and redirected to the dashboard.

### Status

```text
Pass
```

Another example:

### Expected

> Invalid email format is rejected and an appropriate validation message is displayed.

### Actual

> The system rejects the invalid email and displays the email validation message.

### Status

```text
Pass
```

Remember:

> **Pass means the software behaved as expected.**

It does not necessarily mean that the user successfully completed an action.

For a negative test, correctly rejecting invalid input is a **Pass**.

---

# 7. Fail

A test is **Fail** when the actual behavior does not satisfy the expected behavior.

Example:

### Expected

> Matching products are displayed.

### Actual

> No products are displayed even though matching products exist.

### Status

```text
Fail
```

Another example:

### Expected

> A user with valid credentials is redirected to the dashboard.

### Actual

> The system displays "Invalid email or password" and keeps the user on the Login page.

### Status

```text
Fail
```

A failed test should normally be investigated to determine the cause.

If the failure is confirmed to be a software defect, a bug report should be created.

---

# 8. Blocked

A test is **Blocked** when it cannot be executed because something required for execution is unavailable.

Example:

```text
Test Case:
TC_CHECKOUT_005

Precondition:
Payment service is available.

Situation:
Payment service is unavailable.

Status:
Blocked
```

The tester cannot meaningfully complete the test because a required dependency is unavailable.

### Common reasons for Blocked

* Application is unavailable.
* Required environment is down.
* Test data cannot be created.
* Required user account does not exist.
* Another defect prevents execution.
* External service is unavailable.
* Required configuration is missing.

---

# 9. Blocked vs Failed

This distinction is very important.

### Failed

You **executed the test**, and the software produced the wrong result.

```text
Test executed
      ↓
Actual ≠ Expected
      ↓
FAIL
```

### Blocked

You **could not properly execute the test** because something prevented execution.

```text
Cannot execute test
        ↓
Required dependency unavailable
        ↓
BLOCKED
```

### Example

Suppose you are testing checkout.

#### Situation A — Fail

The checkout page opens.

You enter valid information.

You click **Place Order**.

Expected:

> Order is successfully placed.

Actual:

> The application displays "Something went wrong" and the order is not placed.

Result:

> **Fail**

The test was executed.

#### Situation B — Blocked

You cannot even reach the checkout page because the application is unavailable.

Result:

> **Blocked**

The test could not be executed.

---

# 10. Blocked vs Not Run

These can also be confused.

### Not Run

The test simply hasn't been executed.

Example:

> Checkout testing is scheduled for tomorrow.

```text
Status: Not Run
```

### Blocked

The tester attempted or was ready to execute the test, but a dependency prevented execution.

Example:

> Checkout testing was planned for today, but the checkout environment is unavailable.

```text
Status: Blocked
```

A simple way to remember:

```text
NOT RUN
"Nobody has executed this yet."

BLOCKED
"We cannot execute this because something is preventing us."
```

---

# 11. Status Decision Flow

Use this simple decision process:

```text
Has the test been executed?
          │
      ┌───┴───┐
     No      Yes
     │         │
     ↓         ↓
 Not Run   Could it be
           executed properly?
                │
          ┌─────┴─────┐
         No          Yes
         │             │
         ↓             ↓
     Blocked      Compare Actual
                  vs Expected
                       │
                 ┌─────┴─────┐
                Match     Doesn't Match
                  │            │
                  ↓            ↓
                Pass          Fail
```

---

# 12. Executing a Test Case Step by Step

Let's execute one of our Easy Buy test cases.

## Test Case

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

---

## Step 1 — Review Preconditions

Check:

> Does the registered user account exist?

Yes.

Proceed.

---

## Step 2 — Prepare Test Data

Use:

```text
Email: user1@test.com
Password: <test account password>
```

---

## Step 3 — Execute Steps

Perform:

```text
1. Open Login page.
2. Enter email.
3. Enter password.
4. Click Login.
```

---

## Step 4 — Observe the Application

Suppose the application redirects the user to the dashboard.

---

## Step 5 — Record Actual Result

```text
Actual Result:
The user is successfully logged in and redirected to the dashboard.
```

---

## Step 6 — Compare Results

Expected:

> User is successfully logged in and redirected to the dashboard.

Actual:

> User is successfully logged in and redirected to the dashboard.

They match.

---

## Step 7 — Assign Status

```text
Status:
Pass
```

The executed test now looks like:

```text
Test Case ID:
TC_LOGIN_001

Expected Result:
The user is successfully logged in and redirected to the dashboard.

Actual Result:
The user is successfully logged in and redirected to the dashboard.

Status:
Pass
```

---

# 13. Executing a Failed Test

Now suppose the application behaves differently.

### Expected

> The user is successfully logged in and redirected to the dashboard.

### Actual

> The system displays "Invalid email or password" and the user remains on the Login page.

### Status

```text
Fail
```

At this point, the tester should investigate and, if the behavior is confirmed to be a defect, create a bug report.

---

# 14. Recording Evidence

When a test fails, collect useful evidence where possible.

Examples:

* Screenshot
* Screen recording
* Error message
* Console log
* Network information
* Relevant application data

For example:

```text
Actual Result:
The system displays "Invalid email or password" and the user remains on the Login page.

Evidence:
Screenshot attached.
```

Evidence helps developers reproduce and investigate the issue.

---

# 15. Test Execution and Defect Reporting

The relationship between test execution and bug reporting is:

```text
Execute Test
     ↓
Compare Expected vs Actual
     ↓
Mismatch?
     ↓
   Yes
     ↓
Investigate
     ↓
Confirmed Defect?
     ↓
   Yes
     ↓
Create Bug Report
```

Not every failed test necessarily becomes a bug.

For example, a test might fail because:

* The test data was incorrect.
* The environment was misconfigured.
* The requirement was misunderstood.
* The external service was unavailable.
* The test itself contained an error.

The tester should investigate the failure before creating a defect.

---

# 16. Re-testing a Failed Test

After a developer fixes a reported defect, QA may execute the failed test again.

This is commonly called **re-testing** or **confirmation testing**.

Example:

```text
Initial execution
       ↓
Test fails
       ↓
Bug reported
       ↓
Developer fixes defect
       ↓
QA re-executes failed test
       ↓
Compare Expected vs Actual
```

If the original problem is fixed:

```text
Status: Pass
```

If the problem still exists:

```text
Status: Fail
```

The exact workflow may vary between teams.

---

# 17. Regression Testing After a Fix

A fix can potentially affect other functionality.

Therefore, after fixing a defect, QA may also execute related regression tests.

For example:

```text
Login bug fixed
      ↓
Re-test login
      ↓
Run related login tests
      ↓
Run relevant regression tests
```

This helps determine whether the change introduced unintended problems elsewhere.

---

# 18. Updating Test Cases During Execution

Sometimes execution reveals that a test case needs clarification.

For example:

Original:

> Verify that the search works correctly.

This is too vague.

It may be improved to:

> Verify that products matching a valid keyword are displayed in the search results.

If the requirement or product behavior changes, the test case may also need updating.

However, don't change the Expected Result simply to make a failing test pass.

The test case should remain aligned with the approved requirement or intended behavior.

---

# 19. Test Execution Records

A simple execution table might look like this:

| Test Case       | Expected Result                  | Actual Result                | Status  |
| --------------- | -------------------------------- | ---------------------------- | ------- |
| TC_LOGIN_001    | User reaches dashboard           | User reaches dashboard       | Pass    |
| TC_LOGIN_002    | Invalid email is rejected        | Validation message displayed | Pass    |
| TC_LOGIN_003    | Wrong password is rejected       | Error displayed              | Pass    |
| TC_LOGIN_004    | Invalid credentials are rejected | User remains on Login page   | Pass    |
| TC_SEARCH_001   | Matching products displayed      | No products displayed        | Fail    |
| TC_CHECKOUT_001 | Checkout page opens              | Checkout service unavailable | Blocked |
| TC_CART_001     | Product added to cart            | -                            | Not Run |

This table provides a quick view of the current execution state.

---

# 20. Execution Status Summary

Once several tests have been executed, the team can summarize the results.

Example:

```text
Total Test Cases: 10

Passed: 6
Failed: 2
Blocked: 1
Not Run: 1
```

The numbers should add up to the total:

```text
6 + 2 + 1 + 1 = 10
```

These metrics become useful when creating a **Test Execution Report** or **Test Summary Report**.

We will cover that in more detail later.

---

# 21. Common Test Execution Mistakes

## Mistake 1 — Marking an unexecuted test as Pass

Incorrect:

```text
Test was not executed
        ↓
Status: Pass
```

Correct:

```text
Test was not executed
        ↓
Status: Not Run
```

---

## Mistake 2 — Marking an unexecutable test as Fail

Suppose the environment is completely unavailable.

Incorrect:

```text
Application unavailable
        ↓
Status: Fail
```

The tester did not actually test the functionality.

Depending on the circumstances:

```text
Status: Blocked
```

---

## Mistake 3 — Marking every failure as a bug immediately

A failed test needs investigation.

Ask:

* Was the test data correct?
* Was the environment correct?
* Were the steps followed correctly?
* Is the requirement clear?
* Can the problem be reproduced?
* Is the behavior actually a defect?

---

## Mistake 4 — Changing Expected Result after execution

Never do this just because the application behaved differently.

The Expected Result should represent the required behavior.

---

## Mistake 5 — Not recording Actual Results

Avoid:

```text
Status: Fail
```

without documenting what happened.

Better:

```text
Actual Result:
The user remains on the Login page and an "Invalid email or password"
message is displayed.

Status:
Fail
```

The Actual Result provides the evidence behind the status.

---

# 22. Practical Execution Checklist

Before execution:

* [ ] Test environment is available.
* [ ] Preconditions are satisfied.
* [ ] Test data is ready.
* [ ] Test case steps are clear.
* [ ] Expected Result is understood.

During execution:

* [ ] Follow the test steps.
* [ ] Observe the application carefully.
* [ ] Record the Actual Result.
* [ ] Capture evidence when useful.

After execution:

* [ ] Compare Actual vs Expected.
* [ ] Assign the correct status.
* [ ] Investigate failures.
* [ ] Create a bug report when a defect is confirmed.
* [ ] Update execution records.

---

# 23. Key Takeaways

Test execution is where the test case becomes an actual test.

Remember:

```text
NOT RUN
Test hasn't been executed.

PASS
Actual behavior satisfies Expected behavior.

FAIL
Actual behavior does not satisfy Expected behavior.

BLOCKED
The test cannot be properly executed because something prevents it.
```

The complete QA execution flow is:

```text
Requirement
    ↓
Test Scenario
    ↓
Test Case
    ↓
Test Data + Preconditions
    ↓
Execute Test
    ↓
Actual Result
    ↓
Compare with Expected Result
    ↓
┌───────────────┬───────────────┐
│               │               │
PASS           FAIL          BLOCKED
│               │               │
│          Investigate          │
│               ↓               │
│        Confirmed Defect?      │
│               ↓               │
│          Bug Report           │
└───────────────┴───────────────┘
```

Good test execution is not simply clicking through test cases. It requires careful observation, accurate documentation, correct status assignment, and investigation of unexpected behavior.
