
## **1. Defining a Function**
Use the `def` keyword to create a function. Functions encapsulate code for reuse.

### **Syntax:**
```python
def function_name(parameters):
    """Docstring (optional)"""
    # Code block
    return value  # Optional
```

### **Example:**
```python
def greet():
    print("Hello, World!")

# Call the function
greet()  # Output: Hello, World!
```

---

## **2. Parameters and Arguments**
- **Parameters**: Variables listed in the function definition.
- **Arguments**: Actual values passed to the function.

### **Example:**
```python
def add(a, b):  # a and b are parameters
    return a + b

result = add(3, 5)  # 3 and 5 are arguments
print(result)       # Output: 8
```

---

## **3. Return Statement**
- The `return` statement exits the function and sends back a value.
- If no `return` is specified, the function returns `None`.

### **Example:**
```python
def square(num):
    return num ** 2

print(square(4))  # Output: 16
```

---

## **4. Default Parameters**
Assign default values to parameters (used if no argument is provided).

### **Example:**
```python
def greet(name="Guest"):
    print(f"Hello, {name}!")

greet("Alice")  # Output: Hello, Alice!
greet()         # Output: Hello, Guest!
```

---

## **5. Variable Scope**
- **Local Variables**: Defined inside a function (not accessible outside).
- **Global Variables**: Defined outside a function (accessible everywhere).

### **Example:**
```python
x = 10  # Global variable

def my_func():
    y = 5  # Local variable
    print(x + y)  # Access global x

my_func()  # Output: 15
# print(y)  # Error: y is local to my_func
```

---

## **6. Docstrings**
Document your function using a **docstring** (enclosed in triple quotes).

### **Example:**
```python
def multiply(a, b):
    """Multiply two numbers and return the result."""
    return a * b

# Access the docstring
print(multiply.__doc__)  # Output: Multiply two numbers...
```

---

## **7. Lambda Functions**
Small anonymous functions defined with `lambda`.

### **Example:**
```python
# Equivalent to: def square(x): return x**2
square = lambda x: x ** 2

print(square(3))  # Output: 9

# Often used with map/filter
numbers = [1, 2, 3]
squared = list(map(lambda x: x**2, numbers))  # [1, 4, 9]
```

---

## **8. Common Function Types**
### **A. No Parameters/No Return**
```python
def say_hello():
    print("Hello!")
```

### **B. With Parameters and Return**
```python
def power(base, exponent):
    return base ** exponent
```

### **C. Arbitrary Arguments (`*args` and `**kwargs`)**
```python
# *args: Accepts any number of positional arguments
def sum_all(*args):
    return sum(args)

print(sum_all(1, 2, 3))  # Output: 6

# **kwargs: Accepts keyword arguments as a dictionary
def user_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

user_info(name="Alice", age=30)
```

---

## **9. Type Hints (Python 3.5+)**
Specify expected data types for parameters and return values (optional but improves readability).

### **Example:**
```python
def add(a: int, b: int) -> int:
    return a + b
```

---

## **10. Common Mistakes**
- **Missing Colon**: Forgetting `:` after `def`.
- **Incorrect Indentation**: Code inside the function must be indented.
- **Confusing Parameters/Arguments**: Parameters are placeholders; arguments are actual values.

---

## **11. Advanced Topics**
### **A. Recursion**
A function calling itself.

```python
def factorial(n):
    if n == 1:
        return 1
    else:
        return n * factorial(n-1)

print(factorial(5))  # Output: 120
```

### **B. Nested Functions**
Functions defined inside other functions.

```python
def outer():
    def inner():
        print("Inside inner function")
    inner()

outer()  # Output: Inside inner function
```

### **C. Decorators**
Modify or extend function behavior.

```python
def debug(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

@debug
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")  # Output: Calling greet → Hello, Alice!
```

---

## **Summary**
- **Reusable Code**: Functions encapsulate logic for reuse.
- **Parameters/Arguments**: Pass data into functions.
- **Return Values**: Send data back to the caller.
- **Scope**: Variables inside functions are local by default.
- **Flexibility**: Use `*args`, `**kwargs`, and default parameters for dynamic behavior.
