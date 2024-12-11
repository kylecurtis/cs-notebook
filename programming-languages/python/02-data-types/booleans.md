---
tags:
- data-types
---

<br>

# Python Booleans

> Booleans in Python are a core data type representing one of two values: `True` or `False`. They are often used in conditional statements and logical operations.

<br>

### Key Characteristics

> - Represent logical values: `True` and `False`
> - Internally subclass of `int` (`True` = 1, `False` = 0)
> - Used for conditional and control flow logic
> - Supports logical operations
> - Can be converted from other data types

<br>

---

<br>

## Boolean Values and Expressions

> Boolean values are represented by the keywords `True` and `False`.

```python
# Boolean literals
status = True
flag = False

print(status)
print(flag)
```

```sh
True
False
```

<br>

### Implicit Boolean Conversion
> In Python, some values are considered `True` (truthy) or `False` (falsy) when evaluated in a Boolean context.
> Any object can be evaluated as a Boolean using `bool()`. By default:
> - Values like `0`, `None`, `""` (empty string), and empty collections (`[]`, `{}`, `()`) evaluate to `False`.
> - Non-zero numbers, non-empty strings, and non-empty collections evaluate to `True`.

```python
# Falsy values
print(bool(None))   # None (False)
print(bool(False))  # False (False)
print(bool(0))      # 0 Integer (False) 
print(bool(0.0))    # 0.0 Float (False)
print(bool(""))     # Empty string (False)

# Empty collections (False)
print(bool([]))
print(bool(()))
print(bool({}))
```

```sh
False
False
False
False
False
False
False
False
```

<br>

```python
# Truthy values
print(bool(42))  
print(bool("Python"))
print(bool([1, 2, 3]))
print(bool(-10))
```

```sh
True
True
True
True
```

<br>

---

<br>

## Logical Operators

> Python provides three logical operators for Boolean values: `and`, `or`, and `not`.

<br>

### and
> - Syntax: `x and y`
> - Return: `True` if both `x` and `y` are `True`, otherwise `False`.

```python
print(True and True)   # True
print(True and False)  # False
```

```sh
True
False
```

<br>

### or
> - Syntax: `x or y`
> - Return: `True` if either `x` or `y` is `True`, otherwise `False`.

```python
print(True or False)   # True
print(False or False)  # False
```

```sh
True
False
```

<br>

### not
> - Syntax: `not x`
> - Return: `True` if `x` is `False`, and `False` if `x` is `True`.

```python
print(not True)   # False
print(not False)  # True
```

```sh
False
True
```

<br>

---

<br>

## Boolean Methods

> Python provides methods to work with Boolean expressions and conversions.

<br>

### bool()
> - Syntax: `bool([value])`
> - Return: `True` or `False`
> - Parameters:
>   - `value`: Optional object to evaluate
> - Info: Converts an object to its Boolean equivalent.

```python
print(bool(1))      # True
print(bool(0))      # False
print(bool("Yes")) # True
```

```sh
True
False
True
```

<br>

### isinstance()
> - Syntax: `isinstance(object, classinfo)`
> - Return: Boolean
> - Parameters:
>   - `object`: Object to check
>   - `classinfo`: Class or tuple of classes to check against
> - Info: Returns `True` if the object is an instance of the class or tuple of classes.

```python
print(isinstance(True, bool))  # True
print(isinstance(False, bool)) # True
print(isinstance(1, bool))     # False
```

```sh
True
True
False
```

<br>

---

<br>

## Boolean Comparisons

> Comparisons always return a Boolean result: `True` or `False`.

<br>

### Equality and Inequality
> - `==`: Equal to
> - `!=`: Not equal to

```python
print(1 == 1)     # True
print(1 != 2)     # True
print(1 == True)  # True
print(0 == False) # True
```

```sh
True
True
True
True
```

<br>

### Relational Operators
> - `<`, `<=`, `>`, `>=`: Less than, less than or equal, greater than, greater than or equal

```python
print(3 > 2)      # True
print(3 < 2)      # False
print(3 >= 3)     # True
print(2 <= 3)     # True
```

```sh
True
False
True
True
```

<br>

---

<br>

## Boolean Use Cases

> Booleans are widely used in conditional statements, loops, and expressions.

<br>

### Conditional Statements

```python
if True:
    print("This will always execute")

if False:
    print("This will never execute")
```

```sh
This will always execute
```

<br>

### Loops with Conditions

```python
counter = 0
while counter < 3:
    print(f"Counter is {counter}")
    counter += 1
```

```sh
Counter is 0
Counter is 1
Counter is 2
```