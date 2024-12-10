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
