## **1. What is a Deque?**
A **deque** (pronounced "deck") is a double-ended queue optimized for fast appends and pops from both ends.  
- **Key Features**:  
  - Thread-safe for appends/pops from both ends.  
  - More efficient than lists for front operations (O(1) time complexity).  
  - Supports a maximum length (`maxlen`) to automatically discard old elements.  

---

## **2. Importing and Initialization**
```python
from collections import deque

# Create an empty deque
dq = deque()

# Initialize with elements
dq = deque([1, 2, 3])  # deque([1, 2, 3])

# Set a maximum length (discards old elements when full)
dq = deque(maxlen=3)    # After appending 4 elements: [2, 3, 4]
```

---

## **3. Basic Operations**

### **A. Adding Elements**
| Method               | Description                          | Example                          |
|----------------------|--------------------------------------|----------------------------------|
| **`append(x)`**      | Add `x` to the right end.            | `dq.append(4) → [1, 2, 3, 4]`    |
| **`appendleft(x)`**  | Add `x` to the left end.             | `dq.appendleft(0) → [0, 1, 2, 3]`|
| **`extend(iter)`**   | Add multiple elements to the right.  | `dq.extend([4,5]) → [1,2,3,4,5]` |
| **`extendleft(iter)`**| Add multiple elements to the left (**in reverse order**). | `dq.extendleft([-1,0]) → [0, -1, 1, 2, 3]` |

---

### **B. Removing Elements**
| Method               | Description                          | Example                          |
|----------------------|--------------------------------------|----------------------------------|
| **`pop()`**          | Remove and return the rightmost element. | `dq.pop() → 3` (deque becomes `[1, 2]`) |
| **`popleft()`**      | Remove and return the leftmost element. | `dq.popleft() → 1` (deque becomes `[2, 3]`) |
| **`remove(x)`**      | Remove the first occurrence of `x`. | `dq.remove(2) → deque([1, 3])` |
| **`clear()`**        | Remove all elements.                 | `dq.clear() → deque()` |

---

### **C. Rotating Elements**
```python
# Rotate elements n steps to the right (positive n)
dq = deque([1, 2, 3, 4, 5])
dq.rotate(2)    # deque([4, 5, 1, 2, 3])

# Rotate elements n steps to the left (negative n)
dq.rotate(-1)   # deque([5, 1, 2, 3, 4])
```

---

### **D. Other Operations**
| Method/Property       | Description                          | Example                          |
|-----------------------|--------------------------------------|----------------------------------|
| **`len(dq)`**         | Number of elements.                  | `len(deque([1,2,3])) → 3`       |
| **`dq[i]`**           | Access element at index `i`.         | `dq[0] → 1`                     |
| **`count(x)`**        | Count occurrences of `x`.            | `dq.count(2) → 1`               |
| **`index(x)`**        | Find the first position of `x`.      | `dq.index(3) → 2`               |
| **`reverse()`**       | Reverse elements in place.           | `dq.reverse() → [3, 2, 1]`      |
| **`maxlen`**          | Return maximum length (or `None`).   | `dq.maxlen → 3` (if set)        |

---

## **4. Advanced Use Cases**

### **A. Sliding Window (Using `maxlen`)**
```python
# Keep only the last 3 elements
dq = deque(maxlen=3)
for i in range(5):
    dq.append(i)
    print(dq)

# Output:
# deque([0], maxlen=3)
# deque([0, 1], maxlen=3)
# deque([0, 1, 2], maxlen=3)
# deque([1, 2, 3], maxlen=3)
# deque([2, 3, 4], maxlen=3)
```

### **B. Breadth-First Search (BFS)**
```python
# Efficiently pop from the front
queue = deque(["root"])
while queue:
    node = queue.popleft()
    print(node)
    # Add child nodes to the end: queue.extend(children)
```

---

## **5. Performance Comparison**
| Operation       | Deque Time Complexity | List Time Complexity |
|-----------------|-----------------------|----------------------|
| Append/Pop (Right) | O(1)                 | O(1)                |
| Append/Pop (Left)  | O(1)                 | O(n)                |
| Insert/Delete (Middle) | O(n)             | O(n)                |

---

## **6. Summary Table**

| Feature               | Description                                  |
|-----------------------|----------------------------------------------|
| **Double-Ended**      | Fast adds/removes from both ends.            |
| **Thread-Safe**       | Safe for multithreaded appends/pops.         |
| **Fixed Size**        | Use `maxlen` to auto-discard old elements.   |
| **No Slicing**        | Cannot slice like lists (use indexing).      |

---

## **7. Practical Example**
```python
# Palindrome checker using deque
def is_palindrome(s):
    dq = deque(s.lower().replace(" ", ""))
    while len(dq) > 1:
        if dq.popleft() != dq.pop():
            return False
    return True

print(is_palindrome("racecar"))  # True
```
