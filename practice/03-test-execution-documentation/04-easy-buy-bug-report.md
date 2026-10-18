# Easy Buy Test Cases

## Login
```text
Bug ID: BUG-LOGIN-001

Title: Login displays "Invalid credentials" when the email field is empty.

Requirement: R2 — Email Validation

Test Case ID: TC_LOGIN_002

Severity: Medium

Priority: Medium

Status: New

Environment: 
- Browser: Chrome
- Environment: QA
- Device: Desktop

Preconditions:
- The Login page is accessible.
- The user is logged out.

Steps to Reproduce:
1. Open the Login page.
2. Leave the email field empty.
3. Enter a password.
4. Click Login.
5. Observe the validation message.

Expected Result:
The system should display an appropriate validation message indicating that the email field is required. The user should remain on the Login page and should not be authenticated.

Actual Result:
The system displays "Invalid credentials" and the user remains on the Login page.

Impact:
The user receives a misleading error message that does not identify the missing required field, making it harder to understand how to correct the input.

Evidence:
- Screenshot of the Login page showing the error message.
- Test execution record for TC_LOGIN_002.

Notes:
The defect concerns the email validation message. The system correctly prevents authentication, but the displayed message does not meet the expected behavior.
```

```text
Bug ID: BUG-LOGIN-002

Title: Login displays "Invalid credentials" when the password field is empty.  

Requirement: R3 — Password Validation

Test Case ID: TC_LOGIN_007

Severity: Medium

Priority: Medium

Status: New

Environment: 
- Browser: Chrome
- Environment: QA
- Device: Desktop

Preconditions:
- The Login page is accessible.
- A registered user account exists.

Steps to Reproduce:
1. Open the Login page.
2. Enter a registered email address.
3. Leave the password field empty.
4. Click Login.
5. Observe the validation message.

Expected Result:
The system should display an appropriate validation message indicating that the password is required. The user should remain on the Login page and should not be authenticated.

Actual Result:
The system displays **"Invalid credentials"** and the user remains on the Login page.

Impact:
The user is not informed that the password field is empty. This creates a confusing validation experience and does not meet the password-required validation requirement.

Evidence:
- Screenshot of the Login page showing the error message.
- Test execution record for TC_LOGIN_007.

Notes: 
The defect concerns the password validation message. Authentication is prevented, but the displayed message does not meet the expected behavior.
```

```text
Bug ID: BUG-LOGIN-003

Title: Login allows authentication with a seven-character password despite the eight-character minimum requirement.

Requirement: R3 — Password Validation

Test Case ID: TC_LOGIN_008

Severity: High

Priority: High

Status: New

Environment: 
- Browser: Chrome
- Environment: QA
- Device: Desktop

Preconditions:
- A registered user account exists.
- The Login page is accessible.
- The test account and password data are available.

Steps to Reproduce:
1. Open the Login page.
2. Enter the registered email address.
3. Enter a seven-character password.
4. Click Login.
5. Observe the system response.

Expected Result:
The system should reject the password because it contains fewer than eight characters. It should display a validation message indicating that the password must contain at least eight characters, and the user should remain on the Login page without being authenticated.

Actual Result:
The user is successfully logged in and redirected to the dashboard.

Impact:
The application appears to permit authentication with a password that violates the specified minimum-length requirement. This indicates that the login validation may not be enforcing the documented password policy.

Evidence:
- Screenshot showing successful redirection to the dashboard.
- Test execution record for TC_LOGIN_008.
- Recorded test data confirming that the password contains seven characters.

Notes:
Repeat the test to confirm the behavior and verify the exact account and password used. If the behavior is reproducible, investigate whether the minimum-length rule is missing from login validation or whether the test account and credentials are configured unexpectedly.
```