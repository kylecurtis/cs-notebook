# Python Classes

> Classes are the foundation of Object-Oriented Programming (OOP) in Python, providing a way to bundle data and functionality together. They allow you to create custom objects that encapsulate data and behavior.

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

> Classes are defined using the `class` keyword and typically contain methods and attributes.

<br>

### Basic Class Structure
> - Syntax: `class ClassName:`
> - Components:
>   - Class name (typically CapWords convention)
>   - Class body (indented block)
>   - Methods and attributes
> - Note: All classes inherit from `object` by default

```python
class Person:
    def __init__(self, name):
        self.name = name
    
    def greet(self):
        return f"Hello, my name is {self.name}"

# Create and use instance
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

# Using class attributes
student1 = Student("Bob")
student2 = Student("Charlie")

print(f"School: {Student.school}")
print(f"{student1.name} attends {student1.school}")
print(f"{student2.name} attends {student2.school}")
```

```sh
School: Python Academy
Bob attends Python Academy
Charlie attends Python Academy
```

<br>

### Instance Attributes
> - Defined inside methods (typically __init__)
> - Unique to each instance
> - Accessed via instance only
> - Note: Use self to reference instance

```python
class Rectangle:
    def __init__(self, width, height):
        self.width = width      # Instance attributes
        self.height = height
    
    def area(self):
        return self.width * self.height

rect = Rectangle(5, 3)
print(f"Width: {rect.width}")
print(f"Area: {rect.area()}")
```

```sh
Width: 5
Area: 15
```

<br>

---

<br>

## Instance Methods

> Instance methods are functions defined within a class that can access and modify instance attributes. They are the most common type of method in Python classes.

<br>

### Basic Method Definition
> - Syntax: `def method_name(self, parameters...):`
> - Parameters:
>   - self: Reference to instance (automatically passed)
>   - Additional parameters as needed
> - Info: Can access and modify instance state
> - Note: 'self' is convention but any valid name works

```python
class Dog:
    def __init__(self, name):
        self.name = name
    
    def bark(self):
        return f"{self.name} says Woof!"
    
    def rename(self, new_name):
        self.name = new_name

dog = Dog("Rex")
print(dog.bark())
dog.rename("Max")
print(dog.bark())
```

```sh
Rex says Woof!
Max says Woof!
```

<br>

### Accessing Instance State
> - Through self parameter
> - Can read instance attributes
> - Can modify instance attributes
> - Can call other instance methods

```python
class BankAccount:
    def __init__(self, balance):
        self.balance = balance
    
    def deposit(self, amount):
        self.balance += amount
        return self.get_balance()
    
    def get_balance(self):
        return f"Balance: ${self.balance}"

account = BankAccount(100)
print(account.deposit(50))
print(account.get_balance())
```

```sh
Balance: $150
Balance: $150
```

<br>

### Method Interactions
> - Methods can call other methods
> - Use self to access other methods
> - Can chain method calls
> - Note: Maintain clear dependencies

```python
class Temperature:
    def __init__(self, celsius):
        self.celsius = celsius
    
    def to_fahrenheit(self):
        return (self.celsius * 9/5) + 32
    
    def display(self):
        return f"{self.celsius}°C is {self.to_fahrenheit()}°F"

temp = Temperature(25)
print(temp.display())
```

```sh
25°C is 77.0°F
```

<br>

### Method Parameters
> - Can have required parameters
> - Can have default values
> - Can use *args and **kwargs
> - Note: self is always first parameter

```python
class Calculator:
    def add(self, *numbers):
        return sum(numbers)
    
    def multiply(self, a, b=1):
        return a * b

calc = Calculator()
print(f"Sum: {calc.add(1, 2, 3)}")
print(f"Product: {calc.multiply(5)}")
print(f"Product: {calc.multiply(5, 3)}")
```

```sh
Sum: 6
Product: 5
Product: 15
```

<br>

---

<br>

## Class Methods

> Class methods are methods that work with the class itself rather than instances. They are defined using the @classmethod decorator and receive the class as their first parameter.

<br>

### Basic Class Method
> - Syntax: `@classmethod def method_name(cls, parameters...):`
> - Parameters:
>   - cls: Reference to class (automatically passed)
>   - Additional parameters as needed
> - Info: Can access and modify class state
> - Note: Cannot access instance attributes

```python
class Student:
    school = "Python Academy"
    
    @classmethod
    def change_school(cls, new_school):
        cls.school = new_school
    
    @classmethod
    def get_school(cls):
        return cls.school

print(Student.get_school())
Student.change_school("Code Academy")
print(Student.get_school())
```

```sh
Python Academy
Code Academy
```

<br>

### Alternative Constructors
> - Common use case for class methods
> - Create instances from different data formats
> - Factory method pattern
> - Note: Returns class instance

```python
class Date:
    def __init__(self, year, month, day):
        self.year = year
        self.month = month
        self.day = day
    
    @classmethod
    def from_string(cls, date_string):
        year, month, day = map(int, date_string.split('-'))
        return cls(year, month, day)
    
    def __str__(self):
        return f"{self.year}-{self.month}-{self.day}"

# Using regular constructor
date1 = Date(2024, 3, 15)
# Using alternative constructor
date2 = Date.from_string("2024-03-15")

print(date1)
print(date2)
```

```sh
2024-3-15
2024-3-15
```

<br>

### Working with Class State
> - Can access class attributes
> - Can modify class attributes
> - Shared across all instances
> - Note: Cannot access instance attributes directly

```python
class Counter:
    count = 0
    
    def __init__(self):
        Counter.increment()
    
    @classmethod
    def increment(cls):
        cls.count += 1
    
    @classmethod
    def get_count(cls):
        return cls.count

# Create instances and check count
c1 = Counter()
print(f"Count: {Counter.get_count()}")
c2 = Counter()
print(f"Count: {Counter.get_count()}")
```

```sh
Count: 1
Count: 2
```

<br>

---

<br>

## Static Methods

> Static methods are methods that don't access class or instance state. They are defined using the @staticmethod decorator and behave like regular functions that live in the class namespace.

<br>

### Basic Static Method
> - Syntax: `@staticmethod def method_name(parameters...):`
> - Parameters:
>   - No automatic first parameter
>   - Regular parameters as needed
> - Info: Cannot access class or instance state
> - Note: Utility functions related to class purpose

```python
class MathOperations:
    @staticmethod
    def is_positive(number):
        return number > 0
    
    @staticmethod
    def is_even(number):
        return number % 2 == 0

# Use static methods directly
print(MathOperations.is_positive(5))
print(MathOperations.is_even(4))
```

```sh
True
True
```

<br>

### Helper Methods
> - Used for utility functions
> - No access to instance or class data
> - Independent operations
> - Note: Could be regular functions, but logically belong to class

```python
class DateValidator:
    @staticmethod
    def is_valid_month(month):
        return 1 <= month <= 12
    
    @staticmethod
    def is_leap_year(year):
        return year % 4 == 0 and (year % 100 != 0 or year % 400 == 0)

# Validate dates
print(f"Valid month: {DateValidator.is_valid_month(13)}")
print(f"Leap year: {DateValidator.is_leap_year(2024)}")
```

```sh
Valid month: False
Leap year: True
```

<br>

### Comparison with Other Methods
> - Static Methods:
>   - No access to class/instance state
>   - Utility functions
>   - Independent operations
> - Instance Methods:
>   - Access instance state via self
> - Class Methods:
>   - Access class state via cls

```python
class Calculator:
    multiplier = 2  # Class attribute
    
    def __init__(self, value):
        self.value = value  # Instance attribute
    
    @staticmethod
    def add(a, b):  # No access to class/instance
        return a + b
    
    @classmethod
    def multiply_class(cls, x):  # Access to class
        return x * cls.multiplier
    
    def multiply_instance(self):  # Access to instance
        return self.value * self.multiplier

# Using different method types
calc = Calculator(5)
print(f"Static Add: {Calculator.add(3, 4)}")
print(f"Class Multiply: {Calculator.multiply_class(3)}")
print(f"Instance Multiply: {calc.multiply_instance()}")
```

```sh
Static Add: 7
Class Multiply: 6
Instance Multiply: 10
```

<br>

---

<br>

## Properties

> Properties provide a way to manage attribute access, allowing you to define methods that behave like attributes. They enable controlled access to class attributes through getters, setters, and deleters.

<br>

### Basic Property
> - Syntax: `@property def property_name(self):`
> - Return: Any type
> - Info: Creates read-only property
> - Note: Accessed like an attribute, not called like a method

```python
class Circle:
    def __init__(self, radius):
        self._radius = radius
    
    @property
    def radius(self):
        return self._radius

circle = Circle(5)
print(f"Radius: {circle.radius}")  # Access like attribute
```

```sh
Radius: 5
```

<br>

### Property Setter
> - Syntax: `@property_name.setter def property_name(self, value):`
> - Info: Allows setting property value
> - Note: Can include validation logic

```python
class Person:
    def __init__(self, name):
        self._name = name
    
    @property
    def name(self):
        return self._name
    
    @name.setter
    def name(self, value):
        if not value.strip():
            raise ValueError("Name cannot be empty")
        self._name = value

person = Person("Alice")
print(person.name)
person.name = "Bob"    # Uses setter
print(person.name)
```

```sh
Alice
Bob
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

### Property with Validation
> - Validate data before setting
> - Raise exceptions for invalid data
> - Modify data during setting
> - Note: Protects object's internal state

```python
class BankAccount:
    def __init__(self, balance):
        self._balance = 0
        self.balance = balance  # Uses setter
    
    @property
    def balance(self):
        return self._balance
    
    @balance.setter
    def balance(self, value):
        if value < 0:
            raise ValueError("Balance cannot be negative")
        self._balance = value

account = BankAccount(100)
print(f"Balance: ${account.balance}")

try:
    account.balance = -50
except ValueError as e:
    print(f"Error: {e}")
```

```sh
Balance: $100
Error: Balance cannot be negative
```

