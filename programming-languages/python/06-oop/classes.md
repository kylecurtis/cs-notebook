# Python Classes

> Python classes are the foundation of Object-Oriented Programming (OOP), providing a way to bundle data and functionality together into reusable objects.

<br>

### Key Characteristics

> - Blueprint for creating objects
> - Supports inheritance and polymorphism
> - Combines attributes (data) and methods (functions)
> - Provides data encapsulation
> - Supports method overriding
> - Allows for multiple inheritance

<br>

---

<br>

## Class Definition

> Classes are defined using the `class` keyword and contain methods and attributes.

<br>

### Basic Class Structure
> - Syntax: `class ClassName:`
> - Parameters:
>   - Optional base classes in parentheses
> - Components:
>   - Class body (indented block)
>   - Methods and attributes
> - Note: All classes inherit from `object` by default

```python
class Person:
    def __init__(self, name):
        self.name = name
    
    def greet(self):
        return f"Hello, my name is {self.name}"

person = Person("Alice")
print(person.greet())
```

```sh
Hello, my name is Alice
```

<br>

### Class Attributes
> - Defined directly in class body
> - Shared among all instances
> - Can be accessed via class or instance
> - Note: Modifying via instance creates instance attribute

```python
class Student:
    school = "Python Academy"  # Class attribute
    
    def __init__(self, name):
        self.name = name      # Instance attribute

student1 = Student("Bob")
print(f"School: {Student.school}")
print(f"{student1.name} at {student1.school}")
```

```sh
School: Python Academy
Bob at Python Academy
```

<br>

---

<br>

### Instance Attributes
> - Defined inside methods (typically __init__)
> - Unique to each instance
> - Accessed via self parameter
> - Note: Use clear, descriptive names
> - Best Practice: Define all instance attributes in __init__

```python
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    def area(self):
        return self.width * self.height

rect = Rectangle(5, 3)
print(f"Area: {rect.area()}")
```

```sh
Area: 15
```

<br>

---

<br>

## Instance Methods

> Instance methods are functions defined within a class that can access and modify instance state through the self parameter.

<br>

### Method Definition
> - Syntax: `def method_name(self, parameters...):`
> - Parameters:
>   - self: Reference to instance (automatically passed)
>   - Additional parameters as needed
> - Info: Can access and modify instance state
> - Note: 'self' is convention but any valid name works

```python
class Counter:
    def __init__(self):
        self.count = 0
    
    def increment(self):
        self.count += 1
        return self.count

counter = Counter()
print(counter.increment())  # 1
print(counter.increment())  # 2
```

```sh
1
2
```

<br>

### Instance State Access
> - Access through self parameter
> - Can read instance attributes
> - Can modify instance attributes
> - Can call other instance methods
> - Note: Maintain clear method dependencies

```python
class BankAccount:
    def __init__(self, balance):
        self.balance = balance
    
    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
        return self.balance

account = BankAccount(100)
print(account.deposit(50))
```

```sh
150
```

<br>

---

<br>

## Class Methods

> Class methods work with the class itself rather than instances. They are marked with the @classmethod decorator and receive the class as their first parameter.

<br>

### Basic Class Method
> - Syntax: `@classmethod def method_name(cls, parameters...):`
> - Parameters:
>   - cls: Reference to class (automatically passed)
>   - Additional parameters as needed
> - Info: Can access and modify class state
> - Note: Cannot access instance attributes directly

```python
class Date:
    @classmethod
    def from_string(cls, date_str):
        year, month, day = map(int, date_str.split('-'))
        return cls(year, month, day)
    
    def __init__(self, year, month, day):
        self.year = year
        self.month = month
        self.day = day

date = Date.from_string('2024-03-15')
print(f"{date.year}-{date.month}-{date.day}")
```

```sh
2024-3-15
```

<br>

### Alternative Constructors
> - Common use case for class methods
> - Create instances from different data formats
> - Provide meaningful creation patterns
> - Note: Always return class instance

```python
class Time:
    def __init__(self, hours, minutes):
        self.hours = hours
        self.minutes = minutes
    
    @classmethod
    def from_string(cls, time_str):
        hours, minutes = map(int, time_str.split(':'))
        return cls(hours, minutes)

time = Time.from_string('14:30')
print(f"{time.hours}:{time.minutes}")
```

```sh
14:30
```

<br>

---

<br>

## Static Methods

> Static methods are methods that don't access class or instance state. They are utility functions that belong to the class namespace and are marked with the @staticmethod decorator.

<br>

### Basic Static Method
> - Syntax: `@staticmethod def method_name(parameters...):`
> - Parameters:
>   - No automatic first parameter
>   - Regular parameters as needed
> - Info: Cannot access class or instance state
> - Note: Utility functions related to class purpose

```python
class MathUtil:
    @staticmethod
    def is_even(number):
        return number % 2 == 0
    
    @staticmethod
    def is_positive(number):
        return number > 0

print(MathUtil.is_even(4))      # True
print(MathUtil.is_positive(-5))  # False
```

```sh
True
False
```

<br>

---

<br>

## Properties

> Properties provide controlled access to class attributes, allowing get, set, and delete operations with additional logic.

<br>

### Basic Property
> - Syntax: `@property def property_name(self):`
> - Return: Any type
> - Info: Creates read-only property by default
> - Note: Accessed like an attribute, not called like method

```python
class Temperature:
    def __init__(self, celsius):
        self._celsius = celsius
    
    @property
    def celsius(self):
        return self._celsius

temp = Temperature(25)
print(f"{temp.celsius}°C")
```

```sh
25°C
```

<br>

### Property Setter
> - Syntax: `@property_name.setter def property_name(self, value):`
> - Info: Allows setting property value
> - Note: Can include validation logic
> - Best Practice: Validate input data

```python
class Circle:
    def __init__(self, radius):
        self._radius = radius
    
    @property
    def radius(self):
        return self._radius
    
    @radius.setter
    def radius(self, value):
        if value <= 0:
            raise ValueError("Radius must be positive")
        self._radius = value

circle = Circle(5)
print(f"Radius: {circle.radius}")
circle.radius = 10
print(f"New radius: {circle.radius}")
```

```sh
Radius: 5
New radius: 10
```

<br>

### Computed Properties
> - Properties that calculate their value
> - No storage required
> - Updates automatically
> - Note: Calculation occurs on each access

```python
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    @property
    def area(self):
        return self.width * self.height
    
    @property
    def perimeter(self):
        return 2 * (self.width + self.height)

rect = Rectangle(3, 4)
print(f"Area: {rect.area}")
print(f"Perimeter: {rect.perimeter}")
```

```sh
Area: 12
Perimeter: 14
```

<br>

---

<br>

## Magic Methods

> Magic methods (special methods) are predefined method names with double underscores that customize class behavior and integrate with Python's built-in operations.

<br>

### Initialization and Representation
> - `__init__`: Constructor method
> - `__str__`: Informal string representation
> - `__repr__`: Official string representation
> - Note: Always implement both `__str__` and `__repr__`

```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author
    
    def __str__(self):
        return f"{self.title} by {self.author}"
    
    def __repr__(self):
        return f"Book(title='{self.title}', author='{self.author}')"

book = Book("Python", "Guido")
print(str(book))   # Informal string
print(repr(book))  # Official string
```

```sh
Python by Guido
Book(title='Python', author='Guido')
```

<br>

### Comparison Methods
> - `__eq__`: Equal to (==)
> - `__lt__`: Less than (<)
> - `__gt__`: Greater than (>)
> - Note: Other comparison methods derived from these

```python
class Temperature:
    def __init__(self, celsius):
        self.celsius = celsius
    
    def __eq__(self, other):
        return self.celsius == other.celsius
    
    def __lt__(self, other):
        return self.celsius < other.celsius

t1 = Temperature(20)
t2 = Temperature(25)
print(t1 < t2)    # True
print(t1 == t2)   # False
```

```sh
True
False
```

<br>

### Container Methods
> - `__len__`: Length of container
> - `__getitem__`: Access with []
> - `__setitem__`: Assignment with []
> - Note: Makes class behave like built-in containers

```python
class Stack:
    def __init__(self):
        self._items = []
    
    def __len__(self):
        return len(self._items)
    
    def __getitem__(self, index):
        return self._items[index]
    
    def push(self, item):
        self._items.append(item)

stack = Stack()
stack.push("A")
stack.push("B")
print(f"Length: {len(stack)}")
print(f"First item: {stack[0]}")
```

```sh
Length: 2
First item: A
```

<br>

### Arithmetic Methods
> - `__add__`: Addition (+)
> - `__sub__`: Subtraction (-)
> - `__mul__`: Multiplication (*)
> - Note: Implement corresponding right-hand methods (`__radd__`, etc.) if needed

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)
    
    def __str__(self):
        return f"({self.x}, {self.y})"

v1 = Vector(1, 2)
v2 = Vector(3, 4)
print(f"Sum: {v1 + v2}")
```

```sh
Sum: (4, 6)
```

<br>

---

<br>

## Method Resolution Order

> Method Resolution Order (MRO) determines how Python searches for methods in inheritance hierarchies.

<br>

### Basic Inheritance
> - MRO in single inheritance
> - Linear method lookup path
> - Note: Python uses C3 linearization algorithm
> - Access MRO using Class.mro() or Class.__mro__

```python
class Animal:
    def speak(self):
        return "Animal speaks"

class Dog(Animal):
    def speak(self):
        return "Dog barks"

class Puppy(Dog):
    pass

puppy = Puppy()
print(puppy.speak())
print(Puppy.mro())
```

```sh
Dog barks
[<class '__main__.Puppy'>, <class '__main__.Dog'>, <class '__main__.Animal'>, <class 'object'>]
```

<br>

---

<br>

## Abstract Base Classes

> Abstract Base Classes (ABCs) define a common interface for derived classes. They may contain abstract methods that must be implemented by derived classes.

<br>

### Basic Abstract Class
> - Import: `from abc import ABC, abstractmethod`
> - Base Class: Inherit from ABC
> - Methods: Mark abstract methods with @abstractmethod
> - Note: Cannot instantiate abstract classes directly

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass
    
    @abstractmethod
    def perimeter(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    def area(self):
        return self.width * self.height
    
    def perimeter(self):
        return 2 * (self.width + self.height)

rect = Rectangle(5, 3)
print(f"Area: {rect.area()}")
```

```sh
Area: 15
```

<br>

### Abstract Properties
> - Can define abstract properties
> - Must be implemented in derived classes
> - Use @property and @abstractmethod together
> - Note: Order of decorators matters

```python
class Animal(ABC):
    @property
    @abstractmethod
    def sound(self):
        pass

class Dog(Animal):
    @property
    def sound(self):
        return "Woof!"

dog = Dog()
print(f"Dog says: {dog.sound}")
```

```sh
Dog says: Woof!
```

<br>

### Abstract Class Methods
> - Can define abstract class methods
> - Use @classmethod and @abstractmethod together
> - Must be implemented in derived classes
> - Note: Provides interface for class-level operations

```python
class DatabaseConnector(ABC):
    @classmethod
    @abstractmethod
    def connect(cls, url):
        pass

class SQLConnector(DatabaseConnector):
    @classmethod
    def connect(cls, url):
        return f"Connected to SQL at {url}"

print(SQLConnector.connect("localhost"))
```

```sh
Connected to SQL at localhost
```

<br>

### Interface Definition
> - Use ABCs to define interfaces
> - Specify required methods
> - Provide default implementations when appropriate
> - Note: Python supports multiple inheritance of ABCs

```python
class Drawable(ABC):
    @abstractmethod
    def draw(self):
        pass
    
    def prepare(self):  # Default implementation
        return "Preparing to draw"

class Circle(Drawable):
    def draw(self):
        return "Drawing Circle"

circle = Circle()
print(circle.prepare())
print(circle.draw())
```

```sh
Preparing to draw
Drawing Circle
```