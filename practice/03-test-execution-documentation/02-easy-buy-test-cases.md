# Easy Buy Test Cases

## Login
```text
Test Case ID: TC_LOGIN_001

Title: Verify that a registered user can log in with valid credentials.

Requirement: R1

Priority: High

Precondition: A registered user account exists.

Test Data:
- Email: user1@test.com
- Password: <test account password>

Steps:
1. Open the Login page.
2. Enter the registered email.
3. Enter the correct password.
4. Click Login.

Expected Result: The user is successfully logged in and redirected to the dashboard.

Actual Result: -

Status: Not Run

Postcondition: The user is logged in.

Notes: -
```

```text
Test Case ID: TC_LOGIN_002

Title: Verify that a user can not log in with an empty email.

Requirement: R2

Priority: High

Precondition: login page is accessible.

Test Data:
- Email: 
- Password: <test account password>

Steps:
1. Open the Login page.
2. Leave the email field empty.
3. Enter the password.
4. Click Login.

Expected Result: The user is not authenticated and receive an appropriate error message.

Actual Result: -

Status: Not Run

Postcondition: The user remains on the Login page.

Notes: -
```

```text
Test Case ID: TC_LOGIN_003

Title: Verify that a user cannot log in with wrong email and correct password.

Requirement: R4

Priority: High

Precondition: A registered user account exists and Login page is accessible.

Test Data:
- Email: wrongemail@test.com
- Password: <registered user's password>

Steps:
1. Open the Login page.
2. Enter the wrong email address.
3. Enter the correct password.
4. Click Login.

Expected Result: The user is not authenticated and receive an appropriate error message.

Actual Result: - 

Status: Not Run

Postcondition: The user remains on the Login page.

Notes: -
```

```text
Test Case ID: TC_LOGIN_004

Title: Verify that a user cannot log in with correct email and wrong password.

Requirement: R4

Priority: High

Precondition: A registered user account exists and Login page is accessible.

Test Data:
- Email: user1@test.com
- Password: WrongPassword@123

Steps:
1. Open the Login page.
2. Enter the registered email address.
3. Enter the wrong password.
4. Click Login.

Expected Result: The user is not authenticated and receive an appropriate error message.

Actual Result: - 

Status: Not Run

Postcondition: The user remains on the Login page.

Notes: -
```

```text
Test Case ID: TC_LOGIN_005

Title: Verify that a user cannot log in with wrong email and wrong password.

Requirement: R4

Priority: High

Precondition:  Login page is accessible.

Test Data:
- Email: wrongemail@test.com
- Password: WrongPassword@123

Steps:
1. Open the Login page.
2. Enter the wrong email address.
3. Enter the wrong password.
4. Click Login.

Expected Result: The user is not authenticated and receive an appropriate error message.

Actual Result: - 

Status: Not Run

Postcondition: The user remains on the Login page.

Notes: -
```

```text
Test Case ID: TC_LOGIN_006

Title: Verify that a user with an invalid email address cannot log in.

Requirement: R2

Priority: High

Precondition: Login page is accessible.

Test Data:
- Email: user1test
- Password: <registered user's password>

Steps:
1. Open the Login page.
2. Enter the invalid email address.
3. Enter the password.
4. Click Login.

Expected Result: The system displays an email validation error and the user remains on the Login page.

Actual Result: - 

Status: Not Run

Postcondition: The user remains on the Login page.

Notes: -
```

```text
Test Case ID: TC_LOGIN_007

Title: Verify that a user cannot log in with an empty password.

Requirement: R3

Priority: High

Precondition: Login page is accessible.

Test Data:
- Email: user1@test.com
- Password: “”

Steps:
1. Open the Login page.
2. Enter the registered email address.
3. Click Login.

Expected Result: The system displays an error indicating that the password is required and the user remains on the Login page.

Actual Result: - 

Status: Not Run

Postcondition: The user remains on the Login page.

Notes: -
```

```text
Test Case ID: TC_LOGIN_008

Title: Verify that a user cannot log in with a password of 7 characters.

Requirement: R3

Priority: High

Precondition: A registered user account exists with valid credentials.

Test Data:
- Email: user1@test.com
- Password: F@fgfh6

Steps:
1. Open the Login page.
2. Enter the registered email address.
3. Enter the password.
4. Click Login.

Expected Result: The system displays a password validation message indicating that the password must contain at least 8 characters.

Actual Result: - 

Status: Not Run

Postcondition: The user remains on the Login page.

Notes: -
```

```text
Test Case ID: TC_LOGIN_009

Title: Verify that a user can log in when the password meets the minimum 8-character requirement.

Requirement: R3

Priority: High

Precondition: A registered user account exists with valid credentials.

Test Data:
- Email: user2@test.com
- Password: F@fgfh62

Steps:
1. Open the Login page.
2. Enter the registered email address.
3. Enter the correct password.
4. Click Login.

Expected Result: The user is successfully logged in and redirected to the dashboard.

Actual Result: - 

Status: Not Run

Postcondition: The user is logged in.

Notes: -
```

```text
Test Case ID: TC_LOGIN_010

Title: Verify that a user can log in when the password meets the minimum 8-character requirement.

Requirement: R3

Priority: High

Precondition: A registered user account exists with valid credentials.

Test Data:
- Email: user3@test.com
- Password: F@fgfh623

Steps:
1. Open the Login page.
2. Enter the registered email address.
3. Enter the correct password.
4. Click Login.

Expected Result: The user is successfully logged in and redirected to the dashboard.

Actual Result: - 

Status: Not Run

Postcondition: The user is logged in.

Notes: -
```

## Product Search
```text
Test Case ID: TC_SEARCH_001

Title: Verify that users can search for products using valid keywords.

Requirement:R5

Priority: High

Precondition: Products page is accessible and there is at least one product that has the search keyword

Test Data:
- keyword: phone

Steps:
1. Open the Products page.
2. Enter the keyword in the search field.
3. Click Search.

Expected Result: Products matching the keyword are displayed.

Actual Result: - 

Status: Not Run

Postcondition: -

Notes: -
```

```text
Test Case ID: TC_SEARCH_002

Title: Verify that a search with no matching products displays an appropriate "No results" message.

Requirement:R6

Priority: High

Precondition: Products page is accessible

Test Data:
- keyword: qwertyproduct999

Steps:
1. Open the Products page.
2. Enter the keyword in the search field.
3. Click Search.

Expected Result: An appropriate "No results" message is displayed.

Actual Result: - 

Status: Not Run

Postcondition: -

Notes: -
```

```text
Test Case ID: TC_SEARCH_003

Title: Verify that submitting an empty search does not cause a system error.

Requirement:R7

Priority: High

Precondition: Products page is accessible

Test Data:
- keyword: “”

Steps:
1. Open the Products page.
2. Leave the search field empty.
3. Click Search.

Expected Result: The system handles the empty search without crashing or displaying a system error.

Actual Result: - 

Status: Not Run

Postcondition: -

Notes: -
```

```text
Test Case ID: TC_SEARCH_004

Title: Verify how the system handles special-character input

Requirement: Exploratory — no explicit requirement (R5–R7 provide context where applicable)

Priority: Meduim

Precondition: Products page is accessible

Test Data:
- keyword: “$*#>?-@”

Steps:
1. Open the Products page.
2. Enter the keyword.
3. Click Search.

Expected Result: The system handles the input without crashing. Observe the results and any message displayed.

Actual Result: - 

Status: Not Run

Postcondition: -

Notes: -
```

```text
Test Case ID: TC_SEARCH_005

Title: Verify how the system handles numbers-only input

Requirement: Exploratory — no explicit requirement (R5–R7 provide context where applicable)

Priority: Meduim

Precondition: Products page is accessible

Test Data:
- keyword: “123456”

Steps:
1. Open the Products page.
2. Enter the keyword.
3. Click Search.

Expected Result: The system handles the input without crashing. Observe whether matching products or a no-results message appear.

Actual Result: - 

Status: Not Run

Postcondition: -

Notes: -
```

```text
Test Case ID: TC_SEARCH_006

Title: Verify how the system handles input with leading and trailing spaces.

Requirement: Exploratory — no explicit requirement (R5–R7 provide context where applicable)

Priority: Meduim

Precondition: Products page is accessible

Test Data:
- keyword: “    phone  ”

Steps:
1. Open the Products page.
2. Enter the keyword.
3. Click Search.
The system handles the input without crashing. Observe whether leading and trailing spaces affect the results.The system does not crash.

Actual Result: - 

Status: Not Run

Postcondition: -

Notes: -
```

```text
Test Case ID: TC_SEARCH_007

Title: Verify how the system handles input with different letter casing.

Requirement: Exploratory — no explicit requirement (R5–R7 provide context where applicable)

Priority: Low

Precondition: Products page is accessible

Test Data:
- keyword: “pHoNE”

Steps:
1. Open the Products page.
2. Enter the keyword.
3. Click Search.

Expected Result: The system handles the input without crashing. Observe whether letter casing affects the results.

Actual Result: - 

Status: Not Run

Postcondition: -

Notes: -
```

## Cart
```text
Test Case ID: TC_CART_001

Title: Verify that a user can add an available product to the cart.

Requirement: R8

Priority: High

Precondition:
- Products page is accessible.
- At least one available product exists.

Test Data:
- Product: Phone
- Price: ₦50,000
- Quantity: 1

Steps:
1. Open the Products page.
2. Locate the Phone product.
3. Click Add to Cart.
4. Open the cart.

Expected Result:
- The product is added to the cart.
- The correct product name, price, and quantity are displayed.
- The cart reflects the added product.

Actual Result: -

Status: Not Run

Postcondition: The Phone product is in the cart.

Notes: -
```

```text
Test Case ID: TC_CART_002

Title: Verify that a user can increase and decrease product quantity in the cart.

Requirement: R9

Priority: High

Precondition:
- Products page is accessible.
- The Phone product is available and can be added to the cart.
- The cart contains one Phone.

Test Data:
- Product: Phone
- Unit price: ₦50,000
- Initial quantity: 1

Steps:
1. Open the cart.
2. Verify that the Phone quantity is 1.
3. Increase the quantity to 2.
4. Verify the displayed quantity.
5. Decrease the quantity to 1.
6. Verify the displayed quantity.

Expected Result:
- The quantity increases from 1 to 2.
- The quantity decreases from 2 to 1.
- The displayed quantity is correct after each action.

Actual Result: -

Status: Not Run

Postcondition: The Phone quantity is 1.

Notes: The behavior when decreasing the quantity below 1 is not specified in the current requirements.
```

```text
Test Case ID: TC_CART_003

Title: Verify that a user can remove a product from the cart.

Requirement: R10

Priority: High

Precondition:
- The cart contains at least one product.

Test Data:
- Product: Phone

Steps:
1. Open the cart.
2. Locate the Phone product.
3. Click Remove.
4. Check the cart contents.

Expected Result:
- The Phone product is removed from the cart.
- The removed product is no longer displayed in the cart.

Actual Result: -

Status: Not Run

Postcondition: The Phone product is no longer in the cart.

Notes: -
```

```text
Test Case ID: TC_CART_004

Title: Verify that the cart total is calculated correctly based on product prices and quantities.

Requirement: R11

Priority: High

Precondition:
- Products page is accessible.
- Two products are available.

Test Data:
- Phone: ₦250,000 × 2
- Headphone: ₦70,000 × 1
- Expected cart total: ₦570,000

Steps:
1. Add two Phones to the cart.
2. Add one Headphones product to the cart.
3. Open the cart.
4. Check the price, quantity, and subtotal for each product.
5. Verify the cart total.

Expected Result:
- Phone subtotal is ₦100,000.
- Headphones subtotal is ₦10,000.
- Cart total is ₦110,000, assuming no additional charges or discounts apply.

Actual Result: -

Status: Not Run

Postcondition: The cart contains two Phones and one Headphones product.

Notes: This test checks the sum of product prices and quantities. Delivery fees, discounts, and taxes are excluded unless specified by the requirements.
```

## Checkout
```text
Test Case ID: TC_CHECKOUT_001

Title: Verify that a user can proceed to checkout when the cart contains a product.

Requirement: R12

Priority: High

Precondition:
- Products page is accessible.
- At least one available product exists.
- The cart contains at least one product.

Test Data:
- Product: Phone
- Quantity: 1

Steps:
1. Open the cart.
2. Verify that the Phone is displayed.
3. Click Proceed to Checkout.

Expected Result:
- The user is taken to the checkout page.
- The checkout page is displayed without errors.

Actual Result: -

Status: Not Run

Postcondition: The user is on the checkout page.

Notes: -
```

```text
Test Case ID: TC_CHECKOUT_002

Title: Verify that required delivery information is validated before an order is placed.

Requirement: R13

Priority: High

Precondition:
- The cart contains at least one product.
- The user is on the checkout page.

Test Data:
- Delivery address: Empty
- Phone number: Empty

Steps:
1. Leave the required delivery information fields empty.
2. Click Place Order.
3. Observe the validation messages.

Expected Result:
- The order is not placed.
- Appropriate validation messages are displayed for the missing required fields.

Actual Result: -

Status: Not Run

Postcondition: The order remains unplaced.

Notes: Confirm which delivery fields are required by the application's requirements.
```

```text
Test Case ID: TC_CHECKOUT_003

Title: Verify that a user can place an order with valid checkout information.

Requirement: R14

Priority: High

Precondition:
- The cart contains at least one product.
- The user is on the checkout page.
- Valid delivery information is available.

Test Data:
- Product: Phone
- Quantity: 1
- Delivery address: 12 Market Road
- Phone number: 08012345678

Steps:
1. Open the checkout page.
2. Enter the required delivery information.
3. Review the order details.
4. Click Place Order.
5. Observe the system response.

Expected Result:
- The order is successfully placed.
- A confirmation message or order confirmation page is displayed.
- The order details are consistent with the submitted information.

Actual Result: -

Status: Not Run

Postcondition: The order is placed successfully.

Notes: Use a test environment and confirm the expected order confirmation behavior. The address and phone number are sample test data.
```

```text
Test Case ID: TC_CHECKOUT_004

Title: Verify that a user cannot proceed to checkout with an empty cart.

Requirement: R15

Priority: High

Precondition:
- The cart is empty.

Test Data:
- Cart contents: No products

Steps:
1. Open the cart.
2. Verify that no products are displayed.
3. Attempt to proceed to checkout, if the option is available.
4. Observe the system response.

Expected Result:
- The user cannot proceed to checkout.
- An appropriate message is displayed, or the checkout action is disabled.
- No order is created.

Actual Result: -

Status: Not Run

Postcondition: The cart remains empty, and no order is placed.

Notes: -
```