---
tags:
- data-types
---

<br>

# Python Strings

> Strings in Python are immutable sequences of characters used for storing and manipulating text data. They are one of Python's core data types.

<br>

### Key Characteristics

> - Immutable (cannot be changed after creation)
> - Sequence type (supports indexing and slicing)
> - Unicode support by default
> - Multiple creation methods
> - Rich set of string methods
> - Various formatting options
> - Supports regular expression operations

<br>

---

<br>

## String Creation and Literals

> Python offers several ways to create and define strings, each suited for different use cases.

<br>

### str()
> - Syntax: `str(object='')`
> - Return: String
> - Parameters:
>   - object: The object to convert to a string
> - Info: Creates a string containing a printable representation of an object

```python
# Basic string creation
text = str(123)
print(text)        # "123"

name = str()       # Empty string
print(len(name))   # 0
```

```sh
123
0
```

<br>

### Quote Styles
> - Single quotes: `'text'`
> - Double quotes: `"text"`
> - Triple quotes: `'''text'''` or `"""text"""`
> - Info: All create string objects; choice is mainly stylistic

```python
# Different quote styles
name = 'Alice'          # Single quotes
message = "Hello"       # Double quotes
text = """First line    # Triple quotes
Second line"""

print(name)
print(message)
print(text)
```

```sh
Alice
Hello
First line
Second line
```

<br>

## Escape Characters

> Special characters can be included in strings using escape sequences.

| **Escape Character** | **Description**            | **Example**                 | **Output**                    |
| :------------------: | -------------------------- | --------------------------- | ----------------------------- |
|         `\\`         | Backslash                  | `"This is a backslash: \\"` | `This is a backslash: \`      |
|         `\'`         | Single quote               | `"It\'s Python!"`           | `It's Python!`                |
|         `\"`         | Double quote               | `"She said, \"Hello!\""`    | `She said, "Hello!"`          |
|         `\n`         | New line                   | `"Hello\nWorld!"`           | `Hello`<br>`World!`           |
|         `\t`         | Tab                        | `"Hello\tWorld!"`           | `Hello    World!`             |
|         `\r`         | Carriage return            | `"Hello\rWorld!"`           | `World!`                      |
|         `\b`         | Backspace                  | `"Hello\bWorld!"`           | `HelloWorld!`                 |
|         `\f`         | Form feed                  | `"Hello\fWorld!"`           | `Hello`<form feed>`World!`    |
|         `\v`         | Vertical tab               | `"Hello\vWorld!"`           | `Hello`<vertical tab>`World!` |
|       `\uXXXX`       | Unicode character (16-bit) | `"\u2764"`                  | ❤️ (heart symbol)             |
|     `\UXXXXXXXX`     | Unicode character (32-bit) | `"\U0001F600"`              | 😀 (smiley face)              |
|        `\xXX`        | Hexadecimal character      | `"\x48\x65\x6C\x6C\x6F"`    | `Hello`                       |
|         `\0`         | Null character             | `"Hello\0World!"`           | `HelloWorld!`                 |

<br>

---

<br>

## String Methods

> Python strings provide numerous built-in methods for text manipulation and analysis.

<br>

### Case Methods

#### upper()
> - Syntax: `str.upper()`
> - Return: String
> - Parameters: None
> - Info: Returns a copy of the string with all characters in uppercase

```python
text = "Hello"
print(text.upper())
```

```sh
HELLO
```

<br>

#### lower()
> - Syntax: `str.lower()`
> - Return: String
> - Parameters: None
> - Info: Returns a copy of the string with all characters in lowercase

```python
text = "Hello"
print(text.lower())
```

```sh
hello
```

<br>

#### title()
> - Syntax: `str.title()`
> - Return: String
> - Parameters: None
> - Info: Returns a copy with each word's first character capitalized
> - Note: Uses simple word boundaries, may not work for all cases

```python
text = "hello world"
print(text.title())
```

```sh
Hello World
```

<br>

### Search Methods

#### find()
> - Syntax: `str.find(sub[, start[, end]])`
> - Return: Integer (index or -1 if not found)
> - Parameters:
>   - sub: Substring to find
>   - start: Optional starting position
>   - end: Optional ending position
> - Info: Returns lowest index of substring if found, -1 otherwise

```python
text = "Hello, World"
print(text.find("World"))    # 7
print(text.find("Python"))   # -1
```

```sh
7
-1
```

<br>

#### index()
> - Syntax: `str.index(sub[, start[, end]])`
> - Return: Integer
> - Parameters: Same as find()
> - Info: Like find() but raises ValueError if substring not found
> - Note: Use find() if you don't want to handle exceptions

```python
text = "Hello, World"
try:
    pos = text.index("World")
    print(pos)
except ValueError as e:
    print("Not found")
```

```sh
7
```

<br>

### Modification Methods

#### replace()
> - Syntax: `str.replace(old, new[, count])`
> - Return: String
> - Parameters:
>   - old: String to replace
>   - new: Replacement string
>   - count: Maximum replacements to make
> - Info: Returns copy with all occurrences of substring replaced

```python
text = "hello hello hello"
print(text.replace("hello", "hi"))      # All occurrences
print(text.replace("hello", "hi", 2))   # First two only
```

```sh
hi hi hi
hi hi hello
```

<br>

### Strip Methods

#### strip()
> - Syntax: `str.strip([chars])`
> - Return: String
> - Parameters:
>   - chars: Optional string specifying set of characters to remove
> - Info: Returns copy with leading and trailing characters removed
> - Note: Removes whitespace if no chars parameter specified

```python
text = "   Hello   "
print(text.strip())         # Remove whitespace
text = "...Hello..."
print(text.strip('.'))      # Remove dots
```

```sh
Hello
Hello
```

<br>

### Split and Join

#### split()
> - Syntax: `str.split(sep=None, maxsplit=-1)`
> - Return: List of strings
> - Parameters:
>   - sep: Separator to split on (whitespace if None)
>   - maxsplit: Maximum number of splits to perform
> - Info: Splits string into list based on separator

```python
text = "apple,banana,orange"
print(text.split(','))

sentence = "Hello    World"
print(sentence.split())  # Splits on whitespace
```

```sh
['apple', 'banana', 'orange']
['Hello', 'World']
```

<br>

### Validation Methods

#### isdigit()
> - Syntax: `str.isdigit()`
> - Return: Boolean
> - Parameters: None
> - Info: Returns True if all characters are digits
> - Note: Only recognizes decimal digits

```python
print("123".isdigit())    # Numbers only
print("12.3".isdigit())   # Decimal point
print("12a".isdigit())    # Letter included
```

```sh
True
False
False
```

<br>

#### isalpha()
> - Syntax: `str.isalpha()`
> - Return: Boolean
> - Parameters: None
> - Info: Returns True if all characters are alphabetic
> - Note: No spaces or numbers allowed for True result

```python
print("Hello".isalpha())      # Letters only
print("Hello123".isalpha())   # With numbers
print("Hello World".isalpha()) # With space
```

```sh
True
False
False
```

<br>

#### isalnum()
> - Syntax: `str.isalnum()`
> - Return: Boolean
> - Parameters: None
> - Info: Returns True if all characters are alphanumeric
> - Note: No spaces or special characters allowed for True result

```python
print("Hello123".isalnum())    # Letters and numbers
print("Hello!".isalnum())      # Special character
print("Hello World".isalnum()) # Space included
```

```sh
True
False
False
```

<br>

---

<br>

## String Formatting

> Python provides three main ways to format strings: %-formatting (old style), str.format() method, and f-strings (formatted string literals).

<br>

### %-formatting (Old Style)
> - Syntax: `"format_string" % values`
> - Return: String
> - Common specifiers:
>   - %s: String
>   - %d: Integer
>   - %f: Float
>   - %x: Hexadecimal
> - Info: Original Python string formatting method

```python
name = "Alice"
age = 25
print("Name: %s, Age: %d" % (name, age))

price = 19.99
print("Price: $%.2f" % price)
```

```sh
Name: Alice, Age: 25
Price: $19.99
```

<br>

### str.format()
> - Syntax: `"string".format(*args, **kwargs)`
> - Return: String
> - Features:
>   - Positional arguments: `{0}, {1}`
>   - Keyword arguments: `{name}, {age}`
>   - Nested fields: `{0.attribute}`
> - Info: More readable alternative to %-formatting

```python
# Positional arguments
print("{} is {} years old".format("Bob", 30))

# Keyword arguments
print("{name} is {age} years old".format(name="Bob", age=30))

# Numbered arguments
print("{1} and {0}".format("second", "first"))
```

```sh
Bob is 30 years old
Bob is 30 years old
first and second
```

<br>

### f-strings (Python 3.6+)
> - Syntax: `f"string {expression}"`
> - Return: String
> - Features:
>   - Can include expressions
>   - Support format specifiers
>   - Can call methods
> - Info: Most readable and convenient way to format strings

```python
name = "Charlie"
age = 35

print(f"{name} is {age} years old")
print(f"Next year: {age + 1}")
print(f"Name in caps: {name.upper()}")
```

```sh
Charlie is 35 years old
Next year: 36
Name in caps: CHARLIE
```

<br>

### Format Specifiers
> - Common specifiers:
>   - `.2f`: Float with 2 decimal places
>   - `>10`: Right align, width 10
>   - `<10`: Left align, width 10
>   - `,`: Number with thousand separator

```python
number = 1234.5678
price = 1000

print(f"Float: {number:.2f}")
print(f"Aligned: {price:>10}")
print(f"With commas: {price:,}")
```

```sh
Float: 1234.57
Aligned:      1000
With commas: 1,000
```

<br>

### Raw Formatted Strings (Special Note)
> - Syntax: `rf"string"` or `fr"string"`
> - Info: Combines raw string behavior with formatting
> - Use: Especially useful for formatted regular expressions or paths

```python
name = "Alice"
# Regular raw string
print(r"C:\Users\name")
# Raw formatted string
print(rf"C:\Users\{name}")
# Both produce the same result
print(fr"C:\Users\{name}")
```

```sh
C:\Users\name
C:\Users\Alice
C:\Users\Alice
```

<br>

---

<br>

## Raw Strings

> Raw strings are string literals that treat backslashes (\) as literal characters, prefixed with 'r' or 'R'. They're particularly useful for regular expressions, file paths, and URLs.

<br>

### File Paths
> - Common Use Case: Windows file paths
> - Benefit: Avoids double backslashes
> - Note: Makes path strings more readable

```python
# Regular string needs escaped backslashes
regular_path = "C:\\Users\\Documents\\file.txt"

# Raw string is more readable
raw_path = r"C:\Users\Documents\file.txt"

print(regular_path)
print(raw_path)
```

```sh
C:\Users\Documents\file.txt
C:\Users\Documents\file.txt
```

<br>

### Regular Expression Patterns
> - Use Case: Defining regex patterns
> - Benefit: Avoids excessive escaping
> - Note: Makes patterns more readable and maintainable

```python
import re

# Regular string pattern
pattern1 = "\\d+\\.\\d+"    # Match decimal numbers

# Raw string pattern (more readable)
pattern2 = r"\d+\.\d+"      # Same pattern

text = "Price is 23.45"
print(re.findall(pattern2, text))
```

```sh
['23.45']
```

<br>

### Limitations
> - Cannot end with odd number of backslashes
> - Cannot use raw string to end with single quote
> - Special handling needed for certain patterns

```python
# This works
print(r"Path\to\file")

# This would cause syntax error
# print(r"Path\")  # Invalid syntax

# Workaround for backslash at end
print(r"Path" + "\\")
```

```sh
Path\to\file
Path\
```

### Raw Formatted Strings (Special Note)
> - Syntax: `rf"string"` or `fr"string"`
> - Info: Combines raw string behavior with formatting
> - Use: Especially useful for formatted regular expressions or paths

```python
name = "Alice"
# Regular raw string
print(r"C:\Users\name")
# Raw formatted string
print(rf"C:\Users\{name}")
# Both produce the same result
print(fr"C:\Users\{name}")
```

```sh
C:\Users\name
C:\Users\Alice
C:\Users\Alice
```

<br>

---

<br>

## Unicode and Encoding

> Python strings are Unicode by default, supporting international characters and symbols. Encoding converts these Unicode strings to bytes for storage or transmission.

<br>

### Unicode Characters
> - Syntax: `"\uXXXX"` or `"\U00XXXXXX"`
> - Features:
>   - \u for 4 hex digits
>   - \U for 8 hex digits
> - Info: Represents Unicode characters by their code points

```python
# Unicode characters
print("Euro: \u20AC")
print("Degree: \u00B0")
print("Copyright: \u00A9")

# Unicode in regular string
text = "Hello, 世界"
print(text)
```

```sh
Euro: €
Degree: °
Copyright: ©
Hello, 世界
```

<br>

### encode()
> - Syntax: `str.encode(encoding='utf-8', errors='strict')`
> - Return: Bytes object
> - Parameters:
>   - encoding: Encoding to use (default 'utf-8')
>   - errors: Error handling scheme
> - Info: Converts string to bytes using specified encoding

```python
text = "Hello, 世界"

# UTF-8 encoding
utf8_bytes = text.encode('utf-8')
print(utf8_bytes)

# ASCII encoding (with error handling)
ascii_bytes = text.encode('ascii', errors='replace')
print(ascii_bytes)
```

```sh
b'Hello, \xe4\xb8\x96\xe7\x95\x8c'
b'Hello, ??'
```

<br>

### decode()
> - Syntax: `bytes.decode(encoding='utf-8', errors='strict')`
> - Return: String
> - Parameters: Same as encode()
> - Info: Converts bytes back to string using specified encoding

```python
# UTF-8 bytes to string
bytes_data = b'Hello, \xe4\xb8\x96\xe7\x95\x8c'
text = bytes_data.decode('utf-8')
print(text)

# Error handling
try:
    bad_bytes = b'\xFF\xFE'
    text = bad_bytes.decode('utf-8')
except UnicodeError as e:
    print("Decoding error")
```

```sh
Hello, 世界
Decoding error
```

<br>

### Common Encodings
> - UTF-8: Variable width, ASCII compatible
> - ASCII: 7-bit English characters
> - Latin-1: 8-bit Western European
> - UTF-16: Variable width, common in Windows
> - UTF-32: Fixed width, 4 bytes per character

```python
text = "Hello, ©"

# Different encodings
print(text.encode('utf-8'))
print(text.encode('ascii', errors='replace'))
print(text.encode('latin1'))
```

```sh
b'Hello, \xc2\xa9'
b'Hello, ?'
b'Hello, \xa9'
```

<br>

---

<br>

## Regular Expressions

> Regular expressions (regex) provide powerful pattern matching and searching capabilities through the `re` module. They allow complex pattern matching, searching, and text manipulation.

<br>

### re.search()
> - Syntax: `re.search(pattern, string, flags=0)`
> - Return: Match object or None
> - Parameters:
>   - pattern: Regular expression pattern
>   - string: String to search
>   - flags: Optional regex flags
> - Info: Finds first match of pattern in string

```python
import re

text = "The year is 2024"
match = re.search(r'\d+', text)

if match:
    print(f"Found: {match.group()}")
```

```sh
Found: 2024
```

<br>

### re.findall()
> - Syntax: `re.findall(pattern, string, flags=0)`
> - Return: List of strings
> - Parameters: Same as search()
> - Info: Returns all non-overlapping matches in string
> - Note: Returns empty list if no matches found

```python
import re

text = "Phone: 123-456-7890 or 555-1234"
numbers = re.findall(r'\d+-\d+', text)
print(numbers)
```

```sh
['123-456', '555-1234']
```

<br>

### re.sub()
> - Syntax: `re.sub(pattern, repl, string, count=0, flags=0)`
> - Return: String
> - Parameters:
>   - pattern: Pattern to find
>   - repl: Replacement string
>   - string: Original string
>   - count: Maximum replacements (0=all)
> - Info: Replaces pattern matches with replacement string

```python
import re

text = "I love cats and cats"
new_text = re.sub(r'cats', 'dogs', text)
print(new_text)
```

```sh
I love dogs and dogs
```

<br>

### Common Patterns
> - `\d`: Digit (0-9)
> - `\w`: Word character (a-z, A-Z, 0-9, _)
> - `\s`: Whitespace
> - `+`: One or more
> - `*`: Zero or more
> - `?`: Zero or one
> - `[]`: Character set
> - `()`: Group

```python
import re

text = "Python3 is fun!"

# Find word characters
words = re.findall(r'\w+', text)
print(f"Words: {words}")

# Find digits
digits = re.findall(r'\d+', text)
print(f"Digits: {digits}")
```

```sh
Words: ['Python3', 'is', 'fun']
Digits: ['3']
```

<br>

---

<br>

## Text Processing

> Text processing involves manipulating and analyzing text data using various string operations and methods. Python provides built-in functionality for common text processing tasks.

<br>

### splitlines()
> - Syntax: `str.splitlines(keepends=False)`
> - Return: List of strings
> - Parameters:
>   - keepends: If True, keeps line breaks
> - Info: Breaks string into list of lines
> - Note: Recognizes all universal newlines

```python
text = """Line 1
Line 2
Line 3"""

lines = text.splitlines()
print(lines)
```

```sh
['Line 1', 'Line 2', 'Line 3']
```

<br>

### partition()
> - Syntax: `str.partition(separator)`
> - Return: Tuple of three strings
> - Parameters:
>   - separator: String to separate on
> - Info: Splits string at first occurrence of separator
> - Returns: (before_separator, separator, after_separator)

```python
text = "name=Alice"
before, sep, after = text.partition('=')
print(f"Before: {before}")
print(f"After: {after}")
```

```sh
Before: name
After: Alice
```

<br>

### translate()
> - Syntax: `str.translate(table)`
> - Return: String
> - Parameters:
>   - table: Translation table (dict or maketrans())
> - Info: Replaces characters based on translation table
> - Note: Useful for character-by-character replacements

```python
# Create translation table
trans = str.maketrans('aeiou', '12345')

text = "hello world"
translated = text.translate(trans)
print(translated)
```

```sh
h2ll4 w4rld
```

<br>

### expandtabs()
> - Syntax: `str.expandtabs(tabsize=8)`
> - Return: String
> - Parameters:
>   - tabsize: Number of spaces per tab
> - Info: Converts tabs to spaces
> - Note: Default tabsize is 8

```python
text = "Column1\tColumn2\tColumn3"
expanded = text.expandtabs(4)
print(expanded)
```

```sh
Column1    Column2    Column3
```
