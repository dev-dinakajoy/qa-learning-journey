# Bug / Defect Lifecycle

## What I learned

Today I learned about the **bug/defect lifecycle** — the different stages a defect goes through from the moment a QA tester discovers it until it is resolved.

Finding a bug is only part of the job.

As a QA tester, I also need to:

* Report it clearly
* Track its progress
* Retest the fix
* Confirm whether it is resolved
* Reopen it if the problem still exists

A simple defect lifecycle looks like this:

```text
New
 ↓
Assigned
 ↓
In Progress
 ↓
Fixed
 ↓
Retest
 ↓
Closed
```

But a defect can take different paths depending on what happens.

---

# What is a Bug?

A **bug** is a problem or unexpected behavior in software that causes the application to behave differently from what is expected.

For example:

**Expected:**

> Clicking "Login" with valid credentials should take the user to the dashboard.

**Actual:**

> Clicking "Login" displays "Invalid password" even though the password is correct.

That's a bug.

The terms **bug**, **defect**, and **issue** are often used interchangeably in everyday QA work, although organizations may define them slightly differently.

---

# The Defect Lifecycle

## 1. New

The tester discovers a problem and creates a defect report.

At this stage, the bug is **New**.

A good report should contain enough information for someone else to reproduce the problem.

For example:

```text
Title:
Login fails with valid credentials

Steps:
1. Open login page
2. Enter valid email
3. Enter valid password
4. Click Login

Expected:
User is redirected to the dashboard.

Actual:
"Invalid password" is displayed.
```

---

# 2. Assigned

The defect is reviewed and assigned to a developer or appropriate team member.

The developer now knows:

> "This is the issue I need to investigate."

---

# 3. In Progress

The developer starts investigating the defect.

They may:

* Reproduce the problem
* Find the root cause
* Modify the code
* Run their own tests
* Prepare a fix

The defect is now **In Progress**.

---

# 4. Fixed

The developer believes the defect has been fixed.

However, **Fixed does not automatically mean the bug is gone.**

This is where QA comes back in.

The developer may say:

> "I've fixed BUG-001. Please retest."

QA should test the exact scenario again.

---

# 5. Retest

QA verifies whether the reported problem has actually been fixed.

For example:

**Before the fix:**

```text
Valid credentials
      ↓
"Invalid password" ❌
```

**After the fix:**

```text
Valid credentials
      ↓
Dashboard ✅
```

If the problem is fixed, the defect can move toward **Closed**.

If the problem still exists, it may be **Reopened**.

---

# 6. Closed

If QA confirms that the defect has been successfully fixed, the defect can be marked **Closed**.

```text
Fixed
  ↓
Retested
  ↓
Passed
  ↓
Closed ✅
```

---

# 7. Reopened

What happens if QA retests the bug and it still exists?

The tester can **reopen** it.

```text
Fixed
  ↓
Retest
  ↓
Still failing ❌
  ↓
Reopened
  ↓
Developer investigates again
```

This is why QA shouldn't simply trust:

> "It's fixed."

The tester needs to verify it.

---

# Other Possible Defect States

Not every defect follows the exact same path.

Depending on the team or tool, you might see states such as:

### Rejected

The team determines that the reported issue isn't actually a defect.

For example, the behavior might be intentional.

```text
New → Rejected
```

### Duplicate

Someone has already reported the same defect.

```text
New → Duplicate
```

Instead of keeping two separate reports, the team links the new report to the existing one.

### Deferred

The team agrees that the defect is valid but decides not to fix it immediately.

For example:

> The bug is low priority and will be fixed in a future release.

### Cannot Reproduce

The developer or QA team cannot reproduce the reported behavior.

This can happen when:

* Steps are incomplete
* The environment is different
* The issue is intermittent
* Required test data is missing

In this situation, QA may need to provide more information.

---

# A More Complete Lifecycle

A real project might look like:

```text
             ┌───────────┐
             │    New    │
             └─────┬─────┘
                   ↓
             ┌───────────┐
             │ Assigned  │
             └─────┬─────┘
                   ↓
             ┌─────────────┐
             │ In Progress │
             └──────┬──────┘
                    ↓
               ┌─────────┐
               │  Fixed  │
               └────┬────┘
                    ↓
               ┌─────────┐
               │ Retest  │
               └────┬────┘
                    ↓
             ┌──────────────┐
             │   Passed?   │
             └──────┬───────┘
                Yes │ No
                    │  └────────→ Reopened
                    ↓
                Closed
```

Other paths such as **Rejected, Duplicate, Deferred,** or **Cannot Reproduce** can happen along the way.

---

# Bug Report Example

Suppose I'm testing a registration page.

I discover that users can register without entering an email address.

I could report it like this:

```text
Bug ID:
BUG-001

Title:
User can register without providing an email address

Environment:
QA environment
Chrome browser

Precondition:
Registration page is accessible.

Steps:
1. Open the registration page.
2. Enter a valid name.
3. Leave the email field empty.
4. Enter a valid password.
5. Click Register.

Expected Result:
The application should display a validation message
and prevent registration.

Actual Result:
The account is created without an email address.

Severity:
High

Priority:
High

Status:
New
```

This is much more useful than:

> "Registration has a bug."

---

# Retesting vs Regression Testing

One thing I need to understand clearly is that **retesting and regression testing are different**.

### Retesting

I test the **specific bug that was fixed**.

Example:

> Developer fixes login failure.

I test the login failure again.

### Regression Testing

I check **other existing functionality** to make sure the fix didn't break something else.

For example:

```text
Developer changes Login
       ↓
Retest Login
       ↓
Login works
       ↓
Regression Testing
       ↓
Check Registration
Check Password Reset
Check Logout
Check Dashboard
```

So:

> **Retesting = Did the bug get fixed?**

> **Regression testing = Did the fix break anything else?**

---

# What Makes a Good Bug Report?

A good bug report should be:

### Clear

Someone should understand the problem quickly.

### Reproducible

Another person should be able to follow the steps and experience the same issue.

### Specific

Avoid vague descriptions like:

> "It doesn't work."

Explain exactly what happened.

### Evidence-based

When possible, include:

* Screenshots
* Screen recordings
* Error messages
* Logs
* Relevant test data

### Traceable

Give the defect a unique ID so the team can easily discuss and track it.

---

# What clicked for me

I initially thought finding a bug meant the testing work was finished.

Now I understand that finding the bug is only the beginning.

A QA tester needs to **communicate, track, verify, and close the loop**.

I also learned that when a developer says:

> "Fixed."

That doesn't mean I should immediately close the ticket.

I need to **retest it myself**.

---

# Key Takeaway

The defect lifecycle is the journey a bug takes from discovery to resolution.

The basic flow I want to remember is:

```text
New
 ↓
Assigned
 ↓
In Progress
 ↓
Fixed
 ↓
Retest
 ↓
Closed
```

And if the fix doesn't work:

```text
Retest
   ↓
Still failing
   ↓
Reopened
```

A QA tester doesn't just **find bugs**.

A QA tester helps the team **understand, track, verify, and prevent defects.**

---

## Related

* [QA and Software Testing](01-qa-and-software-testing.md)
* [SDLC and STLC](02-sdlc-and-stlc.md)
* [Test Scenarios and Test Cases](03-test-scenarios-and-test-cases.md)
* [Severity vs Priority](05-severity-vs-priority.md)
