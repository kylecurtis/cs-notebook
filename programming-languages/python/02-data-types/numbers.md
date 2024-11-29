## Introduction

> In Python, numbers are a built-in data type used for mathematical calculations and represent numeric values. Python supports multiple numeric types: integers, floats, and complex numbers.

<br>

---

<br>

## Numeric Types

<br>

### Integers

> Whole numbers without a fractional component.

```python
x = 10
print(x)  # 10
```

<br>

### Floats

> Numbers with a decimal point or in exponential form.

```python
y = 3.14
z = 1.5e2  # Equivalent to 150.0

print(y, z)
```

<br>

### Complex Numbers

> Numbers with a real and imaginary part.

```python
c = 3 + 4j
print(c)
```

<br>

---

<br>

## Arithmetic Operators

Python supports the following arithmetic operations for numbers:

- Addition (`+`)
- Subtraction (`-`)
- Multiplication (`*`)
- Division (`/`)
- Floor Division (`//`)
- Modulus (`%`)
- Exponentiation (`**`)

```python
a = 10 + 5   # 15
b = 10 - 3   # 7
c = 10 * 2   # 20
d = 10 / 3   # 3.333...
e = 10 // 3  # 3
f = 10 % 3   # 1
g = 2 ** 3   # 8

print(a, b, c, d, e, f, g)
```

<br>

---

<br>

## Numeric Methods

<br>

### abs

> Returns the absolute value of a number. Example:

```python
print(abs(-10))  # 10
```

### round

> Rounds a number to the nearest integer or specified number of decimal places. Example:

```python
print(round(3.14159))     # 3
print(round(3.14159, 2))  # 3.14
```

### pow

> Raises a number to a power (equivalent to `**` but supports a modulo). Example:

```python
print(pow(2, 3))     # 8
print(pow(2, 3, 5))  # 3 (2**3 % 5)
```

### divmod

> Returns a tuple containing the quotient and remainder of a division. Example:

```python
print(divmod(10, 3))  # (3, 1)
```

### int.bit_length

> Returns the number of bits required to represent an integer in binary. Example:

```python
x = 10
print(x.bit_length())  # 4 (binary: 1010)
```

### int.to_bytes

> Converts an integer to a byte object of a specified length. Example:

```python
x = 255
print(x.to_bytes(2, byteorder='big'))  # b'\x00\xff'
```

### int.from_bytes

> Converts a byte object to an integer. Example:

```python
b = b'\x00\xff'
print(int.from_bytes(b, byteorder='big'))  # 255
```

### float.is_integer

> Checks if a float represents an integer value. Example:

```python
x = 10.0
print(x.is_integer())  # True

y = 10.5
print(y.is_integer())  # False
```

### float.as_integer_ratio

> Returns a pair of integers whose ratio is exactly equal to the float. Example:

```python
x = 1.5
print(x.as_integer_ratio())  # (3, 2)
```

### float.hex

> Returns the hexadecimal representation of a float. Example:

```python
x = 3.14
print(x.hex())  # '0x1.91eb851eb851fp+1'
```

### float.fromhex

> Converts a hexadecimal string to a float. Example:

```python
hex_val = '0x1.91eb851eb851fp+1'
print(float.fromhex(hex_val))  # 3.14
```

<br>

---

<br>

## Built-In Functions for Numbers

<br>

### max

> Returns the largest number among the inputs. Example:

```python
print(max(1, 2, 3))  # 3
```

<br>

### min

> Returns the smallest number among the inputs. Example:

```python
print(min(1, 2, 3))  # 1
```

<br>

### sum

> Returns the sum of all items in an iterable. Example:

```python
print(sum([1, 2, 3, 4]))  # 10
```

### bin

> Converts an integer to its binary representation as a string. Example:

```python
print(bin(10))  # '0b1010'
```

### oct

> Converts an integer to its octal representation as a string. Example:

```python
print(oct(10))  # '0o12'
```

<br>

### hex

> Converts an integer to its hexadecimal representation as a string. Example:

```python
print(hex(255))  # '0xff'
```

<br>

---

<br>

## Mathematical Constants (from math module)

<br>

### math.pi

> The mathematical constant π (pi). Example:

```python
import math
print(math.pi)  # 3.141592653589793
```

<br>

### math.e

> The mathematical constant e (Euler’s number). Example:

```python
import math
print(math.e)  # 2.718281828459045
```

<br>

---

<br>

## Other Useful Methods and Functions

<br>

### isclose

> Determines whether two numbers are close to each other (with a relative tolerance). Example:

```python
import math
print(math.isclose(1.0001, 1.0002, rel_tol=1e-4))  # True
```

<br>

### math.factorial

> Calculates the factorial of a non-negative integer. Example:

```python
import math
print(math.factorial(5))  # 120
```

<br>

### math.sqrt

> Returns the square root of a number. Example:

```python
import math
print(math.sqrt(16))  # 4.0
```