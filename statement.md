# Problem Statement

## Title
Password Strength Checker

## Problem

Weak passwords are one of the most common causes of account compromise. Many users
choose passwords that are too short, predictable, or missing character variety
(uppercase letters, numbers, symbols), which makes them easy to guess or crack.
Most people have no simple way to check, before using a password, whether it is
actually strong enough.

## Objective

To build a command-line Python application that:

1. Lets a user set a password and validates it against a set of basic security rules.
2. Rejects passwords that do not meet minimum requirements, with a clear error message.
3. Rates the strength of an accepted password on a scale of 0 to 10.
4. Gives the user specific, actionable feedback on how to improve a weak password.

## Scope

- The tool runs locally in the terminal; it does not store or transmit passwords anywhere.
- It checks structural properties of a password (length, character types, starting
  character, common weak patterns, and repeated characters) rather than checking it
  against real-world breach databases.
- It is intended as a learning project to demonstrate string validation, scoring
  logic, and a simple menu-driven program flow in Python.

## Validation Rules

A password must:
- Be at least 10 characters long.
- Not start with a number.
- Not contain the restricted symbols `^ * ( ) %`.

## Scoring Criteria

Points are awarded for password length, and for including lowercase letters,
uppercase letters, numbers, and special characters. Points are deducted for
common weak patterns (e.g. "password", "123", "qwerty") and for repeating the
same character four or more times in a row. The final score (0–10) maps to a
strength label from "Very Weak" to "Very Strong".

## Expected Outcome

A working Python script (`password_checker.py`) that a user can run from the
command line to set a password and immediately see how strong it is, along
with concrete suggestions for improving it.

## Author

Piyush Jha
