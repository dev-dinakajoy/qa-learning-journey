# Acceptance Criteria

## What Are Acceptance Criteria?

Acceptance criteria are the **specific conditions that a feature must satisfy to be accepted**.

They provide clear, testable expectations for a user story or requirement.

They help developers understand what to build and help QA understand what to verify.

---

## Example

### User Story

> As a registered user, I want to search for restaurants by name so that I can find a restaurant I want to order from.

### Acceptance Criteria

**AC1**

> Given the user is on the restaurant search page, when the user enters a restaurant name, then matching restaurants should be displayed.

**AC2**

> Given the user is on the restaurant search page, when the user searches for a restaurant that does not exist, then a "No restaurants found" message should be displayed.

**AC3**

> Given the user is on the restaurant search page, when the user enters a restaurant name using different letter casing, then matching restaurants should still be displayed.

---

## Given / When / Then

A common way to write acceptance criteria is:

> **Given** [initial condition]
> **When** [action]
> **Then** [expected outcome]

### Given

Describes the starting condition.

Example:

> Given an available food item...

### When

Describes the user's action.

Example:

> When the user clicks "Add to Cart"...

### Then

Describes the expected result.

Example:

> Then the food item should be added to the cart.

---

## Good Acceptance Criteria

Good acceptance criteria should be:

* Clear
* Specific
* Testable
* Unambiguous
* Relevant
* Understandable

---

## Poor Acceptance Criteria

Example:

> The search should work properly.

This is difficult to test because "properly" is undefined.

Better:

> Given the user enters a valid restaurant name, when they click Search, then matching restaurants are displayed.

---

## Ambiguous Acceptance Criteria

Consider:

> Given a food item is sold out, when the user attempts to add it to the cart, then the Add to Cart button is disabled **or** an error message is displayed.

The word **"or"** introduces ambiguity.

Which behavior is actually required?

QA should ask the Product Owner to clarify.

The expected behavior should be defined before the test case is finalized.

---

## Turning Acceptance Criteria Into Tests

The process is:

```text
Acceptance Criteria
        ↓
Test Scenario
        ↓
Test Case
```

Example:

### Acceptance Criterion

> Given an available food item, when the user clicks Add to Cart, then the food item should be added to the cart.

### Test Scenario

> Verify that users can add an available food item to the cart.

### Test Case

The test case then specifies:

* Test data
* Preconditions
* Steps
* Expected result

---

## Key Takeaway

Acceptance criteria define **what must be true for a feature to be accepted**.

For QA, they provide a direct source for designing tests.
