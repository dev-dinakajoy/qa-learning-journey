# Decision Table Testing

## What Is Decision Table Testing?

**Decision Table Testing** is a black-box test design technique used to test system behavior when the expected result depends on **multiple conditions or combinations of conditions**.

It represents business rules in a table containing:

* **Conditions** — things that can be true or false.
* **Actions** — what the system should do.
* **Rules** — combinations of conditions that produce a particular action.

The main question is:

> **"What should the system do for each combination of conditions?"**

---

## Why Use Decision Table Testing?

Many software requirements contain business rules involving multiple conditions.

For example:

> A premium customer gets free delivery when their order is at least ₦50,000.

There are two conditions:

```text id="2lgl8t"
Is the customer a premium member?
Is the order ≥ ₦50,000?
```

The result depends on the **combination** of those conditions.

Testing only one condition at a time might cause important combinations to be missed.

Decision tables help us:

* Identify combinations of conditions
* Make complex business rules easier to understand
* Ensure important combinations are tested
* Identify missing or contradictory requirements
* Reduce ambiguity
* Create systematic test cases

---

# Basic Structure of a Decision Table

A decision table commonly contains four parts:

|                | Rule 1 | Rule 2 |
| -------------- | ------ | ------ |
| **Conditions** |        |        |
| Condition 1    | Yes    | No     |
| Condition 2    | Yes    | Yes    |
| **Actions**    |        |        |
| Action         | Do X   | Do Y   |

The columns represent **rules**.

Each rule describes one combination of conditions and the expected action.

---

# Example: Free Delivery

### Requirement

> Premium members receive free delivery when their order is **₦50,000 or more**.

We have two conditions:

1. Premium member?
2. Order ≥ ₦50,000?

And one action:

> Free delivery.

Because each condition can be Yes or No:

```text id="m8z3ql"
2² = 4 possible combinations
```

### Decision Table

| Conditions / Actions | Rule 1  | Rule 2 | Rule 3 | Rule 4 |
| -------------------- | ------- | ------ | ------ | ------ |
| Premium member?      | Yes     | Yes    | No     | No     |
| Order ≥ ₦50,000?     | Yes     | No     | Yes    | No     |
| **Free delivery**    | **Yes** | **No** | **No** | **No** |

This gives us four rules to consider.

---

# Understanding the Rules

### Rule 1

```text id="k4x7zm"
Premium member: Yes
Order ≥ ₦50,000: Yes

→ Free delivery: Yes
```

Both conditions are satisfied.

---

### Rule 2

```text id="q5m6t1"
Premium member: Yes
Order ≥ ₦50,000: No

→ Free delivery: No
```

The customer is premium, but the order doesn't meet the minimum.

---

### Rule 3

```text id="r6h3wb"
Premium member: No
Order ≥ ₦50,000: Yes

→ Free delivery: No
```

The order meets the amount requirement, but the customer isn't premium.

---

### Rule 4

```text id="n3p8yj"
Premium member: No
Order ≥ ₦50,000: No

→ Free delivery: No
```

Neither condition is satisfied.

---

# How Many Rules Do We Need?

When conditions are binary, meaning each condition has two possible values:

```text id="m4p7k1"
Yes / No
True / False
```

the number of possible combinations is:

```text id="h5j6x2"
2ⁿ
```

where **n = number of binary conditions**.

### Examples

| Conditions | Possible combinations |
| ---------: | --------------------: |
|          1 |                     2 |
|          2 |                     4 |
|          3 |                     8 |
|          4 |                    16 |
|          5 |                    32 |

For example:

```text id="6y0gqf"
3 conditions
2³ = 8 combinations
```

However, **2ⁿ gives the theoretical number of combinations**, not necessarily the number of final test cases you must execute.

Some combinations may be:

* Impossible
* Redundant
* Irrelevant
* Covered by other tests

The requirements and business rules determine what actually needs to be tested.

---

# Example: Online Checkout

### Requirement

A customer can checkout only if:

1. They are logged in.
2. Their cart contains at least one item.
3. Their delivery address is valid.

We have three binary conditions:

```text id="g8g9q2"
Logged in?
Has items?
Address valid?
```

Therefore:

```text id="q1t4rv"
2³ = 8 possible combinations
```

### Decision Table

| Conditions / Actions  |    R1 |    R2 |    R3 |    R4 |    R5 |    R6 |    R7 |    R8 |
| --------------------- | ----: | ----: | ----: | ----: | ----: | ----: | ----: | ----: |
| Logged in?            |     Y |     Y |     Y |     Y |     N |     N |     N |     N |
| Has items?            |     Y |     Y |     N |     N |     Y |     Y |     N |     N |
| Address valid?        |     Y |     N |     Y |     N |     Y |     N |     Y |     N |
| **Checkout allowed?** | **Y** | **N** | **N** | **N** | **N** | **N** | **N** | **N** |

Only the first rule satisfies all three conditions.

---

# Conditions vs Actions

It's important not to confuse the two.

### Condition

Something the system evaluates.

Examples:

```text id="b6s0fl"
User logged in?
Balance sufficient?
Restaurant open?
Payment successful?
```

### Action

What the system does as a result.

Examples:

```text id="4n8z8v"
Allow checkout
Reject transaction
Grant discount
Confirm order
Show error
```

A useful way to think about it is:

```text id="3u6e6f"
Conditions
     ↓
Decision
     ↓
Action
```

---

# Decision Tables and AND Conditions

Decision tables are especially useful when requirements contain **AND** conditions.

Example:

> A transfer is allowed when the user is logged in **AND** has sufficient balance.

Conditions:

```text id="4a5c9u"
Logged in?
Balance sufficient?
```

Decision table:

| Logged in | Balance sufficient | Transfer   |
| --------- | ------------------ | ---------- |
| Yes       | Yes                | ✅ Allowed  |
| Yes       | No                 | ❌ Rejected |
| No        | Yes                | ❌ Rejected |
| No        | No                 | ❌ Rejected |

This makes the business rule very clear.

---

# Decision Tables and OR Conditions

Decision tables can also represent **OR** conditions.

Example:

> A user can reset their password if they provide either a registered email **OR** a verified phone number.

Conditions:

```text id="2x5tq5"
Registered email provided?
Verified phone provided?
```

Possible combinations:

| Email | Phone | Reset password |
| ----- | ----- | -------------- |
| Yes   | Yes   | ✅              |
| Yes   | No    | ✅              |
| No    | Yes   | ✅              |
| No    | No    | ❌              |

The decision table makes the OR relationship easy to see.

---

# Decision Tables and Negative Testing

Decision tables naturally help us identify negative tests.

For example:

> Checkout requires login, items, and a valid address.

Positive:

```text id="8j7c3p"
Logged in: Yes
Items: Yes
Address: Valid
→ Checkout allowed
```

Negative:

```text id="m8n4p7"
Logged in: No
Items: Yes
Address: Valid
→ Checkout rejected
```

Another:

```text id="0j6w2k"
Logged in: Yes
Items: No
Address: Valid
→ Checkout rejected
```

Another:

```text id="7m2q4f"
Logged in: Yes
Items: Yes
Address: Invalid
→ Checkout rejected
```

The decision table helps ensure we don't forget these combinations.

---

# Decision Tables and Test Design Techniques

Decision Table Testing can work together with other techniques.

## Decision Table + Equivalence Partitioning

Suppose:

> Transfer amount must be ₦5,000–₦500,000.

EP can determine whether the amount is:

```text id="1o4k4v"
Valid
Invalid
```

The decision table can then combine that condition with other conditions:

```text id="8a7p6f"
Logged in?
Amount valid?
Balance sufficient?
```

---

## Decision Table + Boundary Value Analysis

BVA can be used to determine specific amounts for the "valid amount" or "invalid amount" condition.

For example:

```text id="g9z3e1"
₦4,999  → Invalid
₦5,000  → Valid
₦5,001  → Valid
```

The decision table determines how those conditions interact with other conditions.

---

# Decision Tables Can Reveal Missing Requirements

This is one of the most useful benefits.

Suppose a requirement says:

> Free delivery is available to premium members when the order is at least ₦50,000.

We create:

| Premium | Order ≥ ₦50,000 | Free delivery |
| ------- | --------------- | ------------- |
| Yes     | Yes             | Yes           |
| Yes     | No              | No            |
| No      | Yes             | No            |
| No      | No              | No            |

Now imagine the business later says:

> "Actually, non-premium customers also get free delivery for orders over ₦100,000."

The decision table helps us see that the original business rule needs to be expanded.

This makes decision tables useful not only for testing, but also for **reviewing requirements**.

---

# Decision Tables Can Reveal Contradictions

Suppose two requirements say:

> Premium members get free delivery on orders ≥ ₦50,000.

and:

> Orders below ₦100,000 always have a delivery fee.

These rules conflict for a premium member ordering ₦50,000.

A decision table can expose this contradiction.

The tester can then ask:

> **Which rule takes priority?**

This is an example of how QA can identify problems **before testing even begins**.

---

# Don't Automatically Test Every Combination

Although `2ⁿ` gives us the number of possible combinations, real systems can have many conditions.

For example:

```text id="2v7g8q"
6 binary conditions
```

would produce:

```text id="u4b3k7"
2⁶ = 64 combinations
```

Testing all 64 may be unnecessary.

We may reduce the set based on:

* Business rules
* Risk
* Requirements
* Impossible combinations
* Redundant combinations
* Coverage goals

The important thing is to ensure that the selected tests provide appropriate coverage.

---

# Common Mistakes

## 1. Forgetting a condition

If the requirement has:

```text id="k2j5r6"
Logged in?
Account active?
Balance sufficient?
```

don't accidentally create a table with only two conditions.

Missing a condition can mean missing important business rules.

---

## 2. Confusing conditions with actions

For example:

```text id="j8g3k1"
"Transfer successful"
```

is usually an **action/result**, not a condition.

A condition might be:

```text id="5y9r4p"
Balance sufficient?
```

---

## 3. Assuming unspecified behavior

If a combination isn't explained by the requirement, don't simply invent the expected result.

For example:

> What happens when payment is Pending?

If the requirement doesn't say, flag it:

> **Requirement clarification needed.**

---

## 4. Treating every theoretical combination as mandatory

`2ⁿ` tells us the possible combinations, but not automatically the final number of test cases.

Always consider the actual business rules.

---

# Quick Reference

| Concept            | Meaning                                                      |
| ------------------ | ------------------------------------------------------------ |
| **Condition**      | Something evaluated by the system                            |
| **Action**         | What the system does                                         |
| **Rule**           | A specific combination of conditions and its expected action |
| **Decision Table** | A table showing conditions, combinations, and actions        |
| **2ⁿ**             | Theoretical combinations for n binary conditions             |

---

# When Should I Think "Decision Table"?

Look for requirements containing:

* **AND**
* **OR**
* **IF / THEN**
* Multiple conditions
* Multiple business rules
* Discounts
* Eligibility rules
* Permissions
* Payment rules
* Access control
* Checkout conditions
* Approval/rejection logic

For example:

> "A customer receives a discount if they are a premium member **AND** spend at least ₦50,000."

Think:

> **Decision Table Testing.**

---

# Key Takeaways

* **Decision Table Testing** is used when system behavior depends on multiple conditions.
* A decision table contains **conditions, rules, and actions**.
* Each column generally represents a **rule/combination**.
* For `n` binary conditions, there are theoretically **2ⁿ combinations**.
* Not every theoretical combination must necessarily become a final test case.
* Decision tables are useful for both **positive and negative testing**.
* They work well with **Equivalence Partitioning** and **Boundary Value Analysis**.
* They can expose **missing, ambiguous, or contradictory requirements**.
* Always distinguish between what the requirement explicitly says and what you are assuming.

> **When multiple conditions determine the outcome, turn the business rules into a table.**
