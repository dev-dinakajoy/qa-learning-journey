# Requirements Analysis for QA

## What is Requirements Analysis?

Requirements analysis is the process of reviewing requirements to understand:

* What the system should do
* What users need
* What behavior must be tested
* Whether requirements are clear and testable
* Whether important requirements are missing
* Whether there are contradictions or ambiguities

QA should not simply wait until development is finished before reading requirements.

QA can contribute during requirement review and refinement.

---

## Why is Requirements Analysis Important?

Poorly understood requirements can lead to:

* Incorrect functionality
* Missing test cases
* Conflicting expectations
* Unclear acceptance criteria
* Defects discovered late
* Rework

Good requirements analysis helps QA identify problems before implementation.

---

## What Does QA Look For?

### 1. Is the requirement clear?

Example:

> The application should load quickly.

This is vague.

How quickly?

* Under 1 second?
* Under 3 seconds?
* Under 5 seconds?

The requirement needs clarification.

---

### 2. Is the requirement testable?

A requirement should describe behavior that can be verified.

Instead of:

> The application should be user-friendly.

A more testable requirement might specify measurable usability expectations.

---

### 3. Is anything missing?

Suppose the requirement says:

> Users can search for restaurants by name.

QA may ask:

* What happens when there are no results?
* Is the search case-sensitive?
* Is partial matching supported?
* What happens when the search field is empty?
* Are special characters allowed?

These questions can reveal missing requirements.

---

### 4. Are there ambiguities?

Example:

> Users can add food items to their cart.

Questions:

* Can users add unavailable items?
* What happens if stock is insufficient?
* What happens when quantity reaches zero?
* Does the cart persist after logout?

The requirement doesn't answer these questions.

QA should seek clarification rather than make assumptions.

---

## QA Questions During Requirement Review

A QA tester may ask:

### Functional behavior

* What should happen when the user performs this action?
* What happens when the action fails?
* What happens with invalid input?

### Validation

* What values are valid?
* What values are invalid?
* Are there minimum and maximum limits?

### Error handling

* What message should be displayed?
* What happens when a dependency fails?

### User permissions

* Which users can perform this action?
* What happens when an unauthorized user attempts it?

### Data

* What data is required?
* What happens when the data doesn't exist?

---

## Requirements Should Be Testable

A useful requirement should provide enough information for QA to determine whether the implementation satisfies it.

A good requirement should generally be:

* Clear
* Consistent
* Unambiguous
* Testable
* Complete
* Relevant

---

## Key Takeaway

Requirements analysis is not simply reading requirements.

QA should actively ask:

> **"Can I understand this requirement clearly enough to test it?"**

If the answer is no, the requirement may need clarification before testing can be designed properly.
