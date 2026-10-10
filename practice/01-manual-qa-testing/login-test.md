# Login Testing

## 1. Feature

**User Login**

A registered user should be able to log in using their email and password.

### Requirements

1. Registered users can log in with valid credentials.
2. Invalid credentials should not allow login.
3. Email and password are required.
4. Email must have a valid format.
5. Password must contain at least 8 characters.
6. Successful login redirects the user to the Dashboard.
7. Users can log out successfully.
8. After logout, the Dashboard should not be accessible.

## 2. Requirements Analysis

I identified the following areas to test:

* Valid login
* Invalid login
* Empty fields
* Invalid email format
* Password length
* Successful navigation to Dashboard
* Logout
* Access to Dashboard after logout

### Testing Types Identified

**Functional:**

* Login
* Validation
* Logout
* Navigation

**Non-functional:**

* Basic security
* Usability
* Browser compatibility

## 3. Test Plan

### Scope

Test the Login and Logout functionality.

### Test Types

* Functional
* Non-functional
* Positive
* Negative
* Smoke
* Sanity
* Regression
* Exploratory

### Environment

* Web application
* Chrome
* Test account

## 4. Test Scenarios

| ID           | Scenario                                         |
| ------------ | ------------------------------------------------ |
| TS_LOGIN_001 | Verify login with valid credentials              |
| TS_LOGIN_002 | Verify login with invalid credentials            |
| TS_LOGIN_003 | Verify login with empty email                    |
| TS_LOGIN_004 | Verify login with empty password                 |
| TS_LOGIN_005 | Verify invalid email format                      |
| TS_LOGIN_006 | Verify password minimum length                   |
| TS_LOGIN_007 | Verify successful login redirects to Dashboard   |
| TS_LOGIN_008 | Verify user can logout                           |
| TS_LOGIN_009 | Verify Dashboard cannot be accessed after logout |

## 5. Test Cases

| ID           | Test Case                       | Test Data                                               | Expected Result                              |
| ------------ | ------------------------------- | ------------------------------------------------------- | -------------------------------------------- |
| TC_LOGIN_001 | Login with valid credentials    | [valid@email.com](mailto:valid@email.com) / Password123 | User is logged in and Dashboard is displayed |
| TC_LOGIN_002 | Login with incorrect password   | [valid@email.com](mailto:valid@email.com) / Wrong123    | Login fails and error message is displayed   |
| TC_LOGIN_003 | Login with empty email          | Empty / Password123                                     | Email validation message is displayed        |
| TC_LOGIN_004 | Login with empty password       | [valid@email.com](mailto:valid@email.com) / Empty       | Password validation message is displayed     |
| TC_LOGIN_005 | Login with invalid email format | valid-email / Password123                               | Email format validation is displayed         |
| TC_LOGIN_006 | Password below minimum length   | [valid@email.com](mailto:valid@email.com) / Pass123     | Password is rejected                         |
| TC_LOGIN_007 | Logout after successful login   | Valid login                                             | User is logged out                           |
| TC_LOGIN_008 | Access Dashboard after logout   | Logged-out user                                         | Dashboard should not be accessible           |

## 6. Test Execution

| Test Case    | Expected Result        | Actual Result       | Status   |
| ------------ | ---------------------- | ------------------- | -------- |
| TC_LOGIN_001 | Dashboard displayed    | Dashboard displayed | Pass     |
| TC_LOGIN_002 | Error displayed        | Error displayed     | Pass     |
| TC_LOGIN_003 | Email validation       | Email validation    | Pass     |
| TC_LOGIN_004 | Password validation    | Password validation | Pass     |
| TC_LOGIN_005 | Email validation       | Email validation    | Pass     |
| TC_LOGIN_006 | Password rejected      | Password accepted   | **Fail** |
| TC_LOGIN_007 | User logged out        | User logged out     | Pass     |
| TC_LOGIN_008 | Dashboard inaccessible | Dashboard displayed | **Fail** |

## 7. Bug Reports

### BUG_LOGIN_001

**Title:** Password shorter than 8 characters is accepted.

**Related Test Case:** TC_LOGIN_006

**Expected:** Passwords shorter than 8 characters should be rejected.

**Actual:** A 7-character password is accepted.

**Severity:** High

**Priority:** High

### BUG_LOGIN_002

**Title:** Dashboard remains accessible after logout.

**Related Test Case:** TC_LOGIN_008

**Expected:** Logged-out users should not be able to access the Dashboard.

**Actual:** Dashboard is displayed after using the browser Back button.

**Severity:** High

**Priority:** High

## 8. Bug Lifecycle

`BUG_LOGIN_001`

```text
New
 ↓
Assigned
 ↓
In Progress
 ↓
Fixed
 ↓
Retest
 ↓
Verified
 ↓
Closed
```

`BUG_LOGIN_002` fix failed during retesting, and the bug was reopened.

## 9. Retesting and Regression

After the developer fixed `BUG_LOGIN_001`:

### Retesting

I ran `TC_LOGIN_006` again.

**Expected:** A password with fewer than 8 characters is rejected.

**Actual:** The system rejected password with fewer than 8 characters.

**Result:** Pass.

This confirms that the specific defect was fixed.

### Regression

I tested related Login functionality:

* Valid login
* Invalid password
* Empty password
* Password with exactly 8 characters
* Logout

This checks that the fix did not break existing functionality.

## 10. Smoke, Sanity and Exploratory Testing

### Smoke Testing

After receiving a new build, I quickly verified:

* Login page opens.
* Valid login works.
* Dashboard opens.

If these basic functions failed, detailed testing will be blocked.

### Sanity Testing

After the password validation fix, I focused on:

* Password below 8 characters
* Password exactly 8 characters
* Valid login

### Exploratory Testing

I also tried:

* Pressing Enter instead of clicking Login.
* Using spaces around the email.
* Refreshing the page after login.
* Logging out and pressing Back.
* Trying very long input values.

## 11. Test Summary

| Metric     | Result |
| ---------- | -----: |
| Test Cases |      8 |
| Executed   |      8 |
| Passed     |      6 |
| Failed     |      2 |
| Bugs Found |      2 |

### Summary

The Login feature was tested using positive, negative, functional, smoke, sanity, regression, and exploratory testing approaches.

Two defects were identified:

1. Passwords shorter than 8 characters are accepted.
2. Dashboard remains accessible after logout.

The password validation defect was fixed and successfully retested.

The remaining logout/session issue should be fixed before the feature is considered ready.

## 12. Agile/Scrum

If this Login feature is being developed during a Sprint, I will participate throughout the Sprint.

### Sprint Planning

I will review the Login requirement and identifies what needs to be tested.

### During the Sprint

I will prepare test cases while development is in progress and executes them when the build is available.

### Daily Scrum

Example update:

> Yesterday, I prepared Login test cases. Today, I will execute them. I currently have no blockers.

### Sprint Review

I will share the testing status and any remaining defects or risks.

### Sprint Retrospective

Example:

> Testing went well, but we should clarify session/logout requirements earlier in the next Sprint.

## 13. What I Practiced
* Analyzing requirements
* Creating a simple test plan
* Writing test scenarios
* Writing test cases
* Executing tests
* Recording Pass/Fail results
* Reporting bugs
* Understanding Severity vs Priority
* Following the Bug Lifecycle
* Retesting fixes
* Performing regression testing
* Applying smoke testing
* Applying sanity testing
* Performing exploratory testing
* Understanding functional vs non-functional testing
* Applying QA activities within Scrum
