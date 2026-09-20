# What Is Test Design?

## Introduction

**Test design** is the process of deciding **what to test, how to test it, and which test cases to create** based on the requirements and expected behavior of a software application.

Instead of testing every possible input and scenario, test design helps QA testers select **effective and meaningful test cases** that provide good coverage while reducing unnecessary or duplicate testing.

Test design is an important part of software testing because the quality of the tests depends heavily on how well they are designed.

---

## Why Is Test Design Important?

A software application can have a huge number of possible inputs, actions, and user interactions. It is usually impossible to test every possible combination.

Test design techniques help testers:

* Identify important test scenarios
* Reduce redundant test cases
* Improve test coverage
* Find defects more efficiently
* Focus on high-risk areas
* Test valid and invalid behavior
* Identify edge cases
* Handle combinations of conditions systematically
* Make testing more structured and repeatable

### Example

Suppose a field accepts an age between **18 and 60**.

Testing every possible age would be unnecessary.

Instead, test design techniques can help us select meaningful values:

```text
17  → Invalid
18  → Valid
19  → Valid

59  → Valid
60  → Valid
61  → Invalid
```

These values provide useful coverage without testing every possible age.

---

## Test Design Techniques

The main test design techniques covered in this level are:

### 1. Equivalence Partitioning

Divides possible inputs into groups (partitions) that are expected to behave similarly.

Example:

```text
Age: 18–60

< 18       → Invalid
18–60      → Valid
> 60       → Invalid
```

Instead of testing every age, we select representative values from each partition.

---

### 2. Boundary Value Analysis

Focuses on values at and around the boundaries of an input range.

Example:

```text
17 → Invalid
18 → Valid
19 → Valid

59 → Valid
60 → Valid
61 → Invalid
```

Boundary Value Analysis is often used together with Equivalence Partitioning.

---

### 3. Decision Table Testing

Used when the expected behavior depends on **multiple conditions or combinations of conditions**.

Example:

```text
Logged in?
Has sufficient balance?
Transfer amount valid?
```

The different combinations of these conditions can produce different results.

Decision tables help ensure that important combinations are not missed.

---

### 4. State Transition Testing

Used when the behavior of a system depends on its **current state** and the actions or events that occur.

Example:

```text
Pending
   ↓
Confirmed
   ↓
Preparing
   ↓
Shipped
   ↓
Delivered
```

State Transition Testing verifies both valid and invalid transitions between states.

---

### 5. Error Guessing

Uses the tester's **experience, knowledge, and intuition** to predict where defects might occur.

Examples include testing:

* Empty input
* Spaces
* Invalid characters
* Negative numbers
* Zero
* Very large values
* Unexpected user actions
* Previously problematic areas

Error Guessing is less formal than techniques such as Equivalence Partitioning or Boundary Value Analysis, but it can uncover defects that structured techniques may miss.

---

### 6. Positive Testing

Verifies that the application works correctly when provided with **valid input or valid actions**.

Example:

```text
Requirement:
Age must be 18–60.

Input:
25

Expected:
Age accepted
```

---

### 7. Negative Testing

Verifies that the application handles **invalid, unexpected, or disallowed input/actions correctly**.

Example:

```text
Requirement:
Age must be 18–60.

Input:
17

Expected:
Age rejected with appropriate validation
```

Negative testing does not mean that we expect the application to crash or fail. We expect the application to **handle the invalid situation correctly**.

---

## How the Techniques Work Together

Test design techniques are not necessarily used in isolation.

A single requirement may benefit from several techniques.

For example:

> A customer can transfer between **₦5,000 and ₦500,000 inclusive**.

We could use:

### Equivalence Partitioning

```text
< ₦5,000          → Invalid
₦5,000–₦500,000   → Valid
> ₦500,000        → Invalid
```

### Boundary Value Analysis

```text
₦4,999     → Invalid
₦5,000     → Valid
₦5,001     → Valid

₦499,999   → Valid
₦500,000   → Valid
₦500,001   → Invalid
```

### Positive Testing

```text
₦20,000 → Accepted
```

### Negative Testing

```text
₦3,000 → Rejected
```

### Error Guessing

We could additionally consider:

```text
₦0
-₦5,000
"abc"
Empty input
Spaces
Extremely large amount
```

Each technique gives us a different way of looking at the same requirement.

---

## Test Design vs Test Execution

It is important to distinguish **test design** from **test execution**.

### Test Design

Determines:

> **What should we test and how should we test it?**

For example:

```text
Identify partitions
↓
Identify boundaries
↓
Identify conditions
↓
Select test cases
```

### Test Execution

Determines:

> **What actually happens when we run the test?**

For example:

```text
Expected: Transfer succeeds
Actual: Transfer fails
Result: FAIL
```

We will cover test execution and documentation in a later level.

---

## Quick Reference

| Technique                    | Main Question                                          |
| ---------------------------- | ------------------------------------------------------ |
| **Equivalence Partitioning** | What groups of inputs should behave similarly?         |
| **Boundary Value Analysis**  | What happens at and around the boundaries?             |
| **Decision Table Testing**   | What happens when multiple conditions combine?         |
| **State Transition Testing** | What happens when the system moves between states?     |
| **Error Guessing**           | Where do I think the system might break?               |
| **Positive Testing**         | Does valid input/action work correctly?                |
| **Negative Testing**         | Does the system handle invalid input/action correctly? |

---

## Key Takeaways

* **Test design** determines what and how we test.
* We don't need to test every possible input or combination.
* Test design techniques help us select **effective, high-value test cases**.
* Different techniques address different types of requirements.
* **Equivalence Partitioning** focuses on input groups.
* **Boundary Value Analysis** focuses on boundaries.
* **Decision Table Testing** focuses on combinations of conditions.
* **State Transition Testing** focuses on changes between states.
* **Error Guessing** uses tester experience to predict likely failures.
* **Positive and Negative Testing** verify valid and invalid behavior.
* Multiple test design techniques can be combined to improve coverage.

> **Good test design is about testing smarter, not simply testing more.**
