# SDLC and STLC

## What I learned

Today I learned about two important concepts in software testing:

* **SDLC — Software Development Life Cycle**
* **STLC — Software Testing Life Cycle**

Understanding both helps me know **where QA fits into the software development process**.

---

## SDLC — Software Development Life Cycle

SDLC is the process a software product goes through from an initial idea to development, release, and maintenance.

A simplified SDLC looks like this:

```text
Requirements
     ↓
Design
     ↓
Development
     ↓
Testing
     ↓
Deployment
     ↓
Maintenance
```

### 1. Requirements

The team defines what the software should do.

For example:

> Users should be able to create an account using their email and password.

As a QA tester, I can review the requirements and ask questions like:

* What makes an email valid?
* What is the minimum password length?
* What happens if the email already exists?
* What happens when required fields are empty?

Finding unclear requirements early can prevent bugs later.

### 2. Design

The team decides how the application will look and work.

This can include:

* User interface design
* System architecture
* Database design
* User flows

QA can review the design and identify possible usability or functional issues before development begins.

### 3. Development

Developers write the code based on the requirements and design.

QA can start preparing:

* Test scenarios
* Test cases
* Test data
* Testing approach

Testing doesn't have to wait until development is completely finished.

### 4. Testing

The developed features are tested to verify that they work as expected.

QA may:

* Execute test cases
* Perform exploratory testing
* Report bugs
* Retest fixes
* Perform regression testing

### 5. Deployment

Once the software meets the team's release criteria, it is deployed to users.

QA may perform final checks before or after deployment depending on the team's process.

### 6. Maintenance

After release, new bugs, changes, and improvements may come up.

QA continues testing new changes and making sure existing functionality isn't broken.

---

# STLC — Software Testing Life Cycle

STLC focuses specifically on the **testing activities** within the software development process.

A simplified STLC looks like this:

```text
Requirement Analysis
        ↓
Test Planning
        ↓
Test Case Design
        ↓
Test Environment Setup
        ↓
Test Execution
        ↓
Defect Reporting & Retesting
        ↓
Test Closure
```

## 1. Requirement Analysis

QA studies the requirements to understand what needs to be tested.

I should ask:

> What should the system do?

> What could go wrong?

> Are the requirements clear and testable?

---

## 2. Test Planning

The team decides how testing will be carried out.

This can include:

* What will be tested
* What won't be tested
* Testing types
* Resources
* Timeline
* Risks
* Test environment

---

## 3. Test Case Design

QA creates test cases based on the requirements.

For example, for a login feature:

```text
TC001 → Login with valid credentials
TC002 → Login with invalid password
TC003 → Login with invalid email
TC004 → Login with empty fields
```

Each test case should have clear steps and expected results.

---

## 4. Test Environment Setup

The team prepares the environment where testing will happen.

This could include:

* Application build
* Database
* Browser
* Operating system
* Test accounts
* Test data

For example:

```text
Environment: QA
Browser: Chrome
Device: Desktop
Database: Test database
```

---

## 5. Test Execution

QA executes the test cases and compares:

**Actual Result**

with

**Expected Result**

If they match:

> Test Passed ✅

If they don't:

> Test Failed ❌

When a failure is caused by a defect, QA reports it.

---

## 6. Defect Reporting & Retesting

When QA finds a bug, it is documented and assigned to the appropriate person.

A simplified flow might look like:

```text
Bug Found
    ↓
Bug Reported
    ↓
Developer Fixes It
    ↓
QA Retests
    ↓
Passed → Closed
Failed → Reopened
```

---

## 7. Test Closure

Testing is completed when the team meets the agreed testing criteria.

The team may review:

* What was tested
* What passed
* What failed
* Remaining defects
* Test coverage
* Lessons learned

The goal is to capture what was learned and improve future testing.

---

# SDLC vs STLC

The easiest way I understand the difference is:

> **SDLC = The complete software development process.**

> **STLC = The testing process within software development.**

| SDLC                                                                         | STLC                                                                      |
| ---------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Covers the entire software lifecycle                                         | Focuses on testing                                                        |
| Includes requirements, design, development, testing, deployment, maintenance | Includes test planning, test design, execution, defect reporting, closure |
| Involves the whole development team                                          | Mainly focuses on QA/testing activities                                   |

---

# Where QA Fits

One important thing I learned is that **QA isn't only involved when developers finish coding.**
QA can contribute throughout the SDLC.

For example, QA can:

* Review requirements
* Identify missing acceptance criteria
* Prepare test scenarios
* Create test cases
* Test the application
* Report defects
* Retest fixes
* Perform regression testing
* Help determine whether a feature is ready for release

---

# What clicked for me

Before learning about SDLC and STLC, I mostly thought of testing as:

> Developer finishes → Tester tests → Bugs are fixed.

Now I understand that QA can be involved much earlier.
The earlier a problem is discovered, the easier it can be to address.

---

# Key Takeaway

**SDLC tells me how software is developed.**

**STLC tells me how testing is planned and performed.**

As a QA tester, understanding both helps me know **where I fit into the team and what I should be doing at each stage.**

---

## Related

* [QA and Software Testing](01-qa-and-software-testing.md)
* [Test Scenarios and Test Cases](03-test-scenarios-and-test-cases.md)
