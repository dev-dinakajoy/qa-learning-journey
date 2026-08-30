# Smoke, Sanity, Regression & Exploratory Testing

## What I learned

Today I learned about four common testing approaches:

* **Smoke Testing**
* **Sanity Testing**
* **Regression Testing**
* **Exploratory Testing**

They can sound similar at first, but they answer different questions.

The simplest way I understand them is:

> **Smoke:** Is this build stable enough to test?

> **Sanity:** Does this specific change or fix work?

> **Regression:** Did the changes break anything that was already working?

> **Exploratory:** What can I discover by actively exploring the application?

---

# 1. Smoke Testing

Smoke testing is a **quick check of the major functionality** of an application or build.

The goal is to determine whether the build is stable enough for more detailed testing.

Imagine a developer gives me a new version of an e-commerce application.

Before spending hours running detailed test cases, I might check:

* Can the application open?
* Can users log in?
* Can products load?
* Can I add a product to the cart?
* Can I open the checkout page?

If these basic functions are completely broken, there's little value in continuing with detailed testing.

### Example

```text
New Build
   ↓
Smoke Test
   ↓
Basic functions work?
   ↓
Yes → Continue testing ✅
No  → Reject build ❌
```

### What I learned

Smoke testing gives me a **quick confidence check**.

It doesn't prove that the application is bug-free.

It simply answers:

> "Is this build in a reasonable state for further testing?"

---

# 2. Sanity Testing

Sanity testing is a **focused check of a specific area**, usually after a change, enhancement, or bug fix.

For example, a developer fixes a login bug.

I don't necessarily need to immediately run every test in the entire application.

I can first check:

* Can the user log in now?
* Does the fix work with valid credentials?
* Does the login area behave correctly?

If the fix works, I can continue with broader testing as needed.

### Example

```text
Login Bug
   ↓
Developer Fix
   ↓
Sanity Test
   ↓
Login works?
   ↓
Yes → Continue testing
No  → Reopen/report issue
```

### What I learned

Sanity testing is **narrower and more focused** than a broad regression test.

It helps me quickly determine whether a particular change appears to be working.

---

# 3. Regression Testing

Regression testing checks whether **existing functionality still works after changes have been made**.

This is important because fixing or adding one thing can accidentally break something else.

For example:

A developer changes the login system.

The login test passes.

But the change accidentally breaks:

* Password reset
* Registration
* Logout
* User sessions

That's where regression testing becomes important.

### Example

```text
Developer changes Login
          ↓
      Test Login
          ↓
       Pass ✅
          ↓
   Regression Testing
          ↓
 ┌────────┼─────────┐
 ↓        ↓         ↓
Reset   Logout   Registration
```

The goal is to make sure existing functionality hasn't been negatively affected.

---

# 4. Exploratory Testing

Exploratory testing is different from the previous three.

Instead of relying entirely on predefined test cases, I actively **explore the application while learning about it and looking for problems**.

The process can be thought of as:

```text
Explore
   ↓
Learn
   ↓
Think
   ↓
Test
   ↓
Observe
   ↓
Discover
```

For example, I'm testing a login page.

I might start with the normal flow:

```text
Enter email
     ↓
Enter password
     ↓
Click Login
```

Then I start exploring.

### Questions I might ask

* What if the email is empty?
* What if the password is empty?
* What if I enter spaces?
* What if I enter a very long email?
* What if I click Login multiple times?
* What if I refresh the page?
* What happens after several failed attempts?
* What happens if the internet connection disappears?
* What happens when I use the browser's Back button?
* Can I access the dashboard without logging in?

I'm not simply following a script.

I'm using **curiosity, observation, and testing knowledge** to discover unexpected behavior.

---

# Smoke vs Sanity vs Regression

These three are easy to confuse.

Here's how I remember them:

| Testing    | Main Question                                 | Scope              |
| ---------- | --------------------------------------------- | ------------------ |
| Smoke      | Is the build stable enough for testing?       | Broad but shallow  |
| Sanity     | Does this specific change/fix work?           | Narrow and focused |
| Regression | Did the changes break existing functionality? | Broader            |

### Simple example

Imagine a shopping application receives a new checkout update.

### Smoke

> Can the application open and can the main user flow work?

### Sanity

> Does the new checkout change actually work?

### Regression

> Did the checkout change break login, cart, product search, or other existing features?

---

# Smoke vs Regression

These can sometimes involve overlapping tests, but their purpose is different.

### Smoke testing

I'm asking:

> **"Is this build testable?"**

### Regression testing

I'm asking:

> **"Are previously working features still working after the changes?"**

Smoke testing is usually a **quick health check**.

Regression testing is usually **broader and deeper**, depending on the project's regression suite.

---

# Sanity vs Retesting

Another important distinction is between **sanity testing and retesting**.

### Retesting

I test the **specific defect** again to verify that the reported bug was fixed.

Example:

> Login previously failed with valid credentials.

I test that exact scenario after the fix.

### Sanity testing

I perform a focused check around the changed functionality to make sure the change appears reasonable before broader testing.

So:

> **Retesting = Verify the specific bug fix.**

> **Sanity = Quickly check the affected area/change.**

They can overlap in practice, and different teams may use these terms differently.

---

# Exploratory Testing vs Test Cases

Exploratory testing doesn't mean:

> "I don't need test cases."

Test cases and exploratory testing can work together.

For example:

```text
Test Cases
    ↓
Verify known requirements
    +
Exploratory Testing
    ↓
Discover unexpected problems
```

Test cases give me structure.

Exploratory testing gives me freedom to investigate things I didn't anticipate when writing the test cases.

---

# Example: Testing a Registration Page

Imagine I have this registration form:

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

I can use all four approaches.

### Smoke Testing

Quickly check:

* Registration page loads
* Fields are visible
* Register button works
* Basic registration flow starts

### Sanity Testing

Suppose the developer just fixed email validation.

I focus on:

* Valid email
* Invalid email
* Empty email

### Regression Testing

After the email validation change, I check other existing functionality:

* Login
* Registration
* Password reset
* Profile functionality

### Exploratory Testing

I start experimenting:

* Very long names
* Spaces
* Special characters
* Copy/paste
* Multiple clicks
* Refreshing during registration
* Browser Back button
* Unusual email formats

This gives me much broader coverage.

---

# How These Tests Fit Together

In a real project, these aren't necessarily four completely separate activities.

A possible workflow could look like:

```text
New Build
   ↓
Smoke Testing
   ↓
Build is stable
   ↓
Feature Testing
   ↓
Developer Fixes Bug
   ↓
Retesting / Sanity Testing
   ↓
Regression Testing
   ↓
Exploratory Testing
   ↓
Release
```

The exact workflow depends on the team's process.

---

# A Practical Example

Imagine a developer gives me a new build containing:

> "Users can reset their passwords."

### Step 1 — Smoke

I check that the application opens and basic functions work.

### Step 2 — Feature Testing

I test the password reset feature using test cases.

### Step 3 — Bug Found

I discover that the reset link doesn't work.

I report the defect.

### Step 4 — Fix

The developer fixes it.

### Step 5 — Retest

I test the exact password reset scenario again.

### Step 6 — Sanity

I check the password reset functionality more broadly.

### Step 7 — Regression

I verify that the changes didn't break login or other authentication functionality.

### Step 8 — Exploratory

I explore unusual scenarios that weren't covered by my predefined test cases.

That's how these concepts can work together.

---

# What clicked for me

I initially thought these testing terms were just different names for the same thing.

Now I understand that they have **different purposes and scopes**.

The biggest distinction for me is:

```text
Smoke
"Can I test this build?"

Sanity
"Does this change look okay?"

Regression
"Did the change break something else?"

Exploratory
"What can I discover?"
```

---

# Key Takeaway

The four concepts I want to remember are:

> **Smoke → Build health**

> **Sanity → Specific change**

> **Regression → Existing functionality**

> **Exploratory → Discovery**

Good QA isn't just about following test cases.

I need to know **when to use structured testing and when to explore beyond what I already planned to test.**

---

## Related

* [QA and Software Testing](01-qa-and-software-testing.md)
* [SDLC and STLC](02-sdlc-and-stlc.md)
* [Test Scenarios and Test Cases](03-test-scenarios-and-test-cases.md)
* [Bug/Defect Lifecycle](04-bug-defect-lifecycle.md)
* [Severity vs Priority](05-severity-vs-priority.md)
* [Functional vs Non-functional Testing](06-functional-vs-non-functional-testing.md)
* [Agile/Scrum and QA](08-agile-scrum-and-qa.md)
