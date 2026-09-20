# Error Guessing

## What Is Error Guessing?

**Error Guessing** is a software testing technique where the tester uses their **experience, knowledge, intuition, and understanding of common mistakes** to predict where defects are likely to occur.

Instead of relying only on formal test design rules, the tester asks:

> **"What could go wrong here?"**

The tester then creates tests specifically to expose those potential problems.

Error Guessing is an **experience-based test design technique**.

---

## Why Use Error Guessing?

Even when we use structured techniques such as:

* Equivalence Partitioning
* Boundary Value Analysis
* Decision Table Testing
* State Transition Testing

we may still miss unusual situations.

Error Guessing helps testers think beyond the obvious requirements.

It can help us:

* Find unexpected defects
* Test unusual inputs
* Identify common user mistakes
* Explore areas where developers may have made mistakes
* Test edge cases that formal techniques may not cover
* Use knowledge from previous defects
* Complement other test design techniques

---

# The Basic Idea

Suppose we have a phone number field.

The requirement says:

> Phone number must contain exactly 11 digits.

A structured approach might give us:

```text
10 digits → Invalid
11 digits → Valid
12 digits → Invalid
```

With Error Guessing, we ask:

> **"What else might go wrong?"**

We might test:

```text
Empty input
Null
Spaces
Letters
Special characters
Negative numbers
Very large numbers
Leading/trailing spaces
Copy and paste
```

These tests come from thinking about **likely mistakes and failure points**.

---

# Common Error Guessing Areas

There are certain types of inputs and situations that testers commonly investigate.

## 1. Empty Values

Test what happens when a required field is left empty.

Examples:

```text
""
null
```

Questions:

* Is validation displayed?
* Can the form be submitted?
* Does the application crash?
* Is the error message clear?

---

## 2. Spaces

Test:

```text
" "
"   "
"  Joy  "
```

Questions:

* Are spaces allowed?
* Are leading/trailing spaces removed?
* Is an input containing only spaces treated as empty?

---

## 3. Invalid Characters

If a field expects numbers:

```text
abc
abc123
@#$%
```

If it expects letters:

```text
123
123abc
@#$%
```

The goal is to see whether the application correctly handles unexpected characters.

---

## 4. Special Characters

Depending on the requirement, test:

```text
@
#
$
%
&
*
'
"
<
>
/
\
```

This can reveal:

* Validation problems
* Unexpected application behavior
* Formatting problems
* Input-handling defects

The exact characters to test should depend on what the field is expected to accept.

---

## 5. Zero

Zero can be an important value.

For example:

> Quantity must be at least 1.

Test:

```text
0 → Invalid
```

Another example:

> Transfer amount must be greater than ₦0.

Test:

```text
₦0 → Invalid
```

Zero is easy to overlook if the tester only considers positive and negative numbers.

---

## 6. Negative Numbers

For fields that normally accept positive values:

```text
-1
-100
-₦5,000
```

Ask:

> **Should negative values be accepted?**

For example, a product quantity of:

```text
-3
```

should normally be rejected.

---

## 7. Extremely Large Values

Test values much larger than expected.

For example:

```text
999999999999999999
```

Questions:

* Does the field reject it?
* Does the application overflow?
* Is the value truncated?
* Does the application crash?
* Is an appropriate validation message displayed?

---

## 8. Unexpected Data Types

If a field expects a number, try:

```text
"abc"
"12abc"
null
""
```

If it expects text, consider whether numeric or other unexpected input is possible.

This is particularly useful when testing APIs.

---

## 9. Copy and Paste

Users don't always type data manually.

Try:

* Copying valid data
* Copying invalid data
* Pasting spaces
* Pasting very long text
* Pasting formatted text

Sometimes validation behaves differently for pasted input than for typed input.

---

## 10. Repeated Actions

Error Guessing isn't limited to input fields.

Try repeating actions such as:

```text
Double-click Submit
Click Pay multiple times
Refresh during payment
Click Back repeatedly
Submit the same form twice
```

Questions:

* Is a duplicate transaction created?
* Is the button disabled?
* Does the application process the action twice?
* Does the state become inconsistent?

---

# Error Guessing From Previous Defects

One of the strongest uses of Error Guessing is learning from **previous bugs**.

Suppose a previous version had a defect where:

> A user could submit a form with spaces in a required field.

The next time you test a similar form, you should remember this possibility.

You might test:

```text
" "
"   "
"  Joy  "
```

This is experience-based testing.

A previous defect can become a clue for finding similar defects elsewhere.

---

# Error Guessing and Requirements

Error Guessing does **not** mean randomly entering nonsense into the application.

The tests should still have a reason.

For example:

### Requirement

> Product quantity must be between 1 and 10.

Structured techniques give us:

**EP:**

```text
< 1
1–10
> 10
```

**BVA:**

```text
0
1
2
9
10
11
```

Error Guessing might add:

```text
-1
0.5
"abc"
""
null
999999
```

Why?

Because these are common ways input validation can fail.

---

# Error Guessing vs Boundary Value Analysis

These techniques can overlap, but their reasoning is different.

### BVA

We deliberately test values around a known boundary.

Example:

```text
Minimum = 1

0 → Invalid
1 → Valid
2 → Valid
```

The values are selected because they are around the boundary.

### Error Guessing

We select values because we suspect they could expose a defect.

Example:

```text
-1
0.5
"abc"
null
```

The selection comes from tester experience and likely failure points.

---

# Error Guessing vs Equivalence Partitioning

### EP

Groups inputs based on expected behavior.

Example:

```text
< 1      → Invalid
1–10     → Valid
> 10     → Invalid
```

### Error Guessing

Asks:

> What unusual inputs might break the application?

For example:

```text
-1
null
"abc"
1.5
```

Both techniques can be used together.

---

# Error Guessing vs Positive and Negative Testing

These concepts are related but not identical.

### Negative Testing

We deliberately provide invalid input or perform an invalid action.

Example:

```text
Quantity = -1
Expected → Rejected
```

### Error Guessing

Explains **why we chose that particular test**.

For example:

> "I suspect negative numbers may not be handled correctly, so I will test `-1`."

Therefore:

> **Error Guessing can be used to identify negative tests.**

---

# Practical Example — Phone Number

### Requirement

> Phone number must contain exactly 11 digits.

### Structured tests

Using EP:

```text
10 digits → Invalid
11 digits → Valid
12 digits → Invalid
```

Using BVA:

```text
10 digits → ❌
11 digits → ✅
12 digits → ❌
```

### Error Guessing

We might additionally test:

```text
""
null
"           "
"abcdefghijk"
"0809754673a"
"080-9754-6732"
"+2348097546732"
"00000000000"
Very long number
Decimal value
```

Each test should have a reason based on the requirement, system behavior, or common failure patterns.

---

# Practical Example — Login

Suppose the requirement says:

> Users must provide a valid email and password to log in.

A basic test might be:

```text
Correct email
Correct password
→ Login successful
```

Error Guessing encourages us to think further.

### Email

Try:

```text
Empty
Spaces
Invalid format
Very long email
Missing @
Missing domain
Upper/lowercase variations
```

### Password

Try:

```text
Empty
Spaces
Very short password
Very long password
Special characters
Incorrect password
```

### Actions

Try:

```text
Multiple failed attempts
Rapidly clicking Login
Refreshing after login
Using Back after login
Submitting with both fields empty
```

These tests can reveal defects that basic positive testing might miss.

---

# Practical Example — Payment

Payment systems are particularly good candidates for Error Guessing.

Suppose:

> A customer can pay for an order.

We might ask:

> **What could go wrong?**

Potential tests:

```text
Payment succeeds
Payment fails
Payment remains pending
User refreshes during payment
User clicks Pay twice
Network disconnects during payment
Payment succeeds but confirmation is delayed
Payment fails after money is deducted
User retries a failed payment
User attempts payment for an out-of-stock product
```

Some of these may also involve **State Transition Testing**.

This demonstrates that test design techniques can complement each other.

---

# Error Guessing Questions

When testing a feature, ask yourself:

### Input

* What if the field is empty?
* What if it contains spaces?
* What if it contains unexpected characters?
* What if the value is extremely large?
* What if the value is negative?
* What if the value is zero?
* What if the value is null?
* What if the value has an unexpected format?

### Actions

* What if the user clicks twice?
* What if the user clicks very quickly?
* What if the user refreshes?
* What if the user presses Back?
* What if the user submits twice?
* What if the user abandons the process halfway?

### State

* What if the user performs this action from the wrong state?
* What if the previous operation is still pending?
* What if the user retries?
* What if the state changes while the user is performing an action?

### Data

* What if the data is duplicated?
* What if the data no longer exists?
* What if the data changes during the process?
* What if two users try to use the same resource?

---

# Error Guessing Checklist

A simple checklist can help during exploratory testing:

```text
□ Empty input
□ Null input
□ Spaces
□ Leading/trailing spaces
□ Invalid characters
□ Special characters
□ Zero
□ Negative values
□ Decimal values
□ Very large values
□ Very long text
□ Duplicate input
□ Invalid format
□ Unexpected data type
□ Repeated actions
□ Double-click
□ Refresh
□ Back button
□ Network interruption
□ Timeout
□ Retry
□ Invalid state
```

Not every item applies to every feature.

The tester should select the relevant ones.

---

# Advantages of Error Guessing

Error Guessing can:

* Find defects that formal techniques miss
* Make use of tester experience
* Target historically problematic areas
* Help identify unusual scenarios
* Complement structured test design techniques
* Be useful when requirements are incomplete
* Encourage testers to think like real users and potential failure sources

---

# Limitations of Error Guessing

Error Guessing also has limitations.

## 1. Depends on experience

A beginner may not know which unusual situations are common sources of defects.

Experience improves this skill over time.

---

## 2. Not systematic by itself

Two testers may come up with completely different error guesses.

Unlike BVA or Decision Tables, there isn't always a fixed formula for selecting tests.

---

## 3. Can miss important scenarios

If the tester doesn't think of a particular failure, it may never be tested.

This is why Error Guessing should **complement**, rather than replace, structured techniques.

---

# Building an Error Guessing Mindset

As you gain experience, start asking:

> **"If I were implementing this feature, where could I accidentally make a mistake?"**

For example:

### Requirement

> Users cannot cancel an order once it is **Out for Delivery**.

Think:

```text
Can I cancel before shipping?
Can I cancel after shipping?
Can I cancel when Out for Delivery?
What if I click Cancel twice?
What if I refresh immediately after cancelling?
What if cancellation is requested while the status is changing?
What if the order is already Delivered?
```

These questions help uncover scenarios beyond the obvious happy path.

---

# Key Takeaways

* **Error Guessing** is an experience-based test design technique.
* It uses tester knowledge, intuition, previous defects, and common failure patterns.
* The key question is:

  > **"What could go wrong?"**
* Common areas include:

  * Empty values
  * Null
  * Spaces
  * Invalid characters
  * Zero
  * Negative values
  * Large values
  * Unexpected data types
  * Repeated actions
  * Invalid states
* Error Guessing can produce both positive and negative tests.
* It works well alongside **EP, BVA, Decision Tables, and State Transition Testing**.
* It is not random testing; there should be a reason behind the test.
* It depends heavily on tester experience, so building a personal list of common failure patterns is valuable.

> **Good testers don't only ask, "Does it work?" They also ask, "How could this fail?"**
