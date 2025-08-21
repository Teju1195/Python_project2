# Python_project2
expense=[]
def add_expense():
 #name error
    try:
        Name=input("Enter Expense name:")
        if not Name.strip():
            raise ValueError("Name Cannot be Empty")
        if Name.isdigit():
            raise TypeError("Name cannot be only Numbers")
#amount error
        try:
            amount=float(input("Enter the Amount: RS."))
        except ValueError:
            print("Amount must be a Number")
            return
    except(ValueError,TypeError) as e:
        print(e)
    else:
        expense.append((Name,amount))
        print("Expense added successfully.")
    finally:
        print("Returning to menu\n")

def view_expense():
    if not expense:
        print("No Expense Record.")
    else:
        total=0
        print("\n ----Expense List----")
        for e in expense:
            print(e[0],":Rs",e[1])
            total+=e[1]
            print("Total:Rs",total)
def remove_expense():
    try:
        view_expense()
        num=int(input("Enter Number to Remove:"))
        removed=expense.pop(num-1)
        print(f"Removed: {removed[0]}: Rs {removed[1]}")
    except (ValueError, IndexError):
        print("Invalid number!")

while True:
    print("\n--------EXPENSE TRACKER--------")
    print("1) Add Expense")
    print("2) View Expense")
    print("3) Remove Expense")
    print("4) Exit")
    choice=input("Enter Your Choice:")
    
    if choice == "1":
        add_expense()
    elif choice == "2":
        view_expense()
    elif choice == "3":
        remove_expense()
    elif choice == "4":
        print("Thank You")
        break
    else:
        print("Invalid choice!")
