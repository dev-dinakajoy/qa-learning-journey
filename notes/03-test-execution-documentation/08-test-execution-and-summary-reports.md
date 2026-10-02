# Test Execution and Summary Reports

During test execution, QA testers record the result of individual test cases.

For example:

```text
TC_LOGIN_001 → Pass
TC_LOGIN_002 → Pass
TC_LOGIN_003 → Fail
TC_SEARCH_001 → Pass
TC_CART_001 → Blocked
```

But a project team usually needs more than individual test results.

They need an overall picture of the testing activity:

* How many tests were planned?
* How many were executed?
* How many passed?
* How many failed?
* How many were blocked?
* How many were not run?
* How many defects were found?
* What risks remain?
* Is more testing needed?

This is where **Test Execution Reports** and **Test Summary Reports** become useful.

---

# 1. What Is a Test Execution Report?

A **Test Execution Report** provides information about the tests that have been executed during a test cycle.

It focuses primarily on:

> **What happened during test execution?**

It can include:

* Test cases executed
* Passes
* Failures
* Blocked tests
* Not-run tests
* Execution progress
* Defects discovered
* Test environment
* Execution dates
* Tester information
* Comments or observations

The exact format depends on the project and organization.

---

# 2. What Is a Test Summary Report?

A **Test Summary Report** provides a higher-level summary of the overall testing activity.

It answers:

> **What is the current testing status, what did we find, and what risks remain?**

A summary report may include:

* Testing scope
* Test environment
* Test execution statistics
* Defect statistics
* Major findings
* Risks
* Test coverage
* Remaining work
* Recommendations for further testing

The summary is generally intended to help stakeholders understand the overall state of testing.

---

# 3. Test Execution Report vs Test Summary Report

The two reports are related, but they have different purposes.

| Test Execution Report            | Test Summary Report                                    |
| -------------------------------- | ------------------------------------------------------ |
| Focuses on test execution        | Focuses on overall testing status                      |
| Contains execution results       | Summarizes results and findings                        |
| More detailed                    | More high-level                                        |
| Tracks Pass/Fail/Blocked/Not Run | Explains what those results mean                       |
| Useful for QA team               | Useful for QA and stakeholders                         |
| Often updated during testing     | Often produced at the end of a test cycle or milestone |

Think of it as:

```text
Test Cases
    ↓
Test Execution
    ↓
Execution Results
    ↓
Test Execution Report
    ↓
Summary
    ↓
Test Summary Report
```

---

# 4. Why Test Reports Matter

Test reports help the team make informed decisions about the current state of testing.

They can show:

* Whether planned testing has been completed
* Which areas have failures
* Which tests remain unexecuted
* Whether blockers are preventing progress
* How many defects were discovered
* Which important areas remain insufficiently tested

A report should not simply contain numbers.

It should provide enough context to understand what those numbers mean.

---

# 5. Basic Test Execution Metrics

Let's use a simple example.

Suppose a project has:

```text
Planned Test Cases: 50

Passed: 32
Failed: 6
Blocked: 4
Not Run: 8
```

First, verify that the numbers account for all planned tests:

```text
32 + 6 + 4 + 8 = 50
```

Good.

---

# 6. Executed Test Cases

A test is considered **executed** when it has actually been run.

For this example:

```text
Passed = 32
Failed = 6
```

Therefore:

```text
Executed = Passed + Failed

Executed = 32 + 6

Executed = 38
```

So:

> **38 of the 50 planned test cases were executed.**

Blocked and Not Run tests are not counted as successfully executed tests.

---

# 7. Execution Coverage

**Execution Coverage** tells us what percentage of the planned test cases have actually been executed.

Formula:

```text
Execution Coverage =
Executed Test Cases
------------------- × 100
Total Planned Tests
```

Using our example:

```text
38
-- × 100 = 76%
50
```

Therefore:

> **Execution Coverage = 76%**

This means 76% of the planned test cases were executed.

It does **not** mean that 76% of the software is defect-free.

---

# 8. Pass Rate

The **Pass Rate** tells us what percentage of executed tests passed.

Formula:

```text
Pass Rate =
Passed Tests
------------ × 100
Executed Tests
```

Using our example:

```text
32
-- × 100 = 84.21%
38
```

Rounded:

> **Pass Rate ≈ 84%**

This means approximately 84% of the tests that were executed passed.

It does not mean that 84% of the entire application is working correctly.

---

# 9. Fail Rate

The **Fail Rate** tells us what percentage of executed tests failed.

Formula:

```text
Fail Rate =
Failed Tests
------------ × 100
Executed Tests
```

Using our example:

```text
6
-- × 100 = 15.79%
38
```

Rounded:

> **Fail Rate ≈ 16%**

Notice:

```text
84% + 16% ≈ 100%
```

Because these rates are calculated from the executed tests.

---

# 10. Blocked Rate

The **Blocked Rate** tells us what percentage of planned tests are currently blocked.

Formula:

```text
Blocked Rate =
Blocked Tests
------------- × 100
Planned Tests
```

Example:

```text
4
-- × 100 = 8%
50
```

Therefore:

> **Blocked Rate = 8%**

This is useful because blocked tests represent testing that could not proceed.

---

# 11. Not Run Rate

The **Not Run Rate** tells us what percentage of planned tests have not yet been executed.

Formula:

```text
Not Run Rate =
Not Run Tests
------------- × 100
Planned Tests
```

Example:

```text
8
-- × 100 = 16%
50
```

Therefore:

> **Not Run Rate = 16%**

---

# 12. Important: Know Which Denominator You Are Using

This is one of the most important things to understand when calculating QA metrics.

For example:

### Execution Coverage

Uses:

```text
Total Planned Tests
```

### Pass Rate

Uses:

```text
Executed Tests
```

### Fail Rate

Uses:

```text
Executed Tests
```

### Blocked Rate

Usually uses:

```text
Total Planned Tests
```

### Not Run Rate

Usually uses:

```text
Total Planned Tests
```

Always make the denominator clear when reporting metrics.

---

# 13. Example Test Execution Summary

For our Easy Buy project:

| Metric             | Value |
| ------------------ | ----: |
| Planned            |    50 |
| Executed           |    38 |
| Passed             |    32 |
| Failed             |     6 |
| Blocked            |     4 |
| Not Run            |     8 |
| Execution Coverage |   76% |
| Pass Rate          |   84% |
| Fail Rate          |   16% |
| Blocked Rate       |    8% |
| Not Run Rate       |   16% |

These numbers provide a quick view of the test cycle.

---

# 14. Defect Summary

Test reports should also summarize discovered defects.

For example:

```text
Total Defects: 6

Critical: 0
High: 2
Medium: 3
Low: 1
```

You may also report their current states:

```text
Open: 3
Fixed: 2
Closed: 1
```

The exact defect categories depend on the project's workflow.

---

# 15. Why Defect Statistics Matter

Suppose:

```text
50 tests planned
48 passed
2 failed
```

At first glance, the results might appear strong.

But suppose both failed tests affect:

> Order placement.

That information changes the interpretation of the testing results.

This is why a good test summary should provide **context**, not just percentages.

---

# 16. Findings

A Test Summary Report should explain important findings.

For example:

```text
Key Findings:

- 50 test cases were planned.
- 38 were executed.
- 32 passed and 6 failed.
- 4 tests were blocked.
- 8 tests remain unexecuted.
- 6 defects were identified.
- 2 defects are classified as High severity.
- Login and checkout contain unresolved issues.
```

This allows stakeholders to understand the testing situation quickly.

---

# 17. Risks

A good report should identify important testing risks.

For example:

```text
Risks:

- Eight planned test cases remain unexecuted.
- Checkout testing is incomplete.
- Some login scenarios remain untested.
- Four test cases are blocked by unavailable dependencies.
- Open defects remain in important application areas.
```

The purpose is not to exaggerate the situation.

The purpose is to make remaining uncertainty visible.

---

# 18. Recommendations

Based on the documented testing results, the report can identify next testing actions.

For example:

```text
Recommended Actions:

1. Resolve blockers affecting checkout testing.
2. Execute the remaining untested cases.
3. Retest confirmed defects after fixes.
4. Run relevant regression tests after major fixes.
5. Review remaining open defects before release decisions.
```

These are testing actions rather than a release decision.

Release decisions may involve QA, Product, Engineering, and other stakeholders according to the team's process.

---

# 19. Test Environment

A report should identify the environment in which testing was performed.

Example:

```text
Environment:
QA

Browser:
Chrome 154

Operating System:
macOS

Device:
Desktop
```

For a project testing multiple environments, you might report results separately.

Example:

| Environment     | Passed | Failed | Blocked |
| --------------- | -----: | -----: | ------: |
| Chrome / macOS  |     25 |      3 |       1 |
| Firefox / macOS |     23 |      4 |       2 |
| Android         |     20 |      5 |       3 |

This helps identify environment-specific problems.

---

# 20. Test Cycle Information

A report should identify the testing cycle.

Example:

```text
Project:
Easy Buy

Test Cycle:
Release 1.0

Testing Phase:
System Testing

Environment:
QA

Execution Period:
September 2026
```

The exact fields depend on the project.

---

# 21. Sample Test Execution Report

```text
TEST EXECUTION REPORT

Project:
Easy Buy

Test Cycle:
Release 1.0

Environment:
QA
Chrome 154
macOS
Desktop

Test Cases:

Planned: 50
Executed: 38
Passed: 32
Failed: 6
Blocked: 4
Not Run: 8

Execution Coverage:
76%

Pass Rate:
84%

Fail Rate:
16%

Key Defects:
6 total
2 High
3 Medium
1 Low

Execution Notes:
38 of 50 planned test cases were executed.
Six executed tests failed and four tests were blocked.
Eight tests remain unexecuted.
```

This report focuses primarily on execution results.

---

# 22. Sample Test Summary Report

A higher-level summary could look like:

```text
TEST SUMMARY REPORT

Project:
Easy Buy

Test Cycle:
Release 1.0

Environment:
QA
Chrome 154
macOS
Desktop

Testing Scope:
Login
Product Search
Cart
Checkout

Test Execution:

Planned: 50
Executed: 38
Passed: 32
Failed: 6
Blocked: 4
Not Run: 8

Execution Coverage:
76%

Pass Rate:
84%

Fail Rate:
16%

Defects:

Total: 6
Critical: 0
High: 2
Medium: 3
Low: 1

Open: 3
Fixed: 2
Closed: 1

Key Findings:

- 38 of 50 planned tests were executed.
- 32 executed tests passed.
- 6 executed tests failed.
- 4 tests were blocked.
- 8 tests remain unexecuted.
- Six defects were identified.
- Two defects are classified as High severity.
- Login and checkout require additional attention.

Risks:

- Checkout testing is incomplete.
- Some login scenarios remain untested.
- Three defects remain open.
- Eight planned test cases have not been executed.

Recommended Testing Actions:

- Resolve blockers.
- Complete remaining test execution.
- Retest fixed defects.
- Execute relevant regression tests.
- Review open defects and remaining coverage.
```

---

# 23. Test Reports Should Be Evidence-Based

A test report should be based on recorded testing information.

For example:

```text
Test Data
   ↓
Test Cases
   ↓
Execution Results
   ↓
Defects
   ↓
Metrics
   ↓
Findings
   ↓
Report
```

Avoid unsupported statements such as:

> The application is completely bug-free.

Testing cannot prove that an application contains no defects.

A better statement is:

> All planned test cases for the current test scope were executed, and the recorded results are summarized below.

Even then, the report should clearly identify what was actually tested.

---

# 24. Don't Misinterpret Pass Rate

Suppose:

```text
100 planned tests

10 executed
10 passed
90 not run
```

The Pass Rate among executed tests is:

```text
10
-- × 100 = 100%
10
```

But only 10% of the planned tests were executed.

Therefore, reporting only:

> **100% pass rate**

would provide incomplete information.

A more useful summary is:

```text
Execution Coverage: 10%
Pass Rate of Executed Tests: 100%
Not Run: 90%
```

This gives the necessary context.

---

# 25. Test Coverage vs Execution Coverage

These terms can mean different things depending on the organization.

**Execution Coverage** answers:

> How many planned test cases have we executed?

Example:

```text
38 executed / 50 planned = 76%
```

**Test Coverage** can refer more broadly to how much of the requirements, features, code, or other test scope has been covered.

For example:

```text
Requirements:
R1 → Tested
R2 → Tested
R3 → Tested
R4 → Not Tested
```

This is why QA reports should clearly define what a reported percentage represents.

Don't simply write:

> Coverage = 76%

without explaining what the 76% measures.

---

# 26. Test Execution and RTM

Test execution results can also be connected to the **Requirements Traceability Matrix (RTM)**.

For example:

```text
Requirement
     ↓
Test Case
     ↓
Execution Result
     ↓
Defect
```

Example:

```text
R1
 ↓
TC_LOGIN_001
 ↓
Fail
 ↓
BUG-LOGIN-001
```

This gives stakeholders visibility into:

* Which requirements were tested
* Which tests passed
* Which requirements have failures
* Which requirements are associated with defects

We will revisit this in the next lesson on the RTM.

---

# 27. Common Reporting Mistakes

## Mistake 1 — Reporting only the pass rate

Example:

> Pass rate: 90%

Without knowing how many tests were executed, this can be misleading.

Always provide the planned and executed counts.

---

## Mistake 2 — Mixing denominators

For example:

> Pass rate = 32 / 50 = 64%

If you are defining Pass Rate as the percentage of **executed** tests that passed, this calculation is incorrect.

The correct calculation would be:

```text
32 / 38 × 100 ≈ 84%
```

---

## Mistake 3 — Treating blocked tests as failures

A blocked test was not successfully executed.

Don't automatically include it as a failed test unless your organization's reporting rules explicitly define it that way.

---

## Mistake 4 — Treating Not Run as Pass

Not Run means:

> No execution result exists yet.

It does not mean the test passed.

---

## Mistake 5 — Reporting numbers without context

Instead of:

> 16% not run.

Say:

> 8 of 50 planned test cases remain unexecuted, representing 16% of the planned test scope.

This is much clearer.

---

## Mistake 6 — Making unsupported conclusions

Avoid:

> The application is ready for release because 84% of tests passed.

The test results alone do not establish that conclusion.

Instead, report the facts:

> 84% of executed tests passed, while 6 tests failed, 4 were blocked, and 8 remain unexecuted.

Stakeholders can then use this information together with other release criteria.

---

# 28. Test Summary Report Checklist

Before finalizing a report, check:

### Project Information

* [ ] Project name
* [ ] Test cycle
* [ ] Environment
* [ ] Testing period

### Execution

* [ ] Planned tests
* [ ] Executed tests
* [ ] Passed tests
* [ ] Failed tests
* [ ] Blocked tests
* [ ] Not Run tests

### Metrics

* [ ] Execution coverage
* [ ] Pass rate
* [ ] Fail rate
* [ ] Other relevant metrics

### Defects

* [ ] Total defects
* [ ] Severity distribution
* [ ] Defect status
* [ ] Important unresolved defects

### Analysis

* [ ] Key findings
* [ ] Remaining risks
* [ ] Uncovered areas
* [ ] Blockers

### Next Actions

* [ ] Remaining tests
* [ ] Retesting
* [ ] Regression testing
* [ ] Other required testing activities

---

# 29. Key Takeaways

The purpose of a test report is not simply to produce numbers.

It is to communicate the **current state of testing using evidence from test execution**.

Remember:

```text
Individual Test Cases
        ↓
Execution Results
        ↓
Pass / Fail / Blocked / Not Run
        ↓
Metrics
        ↓
Defect Summary
        ↓
Findings
        ↓
Risks
        ↓
Test Report
```

The most important metrics we practiced are:

```text
Executed = Passed + Failed

Execution Coverage =
Executed / Planned × 100

Pass Rate =
Passed / Executed × 100

Fail Rate =
Failed / Executed × 100

Blocked Rate =
Blocked / Planned × 100

Not Run Rate =
Not Run / Planned × 100
```

For our Easy Buy example:

```text
Planned: 50
Executed: 38
Passed: 32
Failed: 6
Blocked: 4
Not Run: 8

Execution Coverage: 76%
Pass Rate: ≈84%
Fail Rate: ≈16%
Blocked Rate: 8%
Not Run Rate: 16%
```

Most importantly:

> **Always report the numbers together with enough context to understand what they mean.**

A good test report allows the team to see not only **what happened during testing**, but also **what remains to be tested and where uncertainty or defects remain**.
