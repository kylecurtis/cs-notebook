# Python Exceptions (Error Handling)

> Exceptions in Python provide a way to handle errors and exceptional conditions gracefully during program execution.

<br>

### Key Characteristics

> - Built-in mechanism for handling runtime errors
> - Prevents program crashes
> - Supports custom exception creation
> - Hierarchical exception model
> - Context management for resource cleanup

<br>

---

<br>

## Try-Except Blocks

> The `try-except` construct allows for handling exceptions that might occur in a block of code.

```python
try:
    x = 1 / 0  # Raises ZeroDivisionError
except ZeroDivisionError as e:
    print(f"Error: {e}")
```

```sh
Error: division by zero
```

<br>

### Optional Else and Finally
> - `else`: Executes if no exceptions are raised.
> - `finally`: Executes always, for cleanup actions.

```python
try:
    x = 10 / 2
except ZeroDivisionError:
    print("Cannot divide by zero!")
else:
    print("Division successful")
finally:
    print("Execution complete")
```

```sh
Division successful
Execution complete
```

<br>

---

<br>

## Exception Hierarchy

> Python exceptions are organized in a hierarchical manner, with `BaseException` as the root.

### Common Built-in Exceptions

| **Exception**         | **Description**                           |
|-----------------------|-------------------------------------------|
| `ValueError`          | Invalid value provided                   |
| `TypeError`           | Operation applied to incompatible types  |
| `IndexError`          | Invalid index for a sequence             |
| `KeyError`            | Missing key in a dictionary              |
| `ZeroDivisionError`   | Division by zero                         |
| `FileNotFoundError`   | File or directory not found              |

```python
try:
    lst = [1, 2, 3]
    print(lst[5])  # Raises IndexError
except IndexError as e:
    print(f"Caught an exception: {e}")
```

```sh
Caught an exception: list index out of range
```

<br>

---

<br>

## Custom Exceptions

> You can define custom exceptions by subclassing the `Exception` class.

```python
class CustomError(Exception):
    def __init__(self, message):
        self.message = message
        super().__init__(self.message)

try:
    raise CustomError("This is a custom error")
except CustomError as e:
    print(f"Caught: {e}")
```

```sh
Caught: This is a custom error
```

<br>

---

<br>

## Raising Exceptions

> Use the `raise` keyword to explicitly raise an exception.

```python
try:
    raise ValueError("Invalid value provided")
except ValueError as e:
    print(f"Error: {e}")
```

```sh
Error: Invalid value provided
```

### Raising Exceptions with Arguments

```python
try:
    raise KeyError("Missing key in dictionary")
except KeyError as e:
    print(f"Error: {e}")
```

```sh
Error: 'Missing key in dictionary'
```

<br>

---

<br>

## Exception Chaining

> Chaining allows linking exceptions using the `from` keyword.

```python
try:
    try:
        x = 1 / 0
    except ZeroDivisionError as e:
        raise ValueError("Invalid calculation") from e
except ValueError as e:
    print(f"Error: {e}")
    print(f"Original exception: {e.__cause__}")
```

```sh
Error: Invalid calculation
Original exception: division by zero
```

<br>

---

<br>

## Context Managers

> Context managers simplify resource management, often used with the `with` statement.

```python
with open("file.txt", "w") as f:
    f.write("Hello, world!")
```

### Custom Context Managers
> Create custom context managers using the `__enter__` and `__exit__` methods.

```python
class MyContext:
    def __enter__(self):
        print("Entering context")
        return self

    def __exit__(self, exc_type, exc_value, traceback):
        print("Exiting context")

with MyContext() as ctx:
    print("Inside context")
```

```sh
Entering context
Inside context
Exiting context
```

<br>

---

<br>

## Cleanup Actions

> Cleanup actions can be ensured using `finally` or context managers.

### Using `finally`

```python
try:
    print("Opening resource")
    raise RuntimeError("Unexpected error")
finally:
    print("Closing resource")
```

```sh
Opening resource
Closing resource
Traceback (most recent call last):
  ...
RuntimeError: Unexpected error
```

### Using Context Managers for Cleanup

```python
class Resource:
    def __enter__(self):
        print("Acquiring resource")
        return self

    def __exit__(self, exc_type, exc_value, traceback):
        print("Releasing resource")

with Resource() as r:
    print("Using resource")
```

```sh
Acquiring resource
Using resource
Releasing resource
```

