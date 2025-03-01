### **1. `map(func, iterable)`  
Applies a function to all items in an iterable and returns an iterator.

```python
# Example: Square numbers
def square(x):
    return x * x

numbers = [1, 2, 3, 4, 5]
squared = list(map(square, numbers))  # Convert iterator to list
print(squared)  # Output: [1, 4, 9, 16, 25]

# With lambda
doubled = list(map(lambda x: x*2, numbers))
print(doubled)  # Output: [2, 4, 6, 8, 10]
```

---

### **2. `zip(*iterables)`**  
Combines multiple iterables into tuples. Stops at the shortest iterable.

```python
# Example: Pair names and surnames
names = ["John", "Charles", "Mike"]
surnames = ["Jenny", "Christy", "Monica"]

zipped = list(zip(names, surnames))
print(zipped)  # Output: [('John', 'Jenny'), ('Charles', 'Christy'), ('Mike', 'Monica')]

# Unzipping
unzipped_names, unzipped_surnames = zip(*zipped)
print(unzipped_names)  # Output: ('John', 'Charles', 'Mike')
```

---

### **3. `any(iterable)`**  
Returns `True` if **any** element is truthy. Returns `False` for empty iterables.

```python
# Example: Check for truthy values
my_list = [0, 1, False, True, ""]
print(any(my_list))  # Output: True

# All falsy values
print(any([0, "", False]))  # Output: False
```

---

### **4. `enumerate(iterable)`**  
Adds a counter to an iterable (index-value pairs).

```python
# Example: Track indices
my_list = ['a', 'b', 'c']
print(list(enumerate(my_list)))  # Output: [(0, 'a'), (1, 'b'), (2, 'c')]

# With start index
print(list(enumerate(my_list, start=1)))  # Output: [(1, 'a'), (2, 'b'), (3, 'c')]

# Practical use in loops
for idx, val in enumerate(['apple', 'banana']):
    print(f"Index {idx}: {val}")
```

---

### **5. `filter(func, iterable)`**  
Creates an iterator of elements where `func` returns `True`.

```python
# Example: Filter even numbers
def is_even(x):
    return x % 2 == 0

numbers = [1, 2, 3, 4, 5]
evens = list(filter(is_even, numbers))
print(evens)  # Output: [2, 4]

# With lambda
odds = list(filter(lambda x: x%2 != 0, numbers))
print(odds)  # Output: [1, 3, 5]
```

---

### **6. `bisect` Module**  
For maintaining sorted lists efficiently.

#### **A. Finding Positions**
```python
import bisect

# Find insertion point
a = [1, 2, 4]
pos = bisect.bisect(a, 3)  # Returns index 2 (right side if duplicates)
print(pos)  # Output: 2

# With duplicates
a = [1, 2, 2, 4]
print(bisect.bisect_left(a, 2))   # Output: 1 (first valid position)
print(bisect.bisect_right(a, 2))  # Output: 3 (after last 2)
```

#### **B. Inserting Elements**
```python
# Insert while maintaining order
a = [1, 2, 4]
bisect.insort(a, 3)
print(a)  # Output: [1, 2, 3, 4]

# Insert-left example
a = [1, 2, 2, 4]
bisect.insort_left(a, 2)  # Insert at first valid position
print(a)  # Output: [1, 2, 2, 2, 4]
```

---

### **Key Takeaways**
| Function/Module       | Use Case                                                                 |
|-----------------------|--------------------------------------------------------------------------|
| `map()`               | Apply transformations to all elements in an iterable                     |
| `zip()`               | Combine multiple iterables into tuples                                   |
| `any()`               | Check for at least one truthy value in a collection                      |
| `enumerate()`         | Get index-value pairs during iteration                                   |
| `filter()`            | Extract elements that satisfy a condition                                |
| `bisect`              | Efficiently manage sorted lists (search/insert)                          |
