# User Stories for QA

## What is a User Story?

A user story is a short description of a feature from the user's perspective.

A common format is:

> **As a [user type], I want [goal], so that [benefit].**

---

## Example

> As a registered user, I want to search for restaurants by name so that I can find a restaurant I want to order from.

This tells us:

* **Who?** Registered user
* **What?** Search for restaurants by name
* **Why?** Find a restaurant to order from

---

## Why Does QA Care About User Stories?

User stories help QA understand:

* Who will use the feature
* What the user wants to accomplish
* Why the feature exists
* What behavior should be tested

QA can use the story as a starting point for identifying questions and test conditions.

---

## QA's Role During Refinement

QA should participate in requirements discussions and refinement.

QA can ask questions such as:

* What happens with invalid input?
* What happens when data doesn't exist?
* What happens when a dependency fails?
* Are there limits?
* What are the valid and invalid values?
* What happens in edge cases?
* Which users have permission?
* What happens after the user logs out?

These questions can help uncover missing requirements before development is complete.

---

## User Story → Acceptance Criteria → Tests

The relationship is:

```text
User Story
     ↓
Acceptance Criteria
     ↓
Test Scenarios
     ↓
Test Cases
```

Example:

### User Story

> As a registered user, I want to add food items to my cart so that I can purchase them later.

### Acceptance Criterion

> Given an available food item, when the user clicks Add to Cart, then the food item should be added to the cart.

### Test Scenario

> Verify that users can add an available food item to the cart.

### Test Case

The tester defines:

* Preconditions
* Test data
* Steps
* Expected result

---

## One User Story Can Have Many Tests

A single user story may produce many acceptance criteria and test cases.

For example:

### User Story

> As a registered user, I want to log in so that I can access my account.

Possible test scenarios include:

* Login with valid credentials
* Login with incorrect password
* Login with an unregistered email
* Login with empty email
* Login with empty password
* Login with invalid email format
* Verify successful login

Therefore:

> **One user story does not equal one test case.**

---

## Key Takeaway

A user story describes **what the user wants and why**.

QA uses it to understand the feature, identify questions, evaluate acceptance criteria, and design tests.
