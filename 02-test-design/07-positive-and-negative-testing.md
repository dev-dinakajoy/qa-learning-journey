# Positive and Negative Testing

## What I learned

**Positive testing** and **negative testing** are two simple but important ways to think about test cases.

They help me answer two questions:

* **Positive testing:** Does the system work when I give it valid input?
* **Negative testing:** Does the system behave correctly when I give it invalid or unexpected input?

The goal is not just to prove that the system works. I also want to know that it **handles incorrect usage properly**.

---

## ✅ Positive Testing

Positive testing checks whether the application behaves as expected with **valid inputs and valid actions**.

### Example: Phone Number

Requirement:

> Phone number must contain exactly 11 digits.

| Test Input    | Expected Result |
| ------------- | --------------- |
| `08097546732` | Accepted ✅      |
| `08123456789` | Accepted ✅      |

These are positive tests because the inputs satisfy the requirement.

### Another example: Login

| Email   | Password | Expected Result  |
| ------- | -------- | ---------------- |
| Correct | Correct  | Login succeeds ✅ |

The user is providing valid credentials, so the expected behavior is successful login.

---

## ❌ Negative Testing

Negative testing checks how the application behaves when given **invalid, unexpected, or unsupported input/actions**.

Using the same phone number requirement:

| Test Input     | Expected Result                    |
| -------------- | ---------------------------------- |
| `0809754673`   | Error — must be 11 digits ❌        |
| `080975467322` | Error — must be 11 digits ❌        |
| `abcdefghijk`  | Error — only numbers allowed ❌     |
| `""`           | Error — phone number is required ❌ |
| `"   "`        | Error — spaces not allowed ❌       |
| `null`         | Error ❌                            |

The system is expected to **reject the invalid input gracefully**.

A negative test is therefore not necessarily a test that should fail.

For example:

> Enter an invalid phone number → system displays an appropriate validation error.

The test **passes** if the application correctly rejects the invalid input.

---

## 🧠 An important distinction

I initially thought:

> Positive test = test passes
> Negative test = test fails

That's not correct.

**Positive and negative testing describe the type of input or behavior being tested, not whether the test case passes or fails.**

For example:

```text
Test: Enter an invalid phone number
Expected: Display "Phone number must be 11 digits"
Actual: Displayed the correct error message

Result: PASS ✅
```

This is a **negative test that passed**.

---

## Positive vs Negative Testing

| Positive Testing                    | Negative Testing                    |
| ----------------------------------- | ----------------------------------- |
| Uses valid input                    | Uses invalid/unexpected input       |
| Checks expected successful behavior | Checks error handling and rejection |
| Verifies happy paths                | Verifies unhappy paths              |
| Example: valid login                | Example: invalid password           |
| Example: valid amount               | Example: negative amount            |

Both are necessary.

---

## Example: Transfer Amount

Suppose a banking application has this requirement:

> Users can transfer between **₦5,000 and ₦500,000**.

### Positive tests

| Input    | Expected           |
| -------- | ------------------ |
| ₦5,000   | Transfer allowed ✅ |
| ₦20,000  | Transfer allowed ✅ |
| ₦500,000 | Transfer allowed ✅ |

### Negative tests

| Input           | Expected |
| --------------- | -------- |
| ₦4,999          | Reject ❌ |
| ₦500,001        | Reject ❌ |
| `abc`           | Reject ❌ |
| Empty           | Reject ❌ |
| Negative amount | Reject ❌ |

Here, I can combine **Positive/Negative Testing with Equivalence Partitioning and Boundary Value Analysis**.

For example:

* **EP:** test a representative valid amount and invalid amounts.
* **BVA:** test ₦4,999, ₦5,000, ₦5,001 and ₦499,999, ₦500,000, ₦500,001.
* **Positive testing:** focus on valid transfer amounts.
* **Negative testing:** focus on invalid amounts and unexpected input.

---

## Positive and Negative Testing with Login

Consider:

> A user must provide a valid email and password to log in.

### Positive tests

| Email   | Password | Expected         |
| ------- | -------- | ---------------- |
| Correct | Correct  | Login succeeds ✅ |

### Negative tests

| Email     | Password  | Expected           |
| --------- | --------- | ------------------ |
| Correct   | Incorrect | Login rejected ❌   |
| Incorrect | Correct   | Login rejected ❌   |
| Incorrect | Incorrect | Login rejected ❌   |
| Empty     | Correct   | Validation error ❌ |
| Correct   | Empty     | Validation error ❌ |

This can also be combined with **Decision Table Testing** because multiple conditions affect the outcome.

---

## Positive and Negative Testing in Real Applications

I can apply these ideas to almost any feature.

### Registration

**Positive:**

* Valid name
* Valid email
* Valid password
* Required fields completed

**Negative:**

* Invalid email
* Weak password
* Empty required field
* Existing email
* Unsupported characters

### Checkout

**Positive:**

* Logged-in user
* Item available
* Valid address
* Successful payment

**Negative:**

* Empty cart
* Out-of-stock item
* Invalid address
* Failed payment
* Expired payment method

### Order cancellation

**Positive:**

* Cancel an order while cancellation is allowed

**Negative:**

* Try to cancel an order after it has been shipped
* Try to cancel an already cancelled order
* Try to cancel a completed order

---

## How I use Positive and Negative Testing

When I receive a requirement, I can ask:

### 1. What should work?

These become my **positive tests**.

### 2. What should not work?

These become my **negative tests**.

### 3. What could go wrong?

This leads me toward **negative testing and error guessing**.

### 4. Are there boundaries?

Use **Boundary Value Analysis**.

### 5. Are there different groups of inputs?

Use **Equivalence Partitioning**.

### 6. Are there multiple conditions?

Use **Decision Table Testing**.

### 7. Does the feature move through different states?

Use **State Transition Testing**.

This is why I don't have to rely on only one test design technique.

---

## 🧪 Practice Exercise

Consider this requirement:

> A product quantity must be between **1 and 10**.

Create:

### Positive tests

Write at least **3 valid test cases**.

Example:

```text
1
5
10
```

### Negative tests

Write at least **5 invalid test cases**.

Think about:

```text
0
11
-1
"abc"
empty
```

Then apply:

* **Equivalence Partitioning**
* **Boundary Value Analysis**
* **Positive Testing**
* **Negative Testing**

---

## 🧠 What clicked for me

Positive and negative testing aren't separate complicated techniques.

They are ways of looking at my tests:

> **"What should work?"** → Positive testing
> **"What should happen when things go wrong?"** → Negative testing

The real strength comes from combining them with other test design techniques.

---

## 💡 Key Takeaway

A good test suite should not only verify that **valid inputs work**.

It should also verify that the application **handles invalid inputs and unexpected situations correctly**.

**Positive testing checks what should work.
Negative testing checks how the system handles what shouldn't work.**

Together, they help me build more complete and realistic test coverage.

---

## 🔗 Related

* [Equivalence Partitioning](02-equivalence-partitioning.md)
* [Boundary Value Analysis](03-boundary-value-analysis.md)
* [Decision Table Testing](04-decision-table-testing.md)
* [State Transition Testing](05-state-transition-testing.md)
* [Error Guessing](06-error-guessing.md)
