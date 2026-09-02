# Test Design Practice

## What I Practiced

I practiced applying different test design techniques to real-world requirements.

### 1. Equivalence Partitioning

I divided inputs into valid and invalid groups and selected representative values from each partition.

**Example — Product Quantity: 1–10**

| Partition | Range           | Example |
| --------- | --------------- | ------: |
| Invalid   | Less than 1     |       0 |
| Valid     | 1–10            |       6 |
| Invalid   | Greater than 10 |      15 |

---

### 2. Boundary Value Analysis

I tested values at and around the boundaries of an allowed range.

**Example — Product Quantity: 1–10**

| Value | Expected |
| ----: | -------- |
|     0 | Invalid  |
|     1 | Valid    |
|     2 | Valid    |
|     9 | Valid    |
|    10 | Valid    |
|    11 | Invalid  |

---

### 3. Decision Table Testing

I created test cases by combining different conditions and checking the expected outcome.

**Example — Free Delivery**

| Premium Member | Order ≥ ₦50,000 | Free Delivery |
| -------------- | --------------- | ------------- |
| Yes            | Yes             | Yes           |
| Yes            | No              | No            |
| No             | Yes             | No            |
| No             | No              | No            |

This helped me understand how decision tables can make business rules easier to test systematically.

---

### 4. State Transition Testing

I practiced testing how a system changes from one state to another based on an action.

**Example — Login Attempts**

| Current State | Action           | Expected State |
| ------------- | ---------------- | -------------- |
| Active        | Wrong password   | Active         |
| Active        | Wrong password   | Active         |
| Active        | Wrong password   | Locked         |
| Locked        | Correct password | Locked         |

This helped me understand that some systems need to be tested based on **what happened previously**, not just the current input.

---

### 5. Positive and Negative Testing

I practiced testing both valid and invalid inputs.

**Example — Phone Number**

| Input       | Type     | Expected Result  |
| ----------- | -------- | ---------------- |
| 08012345678 | Positive | Accepted         |
| 0801234567  | Negative | Validation error |
| `abcdefgh`  | Negative | Validation error |
| Empty value | Negative | Validation error |
| Spaces      | Negative | Validation error |

---

### 6. Error Guessing

I practiced thinking about mistakes users might make that could expose defects.

Examples:

* Leaving required fields empty
* Entering spaces instead of a value
* Entering too few or too many digits
* Entering unexpected characters
* Using invalid combinations of inputs
* Performing an action when the system is in an invalid state

## What I Learned

Test design techniques help me decide **what to test, which values to use, and why those tests are important**.

I also learned that I don't need to test every possible input. By choosing appropriate techniques, I can create a smaller set of meaningful test cases while still achieving good coverage.
