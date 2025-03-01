## **1. RegEx Basics**
Regular expressions are sequences of characters defining search patterns. Use the `re` module in Python.

```python
import re
```

---

## **2. Common RegEx Functions**

| Function          | Description                                      | Example                          |
|-------------------|--------------------------------------------------|----------------------------------|
| `re.search()`     | Returns first match anywhere in the string       | `re.search(r'pattern', text)`    |
| `re.match()`      | Checks for a match only at the **beginning**     | `re.match(r'pattern', text)`     |
| `re.findall()`    | Returns all non-overlapping matches as a list    | `re.findall(r'pattern', text)`   |
| `re.finditer()`   | Returns iterator of match objects                | `re.finditer(r'pattern', text)`  |
| `re.sub()`        | Replaces matches with a string                   | `re.sub(r'pattern', 'new', text)`|
| `re.split()`      | Splits string by matches                         | `re.split(r'pattern', text)`     |

---

## **3. RegEx Syntax Cheatsheet**

| Pattern   | Matches                                 | Example                     |
|-----------|-----------------------------------------|-----------------------------|
| `.`       | Any character (except newline)          | `a.c` → "abc", "a5c"        |
| `\d`      | Digit (0-9)                             | `\d\d` → "42"               |
| `\D`      | Non-digit                               | `\D` → "a", "%"             |
| `\w`      | Word character (a-z, A-Z, 0-9, _)      | `\w+` → "hello_123"         |
| `\W`      | Non-word character                      | `\W` → "!", " "             |
| `\s`      | Whitespace (space, tab, newline)        | `\s+` → "   "               |
| `\S`      | Non-whitespace                          | `\S` → "a", "5"             |
| `^`       | Start of string                         | `^Hello` → "Hello" at start |
| `$`       | End of string                           | `world$` → "world" at end   |
| `*`       | 0 or more repetitions                   | `a*` → "", "a", "aaaa"      |
| `+`       | 1 or more repetitions                   | `a+` → "a", "aaaa"          |
| `?`       | 0 or 1 repetition (optional)            | `colou?r` → "color", "colour"|
| `{n}`     | Exactly `n` repetitions                 | `\d{3}` → "123"             |
| `{n,m}`   | Between `n` and `m` repetitions         | `\d{2,4}` → "12", "1234"    |
| `[abc]`   | Any of a, b, or c                       | `[aeiou]` → vowels           |
| `[^abc]`  | Not a, b, or c                          | `[^0-9]` → non-digits        |
| `|`       | OR operator                             | `cat|dog` → "cat" or "dog"   |
| `()`      | Capture group                           | `(abc)+` → "abcabc"          |

---

## **4. Common Use Cases**

### **A. Validate Email Address**
```python
email_pattern = r'^[\w\.-]+@[\w\.-]+\.\w+$'
email = "user@example.com"

if re.match(email_pattern, email):
    print("Valid email!")
```

### **B. Extract Phone Numbers**
```python
text = "Call me at 415-555-1011 or 555-1234"
phone_pattern = r'\d{3}-\d{3}-\d{4}|\d{3}-\d{4}'

numbers = re.findall(phone_pattern, text)
print(numbers)  # Output: ['415-555-1011', '555-1234']
```

### **C. Replace Dates**
```python
text = "Today is 2023-08-20."
new_text = re.sub(r'\d{4}-\d{2}-\d{2}', "YYYY-MM-DD", text)
print(new_text)  # Output: "Today is YYYY-MM-DD."
```

---

## **5. Groups & Capturing**
Use parentheses `()` to capture parts of a match.

```python
text = "John: 30, Alice: 25"
pattern = r'(\w+): (\d+)'

matches = re.findall(pattern, text)
print(matches)  # Output: [('John', '30'), ('Alice', '25')]

# Iterate with groups
for match in re.finditer(pattern, text):
    name, age = match.groups()
    print(f"{name} is {age} years old.")
```

---

## **6. Flags**
Modify regex behavior with flags:

| Flag              | Description                          | Example                          |
|-------------------|--------------------------------------|----------------------------------|
| `re.IGNORECASE`   | Case-insensitive matching            | `re.findall(r'hello', text, re.I)`|
| `re.MULTILINE`    | `^` and `$` match start/end of lines | `re.match(r'^start', text, re.M)`|
| `re.DOTALL`       | `.` matches newlines                 | `re.search(r'.+', text, re.S)`   |

---

## **7. Greedy vs. Non-Greedy**
- **Greedy** (`*`, `+`, `{}`): Matches as much as possible.
- **Non-Greedy** (`*?`, `+?`, `{}?`): Matches as little as possible.

```python
text = "<div>content</div>"

# Greedy match
print(re.findall(r'<.*>', text))       # Output: ['<div>content</div>']

# Non-greedy match
print(re.findall(r'<.*?>', text))      # Output: ['<div>', '</div>']
```

---

## **8. Common Patterns**
| Purpose           | Pattern                               |
|-------------------|---------------------------------------|
| **URL**           | `https?://(?:www\.)?\w+\.\w+`         |
| **IPv4 Address**  | `\b(?:\d{1,3}\.){3}\d{1,3}\b`        |
| **Hex Color**     | `#([A-Fa-f0-9]{6}|[A-Fa-f0-9]{3})\b` |
| **HTML Tags**     | `</?[\w\s]*>|<.+?>`                   |

---

## **9. Best Practices**
1. **Use Raw Strings**: Prefix patterns with `r` to avoid escaping issues.
   ```python
   re.search(r'\d+', text)  # Correct
   re.search('\\d+', text)  # Avoid (messy)
   ```
2. **Compile Repeated Patterns**:
   ```python
   pattern = re.compile(r'\d{3}-\d{3}-\d{4}')
   matches = pattern.findall(text)
   ```
3. **Test Patterns**: Use tools like [regex101.com](https://regex101.com/) for debugging.

---

## **10. Summary Table**

| Concept              | Example Pattern             | Use Case                          |
|----------------------|-----------------------------|-----------------------------------|
| **Basic Matching**   | `r'hello'`                  | Find exact text                   |
| **Digits**           | `r'\d{3}'`                  | Match 3-digit numbers             |
| **Word Boundaries**  | `r'\bword\b'`               | Whole words only                  |
| **Capture Groups**   | `r'(\d{2})-(\d{2})'`        | Split date components             |
| **Non-Greedy**       | `r'<.*?>'`                  | Extract HTML tags                 |
