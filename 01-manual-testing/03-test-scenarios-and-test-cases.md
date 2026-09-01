# Test Scenarios and Test Cases

## What I learned

Today I learned about **test scenarios** and **test cases**.
They are both used to make sure we test the right things, but they are not the same.
The simplest way I understand the difference is:
> **Test Scenario = What to test**

> **Test Case = How to test it**

---

# Test Scenario

A **test scenario** is a high-level description of something that needs to be tested.
It focuses on **what functionality or behavior** we want to verify.
For example, if I'm testing a login page:

```text
Test Scenario:
Verify that users can log in.
```

From this one scenario, I can create several test cases.

### Login test scenarios

* Verify login with valid credentials
* Verify login with an invalid password
* Verify login with an invalid email
* Verify login with empty fields
* Verify login with an invalid email format
* Verify login with a locked account

A scenario gives me the **testing direction** without going into detailed steps.

---

# Test Case

A **test case** is a detailed set of steps used to verify a specific behavior.

A test case normally contains:

* Test case ID
* Test case title
* Preconditions
* Test data
* Steps
* Expected result
* Actual result
* Status

For example:

### TC001 — Login with valid credentials

**Precondition:**

A registered user account exists.

**Test data:**

```text
Email: user@example.com
Password: Password123
```

**Steps:**

1. Open the login page.
2. Enter the registered email.
3. Enter the correct password.
4. Click **Login**.

**Expected result:**

The user should be successfully logged in and redirected to the dashboard.

**Actual result:**

The user is redirected to the dashboard.

**Status:**

Passed ✅

---

# Test Scenario vs Test Case

Here's the difference in a simple table:

| Test Scenario                   | Test Case                  |
| ------------------------------- | -------------------------- |
| High-level                      | Detailed                   |
| Describes what to test          | Describes how to test      |
| Usually shorter                 | Contains specific steps    |
| Can produce multiple test cases | Tests a specific condition |
| Focuses on functionality        | Focuses on verification    |

### Example

**Scenario:**

> Verify the login functionality.

**Test cases:**

```text
TC001 → Login with valid credentials
TC002 → Login with invalid password
TC003 → Login with invalid email
TC004 → Login with empty email
TC005 → Login with empty password
TC006 → Login with both fields empty
```

One scenario can therefore have many test cases.

---

# Positive Testing

When writing test cases, I should test valid input and expected behavior.

For example:

```text
Email: user@example.com
Password: Password123
```

Expected:

> Login succeeds.

This is **positive testing**.

The goal is to verify that the application works correctly when valid data is provided.

---

# Negative Testing

I also need to test invalid or unexpected input.

For example:

```text
Email: user@example.com
Password:
```

Expected:

> The application displays a validation message.

Other examples:

* Invalid email
* Wrong password
* Empty fields
* Very long input
* Unsupported characters
* Invalid data

This is **negative testing**.

A good tester doesn't only check:

> "Can I make it work?"

I should also ask:

> "What happens when I use it incorrectly?"

---

# Test Case Example: Registration

Imagine I'm testing a registration form:

```text
--------------------------------
        Create Account
--------------------------------

Name:     [____________]

Email:    [____________]

Password: [____________]

          [ Register ]
--------------------------------
```

Possible test scenarios:

### Scenario 1

Verify user registration with valid information.

### Scenario 2

Verify registration with an existing email.

### Scenario 3

Verify registration with an invalid email.

### Scenario 4

Verify registration with empty required fields.

### Scenario 5

Verify password validation.

From these scenarios, I can create detailed test cases.

---

# Example Test Cases

| ID    | Test Case                                     | Expected Result                 |
| ----- | --------------------------------------------- | ------------------------------- |
| TC001 | Register with valid information               | Account is created              |
| TC002 | Register with existing email                  | Error message is displayed      |
| TC003 | Register with invalid email                   | Validation message is displayed |
| TC004 | Register without a name                       | Validation message is displayed |
| TC005 | Register without an email                     | Validation message is displayed |
| TC006 | Register without a password                   | Validation message is displayed |
| TC007 | Register with a password below minimum length | Validation message is displayed |

---

# What Makes a Good Test Case?

A good test case should be:

### Clear

Another tester should understand what I'm trying to test.

### Specific

The steps shouldn't be vague.

Instead of:

> Test login.

Write:

> Enter a registered email and valid password, then click Login.

### Reproducible

Another tester should be able to follow the same steps and get the same result.

### Traceable

The test case should ideally relate back to a requirement or user story.

### Independent

Where possible, a test case shouldn't unnecessarily depend on another test case.

---

# Test Case Template

This is a basic template I can use for my practice:

```text
Test Case ID:
Title:

Precondition:

Test Data:

Steps:
1.
2.
3.

Expected Result:

Actual Result:

Status:
```

For larger projects, test management tools can provide additional fields.

---

# What I Should Test

When creating test cases, I shouldn't only test the **happy path**.

I should think about different categories.

### 1. Valid input

What happens when the user does everything correctly?

### 2. Invalid input

What happens when the user provides incorrect information?

### 3. Empty input

What happens when required fields are left empty?

### 4. Boundary values

What happens at the minimum and maximum allowed values?

### 5. Unexpected behavior

What happens if the user does something unusual?

### 6. Usability

Can the user understand what to do?

### 7. Error handling

Does the application give a useful response when something goes wrong?

---

# Example: Password Field

Suppose the requirement says:

> Password must be between 8 and 20 characters.

I shouldn't only test a 10-character password.

I should think about the boundaries:

```text
7 characters  → Invalid
8 characters  → Valid
9 characters  → Valid
19 characters → Valid
20 characters → Valid
21 characters → Invalid
```

This introduces me to **Boundary Value Analysis**, which I'll learn in more detail later.

---

# Test Scenario → Test Case → Test Result

I can think about the process like this:

```text
Requirement
     ↓
Test Scenario
     ↓
Test Case
     ↓
Execute Test
     ↓
Pass / Fail
     ↓
Bug Report (if failed)
```

For example:

```text
Requirement:
Users should be able to log in.

        ↓

Scenario:
Verify login functionality.

        ↓

Test Case:
Login with valid credentials.

        ↓

Expected:
User reaches dashboard.

        ↓

Actual:
Error message appears.

        ↓

Result:
FAILED ❌

        ↓

Bug Report
```

This connects the things I've learned so far.

---

# What clicked for me

I initially thought writing test cases was simply writing down a list of things to click.

Now I understand that **test cases should be based on requirements and should deliberately cover different conditions**.

The goal isn't to create as many test cases as possible.

The goal is to create **useful test cases that provide good coverage and help discover defects.**

---

# Key Takeaway

The simplest distinction I want to remember is:

> **Scenario = What am I testing?**

> **Test Case = How am I testing it?**

And a good QA tester doesn't just test what should work.

I should also think about:

> **What happens when things go wrong?**

---

## 🔗 Related

* [QA and Software Testing](01-qa-and-software-testing.md)
* [SDLC and STLC](02-sdlc-and-stlc.md)
* [Bug/Defect Lifecycle](04-bug-defect-lifecycle.md)
