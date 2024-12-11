---
tags:
- basics
---

<br>

# Python Variables

> Variables in Python are used to store data values. They are dynamically typed and flexible, making Python both powerful and easy to use.

<br>

### Key Characteristics

> - No explicit declaration required
> - Dynamically typed (type inferred at runtime)
> - Can hold any data type
> - Naming rules and best practices apply
> - Supports type hints for clarity and static analysis
> - Constants and multiple assignments supported

<br>

---

<br>

## Declaring Variables

> Variables are created when you assign a value to them.

```python
# Basic variable assignment
x = 10
name = "Python"
flag = True

print(x)
print(name)
print(flag)
```

```sh
10
Python
True
```

<br>

---

<br>

## Naming Variables

> Variable names must follow certain rules:
> - Must begin with a letter (a–z, A–Z) or an underscore (_).
> - Can contain letters, digits (0–9), and underscores.
> - Cannot start with a number or be separated by spacing.
> - Case-sensitive (`myvar` and `MyVar` are different).
> - Cannot use reserved keywords (e.g., `def`, `class`, `if`).

<br>

### Examples of Valid and Invalid Names

| **Valid Names**   | **Invalid Names** |
|-------------------|-------------------|
| `snake_case`          | `2variable`       |
| `SCREAMING_SNAKE_CASE` | `var name` (no space) |
| `camelCase`       | `class` (keyword) |
| `PascalCase`      | `var@123`         |
| `_private`        | `var-name`        |

<br>

---

<br>

## Dynamic Typing

> Python determines the type of a variable at runtime based on the value assigned.

```python
x = 42         # Integer
y = 3.14       # Float
name = "John"  # String
flag = True    # Boolean

print(type(x))
print(type(y))
print(type(name))
print(type(flag))
```

```sh
<class 'int'>
<class 'float'>
<class 'str'>
<class 'bool'>
```

<br>

> Variables in Python can change types during execution.

```python
value = 10  # int
print(f"{value} is of type {type(value)}")

value = "10"  # str
print(f"{value} is now of type {type(value)}")
```

<br>

---

<br>

## Type Hints

> Type hints provide optional type information to improve code clarity and enable static type checking.
> - Syntax: `<name>: <type> = <value>`

```python
# Type hint for variable
greeting: str = "Hello!"
DAYS_IN_WEEK: int = 7 

print(greeting)
print(DAYS_IN_WEEK)
```

```sh
Hello!
7
```


### Possible Type Hint Values

> Python supports a wide range of type hints, including:

|**Type**|**Description**|
|---|---|
|`int`|Integer values|
|`float`|Floating-point numbers|
|`str`|String values|
|`bool`|Boolean values (`True`, `False`)|
|`list`|List of items|
|`tuple`|Tuple of items|
|`dict`|Dictionary of key-value pairs|
|`set`|Set of unique items|
|`Any`|Any type (from `typing` module)|
|`Union`|Multiple possible types (e.g., `Union[int, str]`)|
|`Optional`|Allows `None` as a valid value (e.g., `Optional[str]`)|
|`Callable`|Represents functions or callable objects|
|`TypeVar`|Represents generic types|
|`Literal`|Specific literal values (e.g., `Literal["yes", "no"]`)|

<br>

### Benefits of Type Hints
> - Helps catch type-related bugs early.
> - Improves code readability and documentation.
> - Supported by tools like `mypy` for static analysis.

<br>

---

<br>

## Multiple Assignments

> Python allows assigning values to multiple variables in a single line.

```python
x, y, z = 1, 2, 3
print(x, y, z)

# Assign the same value to multiple variables
a = b = c = 0
print(a, b, c)
```

```sh
1 2 3
0 0 0
```

<br>

---

<br>

## Constants

> Python does not have built-in constant types, but naming conventions are used to indicate constants.

```python
PI = 3.14159   # Use uppercase names for constants
URL = "https://example.com"

print(PI)
print(URL)
```

```sh
3.14159
https://example.com
```

### Best Practice
> Use constants for values that should not change during program execution.
> 
> While Python does not enforce immutability for constants, developers should treat variables with uppercase names as constants.

<br>

---

<br>

## Best Practices

<br>

### Follow PEP 8 Guidelines
> - Use descriptive names (`total_sum` instead of `ts`).
> - Avoid single-character names, except for temporary variables (`i`, `j`).
> - Use underscores for readability (`user_name`).
> - Keep constants in uppercase (`MAX_LIMIT`).

<br>

### Initialize Before Use
> Ensure variables are initialized before they are accessed.

```python
count = 0
print(count)  # Safe
```

<br>

### Use Type Hints
> Add type hints to improve clarity and avoid errors in large projects.

<br>

---

<br>

## Variable Scope

> The scope of a variable determines where it can be accessed.

<br>

### Local Scope
> Variables declared inside a function are local to that function.

```python
def my_function():
    local_var = 10
    print(local_var)

my_function()
# print(local_var)  # Error: local_var is not accessible here
```

<br>

### Global Scope
> Variables declared outside any function are global.

```python
global_var = 100

def show_global():
    print(global_var)

show_global()
```

```sh
100
```

<br>

---

<br>

## Mutable and Immutable Variables

> Variables in Python can be mutable or immutable based on their type.

| **Immutable Types**  | **Mutable Types**      |
|----------------------|------------------------|
| `int`, `float`, `str`| `list`, `dict`, `set`  |
| `tuple`, `frozenset` | `bytearray`            |

```python
# Immutable example
x = 10
x = x + 1  # Creates a new object

# Mutable example
lst = [1, 2, 3]
lst.append(4)  # Modifies the same object

print(x)
print(lst)
```

```sh
11
[1, 2, 3, 4]
```

