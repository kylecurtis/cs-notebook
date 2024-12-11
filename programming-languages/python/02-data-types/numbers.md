# Python Numeric Types

> Python provides several built-in numeric types to handle different kinds of numbers and mathematical operations. Each type has its specific use cases and characteristics.

<br>

---

<br>

## Integers (int)

> Integers in Python 3 are unbounded, following the [arbitrary-precision arithmetic](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex) standard.

<br>

### Key Characteristics

> - Whole numbers (positive, negative, or zero)
> - No decimal point
> - Unbounded size (limited only by available memory)
> - Immutable type
> - Support for arbitrary base representation (binary, octal, hexadecimal)

<br>

### Memory Representation

> - Python 3 integers use a variable-length representation
> - Small integers (-5 to 256) are pre-allocated for efficiency
> - Memory usage grows with the magnitude of the number

<br>

---

<br>

### Integer Construction

> Direct assignment is the most common way to create integers:

```python
x = 42
print(x)
```

```sh
42
```

<br>

> Using the int() constructor from string:

```python
print(int("123"))
```

```sh
123
```

<br>

> Using the int() constructor from float (truncates decimal part):

```python
print(int(3.14))
```

```sh
3
```

<br>

> Using the int() constructor from binary string (base 2):

```python
print(int("1010", 2))
```

```sh
10
```

<br>

> Using the int() constructor from octal string (base 8):

```python
print(int("17", 8))
```

```sh
15
```

<br>

> Using the int() constructor from hexadecimal string (base 16):

```python
print(int("1A", 16))
```

```sh
26
```

<br>

---

<br>

### Integer Methods

<br>

#### bit_length()

> - Syntax: `int.bit_length()`
> - Return: `int`
> - Info: Returns the number of bits needed to represent the absolute value of the integer in binary.

```python
x = 123
print(x.bit_length())
```

```sh
7
```

<br>

#### to_bytes()

> - Syntax: `int.to_bytes(length, byteorder, *, signed=False)`
> - Return: `bytes`
> - Info: Returns an array of bytes representing the integer
> - Parameters:
>   - length: Number of bytes to use
>   - byteorder: 'big' or 'little'
>   - signed: Whether to use signed representation

```python
x = 1234
print(x.to_bytes(2, byteorder='big'))
print(x.to_bytes(2, byteorder='little'))
```

```sh
b'\x04\xd2'
b'\xd2\x04'
```

<br>

#### from_bytes()

> - Syntax: `int.from_bytes(bytes, byteorder, *, signed=False)`
> - Return: `int`
> - Info: Class method that constructs an integer from a bytes array
> - Parameters match `to_bytes()`

```python
# 1234 in hex
data = bytes([0x04, 0xd2])

print(int.from_bytes(data, byteorder='big'))
print(int.from_bytes(data, byteorder='little'))
```

```sh
1234
53764
```

<br>

#### as_integer_ratio()

> - Syntax: `int.as_integer_ratio()`
> - Return: `tuple[int, int]`
> - Info: Returns a pair of integers whose ratio equals the original integer
> - Note: Always returns `(n, 1)` for integers

```python
x = 123
num, den = x.as_integer_ratio()
print(f"Numerator: {num}, Denominator: {den}")
```

```sh
Numerator: 123, Denominator: 1
```

<br>

---

<br>

### Integer Base Representations

<br>

#### bin() - Binary Representation

> - Syntax: `bin(x)`
> - Return: `str`
> - Info: Returns the binary string representation with prefix '0b'

```python
x = 123
print(bin(x))
print(format(x, 'b'))  # without '0b' prefix
```

```sh
0b1111011
1111011
```

<br>

#### oct() - Octal Representation

> - Syntax: `oct(x)`
> - Return: `str`
> - Info: Returns the octal string representation with prefix '0o'

```python
x = 123
print(oct(x))
print(format(x, 'o'))  # without '0o' prefix
```

```sh
0o173
173
```

<br>

#### hex() - Hexadecimal Representation

> - Syntax: `hex(x)`
> - Return: `str`
> - Info: Returns the hexadecimal string representation with prefix '0x'

```python
x = 123
print(hex(x))
print(format(x, 'x'))  # without '0x' prefix
print(format(x, 'X'))  # uppercase
```

```sh
0x7b
7b
7B
```

<br>

---

<br>

### Integer Operations and Limitations

Integer operations in Python 3 have the following characteristics:

> - No overflow for basic arithmetic (limited only by memory)
> - Floor division with `//` operator
> - True division with `/` operator always returns float
> - Bitwise operations supported
> - [PEP 238](https://peps.python.org/pep-0238/) defines division behavior

```python
# Large integer arithmetic
print(2 ** 100)
```

```sh
1267650600228229401496703205376
```

<br>

> Division operations:

```python
print(7 // 3)  # Floor division
print(7 / 3)   # True division
```

```sh
2
2.3333333333333335
```

<br>

---

<br>

## Floating-Point Numbers (float)

> Python implements floating-point numbers following the [IEEE 754](https://standards.ieee.org/ieee/754/6210/) double-precision format.

<br>

### Key Characteristics

> - Uses 64 bits for storage (double precision)
> - 53 bits for precision (approximately 15-17 decimal digits)
> - Range: $\pm 2.23 \times 10^{-308}$ to $\pm 1.80 \times 10^{308}$
> - Special values: `inf`, `-inf`, `nan`
> - Subject to floating-point arithmetic limitations

<br>

### Memory Layout (IEEE 754)

> The 64-bit double-precision format consists of:
>
> - 1 bit for sign
> - 11 bits for exponent
> - 52 bits for mantissa (significand)

<br>

---

<br>

### Float Construction

> Direct assignment creates float values:

```python
x = 3.14
print(x)
```

```sh
3.14
```

<br>

> Scientific notation:

```python
y = 2.5e-3  # 2.5 × 10^-3
print(y)
```

```sh
0.0025
```

<br>

> Using the float() constructor from string:

```python
print(float("3.14"))
```

```sh
3.14
```

<br>

> Using the float() constructor from integer:

```python
print(float(42))
```

```sh
42.0
```

<br>

---

<br>

### Special Values

> IEEE 754 defines special floating-point values:

<br>

> Infinity:

```python
pos_inf = float('inf')
neg_inf = float('-inf')
print(f"Positive infinity: {pos_inf}")
print(f"Negative infinity: {neg_inf}")
```

```sh
Positive infinity: inf
Negative infinity: -inf
```

<br>

> Not a Number (NaN):

```python
# Not a Number (NaN)
nan = float('nan')
print(f"NaN: {nan}")
print(f"Is NaN equal to itself? {nan == nan}")  # Always False
```

```sh
NaN: nan
Is NaN equal to itself? False
```

<br>

---

<br>

### Float Methods

<br>

#### as_integer_ratio()

> - Syntax: `float.as_integer_ratio()`
> - Return: `tuple[int, int]`
> - Info: Returns a pair of integers whose ratio exactly equals the float
> - Note: Raises `OverflowError` for `inf`/`nan`

```python
x = 3.14
num, den = x.as_integer_ratio()
print(f"Numerator: {num}")
print(f"Denominator: {den}")
print(f"Verification: {num/den}")
```

```sh
Numerator: 7070651414971679
Denominator: 2251799813685248
Verification: 3.14
```

<br>

#### hex()

> - Syntax: `float.hex()`
> - Return: `str`
> - Info: Returns a hexadecimal string representation of the float
> - Note: Preserves exact values (no precision loss)

```python
x = 3.14
hex_str = x.hex()
print(f"Hex representation: {hex_str}")
```

```sh
Hex representation: 0x1.91eb851eb851fp+1
```

<br>

#### fromhex()

> - Syntax: `float.fromhex(string)`
> - Return: `float`
> - Info: Class method that constructs a float from a hexadecimal string
> - Note: Provides exact conversion (no precision loss)

```python
hex_str = '0x1.91eb851eb851fp+1'

x = float.fromhex(hex_str)
print(f"Value from hex: {x}")
```

```sh
Value from hex: 3.14
```

<br>

#### is_integer()

> - Syntax: `float.is_integer()`
> - Return: `bool`
> - Info: Returns True if the float is integral (has no fractional part)

```python
print(3.0.is_integer())
print(3.14.is_integer())
```

```sh
True
False
```

<br>

---

<br>

### Floating-Point Precision

> Floating-point arithmetic follows IEEE 754 rules and has inherent limitations:

```python
# Classic floating-point precision example
x = 0.1 + 0.2
print(f"0.1 + 0.2 = {x}")
print(f"Is 0.1 + 0.2 == 0.3? {x == 0.3}")
```

```sh
0.1 + 0.2 = 0.30000000000000004
Is 0.1 + 0.2 == 0.3? False
```

<br>

#### Best practices for floating-point comparisons

<br>

> Using round() for comparison
>
> - Syntax: `round(number, ndigits)`

```python
x = 0.1 + 0.2
print(f"Rounded comparison: {round(x, 10) == round(0.3, 10)}")
```

```sh
Rounded comparison: True
```

<br>

> Using absolute difference for comparison

```python
def isclose(a, b, rel_tol=1e-9):
    return abs(a-b) <= rel_tol * max(abs(a), abs(b))

print(f"Is close comparison: {isclose(0.1 + 0.2, 0.3)}")
```

```sh
Is close comparison: True
```

<br>

---

<br>

## Complex Numbers

> Python provides built-in support for complex numbers, which represent numbers with both real and imaginary components in the form $a + bi$ where $i$ is the imaginary unit (√-1).

<br>

### Key Characteristics

> - Written as `real + imagj` (or `real + imagJ`)
> - Both real and imaginary parts stored as floats
> - Immutable type
> - Supports all standard complex arithmetic operations
> - Follows [mathematical complex number rules](https://docs.python.org/3/library/cmath.html)

<br>

---

<br>

### Complex Number Construction

> Direct assignment using the 'j' notation:

```python
z1 = 3 + 4j
print(z1)
```

```sh
(3+4j)
```

<br>

> Using the complex() constructor from real and imaginary parts:

```python
z2 = complex(3, 4)
print(z2)
```

```sh
(3+4j)
```

<br>

> Using the complex() constructor from string:

```python
z3 = complex("3+4j")
print(z3)
```

```sh
(3+4j)
```

<br>

---

<br>

### Properties

<br>

#### real

> - Syntax: `complex.real`
> - Return: `float`
> - Info: Returns the real part of the complex number

```python
z = 3 + 4j
print(f"Real part: {z.real}")
```

```sh
Real part: 3.0
```

<br>

#### imag

> - Syntax: `complex.imag`
> - Return: `float`
> - Info: Returns the imaginary part of the complex number

```python
z = 3 + 4j
print(f"Imaginary part: {z.imag}")
```

```sh
Imaginary part: 4.0
```

<br>

---

<br>

### Complex Number Methods

<br>

#### conjugate()

> - Syntax: `complex.conjugate()`
> - Return: `complex`
> - Info: Returns the complex conjugate (real part unchanged, imaginary part negated)
> - Mathematical form: For $z = a + bi$, returns $z* = a - bi$

```python
z = 3 + 4j
print(f"Original number: {z}")
print(f"Conjugate: {z.conjugate()}")
```

```sh
Original number: (3+4j)
Conjugate: (3-4j)
```

<br>

---

<br>

### Complex Operations

<br>

> Complex numbers support all standard arithmetic operations:

```python
z1 = 1 + 2j
z2 = 3 + 4j

# Addition
print(f"Addition: {z1 + z2}")

# Multiplication
print(f"Multiplication: {z1 * z2}")

# Division
print(f"Division: {z1 / z2}")
```

```sh
Addition: (4+6j)
Multiplication: (-5+10j)
Division: (0.44+0.08j)
```

<br>

---

<br>

### Built-in Functions with Complex Numbers

<br>

#### abs()

> - Syntax: `abs(complex)`
> - Return: `float`
> - Info: Returns the magnitude (modulus) of the complex number
> - Mathematical form: For $z = a + bi$, returns $\sqrt{a^2 + b^2}$

```python
z = 3 + 4j
print(f"Magnitude: {abs(z)}")
```

```sh
Magnitude: 5.0
```

<br>

#### pow()

> - Syntax: `pow(complex, exponent)`
> - Return: `complex`
> - Info: Returns the complex number raised to a power
> - Note: Works with any real or complex exponent

```python
z = 1 + 1j  # 45-degree angle
print(f"Square: {pow(z, 2)}")
```

```sh
Square: (0+2j)
```

<br>

---

<br>

### Special Cases and Common Pitfalls

> Complex numbers have some special behaviors to be aware of:

```python
# Imaginary unit squared
print(f"i^2: {1j * 1j}")
```

```sh
i^2: (-1+0j)
```

<br>

> No direct comparison operators

```python
z1 = 1 + 2j
z2 = 1 + 2j
print(f"Equality comparison: {z1 == z2}")  # This works

try:
    print(z1 < z2)  # This raises an error
except TypeError as e:
    print(f"Error: {e}")
```

```sh
Equality comparison: True
Error: '<' not supported between instances of 'complex' and 'complex'
```

<br>

---

<br>

## Decimal Numbers

> The `Decimal` class provides exact decimal arithmetic with configurable precision, following the [General Decimal Arithmetic Specification](http://speleotrove.com/decimal/).

<br>

### Key Characteristics

> - Exact decimal representation
> - Configurable precision
> - No floating-point rounding errors
> - Ideal for financial calculations
> - Slower than float operations
> - Implements [IEEE 754-2019](https://standards.ieee.org/ieee/754/6210/) decimal arithmetic

<br>

### Decimal Setup

> Import and configure the Decimal system:

```python
from decimal import Decimal, getcontext

# Configure precision (default is 28)
getcontext().prec = 28
print(f"Current precision: {getcontext().prec}")
```

```sh
Current precision: 28
```

<br>

---

<br>

### Decimal Construction

> Using the Decimal() constructor from string (preferred method):

```python
d1 = Decimal('3.14')
print(f"From string: {d1}")
```

```sh
From string: 3.14
```

<br>

> Using the Decimal() constructor from integer:

```python
d2 = Decimal(5)
print(f"From integer: {d2}")
```

```sh
From integer: 5
```

<br>

> Using the Decimal() constructor from tuple (sign, digits, exponent):

```python
d3 = Decimal((0, (3, 1, 4), -2))  # 3.14
print(f"From tuple: {d3}")
```

```sh
From tuple: 3.14
```

<br>

---

<br>

### Warning about float conversion

> From float (not recommended due to precision issues)

```python
float_num = 0.1 + 0.2
dec_from_float = Decimal(float_num)
dec_from_string = Decimal('0.1') + Decimal('0.2')

print(f"From float: {dec_from_float}")
print(f"From string: {dec_from_string}")
```

```sh
From float: 0.3000000000000000444089209850
From string: 0.3
```

<br>

---

<br>

### Decimal Methods

<br>

#### adjusted()

> - Syntax: `Decimal.adjusted()`
> - Return: `int`
> - Info: Returns the adjusted exponent of the number
> - Formula: Returns `exp + len(digits) - 1`

```python
x = Decimal('123.45')
print(f"Number: {x}")
print(f"Adjusted exponent: {x.adjusted()}")
```

```sh
Number: 123.45
Adjusted exponent: 2
```

<br>

#### as_integer_ratio()

> - Syntax: `Decimal.as_integer_ratio()`
> - Return: `tuple[int, int]`
> - Info: Returns numerator and denominator of the rational representation
> - Availability: Python 3.11+

```python
x = Decimal('3.14')
num, den = x.as_integer_ratio()
print(f"Numerator: {num}")
print(f"Denominator: {den}")
```

```sh
Numerator: 157
Denominator: 50
```

<br>

#### as_tuple()

> - Syntax: `Decimal.as_tuple()`
> - Return: `DecimalTuple`
> - Info: Returns named tuple with sign, digits, and exponent

```python
x = Decimal('123.45')
tup = x.as_tuple()
print(f"Sign: {tup.sign}")
print(f"Digits: {tup.digits}")
print(f"Exponent: {tup.exponent}")
```

```sh
Sign: 0
Digits: (1, 2, 3, 4, 5)
Exponent: -2
```

<br>

#### compare()

> - Syntax: `Decimal.compare(other)`
> - Return: `Decimal`
> - Info: Returns -1 for less than, 0 for equal, 1 for greater than
> - Note: Similar to `__cmp__` in older Python versions

```python
x = Decimal('3.14')
y = Decimal('2.71')
print(f"Comparing {x} and {y}: {x.compare(y)}")
```

```sh
Comparing 3.14 and 2.71: 1
```

<br>

#### normalize()

> - Syntax: `Decimal.normalize()`
> - Return: `Decimal`
> - Info: Removes trailing zeros, normalizes scientific notation

```python
x = Decimal('123.45000')
print(f"Original: {x}")
print(f"Normalized: {x.normalize()}")
```

```sh
Original: 123.45000
Normalized: 123.45
```

<br>

#### quantize()

> - Syntax: `Decimal.quantize(exp, rounding=None)`
> - Return: `Decimal`
> - Info: Returns a value with exponent matching the given exponent
> - Use: Common for rounding to specific decimal places

```python
x = Decimal('3.14159')
rounded = x.quantize(Decimal('0.01'))
print(f"Original: {x}")
print(f"Rounded to 2 decimal places: {rounded}")
```

```sh
Original: 3.14159
Rounded to 2 decimal places: 3.14
```

<br>

---

<br>

### Decimal Context Settings

> The decimal module provides context management for:
>
> - Precision control
> - Rounding methods
> - Error handling

```python
from decimal import getcontext, ROUND_HALF_UP

# Set precision and rounding
getcontext().prec = 4
getcontext().rounding = ROUND_HALF_UP

x = Decimal('1') / Decimal('3')
print(f"1/3 with precision 4: {x}")
```

```sh
1/3 with precision 4: 0.3333
```

<br>

---

<br>

## Fraction Numbers

> The `Fraction` class represents exact rational numbers as the ratio of two integers, providing exact arithmetic operations without floating-point errors.

<br>

### Key Characteristics

> - Represents numbers as ratio of integers (numerator/denominator)
> - Automatically reduces to lowest terms
> - Exact arithmetic with no rounding errors
> - Ideal for rational number calculations
> - Part of the standard library `fractions` module
> - Slower than float operations for large numbers

<br>

### Fraction Construction

> Creating Fraction objects using different methods:

```python
from fractions import Fraction

# From numerator and denominator
f1 = Fraction(3, 4)
print(f"From integers: {f1}")
```

```sh
From integers: 3/4
```

<br>

```python
# From string
f2 = Fraction('3.14159')
print(f"From decimal string: {f2}")
```

```sh
From decimal string: 314159/100000
```

<br>

```python
# From another number type
from decimal import Decimal
f3 = Fraction(Decimal('1.1'))
print(f"From Decimal: {f3}")
```

```sh
From Decimal: 11/10
```

<br>

---

<br>

### Class Methods

<br>

#### from_float()

> - Syntax: `Fraction.from_float(flt)`
> - Return: `Fraction`
> - Info: Creates a Fraction from a float value
> - Note: May give unexpected results due to float representation

```python
x = 3.14159
f = Fraction.from_float(x)
print(f"Float: {x}")
print(f"Fraction: {f}")
print(f"Decimal form: {float(f)}")
```

```sh
Float: 3.14159
Fraction: 7074237752028440/2251799813685248
Decimal form: 3.14159
```

<br>

#### from_decimal()

> - Syntax: `Fraction.from_decimal(dec)`
> - Return: `Fraction`
> - Info: Creates a Fraction from a Decimal object
> - Note: Preserves exact decimal representation

```python
d = Decimal('3.14')
f = Fraction.from_decimal(d)
print(f"Decimal: {d}")
print(f"Fraction: {f}")
```

```sh
Decimal: 3.14
Fraction: 157/50
```

<br>

---

<br>

### Instance Methods

<br>

#### limit_denominator()

> - Syntax: `Fraction.limit_denominator(max_denominator=1000000)`
> - Return: `Fraction`
> - Info: Returns the closest Fraction with denominator no larger than max_denominator
> - Use: Approximating irrational numbers

```python
# Approximating π
from math import pi
f = Fraction.from_float(pi).limit_denominator(100)
print(f"π ≈ {f}")
print(f"Decimal form: {float(f)}")
print(f"Actual π: {pi}")
```

```sh
π ≈ 22/7
Decimal form: 3.142857142857143
Actual π: 3.141592653589793
```

<br>

---

<br>

### Properties

<br>

#### numerator

> - Syntax: `Fraction.numerator`
> - Return: `int`
> - Info: Returns the numerator of the fraction in lowest terms

```python
f = Fraction('3.14')
print(f"Fraction: {f}")
print(f"Numerator: {f.numerator}")
```

```sh
Fraction: 157/50
Numerator: 157
```

<br>

#### denominator

> - Syntax: `Fraction.denominator`
> - Return: `int`
> - Info: Returns the denominator of the fraction in lowest terms

```python
f = Fraction('3.14')
print(f"Fraction: {f}")
print(f"Denominator: {f.denominator}")
```

```sh
Fraction: 157/50
Denominator: 50
```

<br>

---

<br>

### Arithmetic Operations

> Fractions support all standard arithmetic operations with exact results:

```python
f1 = Fraction(1, 3)
f2 = Fraction(1, 6)

# Addition
print(f"Addition: {f1} + {f2} = {f1 + f2}")

# Multiplication
print(f"Multiplication: {f1} × {f2} = {f1 * f2}")

# Division
print(f"Division: {f1} ÷ {f2} = {f1 / f2}")
```

```sh
Addition: 1/3 + 1/6 = 1/2
Multiplication: 1/3 × 1/6 = 1/18
Division: 1/3 ÷ 1/6 = 2
```

<br>

---

<br>

### Type Conversions

> Converting between Fraction and other numeric types:

```python
f = Fraction(22, 7)  # Approximation of π

# To float
print(f"Float: {float(f)}")

# To Decimal
print(f"Decimal: {Decimal(f.numerator) / Decimal(f.denominator)}")
```

```sh
Float: 3.142857142857143
Decimal: 3.142857142857142857142857143
```
