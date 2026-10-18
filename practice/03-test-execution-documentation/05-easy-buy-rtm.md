# Easy Buy Requirements Traceability Matrix (RTM)

| Requirement | Test Case ID | Status | Defect |
|---|---|---|---|
| R1 — Valid Login | TC_LOGIN_001 | Pass | - |
| R2 — Email Validation | TC_LOGIN_002 | Fail | BUG-LOGIN-001 |
| R2 — Email Validation | TC_LOGIN_006 | Pass | - |
| R3 — Password Validation | TC_LOGIN_007 | Fail | BUG-LOGIN-002 |
| R3 — Password Validation | TC_LOGIN_008 | Fail | BUG-LOGIN-003 |
| R3 — Password Validation | TC_LOGIN_009 | Pass | - |
| R3 — Password Validation | TC_LOGIN_010 | Pass | - |
| R4 — Invalid Credentials | TC_LOGIN_003 | Pass | - |
| R4 — Invalid Credentials | TC_LOGIN_004 | Pass | - |
| R4 — Invalid Credentials | TC_LOGIN_005 | Pass | - |
| R5 — Valid Search | TC_SEARCH_001 | Pass | - |
| R6 — No Search Results | TC_SEARCH_002 | Pass | - |
| R7 — Empty Search | TC_SEARCH_003 | Pass | - |
| R8 — Add Product | TC_CART_001 | Pass | - |
| R9 — Update Quantity | TC_CART_002 | Pass | - |
| R10 — Remove Product | TC_CART_003 | Pass | - |
| R11 — Cart Total | TC_CART_004 | Pass | - |
| R12 — Proceed to Checkout | TC_CHECKOUT_001 | Pass | - |
| R13 — Required Delivery Information | TC_CHECKOUT_002 | Pass | - |
| R14 — Valid Checkout | TC_CHECKOUT_003 | Pass | - |
| R15 — Empty Cart Checkout | TC_CHECKOUT_004 | Pass | - |

## Exploratory test cases

| Test Case ID | Related Requirements | Status | Defect |
|---|---|---|---|
| TC_SEARCH_004 — Special Characters | R5–R7, where applicable | Pass | - |
| TC_SEARCH_005 — Numbers-Only Input | R5–R7, where applicable | Pass | - |
| TC_SEARCH_006 — Leading/Trailing Spaces | R5–R7, where applicable | Pass | - |
| TC_SEARCH_007 — Letter Casing | R5–R7, where applicable | Pass | - |