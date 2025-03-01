## variables and data types with examples:

---

## **Variables**
- Variables are containers for storing data values.
- No explicit declaration needed (dynamic typing).
- Created when you assign a value.

### **Example:**
```python
# Assign values to variables
x = 10             # Integer
name = "Alice"     # String
is_student = True  # Boolean
pi = 3.14          # Float
```

---

## **Basic Data Types**

| Data Type      | Description                  | Example                   |
|----------------|------------------------------|---------------------------|
| `int`          | Integer values               | `x = 42`                  |
| `float`        | Decimal values               | `y = 3.14`                |
| `str`          | Text (enclosed in quotes)    | `s = "Hello"`             |
| `bool`         | Boolean (`True`/`False`)     | `is_valid = True`         |
| `NoneType`     | Represents absence of value  | `result = None`           |

---

## **Composite Data Types**

| Data Type      | Description                  | Example                           |
|----------------|------------------------------|-----------------------------------|
| `list`         | Ordered, mutable sequence    | `numbers = [1, 2, 3]`            |
| `tuple`        | Ordered, **immutable** sequence | `colors = ("red", "green")`     |
| `set`          | Unordered, unique elements   | `unique = {1, 2, 3}`             |
| `dict`         | Key-value pairs              | `person = {"name": "Alice", "age": 30}` |

---

## **Type Checking**
Use `type()` to check the data type of a variable:
```python
x = 5
print(type(x))  # Output: <class 'int'>
```

---

## **Type Conversion**
Convert between types using built-in functions:
```python
# Convert to integer
num_str = "123"
num_int = int(num_str)

# Convert to string
age = 25
age_str = str(age)

# Convert to float
x = float(10)  # 10.0
```

---

## **Key Points**
1. **Dynamic Typing**: Variables can change types.
   ```python
   x = 10     # x is an integer
   x = "ten"  # Now x is a string
   ```

2. **Case Sensitivity**: `Name` and `name` are different variables.

3. **Naming Rules**:
   - Start with a letter or `_`.
   - Can include letters, numbers, and `_`.
   - Use snake_case (e.g., `user_name`).

---

## **Example with All Types**
```python
# Basic types
integer = 42
floating = 3.14
text = "Python"
boolean = True

# Composite types
my_list = [1, "apple", 3.14]
my_tuple = (1, 2, 3)
my_set = {1, 2, 2, 3}  # {1, 2, 3} (duplicates removed)
my_dict = {"name": "Bob", "age": 25}

# Special value
nothing = None
```

---

## **Common Operations**
### **Strings**
```python
s = "hello"
print(s.upper())      # "HELLO"
print(s + " world")   # "hello world"
```

### **Lists**
```python
numbers = [1, 2, 3]
numbers.append(4)     # [1, 2, 3, 4]
```

### **Dictionaries**
```python
person = {"name": "Alice", "age": 30}
print(person["name"])  # "Alice"
```

---

## **Summary**
- Use variables to store data.
- Python infers types dynamically.
- Convert between types explicitly when needed.
- Choose the right data structure (list, tuple, dict, etc.) for your task.
