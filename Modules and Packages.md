## modules and packages

---

## **1. Modules**
A **module** is a single Python file (`*.py`) containing functions, classes, or variables that can be reused in other scripts.

### **Creating a Module**
1. Save your code in a `.py` file.  
   Example: `mymath.py`  
   ```python
   # mymath.py
   def add(a, b):
       return a + b

   def multiply(a, b):
       return a * b

   PI = 3.14159
   ```

### **Importing a Module**
```python
# Import the entire module
import mymath

print(mymath.add(2, 3))       # Output: 5
print(mymath.PI)              # Output: 3.14159

# Import specific items
from mymath import multiply
print(multiply(2, 3))         # Output: 6

# Import with an alias
import mymath as mm
print(mm.PI)                  # Output: 3.14159

# Import all names (not recommended)
from mymath import *
print(add(5, 2))              # Output: 7
```

---

## **2. Packages**
A **package** is a directory containing multiple modules and a special `__init__.py` file to indicate it’s a Python package.  
**Structure**:  
```
my_package/
├── __init__.py
├── module1.py
└── module2.py
```

### **Creating a Package**
1. Create a directory (e.g., `my_package`).  
2. Add an empty `__init__.py` file (can include initialization code).  
3. Add modules inside the directory.  

**Example**:  
```python
# my_package/module1.py
def greet(name):
    return f"Hello, {name}!"

# my_package/module2.py
def square(n):
    return n ** 2
```

---

## **3. Importing from Packages**
### **Absolute Imports**
```python
# Import a module from the package
import my_package.module1
print(my_package.module1.greet("Alice"))  # Output: Hello, Alice!

# Import specific functions
from my_package.module2 import square
print(square(5))                          # Output: 25

# Import with aliases
from my_package import module1 as m1
print(m1.greet("Bob"))                    # Output: Hello, Bob!
```

### **Relative Imports** (within a package)  
Use `.` to refer to modules in the same package.  
```python
# Inside my_package/module3.py
from .module1 import greet
from .module2 import square
```

---

## **4. The `__init__.py` File**
- Marks the directory as a Python package.  
- Can initialize package-level variables or control imports.  

**Example**:  
```python
# my_package/__init__.py
from .module1 import greet
from .module2 import square

__all__ = ['greet', 'square']  # Defines what 'from my_package import *' includes
```

---

## **5. Organizing Larger Projects**
For multi-level packages:  
```
project/
├── main.py
└── my_package/
    ├── __init__.py
    ├── utils/
    │   ├── __init__.py
    │   └── helpers.py
    └── core/
        ├── __init__.py
        └── calculations.py
```

**Importing from Subpackages**:  
```python
from my_package.utils.helpers import validate_email
```

---

## **6. Installing Packages Locally**
To make your package importable anywhere:  
1. Create a `setup.py` file:  
   ```python
   from setuptools import setup, find_packages

   setup(
       name="my_package",
       version="0.1",
       packages=find_packages(),
   )
   ```
2. Install in development mode:  
   ```bash
   pip install -e .
   ```

---

## **7. Key Best Practices**
1. **Avoid Circular Imports**: Module A imports Module B, and Module B imports Module A.  
2. **Use `if __name__ == "__main__"`**: Prevent code from executing on import.  
   ```python
   # mymath.py
   def add(a, b):
       return a + b

   if __name__ == "__main__":
       print(add(2, 3))  # Runs only when executed directly
   ```
3. **Organize Code Logically**: Group related functions/classes in modules.  
4. **Use Descriptive Names**: e.g., `data_loader.py`, `plot_utils.py`.

---

## **8. Common Import Errors & Fixes**
| Error                          | Solution                                  |
|--------------------------------|-------------------------------------------|
| `ModuleNotFoundError`          | Check file paths and `sys.path`.          |
| `ImportError`                  | Ensure the module/function exists.        |
| Circular Import                | Restructure code or use local imports.    |

---

## **9. Summary**
| Concept               | Description                                  | Example                          |
|-----------------------|----------------------------------------------|----------------------------------|
| **Module**            | Single `.py` file with reusable code.        | `import mymath`                  |
| **Package**           | Directory with modules + `__init__.py`.      | `from my_package import module1` |
| **Absolute Import**   | Full path from project root.                 | `import my_package.module1`      |
| **Relative Import**   | Relative to current module (using `.`).      | `from . import helpers`          |
