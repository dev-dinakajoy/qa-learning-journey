# Test Execution

## Login

**Test Case ID:** TC_LOGIN_001  
**Actual Result:** After clicking Login, the user is redirected to the dashboard.  
**Status:** Pass  
**Reason:** The actual result matches the expected result, the user was redirected to the dashboard.

**Test Case ID:** TC_LOGIN_002  
**Actual Result:** After clicking Login, the system displays the error “Invalid credentials" and the user remains on the Login page.  
**Status:** Fail  
**Reason:** The actual result does not match the expected result because the user received the wrong error message. The error should tell that the email is empty not invalid.

**Test Case ID:** TC_LOGIN_003  
**Actual Result:** After clicking Login, the system displays the error “Invalid email or password" and the user remains on the Login page.  
**Status:** Pass  
**Reason:** The actual result matches the expected result, and the user received the appropriate error message because the email was wrong.

**Test Case ID:** TC_LOGIN_004  
**Actual Result:** After clicking Login, the system displays the error “Invalid email or password" and the user remains on the Login page.  
**Status:** Pass 
**Reason:** The actual result matches the expected result. The system rejected the wrong password and displayed the expected error message.  

**Test Case ID:** TC_LOGIN_005  
**Actual Result:** After clicking Login, the system displays the error “Invalid email or password" and the user remains on the Login page.  
**Status:** Pass 
**Reason:** The actual result matches the expected result. The system rejected the wrong email and password and displayed the expected error message. 

**Test Case ID:** TC_LOGIN_006  
**Actual Result:** After clicking Login, the system displays the error “Please enter a valid email address." and the user remains on the Login page.  
**Status:** Pass  
**Reason:** The actual result matches the expected result. The system rejected the invalid email format and displayed the expected validation message.

**Test Case ID:** TC_LOGIN_007  
**Actual Result:** After clicking Login, the system displays the error “Invalid credentials" and the user remains on the Login page.  
**Status:** Fail  
**Reason:** The actual result does not match the expected result because the user received the wrong error message. The error should tell that the password is empty not invalid.

**Test Case ID:** TC_LOGIN_008  
**Actual Result:** The user is successfully logged in and redirected to the dashboard.    
**Status:** Fail  
**Reason:** The actual result does not match the expected result because the user logged in successfully. The system should throw error that indicates that the password must contain at least 8 characters.

**Test Case ID:** TC_LOGIN_009  
**Actual Result:** The user is successfully logged in and redirected to the dashboard.  
**Status:** Pass  
**Reason:** The actual result matches the expected result, the user was redirected to the dashboard.

**Test Case ID:** TC_LOGIN_010  
**Actual Result:** The user is successfully logged in and redirected to the dashboard.  
**Status:** Pass  
**Reason:** The actual result matches the expected result, the user was redirected to the dashboard.

## Product Search
**Test Case ID:** TC_SEARCH_001  
**Actual Result:** After clicking Search, matching products were displayed.  
**Status:** Pass  
**Reason:** The actual result matches the expected result, the matching products were displayed.

**Test Case ID:** TC_SEARCH_002  
**Actual Result:** After clicking Search, the system displays "No results" message.  
**Status:** Pass  
**Reason:** The actual result matches the expected result because the user received the correct error message.

**Test Case ID:** TC_SEARCH_003  
**Actual Result:** After clicking Search, the system displays no error and all products were displayed.  
**Status:** Pass  
**Reason:** The actual result matches the expected result, the system displayed all products.

**Test Case ID:** TC_SEARCH_004  
**Actual Result:** After clicking Search, the system displays the error “Invalid keyword".  
**Status:** Pass 
**Reason:** The system rejected the wrong keyword and displayed the appropriate error message.  

**Test Case ID:** TC_SEARCH_005  
**Actual Result:** After clicking Search, products that contains the numbers in their names were displayed.  
**Status:** Pass  
**Reason:** The matching products were displayed.

**Test Case ID:** TC_SEARCH_006   
**Actual Result:** After clicking Search, matching products were displayed.  
**Status:** Pass  
**Reason:** The system trimmed the spaces and returned the matching products.

**Test Case ID:** TC_SEARCH_007  
**Actual Result:** After clicking Search, matching products were displayed.  
**Status:** Pass  
**Reason:** The system converted the keyword to lowercase and returned the matching products.

## Cart
**Test Case ID:** TC_CART_001  
**Actual Result:** After selecting product and clicking "Add to cart", the product was successfully added to cart.  
**Status:** Pass  
**Reason:** The actual result matches the expected result, the product was added to cart.

**Test Case ID:** TC_CART_002  
**Actual Result:** Clicking the arrow button up and down increases and decreases product quantity respectively in cart.  
**Status:** Pass  
**Reason:** The actual result matches the expected result, user can increase and decrease product quantity in the cart 

**Test Case ID:** TC_CART_003  
**Actual Result:** After clicking the "X" button besides the product in cart, the product was successfully removed from cart.  
**Status:** Pass  
**Reason:** The actual result matches the expected result, products can be removed from cart.

**Test Case ID:** TC_CART_004  
**Actual Result:** After adding items (two phones ₦250,000 and one headphone ₦70,000) to cart and increasing or decreasing the quantity of products, the total is calculated correctly (₦570,000).  
**Status:** Pass 
**Reason:** The system calculates the total amount in cart correctly. 

## Checkout
**Test Case ID:** TC_CHECKOUT_001  
**Actual Result:** Clicking "Checkout" redirects to the checkout page.  
**Status:** Pass  
**Reason:** The actual result matches the expected result, user is directed to the checkout page.

**Test Case ID:** TC_CHECKOUT_002  
**Actual Result:** Before you can place an order, all users delivery information are validated. 
**Status:** Pass  
**Reason:** The actual result matches the expected result, users delivery information are validated.

**Test Case ID:** TC_CHECKOUT_003  
**Actual Result:** User can place order after filling checkout information.  
**Status:** Pass  
**Reason:** The actual result matches the expected result, users can place an order after filling out valid checkout information.

**Test Case ID:** TC_CHECKOUT_004  
**Actual Result:** User cannot proceed to checkout when cart is empty.  
**Status:** Pass 
**Reason:** The actual result matches the expected result, users cannot proceed to checkout with an empty cart.
