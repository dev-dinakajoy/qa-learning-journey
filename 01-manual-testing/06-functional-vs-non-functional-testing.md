# Functional vs Non-functional Testing

## What I learned

Today I learned about **functional** and **non-functional testing**.

The easiest way I understand the difference is:

> **Functional testing = Does the software do what it is supposed to do?**

> **Non-functional testing = How well does the software do it?**

Both are important because an application can have all the right features and still provide a poor experience.

---

# Functional Testing

Functional testing checks whether the software's **features and functions work according to the requirements**.

It focuses on **what the system does**.

For example, in an e-commerce application, I might test:

* User registration
* Login
* Product search
* Add to cart
* Remove from cart
* Checkout
* Payment
* Order confirmation
* Logout

If the requirement says:

> Users should be able to add products to their cart.

I should verify that the feature actually works.

---

## Example: Login

Suppose the requirement is:

> A registered user should be able to log in using a valid email and password.

I can test:

```text id="2vuw0m"
Valid email + valid password
        ↓
Login successful ✅
```

I can also test:

```text id="gk0a3n"
Valid email + wrong password
        ↓
Login rejected ✅
```

```text id="8s9s8h"
Empty email + valid password
        ↓
Validation message ✅
```

These are functional tests because I'm checking whether the login functionality behaves as required.

---

# Types of Functional Testing

There are different approaches to functional testing.

Some of the important ones I'll encounter include:

### Unit Testing

Testing individual pieces of code, usually done by developers.

Example:

> Testing a function that calculates the total price.

### Integration Testing

Testing whether different components work correctly together.

Example:

> Checking that the checkout system correctly communicates with the payment service.

### System Testing

Testing the complete application as a whole.

Example:

> Testing the complete flow from login → product selection → checkout → payment.

### Acceptance Testing

Checking whether the system meets the business requirements and is acceptable for release.

Example:

> A customer should be able to successfully complete an order from start to finish.

As a manual QA tester, I'll often work heavily with **system and acceptance-level testing**, although the exact responsibilities depend on the team.

---

# Non-functional Testing

Non-functional testing focuses on **how the system performs** rather than simply whether a feature exists.

It answers questions like:

> Is it fast enough?

> Is it secure?

> Is it easy to use?

> Can it handle many users?

> Does it work across different environments?

---

# Example: Performance

Suppose an e-commerce application allows users to search for products.

Functionally:

> The search works. ✅

But imagine every search takes **15 seconds**.

The feature works, but the performance is poor.

So I might test:

* Response time
* Load handling
* Performance under different conditions
* Resource usage

---

# Example: Usability

Suppose the checkout process technically works.

But users can't figure out how to complete payment because the **Pay Now** button is difficult to find.

Functionally:

> Payment works.

From a usability perspective:

> The experience is poor.

That's a non-functional concern.

---

# Example: Compatibility

Suppose an application works perfectly in Chrome.

But on another supported browser, the layout is broken.

I might test:

* Different browsers
* Different operating systems
* Different screen sizes
* Different devices

This is **compatibility testing**.

---

# Example: Security

Suppose a user logs into their account.

I should consider:

> Can this user access another user's account or private information?

Security testing can involve checking things such as:

* Authentication
* Authorization
* Access control
* Session management
* Input validation

Security testing can become a specialized field on its own, but QA testers should understand the basic concepts.

---

# Functional vs Non-functional

Here's the comparison:

| Functional Testing                       | Non-functional Testing                        |
| ---------------------------------------- | --------------------------------------------- |
| Tests what the system does               | Tests how well the system works               |
| Based heavily on functional requirements | Based on quality attributes/constraints       |
| Checks features and behavior             | Checks performance, usability, security, etc. |
| Example: Login works                     | Example: Login responds quickly               |
| Example: Payment succeeds                | Example: Payment remains reliable under load  |

---

# A Simple Example

Imagine I'm testing a food delivery application.

The requirement says:

> Users should be able to place an order.

### Functional testing

I check:

```text id="gqf4ec"
Select restaurant
      ↓
Select food
      ↓
Add to cart
      ↓
Enter address
      ↓
Pay
      ↓
Order confirmed ✅
```

The functionality works.

### Non-functional testing

Now I ask:

> How quickly does the order process?

> What happens when thousands of users place orders at the same time?

> Is the application easy to use?

> Does it work on different devices?

> Is the user's payment information protected?

These are non-functional concerns.

---

# Why Both Matter

Imagine a banking application.

It allows users to transfer money correctly.

That's good functional behavior.

But suppose:

* It takes 30 seconds to load each page.
* It crashes when many users log in.
* The interface is confusing.
* It doesn't work properly on mobile.
* User data isn't adequately protected.

The application may be **functionally correct but still poor quality**.

That's why QA needs to consider both functional and non-functional aspects.

---

# Functional + Non-functional Example

Let's say the requirement is:

> Users should be able to upload a profile picture.

### Functional tests

* Upload a valid image
* Upload an unsupported file type
* Upload an empty file
* Upload a file larger than the allowed size
* Cancel an upload
* Replace an existing image

### Non-functional tests

**Performance:**

> How long does the upload take?

**Usability:**

> Is it obvious how to upload the image?

**Compatibility:**

> Does the upload work across supported browsers?

**Security:**

> Can a malicious file be uploaded?

This shows how the same feature can have **both functional and non-functional tests**.

---

# A Useful Mental Model

When I see a feature, I can ask two questions:

### Question 1

> **Does it work?**

That's primarily functional testing.

### Question 2

> **How well does it work?**

That's primarily non-functional testing.

```text id="t2q9zi"
                  FEATURE
                     │
          ┌──────────┴──────────┐
          ↓                     ↓
   Does it work?          How well does it work?
          ↓                     ↓
     Functional          Non-functional
```

---

# What clicked for me

I initially thought testing was mostly about checking whether features worked.

Now I understand that **software quality goes beyond functionality**.

A feature can work correctly and still be:

* Too slow
* Difficult to use
* Incompatible with supported devices
* Unreliable
* Insecure

So testing should look at both **what the software does** and **the quality of that behavior**.

---

# Key Takeaway

The simplest way I want to remember this is:

> **Functional testing:** Does it do what it should?

> **Non-functional testing:** Does it do it well?

A good QA tester shouldn't stop at:

> "The feature works."

I should also think:

> "Is it fast enough, usable, reliable, secure, and compatible with the environments we support?"

---

## Related

* [QA and Software Testing](01-qa-and-software-testing.md)
* [SDLC and STLC](02-sdlc-and-stlc.md)
* [Test Scenarios and Test Cases](03-test-scenarios-and-test-cases.md)
* [Bug/Defect Lifecycle](04-bug-defect-lifecycle.md)
* [Severity vs Priority](05-severity-vs-priority.md)
* [Smoke, Sanity and Regression Testing](07-smoke-sanity-regression-testing.md)
