---
tags:
- basics
---

<br>

## Introduction

> Variables and constants are fundamental concepts in Python programming. Variables store data values that can change during program execution, while constants are values meant to remain unchanged.

<br>

---

<br>

## Variables

> A variable is a name that refers to a memory location where data is stored. In Python, variables are dynamically typed, meaning you don’t need to specify the type explicitly (although you can use type hints to improve code readability and prevent type-related errors).

<br>

---

<br>

### Declaring Variables

> In Python, variable declaration is implicit. You assign a type using `: <type>`, and a value using the assignment operator `=`.

```python
x = 10       # Integer (dynamic)
y: int = 10  # Integer (type hinted)

print(x, y)
```

<br>

### Rules for Naming Variables

> - Must begin with a letter (a–z, A–Z) or an underscore (_).
> - Can contain letters, digits (0–9), and underscores.
> - Case-sensitive (e.g., `Name` and `name` are different variables).
> - Cannot use reserved keywords (e.g., `def`, `class`, `if`).

<br>

### Common Variable Types

> Integers (`int`): Whole numbers.

```python
count = 1
```

> Floats (`float`): Decimal numbers.

```python
price = 4.99
```

> Strings (`str`): Sequence of characters.

```python
message = "Hello, World!"
```

> Booleans (`bool`): True or False.

```python
is_python = True
```

> `None`: Represents the absence of a value.

```python
data = None
```

<br>

### Dynamic Typing

> Variables in Python can change types during execution.

```python
x = 10  # Integer
print(x)

x = "Now a string"  # String
print(x)
```

<br>

### Multiple Assignment

> Python supports assigning values to multiple variables in a single line.

```python
a, b, c = 1, 2, 3
```

<br>

> You can also assign the same value to multiple variables.

```python
x = y = z = 0
```

<br>

---

<br>

## Constants

> A constant is a value that is intended to remain unchanged during the execution of a program. Python does not have built-in constant support but follows naming conventions to indicate constants.

<br>

### Declaring Constants

> By convention, constants are written in uppercase with underscores separating words.
> While Python does not enforce immutability for constants, developers should treat variables with uppercase names as constants.

```python
PI = 3.14159
DAYS_IN_WEEK = 7
```

<br>

---

<br>

## Best Practices for Variables and Constants

1. Use descriptive names to improve readability.

```python
user_age = 25  # Clear and descriptive
```

2. Follow PEP 8 guidelines:
    - Use snake_case for variable names.
    - Use UPPERCASE for constants.
3. Avoid using ambiguous names like `x`, `y`, or `data` unless the context is clear.
4. Initialize variables before use to prevent runtime errors.

<br>

---

<br>

## Key Points

> - Variables are dynamically typed and can change during runtime.
> - Constants are not enforced in Python but are indicated using uppercase names.
> - Use descriptive and meaningful names for variables and constants to improve code clarity.