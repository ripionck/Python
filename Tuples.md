## **1. What is a Tuple?**
A **tuple** is an ordered, **immutable** (unchangeable) collection of elements enclosed in parentheses `()`.  
- Can hold items of different data types.  
- Once created, elements cannot be added, removed, or modified.  
- Often used for fixed data (e.g., coordinates, database records).  

**Example:**
```python
my_tuple = (1, "apple", True, 3.14)  # Mixed data types
```

---

## **2. Tuple Creation**
```python
# Empty tuple
empty_tuple = ()

# Single-element tuple (requires a trailing comma)
single_item = ("hello",)  # Not ("hello")

# Multiple elements
colors = ("red", "green", "blue")
numbers = tuple([1, 2, 3])  # Convert from a list
```

---

## **3. Basic Operations**

### **A. Indexing**
- Access elements using their position (zero-based).  
- Negative indexing starts from the end (`-1` is last item).  

```python
fruits = ("apple", "banana", "cherry")
print(fruits[0])   # Output: "apple"
print(fruits[-1])  # Output: "cherry"
```

### **B. Slicing**
Extract subtuples using `[start:end:step]`.  
```python
numbers = (0, 1, 2, 3, 4, 5)
print(numbers[1:4])    # (1, 2, 3) (end index excluded)
print(numbers[::2])    # (0, 2, 4) (step of 2)
print(numbers[::-1])   # (5, 4, 3, 2, 1, 0) (reverse)
```

### **C. Concatenation**
Combine tuples with `+`.  
```python
tuple1 = (1, 2)
tuple2 = (3, 4)
combined = tuple1 + tuple2  # (1, 2, 3, 4)
```

### **D. Repetition**
Repeat elements with `*`.  
```python
repeated = ("a",) * 3  # ("a", "a", "a")
```

### **E. Membership**
Check existence with `in`/`not in`.  
```python
print("apple" in fruits)  # True
```

---

## **4. Tuple Methods**
Since tuples are immutable, they have only two built-in methods:

| Method    | Description                          | Example                          |
|-----------|--------------------------------------|----------------------------------|
| `count()` | Returns the number of occurrences    | `(1, 2, 1).count(1) → 2`         |
| `index()` | Returns the index of the first match | `fruits.index("banana") → 1`      |

---

## **5. Immutability**
- **Cannot modify elements** after creation:  
  ```python
  fruits = ("apple", "banana", "cherry")
  # fruits[1] = "mango"  # Error: 'tuple' object does not support item assignment
  ```
- **Workaround**: Convert to a list, modify, then convert back.  
  ```python
  temp_list = list(fruits)
  temp_list[1] = "mango"
  fruits = tuple(temp_list)
  ```

---

## **6. Use Cases**
### **A. Fixed Data**
```python
coordinates = (40.7128, -74.0060)  # Latitude, Longitude (immutable)
```

### **B. Dictionary Keys**
Tuples (unlike lists) can be used as keys because they are hashable.  
```python
locations = {(35.68, 139.69): "Tokyo", (48.85, 2.35): "Paris"}
```

### **C. Returning Multiple Values from Functions**
```python
def min_max(numbers):
    return min(numbers), max(numbers)

result = min_max([5, 2, 8])  # (2, 8)
```

---

## **7. Tuple Unpacking**
Assign tuple elements to variables in one line.  
```python
point = (3, 4)
x, y = point  # x=3, y=4

# Swap variables
a, b = 5, 10
a, b = b, a  # a=10, b=5
```

---

## **8. Nested Tuples**
Tuples can contain other tuples or mutable objects (like lists).  
```python
matrix = (
    (1, 2, 3),
    (4, 5, 6),
    (7, 8, 9)
)
print(matrix[1][2])  # Output: 6
```

---

## **9. Performance**
- **Faster** than lists for iteration and fixed data due to immutability.  
- **Memory-efficient**: Optimized by Python for static data.  

---

## **10. Common Pitfalls**
- **Forgetting the Comma**: `("apple")` is a string, not a tuple. Use `("apple",)`.  
- **Modifying Nested Mutable Objects**:  
  ```python
  mixed_tuple = (1, [2, 3])
  mixed_tuple[1].append(4)  # Valid: The list inside can be modified
  ```

---

## **11. Advanced Topics**
### **A. Extended Unpacking**
Use `*` to capture multiple elements.  
```python
numbers = (1, 2, 3, 4, 5)
first, *middle, last = numbers  # first=1, middle=[2,3,4], last=5
```

### **B. Named Tuples**
Create tuple subclasses with named fields (from `collections`).  
```python
from collections import namedtuple

Person = namedtuple("Person", ["name", "age"])
alice = Person("Alice", 30)
print(alice.name)  # Output: Alice
```

### **C. Zip Function**
Combine multiple iterables into tuples.  
```python
names = ["Alice", "Bob"]
ages = [25, 30]
combined = list(zip(names, ages))  # [('Alice', 25), ('Bob', 30)]
```

---

## **12. Summary Table**

| Feature               | Description                                  |
|-----------------------|----------------------------------------------|
| **Immutability**      | Elements cannot be modified after creation.  |
| **Order**             | Elements maintain insertion order.           |
| **Duplicates**        | Allows duplicate values.                     |
| **Heterogeneous**     | Can store different data types.              |
| **Hashable**          | Can be used as dictionary keys.              |

---

**Example: Practical Use Case**  
```python
# RGB color codes (immutable)
red = (255, 0, 0)
green = (0, 255, 0)
blue = (0, 0, 255)

def blend_colors(color1, color2):
    return (
        (color1[0] + color2[0]) // 2,
        (color1[1] + color2[1]) // 2,
        (color1[2] + color2[2]) // 2
    )

print(blend_colors(red, blue))  # (127, 0, 127)
```
