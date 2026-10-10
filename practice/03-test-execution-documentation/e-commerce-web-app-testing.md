# E-Commerce Web App Testing

This covers a realistic QA workflow from understanding requirements through test planning, test design, execution, defect reporting, and test reporting.

## Project Overview

### Project

**Easy Buy: An E-commerce Web Application**

### Objective

To test the core functionality of an e-commerce application and identify defects before release.

The application allows users to:

* Register
* Log in
* Search for products
* View products
* Add products to cart
* Update cart quantities
* Remove products from cart
* Proceed to checkout

## QA Workflow

I followed this workflow:

```text
Requirements
     ↓
Test Plan
     ↓
Test Scenarios
     ↓
Test Cases
     ↓
Test Data
     ↓
Test Execution
     ↓
Pass / Fail / Blocked / Not Run
     ↓
Bug Reports
     ↓
Retesting
     ↓
Regression Testing
     ↓
Test Summary Report
     ↓
RTM
```

## Project Requirements

### Login Requirements

- R1 — Valid Login: 
A registered user who enters a valid email address and correct password should be successfully logged in and redirected to the dashboard.

- R2 — Email Validation:
The email field is required and must contain a valid email format.

- R3 — Password Validation:
The password field is required and must contain at least 8 characters.

- R4 — Invalid Credentials:
A user who enters invalid credentials should not be authenticated and should receive an appropriate error message.

### Product Search Requirements

- R5 — Valid Search:
When a user searches using a keyword, products matching the keyword should be displayed.

- R6 — No Search Results:
When no products match the search keyword, the system should display an appropriate "No results" message.

- R7 — Empty Search:
Submitting an empty search should not cause a system error.

### Cart Requirements

- R8 — Add Product:
A user should be able to add an available product to the shopping cart.

- R9 — Update Quantity:
A user should be able to increase or decrease the quantity of a product in the cart.

- R10 — Remove Product:
A user should be able to remove a product from the cart.

- R11 — Cart Total:
The cart total should accurately reflect the prices and quantities of the products in the cart.

### Checkout Requirements

- R12 — Proceed to Checkout:
A user with at least one product in the cart should be able to proceed to checkout.

- R13 — Required Delivery Information:
Required delivery information must be provided before an order can be placed.

- R14 — Valid Checkout:
A user who provides valid checkout information should be able to place an order.

- R15 — Empty Cart Checkout:
A user should not be able to proceed to checkout when the cart is empty.

## Testing Scope

### In Scope

The project will cover:

- User Authentication
  * Login
  * Email validation
  * Password validation
  * Invalid credentials

- Product Search
  * Valid searches
  * No-result searches
  * Empty searches
  * Exploratory search conditions

- Shopping Cart
  * Adding products
  * Quantity changes
  * Removing products
  * Cart totals

- Checkout
  * Checkout access
  * Delivery information validation
  * Empty-cart behavior

### Out of Scope

The following areas are outside the current project scope:

* Password reset
* Payment gateway integration
* Actual payment processing
* Order placement
* Delivery processing
* Third-party logistics
* Email delivery
* SMS notifications

Out-of-scope features may be mentioned during exploratory testing if encountered, but they will not be part of the planned test coverage.

## Testing Types

I practiced several testing types during this project.

### Functional Testing

I verified the application functionality behaves according to requirements.

Example: I Verified that a user can add a product to the cart.

### Regression Testing

After changes or fixes, I verified that previously working functionality still works.

Example: After fixing login, I executed related login tests again.

### Exploratory Testing

I explored the application beyond the predefined test cases to discover unexpected behavior.

Example: I entered unusual search inputs and observed how the application responds.

### Negative Testing

I verified that the system handles invalid inputs and actions appropriately.

Example: I attempted to log in with an incorrect password.

### Smoke Testing

I performed a small set of critical tests to determine whether the application is stable enough for further testing.

Example:

```text
Open application
     ↓
Login
     ↓
Search product
     ↓
Add product to cart
     ↓
Open checkout
```

### Usability Testing

I observed whether the application is understandable and easy to use.

Example:
* Are error messages understandable?
* Are important buttons easy to find?
* Is navigation clear?

### Compatibility Testing

I verified behavior across supported environments.

For this project, examples include:

* Chrome
* Firefox
* Desktop
* Android

## Test Design Techniques

### Equivalence Partitioning

I divided input values into groups that are expected to behave similarly.

Example: Password minimum length:

```text
Invalid: < 8 characters

Valid: ≥ 8 characters
```

### Boundary Value Analysis

I tested values around boundaries.

For the 8-character minimum:

```text
7 characters -> Invalid
8 characters -> Valid
9 characters -> Valid
```

### Decision Table Testing

This test is useful when multiple conditions determine an outcome.

Example - Checkout:

| Cart           | Delivery Information | Expected             |
| -------------- | -------------------- | -------------------- |
| Empty          | Valid                | Checkout unavailable |
| Product exists | Missing              | Validation message   |
| Product exists | Valid                | Order can be placed  |

### State Transition Testing

This test is useful for features whose behavior changes based on state.

Example:

```text
Cart Empty
    ↓
Add Product
    ↓
Cart Contains Product
    ↓
Remove Product
    ↓
Cart Empty
```

### Error Guessing

I used experience (both as a developer) and common failure patterns to identify additional tests.

Examples:
* Empty values
* Special characters
* Very long input
* Unexpected input types
* Repeated clicks
* Rapid actions
* Invalid combinations

### Positive Testing

I verified that valid inputs produce the expected successful behavior.

Example: Log in using valid credentials.

### Negative Testing

I verified that invalid inputs or actions are handled correctly.

Example: Log in using an incorrect password.

## Test Scenarios

### Login

```text
TS_LOGIN_001
Verify that a registered user can log in with valid credentials.

TS_LOGIN_002
Verify that the system validates the email field.

TS_LOGIN_003
Verify that the system validates the password minimum length.

TS_LOGIN_004
Verify that a user cannot log in with invalid credentials.
```

### Product Search

```text
TS_SEARCH_001
Verify that products can be searched using a valid keyword.

TS_SEARCH_002
Verify that an appropriate message is displayed when no products match the search.

TS_SEARCH_003
Verify that submitting an empty search does not cause a system error.

TS_SEARCH_004
Explore how search handles special-character input.

TS_SEARCH_005
Explore how search handles numbers-only input.
```

The first three are directly tied to documented requirements.

The last two are exploratory/error-guessing scenarios because the current requirements do not explicitly define those behaviors.

### Cart

```text
TS_CART_001
Verify that a user can add a product to the cart.

TS_CART_002
Verify that a user can increase and decrease product quantity.

TS_CART_003
Verify that a user can remove a product from the cart.

TS_CART_004
Verify that the cart total is calculated correctly.
```

### Checkout

```text
TS_CHECKOUT_001
Verify that a user can proceed to checkout when the cart contains a product.

TS_CHECKOUT_002
Verify that required delivery information is validated.

TS_CHECKOUT_003
Verify that a user can place an order with valid checkout information.

TS_CHECKOUT_004
Verify that a user cannot proceed to checkout with an empty cart.
```

## Test Case Design

Each scenario was be broken down into detailed test cases.

```text
TS_LOGIN_003
Verify that the system validates the password minimum length.
```

Apply Boundary Value Analysis.

Requirement: Password must contain at least 8 characters.

Test cases:
```text
TC_LOGIN_008 -> 7 characters
TC_LOGIN_009 -> 8 characters
TC_LOGIN_010 -> 9 characters
```
Test cases on [easy-buy-test-cases.md](./easy-buy-test-cases.md)
