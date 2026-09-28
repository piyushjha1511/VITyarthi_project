# Password Strength Checker

A small command-line tool written in Python that lets you set a password, validates it against a few basic rules, and rates its strength out of 10 with tips to improve it.

## Features

- Menu-driven interface (set a password, check its strength, exit)
- Validation rules that reject unacceptable passwords with a clear error message
- Strength score from 0 to 10 with a label from *Very Weak* to *Very Strong*
- Personalised recommendations on how to make the password stronger
- No external libraries needed

## Requirements

- **Python 3.10 or newer** (the program uses `match` statements, which were introduced in Python 3.10)

Check your version with:

```bash
python --version
```

## How to Run

1. Clone the repository:

   ```bash
   git clone https://github.com/piyushjha1511/VITyarthi_project.git
   cd VITyarthi_project
   ```

2. Run the program:

   ```bash
   python password_checker.py
   ```

   On some systems you may need to use `python3` instead of `python`.

## Usage

When you start the program you will see this menu:

```
===== Password Strength Checker =====
1. Set or replace password
2. Check password strength (out of 10)
3. Exit
Please choose an option (1-3):
```

- **Option 1**: enter a new password. If it breaks a rule, you will see an error and be asked to try again until it is valid.
- **Option 2**: rate the password you set. You must set a password with option 1 first.
- **Option 3**: exit the program.

### Example Session

```
Enter a new password: MyPassword2024!
Password updated successfully.

Password Strength: Strong  (8/10)

Recommendations:
- Avoid common patterns such as 'password'.
```

## Password Rules (Validation)

A password is only accepted if it:

| Rule | Detail |
|------|--------|
| Has a minimum length | At least **10** characters |
| Does not start with a number | The first character must not be a digit |
| Avoids restricted symbols | Must not contain `^` `*` `(` `)` `%` |

## Scoring System

Once a password is valid, it is scored out of **10**:

| Criterion | Points |
|-----------|--------|
| Length of 14 or more characters | +2 |
| Length of 10 to 13 characters | +1 |
| Contains a lowercase letter | +2 |
| Contains an uppercase letter | +2 |
| Contains a number | +2 |
| Contains a special character (any non-alphanumeric character) | +2 |
| Contains a common pattern (`123`, `password`, `qwerty`, `abc`, `letmein`, `admin`) | −2 |
| Repeats the same character 4 or more times in a row | −2 |

The final score is kept between 0 and 10.

### Strength Labels

| Score | Label |
|-------|-------|
| 0 to 3 | Very Weak |
| 4 to 5 | Weak |
| 6 to 7 | Moderate |
| 8 to 9 | Strong |
| 10 | Very Strong |

## Project Structure

```
VITyarthi_project/
├── password_checker.py   # The full program
└── README.md             # Project documentation
```

## How It Works

- `find_error(pw)` runs the validation checks (`check_len`, `check_not_start_with_number`, `check_no_bad_symbols`) and returns an error message, or `None` if the password is valid.
- `set_password()` keeps prompting until the user enters a valid password.
- `check_pw(pw)` calculates the score and builds the list of recommendations.
- `label(sc)` converts a score into a strength label.
- `show_strength(pw)` prints the result to the user.
- `main()` runs the menu loop.

## Notes

- The password is stored only in memory while the program runs. It is never saved to a file or sent anywhere.
- Spaces count as special characters in the scoring.
- This is a learning project. The scoring is a simple heuristic and is not a substitute for a professional password audit.

## Author

Piyush Jha
