## **1. If-Else Statements**
Conditional execution based on boolean expressions.

### **Syntax:**
```python
if condition1:
    # code block if condition1 is True
elif condition2:
    # code block if condition2 is True
else:
    # code block if all conditions are False
```

### **Example:**
```python
age = 18

if age < 13:
    print("Child")
elif 13 <= age < 18:
    print("Teen")
else:
    print("Adult")  # Output: Adult
```

---

## **2. Loops**
### **A. `for` Loops**
Iterate over a sequence (list, string, range, etc.).

**Example:**
```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(fruit)
# Output:
# apple
# banana
# cherry

# Loop with range()
for i in range(3):  # 0, 1, 2
    print(i)
```

### **B. `while` Loops**
Execute as long as a condition is `True`.

**Example:**
```python
count = 0

while count < 3:
    print(count)  # Output: 0, 1, 2
    count += 1
```

### **C. Nested Loops**
A loop inside another loop.

**Example:**
```python
for i in range(2):      # Outer loop
    for j in range(3):  # Inner loop
        print(i, j)
# Output:
# 0 0
# 0 1
# 0 2
# 1 0
# 1 1
# 1 2
```

---

## **3. Loop Control Statements**
### **A. `break`**
Exit the loop immediately.

**Example:**
```python
for num in [1, 2, 3, 4, 5]:
    if num == 3:
        break  # Exit loop when num is 3
    print(num)
# Output: 1 2
```

### **B. `continue`**
Skip the rest of the current iteration and proceed to the next one.

**Example:**
```python
for num in range(5):
    if num == 2:
        continue  # Skip number 2
    print(num)
# Output: 0 1 3 4
```

### **C. `pass`**
A placeholder for empty code blocks (does nothing).

**Example:**
```python
for num in [1, 2, 3]:
    pass  # No action, but avoids syntax errors

# Commonly used in empty functions/classes
def my_function():
    pass  # To be implemented later
```

---

## **4. Key Differences**

| Statement | Purpose                                                                 |
|-----------|-------------------------------------------------------------------------|
| `break`   | Terminates the loop entirely.                                          |
| `continue`| Skips to the next iteration of the loop.                               |
| `pass`    | Acts as a placeholder (no operation).                                  |

---

## **5. Practical Examples**
### **Example 1: Prime Check**
```python
num = 7
is_prime = True

for i in range(2, num):
    if num % i == 0:
        is_prime = False
        break  # Exit early if divisor found

print(is_prime)  # Output: True
```

### **Example 2: Filter Odd Numbers**
```python
numbers = [1, 2, 3, 4, 5]
odds = []

for num in numbers:
    if num % 2 == 0:
        continue  # Skip even numbers
    odds.append(num)

print(odds)  # Output: [1, 3, 5]
```

---

## **6. Common Pitfalls**
- **Infinite `while` Loops**: Ensure the loop condition eventually becomes `False`.
  ```python
  # Bad Example (Infinite Loop)
  # while True:
  #     print("Looping forever!")
  ```

- **Misusing `pass` vs `continue`**:
  - `pass` is a placeholder (no action).
  - `continue` actively skips to the next iteration.

---

## **7. Advanced: `else` with Loops**
- The `else` block executes **only if the loop completes normally** (not terminated by `break`).

**Example:**
```python
for num in [2, 4, 6]:
    if num % 2 != 0:
        break
else:
    print("All numbers are even")  # Output: All numbers are even
```

---

## **Summary**
- Use **`if-elif-else`** for conditional branching.
- **`for`** and **`while`** loops handle repetitive tasks.
- **`break`**, **`continue`**, and **`pass`** provide fine-grained control over loop execution.
