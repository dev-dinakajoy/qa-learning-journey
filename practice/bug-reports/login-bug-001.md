# BUG-001 — Login fails with valid credentials

## Title

Login displays an invalid password error when valid credentials are provided.

## Environment

* Browser: Chrome
* Environment: QA
* Device: Desktop

## Preconditions

A registered user account exists.

## Steps to Reproduce

1. Open the login page.
2. Enter a valid email address.
3. Enter the correct password.
4. Click **Login**.

## Expected Result

The user should be successfully logged in and redirected to the dashboard.

## Actual Result

The application displays:

> Invalid password

and the user remains on the login page.

## Severity

High

## Priority

High

## Status

New

## Notes

This bug prevents registered users from accessing their accounts.
