# Free Delivery Test Case Design

## Feature

Free Delivery Eligibility

## Business Rule

A customer receives **free delivery only when both conditions are true**:

* The customer is a Premium Member.
* The order total is **₦50,000 or more**.

If either condition is false, the customer does not receive free delivery.

---

## Decision Table

| Rule | Premium Member | Order ≥ ₦50,000 | Free Delivery |
| ---- | -------------- | --------------- | ------------- |
| R1   | Yes            | Yes             | Yes           |
| R2   | Yes            | No              | No            |
| R3   | No             | Yes             | No            |
| R4   | No             | No              | No            |

---

## Test Cases

| Test Case ID | Test Case                                        | Premium Member | Order Amount | Expected Result              |
| ------------ | ------------------------------------------------ | -------------- | ------------ | ---------------------------- |
| TC_FD_001    | Premium member places an order of ₦50,000        | Yes            | ₦50,000      | Free delivery is applied     |
| TC_FD_002    | Premium member places an order below ₦50,000     | Yes            | ₦49,999      | Free delivery is not applied |
| TC_FD_003    | Non-premium member places an order of ₦50,000    | No             | ₦50,000      | Free delivery is not applied |
| TC_FD_004    | Non-premium member places an order below ₦50,000 | No             | ₦49,999      | Free delivery is not applied |

---

## Test Case Details

### TC_FD_001 — Premium Member + Eligible Order

**Preconditions:**

* User is logged in.
* User is a Premium Member.
* Products in the cart total ₦50,000.

**Steps:**

1. Add products worth ₦50,000 to the cart.
2. Proceed to checkout.
3. Check the delivery charge.

**Expected Result:**

* Free delivery is applied.
* Delivery charge is ₦0.

**Decision Table Rule:** R1

---

### TC_FD_002 — Premium Member + Ineligible Order

**Preconditions:**

* User is logged in.
* User is a Premium Member.
* Products in the cart total less than ₦50,000.

**Steps:**

1. Add products worth ₦49,999 to the cart.
2. Proceed to checkout.
3. Check the delivery charge.

**Expected Result:**

* Free delivery is not applied.
* The applicable delivery charge is displayed.

**Decision Table Rule:** R2

---

### TC_FD_003 — Non-Premium Member + Eligible Order

**Preconditions:**

* User is logged in.
* User is not a Premium Member.
* Products in the cart total ₦50,000 or more.

**Steps:**

1. Add products worth ₦50,000 to the cart.
2. Proceed to checkout.
3. Check the delivery charge.

**Expected Result:**

* Free delivery is not applied.
* The applicable delivery charge is displayed.

**Decision Table Rule:** R3

---

### TC_FD_004 — Non-Premium Member + Ineligible Order

**Preconditions:**

* User is logged in.
* User is not a Premium Member.
* Products in the cart total less than ₦50,000.

**Steps:**

1. Add products worth ₦49,999 to the cart.
2. Proceed to checkout.
3. Check the delivery charge.

**Expected Result:**

* Free delivery is not applied.
* The applicable delivery charge is displayed.

**Decision Table Rule:** R4

---

## Coverage

The four test cases cover **all four combinations** in the decision table:

* Premium + Order ≥ ₦50,000
* Premium + Order < ₦50,000
* Non-premium + Order ≥ ₦50,000
* Non-premium + Order < ₦50,000

This ensures that each business-rule combination has been tested.

## Test Design Technique

**Decision Table Testing**

The test cases were derived from combinations of conditions and their expected outcomes. Each row of the decision table represents a rule that is covered by at least one test case.
