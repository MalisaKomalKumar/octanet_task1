# octanet_task1
This is my Task as an intern at OctaNet ,  This is a program written in the Python language. Simple ATM program
import time

print("Please insert your CARD")

time.sleep(5)  # Simulate card insertion (optional)

def validate_pin():
    password = 1234
    pin = int(input("Enter your PIN: "))
    if pin == password:
        return True
    else:
        print("Wrong PIN. Please try again.")
        return False

if validate_pin():
    balance = 5000

    while True:
        print("""
                1. Balance
                2. Withdraw Cash
                3. Deposit Cash
                4. Exit
                """)

        try:
            option = int(input("Please enter your choice: "))
        except ValueError:
            print("Invalid option. Please enter a number (1-4).")
            continue  # Skip to the next iteration of the loop

        if option == 1:
            print(f"Your current balance is ${balance:.2f}")  # Format for currency

        elif option == 2:
            withdraw_amount = int(input("Enter the amount to withdraw: "))

            if withdraw_amount > balance:
                print("Insufficient funds. Please enter an amount less than or equal to your balance.")
            else:
                balance -= withdraw_amount
                print(f"You have withdrawn ${withdraw_amount:.2f}")
                print(f"Your current balance is ${balance:.2f}")

        elif option == 3:
            deposit_amount = int(input("Enter the amount to deposit: "))
            balance += deposit_amount
            print(f"${deposit_amount:.2f} has been deposited to your account.")
            print(f"Your current balance is ${balance:.2f}")

        elif option == 4:
            print("Thank you for banking with us!")
            break  # Exit the loop

        else:
            print("Invalid option. Please enter a number (1-4).")

else:
    print("Maximum PIN attempts reached. Your card has been locked. Please contact your bank.")
