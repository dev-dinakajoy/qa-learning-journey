# Writing High-Quality Bug Reports

A QA tester does more than find defects.

A good QA tester also needs to **communicate defects clearly enough for the development team to understand, reproduce, investigate, and fix them**.

A **bug report** is a documented description of unexpected software behavior.

A high-quality bug report should answer:

> **What is wrong?**

> **Where does it happen?**

> **How can someone reproduce it?**

> **What should happen?**

> **What actually happens?**

> **How serious or urgent is it?**

---

# 1. What Is a Bug Report?

A **bug report** is a structured record of a software defect or unexpected behavior.

For example:

```text
BUG-LOGIN-001

Title:
Login rejects valid credentials and keeps the user on the Login page.

Expected:
The user should be logged in and redirected to the dashboard.

Actual:
The system displays "Invalid email or password" and keeps the user on the Login page.
```

A developer reading this should be able to understand the problem and attempt to reproduce it.

---

# 2. Why Bug Reports Matter

A poor bug report can create unnecessary back-and-forth between QA and developers.

For example:

> Login is broken.

A developer may ask:

* Which login?
* Which environment?
* Which account?
* What did you enter?
* What happened?
* What should have happened?
* Can you reproduce it?
* What browser were you using?

A better report provides these details from the beginning.

Good bug reports help teams:

* Reproduce defects
* Understand expected behavior
* Understand actual behavior
* Investigate causes
* Prioritize work
* Track fixes
* Retest fixes
* Maintain a history of defects

---

# 3. Basic Bug Report Structure

A typical manual QA bug report can contain:

1. Bug ID
2. Title / Summary
3. Environment
4. Preconditions
5. Test Data
6. Steps to Reproduce
7. Expected Result
8. Actual Result
9. Severity
10. Priority
11. Reproducibility
12. Related Test Case
13. Evidence
14. Additional Notes

Different companies and bug-tracking tools may use different fields.

The exact structure is less important than providing enough useful information.

---

# 4. Bug ID

The **Bug ID** uniquely identifies the defect.

Examples:

```text
BUG-LOGIN-001
BUG-SEARCH-001
BUG-CART-002
BUG-CHECKOUT-003
```

The ID allows team members to refer to a specific defect.

For example:

> "Please check BUG-LOGIN-001."

is much clearer than:

> "Please check that login issue."

---

# 5. Bug Title

The title should summarize the defect clearly and concisely.

A useful bug title often follows this pattern:

```text
[Feature] + [Problem] + [Condition]
```

### Weak

> Login broken

### Better

> Login fails with valid credentials

### Stronger

> Login rejects valid credentials and keeps the user on the Login page

The stronger title tells us:

* Feature: Login
* Problem: Valid credentials are rejected
* Result: User remains on Login page

---

# 6. What Makes a Good Bug Title?

A good title should be:

* Specific
* Concise
* Objective
* Reproducible
* Easy to understand

Avoid emotional or subjective language.

### Avoid

> Terrible login bug!!!

### Prefer

> Login rejects valid credentials for registered users

Avoid conclusions that have not been established.

### Avoid

> Database authentication query is broken

Unless you have evidence that the database query is actually the cause.

Prefer describing the observable behavior:

> Login rejects valid credentials and displays an authentication error

---

# 7. Environment

The **Environment** describes where the defect was observed.

It may include:

* Environment name
* Browser
* Browser version
* Operating system
* Device
* Application version/build
* Relevant configuration

Example:

```text
Environment:
QA
Chrome 154
macOS
Desktop
```

For mobile testing:

```text
Environment:
QA
Chrome
Android 15
Pixel device
```

The exact information required depends on the project.

---

# 8. Preconditions

The **Preconditions** describe what must be true before reproducing the defect.

Example:

```text
Precondition:
A registered user account exists with valid credentials.
```

For a search defect:

```text
Precondition:
The Products page is accessible and at least one product matching the search keyword exists.
```

For a cart defect:

```text
Precondition:
The user is logged in and a product is available.
```

Clear preconditions make reproduction easier.

---

# 9. Test Data

The **Test Data** identifies the data used when the defect occurred.

Example:

```text
Email: user1@test.com
Password: <test account password>
```

For search:

```text
Keyword: phone
```

For cart:

```text
Product: Smartphone X
Quantity: 2
```

### Important

Never expose real user passwords, payment information, API keys, or other sensitive credentials in public bug reports.

Use dedicated test accounts and safe test data.

---

# 10. Steps to Reproduce

The **Steps to Reproduce** explain exactly how another person can reproduce the defect.

Good steps are:

* Sequential
* Specific
* Easy to follow
* Reproducible

Example:

```text
1. Open the Login page.
2. Enter a registered email address.
3. Enter the correct password.
4. Click Login.
```

Another tester or developer should be able to follow these steps without guessing.

---

# 11. Poor vs Good Reproduction Steps

### Poor

> Try logging in and see what happens.

Too vague.

### Better

```text
1. Open the Login page.
2. Enter user1@test.com.
3. Enter the correct test password.
4. Click Login.
```

The second version provides a reproducible procedure.

---

# 12. Expected Result

The Expected Result describes what should have happened.

Example:

> The user is successfully logged in and redirected to the dashboard.

The Expected Result should normally come from:

* Requirement
* Acceptance criteria
* Product specification
* Approved business behavior
* Established application behavior

---

# 13. Actual Result

The Actual Result describes what actually happened.

Example:

> The system displays "Invalid email or password" and the user remains on the Login page.

The Actual Result should be factual and observable.

Avoid unsupported assumptions.

### Avoid

> The backend authentication service is broken.

### Prefer

> The application displays "Invalid email or password" even though valid credentials were provided.

The second statement describes what the tester actually observed.

---

# 14. Expected vs Actual in a Bug Report

A useful bug report makes the difference obvious.

```text
Expected:
User is logged in and redirected to the dashboard.

Actual:
User remains on the Login page and receives
an "Invalid email or password" message.
```

This difference is the core of many defect reports.

---

# 15. Severity

**Severity** describes the impact of the defect on the system, functionality, users, or business.

A project may define its own severity levels.

A simple example:

### Critical

The defect causes a severe system or business impact.

Examples may include:

* Application completely unavailable
* Major data loss
* Critical security failure
* Core functionality completely unusable

### High

The defect seriously affects important functionality.

Examples:

* Users cannot complete a major business operation
* Important functionality is unusable
* A major workflow is significantly affected

### Medium

The defect affects functionality but has a workaround or limited impact.

Examples:

* A secondary feature does not work
* Some functionality behaves incorrectly but core operations remain available

### Low

The defect has relatively limited impact.

Examples:

* Minor visual issue
* Small text or alignment problem
* Non-critical UI inconsistency

The exact definitions should always follow the team's agreed severity matrix.

---

# 16. Priority

**Priority** describes how urgently the team should address the defect.

A simple scale might be:

* High
* Medium
* Low

For example, a defect affecting a heavily used workflow may receive high priority even if its technical impact is moderate.

Priority can be influenced by:

* Release deadlines
* Business importance
* Number of affected users
* Customer impact
* Frequency of occurrence
* Workaround availability
* Regulatory or contractual requirements

Severity and priority are related, but they are **not the same thing**.

---

# 17. Severity vs Priority

Remember:

```text
Severity
    ↓
How much does the defect impact the system or users?

Priority
    ↓
How urgently should the team address it?
```

Example:

### Defect A

A spelling mistake appears on the checkout page.

Possible classification:

```text
Severity: Low
Priority: High
```

Why might priority be high?

Because the text could be customer-facing and need correction before a release.

### Defect B

A rarely used administrative feature has a significant technical problem.

Possible classification:

```text
Severity: High
Priority: Medium
```

The exact classification depends on the project's agreed criteria.

Do not assume that:

> High severity = High priority

They can be different.

---

# 18. Reproducibility

**Reproducibility** indicates how consistently the defect can be reproduced.

Example:

```text
Reproducibility:
5/5 attempts
```

This means the tester reproduced the problem five times out of five attempts.

Other examples:

```text
Always
Frequently
Intermittently
Once
Unable to reproduce
```

A defect that occurs intermittently may require additional information such as:

* Time of occurrence
* Network conditions
* Browser/device
* User actions
* Logs
* Screen recording

---

# 19. Related Test Case

Linking a bug to the test case that exposed it provides traceability.

Example:

```text
Related Test Case:
TC_LOGIN_001
```

This creates a relationship:

```text
Requirement
    ↓
Test Case
    ↓
Failed Execution
    ↓
Bug
```

For example:

```text
R1
 ↓
TC_LOGIN_001
 ↓
Fail
 ↓
BUG-LOGIN-001
```

This is useful for both defect tracking and the Requirements Traceability Matrix.

---

# 20. Evidence

Evidence can help demonstrate and reproduce a defect.

Examples:

* Screenshot
* Screen recording
* Console log
* Network information
* Error message
* Application log
* Relevant API response

Example:

```text
Evidence:
Screenshot attached showing the authentication error.
```

Evidence should support the defect rather than replace the written description.

---

# 21. Complete Bug Report Example

Let's use the Easy Buy login defect we previously practiced.

```text
Bug ID:
BUG-LOGIN-001

Title:
Login rejects valid credentials and keeps the registered user on the Login page.

Environment:
QA
Chrome 154
macOS
Desktop

Precondition:
A registered user account exists with valid credentials.

Test Data:
Email: user1@test.com
Password: <test account password>

Steps to Reproduce:
1. Open the Login page.
2. Enter the registered email address.
3. Enter the correct password.
4. Click Login.

Expected Result:
The user is successfully logged in and redirected to the dashboard.

Actual Result:
The system displays "Invalid email or password" and the user remains on the Login page.

Severity:
Critical

Priority:
High

Reproducibility:
5/5 attempts

Related Test Case:
TC_LOGIN_001

Evidence:
Screenshot attached.

Notes:
The issue occurs consistently with valid test credentials.
```

This is a much more useful report than:

> Login doesn't work.

---

# 22. Another Example — Product Search

Consider this defect:

### Test Case

```text
TC_SEARCH_001

Verify that users can search for products using valid keywords.
```

### Expected

> Products matching the keyword are displayed.

### Actual

> No products are displayed even though matching products exist.

A bug report could be:

```text
Bug ID:
BUG-SEARCH-001

Title:
Product search returns no results for a valid keyword.

Environment:
QA
Chrome 154
macOS
Desktop

Precondition:
The Products page is accessible and products matching the search keyword exist.

Test Data:
Keyword: phone

Steps to Reproduce:
1. Open the Products page.
2. Enter "phone" in the search field.
3. Click Search.

Expected Result:
Products matching "phone" are displayed.

Actual Result:
No products are displayed and no error message appears.

Severity:
High

Priority:
Medium

Reproducibility:
5/5 attempts

Related Test Case:
TC_SEARCH_001

Evidence:
Screenshot attached.
```

Notice that the report describes **what happened** rather than guessing why it happened.

---

# 23. Bug Lifecycle

After a bug is reported, it normally moves through different states.

A simplified lifecycle is:

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

There can also be other states depending on the team's workflow:

```text
Rejected
Duplicate
Deferred
Reopened
Cannot Reproduce
Won't Fix
```

Different organizations may use different names and transitions.

---

# 24. Re-testing a Fixed Bug

Suppose `BUG-LOGIN-001` is marked as fixed.

QA should re-execute the test that originally exposed the issue.

Original:

```text
TC_LOGIN_001
Status: Fail
```

After the fix:

```text
Expected:
User is successfully logged in and redirected to dashboard.

Actual:
User is successfully logged in and redirected to dashboard.

Status:
Pass
```

The bug can then be moved to the appropriate verification/closed state according to the team's workflow.

---

# 25. Reopened Bugs

A bug may be reopened if the defect still exists after the fix.

Example:

```text
Bug:
BUG-LOGIN-001

Developer:
Fixed

QA Retest:
Login still rejects valid credentials.

Result:
Fail

Bug Status:
Reopened
```

This is why retesting is important.

---

# 26. Common Bug Reporting Mistakes

## Mistake 1 — Vague title

```text
Login issue
```

Better:

```text
Login rejects valid credentials and keeps the user on the Login page
```

---

## Mistake 2 — Missing steps

```text
Search doesn't work.
```

A developer cannot reliably reproduce the issue.

Include the exact steps.

---

## Mistake 3 — Missing expected result

Without an Expected Result, it may be unclear why the behavior is considered incorrect.

---

## Mistake 4 — Missing actual result

The report needs to explain what actually happened.

---

## Mistake 5 — Mixing assumptions with observations

Avoid:

> The database is broken.

Unless you have evidence.

Prefer:

> Search returns no results when matching products are available.

---

## Mistake 6 — Combining unrelated defects

Don't create one report such as:

> Login, search, cart, and checkout are all broken.

Create separate bug reports when the defects are independent.

For example:

```text
BUG-LOGIN-001
BUG-SEARCH-001
BUG-CART-001
BUG-CHECKOUT-001
```

This makes tracking and fixing easier.

---

## Mistake 7 — Including sensitive information

Never put real passwords, payment card numbers, API keys, or other sensitive information into bug reports.

Use safe test data.

---

# 27. Bug Report Quality Checklist

Before submitting a bug report, check:

### Title

* [ ] Is the title specific?
* [ ] Does it describe the actual problem?
* [ ] Is it concise?

### Environment

* [ ] Is the environment identified?
* [ ] Is the browser/device included where relevant?
* [ ] Is the application version/build included where relevant?

### Reproduction

* [ ] Are the preconditions clear?
* [ ] Is the test data provided?
* [ ] Are the steps reproducible?

### Results

* [ ] Is the Expected Result clear?
* [ ] Is the Actual Result clear?
* [ ] Are observations separated from assumptions?

### Classification

* [ ] Is Severity assigned according to project definitions?
* [ ] Is Priority assigned according to project rules?
* [ ] Is reproducibility documented?

### Traceability

* [ ] Is the related test case included?
* [ ] Is the related requirement included where useful?

### Evidence

* [ ] Is relevant evidence attached?
* [ ] Does the evidence support the reported behavior?

### Security

* [ ] Is sensitive information excluded?

---

# 28. The QA Bug Reporting Flow

The complete process can be visualized as:

```text
Execute Test Case
       ↓
Compare Expected vs Actual
       ↓
Unexpected Result?
       ↓
     Yes
       ↓
Investigate
       ↓
Confirm Defect
       ↓
Write Bug Report
       ↓
Assign Severity/Priority
       ↓
Attach Evidence
       ↓
Submit / Assign
       ↓
Developer Investigates
       ↓
Fix Implemented
       ↓
QA Retests
       ↓
┌───────────────┐
│               │
Pass           Fail
│               │
↓               ↓
Verify/Close   Reopen
```

---

# 29. Key Takeaways

A high-quality bug report should be:

* **Clear** — easy to understand.
* **Specific** — describes the exact problem.
* **Reproducible** — provides steps that others can follow.
* **Objective** — focuses on observable behavior.
* **Traceable** — connects to test cases and requirements.
* **Actionable** — provides enough information for investigation.

The most important structure to remember is:

```text
Bug ID
   ↓
Title
   ↓
Environment
   ↓
Precondition
   ↓
Test Data
   ↓
Steps to Reproduce
   ↓
Expected Result
   ↓
Actual Result
   ↓
Severity / Priority
   ↓
Reproducibility
   ↓
Related Test Case
   ↓
Evidence
```

A strong QA tester doesn't simply say:

> **"I found a bug."**

A strong QA tester provides enough information for the team to understand:

> **"Here is exactly what I tested, what should have happened, what actually happened, and how you can reproduce it."**
