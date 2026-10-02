# Expected vs Actual Results

**Expected Result** and **Actual Result** are two of the most important fields in a test case.

They answer two different questions:

> **Expected Result:** What should the system do?

> **Actual Result:** What did the system actually do?

Comparing these two results allows a QA tester to determine whether a test has **Passed or Failed**.

---

# 1. Expected Result

The **Expected Result** describes the behavior the system should produce based on the requirements, specifications, acceptance criteria, or other agreed product behavior.

### Example

Requirement:

> A registered user who enters valid credentials should be successfully logged in and redirected to the dashboard.

Expected Result:

> The user is successfully logged in and redirected to the dashboard.

The Expected Result represents the **correct or required behavior**.

---

# 2. Actual Result

The **Actual Result** records what the tester observed when executing the test.

For the same test, the application might behave correctly:

```text
Actual Result:
The user is successfully logged in and redirected to the dashboard.
```

Or it might behave incorrectly:

```text
Actual Result:
The system displays "Invalid email or password" and the user remains on the Login page.
```

The Actual Result should describe what actually happened, not what the tester expected to happen.

---

# Expected vs Actual

The basic relationship is:

```text
Expected Result
       ↓
What should happen?

        VS

Actual Result
       ↓
What actually happened?
```

Then:

```text
Expected Result = Actual Result
             ↓
            PASS
```

or:

```text
Expected Result ≠ Actual Result
             ↓
            FAIL
```

---

# Example: Passing Test

### Expected Result

> The user is successfully logged in and redirected to the dashboard.

### Actual Result

> The user is successfully logged in and redirected to the dashboard.

### Status

> **Pass**

The observed behavior matches the expected behavior.

---

# Example: Failed Test

### Expected Result

> The user is successfully logged in and redirected to the dashboard.

### Actual Result

> The system displays "Invalid email or password" and the user remains on the Login page.

### Status

> **Fail**

The observed behavior does not match the requirement.

This is what happened with our Easy Buy login defect:

```text
Expected:
User logs in and reaches dashboard.

Actual:
User remains on Login page.

Result:
Fail
```

---

# Expected Result Should Come From Requirements

The Expected Result should not be based on what the tester personally thinks the application should do.

Consider:

> Users should be able to search for products using keywords.

A tester should not automatically assume:

> Search must be case-insensitive.

That behavior might be reasonable, but unless it is specified or established as intended product behavior, it should not automatically become the Expected Result of a requirement-based test.

This is particularly important when testing behavior that is not explicitly defined.

---

# Avoid Vague Expected Results

### Poor

> The system works correctly.

This doesn't tell us what "correctly" means.

### Better

> Matching products are displayed.

### Even better when appropriate

> Products matching the entered keyword are displayed in the search results.

The Expected Result should be specific enough that another tester can objectively determine whether it happened.

---

# Expected Results Should Be Observable

A tester should be able to observe whether the expected behavior occurred.

### Weak

> The system processes the request properly.

### Stronger

> The order confirmation page is displayed and the order number is shown.

The second result gives the tester something concrete to verify.

---

# Actual Results Should Describe Facts

The Actual Result should report what the tester observed without adding unnecessary assumptions.

### Poor

> The backend authentication system is broken.

The tester may not have enough evidence to make this conclusion.

### Better

> The system displays "Invalid email or password" and the user remains on the Login page.

The second statement describes the observable behavior.

This distinction becomes very important when writing bug reports.

---

# Actual Result Should Not Be Written Before Execution

Before execution:

```text
Expected Result:
The user is successfully logged in and redirected to the dashboard.

Actual Result:
-

Status:
Not Run
```

After execution:

```text
Expected Result:
The user is successfully logged in and redirected to the dashboard.

Actual Result:
The user is successfully logged in and redirected to the dashboard.

Status:
Pass
```

Or:

```text
Expected Result:
The user is successfully logged in and redirected to the dashboard.

Actual Result:
The system displays "Invalid email or password" and the user remains on the Login page.

Status:
Fail
```

Do not predict the Actual Result.

---

# Expected vs Actual During Test Execution

A typical execution process looks like this:

```text
1. Read the test case
        ↓
2. Review the Expected Result
        ↓
3. Execute the test steps
        ↓
4. Observe the application
        ↓
5. Record the Actual Result
        ↓
6. Compare Expected vs Actual
        ↓
7. Assign the Status
```

This makes test execution objective and repeatable.

---

# What Counts as a Pass?

A test **Passes** when the observed behavior satisfies the expected behavior.

For example:

```text
Expected:
"Invalid email format" message is displayed.

Actual:
"Invalid email format" message is displayed.

Status:
Pass
```

The wording doesn't necessarily have to be identical.

What matters is whether the observed behavior satisfies the requirement.

For example:

```text
Expected:
The user is redirected to the dashboard.

Actual:
The application navigates the user to the dashboard after successful authentication.

Status:
Pass
```

These describe the same behavior.

---

# What Counts as a Fail?

A test **Fails** when the observed behavior does not satisfy the Expected Result.

Example:

```text
Expected:
Matching products are displayed.

Actual:
No products are displayed even though matching products exist.

Status:
Fail
```

Another example:

```text
Expected:
The user remains unauthenticated.

Actual:
The user is logged into the dashboard.

Status:
Fail
```

---

# Fail Does Not Automatically Mean the Software Is Broken

A failed test tells us:

> **The observed result did not match the expected result.**

It does not automatically tell us why.

Possible causes include:

* Software defect
* Incorrect test data
* Incorrect test environment
* Configuration problem
* Test setup problem
* Requirement misunderstanding
* Environment dependency
* External service failure

Therefore, after a failure, the QA tester should investigate before concluding exactly what caused it.

---

# Expected vs Actual and Defect Reporting

When a test fails because of a software defect, the Expected and Actual Results become important parts of the defect report.

Example:

### Expected Result

> User is successfully logged in and redirected to the dashboard.

### Actual Result

> The system displays "Invalid email or password" and the user remains on the Login page.

This gives the developer a clear description of the difference between the required and observed behavior.

The relationship is:

```text
Test Case
   ↓
Expected Result
   ↓
Execute
   ↓
Actual Result
   ↓
Expected ≠ Actual
   ↓
Fail
   ↓
Investigate
   ↓
Bug Report (if defect is confirmed)
```

---

# Example: Easy Buy Login

Our practical project provides a good example.

### Test Case

```text
TC_LOGIN_001
Verify that a registered user can log in with valid credentials.
```

### Expected Result

> The user is successfully logged in and redirected to the dashboard.

### Actual Result

> The system displays "Invalid email or password" and the user remains on the Login page.

### Status

> Fail

### Related Defect

```text
BUG-LOGIN-001
Login rejects valid credentials and keeps registered user on the Login page.
```

This demonstrates how test execution connects directly to defect reporting.

---

# Expected Results and Negative Testing

Expected behavior isn't always a successful business action.

For negative tests, the expected result may be that the system **rejects** an invalid input.

Example:

### Test

> User enters an invalid email format.

### Expected Result

> The system displays an email validation message and does not authenticate the user.

If the application correctly rejects the invalid input:

```text
Expected = Actual
        ↓
      PASS
```

So:

> **Pass does not always mean "the user successfully completed the action."**

It means:

> **The application behaved as expected.**

---

# Expected Results and Validation Testing

Consider:

> Password must contain at least 8 characters.

Test:

```text
Password: F@fgfh6
Length: 7
```

Expected:

> The system rejects the password and displays a validation message indicating that at least 8 characters are required.

Actual:

> The system rejects the password and displays the minimum-length validation message.

Result:

> **Pass**

The application successfully rejected an invalid input.

---

# Multiple Expected Conditions

Sometimes a test has more than one expected condition.

For example:

> After successful login, the user should be redirected to the dashboard and their profile name should be displayed.

The Expected Result could be:

> The user is redirected to the dashboard and the user's profile name is displayed.

During execution, suppose:

* Dashboard opens ✅
* Profile name is missing ❌

Then the overall test should be considered **Fail**, because one required condition was not satisfied.

When a test contains multiple expected conditions, make them explicit so it is clear what failed.

---

# Actual Result Should Include Useful Evidence

When appropriate, the Actual Result can reference evidence such as:

* Screenshot
* Screen recording
* Console output
* Log information
* Error message
* Network response
* Relevant application data

Example:

```t
```
