## Object-Oriented Programming (OOP) concepts

---
## **1. Classes and Objects**
### **Definition**
- **Class**: A blueprint for creating objects (e.g., "Car").
- **Object**: An instance of a class (e.g., "Toyota Camry").
- **`self`**: Refers to the instance itself (access attributes/methods).
- **Data Attributes**: Variables bound to an object (e.g., `color`, `speed`).
- **Methods**: Functions defined within a class (e.g., `accelerate()`).

### **Code Example**
```python
class Car:
    # Class variable (shared by all instances)
    wheels = 4

    def __init__(self, make, model, color):
        # Instance variables
        self.make = make
        self.model = model
        self.color = color
        self.speed = 0

    # Instance method
    def accelerate(self, increment):
        self.speed += increment

    # String representation for users
    def __str__(self):
        return f"{self.color} {self.make} {self.model}"

    # Unambiguous representation for developers
    def __repr__(self):
        return f"Car(make={self.make}, model={self.model}, color={self.color})"

# Instantiation
my_car = Car("Toyota", "Camry", "Blue")
print(my_car)        # Output: Blue Toyota Camry (uses __str__)
print(repr(my_car))  # Output: Car(make=Toyota, model=Camry, color=Blue)
```

### **UML Diagram**
```
+------------------+
|      Car         |
+------------------+
| wheels: int = 4  |
| make: str        |
| model: str       |
| color: str       |
| speed: int       |
+------------------+
| __init__()       |
| accelerate()     |
| __str__()        |
| __repr__()       |
+------------------+
```

---

## **2. Inheritance**
### **Definition**
- **Inheritance**: Derive a new class (child) from an existing class (parent).
- **Method Overriding**: Redefine a parent method in the child class.
- **`super()`**: Access parent class methods/constructors.
- **Abstract Base Class (ABC)**: Define a template for derived classes.

### **Code Example**
```python
from abc import ABC, abstractmethod

# Abstract Base Class
class Vehicle(ABC):
    def __init__(self, name):
        self.name = name

    @abstractmethod
    def move(self):
        pass

# Child Class
class Boat(Vehicle):
    def move(self):
        return "Sailing on water"

class Truck(Vehicle):
    def __init__(self, name, cargo):
        super().__init__(name)  # Call parent constructor
        self.cargo = cargo

    def move(self):
        return "Driving on road"

# Usage
boat = Boat("Sailboat")
truck = Truck("Volvo", "Electronics")
print(boat.move())   # Output: Sailing on water
print(truck.move())  # Output: Driving on road
```

---

## **3. OOP in a Dynamic Language**
### **Dynamic Typing**
Variables can hold any type, resolved at runtime:
```python
x = 5       # Integer
x = "Hello" # String (allowed)
```

### **Static Type Checking (with `mypy`)**
```python
# Add type hints
def greet(name: str) -> str:
    return f"Hello, {name}"

greet(42)  # mypy error: Argument 1 has incompatible type "int"
```

### **Method Overloading (Workaround)**
Python doesn’t support traditional overloading, but use default parameters:
```python
class Calculator:
    def add(self, a, b, c=0):
        return a + b + c

calc = Calculator()
print(calc.add(2, 3))    # 5
print(calc.add(2, 3, 4)) # 9
```

---

## **4. Polymorphism**
### **Open-Closed Principle**
Classes should be open for extension but closed for modification.
```python
class Animal:
    def sound(self):
        raise NotImplementedError

class Dog(Animal):
    def sound(self):
        return "Woof!"

class Cat(Animal):
    def sound(self):
        return "Meow!"

# Common interface
animals = [Dog(), Cat()]
for animal in animals:
    print(animal.sound())  # Woof! Meow!
```

### **Protocols (Duck Typing)**
Objects are judged by their methods, not their types:
```python
class JSONSerializable:
    def to_json(self):
        return {"data": str(self)}

class Product(JSONSerializable):
    def __init__(self, name):
        self.name = name

def save_to_file(obj: JSONSerializable):
    print(obj.to_json())

save_to_file(Product("Laptop"))  # Output: {'data': '<__main__.Product object ...>'}
```

---

## **5. Encapsulation**
### **Attribute Visibility**
- **Public**: No underscores (default).
- **Protected**: Single underscore `_` (convention only).
- **Private**: Double underscore `__` (name mangling).

### **Code Example**
```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance  # Private attribute

    @property
    def balance(self):
        return self.__balance

    @balance.setter
    def balance(self, value):
        if value >= 0:
            self.__balance = value
        else:
            raise ValueError("Balance cannot be negative")

account = BankAccount(1000)
print(account.balance)  # 1000 (uses getter)
account.balance = 1500   # Uses setter
```

---

## **6. Abstraction**
Hide complex implementation details, expose only essentials.
```python
from abc import ABC, abstractmethod

class DatabaseConnector(ABC):
    @abstractmethod
    def connect(self):
        pass

class MySQLConnector(DatabaseConnector):
    def connect(self):
        return "Connected to MySQL"

# Usage
connector = MySQLConnector()
print(connector.connect())  # Output: Connected to MySQL
```

---

## **7. Classes in Python**
### **Class as an Object**
Classes are first-class objects (can be modified dynamically).
```python
class Employee:
    company = "Tech Corp"  # Class variable

    def __init__(self, name):
        self.name = name    # Instance variable

    @classmethod
    def change_company(cls, new_name):
        cls.company = new_name

    @staticmethod
    def calculate_tax(salary):
        return salary * 0.2

# Class method usage
Employee.change_company("Innovate Inc")
print(Employee.company)  # Output: Innovate Inc

# Static method usage
tax = Employee.calculate_tax(50000)
print(tax)  # Output: 10000.0
```

---

## **8. Real-Life Examples**
### **E-Commerce System**
- **Class**: `Product`, `Cart`, `Order`.
- **Inheritance**: `Electronics` → `Product`.
- **Encapsulation**: Private `__discount` in `Product`.
- **Polymorphism**: `calculate_price()` in different product categories.

### **Banking Application**
- **Abstraction**: `Account` base class with `withdraw()` method.
- **Static Method**: `Account.validate_account_number()`.
- **Class Variable**: `total_accounts` to track all accounts.

---

## **Summary Table**

| Concept              | Key Features                           | Python Syntax                     |
|----------------------|----------------------------------------|-----------------------------------|
| **Class/Objects**    | `__init__`, `self`, `__str__`, `__repr__` | `class Car:`                     |
| **Inheritance**      | `super()`, `ABC`, method overriding    | `class Truck(Vehicle):`          |
| **Polymorphism**     | Duck typing, protocols                 | Common method names across classes |
| **Encapsulation**    | `__private`, `@property`               | `self.__balance`, `@balance.setter` |
| **Abstraction**      | ABCs, hiding implementation           | `from abc import ABC, abstractmethod` |
| **Class Methods**    | `@classmethod`, `cls`                  | `def change_company(cls):`       |
| **Static Methods**   | `@staticmethod`                        | `def calculate_tax(salary):`     |
