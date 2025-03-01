## **1. Opening Files**
Use the `open()` function to work with files. Always use a **context manager** (`with` statement) for automatic cleanup.

### **Modes**:
- `'r'`: Read (default mode).
- `'w'`: Write (overwrites existing file or creates a new one).
- `'a'`: Append (adds to the end of an existing file).
- `'b'`: Binary mode (e.g., `'rb'` or `'wb'` for images).

```python
# Open a file for reading
with open("example.txt", "r") as file:
    content = file.read()
```

---

## **2. Reading Files**
### **Read Entire File**:
```python
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```

### **Read Line by Line**:
```python
with open("example.txt", "r") as file:
    for line in file:
        print(line.strip())  # Remove newline characters
```

### **Read Lines into a List**:
```python
with open("example.txt", "r") as file:
    lines = file.readlines()  # Returns a list of lines
```

### **Read a Specific Number of Characters**:
```python
with open("example.txt", "r") as file:
    chunk = file.read(100)  # Read first 100 characters
```

---

## **3. Writing Files**
### **Write to a New File**:
```python
with open("new_file.txt", "w") as file:
    file.write("Hello, World!\n")
    file.write("This is a new line.")
```

### **Append to an Existing File**:
```python
with open("existing.txt", "a") as file:
    file.write("\nAppended text.")
```

---

## **4. Managing Files**
### **Check if a File Exists**:
```python
import os

if os.path.exists("example.txt"):
    print("File exists!")
```

### **Delete a File**:
```python
import os

os.remove("file_to_delete.txt")
```

### **Rename/Move a File**:
```python
import os

os.rename("old_name.txt", "new_name.txt")
```

### **Copy a File**:
```python
import shutil

shutil.copy("source.txt", "destination.txt")
```

---

## **5. Working with Binary Files**
```python
# Read binary file (e.g., image)
with open("image.jpg", "rb") as file:
    data = file.read()

# Write binary file
with open("copy.jpg", "wb") as file:
    file.write(data)
```

---

## **6. File Handling Best Practices**
1. **Use Context Managers**: Ensures files are closed properly.
2. **Handle Exceptions**:
    ```python
    try:
        with open("missing.txt", "r") as file:
            print(file.read())
    except FileNotFoundError:
        print("File not found!")
    except PermissionError:
        print("Permission denied!")
    ```
3. **Specify Encoding** (for text files):
    ```python
    with open("example.txt", "r", encoding="utf-8") as file:
        content = file.read()
    ```

---

## **7. Common File Operations**
### **Read CSV Files**:
```python
import csv

with open("data.csv", "r") as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
```

### **Write JSON Files**:
```python
import json

data = {"name": "Alice", "age": 30}
with open("data.json", "w") as file:
    json.dump(data, file)
```

### **Read JSON Files**:
```python
with open("data.json", "r") as file:
    data = json.load(file)
    print(data["name"])  # Output: Alice
```

---

## **8. Summary Table**

| Operation          | Method/Module           | Example                                  |
|---------------------|-------------------------|------------------------------------------|
| **Open/Read**       | `open()`, `read()`      | `with open("file.txt", "r") as f: ...`   |
| **Write/Append**    | `open()`, `write()`     | `with open("file.txt", "w") as f: ...`   |
| **Check Existence** | `os.path.exists()`      | `os.path.exists("file.txt")`             |
| **Delete File**     | `os.remove()`           | `os.remove("file.txt")`                  |
| **Copy File**       | `shutil.copy()`         | `shutil.copy("src.txt", "dest.txt")`     |
