# bank-management-system
accounts = {}


def create_account():
    print("\n--- Create New Account ---")

    account_number = input("Enter account number: ")

    if account_number in accounts:
        print("Account already exists!")
        return

    name = input("Enter account holder name: ")
    phone = input("Enter phone number: ")
    initial_deposit = float(input("Enter initial deposit amount: "))

    if initial_deposit < 0:
        print("Deposit amount cannot be negative!")
        return

    accounts[account_number] = {
        "name": name,
        "phone": phone,
        "balance": initial_deposit
    }

    print("Account created successfully!")


def deposit_money():
    print("\n--- Deposit Money ---")

    account_number = input("Enter account number: ")

    if account_number not in accounts:
        print("Account not found!")
        return

    amount = float(input("Enter amount to deposit: "))

    if amount <= 0:
        print("Please enter a valid amount!")
        return

    accounts[account_number]["balance"] += amount

    print("Money deposited successfully!")
    print("New balance:", accounts[account_number]["balance"])


def withdraw_money():
    print("\n--- Withdraw Money ---")

    account_number = input("Enter account number: ")

    if account_number not in accounts:
        print("Account not found!")
        return

    amount = float(input("Enter amount to withdraw: "))

    if amount <= 0:
        print("Please enter a valid amount!")
        return

    if amount > accounts[account_number]["balance"]:
        print("Insufficient balance!")
        return

    accounts[account_number]["balance"] -= amount

    print("Money withdrawn successfully!")
    print("Remaining balance:", accounts[account_number]["balance"])


def check_balance():
    print("\n--- Check Balance ---")

    account_number = input("Enter account number: ")

    if account_number not in accounts:
        print("Account not found!")
        return

    balance = accounts[account_number]["balance"]

    print("Account Balance:", balance)


def account_details():
    print("\n--- Account Details ---")

    account_number = input("Enter account number: ")

    if account_number not in accounts:
        print("Account not found!")
        return

    account = accounts[account_number]

    print("\nAccount Number :", account_number)
    print("Account Holder :", account["name"])
    print("Phone Number   :", account["phone"])
    print("Balance        :", account["balance"])


while True:

    print("\n==============================")
    print("     BANK MANAGEMENT SYSTEM")
    print("==============================")
    print("1. Create Account")
    print("2. Deposit Money")
    print("3. Withdraw Money")
    print("4. Check Balance")
    print("5. Account Details")
    print("6. Exit")
    print("==============================")

    choice = input("Enter your choice: ")

    if choice == "1":
        create_account()

    elif choice == "2":
        deposit_money()

    elif choice == "3":
        withdraw_money()

    elif choice == "4":
        check_balance()

    elif choice == "5":
        account_details()

    elif choice == "6":
        print("Thank you for using Bank Management System!")
        break

    else:
        print("Invalid choice! Please try again.")
