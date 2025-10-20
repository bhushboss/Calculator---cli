# Calculator---cli
# calculator.py  
# A simple command-line calculator supporting basic arithmetic operations with history.  
  
def add(x, y):  
    """Add two numbers."""  
    return x + y  
  
def subtract(x, y):  
    """Subtract y from x."""  
    return x - y  
  
def multiply(x, y):  
    """Multiply two numbers."""  
    return x * y  
  
def divide(x, y):  
    """Divide x by y, handling division by zero."""  
    if y == 0:  
        return "Error: Division by zero!"  
    return x / y  
  
def modulo(x, y):  
    """Return the remainder of x divided by y, handling division by zero."""  
    if y == 0:  
        return "Error: Modulo by zero!"  
    return x % y  
  
def store_in_history(history, expression, result):  
    """Store a calculation in the history list."""  
    if isinstance(result, str):  # Error case  
        history.append(f"{expression} = {result}")  
    else:  
        history.append(f"{expression} = {result}")  
  
def view_history(history):  
    """Display the calculation history."""  
    if not history:  
        print("No calculations in history yet.")  
        return  
    print("\n--- Calculation History ---")  
    for i, calc in enumerate(history[-10:], 1):  # Show last 10 calculations  
        print(f"{i}. {calc}")  
    print("---------------------------")  
  
def clear_history(history):  
    """Clear the calculation history."""  
    history.clear()  
    print("History cleared.")  
  
def main():  
    """Main function to run the calculator loop."""  
    history = []  # List to store calculation history  
    print("=== Welcome to the Calculator CLI ===")  
      
    while True:  
        print("\nSelect an operation:")  
        print("1: Add (+)")  
        print("2: Subtract (-)")  
        print("3: Multiply (*)")  
        print("4: Divide (/)")  
        print("5: Modulo (%)")  
        print("H: View History")  
        print("C: Clear History")  
        print("X: Exit")  
          
        choice = input("Enter choice (1-5/H/C/X): ").strip().upper()  
          
        if choice == 'X':  
            print("Goodbye! Thanks for using the calculator.")  
            break  
          
        if choice.isdigit() and 1 <= int(choice) <= 5:  
            choice_num = int(choice)  
            try:  
                num1 = float(input("Enter the first number: "))  
                num2 = float(input("Enter the second number: "))  
            except ValueError:  
                print("Invalid input! Please enter valid numbers.")  
                continue  
              
            if choice_num == 1:  
                result = add(num1, num2)  
                expression = f"{num1} + {num2}"  
            elif choice_num == 2:  
                result = subtract(num1, num2)  
                expression = f"{num1} - {num2}"  
            elif choice_num == 3:  
                result = multiply(num1, num2)  
                expression = f"{num1} * {num2}"  
            elif choice_num == 4:  
                result = divide(num1, num2)  
                expression = f"{num1} / {num2}"  
            elif choice_num == 5:  
                result = modulo(num1, num2)  
                expression = f"{num1} % {num2}"  
              
            print(f"{expression} = {result}")  
            store_in_history(history, expression, result)  
          
        elif choice == 'H':  
            view_history(history)  
          
        elif choice == 'C':  
            clear_history(history)  
          
        else:  
            print("Invalid choice! Please select 1-5, H, C, or X.")  
  
if __name__ == "__main__":  
    main()
