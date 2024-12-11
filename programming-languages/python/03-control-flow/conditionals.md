---
tags:
- control-flow
---

<br>

# Python Conditional Statements

> Conditional statements in Python allow you to execute different code blocks based on specific conditions. They are fundamental to control flow and decision making in programs.

<br>

### Key Characteristics

> - Indentation-based block structure
> - Multiple condition checking
> - Short-circuit evaluation
> - Truthy and falsy values
> - Pattern matching support (Python 3.10+)
> - Context management capabilities

<br>

---

<br>

## if, elif, else Statements

> The basic conditional statement structure in Python using if, elif, and else.

<br>

### Basic if Statement

> Simple condition checking:

```python
number = 5

if number > 0:
    print("Number is positive")

print("This always executes")
```

```sh
Number is positive
This always executes
```

<br>

### if-else Statement

> Two-way decision making:

```python
number = -5

if number > 0:
    print("Number is positive")
else:
    print("Number is non-positive")
```

```sh
Number is non-positive
```

<br>

### if-elif-else Chain

> Multiple condition checking:

```python
score = 85

if score >= 90:
    print("Grade: A")
elif score >= 80:
    print("Grade: B")
elif score >= 70:
    print("Grade: C")
elif score >= 60:
    print("Grade: D")
else:
    print("Grade: F")
```

```sh
Grade: B
```

<br>

### Nested Conditions

> Conditional statements within other conditional statements:

```python
age = 25
has_license = True

if age >= 18:
    print("Age requirement met")
    if has_license:
        print("Can drive")
    else:
        print("Cannot drive - no license")
else:
    print("Cannot drive - too young")
```

```sh
Age requirement met
Can drive
```

<br>

### Compound Conditions

> Using logical operators (and, or, not):

```python
age = 25
income = 50000
credit_score = 700

if age >= 21 and income >= 40000:
    if credit_score >= 700:
        print("Loan approved")
    elif credit_score >= 600:
        print("Loan needs review")
    else:
        print("Loan denied - low credit score")
else:
    print("Loan denied - age or income requirement not met")
```

```sh
Loan approved
```

<br>

### Truthy and Falsy Values

> Python considers certain values as False in boolean context:

```python
# Demonstrate falsy values
falsy_examples = [None, False, 0, 0.0, "", [], (), {}]

for value in falsy_examples:
    if value:
        print(f"{value} is True")
    else:
        print(f"{value} is False")

# Demonstrate truthy values
truthy_examples = [True, 42, -1, 3.14, "hello", [1, 2], (1,), {"a": 1}]

for value in truthy_examples:
    if value:
        print(f"{value} is True")
    else:
        print(f"{value} is False")
```

```sh
None is False
False is False
0 is False
0.0 is False
 is False
[] is False
() is False
{} is False
True is True
42 is True
-1 is True
3.14 is True
hello is True
[1, 2] is True
(1,) is True
{'a': 1} is True
```

<br>

---

<br>

## Match Statement

> The match statement (introduced in Python 3.10) provides advanced pattern matching capabilities, similar to switch statements in other languages but with more powerful features.

<br>

### Basic Match Pattern

> Simple value matching:

```python
def check_status(status):
    match status:
        case "ok":
            print("Everything is fine")
        case "error":
            print("Something went wrong")
        case _:  # Default case
            print("Unknown status")

# Test different values
statuses = ["ok", "error", "pending"]
for status in statuses:
    print(f"\nChecking status: {status}")
    check_status(status)
```

```sh
Checking status: ok
Everything is fine

Checking status: error
Something went wrong

Checking status: pending
Unknown status
```

<br>

### Pattern Matching with Literals

> Matching against different types of literal values:

```python
def describe_value(value):
    match value:
        case 0:
            print("Zero")
        case 1 | 2 | 3:
            print("Small number")
        case True:
            print("Boolean True")
        case False:
            print("Boolean False")
        case None:
            print("None value")
        case "":
            print("Empty string")
        case _:
            print(f"Something else: {value}")

# Test with different values
values = [0, 2, True, False, None, "", "hello"]
for val in values:
    print(f"\nValue: {val}")
    describe_value(val)
```

```sh
Value: 0
Zero

Value: 2
Small number

Value: True
Boolean True

Value: False
Boolean False

Value: None
None value

Value: 
Empty string

Value: hello
Something else: hello
```

<br>

### Sequence Patterns

> Matching sequences with various patterns:

```python
def analyze_point(point):
    match point:
        case (0, 0):
            print("At origin")
        case (0, y):
            print(f"On y-axis at y={y}")
        case (x, 0):
            print(f"On x-axis at x={x}")
        case (x, y):
            print(f"At point ({x}, {y})")
        case _:
            print("Not a point")

# Test with different points
points = [(0, 0), (0, 5), (5, 0), (3, 4), [1, 2]]
for p in points:
    print(f"\nAnalyzing: {p}")
    analyze_point(p)
```

```sh
Analyzing: (0, 0)
At origin

Analyzing: (0, 5)
On y-axis at y=5

Analyzing: (5, 0)
On x-axis at x=5

Analyzing: (3, 4)
At point (3, 4)

Analyzing: [1, 2]
At point (1, 2)
```

<br>

### Class Patterns

> Matching objects and their attributes:

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

class Circle:
    def __init__(self, center, radius):
        self.center = center
        self.radius = radius

def analyze_shape(shape):
    match shape:
        case Point(x=0, y=0):
            print("Point at origin")
        case Point(x=x, y=y):
            print(f"Point at ({x}, {y})")
        case Circle(center=Point(x=0, y=0), radius=r):
            print(f"Circle centered at origin with radius {r}")
        case Circle(center=center, radius=r):
            print(f"Circle centered at ({center.x}, {center.y}) with radius {r}")
        case _:
            print("Unknown shape")

# Test with different shapes
shapes = [
    Point(0, 0),
    Point(3, 4),
    Circle(Point(0, 0), 5),
    Circle(Point(1, 1), 3)
]

for shape in shapes:
    print(f"\nAnalyzing shape: {shape.__class__.__name__}")
    analyze_shape(shape)
```

```sh
Analyzing shape: Point
Point at origin

Analyzing shape: Point
Point at (3, 4)

Analyzing shape: Circle
Circle centered at origin with radius 5

Analyzing shape: Circle
Circle centered at (1, 1) with radius 3
```

<br>

### Guard Patterns

> Adding conditions to pattern matches:

```python
def analyze_number(value):
    match value:
        case int(x) if x < 0:
            print(f"Negative integer: {x}")
        case int(x) if x > 0:
            print(f"Positive integer: {x}")
        case float(x) if x.is_integer():
            print(f"Float with integer value: {x}")
        case float(x):
            print(f"Float value: {x}")
        case _:
            print(f"Other type: {value}")

# Test with different values
values = [-5, 10, 3.0, 3.14, "string"]
for val in values:
    print(f"\nAnalyzing: {val}")
    analyze_number(val)
```

```sh
Analyzing: -5
Negative integer: -5

Analyzing: 10
Positive integer: 10

Analyzing: 3.0
Float with integer value: 3.0

Analyzing: 3.14
Float value: 3.14

Analyzing: string
Other type: string
```

<br>

---

<br>

## Conditional Expressions

> Conditional expressions (also known as ternary operators) provide a concise way to write simple if-else statements in a single line.

<br>

### Basic Syntax

> The syntax is: `value_if_true if condition else value_if_false`

```python
# Basic ternary operator
x = 5
result = "Positive" if x > 0 else "Non-positive"
print(f"Number is: {result}")

# Compare with traditional if-else
if x > 0:
    traditional_result = "Positive"
else:
    traditional_result = "Non-positive"
print(f"Same result using if-else: {traditional_result}")
```

```sh
Number is: Positive
Same result using if-else: Positive
```

<br>

### Common Use Cases

> Practical applications of conditional expressions:

```python
# Setting default values
name = ""
display_name = name if name else "Anonymous"
print(f"Display name: {display_name}")

# Selecting format string
age = 20
status = "adult" if age >= 18 else "minor"
print(f"Person is an: {status}")

# List operations
numbers = [1, 2, 3]
message = "List has items" if numbers else "List is empty"
print(message)
```

```sh
Display name: Anonymous
Person is an: adult
List has items
```

<br>

### Multiple Conditions

> Handling multiple conditions in conditional expressions:

```python
# Multiple conditions using and/or
x = 5
y = 10

# Check if x is between 0 and y
result = "In range" if 0 <= x <= y else "Out of range"
print(f"Value {x} is {result}")

# Combining multiple conditions
status = "Valid" if x > 0 and y > 0 else "Invalid"
print(f"Status: {status}")

# Chaining conditions
grade = 85
letter = "A" if grade >= 90 else "B" if grade >= 80 else "C" if grade >= 70 else "F"
print(f"Grade: {letter}")
```

```sh
Value 5 is In range
Status: Valid
Grade: B
```

<br>

### Function Arguments

> Using conditional expressions in function calls:

```python
def greet(name, formal=False):
    greeting = "Dear" if formal else "Hello"
    return f"{greeting}, {name}!"

# Test with different formality
print(greet("Alice", formal=True))
print(greet("Bob", formal=False))

# Conditional in function call
def process_number(x):
    return abs(x) if x < 0 else x * 2

print(f"Process -5: {process_number(-5)}")
print(f"Process 5: {process_number(5)}")
```

```sh
Dear, Alice!
Hello, Bob!
Process -5: 5
Process 5: 10
```

<br>

### List Comprehension with Conditionals

> Combining conditional expressions with list comprehensions:

```python
numbers = range(-5, 6)

# Filter and transform
results = [
    "Positive" if n > 0 else "Zero" if n == 0 else "Negative"
    for n in numbers
]

print("Number classifications:")
for n, result in zip(numbers, results):
    print(f"{n}: {result}")

# Conditional transformation
processed = [x * 2 if x > 0 else x for x in numbers]
print(f"\nProcessed numbers: {processed}")
```

```sh
Number classifications:
-5: Negative
-4: Negative
-3: Negative
-2: Negative
-1: Negative
0: Zero
1: Positive
2: Positive
3: Positive
4: Positive
5: Positive

Processed numbers: [-5, -4, -3, -2, -1, 0, 2, 4, 6, 8, 10]
```

<br>

### Best Practices

> Guidelines for using conditional expressions effectively:

```python
# Good: Simple, clear conditions
age = 20
status = "adult" if age >= 18 else "minor"

# Bad: Complex nested conditions (use regular if statements instead)
value = 5
result = (
    "A" if value > 10 else 
    "B" if value > 5 else 
    "C" if value > 0 else 
    "D"
)

# Good: Default values
config = {}
port = config.get('port') if config else 8080

# Good: Simple transformations
numbers = [1, -2, 3, -4]
abs_values = [x if x >= 0 else -x for x in numbers]
print(f"Absolute values: {abs_values}")
```

```sh
Absolute values: [1, 2, 3, 4]
```