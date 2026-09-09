# Bank Account Simulation System

A simple Python program that simulates basic bank account operations using an in-memory data structure. It supports account creation, deposits, withdrawals, and transaction history, all with input validation.

## Overview

This project simulates a basic banking system without a real database. It uses a single Python list to act as in-memory storage:

- `accounts` — stores all bank accounts, each as a dictionary with `name`, `balance`, and `transactions`
  - `transactions` is itself a list of dictionaries, each with `type` (`"Deposit"` or `"Withdrawal"`) and `amount`

The system validates every operation — account creation, deposits, and withdrawals — before applying it, and keeps a full transaction history per account.

## Features

- **Account creation** — validates a non-negative initial balance and blocks duplicate account names
- **Deposits** — validates the amount and increases the account balance
- **Withdrawals** — validates the amount and available funds, and decreases the account balance
- **Transaction history** — every deposit and withdrawal is logged against the account
- **Account summary** — displays an account's name, current balance, and full transaction history
- **Built-in test cases** — demonstrates deposits, withdrawals, an overdraft attempt, and a duplicate account attempt

## How It Works

1. `create_account(name, initial_balance)` validates that `initial_balance` is not negative and that no account with the same name already exists, raising a `ValueError` if either check fails. On success, it builds an account dictionary (with an empty `transactions` list) and appends it to `accounts`.
2. `deposit(name, amount)` validates that `amount` is greater than 0, locates the account by name, increases its balance, and logs a `"Deposit"` transaction. Returns the updated balance.
3. `withdraw(name, amount)` validates that `amount` is greater than 0 and that the account has sufficient funds, raising a `ValueError` if either check fails. On success, it decreases the balance and logs a `"Withdrawal"` transaction. Returns the updated balance.
4. `show_account(name)` prints the account's name, current balance, and every transaction in its history.

## Project Structure

```
├── bank_account_system.py   # Main script: data storage, functions, and tests
└── README.md
```

## Requirements

- Python 3.x
- No external dependencies (standard library only)

## Usage

Run the script directly to see the banking system in action:

```bash
python bank-account-simulation-system.py
```

The script includes a testing section at the bottom that:

| Step | Action                                      |
|------|-----------------------------------------------|
| 1    | Creates at least one account                   |
| 2    | Performs multiple deposits                     |
| 3    | Performs multiple withdrawals                  |
| 4    | Attempts an overdraft (should fail)            |
| 5    | Attempts to create a duplicate account (should fail) |
| 6    | Displays the account summary                   |

## Validation Rules Summary

| Operation       | Rule(s)                                              |
|-----------------|--------------------------------------------------------|
| Create account  | Initial balance must not be negative; name must be unique |
| Deposit         | Amount must be greater than 0                          |
| Withdraw        | Amount must be greater than 0; balance must be sufficient |

## Author

Ahmed Reda
