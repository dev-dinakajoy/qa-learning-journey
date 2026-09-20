# Agile, Scrum and QA

## What I learned

Today I learned how **QA works in an Agile/Scrum development team**.

Before this, I mostly imagined software development as:

```text
Developer builds
      ↓
QA tests
      ↓
Bugs are fixed
      ↓
Software is released
```

But in an Agile team, QA is involved **throughout the development process**, not just at the end.

The goal is to build and test software continuously while working closely with the rest of the team.

---

# What is Agile?

**Agile** is an approach to software development that focuses on:

* Collaboration
* Frequent feedback
* Continuous improvement
* Responding to change
* Delivering working software in small increments

Instead of trying to build the entire application at once, the team breaks the work into smaller pieces and delivers them gradually.

For example, instead of:

```text
Build entire shopping app
            ↓
Test everything
            ↓
Release
```

An Agile team might work like:

```text
Login
 ↓
Build → Test → Review

Registration
 ↓
Build → Test → Review

Shopping Cart
 ↓
Build → Test → Review

Checkout
 ↓
Build → Test → Review
```

This allows the team to get feedback earlier.

---

# What is Scrum?

**Scrum** is one framework teams can use to work in an Agile way.

Scrum organizes work into short, fixed periods called **Sprints**.

A Sprint might last:

> 1–2 weeks

The team selects a group of work to complete during the Sprint.

---

# Scrum Team

A typical Scrum team has three key accountabilities:

## Product Owner

The Product Owner focuses on the product and business needs.

They help answer:

> What should we build?

They may:

* Define product requirements
* Manage the product backlog
* Prioritize work
* Clarify acceptance criteria
* Represent customer/business needs

---

## Scrum Master

The Scrum Master helps the team use Scrum effectively.

They may:

* Facilitate Scrum events
* Help remove blockers
* Encourage collaboration
* Help the team improve its process

The Scrum Master isn't simply the team's manager.

---

## Developers

Developers build the product.

They:

* Write code
* Implement features
* Fix defects
* Perform technical work
* Collaborate with QA and other team members

---

## QA / Testers

QA helps the team ensure that the product meets its requirements and provides the expected quality.

QA may:

* Review requirements
* Ask questions
* Identify risks
* Create test scenarios
* Write test cases
* Prepare test data
* Execute tests
* Report defects
* Retest fixes
* Perform regression testing
* Perform exploratory testing
* Help verify acceptance criteria

One important thing I learned is:

> **QA is part of the team, not a gatekeeper who appears only after development.**

---

# The Product Backlog

The **Product Backlog** is a prioritized list of work that may need to be done on the product.

It can contain:

* New features
* Improvements
* Bugs
* Technical work
* Other product-related tasks

For example:

```text
Product Backlog

1. User registration
2. User login
3. Password reset
4. Product search
5. Shopping cart
6. Checkout
7. Payment
```

The Product Owner helps prioritize the backlog.

---

# User Stories

Agile teams often describe features using **user stories**.

A common format is:

```text
As a [type of user],
I want [something],
so that [reason/benefit].
```

For example:

> As a customer, I want to reset my password so that I can regain access to my account if I forget it.

This describes the feature from the user's perspective.

---

# Acceptance Criteria

User stories usually have **acceptance criteria** that describe the conditions the feature must satisfy.

For example:

### User Story

> As a user, I want to reset my password so that I can regain access to my account.

### Acceptance Criteria

```text
1. User can enter their registered email.
2. The system sends a password reset email.
3. The reset link allows the user to create a new password.
4. The reset link expires after a defined period.
5. An appropriate message is displayed for an unregistered email.
```

As a QA tester, these criteria are extremely useful.

They help me determine:

> **What exactly should I test?**

---

# QA During Sprint Planning

Before a Sprint starts, the team discusses the work they want to complete.

QA can contribute by asking questions such as:

> What happens if the email doesn't exist?

> What is the minimum password length?

> What happens when the reset link expires?

> What browsers/devices are supported?

> What should happen if the email service is unavailable?

These questions can expose gaps in requirements before development starts.

---

# QA During Development

While developers are working, QA doesn't necessarily sit and wait.

I can prepare:

* Test scenarios
* Test cases
* Test data
* Test environments
* Risk areas
* Exploratory testing ideas

For example, if the team is building registration, I can already think about:

```text
Valid registration
Invalid email
Existing email
Empty fields
Weak password
Maximum input length
Special characters
Duplicate submission
```

Then I'm ready when the feature becomes available.

---

# QA During Testing

Once the feature is available in the test environment, QA executes the planned tests.

For example:

```text
User Story: Registration

TC001 → Register with valid details
TC002 → Register with existing email
TC003 → Register with invalid email
TC004 → Register with empty fields
TC005 → Register with invalid password
```

If a test fails because of a defect, I create a bug report.

---

# QA and Developers Working Together

Suppose I find a bug.

Instead of simply creating a ticket and walking away, I can communicate with the developer.

For example:

> "I found an issue with registration. When I use a valid email and leave the password empty, the form submits instead of displaying the required-field validation. I've added the reproduction steps and a screen recording."

The developer can investigate and fix it.

After the fix:

> QA retests.

If it passes:

> Close the defect.

If it fails:

> Reopen the defect.

---

# Scrum Events

Scrum has several important events.

## Sprint Planning

The team decides:

> What work will we focus on during this Sprint?

QA participates by helping understand the testing requirements, risks, and effort.

---

## Daily Scrum

This is a short daily synchronization meeting.

Team members usually discuss:

* What they worked on
* What they're working on
* Any blockers

As a QA tester, I might say:

> "Yesterday I tested the registration feature and reported two defects. Today I'll retest the fixes and continue testing password reset. My blocker is that the QA environment is currently unavailable."

Keep it short and relevant.

---

## Sprint Review

At the end of the Sprint, the team demonstrates completed work to stakeholders.

QA can help ensure that the demonstrated features meet the agreed requirements.

---

## Sprint Retrospective

The team reflects on the Sprint.

Questions might include:

> What went well?

> What didn't go well?

> What can we improve?

QA can contribute observations such as:

> "We found several bugs because the acceptance criteria weren't clear. We should clarify them during refinement before development starts."

This is one way QA contributes to **process improvement**, not just product testing.

---

# Backlog Refinement

Teams often spend time refining upcoming backlog items.

The team may:

* Clarify requirements
* Break large stories into smaller ones
* Discuss acceptance criteria
* Estimate work
* Identify risks

QA can be very valuable here.

For example:

> "The story says users can upload a profile image. What's the maximum file size?"

That question might prevent ambiguity before development begins.

---

# Definition of Done

A Scrum team may have a **Definition of Done (DoD)**.

This is a shared understanding of what it means for work to be considered complete.

For example:

```text
Definition of Done

✓ Code completed
✓ Code reviewed
✓ Unit tests passed
✓ QA testing completed
✓ Critical defects resolved
✓ Acceptance criteria satisfied
✓ Documentation updated
```

The exact Definition of Done varies by team.

The important thing is:

> **"Developer says it's coded" does not necessarily mean "the work is done."**

---

# A Complete Sprint Example

Imagine we're building a food delivery application.

The Sprint goal is:

> Allow users to place food orders.

The team selects these stories:

```text
1. Browse restaurants
2. View restaurant menu
3. Add food to cart
4. Place order
```

### Sprint Planning

QA reviews the stories and asks questions about:

* Maximum cart quantity
* Out-of-stock items
* Invalid addresses
* Payment failures
* Order confirmation

### During development

QA prepares test cases.

### Feature becomes available

QA tests:

```text
Browse restaurant
      ↓
Select food
      ↓
Add to cart
      ↓
Enter address
      ↓
Place order
```

### Bug found

> Order can be placed without a delivery address.

QA reports it.

### Developer fixes it

QA retests.

### Retest passes

QA performs relevant regression testing.

### Sprint Review

The team demonstrates the completed feature.

### Retrospective

The team discusses what went well and what could improve.

This is Agile/Scrum with QA in practice.

---

# QA Is Not Just "The Bug Finder"

One of the biggest things I'm learning is that QA isn't just:

> Find bugs → send bugs to developers.

A good QA tester contributes throughout the process.

```text
Requirements
     ↓
QA asks questions
     ↓
Planning
     ↓
QA identifies risks
     ↓
Development
     ↓
QA prepares tests
     ↓
Testing
     ↓
QA finds & reports defects
     ↓
Fixes
     ↓
QA retests
     ↓
Release
     ↓
QA helps verify quality
```

---

# What clicked for me

Before learning about Agile and Scrum, I thought QA mainly happened **after development**.

Now I understand that QA can be involved from the beginning:

> **Requirements → Planning → Development → Testing → Release → Improvement**

I also learned that QA and developers should work together rather than treating testing as a separate phase where QA simply "checks the developer's work."

---

# Key Takeaway

The main thing I want to remember is:

> **Agile is about delivering and improving software incrementally.**

> **Scrum is a framework that helps teams organize that work.**

> **QA is involved throughout the process.**

As a QA tester, my job isn't simply to find bugs.

I should:

* Ask questions
* Understand requirements
* Think about risks
* Design tests
* Test continuously
* Communicate clearly
* Verify fixes
* Help improve the team's process

Good QA is a **team responsibility**, and QA helps make that responsibility visible throughout the development process.

---

## Related

* [QA and Software Testing](01-qa-and-software-testing.md)
* [SDLC and STLC](02-sdlc-and-stlc.md)
* [Test Scenarios and Test Cases](03-test-scenarios-and-test-cases.md)
* [Bug/Defect Lifecycle](04-bug-defect-lifecycle.md)
* [Severity vs Priority](05-severity-vs-priority.md)
* [Functional vs Non-functional Testing](06-functional-vs-non-functional-testing.md)
* [Smoke, Sanity, Regression & Exploratory Testing](07-smoke-sanity-regression-exploratory.md)
