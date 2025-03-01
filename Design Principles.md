### **Core Object-Oriented Design Principles**  
1. [Single Responsibility Principle (SRP)](#single-responsibility-principle-srp)  
2. [Open/Closed Principle (OCP)](#openclosed-principle-ocp)  
3. [Liskov Substitution Principle (LSP)](#liskov-substitution-principle-lsp)  
4. [Interface Segregation Principle (ISP)](#interface-segregation-principle-isp)  
5. [Dependency Inversion Principle (DIP)](#dependency-inversion-principle-dip)  
6. [DRY (Don’t Repeat Yourself)](#dry-dont-repeat-yourself)  
7. [Composition Over Inheritance](#composition-over-inheritance)  

---

### **Additional Design Principles**  
1. [Keep It Simple, Stupid (KISS)](#keep-it-simple-stupid-kiss)  
2. [You Aren’t Gonna Need It (YAGNI)](#you-arent-gonna-need-it-yagni)  

---

## **1. Single Responsibility Principle (SRP)**  
**Definition**: A class should have only one reason to change (i.e., one responsibility).  

### ❌ Bad Example:
```python
class UserManager:
    def authenticate(self, username, password):
        # Authentication logic
    
    def save_to_database(self, user_data):
        # Database save logic
    
    def send_email(self, user_email, message):
        # Email sending logic
```
**Problem**: Combines authentication, database management, and email handling.

### ✅ Good Example:
```python
class Authenticator:
    def authenticate(self, username, password): ...

class DatabaseService:
    def save_user(self, user_data): ...

class EmailService:
    def send_email(self, user_email, message): ...
```
**Benefit**: Each class handles a single responsibility.

---

## **2. Open/Closed Principle (OCP)**  
**Definition**: Classes should be **open for extension** but **closed for modification**.  

### ❌ Bad Example:
```python
class AreaCalculator:
    def calculate_area(self, shape):
        if isinstance(shape, Rectangle):
            return shape.width * shape.height
        elif isinstance(shape, Circle):
            return 3.14 * shape.radius ** 2
        # Adding a new shape requires modifying this method
```
**Problem**: Adding a new shape (e.g., `Triangle`) forces changes to `AreaCalculator`.

### ✅ Good Example:
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self): ...

class Rectangle(Shape):
    def area(self): return self.width * self.height

class Circle(Shape):
    def area(self): return 3.14 * self.radius ** 2

class AreaCalculator:
    def calculate_area(self, shape: Shape):
        return shape.area()  # Works for any Shape subclass
```
**Benefit**: New shapes extend `Shape` without altering existing code.

---

## **3. Liskov Substitution Principle (LSP)**  
**Definition**: Subtypes must be substitutable for their base types.  

### ❌ Bad Example:
```python
class Rectangle:
    def set_width(self, w): ...
    def set_height(self, h): ...

class Square(Rectangle):
    def set_width(self, w):
        self.width = w
        self.height = w  # Violates Rectangle's behavior
```
**Problem**: A `Square` changes the behavior of `set_width/set_height`.

### ✅ Good Example:
```python
class Shape(ABC):
    @abstractmethod
    def area(self): ...

class Rectangle(Shape): ...
class Square(Shape): ...
```
**Benefit**: Avoid inheritance hierarchies that violate base class contracts.

---

## **4. Interface Segregation Principle (ISP)**  
**Definition**: Clients should not depend on interfaces they don’t use.  

### ❌ Bad Example:
```python
class Worker(ABC):
    @abstractmethod
    def work(self): ...
    @abstractmethod
    def eat(self): ...  # Not all workers need this

class Robot(Worker):
    def work(self): ...
    def eat(self): ...  # Robots don't eat!
```
**Problem**: Forcing `Robot` to implement `eat`.

### ✅ Good Example:
```python
class Workable(ABC):
    @abstractmethod
    def work(self): ...

class Eatable(ABC):
    @abstractmethod
    def eat(self): ...

class Human(Workable, Eatable): ...
class Robot(Workable): ...
```
**Benefit**: Split interfaces into smaller, role-specific components.

---

## **5. Dependency Inversion Principle (DIP)**  
**Definition**: Depend on abstractions, not concrete implementations.  

### ❌ Bad Example:
```python
class LightBulb:
    def turn_on(self): ...

class Switch:
    def __init__(self):
        self.bulb = LightBulb()  # Direct dependency
    
    def operate(self):
        self.bulb.turn_on()
```
**Problem**: `Switch` is tightly coupled to `LightBulb`.

### ✅ Good Example:
```python
class Switchable(ABC):
    @abstractmethod
    def turn_on(self): ...

class LightBulb(Switchable): ...

class Fan(Switchable): ...

class Switch:
    def __init__(self, device: Switchable):  # Dependency injection
        self.device = device
    
    def operate(self):
        self.device.turn_on()
```
**Benefit**: Switch works with any `Switchable` device (bulb, fan, etc.).

---

## **Additional Principles**  
### **DRY (Don’t Repeat Yourself)**  
**Example**: Extract shared code into functions/classes.  
```python
# ❌ Repeated code
def calculate_tax(order):
    return order.total * 0.1

def calculate_shipping(order):
    return order.total * 0.05

# ✅ Reusable function
def calculate_fee(order, rate):
    return order.total * rate
```

## **Keep It Simple, Stupid (KISS)**  
**Definition**: Prefer simple, straightforward solutions over complex ones.  

### ❌ Bad Example (Over-Engineering):  
```python
def calculate_discount(price: float, is_member: bool, coupon_code: str = None) -> float:
    discount = 0
    if is_member:
        discount += 0.1
    if coupon_code == "SUMMER25":
        discount += 0.25
    elif coupon_code == "FALL15":
        discount += 0.15
    return price * (1 - discount)
```

### ✅ Good Example (Simplified):  
```python
def calculate_discount(price: float, discount_percent: float) -> float:
    return price * (1 - discount_percent)

# Usage: Apply discounts externally based on rules
discount = 0.1 if is_member else 0.0
if coupon_code in DISCOUNT_MAP:  # DISCOUNT_MAP = {"SUMMER25": 0.25, ...}
    discount += DISCOUNT_MAP[coupon_code]
final_price = calculate_discount(price, discount)
```
**Why It Works**: Separates discount calculation from business rules.  

---

## **You Aren’t Gonna Need It (YAGNI)**  
**Definition**: Don’t add functionality until it’s necessary.  

### ❌ Bad Example (Premature Generalization):  
```python
class PaymentProcessor:
    def pay_credit_card(self, amount): ...  # Current requirement
    def pay_paypal(self, amount): ...       # Not needed yet
    def pay_crypto(self, amount): ...       # Not needed yet
```

### ✅ Good Example (Minimal Implementation):  
```python
class PaymentProcessor:
    def pay(self, amount, method="credit_card"):
        if method == "credit_card":
            self._process_credit_card(amount)
        else:
            raise ValueError("Unsupported method")
```
**Why It Works**: Avoids code bloat by focusing on current needs.  

---

## **Composition Over Inheritance**  
**Definition**: Favor composing objects over rigid class hierarchies.  

### ❌ Bad Example (Deep Inheritance):  
```python
class Bird:
    def fly(self): ...

class Duck(Bird):
    def quack(self): ...

class RubberDuck(Duck):  # Can't fly or quack!
    def fly(self): raise NotImplementedError
    def quack(self): print("Squeak!")
```
**Problem**: Forced to override methods, violating Liskov Substitution Principle.  

### ✅ Good Example (Composition):  
```python
class Flyable:
    def fly(self): ...

class Quackable:
    def quack(self): ...

class Duck:
    def __init__(self):
        self.fly_behavior = Flyable()
        self.quack_behavior = Quackable()

class RubberDuck:
    def __init__(self):
        self.quack_behavior = SqueakBehavior()  # Custom behavior
```
**Why It Works**: Flexible behaviors without inheritance constraints.  

---

## **Key Takeaways**  
| Principle              | Goal                                  | Example                          |
|------------------------|---------------------------------------|----------------------------------|
| **SRP**                | Single responsibility per class       | Split `UserManager` into services |
| **OCP**                | Extend without modifying existing code| Abstract `Shape` classes          |
| **LSP**                | Substitutability of subtypes          | Avoid `Square` → `Rectangle`      |
| **ISP**                | Avoid fat interfaces                  | Split `Worker` → `Workable`/`Eatable` |
| **DIP**                | Decouple via abstractions             | `Switch` depends on `Switchable`  |
| **KISS**               | Simplify solutions                    | Avoid nested conditionals        |
| **YAGNI**              | Build only what’s needed now          | Skip speculative features        |
| **Composition Over Inheritance** | Prefer flexible object assembly | Use components instead of deep hierarchies |

---
