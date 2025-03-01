### **Input/Output in Python: Reading from and Writing to the Console**
---

## **1. Output: Writing to the Console**
### **`print()` Function**  
Used to display messages, variables, or results directly to the console.  
**Syntax**:  
```python
print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)
```

#### **Examples**:
```python
# Print a string
print("Hello, World!")  # Output: Hello, World!

# Print variables
name = "Alice"
age = 25
print("Name:", name, "Age:", age)  # Output: Name: Alice Age: 25

# Formatting with f-strings (Python 3.6+)
print(f"{name} is {age} years old.")  # Output: Alice is 25 years old.

# Custom separators and end characters
print("Python", "is", "fun", sep="-", end="!\n")  # Output: Python-is-fun!
```

---

## **2. Input: Reading from the Console**  
### **`input()` Function**  
Reads a line of text from the user and returns it as a **string**.  
**Syntax**:  
```python
input(prompt_message)
```

#### **Examples**:
```python
# Basic input
name = input("Enter your name: ")  # User types "Bob"
print(f"Hello, {name}!")  # Output: Hello, Bob!

# Convert input to other data types
age = int(input("Enter your age: "))  # User types "30"
print(f"You are {age} years old.")  # Output: You are 30 years old.

# Read multiple values in one line
values = input("Enter two numbers (space-separated): ").split()
num1, num2 = map(int, values)  # Converts to integers
print(f"Sum: {num1 + num2}")  # Output: Sum: 15 (if inputs are 5 and 10)
```

---

## **3. Common Use Cases**  
### **A. Simple Form**  
```python
# Collect user details
name = input("Name: ")
email = input("Email: ")
print(f"Welcome, {name}! We’ll contact you at {email}.")
```

### **B. Calculator**  
```python
# Read two numbers and perform arithmetic
num1 = float(input("Enter first number: "))
num2 = float(input("Enter second number: "))
print(f"{num1} + {num2} = {num1 + num2}")
print(f"{num1} * {num2} = {num1 * num2}")
```

### **C. Password Input (Hidden)**  
Use the `getpass` module to hide sensitive input:  
```python
from getpass import getpass
password = getpass("Enter password: ")  # Input is not visible
```

---

## **4. Key Notes**  
1. **Input Always Returns a String**:  
   - Use `int()`, `float()`, or `eval()` to convert inputs to other types.  
   - **Caution**: Avoid `eval()` for untrusted inputs (security risk).  

2. **Handling Multiple Inputs**:  
   - Split using `split()` and convert to desired types.  
   ```python
   # Read three integers in one line
   a, b, c = map(int, input("Enter three numbers: ").split())
   ```

3. **Error Handling**:  
   - Use `try-except` blocks to handle invalid inputs.  
   ```python
   try:
       age = int(input("Age: "))
   except ValueError:
       print("Invalid input! Enter a number.")
   ```

---

## **5. Advanced Formatting**  
### **A. Formatting Numbers**  
```python
pi = 3.1415926535
print(f"Pi rounded to 2 decimals: {pi:.2f}")  # Output: 3.14
```

### **B. Table Output**  
```python
# Align text in columns
print(f"{'Name':<10} {'Age':<5}")  # Left-aligned
print(f"{'Alice':<10} {25:<5}")
print(f"{'Bob':<10} {30:<5}")
```
**Output**:  
```
Name       Age  
Alice      25   
Bob        30   
```

---

## **6. Summary**  
| Task               | Function/Method                     | Example                          |
|--------------------|-------------------------------------|----------------------------------|
| **Print**          | `print()`                           | `print("Hello")`                 |
| **Read Input**     | `input()`                           | `name = input("Name: ")`         |
| **Convert Input**  | `int()`, `float()`, `str()`         | `age = int(input("Age: "))`      |
| **Format Output**  | f-strings, `format()`               | `print(f"Value: {x:.2f}")`       |
