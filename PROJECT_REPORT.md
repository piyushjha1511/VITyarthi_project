# Project Report

## Password Strength Checker

**Submitted by:** Piyush Jha
**GitHub Repository:** https://github.com/piyushjha1511/VITyarthi_project

---

## Abstract

Weak passwords remain one of the leading causes of account compromise, as
many users choose passwords that are short, predictable, or lack character
variety. This project presents a Python-based command-line application,
the **Password Strength Checker**, that validates a password against a set
of security rules and, once accepted, scores its strength on a scale of 0
to 10. The tool provides specific, actionable feedback so users can
strengthen weak passwords. The system is built using only Python's
built-in features, with no external dependencies, and demonstrates
practical use of input validation, conditional logic, and scoring
algorithms.

---

## 1. Introduction

Passwords are the most common method of authentication used to protect
personal and organizational data. Despite widespread awareness of
password best practices, many users still choose weak, easily guessable
passwords. This project addresses that gap by giving users an immediate,
easy way to check whether a password they intend to use is strong enough,
along with practical suggestions to improve it before it is used
elsewhere.

### 1.1 Objective

1. Let a user set a password and validate it against basic security rules.
2. Reject passwords that fail minimum requirements, with a clear error message.
3. Rate the strength of an accepted password on a scale of 0 to 10.
4. Give the user specific, actionable feedback to improve a weak password.

### 1.2 Scope

- Runs locally in the terminal; passwords are never stored or transmitted.
- Evaluates the structure of a password (length, character variety, starting
  character, weak patterns, repeated characters) rather than checking real
  breach databases.
- Intended as a learning project demonstrating string validation, scoring
  logic, and a menu-driven program flow in Python.

---

## 2. Tools and Technologies Used

| Item | Details |
|------|---------|
| Language | Python 3.10+ |
| Editor | Visual Studio Code |
| Version Control | Git |
| Hosting | GitHub |
| External Libraries | None (built-in Python only) |

### 2.1 System Requirements

- Python 3.10 or newer (the program uses `match` statements, introduced in
  Python 3.10)
- No internet connection or external packages needed to run

---

## 3. System Design

### 3.1 Project Structure

```
VITyarthi_project/
├── password_checker.py   # Main program
├── README.md              # Setup and usage instructions
├── STATEMENT.md            # Problem statement
└── PROJECT_REPORT.md       # This report
```

### 3.2 Program Flow

The application runs as a loop presenting three menu options: set or
replace a password, check the strength of the current password, or exit.
Internally, it separates the logic into two stages: **validation** and
**scoring**.

```
Start
  │
  ▼
Show Menu (1. Set Password  2. Check Strength  3. Exit)
  │
  ├── Option 1 → Validate input → Accept or show error → Loop until valid
  ├── Option 2 → Score password → Show strength label + recommendations
  └── Option 3 → Exit program
```

---

## 4. Implementation

### 4.1 Validation Stage

Before a password is accepted, it must pass three checks:

| Rule | Requirement |
|------|-------------|
| Minimum length | At least 10 characters |
| Starting character | Must not start with a number |
| Restricted symbols | Must not contain `^ * ( ) %` |

If a password fails a rule, a specific error message is shown and the user
is prompted again, repeating until a valid password is entered.

### 4.2 Scoring Stage

Once accepted, the password is scored out of 10:

| Criterion | Points |
|-----------|--------|
| Length of 14+ characters | +2 |
| Length of 10–13 characters | +1 |
| Contains a lowercase letter | +2 |
| Contains an uppercase letter | +2 |
| Contains a number | +2 |
| Contains a special character | +2 |
| Contains a weak pattern (e.g. "password", "123", "qwerty", "abc", "letmein", "admin") | −2 |
| Same character repeated 4+ times in a row | −2 |

The score is capped between 0 and 10, then mapped to a label:

| Score Range | Label |
|-------------|-------|
| 0–3 | Very Weak |
| 4–5 | Weak |
| 6–7 | Moderate |
| 8–9 | Strong |
| 10 | Very Strong |

### 4.3 Function-Wise Breakdown

| Function | Purpose |
|----------|---------|
| `check_len(pw)` | Checks minimum length |
| `check_not_start_with_number(pw)` | Checks the password doesn't start with a digit |
| `check_no_bad_symbols(pw)` | Checks for restricted symbols |
| `find_error(pw)` | Runs all validation checks, returns the first error or `None` |
| `set_password()` | Repeatedly prompts until a valid password is entered |
| `check_pw(pw)` | Calculates the score and builds feedback |
| `label(sc)` | Converts a score into a strength label |
| `show_strength(pw)` | Prints the score, label, and recommendations |
| `main()` | Runs the menu loop |

---

## 5. Results and Testing

The program was manually tested with a range of inputs to confirm correct
behaviour.

**Invalid password (too short):**
```
Enter a new password: short
Error: password must be at least 10 characters long.
```

**Invalid password (starts with a number):**
```
Enter a new password: 1StartsWithNum!
Error: password must not start with a number.
```

**Invalid password (restricted symbol):**
```
Enter a new password: Hello^World123
Error: password contains a restricted symbol. Avoid: ^*()%
```

**Valid but weak password:**
```
Enter a new password: helloworld
Password Strength: Very Weak  (3/10)
Recommendations:
- Use 14 or more characters to earn full length points.
- Include at least one uppercase letter.
- Include at least one number.
- Include a special character, other than ^ * ( ) %
```

**Valid, strong password with a weak pattern flagged:**
```
Enter a new password: MyPassword2024!
Password Strength: Strong  (8/10)
Recommendations:
- Avoid common patterns such as 'password'.
```

**Valid, very strong password:**
```
Enter a new password: Blue$Tiger#Runs42
Password Strength: Very Strong  (10/10)
Excellent, this is a strong password.
```

### 5.1 Testing Summary

- Passwords shorter than 10 characters are correctly rejected.
- Passwords starting with a digit are correctly rejected.
- Passwords with restricted symbols are correctly rejected.
- Scoring correctly rewards length and character variety, and penalizes
  weak words and repeated characters.
- The menu loop correctly handles invalid choices and repeats until Exit
  is selected.
- Checking strength before setting a password shows a warning instead of
  crashing.

---

## 6. Limitations

- Checks the structure of a password, not whether it has appeared in a
  real-world data breach.
- The password exists only in memory during the program's run; nothing is
  saved between sessions.
- Command-line only, with no graphical interface.

---

## 7. Future Scope

- Add a graphical user interface (GUI) using a library such as Tkinter.
- Check passwords against a breach database (e.g. the "Have I Been Pwned"
  API) for real-world leak detection.
- Maintain password history so a new password cannot repeat a previous one.
- Add automated unit tests using `unittest` or `pytest`.

---

## 8. Conclusion

The Password Strength Checker successfully demonstrates how basic input
validation and a rule-based scoring system can be combined to build a
practical, real-world useful tool. It reinforces core programming
concepts including functions, loops, string handling, and structured
program flow, while giving users a genuinely useful way to evaluate and
improve their password choices.

---

## 9. References

- Python official documentation: https://docs.python.org/3/
- OWASP Password Guidelines: https://owasp.org/www-community/password-special-characters
