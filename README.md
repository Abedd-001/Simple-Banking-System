# Simple Banking System

A command-line banking system written in Python. Accounts are stored in a local SQLite database, and card numbers are generated and validated with the Luhn algorithm.

## Features

- Create an account with a generated card number (starts with `400000`, ends with a Luhn check digit) and a random 4-digit PIN
- Log in with card number and PIN
- Check balance
- Add income
- Transfer money to another card (validates the card number with the Luhn algorithm and checks that the card exists and that the balance is sufficient)
- Close an account
- Log out / exit

## Requirements

- Python 3.6+
- No external packages (uses only `random`, `sys`, and `sqlite3` from the standard library)

## Usage

```bash
python banking_system.py
```

On first run, a `card.s3db` SQLite database file is created in the current folder with a `card` table:

| Column  | Type    | Notes                  |
|---------|---------|------------------------|
| id      | INTEGER | Primary key            |
| number  | TEXT    | 16-digit card number   |
| pin     | TEXT    | 4-digit PIN            |
| balance | INTEGER | Defaults to 0          |

## Menu

```
1. Create an account
2. Log into account
0. Exit
```

After logging in:

```
1. Balance
2. Add income
3. Do transfer
4. Close account
5. Log out
0. Exit
```

## How the card number is built

1. IIN: `400000`
2. Account identifier: 9 random digits
3. Checksum: the last digit, calculated with the Luhn algorithm so the full 16-digit number is valid

## Disclaimer

This is an educational project. It is not meant for real banking use: PINs are stored in plain text and there is no real authentication or security layer.
