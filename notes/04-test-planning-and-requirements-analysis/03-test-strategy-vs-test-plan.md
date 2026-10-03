# Test Strategy vs Test Plan

## What is a Test Strategy?

A Test Strategy is a high-level document that describes the **overall approach to testing**.

It defines how an organization or project intends to achieve its testing objectives.

It can cover areas such as:

* Testing approach
* Testing levels
* Testing types
* Automation strategy
* Risk management
* Tools
* Environments
* Quality objectives

A Test Strategy is generally more high-level than a Test Plan.

---

## What is a Test Plan?

A Test Plan describes the **specific testing activities for a particular project, release, feature, or testing effort**.

It is more detailed and operational.

It may include:

* Scope
* Objectives
* Features to test
* Features not to test
* Test environment
* Test data
* Schedule
* Roles
* Entry criteria
* Exit criteria
* Risks
* Deliverables

---

## Test Strategy vs Test Plan

| Test Strategy                        | Test Plan                                               |
| ------------------------------------ | ------------------------------------------------------- |
| High-level                           | More detailed                                           |
| Defines overall approach             | Defines specific testing activities                     |
| May apply across projects            | Usually applies to a project/release/feature            |
| Focuses on how testing is approached | Focuses on what, when, who, and how testing will happen |
| Usually less frequently changed      | Can change as project conditions change                 |

---

## Example

### Test Strategy

> All critical applications must use risk-based testing, automated regression testing, API testing, and security testing.

This describes a **general testing approach**.

### Test Plan

> For the January release, QA will test login, transfers, account balance, and transaction history from January 5–15 using the QA environment and Chrome/Firefox.

This describes the **specific testing effort**.

---

## Test Policy

A Test Policy is even more organizational and high-level.

It can define the organization's overall expectations and principles around software quality and testing.

A simplified hierarchy is:

```text
Test Policy
     ↓
Test Strategy
     ↓
Test Plan
     ↓
Test Scenarios
     ↓
Test Cases
     ↓
Test Execution
```

The exact terminology and document structure can vary between organizations.

---

## Key Takeaway

Think of the difference as:

**Test Policy:** What does the organization expect regarding testing?

**Test Strategy:** What is our overall approach to testing?

**Test Plan:** How will we test this particular project/release?

**Test Cases:** How exactly will we execute individual tests?
