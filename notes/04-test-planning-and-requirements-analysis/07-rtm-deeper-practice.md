# RTM — Deeper Practice

## What is Traceability?

Traceability means being able to follow a requirement through the testing process.

A typical traceability chain is:

```text
Requirement
     ↓
Acceptance Criteria
     ↓
Test Scenario
     ↓
Test Case
     ↓
Execution Result
     ↓
Defect
     ↓
Retest
     ↓
Regression
```

---

## Why is Traceability Important?

Traceability helps QA determine:

* Whether requirements are covered
* Which scenarios test each requirement
* Which test cases verify each scenario
* Which tests passed or failed
* Which defects are associated with failed tests
* What is affected when requirements change

---

## Basic RTM

Example:

| Requirement | Test Case     | Status | Defect        |
| ----------- | ------------- | ------ | ------------- |
| R1          | TC_LOGIN_001  | Fail   | BUG-LOGIN-001 |
| R2          | TC_SEARCH_001 | Pass   | —             |
| R2          | TC_SEARCH_002 | Pass   | —             |
| R3          | TC_CART_001   | Pass   | —             |
| R3          | TC_CART_002   | Fail   | BUG-CART-001  |

---

## One Requirement Can Have Multiple Test Cases

For example:

```text
R2 — Users can search for restaurants
│
├── TC_SEARCH_001
└── TC_SEARCH_002
```

This allows one requirement to be tested from multiple conditions.

---

## One Test Case Can Sometimes Cover Multiple Requirements

Depending on how requirements are structured, one test case may provide coverage for multiple related requirements.

However, traceability should only be recorded when the test genuinely verifies the requirement.

---

## Forward Traceability

Forward traceability starts with the requirement.

Example:

```text
R2
 ↓
TS_SEARCH_001
 ↓
TC_SEARCH_001
 ↓
Pass
```

It answers:

> Has this requirement been tested?

---

## Backward Traceability

Backward traceability starts with the test.

Example:

```text
TC_SEARCH_001
 ↓
TS_SEARCH_001
 ↓
R2
```

It answers:

> Which requirement does this test verify?

---

## Defect Traceability

A failed test can be linked to a defect.

Example:

```text
R2
 ↓
TS_SEARCH_001
 ↓
TC_SEARCH_001
 ↓
Fail
 ↓
BUG-SEARCH-001
```

This allows the team to determine which requirement is affected by the defect.

---

## Requirement Changes and Impact Analysis

Requirements can change during development.

When a requirement changes, QA should determine what existing testing is affected.

For example:

Original:

> Users can add food items to their cart.

Updated:

> Users can add food items to their cart, but cannot add more items than available stock.

QA should determine:

* Which test scenarios are affected?
* Which test cases need updating?
* Are new test cases required?
* Does the RTM need updating?
* Is additional regression testing required?

This process is called **impact analysis**.

---

## Maintaining Traceability

RTM should be updated when:

* Requirements change
* New requirements are added
* Test scenarios are added or removed
* Test cases change
* Test execution results change
* Defects are discovered
* Defects are fixed and retested

An RTM is a living document during the testing lifecycle.

---

## Traceability and Coverage

RTM can help identify coverage gaps.

For example:

```text
R1 → Tested
R2 → Tested
R3 → Tested
R4 → NOT COVERED
```

R4 represents a testing gap.

QA can then investigate whether test scenarios and test cases need to be created.

---

## Coverage Does Not Mean Bug-Free

Having every requirement mapped to at least one test case does **not** mean the application is defect-free.

For example:

> "Users can log in."

One valid-login test may provide requirement coverage, but additional testing may be needed for:

* Invalid password
* Invalid email
* Empty fields
* Invalid email format
* Account lockout
* Session behavior
* Boundary conditions

Therefore:

> **Requirement coverage indicates that requirements have associated tests. It does not guarantee complete testing or a defect-free application.**

---

## Key Takeaway

RTM provides traceability between requirements and testing activities.

A strong RTM allows QA to answer:

> **What requirement are we testing?**

> **Which test verifies it?**

> **Did the test pass or fail?**

> **If it failed, is there a defect?**

> **What testing is affected if the requirement changes?**

The goal of traceability is not simply to create a table. It is to maintain a clear connection between **requirements, testing, results, and defects**.
