## Python String Methods Examples

A collection of Python string method examples demonstrating their usage and outputs.

### Table of Contents
- [Split Function](#split-function)
- [Convert String to List](#convert-string-to-list)
- [Count Function](#count-function)
- [isnumeric() Method](#isnumeric-method)
- [find() Method](#find-method)
- [isalnum() Method](#isalnum-method)
- [isalpha() Method](#isalpha-method)
- [strip() Method](#strip-method)
- [upper() Method](#upper-method)
- [lower() Method](#lower-method)
- [islower() Method](#islower-method)
- [isdigit() Method](#isdigit-method)
- [isupper() Method](#isupper-method)
- [replace() Method](#replace-method)
- [startswith() Method](#startswith-method)
- [endswith() Method](#endswith-method)
- [join() Method](#join-method)
- [title() Method](#title-method)
- [capitalize() Method](#capitalize-method)
- [swapcase() Method](#swapcase-method)
- [zfill() Method](#zfill-method)
- [partition() Method](#partition-method)
- [splitlines() Method](#splitlines-method)
- [expandtabs() Method](#expandtabs-method)

---

### Split Function
The `split()` method breaks up a string at the specified separator and returns a list of strings.

```python
text = 'Python is a fun programming language'
print(text.split(' '))
```
**Output:**
```
['Python', 'is', 'a', 'fun', 'programming', 'language']
```

---

### Convert String to List
Convert a string to a list using `list()`.

```python
s = "abcd"
s = list(s)
print(s)
```
**Output:**
```
['a', 'b', 'c', 'd']
```

---

### Count Function
The `count()` method returns the number of occurrences of a substring.

```python
message = 'python is popular programming language'
print('Number of occurrence of p:', message.count('p'))
```
**Output:**
```
Number of occurrence of p: 4
```

---

### isnumeric() Method
Check if all characters in a string are numeric.

```python
s = '1242323'
print(s.isnumeric())
```
**Output:**
```
True
```

---

### find() Method
Find the index of the first occurrence of a substring. Returns `-1` if not found.

```python
message = 'python is popular programming language'
print(message.find('fun'))
```
**Output:**
```
-1
```

---

### isalnum() Method
Check if all characters are alphanumeric (alphabets or numbers).

```python
name = "M3onica Gell22er "
print(name.isalnum())
```
**Output:**
```
False   # Contains spaces
```

---

### isalpha() Method
Check if all characters are alphabets.

```python
name = "Monica"
print(name.isalpha())
```
**Output:**
```
True
```

---

### strip() Method
Remove leading and trailing whitespace.

```python
string = "  Hello, World!  "
print(string.strip())
```
**Output:**
```
Hello, World!
```

---

### upper() Method
Convert all characters to uppercase.

```python
string = "  Hello, World!  "
print(string.upper())
```
**Output:**
```
  HELLO, WORLD!  
```

---

### lower() Method
Convert all characters to lowercase.

```python
string = "  Hello, World!  "
print(string.lower())
```
**Output:**
```
  hello, world!  
```

---

### islower() Method
Check if all cased characters are lowercase.

```python
string = "hello"
print(string.islower())
```
**Output:**
```
True
```

---

### isdigit() Method
Check if all characters are digits.

```python
num_str = "12345"
print(num_str.isdigit())
```
**Output:**
```
True
```

---

### isupper() Method
Check if all cased characters are uppercase.

```python
string = "HELLO"
print(string.isupper())
```
**Output:**
```
True
```

---

### replace() Method
Replace occurrences of a substring with another substring.

```python
text = "hello world"
new_text = text.replace("world", "Python")
print(new_text)
```
**Output:**
```
hello Python
```

---

### startswith() Method
Check if a string starts with a specific substring.

```python
text = "hello world"
print(text.startswith("hello"))
```
**Output:**
```
True
```

---

### endswith() Method
Check if a string ends with a specific substring.

```python
text = "hello world"
print(text.endswith("world"))
```
**Output:**
```
True
```

---

### join() Method
Join elements of a list into a single string.

```python
words = ["hello", "world"]
text = " ".join(words)
print(text)
```
**Output:**
```
hello world
```

---

### title() Method
Convert the first character of each word to uppercase.

```python
text = "hello world"
print(text.title())
```
**Output:**
```
Hello World
```

---

### capitalize() Method
Convert the first character to uppercase and the rest to lowercase.

```python
text = "hello world"
print(text.capitalize())
```
**Output:**
```
Hello world
```

---

### swapcase() Method
Swap the case of all characters.

```python
text = "hELLo wORLd"
print(text.swapcase())
```
**Output:**
```
HellO WorlD
```

---

### zfill() Method
Pad the string with leading zeros to a specified width.

```python
text = "42"
print(text.zfill(5))
```
**Output:**
```
00042
```

---

### partition() Method
Split the string at the first occurrence of a separator.

```python
text = "hello world"
print(text.partition(" "))
```
**Output:**
```
('hello', ' ', 'world')
```

---

### splitlines() Method
Split the string at line breaks.

```python
text = "hello\nworld"
print(text.splitlines())
```
**Output:**
```
['hello', 'world']
```

---

### expandtabs() Method
Replace tab characters with spaces.

```python
text = "hello\tworld"
print(text.expandtabs())
```
**Output:**
```
hello   world    # Replaces \t with 8 spaces by default
```
