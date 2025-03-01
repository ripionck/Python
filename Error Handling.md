## **1. Basic Try-Except Block**
Catch and handle exceptions to prevent program crashes.

```python
try:
    # Code that might raise an error
    result = 10 / 0
except ZeroDivisionError:
    # Handle specific error
    print("Cannot divide by zero!")
```

---

## **2. Handling Multiple Exceptions**
Catch different types of errors separately.

```python
try:
    num = int(input("Enter a number: "))
    result = 10 / num
    print("Result:", result)
except ValueError:
    print("Invalid input! Enter a number.")
except ZeroDivisionError:
    print("Cannot divide by zero!")
```

---

## **3. Generic Exception Handling**
Catch all exceptions (use cautiously to avoid hiding bugs).

```python
try:
    # Risky code
    file = open("missing.txt", "r")
except Exception as e:
    print(f"An error occurred: {e}")
```

---

## **4. Else Clause**
Execute code only if no exceptions were raised.

```python
try:
    print("Attempting connection...")
    # Simulate successful connection
except ConnectionError:
    print("Connection failed!")
else:
    print("Connection successful!")
    # Perform post-connection tasks
```

---

## **5. Finally Clause**
Always execute cleanup code (e.g., closing files).

```python
try:
    file = open("data.txt", "r")
    content = file.read()
except FileNotFoundError:
    print("File not found!")
finally:
    file.close()  # Always runs
    print("Cleanup complete.")
```

---

## **6. Raising Exceptions**
Trigger errors manually with `raise`.

```python
def validate_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative.")
    return True

try:
    validate_age(-5)
except ValueError as ve:
    print(ve)  # Output: Age cannot be negative.
```

---

## **7. Custom Exceptions**
Create application-specific errors.

```python
class InvalidEmailError(Exception):
    """Raised for invalid email formats"""
    pass

def send_email(email):
    if "@" not in email:
        raise InvalidEmailError(f"Invalid email: {email}")

try:
    send_email("user.example.com")
except InvalidEmailError as iee:
    print(iee)
```

---

## **8. Built-in Exceptions**
Common exception types to handle:

| Exception              | Cause                                  |
|------------------------|----------------------------------------|
| `ValueError`           | Invalid value (e.g., `int("text")`)    |
| `TypeError`            | Invalid operation (e.g., `"a" + 5`)    |
| `IndexError`           | Invalid list/index access              |
| `KeyError`             | Missing dictionary key                 |
| `FileNotFoundError`    | File doesn’t exist                     |
| `ZeroDivisionError`    | Division by zero                       |

---

## **9. Best Practices**
1. **Be Specific**: Catch specific exceptions first.
   ```python
   try:
       # Code
   except FileNotFoundError:
       # Handle file not found
   except Exception:
       # Generic fallback
   ```

2. **Log Errors**: Use logging instead of `print()`.
   ```python
   import logging
   logging.basicConfig(filename='errors.log', level=logging.ERROR)

   try:
       # Risky code
   except Exception as e:
       logging.error(f"Error: {e}")
   ```

3. **Avoid Bare Excepts**: Never use `except:` without specifying an error type.

4. **Use Finally for Cleanup**: Ensure resources (files, connections) are released.

---

## **10. Practical Example: File Handling**
Combine multiple error-handling techniques.

```python
def read_file(filename):
    try:
        with open(filename, "r") as file:
            content = file.read()
    except FileNotFoundError:
        print(f"File {filename} not found!")
    except PermissionError:
        print("Permission denied!")
    else:
        print("File read successfully.")
        return content
    finally:
        print("Operation attempted.")

read_file("data.txt")
```

---

## **Key Takeaways**
| Concept                | Syntax/Example                          | Purpose                                 |
|------------------------|-----------------------------------------|-----------------------------------------|
| **Basic Handling**     | `try-except`                            | Catch and recover from errors           |
| **Multiple Errors**    | Multiple `except` blocks                | Handle different error types            |
| **Cleanup**            | `finally` clause                        | Ensure resources are released           |
| **Manual Errors**      | `raise ExceptionType("message")`        | Trigger custom errors                   |
| **Custom Errors**      | `class MyError(Exception): pass`        | Create application-specific exceptions  |
