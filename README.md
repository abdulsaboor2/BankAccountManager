# BankAccountManager

## Description
BankAccountManager is a Python-based application that simulates basic banking operations. The program allows users to perform deposits, withdrawals, and view account and Credits details after a simple login process it will display a menu what do you want to perform. It showcases the use of object-oriented programming (OOP) concepts in Python.

## Features
- **Account Creation**: Create bank accounts with an account name and number.
- **Deposit Money**: Deposit a specified amount into the account.
- **Withdraw Money**: Withdraw a specified amount from the account, subject to sufficient funds.
- **Account Details**: Display the account name, account number, and current balance.
- **Authentication**: Simple login mechanism to access account operations.
- **Account Locked**: Add 3 time wrong Account No, then account will be locked.

## How to Use
1. **Clone the Repository**:
    ```bash
    git clone https://github.com/abdulsaboor2/BankAccountManager.git
    cd BankAccountManager
    ```

2. **Run the Program**:
    ```bash
    python DMS.py
    ```

3. **Follow the On-Screen Prompts**:
    - Enter your account number (`1111` for Batman or `2222` for Robin).
    - After successful login, choose an operation from the menu:
        1. Deposit Money
        2. Withdraw Money
        3. Display Account Details
        4. Exit

## Code Overview

```python
class BankAccount:
    def __init__(self, account_name, account_number):
        self.account_name = account_name
        self.account_number = account_number
        self.balance = 0

    def getAccountName(self):
        return self.account_name

    def getAccountNumber(self):
        return self.account_number

    def getBalance(self):
        return self.balance

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            print("Deposited ", amount, "£. New balance: ", self.balance, "£.")
        else:
            print("Invalid deposit amount. Please provide a positive value.")

    def withdraw(self, amount):
        if 0 < amount <= self.balance:
            self.balance -= amount
            print("Withdrew ", amount, "£. New balance: ", self.balance, "£.")
        else:
            print("Insufficient funds or invalid withdrawal amount.")

acc1 = BankAccount("Batman", "1111")
acc2 = BankAccount("Robin", "2222")

count = 0
login = "0"
while True:
    if count == 0:
        rep = 3
        while rep >= 1:
            rep -= 1
            accNumber = input("Enter your account Number: ")
            if accNumber == "1111" or accNumber == "2222":
                print("Login Successfully")
                login = accNumber
                break
            else:
                print("Please Enter Correct Account No. You have only ", rep, " Attempt Left")
                if rep == 0:
                    print("Please Come Back Later. You Are Not Authorized to transact")
                    count = 1
    
    if count == 1:
        break
    else:
        count = 2
        print("Please Enter Your Choice from 1 to 3")
        print("Press 1 for Deposit Money")
        print("Press 2 for Withdraw Money")
        print("Press 3 for Display Account Details")
        print("Press any other key to Exit")

        print(" ")
        choice = input("Enter Your Choice: ")

        if choice == "1":
            amount = int(input("Enter Your Deposit Amount: "))
            if login == accNumber:
                acc1.deposit(amount)
            else:
                acc2.deposit(amount)

            print("")
        elif choice == "2":
            wit = int(input("Enter Your Withdraw Amount: "))
            if login == accNumber:
                acc1.withdraw(wit)
            else:
                acc2.withdraw(wit)

            print("")
        elif choice == "3":
            if login == accNumber:
                print("Account Name: ", acc1.getAccountName(), ", Account Number: ", acc1.getAccountNumber(), ", Balance: ", acc1.getBalance(), "£ ")
            else:
                print("Account Name: ", acc2.getAccountName(), ", Account Number: ", acc2.getAccountNumber(), ", Balance: ", acc2.getBalance(), "£ ")
        else:
            print("Thank You!")
            break
