---
tags:
- basics
---

<br>

> Python provides robust support for file handling, enabling the creation, reading, updating, and deletion of files. The built-in `open` function, along with modules like `os`, `csv`, and `json`, facilitates working with various file types including text, CSV, and JSON.

<br>

---

<br>

## Working with Text Files

> Python can create, read, write, and update text files using built-in functions and tools.

<br>

---

<br>

### Opening and Closing Files

<br>

> The `open` function is used to open a file. Files should be closed using `close` or handled using the `with` statement for automatic closure.

```python
# Open the file in read-only mode
file = open("example.txt", "r")

# Read and Print the file contents
content = file.read()
print(content)

# Manually close file
file.close()
```

<br>

> Using `with` for automatic file closure 
```python
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```

<br>

---

<br>

### File Modes

|Mode|Description|
|---|---|
|`r`|Opens the file in read-only mode. Raises an error if the file does not exist.|
|`rb`|Opens the file in read-only mode in binary format.|
|`r+`|Opens the file for both reading and writing. The file must exist.|
|`rb+`|Opens the file for both reading and writing in binary format. The file must exist.|
|`w`|Opens the file in write mode. Creates the file if it doesn’t exist, or truncates it if it does.|
|`wb`|Opens the file in write mode in binary format. Creates or truncates the file.|
|`w+`|Opens the file for both writing and reading. Creates or truncates the file.|
|`wb+`|Opens the file for both writing and reading in binary format. Creates or truncates the file.|
|`a`|Opens the file in append mode. Creates the file if it doesn’t exist.|
|`ab`|Opens the file in append mode in binary format. Creates the file if it doesn’t exist.|
|`a+`|Opens the file for both appending and reading. Creates the file if it doesn’t exist.|
|`ab+`|Opens the file for both appending and reading in binary format. Creates the file if it doesn’t exist.|
|`x`|Opens the file for exclusive creation. Fails if the file already exists.|
|`xb`|Opens the file for exclusive creation in binary format. Fails if the file already exists.|
|`x+`|Opens the file for exclusive creation, allowing both reading and writing. Fails if the file already exists.|
|`xb+`|Opens the file for exclusive creation in binary format, allowing both reading and writing. Fails if the file already exists.|

<br>

#### Text vs Binary Modes

> - Text mode (`r`, `w`, `a`, etc.) is the default and interprets the file contents as strings.
> - Binary mode (`rb`, `wb`, `ab`, etc.) works with bytes instead of strings.

<br>

#### Combining Modes
  
> - Modes like `r+`, `w+`, and `a+` allow both reading and writing, with specific behavior:
>    - `r+`: Requires the file to exist and allows modification without truncation.
>    - `w+`: Overwrites existing content (truncates) or creates a new file.
>    - `a+`: Writes at the end of the file and allows reading existing content.

<br>

#### Exclusive Creation

> - `x`, `xb`, `x+`, and `xb+` modes are useful for creating files where overwriting existing files is undesirable. These raise a `FileExistsError` if the file already exists.

<br>

#### Default Encoding

> - When opening files in text mode, Python uses the default encoding (`utf-8` in most cases). This can be explicitly set using the `encoding` parameter:

```python
    with open("example.txt", "r", encoding="utf-8") as file:
        content = file.read()
```



<br>

---

<br>

### Reading Files

> Python provides several methods to read data from files.

<br>

#### Reading the entire file
```python
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```

<br>

#### Reading line by line

```python
with open("example.txt", "r") as file:
    for line in file:
        print(line.strip())
```

<br>

#### Reading into a list of lines

```python
with open("example.txt", "r") as file:
    lines = file.readlines()
    print(lines)
```

<br>

---

<br>

### Writing to Files

> Data can be written to files using `write` or `writelines`.

<br>

#### Writing to a file

```python
with open("example.txt", "w") as file:
    file.write("Hello, World!")
```

<br>

#### Writing multiple lines

```python
with open("example.txt", "w") as file:
    file.writelines(["Line 1\n", "Line 2\n"])
```

<br>

---

<br>

### Appending to Files

> Append mode allows adding new content to an existing file.

```python
with open("example.txt", "a") as file:
    file.write("This is an additional line.\n")
```

<br>

---

<br>

## File Operations with os Module

<br>

### Import the OS Module

```python
import os
```

<br>

### Checking File Existence

```python
if os.path.exists("example.txt"):
    print("True")
else:
    print("False")
```

<br>

```python
print("True" if os.path.exists("example.txt") else "False")
```

<br>

---

<br>

### Renaming Files

```python
os.rename("example.txt", "renamed_example.txt")
```

<br>

---

<br>

### Deleting Files

```python
os.remove("renamed_example.txt")
```

<br>

---

<br>

## Working with CSV Files

> Python’s `csv` module provides tools to read and write CSV files.

<br>

### Import the CSV Module

```python
import csv
```

<br>

### Reading a CSV File

```python
with open("data.csv", "r") as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
```

<br>

### Reading into a Dictionary

```python
with open("data.csv", "r") as file:
    reader = csv.DictReader(file)
    for row in reader:
        print(row)
```

<br>

### Writing CSV Files

```python
with open("data.csv", "w", newline="") as file:
    writer = csv.writer(file)
    writer.writerow(["Name", "Age", "City"])
    writer.writerow(["Alice", 25, "New York"])
```

<br>

### Writing from a Dictionary

```python
with open("data.csv", "w", newline="") as file:
    fieldnames = ["Name", "Age", "City"]
    writer = csv.DictWriter(file, fieldnames=fieldnames)
    writer.writeheader()
    writer.writerow({"Name": "Alice", "Age": 25, "City": "New York"})
```

<br>

---

<br>

## Working with JSON Files

> The `json` module allows working with JSON data.

<br>

### Import the JSON Module

```python
import json
```

<br>


### Reading a JSON File

```python
with open("data.json", "r") as file:
    data = json.load(file)
    print(data)
```

<br>

### Writing JSON Files

```python
data = {"name": "Alice", "age": 25, "city": "New York"}

with open("data.json", "w") as file:
    json.dump(data, file, indent=4)
```

<br>

---

<br>

## Working with Binary Files

<br>

### Reading Binary Files

```python
with open("example.bin", "rb") as file:
    data = file.read()
    print(data)
```

<br>

### Writing Binary Files

```python
with open("example.bin", "wb") as file:
    file.write(b"This is binary data.")
```

<br>

---

<br>

## Common Exceptions in File Handling

|Exception|Description|
|---|---|
|`FileNotFoundError`|Raised when the file does not exist.|
|`PermissionError`|Raised when permissions are insufficient.|
|`IsADirectoryError`|Raised when attempting to open a directory as a file.|

<br>

### Example

```python
try:
    with open("nonexistent.txt", "r") as file:
        content = file.read()
except FileNotFoundError:
    print("File not found.")
```

<br>

---

<br>

## Examples and Use Cases

<br>

### Example 1: Copying Files

```python
with open("source.txt", "r") as source:
    content = source.read()

with open("destination.txt", "w") as destination:
    destination.write(content)
```

<br>

### Example 2: Counting Words in a Text File

```python
with open("example.txt", "r") as file:
    content = file.read()
    words = content.split()
    print(f"Word count: {len(words)}")
```

<br>

### Example 3: Merging CSV Files

```python
import csv

with open("merged.csv", "w", newline="") as outfile:
    writer = csv.writer(outfile)

    for filename in ["file1.csv", "file2.csv"]:
        with open(filename, "r") as infile:
            reader = csv.reader(infile)
            for row in reader:
                writer.writerow(row)
```