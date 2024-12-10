# Python Tuples

> Python tuples are immutable sequences, meaning once created, their elements cannot be changed. They serve as a fundamental data structure for representing fixed collections of items.

<br>

### Key Characteristics

> - Immutable (cannot be modified after creation)
> - Ordered sequence of elements
> - Can contain items of different types
> - Support for nesting
> - Hashable (if all elements are hashable)
> - Memory efficient compared to lists
> - Used for packing/unpacking operations

<br>

---

<br>

## Tuple Creation

> Python provides several ways to create tuples:

<br>

### Direct Creation

> Using parentheses (optional for unambiguous cases):

```python
# With parentheses
numbers = (1, 2, 3)
print(numbers)
```

```sh
(1, 2, 3)
```

<br>

> Without parentheses (tuple packing):

```python
numbers = 1, 2, 3
print(numbers)
```

```sh
(1, 2, 3)
```

<br>

### Single Element Tuples

> Creating a tuple with one element requires a trailing comma:

```python
# Without comma (creates an integer)
not_tuple = (1)
print(f"Type: {type(not_tuple)}, Value: {not_tuple}")

# With comma (creates a tuple)
single_tuple = (1,)
print(f"Type: {type(single_tuple)}, Value: {single_tuple}")
```

```sh
Type: <class 'int'>, Value: 1
Type: <class 'tuple'>, Value: (1,)
```

<br>

### Tuple Constructor

> Using the tuple() constructor to create tuples from iterables:

```python
# From list
list_to_tuple = tuple([1, 2, 3])
print(f"From list: {list_to_tuple}")

# From string
string_to_tuple = tuple("Python")
print(f"From string: {string_to_tuple}")

# From range
range_to_tuple = tuple(range(3))
print(f"From range: {range_to_tuple}")
```

```sh
From list: (1, 2, 3)
From string: ('P', 'y', 't', 'h', 'o', 'n')
From range: (0, 1, 2)
```

<br>

### Empty Tuple

> Creating an empty tuple:

```python
# Using parentheses
empty_tuple1 = ()
print(f"Empty tuple 1: {empty_tuple1}")

# Using constructor
empty_tuple2 = tuple()
print(f"Empty tuple 2: {empty_tuple2}")
```

```sh
Empty tuple 1: ()
Empty tuple 2: ()
```

<br>

### Nested Tuples

> Creating tuples containing other tuples:

```python
# Nested structure
nested = (1, (2, 3), (4, 5, 6))
print(f"Nested tuple: {nested}")
print(f"Second element: {nested[1]}")
print(f"Access nested element: {nested[1][0]}")
```

```sh
Nested tuple: (1, (2, 3), (4, 5, 6))
Second element: (2, 3)
Access nested element: 2
```

<br>

---

<br>

## Named Tuples

> Named tuples are tuple subclasses that allow accessing elements by name instead of just index. They provide a way to create simple classes that are both readable and efficient.

<br>

### Creating Named Tuples

> Using collections.namedtuple:

```python
from collections import namedtuple

# Create a named tuple class
Point = namedtuple('Point', ['x', 'y'])

# Create instance
p = Point(1, 2)
print(f"Point: {p}")
print(f"x coordinate: {p.x}")
print(f"y coordinate: {p.y}")
```

```sh
Point: Point(x=1, y=2)
x coordinate: 1
y coordinate: 2
```

<br>

### Alternative Field Specification

> Different ways to specify field names:

```python
from collections import namedtuple

# Space-separated string
Person = namedtuple('Person', 'name age')

# Comma-separated string
Point = namedtuple('Point', 'x, y')

# List of strings
Car = namedtuple('Car', ['make', 'model', 'year'])

# Test each type
person = Person('Alice', 30)
point = Point(3, 4)
car = Car('Toyota', 'Corolla', 2020)

print(f"Person: {person}")
print(f"Point: {point}")
print(f"Car: {car}")
```

```sh
Person: Person(name='Alice', age=30)
Point: Point(x=3, y=4)
Car: Car(make='Toyota', model='Corolla', year=2020)
```

<br>

### Named Tuple Features

> Special attributes and methods:

```python
Point = namedtuple('Point', ['x', 'y'])
p = Point(1, 2)

# Get field names
print(f"Field names: {p._fields}")

# Convert to dictionary
print(f"As dictionary: {p._asdict()}")

# Create new instance with updated values
p2 = p._replace(x=10)
print(f"After replace: {p2}")

# Original remains unchanged (immutable)
print(f"Original: {p}")
```

```sh
Field names: ('x', 'y')
As dictionary: {'x': 1, 'y': 2}
After replace: Point(x=10, y=2)
Original: Point(x=1, y=2)
```

<br>

### Creating from Dictionary

> Converting dictionary to named tuple:

```python
from collections import namedtuple

# Define the named tuple class
Person = namedtuple('Person', 'name age city')

# Dictionary of data
data = {'name': 'Bob', 'age': 25, 'city': 'New York'}

# Create using ** unpacking
person = Person(**data)
print(f"From dictionary: {person}")
print(f"Access name: {person.name}")
```

```sh
From dictionary: Person(name='Bob', age=25, city='New York')
Access name: Bob
```

<br>

### Default Values

> Setting default values for fields:

```python
from collections import namedtuple

# Create named tuple with defaults
Settings = namedtuple('Settings', ['host', 'port', 'user', 'timeout'],
                     defaults=['localhost', 8080, 'admin', 30])

# Create with some values
s1 = Settings()  # All defaults
s2 = Settings('example.com')  # Override first value
s3 = Settings('example.com', 9000, 'root')  # Override multiple values

print(f"Default settings: {s1}")
print(f"Custom host: {s2}")
print(f"Multiple custom values: {s3}")
```

```sh
Default settings: Settings(host='localhost', port=8080, user='admin', timeout=30)
Custom host: Settings(host='example.com', port=8080, user='admin', timeout=30)
Multiple custom values: Settings(host='example.com', port=9000, user='root', timeout=30)
```

<br>

### Type Hints with Named Tuples

> Using type hints with named tuples:

```python
from typing import NamedTuple

class Point(NamedTuple):
    x: float
    y: float
    label: str = ''  # Optional field with default

# Create instances
p1 = Point(1.0, 2.0)
p2 = Point(3.0, 4.0, 'Center')

print(f"Point 1: {p1}")
print(f"Point 2: {p2}")
```

```sh
Point 1: Point(x=1.0, y=2.0, label='')
Point 2: Point(x=3.0, y=4.0, label='Center')
```

<br>

### Memory Usage

> Comparing memory usage with regular tuples and classes:

```python
from collections import namedtuple
import sys

# Regular tuple
regular_tuple = (1, 2)

# Named tuple
Point = namedtuple('Point', ['x', 'y'])
named_tuple = Point(1, 2)

# Equivalent class
class PointClass:
    def __init__(self, x, y):
        self.x = x
        self.y = y

point_class = PointClass(1, 2)

print(f"Regular tuple size: {sys.getsizeof(regular_tuple)} bytes")
print(f"Named tuple size: {sys.getsizeof(named_tuple)} bytes")
print(f"Class instance size: {sys.getsizeof(point_class)} bytes")
```

```sh
Regular tuple size: 56 bytes
Named tuple size: 72 bytes
Class instance size: 48 bytes
```

<br>

---

<br>

## Tuple Methods

> Tuples have a limited set of methods due to their immutable nature, but they support many sequence operations.

<br>

### count()

> - Syntax: `tuple.count(value)`
> - Return: `int`
> - Info: Returns the number of occurrences of a value in the tuple
> - Time Complexity: O(n)

```python
numbers = (1, 2, 2, 3, 2, 4)
count = numbers.count(2)
print(f"Tuple: {numbers}")
print(f"Count of 2: {count}")
```

```sh
Tuple: (1, 2, 2, 3, 2, 4)
Count of 2: 3
```

<br>

### index()

> - Syntax: `tuple.index(value[, start[, stop]])`
> - Return: `int`
> - Info: Returns the index of the first occurrence of value
> - Raises: `ValueError` if value not found
> - Time Complexity: O(n)

```python
numbers = (1, 2, 3, 2, 4)

# Basic index search
print(f"Index of 2: {numbers.index(2)}")

# Search with start position
print(f"Index of 2 after position 2: {numbers.index(2, 2)}")

# Search within range
print(f"Index of 2 between positions 1 and 3: {numbers.index(2, 1, 3)}")

# Value not in tuple
try:
    numbers.index(5)
except ValueError as e:
    print(f"Error: {e}")
```

```sh
Index of 2: 1
Index of 2 after position 2: 3
Index of 2 between positions 1 and 3: 1
Error: tuple.index(x): x not in tuple
```

<br>

### Sequence Operations

> Tuples support various sequence operations:

<br>

#### Concatenation

> Using the + operator to combine tuples:

```python
t1 = (1, 2)
t2 = (3, 4)
combined = t1 + t2
print(f"Combined tuple: {combined}")
```

```sh
Combined tuple: (1, 2, 3, 4)
```

<br>

#### Repetition

> Using the * operator to repeat tuples:

```python
base = (1, 2)
repeated = base * 3
print(f"Repeated tuple: {repeated}")
```

```sh
Repeated tuple: (1, 2, 1, 2, 1, 2)
```

<br>

#### Slicing

> Extracting portions of tuples:

```python
numbers = (0, 1, 2, 3, 4, 5)

# Basic slicing
print(f"First three: {numbers[:3]}")
print(f"Last three: {numbers[-3:]}")
print(f"Every second item: {numbers[::2]}")
print(f"Reversed: {numbers[::-1]}")
```

```sh
First three: (0, 1, 2)
Last three: (3, 4, 5)
Every second item: (0, 2, 4)
Reversed: (5, 4, 3, 2, 1, 0)
```

<br>

#### Membership Testing

> Using in and not in operators:

```python
numbers = (1, 2, 3, 4, 5)

print(f"Is 3 in tuple? {3 in numbers}")
print(f"Is 6 in tuple? {6 in numbers}")
print(f"Is 6 not in tuple? {6 not in numbers}")
```

```sh
Is 3 in tuple? True
Is 6 in tuple? False
Is 6 not in tuple? True
```

<br>

#### Length and Min/Max

> Built-in functions for tuples:

```python
numbers = (3, 1, 4, 1, 5, 9)

print(f"Length: {len(numbers)}")
print(f"Minimum: {min(numbers)}")
print(f"Maximum: {max(numbers)}")
print(f"Sum: {sum(numbers)}")
```

```sh
Length: 6
Minimum: 1
Maximum: 9
Sum: 23
```

<br>

### Comparison Operations

> Tuples support all comparison operators:

```python
t1 = (1, 2, 3)
t2 = (1, 2, 4)
t3 = (1, 2, 3)

print(f"t1 == t3: {t1 == t3}")  # True (same elements)
print(f"t1 < t2: {t1 < t2}")    # True (compared element by element)
print(f"t2 > t3: {t2 > t3}")    # True (first different element decides)
```

```sh
t1 == t3: True
t1 < t2: True
t2 > t3: True
```

<br>

---

<br>

## Tuple vs List Comparison

> Understanding the key differences between tuples and lists helps in choosing the right data structure for your needs.

<br>

### Mutability

> The primary difference is that lists are mutable while tuples are immutable:

```python
# List modification
lst = [1, 2, 3]
lst[0] = 10
print(f"Modified list: {lst}")

# Tuple modification attempt
tup = (1, 2, 3)
try:
    tup[0] = 10
except TypeError as e:
    print(f"Tuple modification error: {e}")
```

```sh
Modified list: [10, 2, 3]
Tuple modification error: 'tuple' object does not support item assignment
```

<br>

### Memory Usage

> Comparing memory usage between tuples and lists:

```python
import sys

# Compare empty containers
empty_list = []
empty_tuple = ()
print(f"Empty list size: {sys.getsizeof(empty_list)} bytes")
print(f"Empty tuple size: {sys.getsizeof(empty_tuple)} bytes")

# Compare with same elements
data_list = [1, 2, 3, 4, 5]
data_tuple = (1, 2, 3, 4, 5)
print(f"List with 5 elements: {sys.getsizeof(data_list)} bytes")
print(f"Tuple with 5 elements: {sys.getsizeof(data_tuple)} bytes")
```

```sh
Empty list size: 56 bytes 
Empty tuple size: 40 bytes 
List with 5 elements: 104 bytes 
Tuple with 5 elements: 80 bytes
```

<br>

### Performance Comparison

> Measuring creation and access times:

```python
import timeit

# Creation performance
list_creation = timeit.timeit("lst = [1, 2, 3, 4, 5]", number=1000000)
tuple_creation = timeit.timeit("tup = (1, 2, 3, 4, 5)", number=1000000)

print(f"List creation time: {list_creation:.4f} seconds")
print(f"Tuple creation time: {tuple_creation:.4f} seconds")

# Access performance
setup = """
lst = [1, 2, 3, 4, 5]
tup = (1, 2, 3, 4, 5)
"""
list_access = timeit.timeit("x = lst[2]", setup=setup, number=1000000)
tuple_access = timeit.timeit("x = tup[2]", setup=setup, number=1000000)

print(f"List access time: {list_access:.4f} seconds")
print(f"Tuple access time: {tuple_access:.4f} seconds")
```

```sh
List creation time: 0.0466 seconds 
Tuple creation time: 0.0108 seconds 
List access time: 0.0177 seconds 
Tuple access time: 0.0170 seconds
```

<br>

### Usage Scenarios

> When to use tuples vs lists:

```python
# Tuple: Natural for representing fixed data structures
Point = (2, 3)
RGB = (255, 128, 0)
CardinalDirections = ('N', 'S', 'E', 'W')

# List: Natural for collections that may change
scores = [10, 20, 30]  # Can add more scores
commands = ['start', 'stop']  # Can add more commands

print("Tuple examples:")
print(f"Point coordinates: {Point}")
print(f"RGB color: {RGB}")
print(f"Directions: {CardinalDirections}")

print("\nList examples:")
print(f"Initial scores: {scores}")
scores.append(40)
print(f"Updated scores: {scores}")
```

```sh
Tuple examples:
Point coordinates: (2, 3)
RGB color: (255, 128, 0)
Directions: ('N', 'S', 'E', 'W')

List examples:
Initial scores: [10, 20, 30]
Updated scores: [10, 20, 30, 40]
```

<br>

### Dictionary Keys

> Tuples can be dictionary keys, lists cannot:

```python
# Tuple as dictionary key
coordinate_values = {(0, 0): 'origin', (1, 0): 'right', (0, 1): 'up'}
print(f"Value at origin: {coordinate_values[(0, 0)]}")

# List as dictionary key attempt
try:
    bad_dict = {[0, 0]: 'origin'}
except TypeError as e:
    print(f"List as key error: {e}")
```

```sh
Value at origin: origin
List as key error: unhashable type: 'list'
```

<br>

### Feature Comparison Table

> Key differences between tuples and lists:

Feature | Tuple | List
--------|-------|------
Mutability | Immutable | Mutable
Syntax | Parentheses () | Square brackets []
Memory Usage | Less | More
Performance | Slightly faster | Slightly slower
Usage as Dict Keys | Yes | No
Common Use Case | Fixed data, Records | Dynamic collections
Methods Available | 2 (count, index) | 11+ methods

<br>

### Common Operations Comparison

> Showing equivalent operations between tuples and lists:

```python
# List operations
lst = [1, 2, 3]
lst.append(4)
lst.extend([5, 6])
print(f"Modified list: {lst}")

# Tuple equivalent operations
tup = (1, 2, 3)
tup = tup + (4,)        # Create new tuple
tup = tup + (5, 6)      # Create new tuple
print(f"New tuple: {tup}")

# Length and iteration work the same
print(f"List length: {len(lst)}")
print(f"Tuple length: {len(tup)}")
```

```sh
Modified list: [1, 2, 3, 4, 5, 6]
New tuple: (1, 2, 3, 4, 5, 6)
List length: 6
Tuple length: 6
```

<br>

---

<br>

## Tuple Performance

> Understanding tuple performance characteristics is crucial for optimal usage in Python applications.

<br>

### Memory Allocation

> Examining how tuples allocate memory compared to lists:

```python
import sys

def measure_size(n):
    lst = list(range(n))
    tup = tuple(range(n))
    return sys.getsizeof(lst), sys.getsizeof(tup)

sizes = [(0, "Empty"), (5, "Small"), (50, "Medium"), (500, "Large")]

for n, label in sizes:
    list_size, tuple_size = measure_size(n)
    print(f"{label} ({n} elements):")
    print(f"  List size: {list_size} bytes")
    print(f"  Tuple size: {tuple_size} bytes")
```

```sh
Empty (0 elements):
  List size: 56 bytes
  Tuple size: 40 bytes
Small (5 elements):
  List size: 104 bytes
  Tuple size: 80 bytes
Medium (50 elements):
  List size: 456 bytes
  Tuple size: 440 bytes
Large (500 elements):
  List size: 4056 bytes
  Tuple size: 4040 bytes
```

<br>

### Operation Performance

> Time complexity comparison of common operations:

Operation | Time Complexity | Notes
----------|----------------|-------
Creation | O(n) | Linear with size
Access | O(1) | Constant time
Count | O(n) | Linear scan
Index | O(n) | Linear scan
Slice | O(k) | k = slice size
Hash | O(n) | For use as dict key

<br>

### Performance Benchmarks

> Comparing different operations between tuples and lists:

```python
import timeit

def benchmark_comparison(size=1000):
    setup = f"""
data_list = list(range({size}))
data_tuple = tuple(range({size}))
"""
    
    tests = {
        'Creation': {
            'list': f'list(range({size}))',
            'tuple': f'tuple(range({size}))'
        },
        'Access': {
            'list': 'data_list[500]',
            'tuple': 'data_tuple[500]'
        },
        'Slice': {
            'list': 'data_list[100:200]',
            'tuple': 'data_tuple[100:200]'
        },
        'Count': {
            'list': 'data_list.count(500)',
            'tuple': 'data_tuple.count(500)'
        }
    }
    
    for operation, implementations in tests.items():
        print(f"\n{operation} Performance:")
        for type_name, code in implementations.items():
            time = timeit.timeit(code, setup, number=10000)
            print(f"  {type_name}: {time:.6f} seconds")

benchmark_comparison()
```

```sh
Creation Performance:
  list: 0.127542 seconds
  tuple: 0.126450 seconds

Access Performance:
  list: 0.000155 seconds
  tuple: 0.000209 seconds

Slice Performance:
  list: 0.002734 seconds
  tuple: 0.002445 seconds

Count Performance:
  list: 0.086209 seconds
  tuple: 0.076193 seconds
```

<br>

### Memory Usage Patterns

> Understanding memory behavior with nested structures:

```python
import sys

# Compare flat vs nested structures
flat_tuple = (1, 2, 3, 4)
nested_tuple = ((1, 2), (3, 4))
deep_nested = (((1, 2),), ((3, 4),))

print(f"Flat tuple size: {sys.getsizeof(flat_tuple)} bytes")
print(f"Nested tuple size: {sys.getsizeof(nested_tuple)} bytes")
print(f"Deep nested size: {sys.getsizeof(deep_nested)} bytes")

# Memory for individual elements
total_nested = (sys.getsizeof(nested_tuple) + 
                sys.getsizeof((1, 2)) + 
                sys.getsizeof((3, 4)))
print(f"Total nested memory: {total_nested} bytes")
```

```sh
Flat tuple size: 72 bytes
Nested tuple size: 56 bytes
Deep nested size: 56 bytes
Total nested memory: 168 bytes
```

<br>

### Optimization Strategies

> Best practices for optimal tuple usage:

```python
# Efficient tuple concatenation
def bad_concatenation(n):
    result = ()
    for i in range(n):
        result = result + (i,)  # Creates new tuple each time
    return result

def good_concatenation(n):
    return tuple(range(n))  # Creates tuple once

# Compare performance
n = 1000
bad_time = timeit.timeit(lambda: bad_concatenation(n), number=100)
good_time = timeit.timeit(lambda: good_concatenation(n), number=100)

print(f"Bad concatenation time: {bad_time:.4f} seconds")
print(f"Good concatenation time: {good_time:.4f} seconds")
```

```sh
Bad concatenation time: 0.1193 seconds
Good concatenation time: 0.0012 seconds
```

<br>

### Best Practices

> Guidelines for optimal tuple performance:

1. Creation Patterns
```python
# Prefer direct creation over concatenation
good = (1, 2, 3, 4)  # Better
bad = () + (1,) + (2,) + (3,) + (4,)  # Worse

# Use tuple() constructor for iterables
numbers = tuple(range(5))  # Efficient
```

<br>

2. Memory Management
```python
# Reuse tuples when possible
coordinates = [(x, y) for x, y in zip(range(3), range(3))]
unique_coords = list(set(coordinates))  # Tuples are hashable
```

<br>

3. Performance Tips
```python
def demonstrate_tips():
    # Use tuple unpacking
    point = (3, 4)
    x, y = point  # More efficient than indexing
    
    # Prefer tuple over list for immutable sequences
    CONSTANTS = (1, 2, 3)  # Better than list for fixed data
    
    return x, y  # Return tuple directly

x, y = demonstrate_tips()
print(f"Unpacked values: x={x}, y={y}")
```

```sh
Unpacked values: x=3, y=4
```

