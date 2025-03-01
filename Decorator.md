## **1. What is a Decorator?**
A decorator is a function that **modifies the behavior of another function** without changing its source code. It "wraps" another function to add features like logging, timing, or access control.

---

## **2. Basic Decorator Syntax**
### **Example: Logging Decorator**
```python
def logger(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__} with args: {args}, kwargs: {kwargs}")
        result = func(*args, **kwargs)  # Execute the original function
        print(f"{func.__name__} returned {result}")
        return result
    return wrapper

@logger
def add(a, b):
    return a + b

add(3, 5)
# Output:
# Calling add with args: (3, 5), kwargs: {}
# add returned 8
```

### **How It Works**:
1. `logger` is the decorator function.
2. `wrapper` wraps `add` to add logging.
3. `@logger` applies the decorator to `add`.

---

## **3. Decorators with Arguments**
To pass arguments to a decorator, nest another layer of functions:
```python
def repeat(n):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(n):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(3)
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")
# Output:
# Hello, Alice!
# Hello, Alice!
# Hello, Alice!
```

---

## **4. Preserving Function Metadata**
Use `functools.wraps` to retain the original function’s name/docstring:
```python
from functools import wraps

def timer(func):
    @wraps(func)  # Preserves func's metadata
    def wrapper(*args, **kwargs):
        import time
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.2f}s")
        return result
    return wrapper

@timer
def slow_func():
    """Simulates a slow function."""
    time.sleep(2)

print(slow_func.__name__)  # Output: slow_func (instead of wrapper)
print(slow_func.__doc__)   # Output: Simulates a slow function.
```

---

## **5. Stacking Decorators**
Apply multiple decorators (executed from bottom to top):
```python
@timer
@logger
def multiply(a, b):
    return a * b

multiply(3, 4)
# Output:
# Calling multiply with args: (3, 4), kwargs: {}
# multiply returned 12
# multiply took 0.00s
```

---

## **6. Common Use Cases**
### **A. Authorization**
```python
def requires_admin(func):
    @wraps(func)
    def wrapper(user, *args, **kwargs):
        if user != "admin":
            raise PermissionError("Admin access required!")
        return func(*args, **kwargs)
    return wrapper

@requires_admin
def delete_database(user):
    print("Database deleted!")

delete_database("admin")  # Works
delete_database("guest")  # Raises PermissionError
```

### **B. Memoization (Caching)**
```python
def memoize(func):
    cache = {}
    @wraps(func)
    def wrapper(*args):
        if args not in cache:
            cache[args] = func(*args)
        return cache[args]
    return wrapper

@memoize
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

print(fibonacci(10))  # Computed efficiently due to caching
```

---

## **7. Class-Based Decorators**
Implement decorators using classes with `__call__`:
```python
class CountCalls:
    def __init__(self, func):
        self.func = func
        self.calls = 0

    def __call__(self, *args, **kwargs):
        self.calls += 1
        print(f"Call {self.calls} of {self.func.__name__}")
        return self.func(*args, **kwargs)

@CountCalls
def say_hello():
    print("Hello!")

say_hello()  # Output: Call 1 of say_hello → Hello!
say_hello()  # Output: Call 2 of say_hello → Hello!
```

---

## **8. Key Takeaways**
| Concept               | Description                                  | Example                          |
|-----------------------|----------------------------------------------|----------------------------------|
| **Basic Decorator**   | Wraps a function to add functionality        | `@logger`                        |
| **Decorator with Args** | Uses nested functions for configuration   | `@repeat(3)`                     |
| **Stacking**          | Apply multiple decorators (order matters)    | `@timer` → `@logger`             |
| **Metadata**          | Use `@wraps(func)` to preserve info          | `from functools import wraps`    |
| **Common Uses**       | Logging, timing, caching, access control     | `@memoize`, `@requires_admin`    |

---

## **9. Pitfalls to Avoid**
1. **Accidental Side Effects**: Ensure decorators don’t modify function arguments/returns unexpectedly.
2. **Overusing Decorators**: Can make code harder to debug if stacked deeply.
3. **Mutable Defaults**: Avoid mutable default arguments in decorators (e.g., `cache={}`).
