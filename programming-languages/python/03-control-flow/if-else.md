---
tags:
- control-flow
---

<br>

> The `if-else` statement in Python is a fundamental control flow construct used to execute code conditionally. It allows your program to make decisions based on specified conditions.

<br>

---

<br>

## Basic if Statement

> The `if` statement executes a block of code if the given condition evaluates to `True`.

<br>

```python
if condition:
    # Code to execute if condition is True
```

<br>

### Example

```python
x = 10

if x > 5:
    print("x is greater than 5")
```

```sh
x is greater than 5
```

<br>

---

<br>

## if-else Statement

> The `else` block executes when the condition in the `if` statement evaluates to `False`.

<br>

```python
if condition:
    # Code to execute if condition is True
else:
    # Code to execute if condition is False
```

### Example

```python
x = 3

if x > 5:
    print("x is greater than 5")
else:
    print("x is less than or equal to 5")
```

```sh
x is less than or equal to 5
```

<br>

---

<br>

## if-elif-else Statement

> The `elif` block allows multiple conditions to be tested sequentially. The first condition that evaluates to `True` executes, and the rest are skipped.

<br>

```python
if condition1:
    # Code to execute if condition1 is True
elif condition2:
    # Code to execute if condition2 is True
else:
    # Code to execute if none of the above conditions are True
```

### Example

```python
x = 7

if x < 5:
    print("x is less than 5")
elif x == 5:
    print("x is equal to 5")
else:
    print("x is greater than 5")
```

```sh
x is greater than 5
```

<br>

---

<br>

## Nested if-else Statements

> An `if-else` statement can be nested within another `if` or `else` block for more complex decision-making.

<br>

### Example

```python
x = 10

if x > 5:
    if x % 2 == 0:
        print("x is greater than 5 and even")
    else:
        print("x is greater than 5 and odd")
else:
    print("x is less than or equal to 5")
```

```sh
x is greater than 5 and even
```

<br>

---

<br>

## Ternary if-else Statements

> A shorthand for simple `if-else` conditions using a single line.

<br>

```python
value = true_value if condition else false_value
```

### Example

```python
x = 10

result = "Even" if x % 2 == 0 else "Odd"
print(result)
```

```sh
Even
```

<br>

---

<br>

## Examples and Use Cases

<br>

### Example 1: Checking Age

```python
age = 20

if age >= 18:
    print("You are eligible to vote.")
else:
    print("You are not eligible to vote.")
```

```sh
You are eligible to vote.
```

<br>

### Example 2: Grading System

```python
marks = 85
if marks >= 90:
    print("Grade: A")
elif marks >= 75:
    print("Grade: B")
else:
    print("Grade: C")
```

```sh
Grade: B
```

<br>

### Example 3: Default Value with Ternary Operator

```python
username = None
display_name = username if username else "Guest"
print(display_name)
```

```sh
Guest
```

<br>

---

<br>

## Key Points to Remember

1. The `if-else` construct allows conditional execution of code.
2. `elif` lets you handle multiple conditions sequentially.
3. Only the first condition that evaluates to `True` is executed.
4. Ternary `if-else` statements offer a concise way to write simple conditions.