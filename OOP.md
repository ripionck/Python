## **1. Classes & Objects**
### **Class Instantiation & `self`**
```python
class Dog:
    # Class Variable (shared across instances)
    species = "Canis familiaris"

    # Constructor (__init__ method)
    def __init__(self, name, age):
        # Instance Variables (data attributes)
        self.name = name
        self.age = age

    # Instance Method (self refers to the object)
    def description(self):
        return f"{self.name} is {self.age} years old"

    # __str__ for user-friendly string
    def __str__(self):
        return self.description()

    # __repr__ for unambiguous representation
    def __repr__(self):
        return f"Dog(name={self.name!r}, age={self.age!r})"

# Instantiate
buddy = Dog("Buddy", 5)
print(buddy)          # Uses __str__: "Buddy is 5 years old"
print(repr(buddy))    # Uses __repr__: Dog(name='Buddy', age=5)
```

### **UML Representation (Simplified)**
```
+------------------+
|      Dog         |
+------------------+
| - name: str      |
| - age: int       |
| + species: str   |
+------------------+
| + __init__()     |
| + description()  |
| + __str__()      |
| + __repr__()     |
+------------------+
```

---

## **2. Inheritance**
### **Base & Derived Classes**
```python
class Animal:  # Base class
    def __init__(self, name):
        self.name = name

    def speak(self):
        raise NotImplementedError("Subclass must implement abstract method")

class Cat(Animal):  # Derived class
    def speak(self):  # Override method
        return "Meow!"

    def climb(self):  # Extend with new method
        return f"{self.name} climbs a tree"

# Abstract Base Class (ABC)
from abc import ABC, abstractmethod
class Bird(ABC):
    @abstractmethod
    def fly(self):
        pass

class Sparrow(Bird):
    def fly(self):  # Must implement abstract method
        return "Flying high!"

# Usage
kitty = Cat("Whiskers")
print(kitty.speak())  # Meow!
print(kitty.climb())  # Whiskers climbs a tree
```

---

## **3. OOP in Dynamic Language**
### **Dynamic Typing & Static Checks**
```python
def add(a, b):
    return a + b

add(2, 3)       # 5 (int)
add("Hello", " World")  # "Hello World" (str)

# Static Type Checking (via type hints)
def greet(name: str) -> str:
    return f"Hello, {name}"

# Simulate Overloading (using default args)
class Calculator:
    def add(self, a, b, c=0):
        return a + b + c

calc = Calculator()
calc.add(2, 3)    # 5
calc.add(1, 2, 3) # 6
```

---

## **4. Polymorphism**
### **Open-Closed Principle & Duck Typing**
```python
class Rectangle:
    def draw(self):
        print("Drawing a rectangle")

class Circle:
    def draw(self):
        print("Drawing a circle")

def render_shape(shape):  # Accepts any object with draw()
    shape.draw()

render_shape(Rectangle())  # Drawing a rectangle
render_shape(Circle())     # Drawing a circle
```

---

## **5. Encapsulation**
### **Attribute Visibility & Properties**
```python
class BankAccount:
    def __init__(self, balance):
        self._balance = balance  # Protected (convention)
        self.__secret = 123       # Private (name mangling)

    @property
    def balance(self):
        return self._balance

    @balance.setter
    def balance(self, value):
        if value < 0:
            raise ValueError("Balance cannot be negative")
        self._balance = value

acc = BankAccount(100)
print(acc.balance)       # 100 (uses property)
acc.balance = 200        # Valid
# print(acc.__secret)    # Error: AttributeError (name mangled to _BankAccount__secret)
```

---

## **6. Abstraction**
### **Abstract Base Classes (ABCs)**
```python
from abc import ABC, abstractmethod

class Vehicle(ABC):
    @abstractmethod
    def start_engine(self):
        pass

class Car(Vehicle):
    def start_engine(self):
        return "Vroom!"

# vehicle = Vehicle()  # Error: Can't instantiate abstract class
car = Car()
print(car.start_engine())  # Vroom!
```

---

## **7. Classes in Python**
### **Class Variables & Methods**
```python
class MyClass:
    class_var = 10  # Class-level variable

    def __init__(self, instance_var):
        self.instance_var = instance_var  # Instance-level

    @classmethod
    def class_method(cls):  # Operates on class
        print(f"Class var: {cls.class_var}")

    @staticmethod
    def static_method():  # No cls/self
        print("Utility method")

# Access
MyClass.class_method()    # Class var: 10
MyClass.static_method()   # Utility method
```

---

## **Summary Table**

| Concept               | Python Feature                          | Example                          |
|-----------------------|-----------------------------------------|----------------------------------|
| **Class Instantiation** | `__init__` & `self`                   | `obj = MyClass(arg)`             |
| **Inheritance**       | `class Child(Parent):` & `super()`      | Override methods, `super().__init__()` |
| **Polymorphism**      | Duck typing & ABCs                     | Shared method names across classes |
| **Encapsulation**     | `_protected` & `__private` (name mangling) | Use `@property` for controlled access |
| **Abstraction**       | `abc.ABC` & `@abstractmethod`          | Force method implementation      |
| **Class Methods**     | `@classmethod` & `cls`                 | Modify class state               |
| **Static Methods**    | `@staticmethod`                        | Utility functions                |
