## Introduction

> Strings in Python are sequences of characters used to represent textual data. They are immutable, meaning they cannot be changed after creation.

<br>

---

<br>

## Creating Strings

<br>

### Single Quotes and Double Quotes

> Strings can be created using single quotes or double quotes.

```python
s1 = 'Hello'
s2 = "World"
print(s1, s2)  # Hello World
```

<br>

### Triple Quotes

> Triple quotes are used for multi-line strings or string literals that span multiple lines.

```python
s = """This is a 
multi-line string."""
print(s)
```

<br>

### Escape Characters

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

### Raw Strings

> Sometimes, escape sequences should be treated as literal text. Use raw strings by prefixing the string with an `r`.
>
> In raw strings, backslashes are treated as literal characters, and escape sequences are not processed.

```python
# Without raw string
print("C:\\Users\\Name\\Documents")

# Using raw string
print(r"C:\Users\Name\Documents")
```

<br>

---

<br>

## String Methods

<br>

### str.upper()

> Converts all characters in the string to uppercase.

```python
s = "hello"
print(s.upper())  # HELLO
```

<br>

### str.lower()
> Converts all characters in the string to lowercase.

```python
s = "HELLO"
print(s.lower())  # hello
```

<br>

### str.capitalize()

> Capitalizes the first character of the string.

```python
s = "hello world"
print(s.capitalize())  # Hello world
```

<br>

### str.title()

> Converts the first character of each word to uppercase.

```python
s = "hello world"
print(s.title())  # Hello World
```

<br>

### str.strip()

> Removes leading and trailing whitespace (or specified characters).

```python
s = "   hello   "
print(s.strip())  # hello
```

<br>

### str.lstrip()

> Removes leading whitespace (or specified characters).

```python
s = "   hello   "
print(s.lstrip())  # hello___
```

<br>

### str.rstrip()

> Removes trailing whitespace (or specified characters).

```python
s = "   hello   "
print(s.rstrip())  # ___hello
```

<br>

### str.replace()

> Replaces occurrences of a substring with another substring.

```python
s = "hello world"
print(s.replace("world", "Python"))  # hello Python
```

<br>

### str.find()

> Returns the index of the first occurrence of a substring. Returns -1 if not found.

```python
s = "hello world"
print(s.find("world"))  # 6
```

<br>

### str.index()

> Similar to str.find but raises a ValueError if the substring is not found.

```python
s = "hello world"
print(s.index("world"))  # 6
```

<br>

### str.split()

> Splits the string into a list using a specified delimiter.

```python
s = "apple,banana,orange"
print(s.split(","))  # ['apple', 'banana', 'orange']
```

<br>

### str.join()

> Joins elements of an iterable with the string as a delimiter.

```python
items = ['apple', 'banana', 'orange']
print(", ".join(items))  # apple, banana, orange
```

<br>

### str.startswith()

> Checks if the string starts with a specified prefix.

```python
s = "hello world"
print(s.startswith("hello"))  # True
```

<br>

### str.endswith()

> Checks if the string ends with a specified suffix.

```python
s = "hello world"
print(s.endswith("world"))  # True
```

<br>

### str.isalpha()

> Returns True if the string contains only alphabetic characters.

```python
s = "hello"
print(s.isalpha())  # True
```

<br>

### str.isdigit()

> Returns True if the string contains only numeric characters.

```python
s = "12345"
print(s.isdigit())  # True
```

<br>

### str.isalnum()

> Returns True if the string contains only alphanumeric characters.

```python
s = "hello123"
print(s.isalnum())  # True
```

<br>

---

<br>


## String Formatting

<br>

### f-strings (formatted string literal)

> A modern way to embed expressions inside string literals.

```python
greeting = "Hello"
print(f"{greeting}, World!")  # Hello, World! 
```

<br>

### fr-strings (formatted raw string literals)

> Formatted raw strings (`rf`) are powerful for scenarios like working with Windows file paths or regex patterns that need dynamic variable interpolation. They combine the best of both raw and formatted strings.
>
> `rf` or `fr` can be used interchangeably; the behavior is the same.

```python
user_name = "Adam"
path = rf"C:\{user_name}\Documents"

print(path)  # C:\Adam\Documents
```

<br>

### str.format()

> Another way to format strings.

```python
name = "Adam"
age = 32

print("{} is {} years old.".format(name, age))  # Adam is 32 years old.
```

<br>

### Old-Style Formatting

> The `%` operator can also be used for string formatting.

```python
name = "Adam"
age = 32

print("%s is %d years old." % (name, age))  # Adam is 32 years old.
```

<br>

---

<br>

## String Slicing

> Strings can be sliced using the syntax `string[start:end:step]`.

```python
s = "hello world"
print(s[0:5])    # hello
print(s[:5])     # hello
print(s[6:])     # world
print(s[::-1])   # dlrow olleh
```

<br>

---

<br>

## String Encoding and Decoding

<br>

### Encoding

> Converts a string into a sequence of bytes.

```python
s = "hello"
encoded = s.encode("utf-8")
print(encoded)  # b'hello'
```

<br>

### Decoding

> Converts a sequence of bytes back into a string.

```python
decoded = encoded.decode("utf-8")
print(decoded)  # hello
```