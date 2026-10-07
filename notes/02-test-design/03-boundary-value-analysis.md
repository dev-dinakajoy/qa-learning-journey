# Boundary Value Analysis

## What Is Boundary Value Analysis?

**Boundary Value Analysis (BVA)** is a black-box test design technique that focuses on testing values **at and around the boundaries** of an input range.

The idea is that defects often occur at the **edges of valid and invalid ranges**, rather than in the middle.

Instead of testing many values within a range, BVA selects values close to the boundaries.

## Why Use Boundary Value Analysis?

Developers can make mistakes when implementing conditions such as:

```text
Age >= 18
Age <= 60
```

A small mistake could accidentally result in:

```text
Age > 18
Age < 60
```

This could cause valid boundary values such as `18` or `60` to be rejected.

BVA helps us detect these kinds of defects by deliberately testing values around the limits.

## Basic BVA Pattern

For a range with a minimum and maximum value, a common BVA approach is to test:

```text
Minimum - 1
Minimum
Minimum + 1

Maximum - 1
Maximum
Maximum + 1
```

For example:

> Age must be between **18 and 60**.

The boundary values are:

```text
17 → Invalid
18 → Valid
19 → Valid

59 → Valid
60 → Valid
61 → Invalid
```

These six values give us strong coverage around both boundaries.

## BVA Example: Transfer Amount

Requirement: Users can transfer between **₦5,000 and ₦500,000 inclusive**.

The minimum boundary is:

```text
₦5,000
```

The maximum boundary is:

```text
₦500,000
```

Using BVA:

```text
₦4,999     → ❌ Invalid
₦5,000     → ✅ Valid
₦5,001     → ✅ Valid

₦499,999   → ✅ Valid
₦500,000   → ✅ Valid
₦500,001   → ❌ Invalid
```

Notice that we aren't randomly choosing these values.

Each value has a specific reason for being tested.

## BVA and Equivalence Partitioning

BVA and EP are closely related and are often used together.

Consider this: A customer can purchase between **1 and 10 units**.

### Equivalence Partitioning

First, divide the input into groups:

```text
< 1       → Invalid
1–10      → Valid
> 10      → Invalid
```

### Boundary Value Analysis

Then test around the boundaries:

```text
0  → ❌
1  → ✅
2  → ✅

9  → ✅
10 → ✅
11 → ❌
```

### The difference

**EP asks:** What groups of values should behave similarly?

**BVA asks:** What happens at and around the edges of those groups?

## Why Boundaries Are Important

Imagine the requirement:

> Username must contain **5–20 characters**.

A tester might choose:

```text
"JoyQA123" → Valid
```

This tests the middle of the valid partition.

But bugs may occur specifically at:

```text
4 characters
5 characters
6 characters

19 characters
20 characters
21 characters
```

BVA focuses our attention on these areas.

## BVA for a Single Boundary

Not every requirement has both a minimum and maximum.

For example: A customer must be at least **18 years old**.

There is a lower boundary but no specified upper boundary.

The boundary is:

```text
18
```

BVA can focus on:

```text
17 → ❌
18 → ✅
19 → ✅
```

### BVA for Maximum Values

Suppose: A customer can enter a maximum of **500 characters**.

The boundary is:

```text
500
```

Test:

```text
499 → ✅
500 → ✅
501 → ❌
```

### BVA for Minimum Values

Suppose: A password must contain at least **8 characters**.

The boundary is:

```text
8
```

Test:

```text
7 → ❌
8 → ✅
9 → ✅
```

### Inclusive vs Exclusive Boundaries

This is very important.

Consider: Age must be **18 or older**.

This means:

```text
Age >= 18
```

Therefore:

```text
17 → ❌
18 → ✅
19 → ✅
```

But suppose the requirement says: Age must be **greater than 18**.

Now:

```text
Age > 18
```

Therefore:

```text
17 → ❌
18 → ❌
19 → ✅
```

The word **"inclusive"** matters.

- Inclusive

Requirnment: Between 18 and 60 **inclusive**

```text
18 → Valid
60 → Valid
```

- Exclusive

Requirnment: Greater than 18 and less than 60

```text
18 → Invalid
60 → Invalid
```

A tester must understand the exact requirement before selecting boundary values.

## BVA for Decimal Values

BVA isn't limited to integers.

Suppose: A product discount can be between **0% and 100%**.

Depending on the system's precision, we might test:

```text
-0.01% → ❌
0%     → ✅
0.01%  → ✅

99.99% → ✅
100%   → ✅
100.01% → ❌
```

The exact values around the boundary depend on the system's allowed precision.

This is another reason to understand the input format and requirements.

## BVA for Dates

BVA can also be used with dates.

Suppose: A promotion is valid from **September 1 to September 30**.

Important boundary dates include:

```text
August 31  → ❌
September 1 → ✅
September 2 → ✅

September 29 → ✅
September 30 → ✅
October 1 → ❌
```

Dates are particularly useful for BVA because off-by-one-day errors can easily occur.

## BVA for String Length

Suppose: Username must be **5–20 characters**.

Test:

```text
4 characters  → ❌
5 characters  → ✅
6 characters  → ✅

19 characters → ✅
20 characters → ✅
21 characters → ❌
```

The actual characters used should be valid so that we are testing **length**, rather than accidentally testing another rule.

For example, if special characters aren't allowed, don't use:

```text
"@@@@@"
```

for a length test.

Use valid characters:

```text
"JoyQA"
```

This isolates the condition we are testing.

## BVA and Test Isolation

A useful testing principle is:

> **When testing a particular boundary, avoid introducing unrelated invalid conditions unless you intend to test their combination.**

Suppose: Password must contain 8–20 characters and only letters/numbers.

If you are testing the **length boundary**, use valid characters.

For example:

```text
7 valid characters → ❌
8 valid characters → ✅
9 valid characters → ✅
```

Don't use:

```text
7 characters containing @
```

because now you are testing both:

* Length
* Invalid character

That may be useful for another test, but it makes the purpose of the boundary test less clear.

## BVA for Quantity

Requirement: Customer can purchase **1–10 units**.

### Lower boundary

```text
0 → ❌
1 → ✅
2 → ✅
```

### Upper boundary

```text
9  → ✅
10 → ✅
11 → ❌
```

## Common BVA Mistakes

### 1. Testing only the boundaries

Some testers might test:

```text
18
60
```

But that's incomplete.

We also want values immediately outside and inside the boundaries:

```text
17
18
19

59
60
61
```

### 2. Ignoring whether boundaries are inclusive

Don't assume:

> 18–60

means the same thing as:

> Greater than 18 and less than 60.

Always check the requirement.

### 3. Using the wrong increment

For integers:

```text
minimum - 1
minimum
minimum + 1
```

makes sense.

But for decimals, dates, currency, or other data types, the appropriate increment depends on the system.

For example, if a currency field accepts two decimal places:

```text
₦4,999.99
₦5,000.00
₦5,000.01
```

may be more appropriate than simply adding ₦1.

### 4. Testing unrelated rules accidentally

If you are testing an age boundary, don't accidentally use invalid formatting or another invalid condition unless that's intentional.

Keep the test focused.

## BVA in Real QA Work

When you see words such as:

* Minimum
* Maximum
* At least
* At most
* Between
* Greater than
* Less than
* Up to
* No more than
* No fewer than
* Exactly

your first thought should be:

> **Is there a boundary I should test?**

For example:

> "Maximum 10 items"

Think:

```text
9
10
11
```

> "At least ₦5,000"

Think:

```text
₦4,999
₦5,000
₦5,001
```

> "Exactly 11 digits"

Think about both sides:

```text
10 digits
11 digits
12 digits
```

## BVA + Other Test Design Techniques

BVA is often combined with other techniques.

### BVA + EP

For numeric ranges:

```text
EP → Identify partitions
BVA → Identify boundary values
```

### BVA + Positive/Negative Testing

```text
17 → Negative
18 → Positive
19 → Positive
60 → Positive
61 → Negative
```

### BVA + Error Guessing

After identifying the formal boundaries, a tester might also consider unusual values such as:

```text
0
-1
very large number
empty input
null
decimal value
```

depending on the application's requirements and data type.

### BVA + Decision Table

When a boundary condition interacts with other conditions, a decision table can help test the combinations.

## Quick Reference

| Requirement              | Boundary Tests                                       |
| ------------------------ | ---------------------------------------------------- |
| Age 18–60                | 17, 18, 19, 59, 60, 61                               |
| Quantity 1–10            | 0, 1, 2, 9, 10, 11                                   |
| Transfer ₦5,000–₦500,000 | ₦4,999, ₦5,000, ₦5,001, ₦499,999, ₦500,000, ₦500,001 |
| Password 8–20 chars      | 7, 8, 9, 19, 20, 21 characters                       |
| Maximum 500 chars        | 499, 500, 501                                        |
| Minimum 18               | 17, 18, 19                                           |

## Key Takeaways

* **Boundary Value Analysis** focuses on values at and around input boundaries.
* Defects frequently occur at boundaries because of incorrect conditions or **off-by-one errors**.
* A common BVA pattern is:

  * Minimum − 1
  * Minimum
  * Minimum + 1
  * Maximum − 1
  * Maximum
  * Maximum + 1
* Always determine whether boundaries are **inclusive or exclusive**.
* BVA can be applied to numbers, strings, dates, currency, quantities, and other data types.
* When testing a specific boundary, avoid introducing unrelated invalid conditions unless you are deliberately testing their combination.
* **EP identifies partitions; BVA focuses on their boundaries.**
* BVA is often combined with EP, positive/negative testing, error guessing, and decision tables.

> **When you see a limit, look at the edge, and one step on either side.**

## Related

* [Equivalence Partitioning](02-equivalence-partitioning.md)
* [Decision Table Testing](04-decision-table-testing.md)