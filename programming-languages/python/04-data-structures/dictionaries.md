# Python Dictionaries

> Python dictionaries are hash tables that store key-value pairs. They provide fast access and modification of values using unique keys.

<br>

### Key Characteristics

> - Mutable mapping of keys to values
> - Keys must be hashable and unique
> - Values can be any Python object
> - Maintains insertion order (Python 3.7+)
> - Efficient lookup by key (O(1) average case)
> - Dynamic sizing
> - Memory optimized for sparse data

<br>

---

<br>

## Dictionary Creation

> Python offers several ways to create dictionaries:

<br>

### Literal Syntax

> Using curly braces:

```python
# Empty dictionary
empty_dict = {}
print(f"Empty dictionary: {empty_dict}")
```

```sh
Empty dictionary: {}
```

<br>

> With initial key-value pairs:

```python
# Basic key-value pairs
person = {
    'name': 'Alice',
    'age': 30,
    'city': 'New York'
}
print(f"Person dictionary: {person}")
```

```sh
Person dictionary: {'name': 'Alice', 'age': 30, 'city': 'New York'}
```

<br>

### dict() Constructor

> Creating dictionaries using the dict() constructor:

```python
# From keyword arguments
person = dict(name='Bob', age=25, city='London')
print(f"From keywords: {person}")

# From list of tuples
items = [('x', 1), ('y', 2)]
coords = dict(items)
print(f"From tuples: {coords}")

# From two sequences
keys = ['a', 'b', 'c']
values = [1, 2, 3]
mapping = dict(zip(keys, values))
print(f"From sequences: {mapping}")
```

```sh
From keywords: {'name': 'Bob', 'age': 25, 'city': 'London'}
From tuples: {'x': 1, 'y': 2}
From sequences: {'a': 1, 'b': 2, 'c': 3}
```

<br>

### Dictionary Comprehension

> Creating dictionaries using comprehension syntax:

```python
# Square numbers dictionary
squares = {x: x**2 for x in range(5)}
print(f"Squares: {squares}")

# Filtered dictionary comprehension
evens = {x: x**2 for x in range(5) if x % 2 == 0}
print(f"Even squares: {evens}")
```

```sh
Squares: {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
Even squares: {0: 0, 2: 4, 4: 16}
```

<br>

### fromkeys() Method

> Creating dictionaries with default values:

```python
# Create dict with default value
keys = ['a', 'b', 'c']
default_dict = dict.fromkeys(keys, 0)
print(f"With default value: {default_dict}")

# Default value is None if not specified
null_dict = dict.fromkeys(keys)
print(f"With None defaults: {null_dict}")
```

```sh
With default value: {'a': 0, 'b': 0, 'c': 0}
With None defaults: {'a': None, 'b': None, 'c': None}
```

<br>

### Nested Dictionaries

> Creating nested dictionary structures:

```python
# Nested structure
organization = {
    'department1': {
        'name': 'Engineering',
        'employees': ['Alice', 'Bob']
    },
    'department2': {
        'name': 'Sales',
        'employees': ['Charlie', 'David']
    }
}

print("Organization structure:")
for dept, details in organization.items():
    print(f"{dept}:")
    print(f"  Name: {details['name']}")
    print(f"  Employees: {details['employees']}")
```

```sh
Organization structure:
department1:
  Name: Engineering
  Employees: ['Alice', 'Bob']
department2:
  Name: Sales
  Employees: ['Charlie', 'David']
```

<br>

---

<br>

## Dictionary Methods

> Dictionaries provide numerous methods for managing and accessing key-value pairs.

<br>

### get()

> - Syntax: `dict.get(key[, default])`
> - Return: value for key if found, else default
> - Info: Safely retrieve values without raising KeyError

```python
data = {'a': 1, 'b': 2}

# Basic get
print(f"Value for 'a': {data.get('a')}")

# Get with default
print(f"Value for missing key: {data.get('c', 0)}")

# Get missing key without default
print(f"Missing key without default: {data.get('c')}")
```

```sh
Value for 'a': 1
Value for missing key: 0
Missing key without default: None
```

<br>

### setdefault()

> - Syntax: `dict.setdefault(key[, default])`
> - Return: value if key exists, else default (and adds key:default)
> - Info: Get value and set default in one operation

```python
data = {'a': 1}

# Get existing key
value1 = data.setdefault('a', 0)
print(f"Existing key: {value1}")
print(f"Dictionary: {data}")

# Set default for new key
value2 = data.setdefault('b', 2)
print(f"New key: {value2}")
print(f"Updated dictionary: {data}")
```

```sh
Existing key: 1
Dictionary: {'a': 1}
New key: 2
Updated dictionary: {'a': 1, 'b': 2}
```

<br>

### update()

> - Syntax: `dict.update([other])`
> - Return: `None`
> - Info: Update dictionary with elements from another dictionary or iterable

```python
data = {'a': 1, 'b': 2}

# Update with dictionary
data.update({'b': 3, 'c': 4})
print(f"After dict update: {data}")

# Update with keyword arguments
data.update(d=5, e=6)
print(f"After kwargs update: {data}")

# Update with list of tuples
data.update([('f', 7), ('g', 8)])
print(f"After tuple update: {data}")
```

```sh
After dict update: {'a': 1, 'b': 3, 'c': 4}
After kwargs update: {'a': 1, 'b': 3, 'c': 4, 'd': 5, 'e': 6}
After tuple update: {'a': 1, 'b': 3, 'c': 4, 'd': 5, 'e': 6, 'f': 7, 'g': 8}
```

<br>

### pop()

> - Syntax: `dict.pop(key[, default])`
> - Return: value if key found, else default
> - Info: Remove specified key and return value
> - Raises: KeyError if key missing and no default provided

```python
data = {'a': 1, 'b': 2, 'c': 3}

# Pop existing key
value1 = data.pop('b')
print(f"Popped value: {value1}")
print(f"After pop: {data}")

# Pop with default
value2 = data.pop('x', None)
print(f"Pop missing key: {value2}")

# Pop missing key without default
try:
    data.pop('x')
except KeyError as e:
    print(f"Error: {e}")
```

```sh
Popped value: 2
After pop: {'a': 1, 'c': 3}
Pop missing key: None
Error: 'x'
```

<br>

### popitem()

> - Syntax: `dict.popitem()`
> - Return: `tuple(key, value)`
> - Info: Remove and return last inserted key-value pair
> - Raises: KeyError if dictionary is empty

```python
data = {'a': 1, 'b': 2, 'c': 3}

# Pop items one by one
while data:
    item = data.popitem()
    print(f"Popped item: {item}")
    print(f"Remaining: {data}")

# Try to pop from empty dict
try:
    data.popitem()
except KeyError as e:
    print(f"Error: {e}")
```

```sh
Popped item: ('c', 3)
Remaining: {'a': 1, 'b': 2}
Popped item: ('b', 2)
Remaining: {'a': 1}
Popped item: ('a', 1)
Remaining: {}
Error: 'popitem(): dictionary is empty'
```

<br>

### clear()

> - Syntax: `dict.clear()`
> - Return: `None`
> - Info: Remove all items from dictionary

```python
data = {'a': 1, 'b': 2, 'c': 3}
print(f"Before clear: {data}")

data.clear()
print(f"After clear: {data}")
```

```sh
Before clear: {'a': 1, 'b': 2, 'c': 3}
After clear: {}
```

<br>

### copy()

> - Syntax: `dict.copy()`
> - Return: shallow copy of dictionary
> - Info: Create a new dictionary with references to same values

```python
original = {'a': 1, 'b': [2, 3]}
copied = original.copy()

# Modify original
original['a'] = 10
original['b'].append(4)

print(f"Original: {original}")
print(f"Copy: {copied}")  # Note: nested list is shared
```

```sh
Original: {'a': 10, 'b': [2, 3, 4]}
Copy: {'a': 1, 'b': [2, 3, 4]}
```

<br>

### keys(), values(), items()

> - Return dictionary views
> - Info: Provide dynamic views of dictionary entries

```python
data = {'a': 1, 'b': 2, 'c': 3}

# Get views
keys = data.keys()
values = data.values()
items = data.items()

print(f"Keys view: {keys}")
print(f"Values view: {values}")
print(f"Items view: {items}")

# Views update automatically
data['d'] = 4
print(f"\nAfter adding new item:")
print(f"Updated keys view: {keys}")
print(f"Updated values view: {values}")
print(f"Updated items view: {items}")
```

```sh
Keys view: dict_keys(['a', 'b', 'c'])
Values view: dict_values([1, 2, 3])
Items view: dict_items([('a', 1), ('b', 2), ('c', 3)])

After adding new item:
Updated keys view: dict_keys(['a', 'b', 'c', 'd'])
Updated values view: dict_values([1, 2, 3, 4])
Updated items view: dict_items([('a', 1), ('b', 2), ('c', 3), ('d', 4)])
```

<br>

---

<br>

## Dictionary Views

> Dictionary views provide a dynamic window into the dictionary's entries. They support set operations and update automatically when the dictionary changes.

<br>

### Types of Views

> Dictionaries provide three types of views:

```python
data = {'a': 1, 'b': 2, 'c': 3}

# Create all view types
key_view = data.keys()
value_view = data.values()
item_view = data.items()

print(f"Keys view: {key_view}")
print(f"Values view: {value_view}")
print(f"Items view: {item_view}")
```

```sh
Keys view: dict_keys(['a', 'b', 'c'])
Values view: dict_values([1, 2, 3])
Items view: dict_items([('a', 1), ('b', 2), ('c', 3)])
```

<br>

### Dynamic Nature

> Views automatically reflect changes to the dictionary:

```python
data = {'a': 1, 'b': 2}
view = data.keys()

print(f"Initial view: {view}")

# Modify dictionary
data['c'] = 3
print(f"After addition: {view}")

del data['a']
print(f"After deletion: {view}")
```

```sh
Initial view: dict_keys(['a', 'b'])
After addition: dict_keys(['a', 'b', 'c'])
After deletion: dict_keys(['b', 'c'])
```

<br>

### Set Operations

> Dictionary views support set operations when keys are hashable:

```python
dict1 = {'a': 1, 'b': 2, 'c': 3}
dict2 = {'b': 2, 'c': 3, 'd': 4}

# Set operations on keys
keys1 = dict1.keys()
keys2 = dict2.keys()

print(f"Union: {keys1 | keys2}")
print(f"Intersection: {keys1 & keys2}")
print(f"Difference: {keys1 - keys2}")
print(f"Symmetric difference: {keys1 ^ keys2}")
```

```sh
Union: {'a', 'b', 'c', 'd'}
Intersection: {'b', 'c'}
Difference: {'a'}
Symmetric difference: {'a', 'd'}
```

<br>

### View Comparisons

> Views can be compared with other views and sets:

```python
dict1 = {'a': 1, 'b': 2}
dict2 = {'b': 2, 'a': 1}
dict3 = {'a': 1, 'b': 2, 'c': 3}

# Compare views
view1 = dict1.items()
view2 = dict2.items()
view3 = dict3.items()

print(f"view1 == view2: {view1 == view2}")
print(f"view1 < view3: {view1 < view3}")
print(f"view1.issubset(view3): {view1 <= view3}")
```

```sh
view1 == view2: True
view1 < view3: True
view1.issubset(view3): True
```

<br>

### Iteration and Length

> Views can be iterated over and have length:

```python
data = {'a': 1, 'b': 2, 'c': 3}
key_view = data.keys()

# Length
print(f"View length: {len(key_view)}")

# Iteration
print("Iterating over key view:")
for key in key_view:
    print(f"  Key: {key}")

# List conversion
key_list = list(key_view)
print(f"Converted to list: {key_list}")
```

```sh
View length: 3
Iterating over key view:
  Key: a
  Key: b
  Key: c
Converted to list: ['a', 'b', 'c']
```

<br>

### Memory Efficiency

> Views provide memory-efficient access to dictionary entries:

```python
import sys

data = dict.fromkeys(range(1000))
keys_view = data.keys()
keys_list = list(data.keys())

print(f"View size: {sys.getsizeof(keys_view)} bytes")
print(f"List size: {sys.getsizeof(keys_list)} bytes")
```

```sh
View size: 48 bytes
List size: 8856 bytes
```

<br>

### Common Use Cases

> Practical applications of dictionary views:

```python
# Finding common keys
user1 = {'name': 'Alice', 'age': 30, 'city': 'New York'}
user2 = {'name': 'Bob', 'city': 'London', 'job': 'Developer'}

common_fields = user1.keys() & user2.keys()
print(f"Common fields: {common_fields}")

# Checking for required keys
required = {'name', 'age'}
has_required = required <= user1.keys()
print(f"Has required fields: {has_required}")

# Finding unique keys
all_fields = user1.keys() | user2.keys()
print(f"All fields: {all_fields}")
```

```sh
Common fields: {'name', 'city'}
Has required fields: True
All fields: {'name', 'age', 'city', 'job'}
```

<br>

---

<br>

## Dictionary Comprehensions

> Dictionary comprehensions provide a concise way to create dictionaries using a single line of code. They follow the pattern:
> `{key_expr: value_expr for item in iterable if condition}`

<br>

### Basic Comprehension

> Simple key-value mapping:

```python
# Square numbers dictionary
squares = {x: x**2 for x in range(5)}
print(f"Squares: {squares}")

# Character positions in string
word = "hello"
char_pos = {char: idx for idx, char in enumerate(word)}
print(f"Character positions: {char_pos}")
```

```sh
Squares: {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
Character positions: {'h': 0, 'e': 1, 'l': 2, 'o': 4}
```

<br>

### Conditional Comprehension

> Adding conditions to filter items:

```python
numbers = range(10)

# Even squares only
even_squares = {x: x**2 for x in numbers if x % 2 == 0}
print(f"Even squares: {even_squares}")

# Conditional values
parity = {x: 'even' if x % 2 == 0 else 'odd' for x in range(5)}
print(f"Parity mapping: {parity}")
```

```sh
Even squares: {0: 0, 2: 4, 4: 16, 6: 36, 8: 64}
Parity mapping: {0: 'even', 1: 'odd', 2: 'even', 3: 'odd', 4: 'even'}
```

<br>

### Dictionary Transformation

> Creating new dictionaries from existing ones:

```python
prices = {'apple': 0.40, 'orange': 0.35, 'banana': 0.25}

# Convert to euros (assuming USD)
euro_rate = 0.85
euros = {item: price * euro_rate for item, price in prices.items()}
print(f"Prices in euros: {euros}")

# Round to 2 decimal places
rounded = {k: round(v, 2) for k, v in euros.items()}
print(f"Rounded prices: {rounded}")
```

```sh
Prices in euros: {'apple': 0.34, 'orange': 0.2975, 'banana': 0.2125}
Rounded prices: {'apple': 0.34, 'orange': 0.3, 'banana': 0.21}
```

<br>

### Nested Comprehension

> Creating dictionaries with nested structures:

```python
# Matrix of multiplication table
table = {x: {y: x*y for y in range(1, 4)} for x in range(1, 4)}

print("Multiplication table:")
for x, row in table.items():
    print(f"{x}: {row}")

# Flatten nested structures
matrix = {'a': [1, 2, 3], 'b': [4, 5, 6]}
flat = {f"{k}_{i}": v for k, vals in matrix.items() 
                    for i, v in enumerate(vals)}
print(f"\nFlattened matrix: {flat}")
```

```sh
Multiplication table:
1: {1: 1, 2: 2, 3: 3}
2: {1: 2, 2: 4, 3: 6}
3: {1: 3, 2: 6, 3: 9}

Flattened matrix: {'a_0': 1, 'a_1': 2, 'a_2': 3, 'b_0': 4, 'b_1': 5, 'b_2': 6}
```

<br>

### Set and Dictionary Operations

> Combining comprehensions with set operations:

```python
dict1 = {'a': 1, 'b': 2, 'c': 3}
dict2 = {'b': 2, 'c': 4, 'd': 5}

# Keys in dict1 but not in dict2
diff = {k: dict1[k] for k in dict1.keys() - dict2.keys()}
print(f"Unique to dict1: {diff}")

# Common keys with matching values
common = {k: dict1[k] for k in dict1.keys() & dict2.keys() 
         if dict1[k] == dict2[k]}
print(f"Matching items: {common}")
```

```sh
Unique to dict1: {'a': 1}
Matching items: {'b': 2}
```

<br>

### Performance Considerations

> Comparing comprehension with traditional loop:

```python
import timeit

# Test data
data = range(1000)

def using_loop():
    d = {}
    for n in data:
        d[n] = n**2
    return d

def using_comprehension():
    return {n: n**2 for n in data}

# Time comparison
loop_time = timeit.timeit(using_loop, number=1000)
comp_time = timeit.timeit(using_comprehension, number=1000)

print(f"Loop time: {loop_time:.4f} seconds")
print(f"Comprehension time: {comp_time:.4f} seconds")
```

```sh
Loop time: 0.1011 seconds
Comprehension time: 0.0996 seconds
```

<br>

### Best Practices

> Guidelines for using dictionary comprehensions effectively:

```python
# Good: Simple and clear transformation
names = ['alice', 'bob', 'charlie']
name_lengths = {name: len(name) for name in names}
print(f"Name lengths: {name_lengths}")

# Better than nested comprehension when complex
matrix = [[1, 2], [3, 4]]
flat = {}
for i, row in enumerate(matrix):
    for j, val in enumerate(row):
        flat[f"{i},{j}"] = val
print(f"Flat matrix: {flat}")

# Avoid when too complex
data = {'a': [1, 2], 'b': [3, 4]}
# Complex comprehension (hard to read):
# {f"{k}_{i}_{v}": v**2 for k, vals in data.items() 
#  for i, v in enumerate(vals) if v % 2 == 0}
# Better as a loop:
result = {}
for k, vals in data.items():
    for i, v in enumerate(vals):
        if v % 2 == 0:
            result[f"{k}_{i}_{v}"] = v**2
print(f"Processed data: {result}")
```

```sh
Name lengths: {'alice': 5, 'bob': 3, 'charlie': 7}
Flat matrix: {'0,0': 1, '0,1': 2, '1,0': 3, '1,1': 4}
Processed data: {'a_1_2': 4, 'b_1_4': 16}
```

<br>

---

<br>

## DefaultDict

> `defaultdict` is a dictionary subclass from the collections module that automatically handles missing keys by calling a factory function to provide default values.

<br>

### Basic Usage

> Creating and using defaultdict:

```python
from collections import defaultdict

# Create defaultdict with int factory
int_dict = defaultdict(int)
words = ['apple', 'banana', 'apple', 'cherry', 'banana', 'apple']

# Count occurrences
for word in words:
    int_dict[word] += 1

print(f"Word counts: {dict(int_dict)}")
```

```sh
Word counts: {'apple': 3, 'banana': 2, 'cherry': 1}
```

<br>

### Built-in Factory Functions

> Common factory functions for defaultdict:

```python
from collections import defaultdict

# int factory (starts at 0)
int_dict = defaultdict(int)
print(f"Missing int: {int_dict['missing']}")

# list factory (starts with empty list)
list_dict = defaultdict(list)
list_dict['numbers'].append(1)
print(f"List dict: {dict(list_dict)}")

# str factory (starts with empty string)
str_dict = defaultdict(str)
print(f"Missing string: {str_dict['missing']}")

# float factory
float_dict = defaultdict(float)
print(f"Missing float: {float_dict['missing']}")
```

```sh
Missing int: 0
List dict: {'numbers': [1]}
Missing string: 
Missing float: 0.0
```

<br>

### Custom Factory Functions

> Using custom functions to provide defaults:

```python
from collections import defaultdict

# Custom factory function
def custom_default():
    return {'count': 0, 'values': []}

# Create defaultdict with custom factory
data = defaultdict(custom_default)

# Access and modify nested structure
data['item1']['count'] += 1
data['item1']['values'].append('a')
data['item2']['values'].append('b')

print("Custom defaultdict:")
for key, value in data.items():
    print(f"{key}: {value}")
```

```sh
Custom defaultdict:
item1: {'count': 1, 'values': ['a']}
item2: {'count': 0, 'values': ['b']}
```

<br>

### Practical Applications

#### Grouping Data

> Using defaultdict for grouping:

```python
from collections import defaultdict

# Group people by age
people = [
    ('Alice', 25),
    ('Bob', 30),
    ('Charlie', 25),
    ('David', 30)
]

# Group using defaultdict
age_groups = defaultdict(list)
for name, age in people:
    age_groups[age].append(name)

print("Age groups:")
for age, names in age_groups.items():
    print(f"{age} years: {names}")
```

```sh
Age groups:
25 years: ['Alice', 'Charlie']
30 years: ['Bob', 'David']
```

<br>

#### Building Graphs

> Using defaultdict for graph representation:

```python
from collections import defaultdict

# Create adjacency list representation
graph = defaultdict(list)

# Add edges
edges = [('A', 'B'), ('B', 'C'), ('A', 'C'), ('B', 'D')]
for src, dst in edges:
    graph[src].append(dst)

print("Graph structure:")
for node, neighbors in graph.items():
    print(f"{node} -> {neighbors}")
```

```sh
Graph structure:
A -> ['B', 'C']
B -> ['C', 'D']
```

<br>

### Performance Comparison

> Comparing defaultdict with regular dict:

```python
from collections import defaultdict
import timeit

# Test data
words = ['apple', 'banana', 'cherry'] * 1000

def using_dict():
    d = {}
    for word in words:
        if word not in d:
            d[word] = 0
        d[word] += 1
    return d

def using_defaultdict():
    d = defaultdict(int)
    for word in words:
        d[word] += 1
    return d

# Time comparison
dict_time = timeit.timeit(using_dict, number=100)
defaultdict_time = timeit.timeit(using_defaultdict, number=100)

print(f"Regular dict time: {dict_time:.4f} seconds")
print(f"defaultdict time: {defaultdict_time:.4f} seconds")
```

```sh
Regular dict time: 0.0467 seconds
defaultdict time: 0.0250 seconds
```

<br>

### Best Practices

> Guidelines for using defaultdict:

```python
from collections import defaultdict

# Good: Simple counting/accumulation
word_count = defaultdict(int)
word_count['word'] += 1

# Good: Collecting items into lists
categories = defaultdict(list)
categories['fruit'].append('apple')

# Avoid: Unnecessary use for simple cases
simple_dict = defaultdict(lambda: 0)  # Better as regular dict
simple_dict = {'default': 0}  # Better approach

# Good: Complex nested structures
nested = defaultdict(lambda: defaultdict(list))
nested['group1']['items'].append('item1')
print(f"Nested structure: {dict(nested)}")
```

```sh
Nested structure: {'group1': {'items': ['item1']}}
```

<br>

---

<br>

## OrderedDict

> `OrderedDict` is a dictionary subclass from the collections module that remembers the order in which keys were inserted. While regular dictionaries now preserve insertion order (Python 3.7+), OrderedDict maintains some unique features.

<br>

### Basic Usage

> Creating and using OrderedDict:

```python
from collections import OrderedDict

# Create from list of pairs
ordered = OrderedDict([
    ('a', 1),
    ('b', 2),
    ('c', 3)
])

print(f"Ordered dictionary: {ordered}")
```

```sh
Ordered dictionary: OrderedDict([('a', 1), ('b', 2), ('c', 3)])
```

<br>

### Key Differences from Regular Dict

> Comparing OrderedDict with regular dict:

```python
from collections import OrderedDict

# Regular dict
regular = {'a': 1, 'b': 2, 'c': 3}

# OrderedDict
ordered = OrderedDict([('a', 1), ('b', 2), ('c', 3)])

# Equality comparison
dict1 = {'a': 1, 'b': 2}
dict2 = {'b': 2, 'a': 1}
odict1 = OrderedDict([('a', 1), ('b', 2)])
odict2 = OrderedDict([('b', 2), ('a', 1)])

print(f"Regular dict equality: {dict1 == dict2}")
print(f"OrderedDict equality: {odict1 == odict2}")
```

```sh
Regular dict equality: True
OrderedDict equality: False
```

<br>

### Specific Methods

#### move_to_end()

> - Syntax: `OrderedDict.move_to_end(key, last=True)`
> - Info: Move an existing key to either end of the OrderedDict

```python
ordered = OrderedDict.fromkeys('abcde')

# Move 'b' to end
ordered.move_to_end('b')
print(f"After moving 'b' to end: {ordered}")

# Move 'a' to beginning
ordered.move_to_end('a', last=False)
print(f"After moving 'a' to start: {ordered}")
```

```sh
After moving 'b' to end: OrderedDict([('a', None), ('c', None), ('d', None), ('e', None), ('b', None)])
After moving 'a' to start: OrderedDict([('a', None), ('c', None), ('d', None), ('e', None), ('b', None)])
```

<br>

### Reversing and Reordering

> OrderedDict supports reversed iteration:

```python
ordered = OrderedDict([('a', 1), ('b', 2), ('c', 3)])

# Forward iteration
print("Forward iteration:")
for k in ordered:
    print(f"  {k}: {ordered[k]}")

# Reverse iteration
print("\nReverse iteration:")
for k in reversed(ordered):
    print(f"  {k}: {ordered[k]}")
```

```sh
Forward iteration:
  a: 1
  b: 2
  c: 3

Reverse iteration:
  c: 3
  b: 2
  a: 1
```

<br>

### Common Use Cases

#### LRU Cache Implementation

> Using OrderedDict for a simple LRU (Least Recently Used) cache:

```python
from collections import OrderedDict

class LRUCache:
    def __init__(self, capacity):
        self.cache = OrderedDict()
        self.capacity = capacity
    
    def get(self, key):
        if key not in self.cache:
            return -1
        # Move accessed item to end
        self.cache.move_to_end(key)
        return self.cache[key]
    
    def put(self, key, value):
        if key in self.cache:
            # Remove existing item first
            self.cache.pop(key)
        elif len(self.cache) >= self.capacity:
            # Remove least recently used item
            self.cache.popitem(last=False)
        self.cache[key] = value

# Usage example
cache = LRUCache(2)
cache.put(1, 1)
cache.put(2, 2)
print(f"Get 1: {cache.get(1)}")
cache.put(3, 3)  # evicts key 2
print(f"Get 2: {cache.get(2)}")  # returns -1
print(f"Cache: {cache.cache}")
```

```sh
Get 1: 1
Get 2: -1
Cache: OrderedDict([(1, 1), (3, 3)])
```

<br>

### Memory Usage

> Comparing memory usage with regular dict:

```python
import sys
from collections import OrderedDict

# Create dictionaries with same content
regular = dict.fromkeys('abcde')
ordered = OrderedDict.fromkeys('abcde')

print(f"Regular dict size: {sys.getsizeof(regular)} bytes")
print(f"OrderedDict size: {sys.getsizeof(ordered)} bytes")
```

```sh
Regular dict size: 232 bytes
OrderedDict size: 384 bytes
```

<br>

### Best Practices

> Guidelines for using OrderedDict:

```python
from collections import OrderedDict

# Good: When order equality matters
config1 = OrderedDict([
    ('name', 'config'),
    ('version', '1.0'),
    ('settings', {})
])

config2 = OrderedDict([
    ('version', '1.0'),
    ('name', 'config'),
    ('settings', {})
])

print(f"Configs are equal: {config1 == config2}")

# Avoid: When regular dict is sufficient
simple_data = {'a': 1, 'b': 2}  # Use regular dict when order doesn't matter

# Good: When you need explicit reordering
ordered = OrderedDict([('a', 1), ('b', 2), ('c', 3)])
ordered.move_to_end('a')
print(f"After reordering: {ordered}")
```

```sh
Configs are equal: False
After reordering: OrderedDict([('b', 2), ('c', 3), ('a', 1)])
```

<br>

---

<br>

## Counter

> `Counter` is a dict subclass for counting hashable objects. It provides a dictionary where elements are stored as dictionary keys and their counts are stored as dictionary values.

<br>

### Basic Usage

> Creating and using Counter objects:

```python
from collections import Counter

# Create from sequence
colors = ['red', 'blue', 'red', 'green', 'blue', 'blue']
color_count = Counter(colors)
print(f"Color counts: {color_count}")

# Create from dictionary
count_dict = Counter({'red': 2, 'blue': 3, 'green': 1})
print(f"From dictionary: {count_dict}")

# Create with keyword arguments
letter_count = Counter(a=4, b=2, c=0, d=-2)
print(f"From keywords: {letter_count}")
```

```sh
Color counts: Counter({'blue': 3, 'red': 2, 'green': 1})
From dictionary: Counter({'blue': 3, 'red': 2, 'green': 1})
From keywords: Counter({'a': 4, 'b': 2, 'c': 0, 'd': -2})
```

<br>

### Counter Methods

#### most_common()

> - Syntax: `Counter.most_common([n])`
> - Return: List of n most common elements and counts
> - Info: If n is omitted, returns all elements sorted by count

```python
text = "mississippi"
counts = Counter(text)

# Get all counts in order
print(f"All counts: {counts.most_common()}")

# Get top 3 most common
print(f"Top 3: {counts.most_common(3)}")
```

```sh
All counts: [('i', 4), ('s', 4), ('p', 2), ('m', 1)]
Top 3: [('i', 4), ('s', 4), ('p', 2)]
```

<br>

#### elements()

> - Syntax: `Counter.elements()`
> - Return: Iterator over elements repeating each as many times as its count
> - Info: Elements with count <= 0 are ignored

```python
c = Counter(a=4, b=2, c=0, d=-2)

# Get all elements
elements_list = list(c.elements())
print(f"Elements: {elements_list}")

# Count matches original
print(f"Length of elements: {len(elements_list)}")
print(f"Counter values sum: {sum(c.values())}")
```

```sh
Elements: ['a', 'a', 'a', 'a', 'b', 'b']
Length of elements: 6
Counter values sum: 4
```

<br>

#### subtract()

> - Syntax: `Counter.subtract([iterable-or-mapping])`
> - Info: Subtract elements from another counter

```python
c = Counter(a=4, b=2, c=0, d=1)
d = Counter(a=1, b=2, c=3, d=1)

# Subtract counters
c.subtract(d)
print(f"After subtraction: {c}")

# Subtract from sequence
c.subtract(['a', 'b'])
print(f"After subtracting sequence: {c}")
```

```sh
After subtraction: Counter({'a': 3, 'b': 0, 'd': 0, 'c': -3})
After subtracting sequence: Counter({'a': 2, 'b': -1, 'd': 0, 'c': -3})
```

<br>

### Mathematical Operations

> Counter objects support several mathematical operations:

```python
c1 = Counter(a=3, b=1, c=1)
c2 = Counter(a=1, b=2, d=3)

# Addition
print(f"Sum: {c1 + c2}")

# Subtraction (keeping only positive counts)
print(f"Difference: {c1 - c2}")

# Union (max of values)
print(f"Union: {c1 | c2}")

# Intersection (min of values)
print(f"Intersection: {c1 & c2}")
```

```sh
Sum: Counter({'a': 4, 'd': 3, 'b': 3, 'c': 1})
Difference: Counter({'a': 2, 'c': 1})
Union: Counter({'a': 3, 'd': 3, 'b': 2, 'c': 1})
Intersection: Counter({'a': 1, 'b': 1})
```

<br>

### Common Use Cases

#### Word Frequency Analysis

> Using Counter for text analysis:

```python
from collections import Counter

def word_frequency(text):
    # Split text into words and create Counter
    words = text.lower().split()
    word_counts = Counter(words)
    
    # Print most common words
    print("Most common words:")
    for word, count in word_counts.most_common(3):
        print(f"  {word}: {count}")
        
    return word_counts

text = "the quick brown fox jumps over the lazy dog the fox"
frequency = word_frequency(text)
```

```sh
Most common words:
  the: 3
  fox: 2
  quick: 1
```

<br>

#### Finding Duplicate Files

> Using Counter to find duplicate files by size:

```python
from collections import Counter
import os

def find_duplicates(directory):
    # Count files by size
    size_count = Counter()
    
    for filename in os.listdir('.')[:5]:  # Limited for example
        size = os.path.getsize(filename)
        size_count[size] += 1
    
    # Find sizes with multiple files
    duplicates = {size: count for size, count 
                 in size_count.items() if count > 1}
    return duplicates

# Example with current directory
dupes = find_duplicates('.')
print(f"Files with same size: {dupes}")
```

```sh
Files with same size: {1024: 2, 2048: 3}
```

<br>

### Performance Characteristics

> Comparing Counter with regular dictionary:

```python
import timeit
from collections import Counter

data = ['a', 'b', 'a', 'c', 'a', 'b'] * 1000

def count_with_dict():
    d = {}
    for item in data:
        d[item] = d.get(item, 0) + 1
    return d

def count_with_counter():
    return Counter(data)

# Time comparison
dict_time = timeit.timeit(count_with_dict, number=100)
counter_time = timeit.timeit(count_with_counter, number=100)

print(f"Dictionary time: {dict_time:.4f} seconds")
print(f"Counter time: {counter_time:.4f} seconds")
```

```sh
Dictionary time: 0.0543 seconds
Counter time: 0.0234 seconds
```

<br>

---

<br>

## ChainMap

> `ChainMap` is a class that groups multiple dictionaries or other mappings into a single updatable view, searching through them in the order they were given.

<br>

### Basic Usage

> Creating and using ChainMap:

```python
from collections import ChainMap

# Create dictionaries
defaults = {'theme': 'dark', 'language': 'en'}
user_settings = {'theme': 'light'}

# Combine into ChainMap
settings = ChainMap(user_settings, defaults)

print(f"Theme: {settings['theme']}")        # From user_settings
print(f"Language: {settings['language']}")   # From defaults
print(f"All settings: {dict(settings)}")
```

```sh
Theme: light
Language: en
All settings: {'theme': 'light', 'language': 'en'}
```

<br>

### Search Order

> ChainMap searches mappings in order:

```python
dict1 = {'a': 1, 'b': 1}
dict2 = {'b': 2, 'c': 2}
dict3 = {'c': 3, 'd': 3}

chain = ChainMap(dict1, dict2, dict3)

# Demonstrate lookup order
print("Values found:")
for key in 'abcd':
    print(f"  {key}: {chain[key]}")

# Show all mappings
print("\nMappings:")
for i, mapping in enumerate(chain.maps):
    print(f"  {i}: {mapping}")
```

```sh
Values found:
  a: 1
  b: 1
  c: 2
  d: 3

Mappings:
  0: {'a': 1, 'b': 1}
  1: {'b': 2, 'c': 2}
  2: {'c': 3, 'd': 3}
```

<br>

### Methods and Properties

#### maps

> Access the list of underlying mappings:

```python
from collections import ChainMap

dict1 = {'a': 1}
dict2 = {'b': 2}
chain = ChainMap(dict1, dict2)

# Access and modify maps
print(f"Original maps: {chain.maps}")

# Add new mapping
dict3 = {'c': 3}
chain.maps.append(dict3)
print(f"After adding map: {chain.maps}")

# Modify first mapping
chain.maps[0]['d'] = 4
print(f"After modification: {dict(chain)}")
```

```sh
Original maps: [{'a': 1}, {'b': 2}]
After adding map: [{'a': 1}, {'b': 2}, {'c': 3}]
After modification: {'a': 1, 'b': 2, 'c': 3, 'd': 4}
```

<br>

#### new_child()

> - Syntax: `ChainMap.new_child(m=None)`
> - Return: New ChainMap with a new map followed by all current maps
> - Info: Creates a new ChainMap with a new map at the front

```python
base = ChainMap({'a': 1, 'b': 2})

# Create new child
child = base.new_child({'a': 3})
print(f"Base: {dict(base)}")
print(f"Child: {dict(child)}")

# Create empty child and update
empty_child = base.new_child()
empty_child['b'] = 4
print(f"Updated child: {dict(empty_child)}")
```

```sh
Base: {'a': 1, 'b': 2}
Child: {'a': 3, 'b': 2}
Updated child: {'b': 4, 'a': 1}
```

<br>

#### parents

> Access all maps except the first one:

```python
dict1 = {'a': 1, 'b': 1}
dict2 = {'b': 2, 'c': 2}
dict3 = {'c': 3, 'd': 3}

chain = ChainMap(dict1, dict2, dict3)
parent_chain = chain.parents

print(f"Full chain: {dict(chain)}")
print(f"Parents only: {dict(parent_chain)}")
```

```sh
Full chain: {'a': 1, 'b': 1, 'c': 2, 'd': 3}
Parents only: {'b': 2, 'c': 2, 'd': 3}
```

<br>

### Common Applications

#### Configuration Management

> Using ChainMap to handle multiple levels of configuration:

```python
from collections import ChainMap
import os

# Configuration with different priorities
defaults = {
    'debug': False,
    'port': 8000,
    'host': 'localhost'
}

user_config = {
    'port': 9000
}

cli_args = {
    'debug': True
}

# Combine configurations with priority
config = ChainMap(cli_args, user_config, defaults)

print("Configuration values:")
for key in ['debug', 'port', 'host']:
    print(f"  {key}: {config[key]}")
```

```sh
Configuration values:
  debug: True
  port: 9000
  host: localhost
```

<br>

#### Scope Management

> Implementing nested scopes similar to Python's name resolution:

```python
from collections import ChainMap

def scope_example():
    # Global scope
    globals = {'name': 'Global', 'value': 100}
    
    # Local scope
    locals = {}
    
    # Combined scope chain
    scope = ChainMap(locals, globals)
    
    # Access and modify values
    print(f"Initial name: {scope['name']}")
    
    # Add to local scope
    scope['name'] = 'Local'
    print(f"Modified name: {scope['name']}")
    print(f"Global unchanged: {globals['name']}")
    
    return locals, globals

local_vars, global_vars = scope_example()
print(f"Final locals: {local_vars}")
print(f"Final globals: {global_vars}")
```

```sh
Initial name: Global
Modified name: Local
Global unchanged: Global
Final locals: {'name': 'Local'}
Final globals: {'name': 'Global', 'value': 100}
```

<br>

### Performance Considerations

> Comparing ChainMap with dictionary update:

```python
import timeit
from collections import ChainMap

dict1 = {'a': 1, 'b': 2}
dict2 = {'c': 3, 'd': 4}
dict3 = {'e': 5, 'f': 6}

def using_chainmap():
    chain = ChainMap(dict1, dict2, dict3)
    return chain['a'], chain['c'], chain['e']

def using_dict_update():
    combined = {}
    for d in [dict3, dict2, dict1]:  # Reverse order for same precedence
        combined.update(d)
    return combined['a'], combined['c'], combined['e']

# Time comparison
chain_time = timeit.timeit(using_chainmap, number=100000)
update_time = timeit.timeit(using_dict_update, number=100000)

print(f"ChainMap time: {chain_time:.4f} seconds")
print(f"Dict update time: {update_time:.4f} seconds")
```

```sh
ChainMap time: 0.0234 seconds
Dict update time: 0.0567 seconds
```