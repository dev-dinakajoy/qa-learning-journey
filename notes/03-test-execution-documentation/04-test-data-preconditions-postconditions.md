# Test Data, Preconditions & Postconditions

Three important parts of a professional test case are:

* **Test Data** — what information or values we use during testing
* **Preconditions** — what must be true before the test starts
* **Postconditions** — what state the system should be in after the test

These help make test cases **clear, repeatable, and executable**.

---

# 1. Test Data

## What is Test Data?

**Test data** is the information used to execute a test case.

It can include:

* Usernames
* Email addresses
* Passwords
* Product names
* Search keywords
* Numbers
* Dates
* File uploads
* Addresses
* Account balances
* Form values
* Other inputs required by the application

### Example

For a login test:

```text
Email: user1@test.com
Password: <test account password>
```

For product search:

```text
Keyword: phone
```

For a password boundary test:

```text
Password: F@fgfh6
Length: 7 characters
```

The test data should match the condition being tested.

---

# Why Test Data Matters

Without test data, a test case may not be reproducible.

Compare:

### Poor

> Enter a valid email.

### Better

> Enter `user1@test.com`.

The second version tells the tester exactly what data to use.

---

# Types of Test Data

Different test conditions require different types of test data.

## 1. Valid Test Data

Data that should be accepted by the system.

Example:

```text
Email: user1@test.com
```

Used for positive testing.

---

## 2. Invalid Test Data

Data that violates a system rule.

Example:

```text
Email: user1test
```

If the requirement says an email must have a valid email format, this is an invalid input.

---

## 3. Boundary Test Data

Values around the limits defined by a requirement.

Suppose:

> Password must contain at least 8 characters.

Useful test data includes:

| Value        | Classification |
| ------------ | -------------- |
| 7 characters | Below boundary |
| 8 characters | Boundary       |
| 9 characters | Above boundary |

This is an application of **Boundary Value Analysis**.

---

## 4. Empty Test Data

Used to test required fields and empty-input behavior.

Example:

```text
Email: ""
Password: ""
```

---

## 5. Realistic Test Data

Test data should resemble data users would realistically enter.

For example:

```text
Product:
iPhone 15
```

is generally more useful for a product search test than:

```text
Product:
abcdef123
```

unless the purpose of the test is specifically to verify behavior for nonexistent data.

---

## 6. Special or Unexpected Test Data

These values can be useful for exploratory testing and error guessing.

Examples:

```text
Search keyword: @#$%
Search keyword: 123456
Search keyword: <script>
Search keyword: very-long-input...
```

The expected behavior should not be invented simply because we're testing an unusual input.

If the requirement does not define the behavior, we can classify the test as **exploratory/error-guessing** and document what actually happens.

---

# Test Data and Test Design

Test design techniques help us decide which test data is useful.

For example:

### Requirement

> Password must contain at least 8 characters.

### Equivalence Partitioning

We can divide password lengths into:

```text
Less than 8 → Invalid
8 or more → Valid
```

### Boundary Value Analysis

We can select:

```text
7 → Invalid
8 → Valid
9 → Valid
```

Therefore, test data isn't chosen randomly.

It should be selected based on:

* Requirements
* Test design techniques
* Business rules
* Realistic user behavior
* Exploratory testing considerations

---

# 2. Preconditions

## What is a Precondition?

A **precondition** is a condition that must be satisfied before a test case can be executed.

It establishes the starting state for the test.

### Example

For valid login:

```text
Precondition:
A registered user account exists with valid credentials.
```

For adding a product to a cart:

```text
Precondition:
The user is logged in and an available product exists.
```

For checkout:

```text
Precondition:
The user is logged in and has at least one product in the cart.
```

---

# Why Preconditions Matter

Imagine a test case says:

> Verify that a user can proceed to checkout.

But it doesn't say whether:

* The user should be logged in
* The cart should contain a product
* The checkout page should already be open

Another tester may execute the test differently.

A clear precondition removes this ambiguity.

---

# Good vs Poor Preconditions

### Poor

> User is ready.

This is too vague.

### Better

> A registered user account exists and the user is logged in.

### Poor

> Product is available.

### Better

> The Products page is accessible and at least one product is available for purchase.

A good precondition should describe a **specific starting state**.

---

# Preconditions Should Not Repeat the Steps

Avoid unnecessary duplication.

For example:

### Poor

```text
Precondition:
User is on the Login page.

Steps:
1. Open the Login page.
```

This can be contradictory because the test is already saying the Login page is a precondition and then instructing the tester to open it.

Instead, decide what the actual starting state should be.

For example:

```text
Precondition:
The application is accessible.

Steps:
1. Open the Login page.
```

Or:

```text
Precondition:
The Login page is accessible.

Steps:
1. Enter the registered email address.
```

Both can be valid depending on how the test is designed.

---

# 3. Postconditions

## What is a Postcondition?

A **postcondition** describes the state of the system after the test has been executed.

It tells us what state the application should be left in.

### Successful Login

```text
Postcondition:
The user is logged in.
```

### Failed Login

```text
Postcondition:
The user remains unauthenticated and on the Login page.
```

### Add Product

```text
Postcondition:
The selected product is present in the shopping cart.
```

### Remove Product

```text
Postcondition:
The selected product is no longer present in the shopping cart.
```

---

# Why Postconditions Matter

Postconditions are particularly useful when a test changes application state.

For example:

```text
TC_CART_001
Add product to cart
        ↓
Product is now in cart
        ↓
Next test may be affected
```

If the tester doesn't understand the resulting state, later tests can be affected.

Postconditions therefore help with:

* Test isolation
* Test sequencing
* Environment cleanup
* Repeatability
* Understanding state changes

---

# Preconditions vs Postconditions

The easiest way to remember the difference:

> **Precondition = what must be true before the test.**

> **Postcondition = what should be true after the test.**

### Example

```text
             TEST
              ↓
Precondition → Login → Postcondition

User account       User is
exists             logged in
```

Another example:

```text
Precondition:
User is logged in.
Product is available.

       ↓

Test:
Add product to cart.

       ↓

Postcondition:
Product is in the cart.
```

---

# Complete Example

```text
Test Case ID:
TC_CART_001

Title:
Verify that a user can add an available product to the shopping cart.

Requirement:
R8

Priority:
High

Precondition:
The user is logged in and an available product exists.

Test Data:
Product: iPhone 15

Steps:
1. Open the Products page.
2. Find the iPhone 15 product.
3. Click Add to Cart.

Expected Result:
The iPhone 15 is added to the shopping cart.

Actual Result:
-

Status:
Not Run

Postcondition:
The iPhone 15 is present in the shopping cart.

Notes:
-
```

Notice how each part has a different purpose:

```text
Precondition
↓
Establish the starting state

Test Data
↓
Provide the values needed

Steps
↓
Perform the test

Expected Result
↓
Define what should happen

Postcondition
↓
Define the resulting state
```

---

# Choosing Appropriate Test Data

Before writing test data, ask:

### 1. What requirement am I testing?

Example:

> Password must contain at least 8 characters.

### 2. What condition am I testing?

Example:

> Password below the minimum length.

### 3. Which test design technique applies?

Example:

> Boundary Value Analysis.

### 4. What value represents the condition?

Example:

> 7 characters.

This produces:

```text
Requirement
      ↓
Condition
      ↓
Test Design Technique
      ↓
Test Data
```

---

# Test Data Should Not Create Ambiguity

Consider this test:

```text
Requirement:
No products match the search keyword → display "No results".

Test Data:
^hg88***ee
```

The problem is that the test data contains special characters.

If the application returns no results, we don't know whether:

* The keyword simply didn't match a product, or
* The application handled special characters in a particular way.

A cleaner test would use:

```text
Keyword:
qwertyproduct999
```

Now the test specifically targets:

> **No matching product exists.**

Special characters can be tested separately as an exploratory/error-guessing test.

This is an important principle:

> **Choose test data that isolates the condition being tested.**

---

# Test Data Reuse

Test data can sometimes be reused across test cases.

For example:

```text
user1@test.com
```

could be used for several login tests.

However, avoid reusing data when one test changes the state needed by another test.

For example:

```text
TC_CART_001:
Add iPhone 15 to cart.

TC_CART_002:
Remove iPhone 15 from cart.
```

If TC_CART_002 depends on TC_CART_001, that dependency should be documented.

Ideally, tests should be as independent as reasonably possible.

---

# Test Data Security

Real applications often contain sensitive information.

Do not put real:

* Passwords
* Credit card numbers
* API keys
* Authentication tokens
* Personal information

into publicly accessible QA documentation or repositories.

For learning projects, use clearly fictional test data.

For example:

```text
user1@test.com
```

is appropriate for a practice project.

A real user's credentials are not.

---

# Test Data, Preconditions and Postconditions Together

These three concepts work together.

Consider a checkout test:

```text
Precondition:
User is logged in.
Cart contains at least one product.

Test Data:
Product: iPhone 15
Quantity: 2
Delivery address: Test Address

Steps:
1. Open the cart.
2. Click Checkout.
3. Enter required delivery information.
4. Click Place Order.

Expected Result:
The order is successfully placed.

Postcondition:
The order appears in the user's order history.
```

The test becomes much easier to understand because the starting state, input data, and resulting state are clearly documented.

---

# Common Mistakes

## Mistake 1: Vague test data

### Poor

> Enter a valid email.

### Better

> `user1@test.com`

---

## Mistake 2: Missing preconditions

### Poor

> Click Add to Cart.

Without knowing whether the user is logged in or whether the product exists, the test may not be executable.

---

## Mistake 3: Putting steps in the precondition

### Poor

> Precondition: Open the Login page.

Opening the Login page is an action and normally belongs in the Steps unless the test specifically requires the page to already be open.

---

## Mistake 4: Using ambiguous test data

### Poor

> Search: `^hg88***ee`

when testing "no matching products."

The special characters introduce another variable.

### Better

> Search: `qwertyproduct999`

---

## Mistake 5: Forgetting state changes

If a test adds an item to a cart, changes a password, creates an account, or places an order, consider what state the application is left in.

This is where the postcondition becomes useful.

---

# Practical Checklist

Before executing a test case, check:

### Test Data

* [ ] Is all required data provided?
* [ ] Does the data match the condition being tested?
* [ ] Is the data realistic where appropriate?
* [ ] Have boundary values been considered?
* [ ] Have sensitive credentials been avoided?

### Preconditions

* [ ] Is the required starting state clear?
* [ ] Can the tester establish the precondition?
* [ ] Does the precondition avoid unnecessary duplication of the steps?

### Postconditions

* [ ] Is the resulting system state clear?
* [ ] Does the test modify application data or state?
* [ ] Does the resulting state need to be cleaned up?
* [ ] Could the state affect another test?

---

# Key Takeaways

Remember:

```text
Precondition
"What must be true before I start?"

        ↓

Test Data
"What information or values do I need?"

        ↓

Steps
"What actions do I perform?"

        ↓

Expected Result
"What should happen?"

        ↓

Actual Result
"What actually happened?"

        ↓

Postcondition
"What state is the system left in?"
```

Good test data makes a test **meaningful**.

Clear preconditions make a test **executable**.

Clear postconditions make a test **repeatable and easier to manage**.

Together, they help produce test cases that another tester can execute confidently without having to guess what the original tester intended.
