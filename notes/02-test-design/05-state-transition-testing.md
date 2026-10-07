# State Transition Testing

## What Is State Transition Testing?

**State Transition Testing** is a black-box test design technique used to test how a system behaves when it moves from one **state** to another as a result of an **event or action**.

The basic idea is: **The system's behavior can depend on its current state.**

A system may behave differently when the same action is performed in different states.

## What Is a State?

A **state** represents the current condition or status of a system or object.

Examples:

```text
Account:
Active
Locked
Suspended

Payment:
Pending
Successful
Failed

Order:
Placed
Confirmed
Shipped
Delivered
Cancelled
```

The system can move from one state to another when something happens.

## What Is a Transition?

A **transition** is the movement from one state to another after an event or action occurs.

For example:

```text
Pending
   ↓
Payment successful
   ↓
Successful
```

Here:

* **Current state:** Pending
* **Event:** Payment successful
* **New state:** Successful

## What Is an Event or Action?

An **event** is something that causes the system to change state.

Examples:

* User enters the correct password
* User enters the wrong password
* Payment succeeds
* Payment fails
* Customer cancels an order
* Order is shipped
* User verifies their email

Example:

```text
Current state: Active
Event: 3rd incorrect password
New state: Locked
```

## Basic State Transition Model

A simple state transition can be represented as:

```text
Current State
      ↓
     Event
      ↓
   New State
```

For example:

```text
Active
  ↓
3 failed login attempts
  ↓
Locked
```

## Example 1 — Login Account Lockout

Suppose the requirement says: An account is locked after **3 consecutive failed login attempts**.

Possible states:

```text
Active
Locked
```

We can also track the number of failed attempts:

```text
0 failed attempts
1 failed attempt
2 failed attempts
3 failed attempts → Locked
```

### State transitions

```text
Active
  │
  ├── Wrong password → Active (1 failed attempt)
  │
  ├── Wrong password → Active (2 failed attempts)
  │
  └── Wrong password → Locked (3 failed attempts)
```

A correct password might reset the failed-attempt counter:

```text
2 failed attempts
      ↓
Correct password
      ↓
Active / 0 failed attempts
```

### State Transition Table

Instead of drawing a diagram, we can use a table.

| Current State       | Event            | Expected New State  |
| ------------------- | ---------------- | ------------------- |
| Active / 0 attempts | Wrong password   | Active / 1 attempt  |
| Active / 1 attempt  | Wrong password   | Active / 2 attempts |
| Active / 2 attempts | Wrong password   | Locked              |
| Active / 1 attempt  | Correct password | Active / 0 attempts |
| Active / 2 attempts | Correct password | Active / 0 attempts |
| Locked              | Correct password | Locked              |
| Locked              | Wrong password   | Locked              |

This makes it easier to identify what should happen after each event.

### Valid Transitions

A **valid transition** is a state change that the requirements allow.

Example:

```text
Pending
   ↓
Payment successful
   ↓
Successful
```

If the requirement allows this transition, it should work.

Another:

```text
Order Confirmed
   ↓
Order Shipped
```

If shipping is allowed from the Confirmed state, this is a valid transition.

### Invalid Transitions

An **invalid transition** is an action that should **not** cause an unauthorized or impossible state change.

For example:

```text
Successful Payment
       ↓
Payment Pending
```

If a successful payment cannot return to Pending, this is an invalid transition.

Similarly:

```text
Delivered
   ↓
Shipped
```

would normally be invalid if the system only allows the order to move forward.

Testing invalid transitions is important because applications must not only handle valid workflows—they must also prevent invalid state changes.

## Example 2 — Payment

Suppose a payment system has these states:

```text
Pending
Successful
Failed
```

Possible transitions:

```text
Pending
 ├── Payment succeeds → Successful
 └── Payment fails → Failed
```

### Valid transitions

```text
Pending → Successful ✅
Pending → Failed    ✅
```

### Potentially invalid transitions

```text
Successful → Pending ❌
Successful → Failed  ❌
Failed → Successful  ❌
```

Whether these are invalid depends on the actual system requirements.

This is important:

> **Don't assume a transition is invalid just because it seems unusual. Verify the expected behavior from the requirements.**

## Example 3 — Order Lifecycle

An e-commerce order might have:

```text
Placed
  ↓
Confirmed
  ↓
Processing
  ↓
Shipped
  ↓
Out for Delivery
  ↓
Delivered
```

There might also be:

```text
Placed → Cancelled
Confirmed → Cancelled
```

But:

```text
Out for Delivery → Cancelled
Delivered → Cancelled
```

may be prohibited.

### Example tests

| Current State    | Action        | Expected State | Result |
| ---------------- | ------------- | -------------- | ------ |
| Placed           | Confirm order | Confirmed      | ✅      |
| Confirmed        | Ship order    | Shipped        | ✅      |
| Shipped          | Deliver order | Delivered      | ✅      |
| Placed           | Cancel order  | Cancelled      | ✅      |
| Out for Delivery | Cancel order  | Cancelled      | ❌      |
| Delivered        | Cancel order  | Cancelled      | ❌      |

The last two tests verify that the system prevents invalid transitions.

---

# State Transition Testing and Requirements

State Transition Testing is especially useful when requirements contain words such as:

* Status
* State
* Before
* After
* Once
* Until
* Cannot
* Can only
* After X attempts
* When X happens
* If X happens
* Moves to
* Changes to
* Locked
* Activated
* Deactivated
* Cancelled
* Completed

For example: "A user is locked after three failed login attempts."

Think: **State Transition Testing.**

## State Transition Testing vs Decision Table Testing

These techniques can sometimes look similar, but they focus on different things.

### Decision Table Testing

Focuses on:**Combinations of conditions and the resulting action.**

Example:

```text
Logged in?
Balance sufficient?

→ Transfer allowed?
```

### State Transition Testing

Focuses on: **How the system moves from one state to another.**

Example:

```text
Pending
   ↓
Payment succeeds
   ↓
Successful
```

A requirement can sometimes benefit from **both** techniques.

## State Transition Testing and Test Data

Some state transitions require us to prepare the system in a particular state before testing.

For example: Test that an account becomes locked after three failed attempts.

We need:

### Preconditions

```text
Account exists
Account is active
Failed attempts = 0
```

Then:

```text
Wrong password
→ 1 failed attempt

Wrong password
→ 2 failed attempts

Wrong password
→ Account locked
```

The sequence matters.

You cannot properly test the third transition without first getting the account into the appropriate state.

## State Transition Testing and Sequences

Some systems require multiple actions to reach a particular state.

For example:

```text
Order Placed
     ↓
Payment Successful
     ↓
Order Confirmed
     ↓
Order Shipped
     ↓
Out for Delivery
     ↓
Delivered
```

To test:

> "A delivered order cannot be cancelled."

you first need an order in the **Delivered** state.

The test may therefore involve:

```text
Place order
→ Make payment
→ Confirm order
→ Ship order
→ Deliver order
→ Attempt cancellation
```

This is why state transition testing often involves **sequences of actions**, not just isolated inputs.

## State Transition Coverage

When designing state transition tests, we want to consider more than just the final result.

Important areas include:

### 1. State coverage

Have we visited each important state?

```text
Pending
Successful
Failed
```

### 2. Transition coverage

Have we tested each important transition?

```text
Pending → Successful
Pending → Failed
```

### 3. Invalid transition coverage

Have we tested actions that should **not** cause certain transitions?

```text
Successful → Pending ❌
```

### 4. Sequence coverage

Have we tested important sequences of events?

For example:

```text
Wrong password
→ Wrong password
→ Correct password
```

versus:

```text
Wrong password
→ Wrong password
→ Wrong password
```

These sequences may produce different states.

## Common Mistakes

### 1. Testing only valid transitions

A tester might test:

```text
Pending → Successful
Pending → Failed
```

and stop there.

But we should also consider transitions that should be blocked.

### 2. Ignoring the current state

The same action can have different results depending on the current state.

For example:

```text
Cancel order while Placed
→ Allowed

Cancel order while Delivered
→ Not allowed
```

The action is the same:

> Cancel order

But the current state changes the expected behavior.

### 3. Forgetting state-reset behavior

Suppose an account has two failed attempts and then the user enters the correct password.

Does the failed-attempt counter:

```text
Stay at 2?
```

or:

```text
Reset to 0?
```

The requirement should tell us.

This is an important transition to test.

### 4. Assuming states without checking requirements

Don't assume that:

```text
Failed → Pending
```

is valid or invalid without understanding the system.

Requirements determine the allowed transitions.

## State Transition Testing in Real QA Work

When you receive a requirement involving a lifecycle, first identify:

### 1. States

What statuses can the system be in?

### 2. Events

What actions/events cause changes?

### 3. Transitions

Which state does each event move the system into?

### 4. Invalid transitions

Which actions should be prevented?

### 5. Sequences

Are multiple actions required to reach a state?

## A Simple Process

Use this process when designing state transition tests:

```text
1. Read the requirement
        ↓
2. Identify the states
        ↓
3. Identify the events/actions
        ↓
4. Map valid transitions
        ↓
5. Identify invalid transitions
        ↓
6. Create test scenarios
        ↓
7. Execute the required sequences
        ↓
8. Verify the resulting state
```

## Quick Example

### Requirement

> A payment starts as Pending. If the payment succeeds, it becomes Successful. If the payment fails, it becomes Failed. A Successful payment cannot return to Pending.

### States

```text
Pending
Successful
Failed
```

### Valid transitions

```text
Pending → Successful
Pending → Failed
```

### Invalid transition

```text
Successful → Pending
```

### Test cases

| Current State | Action                          | Expected State     |
| ------------- | ------------------------------- | ------------------ |
| Pending       | Payment succeeds                | Successful         |
| Pending       | Payment fails                   | Failed             |
| Successful    | Attempt to make payment pending | Remains Successful |

## Key Takeaways

* **State Transition Testing** verifies how a system moves between states.
* A **state** represents the current condition of the system.
* An **event/action** causes a state change.
* A **transition** is the movement from one state to another.
* Test both **valid and invalid transitions**.
* The same action can produce different results depending on the current state.
* State transition tests often require a **sequence of actions**.
* Consider **state coverage, transition coverage, invalid transitions, and important sequences**.
* Always base expected transitions on the **requirements**, not assumptions.
* State Transition Testing is especially useful for:

  * Payments
  * Orders
  * Account status
  * Login lockouts
  * Workflows
  * Approval processes
  * Booking systems
  * Subscription lifecycles

**Don't just test what the system does—test how it moves from one state to another.**

## Related

* [Decision Table Testing](04-decision-table-testing.md)
* [Error Guessing](06-error-guessing.md)