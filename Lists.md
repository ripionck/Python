## **1. What is a List?**
A **list** is an ordered, mutable collection of elements enclosed in square brackets `[]`.  
- Can hold items of different data types (int, str, bool, etc.).  
- Index starts at `0` (zero-based indexing).  

**Example:**
```python
my_list = [1, "apple", True, 3.14]  # Mixed data types
```

---

## **2. List Creation**
```python
# Empty list
empty_list = []

# List with elements
numbers = [10, 20, 30, 40]
fruits = ["apple", "banana", "cherry"]

# Using list constructor
chars = list("hello")  # ['h', 'e', 'l', 'l', 'o']
```

---

## **3. Basic Operations**

### **A. Indexing**
- Access elements using their position.  
- Negative indexing starts from the end (`-1` is last item).  

```python
fruits = ["apple", "banana", "cherry"]
print(fruits[0])   # Output: "apple"
print(fruits[-1])  # Output: "cherry"
```

### **B. Slicing**
Extract sublists using `[start:end:step]`.  
```python
numbers = [0, 1, 2, 3, 4, 5]
print(numbers[1:4])    # [1, 2, 3] (end index excluded)
print(numbers[::2])    # [0, 2, 4] (step of 2)
print(numbers[::-1])   # [5, 4, 3, 2, 1, 0] (reverse)
```

### **C. Adding Elements**
- **`append()`**: Add a single element to the end.  
- **`insert()`**: Insert at a specific index.  
- **`extend()`**: Add multiple elements (from another list).  

```python
fruits = ["apple", "banana"]
fruits.append("orange")      # ['apple', 'banana', 'orange']
fruits.insert(1, "mango")    # ['apple', 'mango', 'banana', 'orange']
fruits.extend(["grape", "kiwi"])  # Adds two elements
```

### **D. Modifying Elements**
```python
fruits = ["apple", "banana", "cherry"]
fruits[1] = "mango"  # ['apple', 'mango', 'cherry']
```

### **E. Removing Elements**
- **`remove()`**: Delete by value.  
- **`pop()`**: Remove by index (returns the removed item).  
- **`clear()`**: Empty the list.  
- **`del`**: Delete by index/slice.  

```python
fruits = ["apple", "banana", "cherry"]
fruits.remove("banana")  # ['apple', 'cherry']
popped = fruits.pop(0)   # popped = "apple", list: ['cherry']
fruits.clear()           # []
del fruits               # Deletes the entire list
```

---

## **4. List Comprehensions**
Create lists concisely using a single line.  
```python
# Squares of numbers 0-4
squares = [x**2 for x in range(5)]  # [0, 1, 4, 9, 16]

# Filter even numbers
evens = [x for x in range(10) if x % 2 == 0]  # [0, 2, 4, 6, 8]
```

---

## **5. Common List Methods**

| Method          | Description                                      | Example                              |
|-----------------|--------------------------------------------------|--------------------------------------|
| `len()`         | Returns the number of items                      | `len([1, 2, 3]) → 3`                |
| `sort()`        | Sorts the list in-place                          | `nums.sort()`                        |
| `reverse()`     | Reverses the list in-place                       | `nums.reverse()`                     |
| `copy()`        | Returns a shallow copy                           | `new_list = old_list.copy()`         |
| `count()`       | Counts occurrences of a value                   | `[1, 2, 1].count(1) → 2`             |
| `index()`       | Returns the index of the first occurrence        | `fruits.index("banana") → 1`         |
| `sum()`         | Sums all elements (numeric lists)                | `sum([1, 2, 3]) → 6`                |
| `min()`/`max()` | Finds the smallest/largest element              | `min([5, 2, 8]) → 2`                |

---

## **6. Nested Lists**
Lists can contain other lists (e.g., matrices).  
```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Access element
print(matrix[1][2])  # Output: 6
```

---

## **7. List Operations**

| Operation      | Description                          | Example                          |
|----------------|--------------------------------------|----------------------------------|
| Concatenation  | Combine lists with `+`               | `[1, 2] + [3, 4] → [1, 2, 3, 4]` |
| Repetition     | Repeat elements with `*`             | `["a"] * 3 → ["a", "a", "a"]`    |
| Membership     | Check existence with `in`/`not in`   | `"apple" in fruits → True`        |
| Equality       | Compare lists with `==`              | `[1, 2] == [1, 2] → True`        |

---

## **8. Performance Considerations**
- **Appending** (`append()`) is **O(1)** time complexity.  
- **Inserting** at the beginning is **O(n)** (slower for large lists).  
- Use `deque` from the `collections` module for efficient insertions/deletions at both ends.  

---

## **9. Common Pitfalls**
- **Shallow Copy**: `list2 = list1.copy()` vs `list2 = list1` (aliasing).  
- **Modifying During Iteration**: Avoid changing list size while looping.  
- **Mixed Data Types**: Sorting lists with mixed types raises errors.  

---

## **10. Advanced Topics**
### **A. List Comprehensions with Conditions**
```python
# Squares of even numbers only
squares = [x**2 for x in range(10) if x % 2 == 0]
```

### **B. Zipping Lists**
```python
names = ["Alice", "Bob"]
ages = [25, 30]
combined = list(zip(names, ages))  # [('Alice', 25), ('Bob', 30)]
```

### **C. Using Lists as Stacks/Queues**
```python
# Stack (LIFO)
stack = []
stack.append("a")  # Push
stack.pop()        # Pop

# Queue (FIFO - inefficient for large lists)
queue = []
queue.append("a")  # Enqueue
queue.pop(0)       # Dequeue
```

---

## **Summary Table**

| Feature               | Description                                  |
|-----------------------|----------------------------------------------|
| **Mutability**        | Elements can be modified after creation.     |
| **Order**             | Elements maintain insertion order.           |
| **Duplicates**        | Allows duplicate values.                     |
| **Heterogeneous**     | Can store different data types.              |
| **Dynamic Sizing**    | Automatically resizes as elements are added. |

---

**Example: Practical Use Case**  
```python
# Shopping list operations
shopping = ["milk", "bread"]

# Add items
shopping.append("eggs")
shopping.insert(1, "butter")

# Remove item
shopping.remove("bread")

# Check if empty
if not shopping:
    print("List is empty!")
else:
    print(f"Items to buy: {shopping}")
```
