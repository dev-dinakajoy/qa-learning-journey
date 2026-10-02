# Requirements Traceability Matrix (RTM)

A **Requirements Traceability Matrix (RTM)** is a document that connects software requirements to the test cases created to verify those requirements.

It helps QA teams answer:

> **Have all requirements been tested?**

It can also help answer:

> **Which test cases verify this requirement?**

> **Did those tests pass or fail?**

> **Is a requirement associated with a defect?**

The RTM provides **traceability** between what the software is supposed to do and what QA actually tested.

---

# 1. What Is Traceability?

**Traceability** means being able to follow a requirement through the testing process.

A simple flow is:

```text
Requirement
     ↓
Test Scenario
     ↓
Test Case
     ↓
Test Execution
     ↓
Result
     ↓
Defect
```

For example:

```text
R1
 ↓
TS_LOGIN_001
 ↓
TC_LOGIN_001
 ↓
Fail
 ↓
BUG-LOGIN-001
```

This allows the QA team to understand exactly how a requirement was tested and whether an issue was discovered.

---

# 2. What Is an RTM?

An RTM is usually a table that maps requirements to test cases.

A simple RTM might look like:

| Requirement ID | Requirement                                 | Test Case ID | Status | Defect ID     |
| -------------- | ------------------------------------------- | ------------ | ------ | ------------- |
| R1             | User can log in with valid credentials      | TC_LOGIN_001 | Pass   | -             |
| R2             | Invalid email is rejected                   | TC_LOGIN_005 | Pass   | -             |
| R3             | Password must contain at least 8 characters | TC_LOGIN_008 | Fail   | BUG-LOGIN-002 |

This gives us a quick view of requirement coverage and test results.

---

# 3. Why Is an RTM Important?

An RTM helps QA teams:

* Confirm that requirements have corresponding tests.
* Identify requirements that have not been tested.
* Track test execution results.
* Connect defects to requirements.
* Identify gaps in test coverage.
* Provide traceability throughout the testing process.
* Support test reporting.
* Make regression testing easier.

Without traceability, it can become difficult to determine whether all required functionality has actually been tested.

---

# 4. Requirement Coverage

One important purpose of the RTM is identifying whether requirements have test coverage.

Suppose we have:

```text
R1 → TC_LOGIN_001
R2 → TC_LOGIN_005
R3 → -
R4 → TC_LOGIN_002
```

We can immediately see that:

```text
R1 → Covered
R2 → Covered
R3 → Not Covered
R4 → Covered
```

Requirement R3 does not currently have a mapped test case.

That represents a **test coverage gap**.

---

# 5. One Requirement Can Have Multiple Test Cases

A requirement does not necessarily need only one test case.

For example:

### Requirement

> Password must contain at least 8 characters.

Using **Boundary Value Analysis**, we might create:

```text
TC_LOGIN_008 → 7 characters
TC_LOGIN_009 → 8 characters
TC_LOGIN_010 → 9 characters
```

All three test cases can map to the same requirement:

```text
R3
 ├── TC_LOGIN_008
 ├── TC_LOGIN_009
 └── TC_LOGIN_010
```

This is one reason the RTM is useful.

It shows the relationship between a requirement and all the tests used to verify it.

---

# 6. One Test Case Can Sometimes Cover Multiple Requirements

A test case may also verify more than one requirement when the requirements are closely related.

For example, suppose a login test verifies:

* Email is valid.
* Password is valid.
* User is authenticated.

One test might therefore be associated with multiple requirements.

However, avoid forcing unrelated requirements into one test case simply to increase traceability.

The mapping should reflect the actual purpose of the test.

---

# 7. RTM and Test Scenarios

Our QA workflow is:

```text
Requirement
     ↓
Test Scenario
     ↓
Test Case
```

The RTM can therefore be extended to include scenarios.

Example:

| Requirement | Scenario                   | Test Case    | Status |
| ----------- | -------------------------- | ------------ | ------ |
| R1          | Valid user login           | TC_LOGIN_001 | Pass   |
| R2          | Email validation           | TC_LOGIN_005 | Pass   |
| R3          | Password length validation | TC_LOGIN_008 | Fail   |

This gives more visibility into the testing structure.

Not every organization includes the Scenario column in the RTM.

---

# 8. RTM and Defects

An RTM can also connect failed test cases to defects.

Example:

| Requirement | Test Case     | Status | Defect         |
| ----------- | ------------- | ------ | -------------- |
| R1          | TC_LOGIN_001  | Fail   | BUG-LOGIN-001  |
| R2          | TC_LOGIN_005  | Pass   | -              |
| R5          | TC_SEARCH_001 | Fail   | BUG-SEARCH-001 |

Now we can see:

```text
R1
 ↓
TC_LOGIN_001
 ↓
Fail
 ↓
BUG-LOGIN-001
```

and:

```text
R5
 ↓
TC_SEARCH_001
 ↓
Fail
 ↓
BUG-SEARCH-001
```

This provides useful defect traceability.

---

# 9. A Basic RTM Structure

A simple RTM can contain:

1. Requirement ID
2. Requirement description
3. Test Scenario ID
4. Test Case ID
5. Execution Status
6. Defect ID
7. Comments

Example:

| Requirement ID | Requirement           | Scenario ID   | Test Case ID  | Status | Defect ID     | Comments              |
| -------------- | --------------------- | ------------- | ------------- | ------ | ------------- | --------------------- |
| R1             | Valid login           | TS_LOGIN_001  | TC_LOGIN_001  | Pass   | -             | -                     |
| R2             | Email validation      | TS_LOGIN_002  | TC_LOGIN_005  | Pass   | -             | -                     |
| R3             | Password min. 8 chars | TS_LOGIN_003  | TC_LOGIN_008  | Fail   | BUG-LOGIN-002 | 7-char input accepted |
| R5             | Valid product search  | TS_SEARCH_001 | TC_SEARCH_001 | Pass   | -             | -                     |

The exact columns depend on the team's needs.

---

# 10. Forward Traceability

**Forward traceability** means following a requirement forward to the tests that verify it.

Example:

```text
Requirement
    ↓
Scenario
    ↓
Test Case
```

Question answered:

> **How are we testing this requirement?**

Example:

```text
R3
 ↓
TS_LOGIN_003
 ↓
TC_LOGIN_008
TC_LOGIN_009
TC_LOGIN_010
```

This shows that the password-length requirement has multiple test cases.

---

# 11. Backward Traceability

**Backward traceability** means following a test case back to the requirement it verifies.

Example:

```text
Test Case
    ↓
Requirement
```

Question answered:

> **Why does this test case exist?**

For example:

```text
TC_LOGIN_009
      ↓
     R3
```

This tells us that the test exists to verify requirement R3.

---

# 12. Bidirectional Traceability

When both directions are possible, we have **bidirectional traceability**.

```text
Requirement
     ↕
Test Case
```

We can go:

```text
Requirement → Test Case
```

and:

```text
Test Case → Requirement
```

This is useful because it helps identify both:

### Missing tests

A requirement has no corresponding test case.

```text
R6 → No Test Case
```

### Unnecessary or orphaned tests

A test case has no clear requirement or testing purpose.

```text
TC_CART_009 → No Requirement
```

An orphaned test may still be useful for exploratory or risk-based testing, but it should have a documented purpose rather than existing without context.

---

# 13. RTM and Test Design Techniques

RTM does not replace test design.

Instead:

```text
Requirement
     ↓
Understand Condition
     ↓
Choose Test Design Technique
     ↓
Create Test Cases
     ↓
Map to Requirement
```

For example:

### Requirement

> Transfer amount must be between ₦5,000 and ₦500,000.

Using Boundary Value Analysis:

```text
₦4,999
₦5,000
₦5,001

₦499,999
₦500,000
₦500,001
```

The resulting test cases can all be mapped to the same requirement.

```text
R_TRANSFER_001
      ↓
TC_TRANSFER_001
TC_TRANSFER_002
TC_TRANSFER_003
TC_TRANSFER_004
TC_TRANSFER_005
TC_TRANSFER_006
```

This demonstrates why a single requirement can have many test cases.

---

# 14. RTM and Test Execution

The RTM becomes more useful after test execution begins.

Before execution:

| Requirement | Test Case    | Status  |
| ----------- | ------------ | ------- |
| R1          | TC_LOGIN_001 | Not Run |
| R2          | TC_LOGIN_005 | Not Run |
| R3          | TC_LOGIN_008 | Not Run |

After execution:

| Requirement | Test Case    | Status |
| ----------- | ------------ | ------ |
| R1          | TC_LOGIN_001 | Pass   |
| R2          | TC_LOGIN_005 | Pass   |
| R3          | TC_LOGIN_008 | Fail   |

The RTM now provides visibility into the current state of requirement testing.

---

# 15. RTM and Defect Tracking

Suppose:

```text
R1 → TC_LOGIN_001 → Fail
```

After investigation, QA confirms a defect:

```text
BUG-LOGIN-001
```

The RTM can become:

| Requirement | Test Case    | Status | Defect        |
| ----------- | ------------ | ------ | ------------- |
| R1          | TC_LOGIN_001 | Fail   | BUG-LOGIN-001 |

Now someone reviewing the RTM can trace the issue back to the original requirement.

---

# 16. Requirement Coverage Percentage

We can calculate basic requirement coverage.

Suppose there are:

```text
Total Requirements = 10
Requirements with at least one test case = 8
```

Then:

```text
Requirement Coverage =
8 / 10 × 100

= 80%
```

So:

> **Requirement coverage = 80%**

This means 80% of the identified requirements have at least one mapped test case.

It does **not** mean 80% of the software has been completely tested.

Coverage metrics should always define exactly what they measure.

---

# 17. Requirement Coverage vs Test Execution Coverage

These are different metrics.

### Requirement Coverage

Measures how many requirements have associated tests.

Example:

```text
8 / 10 requirements mapped to tests = 80%
```

### Test Execution Coverage

Measures how many planned test cases have actually been executed.

Example:

```text
38 / 50 test cases executed = 76%
```

Therefore:

```text
Requirement Coverage ≠ Execution Coverage
```

You could have:

```text
Requirement Coverage: 100%
Execution Coverage: 60%
```

This means all requirements have tests, but many of those tests have not yet been executed.

---

# 18. RTM Example — Easy Buy

Let's use our Easy Buy requirements.

### Requirements

```text
R1 — Registered users can log in with valid credentials.
R2 — Email must be required and use a valid format.
R3 — Password must be required and contain at least 8 characters.
R4 — Invalid credentials should not authenticate the user.
R5 — Valid product searches display matching products.
R6 — Searches with no matching products display an appropriate message.
R7 — Empty search should not cause a system error.
```

A basic RTM could be:

| Requirement | Test Case     | Status | Defect         |
| ----------- | ------------- | ------ | -------------- |
| R1          | TC_LOGIN_001  | Fail   | BUG-LOGIN-001  |
| R2          | TC_LOGIN_005  | Pass   | -              |
| R2          | TC_LOGIN_006  | Pass   | -              |
| R3          | TC_LOGIN_007  | Pass   | -              |
| R3          | TC_LOGIN_008  | Pass   | -              |
| R4          | TC_LOGIN_002  | Pass   | -              |
| R4          | TC_LOGIN_003  | Pass   | -              |
| R4          | TC_LOGIN_004  | Pass   | -              |
| R5          | TC_SEARCH_001 | Fail   | BUG-SEARCH-001 |
| R6          | TC_SEARCH_002 | Pass   | -              |
| R7          | TC_SEARCH_003 | Pass   | -              |

Notice that:

* One requirement can have multiple test cases.
* A failed test can be connected to a defect.
* Multiple test cases can provide coverage for one requirement.

---

# 19. RTM Can Reveal Testing Gaps

Suppose the requirements are:

```text
R1
R2
R3
R4
R5
R6
R7
R8
```

But the RTM only contains:

```text
R1
R2
R3
R4
R5
R6
R7
```

We can immediately see:

```text
R8 → No mapped test case
```

This tells the QA team that R8 needs test coverage.

The RTM therefore helps prevent requirements from being forgotten.

---

# 20. RTM Can Reveal Overlapping or Unnecessary Tests

Suppose we have:

```text
R1 → TC_LOGIN_001
R1 → TC_LOGIN_002
R1 → TC_LOGIN_003
R1 → TC_LOGIN_004
```

This is not automatically a problem.

However, the QA tester should understand why each test exists.

For example:

```text
TC_LOGIN_001 → Valid credentials
TC_LOGIN_002 → Invalid email
TC_LOGIN_003 → Invalid password
TC_LOGIN_004 → Both credentials invalid
```

These test different conditions.

But if we had:

```text
TC_LOGIN_001 → Valid login
TC_LOGIN_002 → Successful login
TC_LOGIN_003 → Login with correct credentials
```

and all three test exactly the same condition, there may be unnecessary duplication.

The RTM can help expose this.

---

# 21. RTM and Regression Testing

RTM can also help identify tests that should be considered for regression after a change.

Suppose a developer changes the login authentication functionality.

The QA team can look at the requirements and associated tests:

```text
R1
 ├── TC_LOGIN_001
 ├── TC_LOGIN_002
 ├── TC_LOGIN_003
 └── TC_LOGIN_004
```

These tests may be candidates for re-execution depending on the change and the team's regression strategy.

RTM therefore helps answer:

> **Which tests are related to this requirement?**

---

# 22. Common RTM Mistakes

## Mistake 1 — Mapping every requirement to exactly one test

A requirement can require multiple test cases.

Don't artificially limit the mapping.

---

## Mistake 2 — Treating coverage as execution

Having a test case mapped to a requirement does not mean the test has been executed.

For example:

```text
R1 → TC_LOGIN_001
Status: Not Run
```

R1 has test coverage, but the test has not yet been executed.

---

## Mistake 3 — Forgetting defects

If a test fails because of a confirmed defect, linking the defect provides useful traceability.

```text
Requirement
    ↓
Test Case
    ↓
Fail
    ↓
Defect
```

---

## Mistake 4 — Including tests with no clear purpose

Every test should have a reason for existing.

Requirement-based tests should normally map to requirements.

Exploratory or error-guessing tests may not map directly to a formal requirement, but their purpose should still be clear.

---

## Mistake 5 — Treating 100% requirement coverage as complete testing

Suppose:

```text
10 requirements
10 requirements have tests
```

Requirement coverage:

> 100%

But:

```text
100 test cases
20 executed
```

Execution coverage:

> 20%

Therefore:

> **100% requirement coverage does not mean testing is complete.**

---

# 23. RTM Checklist

Before considering an RTM complete, check:

### Requirements

* [ ] Are all requirements listed?
* [ ] Does every requirement have an ID?
* [ ] Is each requirement clearly described?

### Test Coverage

* [ ] Does each requirement have appropriate test coverage?
* [ ] Are multiple test cases mapped where necessary?
* [ ] Are test design techniques represented where appropriate?

### Execution

* [ ] Are test statuses updated?
* [ ] Can we identify unexecuted tests?

### Defects

* [ ] Are failed tests linked to confirmed defects?
* [ ] Can defects be traced back to requirements?

### Gaps

* [ ] Are uncovered requirements visible?
* [ ] Are orphaned tests identified?
* [ ] Are unnecessary duplicate tests reviewed?

---

# 24. Complete Traceability Flow

The complete relationship we have learned throughout Level 3 is:

```text
Requirement
     ↓
Test Scenario
     ↓
Test Design Technique
     ↓
Test Case
     ↓
Test Data
     ↓
Precondition
     ↓
Test Steps
     ↓
Expected Result
     ↓
Test Execution
     ↓
Actual Result
     ↓
Status
     ↓
Defect (if confirmed)
     ↓
Retest
     ↓
Regression Testing
```

The RTM provides a way to connect important parts of this flow.

---

# 25. Key Takeaways

Remember the purpose of the RTM:

> **To provide traceability between requirements and testing.**

The basic relationship is:

```text
Requirement
     ↓
Test Case
     ↓
Execution Result
     ↓
Defect
```

An RTM helps us answer:

> **What requirements are we testing?**

> **Which test cases verify them?**

> **Have those tests been executed?**

> **Did they pass or fail?**

> **Are any defects associated with them?**

> **Are there requirements without test coverage?**

Most importantly:

```text
Requirement Coverage
        ≠
Execution Coverage
        ≠
Pass Rate
```

They measure different things and should not be confused.

A well-maintained RTM makes testing more traceable, helps identify coverage gaps, and provides a clear connection between **what the product should do** and **what QA actually tested**.
