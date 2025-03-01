## **1. What is a Heap?**
A **heap** is a specialized tree-based data structure where:
- **Min-Heap**: Each parent node ≤ its children (smallest element at root).  
- **Max-Heap**: Each parent node ≥ its children (largest element at root).  

**`heapq`** in Python provides functions to create and manipulate **min-heaps** (for max-heaps, invert values).

---

## **2. Key Features**
- **Efficiency**: Insertion and extraction in `O(log n)` time.  
- **In-Place Operations**: Modifies lists directly (no separate heap class).  
- **Priority Queues**: Ideal for scheduling tasks by priority.  

---

## **3. Importing the Module**
```python
import heapq
```

---

## **4. Core Operations**

### **A. Create a Heap**
Convert a list into a heap using `heapify()`:
```python
data = [5, 3, 8, 1, 4]
heapq.heapify(data)  # Modifies list in-place → [1, 3, 8, 5, 4]
```

### **B. Add Elements**
Push an element while maintaining the heap property:
```python
heapq.heappush(data, 2)  # Heap becomes [1, 3, 2, 5, 4, 8]
```

### **C. Remove Elements**
Pop the **smallest element** (root):
```python
smallest = heapq.heappop(data)  # smallest = 1, heap → [2, 3, 8, 5, 4]
```

### **D. Push + Pop in One Step**
Efficiently combine `heappush()` and `heappop()`:
```python
val = heapq.heappushpop(data, 0)  # Push 0, pop smallest → val=0
```

### **E. Replace Smallest Element**
Pop the smallest element first, then push a new value:
```python
val = heapq.heapreplace(data, 9)  # Pop 2, add 9 → val=2
```

---

## **5. Advanced Operations**

### **A. Find N Largest/Smallest Elements**
```python
nums = [5, 3, 8, 1, 4]
print(heapq.nlargest(3, nums))   # [8, 5, 4]
print(heapq.nsmallest(2, nums))  # [1, 3]
```

### **B. Merge Sorted Sequences**
Efficiently merge pre-sorted iterables:
```python
list1 = [1, 3, 5]
list2 = [2, 4, 6]
merged = heapq.merge(list1, list2)  # Iterator → [1, 2, 3, 4, 5, 6]
```

### **C. Max-Heap Workaround**
Invert values to simulate a max-heap:
```python
max_heap = []
for num in [5, 3, 8]:
    heapq.heappush(max_heap, -num)  # Store -8, -5, -3

largest = -heapq.heappop(max_heap)  # 8
```

---

## **6. Key Functions Summary**

| Function                  | Description                                      | Time Complexity |
|---------------------------|--------------------------------------------------|-----------------|
| `heapq.heapify(list)`     | Converts list into a heap in-place.              | `O(n)`          |
| `heapq.heappush(heap, x)` | Adds `x` to the heap.                            | `O(log n)`      |
| `heapq.heappop(heap)`     | Removes and returns the smallest element.        | `O(log n)`      |
| `heapq.heappushpop()`     | Pushes `x` then pops smallest element.           | `O(log n)`      |
| `heapq.heapreplace()`     | Pops smallest element then pushes `x`.           | `O(log n)`      |
| `heapq.nlargest(k, iter)` | Returns `k` largest elements from `iter`.        | `O(n + k log n)`|
| `heapq.nsmallest(k, iter)`| Returns `k` smallest elements from `iter`.       | `O(n + k log n)`|
| `heapq.merge(*iterables)` | Merges sorted inputs into a single iterator.     | `O(n)`          |

---

## **7. Practical Examples**

### **A. Priority Queue**
```python
tasks = []
heapq.heappush(tasks, (2, "Low priority task"))
heapq.heappush(tasks, (1, "High priority task"))

while tasks:
    priority, task = heapq.heappop(tasks)
    print(f"Do: {task}")
```

### **B. K Closest Points to Origin**
```python
points = [(1, 2), (3, 4), (5, 6), (2, 1)]
k = 2

# Calculate squared distance (avoid sqrt for efficiency)
def distance(point):
    return point[0]**2 + point[1]**2

closest = heapq.nsmallest(k, points, key=distance)
print(closest)  # [(1, 2), (2, 1)]
```

---

## **8. Common Pitfalls**
- **Direct List Manipulation**: Avoid modifying the heap list directly (use `heapq` functions).  
- **Max-Heap Limitations**: No native support (workaround by inverting values).  
- **Empty Heap Errors**: Check `if heap:` before calling `heappop()`.  

---

## **9. Use Cases**
- **Real-Time Scheduling**: Process tasks by priority.  
- **Merge K Sorted Lists**: Efficiently using `heapq.merge()`.  
- **Top-K Elements**: Find largest/smallest elements in a stream.  
