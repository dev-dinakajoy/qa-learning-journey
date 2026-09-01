# Severity vs Priority

## What I learned

Today I learned the difference between **severity** and **priority** when reporting bugs.

At first, they sounded like the same thing.

But they answer two different questions:

> **Severity = How badly does the bug affect the system?**

> **Priority = How urgently should the bug be fixed?**

Understanding this difference is important because not every serious bug is the most urgent bug, and not every urgent bug is technically severe.

---

# Severity

**Severity** describes the **impact of a defect on the software**.

In other words:

> How badly does this bug affect the application or the user?

A bug that prevents users from completing a critical function usually has high severity.

---

## Common Severity Levels

Different companies may use different names, but a simple classification is:

### Critical

The application or a critical feature is completely unusable.

Example:

> The payment system crashes every time a customer tries to pay.

```text
Severity: Critical
```

### High

A major feature is broken, but the entire application isn't necessarily unusable.

Example:

> Users cannot log into their accounts.

```text
Severity: High
```

### Medium

The bug affects functionality but there is a workaround or the impact is limited.

Example:

> Users cannot update their profile picture, but they can update all other profile information.

```text
Severity: Medium
```

### Low

The bug has little functional impact.

Example:

> A button is slightly misaligned.

```text
Severity: Low
```

---

# Priority

**Priority** describes how urgently the team should fix the bug.

It answers:

> "How soon should we address this?"

A common classification is:

* High
* Medium
* Low

For example:

```text
Priority: High
```

means the team should address the bug quickly.

---

# Severity vs Priority

Here's the easiest way I remember it:

|                       | Severity                  | Priority                   |
| --------------------- | ------------------------- | -------------------------- |
| Question              | How bad is it?            | How soon should we fix it? |
| Focus                 | Impact                    | Urgency                    |
| Usually determined by | Technical/business impact | Product/business needs     |
| Example               | Payment completely fails  | Fix before today's release |

---

# Example 1: High Severity + High Priority

Imagine an e-commerce application.

Users cannot complete payments.

```text
Severity: Critical
Priority: High
```

Why?

The defect prevents users from completing purchases and directly affects the core business.

---

# Example 2: Low Severity + Low Priority

The company's footer contains a small spacing issue.

```text
Severity: Low
Priority: Low
```

The application still works normally.

It can probably wait until a future release.

---

# Example 3: Low Severity + High Priority

This is where things get interesting.

Imagine a company's homepage contains a typo:

> "Welcom to our website"

Technically, the application still works.

So:

```text
Severity: Low
```

But suppose the company is launching a major marketing campaign tomorrow.

The business may want the typo fixed immediately.

So:

```text
Priority: High
```

Therefore:

> **Low Severity + High Priority**

This example helped me understand that severity and priority don't have to be the same.

---

# Example 4: High Severity + Low Priority

Imagine an old admin feature that crashes when a very specific, rarely used input is entered.

The impact could technically be serious:

```text
Severity: High
```

But if:

* Very few users use the feature
* There is a workaround
* The feature isn't currently important
* The release deadline is focused on another area

The team might decide:

```text
Priority: Low
```

The exact decision depends on the project's context.

---

# A Simple Matrix

I can think about bugs using this matrix:

|                   | Low Priority           | High Priority   |
| ----------------- | ---------------------- | --------------- |
| **Low Severity**  | Fix later              | Fix soon        |
| **High Severity** | Important but may wait | Fix immediately |

This isn't a strict rule.

The product team ultimately decides what gets prioritized based on factors such as:

* Business impact
* Number of affected users
* Release deadlines
* Security risks
* Customer impact
* Available workarounds

---

# Who Decides Severity and Priority?

This can vary between organizations.

A QA tester often provides an initial assessment based on the impact they've observed.

For example:

```text
Severity: High
Priority: High
```

The team may then review and adjust it.

The important thing is that I should be able to **explain why I chose the values**.

I shouldn't simply label everything:

> High Severity + High Priority

Just because I want the developer to fix it quickly.

---

# Example Bug Report

Suppose I'm testing a banking application.

I discover:

> Users can transfer money without entering a recipient account number.

My bug report might contain:

```text
Title:
User can initiate a transfer without entering a recipient account number

Expected Result:
The application should require a valid recipient account
number before allowing the transfer.

Actual Result:
The transfer process continues without a recipient account number.

Severity:
High

Priority:
High
```

The important part is not just the labels.

I need to understand **why** the defect has that severity and priority.

---

# Common Mistake

One mistake I want to avoid is thinking:

> "Severity and priority are always the same."

They're not.

For example:

```text
Typo on homepage
↓
Low Severity
↓
But important marketing launch
↓
High Priority
```

Another mistake is:

> "QA always decides priority."

Not necessarily.

Depending on the organization, the Product Owner, Project Manager, QA Lead, or team may determine or adjust priority.

---

# What clicked for me

Before learning this, I thought:

> **Severity = Priority**

Now I understand that they describe different things.

A bug can be:

* High severity + high priority
* High severity + low priority
* Low severity + high priority
* Low severity + low priority

The context of the product and business matters.

---

# Key Takeaway

The easiest way for me to remember the difference is:

> 🔴 **Severity:** How badly does the bug affect the system?

> 🟡 **Priority:** How urgently should the team fix it?

When reporting a bug, I should be able to explain both the **impact** and the **urgency** rather than assigning labels randomly.

---

## Related

* [QA and Software Testing](01-qa-and-software-testing.md)
* [SDLC and STLC](02-sdlc-and-stlc.md)
* [Test Scenarios and Test Cases](03-test-scenarios-and-test-cases.md)
* [Bug/Defect Lifecycle](04-bug-defect-lifecycle.md)
* [Functional vs Non-functional Testing](06-functional-vs-non-functional-testing.md)
