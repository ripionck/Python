## Python operators with examples:

---

## **1. Arithmetic Operators**
Used for mathematical operations.

| Operator | Name           | Example     | Result  |
|----------|----------------|-------------|---------|
| `+`      | Addition       | `5 + 3`     | `8`     |
| `-`      | Subtraction    | `10 - 4`    | `6`     |
| `*`      | Multiplication | `3 * 4`     | `12`    |
| `/`      | Division       | `10 / 3`    | `3.333` |
| `%`      | Modulus        | `10 % 3`    | `1`     |
| `**`     | Exponentiation | `2 ** 3`    | `8`     |
| `//`     | Floor Division | `10 // 3`   | `3`     |

```python
print(5 % 3)   # Output: 2 (remainder)
print(2 ** 4)  # Output: 16
```

---

## **2. Comparison Operators**
Compare values and return `True` or `False`.

| Operator | Name                  | Example     | Result  |
|----------|-----------------------|-------------|---------|
| `==`     | Equal                 | `5 == 5`    | `True`  |
| `!=`     | Not Equal             | `5 != 3`    | `True`  |
| `>`      | Greater Than          | `10 > 5`    | `True`  |
| `<`      | Less Than             | `10 < 5`    | `False` |
| `>=`     | Greater Than or Equal | `10 >= 10`  | `True`  |
| `<=`     | Less Than or Equal    | `5 <= 3`    | `False` |

```python
a, b = 10, 5
print(a >= b)  # Output: True
```

---

## **3. Logical Operators**
Combine conditional statements.

| Operator | Description                     | Example                     | Result  |
|----------|---------------------------------|-----------------------------|---------|
| `and`    | True if **both** are true       | `(5 > 3) and (2 < 4)`       | `True`  |
| `or`     | True if **at least one** is true| `(5 > 3) or (5 < 2)`        | `True`  |
| `not`    | Inverts the result              | `not (5 == 5)`              | `False` |

```python
x = 7
print((x > 5) and (x < 10))  # Output: True
```

---

## **4. Assignment Operators**
Assign values to variables.

| Operator | Example    | Equivalent To |
|----------|------------|---------------|
| `=`      | `x = 5`    | `x = 5`       |
| `+=`     | `x += 3`   | `x = x + 3`   |
| `-=`     | `x -= 2`   | `x = x - 2`   |
| `*=`     | `x *= 4`   | `x = x * 4`   |
| `/=`     | `x /= 2`   | `x = x / 2`   |
| `%=`     | `x %= 3`   | `x = x % 3`   |

```python
x = 10
x += 5  # x becomes 15
```

---

## **5. Bitwise Operators**
Operate on binary representations of integers.

| Operator | Name         | Example     | Result (Binary) |
|----------|--------------|-------------|-----------------|
| `&`      | AND          | `5 & 3`     | `0101 & 0011 = 0001` (1) |
| `\|`     | OR           | `5 \| 3`    | `0101 \| 0011 = 0111` (7) |
| `^`      | XOR          | `5 ^ 3`     | `0101 ^ 0011 = 0110` (6) |
| `~`      | NOT          | `~5`        | Inverts bits (result: `-6`) |
| `<<`     | Left Shift   | `5 << 1`    | `0101 → 1010` (10) |
| `>>`     | Right Shift  | `5 >> 1`    | `0101 → 0010` (2) |

```python
print(5 & 3)   # Output: 1
print(5 << 1)  # Output: 10
```

---

## **6. Membership Operators**
Check if a value exists in a sequence (`list`, `str`, `tuple`, etc.).

| Operator | Description                   | Example                 | Result  |
|----------|-------------------------------|-------------------------|---------|
| `in`     | True if value exists          | `"a" in ["a", "b"]`     | `True`  |
| `not in` | True if value does NOT exist  | `"z" not in "hello"`    | `True`  |

```python
fruits = ["apple", "banana"]
print("apple" in fruits)  # Output: True
```

---

## **7. Identity Operators**
Check if two variables refer to the **same object**.

| Operator | Description                   | Example           | Result  |
|----------|-------------------------------|-------------------|---------|
| `is`     | True if **same object**       | `x is y`          | Depends |
| `is not` | True if **different objects** | `x is not y`      | Depends |

```python
a = [1, 2]
b = a       # b references the same object as a
c = [1, 2]  # c is a new object

print(a is b)  # Output: True
print(a is c)  # Output: False (same value, different object)
```

---

## **Key Notes**
1. **Operator Precedence**: 
   - Parentheses `()` have the highest priority.
   - Followed by `**`, then `*`, `/`, `%`, `//`, then `+`, `-`.
   - Logical operators (`not`, `and`, `or`) have lower precedence.

2. **Short-Circuit Evaluation**:
   - For `and`: Stops if the first condition is `False`.
   - For `or`: Stops if the first condition is `True`.

3. **Use Cases**:
   - Use `is` to compare objects (e.g., `x is None`).
   - Use `==` to compare values.
