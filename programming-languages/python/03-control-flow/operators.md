---
tags:
- control-flow
---

<br>

> Operators in Python are symbols or keywords used to perform operations on variables and values. Python provides various types of operators to handle arithmetic, comparison, logical operations, and more.

<br>

---

<br>

## Types of Operators in Python

> - Arithmetic Operators
> - Comparison (Relational) Operators
> - Logical Operators
> - Bitwise Operators
> - Assignment Operators
> - Identity Operators
> - Membership Operators

<br>

---

<br>

## Arithmetic Operators

> Used to perform mathematical operations like addition, subtraction, multiplication, etc.

| Operator | Description         | Example  | Output |
| :------: | ------------------- | :------: | :----: |
|    +     | Addition            |  3 + 2   |   5    |
|    -     | Subtraction         |  5 - 3   |   2    |
|    \*    | Multiplication      |  4 \* 3  |   12   |
|    /     | Division            |  10 / 2  |  5.0   |
|    //    | Floor Division      | 10 // 3  |   3    |
|    %     | Modulus (Remainder) |  10 % 3  |   1    |
|   \*\*   | Exponentiation      | 2 \*\* 3 |   8    |

<br>

### Example

```python
a, b = 10, 3

# Arithmetic Operators
num_1 = (a + b)
num_2 = (a - b)
num_3 = (a * b)
num_4 = (a / b)
num_5 = (a // b)
num_6 = (a % b)
num_7 = (a ** b)

# Result
print(num_1, num_2, num_3, num_4, num_5, num_6, num_7)
```

```sh
13 7 30 3.3333333333333335 3 1 1000
```

<br>

---

<br>

## Comparison (Relational) Operators

> Used to compare two values and return a boolean result (`True` or `False`).

| Operator | Description           | Example | Output |
| :------: | --------------------- | :-----: | :----: |
|    ==    | Equal to              | 5 == 5  |  True  |
|    !=    | Not equal to          | 5 != 3  |  True  |
|    >     | Greater than          | 10 > 5  |  True  |
|    <     | Less than             |  5 < 3  | False  |
|    >=    | Greater than or equal | 5 >= 5  |  True  |
|    <=    | Less than or equal    | 3 <= 4  |  True  |

<br>

### Example

```python
x, y = 7, 10

# Comparison Operators
bool_1 = (x == y)
bool_2 = (x != y)
bool_3 = (x > y)
bool_4 = (x < y)
bool_5 = (x >= y)
bool_6 = (x <= y)

# Result
print(bool_1, bool_2, bool_3, bool_4, bool_5, bool_6)
```

```sh
False True False True False True
```

<br>

---

<br>

## Logical Operators

> Used to combine conditional statements.

| Operator | Description                                    | Example          | Output |
| :------: | ---------------------------------------------- | ---------------- | :----: |
|   and    | Returns True if both conditions are true       | 5 > 3 and 10 > 5 |  True  |
|    or    | Returns True if at least one condition is true | 5 > 3 or 10 < 5  |  True  |
|   not    | Reverses the result                            | not(5 > 3)       | False  |

<br>

### Example

```python
a, b = 5, 10

# Logical Operators
print(a > 3 and b > 8)
print(a < 5 or b > 5)
print(not (a > b))
```

```sh
True True True
```

<br>

---

<br>

## Bitwise Operators

> Used to perform operations on binary numbers.

| Operator | Description | Example | Output |
| :------: | ----------- | :-----: | :----: |
|    &     | Bitwise AND |  5 & 3  |   1    |
|    \|    | Bitwise OR  | 5 \| 3  |   7    |
|    ^     | Bitwise XOR |  5 ^ 3  |   6    |
|    ~     | Bitwise NOT |   ~5    |   -6   |
|    <<    | Left Shift  | 5 << 1  |   10   |
|    >>    | Right Shift | 5 >> 1  |   2    |

<br>

### Example

```python
a, b = 5, 3

# Bitwise Operators
and_op = (a & b)
or_op = (a | b)
xor_op = (a ^ b)
not_op = (~a)
left_shift = (a << b)
right_shift = (a >> b)

# Result
print(and_op, or_op, xor_op, not_op, left_shift, right_shift)
```

```sh
1 7 6 -6 40 0
```

<br>

---

<br>

## Assignment Operators

> Used to assign values to variables.

| Operator | Description             | Example   | Output       |
| :------: | ----------------------- | --------- | ------------ |
|    =     | Assign                  | x = 5     | x = 5        |
|    +=    | Add and assign          | x += 3    | x = x + 3    |
|    -=    | Subtract and assign     | x -= 2    | x = x - 2    |
|   \*=    | Multiply and assign     | x \*= 4   | x = x \* 4   |
|    /=    | Divide and assign       | x /= 5    | x = x / 5    |
|   //=    | Floor divide and assign | x //= 3   | x = x // 3   |
|    %=    | Modulus and assign      | x %= 2    | x = x % 2    |
|  \*\*=   | Exponent and assign     | x \*\*= 3 | x = x \*\* 3 |
|    &=    | Bitwise AND and assign  | x &= 3    | x = x & 3    |
|   \|=    | Bitwise OR and assign   | x \|= 3   | x = x \| 3   |
|    ^=    | Bitwise XOR and assign  | x ^= 2    | x = x ^ 2    |
|   >>=    | Right shift and assign  | x >>= 1   | x = x >> 1   |
|   <<=    | Left shift and assign   | x <<= 1   | x = x << 1   |

<br>

### Example

```python
a = 5; print(a)
a += 5; print(a)
a -= 5; print(a)
a *= 5; print(a)
a /= 5; print(a)

a = int(a)  # reset back to int

a //= 5; print(a)
a %= 5; print(a)
a **= 5; print(a)
a &= 5; print(a)
a |= 5; print(a)
a ^= 5; print(a)
a >>= 5; print(a)
a <<= 5; print(a)
```

```sh
5 10 5 25 5.0 1 1 1 1 5 0 0 0
```

<br>

---

<br>

## Identity Operators

> Used to compare the identity of two objects.

| Operator | Description                                                 | Example    | Output     |
| -------- | ----------------------------------------------------------- | ---------- | ---------- |
| is       | Returns `True` if two variables reference the same object   | x is y     | True/False |
| is not   | Returns `True` if two variables reference different objects | x is not y | True/False |

<br>

### Example

```python
x = [1, 2, 3]
y = x
z = [1, 2, 3]

print(x is y)
print(x is z)
print(x is not z)
```

```sh
True False True
```

<br>

---

<br>

## Membership Operators

> Used to test whether a value is a member of a sequence (e.g., list, string).

| Operator | Description                                          | Example            | Output |
| -------- | ---------------------------------------------------- | ------------------ | :----: |
| in       | Returns `True` if a value is found in a sequence     | "a" in "apple"     |  True  |
| not in   | Returns `True` if a value is not found in a sequence | "z" not in "apple" |  True  |

<br>

### Example

```python
fruits = ["apple", "banana", "cherry"]

print("apple" in fruits)
print("grape" not in fruits)
```

```sh
True True
```

<br>

---

<br>

## Key Points to Remember

1. Operators enable operations on variables and values.
2. Python supports a rich set of operators, including arithmetic, comparison, logical, and bitwise operators.
3. Membership and identity operators are unique features of Python.
4. Use operators judiciously for concise and readable code.
