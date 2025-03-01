## Testing and Debugging

---

## **1. Unit Testing**
Unit tests validate individual components (functions, classes) in isolation. Python provides the `unittest` module, and third-party tools like `pytest` simplify testing.

### **A. Using `unittest`**
```python
import unittest

def add(a, b):
    return a + b

class TestMathOperations(unittest.TestCase):
    def setUp(self):
        # Runs before each test (e.g., initialize resources)
        pass

    def tearDown(self):
        # Runs after each test (e.g., clean up)
        pass

    def test_add_positive_numbers(self):
        self.assertEqual(add(2, 3), 5)

    def test_add_negative_numbers(self):
        self.assertEqual(add(-1, -2), -3)

if __name__ == '__main__':
    unittest.main()
```

**Run Tests**:
```bash
python -m unittest test_math.py
```

### **B. Using `pytest`**
Install `pytest` first:
```bash
pip install pytest
```

**Example Test**:
```python
# test_math.py
def test_add_positive_numbers():
    assert add(2, 3) == 5

def test_add_negative_numbers():
    assert add(-1, -2) == -3
```

**Run Tests**:
```bash
pytest test_math.py -v
```

### **C. Key Features**
- **Fixtures**: Reusable setup/teardown logic (in `pytest`).
- **Parameterized Tests**: Test multiple inputs with a single function.
- **Mocking**: Simulate external dependencies using `unittest.mock`.

---

## **2. Debugging Techniques**
### **A. Built-in Debugger (`pdb`)**
Insert breakpoints to inspect code execution:
```python
def divide(a, b):
    import pdb; pdb.set_trace()  # Manual breakpoint
    return a / b

divide(10, 0)
```

**Common `pdb` Commands**:
| Command   | Description                  |
|-----------|------------------------------|
| `n`       | Execute next line            |
| `c`       | Continue until next breakpoint |
| `s`       | Step into function           |
| `l`       | Show current code context    |
| `p var`   | Print variable value         |
| `q`       | Quit debugger                |

### **B. IDE Debuggers**
Use graphical debuggers in IDEs like **VS Code**, **PyCharm**, or **Jupyter**:
- Set breakpoints by clicking the gutter.
- Inspect variables in real time.
- Step through code line-by-line.

### **C. Logging**
Track program flow without stopping execution:
```python
import logging

logging.basicConfig(level=logging.DEBUG)

def process_data(data):
    logging.debug(f"Processing data: {data}")
    # ... logic ...
```

---

## **3. Common Debugging Scenarios**
### **A. Handling Exceptions**
Catch and log errors:
```python
try:
    risky_operation()
except ValueError as e:
    print(f"Error: {e}")
    # Log to file: logging.error(f"Error: {e}")
```

### **B. Inspecting Variables**
Use `print()` or debugger tools to check variable states:
```python
def buggy_function(x):
    print(f"Input x: {x}")  # Debugging print
    result = x * 2  # Hypothetical bug
    print(f"Result: {result}")
    return result
```

### **C. Stack Traces**
Analyze tracebacks to identify error origins:
```python
Traceback (most recent call last):
  File "example.py", line 10, in <module>
    divide(10, 0)
  File "example.py", line 5, in divide
    return a / b
ZeroDivisionError: division by zero
```

---

## **4. Best Practices**
### **Testing**
1. **Test Coverage**: Aim for high coverage (use `coverage.py`).
2. **Isolate Tests**: Ensure tests don’t depend on external systems (use mocks).
3. **Test Naming**: Use descriptive names like `test_add_negative_numbers`.
4. **CI/CD Integration**: Automate tests with GitHub Actions, GitLab CI, etc.

### **Debugging**
1. **Reproduce the Issue**: Identify consistent steps to trigger the bug.
2. **Simplify the Problem**: Reduce code to a minimal reproducible example.
3. **Check Edge Cases**: Test boundary conditions (e.g., empty lists, zero values).
4. **Use Version Control**: Isolate bugs by checking out earlier commits.

---

## **5. Tools & Libraries**
| Tool                 | Purpose                          |
|----------------------|----------------------------------|
| `unittest`           | Built-in testing framework       |
| `pytest`             | Simplified testing with plugins  |
| `pdb`                | Command-line debugger            |
| `logging`            | Track program execution          |
| `coverage.py`        | Measure test coverage            |
| `unittest.mock`      | Mock dependencies                |

---

## **6. Example Workflow**
### **Step 1: Write a Failing Test**
```python
def test_divide():
    assert divide(10, 2) == 5  # Passes
    assert divide(10, 0) == 0  # Fails (ZeroDivisionError)
```

### **Step 2: Debug the Code**
```python
def divide(a, b):
    if b == 0:
        return 0  # Handle edge case
    return a / b
```

### **Step 3: Refactor and Retest**
```bash
pytest test_math.py -v  # Verify fixes
```
