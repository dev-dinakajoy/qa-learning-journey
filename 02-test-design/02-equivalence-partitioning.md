# Equivalence Partitioning

## What Is Equivalence Partitioning?

**Equivalence Partitioning (EP)** is a black-box test design technique that divides input data into **groups or partitions** where the system is expected to behave in the same way.

Instead of testing every possible input, we select **representative values** from each partition.

The idea is:

> If one value from a partition behaves correctly, other values in that same partition are expected to behave similarly.

This allows testers to achieve good test coverage with fewer test cases.

---

## Why Use Equivalence Partitioning?

Testing every possible input is often impractical.

For example, suppose an application accepts an age between **18 and 60**.

There are many possible valid values:

```text
18, 19, 20, 21, 22, ... 59, 60
```

We don't need to test every age.

Instead, we can divide the inputs into three partitions:

```text
< 18          → Invalid
18–60         → Valid
> 60          → Invalid
```

Then select one representative value from each partition:

```text
17 → Invalid
30 → Valid
61 → Invalid
```

Three tests can give us useful coverage of the three equivalence classes.

---

## Equivalence Partitions

An **equivalence partition** is a group of input values that should produce the same type of result.

Partitions can generally be:

* **Valid partitions** — inputs the system should accept.
* **Invalid partitions** — inputs the system should reject or handle appropriately.

### Example

Requirement:

> A customer can transfer between **₦5,000 and ₦500,000 inclusive**.

We can identify three partitions:

| Partition | Range           | Valid/Invalid | Representative |
| --------- | --------------- | ------------- | -------------: |
| 1         | < ₦5,000        | Invalid       |         ₦4,000 |
| 2         | ₦5,000–₦500,000 | Valid         |        ₦20,000 |
| 3         | > ₦500,000      | Invalid       |       ₦600,000 |

We don't need to test every amount.

One representative value from each partition gives us basic equivalence-partition coverage.

---

## How to Apply Equivalence Partitioning

### Step 1 — Identify the requirement

Start by understanding what the system accepts and rejects.

Example:

> Username must contain between 5 and 20 characters.

### Step 2 — Identify the partitions

We can divide the inputs into:

```text
< 5 characters       → Invalid
5–20 characters      → Valid
> 20 characters      → Invalid
```

### Step 3 — Select representative values

Choose one or more values from each partition:

```text
"Joy"                 → Invalid
"JoyOdinaka"          → Valid
"JoyOdinakaQA123456789012" → Invalid
```

### Step 4 — Create test cases

Document the selected values as test cases and define the expected behavior.

---

# Example 1 — Age Validation

### Requirement

> Users must be between **18 and 60 years old**.

### Partitions

```text
Partition 1:
< 18
Invalid

Partition 2:
18–60
Valid

Partition 3:
> 60
Invalid
```

### Representative test values

```text
17 → ❌ Invalid
30 → ✅ Valid
61 → ❌ Invalid
```

Notice that we don't need to test:

```text
18
19
20
21
...
59
60
```

to establish basic EP coverage.

Those values belong to the same valid partition.

---

# Example 2 — Transfer Amount

### Requirement

> Users can transfer between **₦5,000 and ₦500,000 inclusive**.

### Partitions

```text
Partition 1:
< ₦5,000
Invalid

Partition 2:
₦5,000–₦500,000
Valid

Partition 3:
> ₦500,000
Invalid
```

### Representative values

```text
₦4,999  → ❌
₦8,000  → ✅
₦500,001 → ❌
```

The important point is that **₦8,000 represents the entire valid partition**, not just ₦8,000.

---

# Example 3 — Phone Number

### Requirement

> A phone number must contain exactly **11 digits**.

Possible partitions include:

```text
< 11 digits       → Invalid
Exactly 11 digits  → Valid
> 11 digits       → Invalid
```

Example representatives:

```text
0809754673       → ❌
08097546732      → ✅
080975467320     → ❌
```

We could also identify additional partitions based on the format requirement.

For example:

```text
Alphabetic input       → Invalid
Special characters     → Invalid
Empty input            → Invalid
Spaces only            → Invalid
11 numeric digits      → Valid
```

This is why understanding the **complete requirement** is important.

---

# Multiple Equivalence Partitions

Sometimes a requirement contains more than one input condition.

Consider:

> A username must contain **5–20 characters** and may contain only letters and numbers.

There are multiple dimensions to consider:

### Length

```text
< 5       → Invalid
5–20      → Valid
> 20      → Invalid
```

### Character type

```text
Letters/numbers → Valid
Special chars   → Invalid
```

This means we may need to consider combinations of partitions.

For example:

```text
"Joy123"
```

* Length: Valid
* Characters: Valid

Therefore:

> ✅ Valid username

But:

```text
"Jo@123"
```

* Length: Valid
* Characters: Invalid

Therefore:

> ❌ Invalid username

This is where other techniques, particularly **Decision Table Testing**, can become useful.

---

# Equivalence Partitioning and Boundary Value Analysis

Equivalence Partitioning and Boundary Value Analysis are closely related, but they serve different purposes.

### Equivalence Partitioning

Focuses on:

> **Groups of inputs**

Example:

```text
< 18
18–60
> 60
```

A representative value might be:

```text
17
30
61
```

### Boundary Value Analysis

Focuses on:

> **The edges of those groups**

For the same requirement:

```text
17 → ❌
18 → ✅
19 → ✅

59 → ✅
60 → ✅
61 → ❌
```

### Together

EP tells us:

> **Which groups should we test?**

BVA tells us:

> **Which values around the boundaries should we test?**

Using both gives stronger coverage.

---

# Equivalence Partitioning Is Not Random Testing

It's important to understand this distinction.

### Random testing

You might randomly choose:

```text
23
41
57
```

There may be no reason these values were selected.

### Equivalence Partitioning

You deliberately select values because they represent specific partitions:

```text
17 → Represents < 18
30 → Represents 18–60
61 → Represents > 60
```

The selection is **systematic and justified**.

---

# Positive and Negative Testing With EP

Equivalence Partitioning naturally helps identify positive and negative tests.

For example:

```text
Age requirement: 18–60
```

### Positive partition

```text
18–60 → Valid
```

Example:

```text
30 → ✅
```

### Negative partitions

```text
< 18 → Invalid
> 60 → Invalid
```

Examples:

```text
17 → ❌
61 → ❌
```

So EP helps us identify both valid and invalid test data.

---

# Important QA Consideration: Don't Assume Partitions

Partitions must come from the **requirements or known system behavior**.

Suppose the requirement says:

> Phone number must contain 11 digits.

We can confidently identify:

```text
< 11
= 11
> 11
```

But if we decide that:

```text
+2348097546732 → Invalid
```

we need to know whether international formats are actually prohibited.

If the requirement doesn't say, this may be a **requirement clarification**, not automatically an invalid partition.

A good QA tester should avoid turning assumptions into requirements.

Instead, ask:

> **"Does the phone number field support international formats such as +234...?"**

---

# Common Mistakes When Using EP

## 1. Testing too many values from the same partition

If:

```text
18–60 → Valid
```

testing:

```text
25
30
35
40
45
50
```

doesn't necessarily provide additional EP coverage.

Other techniques such as BVA may justify additional values.

---

## 2. Missing an invalid partition

For:

```text
18–60
```

don't test only:

```text
30 → Valid
```

You should also identify:

```text
< 18
> 60
```

and test representative values.

---

## 3. Confusing EP with BVA

EP:

> Groups inputs.

BVA:

> Tests values around boundaries.

They are related, but they aren't the same technique.

---

## 4. Assuming an unstated rule

Don't create an invalid partition simply because you think something should be invalid.

Always ask:

> **What does the requirement actually say?**

---

# Advantages of Equivalence Partitioning

EP helps testers:

* Reduce the number of test cases
* Improve test coverage
* Identify valid and invalid input groups
* Systematically select representative test data
* Avoid unnecessary duplication
* Create a clear justification for test-data selection

---

# Limitations of Equivalence Partitioning

EP alone may not find every defect.

For example, suppose:

```text
Age = 18–60
```

EP might select:

```text
30 → Valid
```

But a defect may exist specifically at:

```text
18
60
```

That's why **Boundary Value Analysis** is often combined with EP.

Similarly, EP doesn't necessarily cover complex combinations of conditions. **Decision Table Testing** can help with those situations.

---

# Quick Example

### Requirement

> A discount code is valid when the order total is between **₦10,000 and ₦100,000**.

### Equivalence partitions

```text
Partition 1:
< ₦10,000
Invalid

Partition 2:
₦10,000–₦100,000
Valid

Partition 3:
> ₦100,000
Invalid
```

### Representative values

```text
₦5,000   → ❌
₦50,000  → ✅
₦150,000 → ❌
```

These three tests cover the three equivalence partitions.

Then BVA can be used to investigate:

```text
₦9,999
₦10,000
₦10,001

₦99,999
₦100,000
₦100,001
```

---

# Key Takeaways

* **Equivalence Partitioning (EP)** divides input data into groups that should behave similarly.
* Each group is called an **equivalence partition**.
* Partitions can be **valid or invalid**.
* We select representative values instead of testing every possible input.
* EP helps reduce redundant test cases while maintaining useful coverage.
* EP is based on the **expected behavior defined by requirements**.
* Don't turn assumptions into requirements.
* EP works particularly well with **Boundary Value Analysis**.
* EP identifies **groups**, while BVA focuses on **boundaries**.
* EP can also help identify positive and negative test cases.

> **Think in groups, choose representatives, and test the boundaries separately.**
