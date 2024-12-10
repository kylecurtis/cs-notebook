# Function Basics

> Functions are reusable blocks of code that perform specific tasks. They provide a way to organize code, promote reusability, and break down complex problems into smaller, manageable pieces.

<br>

### Key Characteristics

> - Defined using the `def` keyword
> - Can accept multiple parameters
> - Can return values
> - Support default arguments
> - Allow keyword arguments
> - Support variable-length arguments
> - Enable argument unpacking

<br>

---

<br>

## Function Definition

> Functions are defined using the `def` keyword, followed by the function name and parameters in parentheses.

<br>

### Basic Function Definition

> Simple function with no parameters:

```python
def greet():
    print("Hello, World!")

# Calling the function
greet()
```

```sh
Hello, World!
```

<br>

### Function Body

> The function body contains the code to be executed:

```python
def process_data(value):
    # Local variable
    processed = value * 2
    
    # Multiple statements
    if processed > 10:
        print("Large value")
    else:
        print("Small value")
        
    # Return result
    return processed

# Test the function
print("Processing 4:")
result1 = process_data(4)
print(f"Result: {result1}")

print("\nProcessing 6:")
result2 = process_data(6)
print(f"Result: {result2}")
```

```sh
Processing 4:
Small value
Result: 8

Processing 6:
Large value
Result: 12
```

<br>

### Function Scope

> Variables defined inside functions are local to that function:

```python
def demonstrate_scope():
    # Local variable
    local_var = "I'm local"
    print(f"Inside function: {local_var}")
    
    # Modifying local variable
    local_var = "Modified local"
    print(f"Modified inside: {local_var}")

# Call function
demonstrate_scope()

# Try to access local variable
try:
    print(local_var)
except NameError as e:
    print(f"Error: {e}")
```

```sh
Inside function: I'm local
Modified inside: Modified local
Error: name 'local_var' is not defined
```

<br>

---

<br>

## Parameters and Arguments

> Parameters are variables listed in the function definition, while arguments are the values passed to the function when it is called.

<br>

### Basic Parameters

> Simple parameter passing:

```python
def greet(name):
    print(f"Hello, {name}!")

# Passing different arguments
greet("Alice")
greet("Bob")
```

```sh
Hello, Alice!
Hello, Bob!
```

<br>

### Multiple Parameters

> Functions can accept multiple parameters:

```python
def calculate_rectangle(length, width):
    area = length * width
    perimeter = 2 * (length + width)
    print(f"Length: {length}, Width: {width}")
    print(f"Area: {area}")
    print(f"Perimeter: {perimeter}")
    print("-" * 20)

# Using different arguments
calculate_rectangle(5, 3)
calculate_rectangle(4, 4)
```

```sh
Length: 5, Width: 3
Area: 15
Perimeter: 16
--------------------
Length: 4, Width: 4
Area: 16
Perimeter: 16
--------------------
```

<br>

### Parameter Order

> Arguments are matched to parameters in order:

```python
def describe_person(name, age, city):
    print(f"Name: {name}")
    print(f"Age: {age}")
    print(f"City: {city}")
    print("-" * 20)

# Arguments in correct order
describe_person("Alice", 30, "New York")

# Wrong order can lead to logical errors
describe_person("London", "Charlie", 25)  # Logically incorrect
```

```sh
Name: Alice
Age: 30
City: New York
--------------------
Name: London
Age: Charlie
City: 25
--------------------
```

<br>

### Type Hints

> Using type hints for better code documentation:

```python
def calculate_age(birth_year: int, current_year: int) -> int:
    return current_year - birth_year

# Using the function
age = calculate_age(1990, 2024)
print(f"Age: {age}")

# Type hints don't enforce types
age = calculate_age("1990", "2024")  # Works but not recommended
print(f"Age with strings: {age}")
```

```sh
Age: 34
Age with strings: 34
```

<br>

### Parameter Validation

> Checking parameter values:

```python
def divide_numbers(x: float, y: float) -> float:
    # Validate parameters
    if not isinstance(x, (int, float)) or not isinstance(y, (int, float)):
        raise TypeError("Arguments must be numbers")
        
    if y == 0:
        raise ValueError("Cannot divide by zero")
        
    return x / y

# Test with different arguments
try:
    print(f"10 / 2 = {divide_numbers(10, 2)}")
    print(f"10 / 0 = {divide_numbers(10, 0)}")
except ValueError as e:
    print(f"Error: {e}")

try:
    print(f"'10' / 2 = {divide_numbers('10', 2)}")
except TypeError as e:
    print(f"Error: {e}")
```

```sh
10 / 2 = 5.0
Error: Cannot divide by zero
Error: Arguments must be numbers
```

<br>

### Mutable Parameters

> Be careful with mutable default parameters:

```python
def add_to_list(item, items=None):
    if items is None:
        items = []
    items.append(item)
    return items

# Using the function
list1 = add_to_list("A")
print(f"First list: {list1}")

list2 = add_to_list("B")
print(f"Second list: {list2}")

# Adding to existing list
list3 = add_to_list("C", list1)
print(f"Third list: {list3}")
```

```sh
First list: ['A']
Second list: ['B']
Third list: ['A', 'C']
```

<br>

---

<br>

## Return Values

> Functions can return values using the `return` statement. A function can return single values, multiple values, or nothing (returns None by default).

<br>

### Basic Return

> Returning a single value:

```python
def square(number):
    return number ** 2

# Using the returned value
result = square(5)
print(f"Square of 5: {result}")

# Using return value directly in expressions
print(f"Square of 6: {square(6)}")
```

```sh
Square of 5: 25
Square of 6: 36
```

<br>

### Multiple Return Values

> Returning multiple values (returns as tuple):

```python
def get_statistics(numbers):
    if not numbers:
        return None, None, None
        
    minimum = min(numbers)
    maximum = max(numbers)
    average = sum(numbers) / len(numbers)
    
    return minimum, maximum, average

# Unpacking returned values
numbers = [1, 2, 3, 4, 5]
min_val, max_val, avg = get_statistics(numbers)
print(f"Numbers: {numbers}")
print(f"Minimum: {min_val}")
print(f"Maximum: {max_val}")
print(f"Average: {avg}")

# Handling empty input
empty_min, empty_max, empty_avg = get_statistics([])
print(f"\nEmpty list statistics: {empty_min}, {empty_max}, {empty_avg}")
```

```sh
Numbers: [1, 2, 3, 4, 5]
Minimum: 1
Maximum: 5
Average: 3.0

Empty list statistics: None, None, None
```

<br>

### Early Returns

> Using return for early function exit:

```python
def process_age(age):
    # Early return for invalid input
    if not isinstance(age, (int, float)):
        return "Invalid input: age must be a number"
    
    if age < 0:
        return "Invalid input: age cannot be negative"
        
    if age < 18:
        return "Minor"
    elif age < 65:
        return "Adult"
    else:
        return "Senior"

# Test different cases
ages = [15, 25, 70, -5, "invalid"]
for age in ages:
    result = process_age(age)
    print(f"Age {age}: {result}")
```

```sh
Age 15: Minor
Age 25: Adult
Age 70: Senior
Age -5: Invalid input: age cannot be negative
Age invalid: Invalid input: age must be a number
```

<br>

### Return with Side Effects

> Functions can have side effects before returning:

```python
def process_data(data):
    print("Starting data processing...")
    
    # Early return for empty data
    if not data:
        print("No data to process")
        return []
    
    processed = []
    for item in data:
        print(f"Processing item: {item}")
        processed.append(item * 2)
    
    print("Processing complete")
    return processed

# Test the function
data = [1, 2, 3]
result = process_data(data)
print(f"Result: {result}")

print("\nTesting with empty data:")
empty_result = process_data([])
print(f"Empty result: {empty_result}")
```

```sh
Starting data processing...
Processing item: 1
Processing item: 2
Processing item: 3
Processing complete
Result: [2, 4, 6]

Testing with empty data:
Starting data processing...
No data to process
Empty result: []
```

<br>

### Return Type Hints

> Using type hints to specify return types:

```python
from typing import List, Union, Optional

def process_numbers(numbers: List[float]) -> Optional[dict]:
    if not numbers:
        return None
        
    stats = {
        'count': len(numbers),
        'sum': sum(numbers),
        'average': sum(numbers) / len(numbers)
    }
    
    return stats

# Test the function
numbers = [1.5, 2.5, 3.5]
result = process_numbers(numbers)
print(f"Statistics: {result}")

empty_result = process_numbers([])
print(f"Empty statistics: {empty_result}")
```

```sh
Statistics: {'count': 3, 'sum': 7.5, 'average': 2.5}
Empty statistics: None
```

<br>

### Generator Returns

> Using return in generator functions:

```python
def number_generator(start: int, end: int):
    print(f"Starting generation from {start} to {end}")
    
    current = start
    while current <= end:
        if current % 5 == 0:
            print(f"Found multiple of 5: {current}")
            return  # Early return
        yield current
        current += 1

# Using the generator
print("Generating numbers:")
for num in number_generator(1, 10):
    print(f"Generated: {num}")
```

```sh
Generating numbers:
Starting generation from 1 to 10
Generated: 1
Generated: 2
Generated: 3
Generated: 4
Found multiple of 5: 5
```

<br>

---

<br>

## Default Arguments

> Default arguments allow functions to have optional parameters with predefined values.

<br>

### Basic Default Arguments

> Setting simple default values:

```python
def greet(name, greeting="Hello"):
    print(f"{greeting}, {name}!")

# Using default
greet("Alice")

# Overriding default
greet("Bob", "Hi")

# Using parameter name
greet("Charlie", greeting="Good morning")
```

```sh
Hello, Alice!
Hi, Bob!
Good morning, Charlie!
```

<br>

### Multiple Default Arguments

> Functions can have multiple default arguments:

```python
def create_profile(name, age=None, city="Unknown", active=True):
    profile = {
        "name": name,
        "age": age,
        "city": city,
        "active": active
    }
    return profile

# Different ways to use defaults
print("Default usage:")
print(create_profile("Alice"))

print("\nPartial override:")
print(create_profile("Bob", age=25))

print("\nFull specification:")
print(create_profile("Charlie", 30, "New York", False))
```

```sh
Default usage:
{'name': 'Alice', 'age': None, 'city': 'Unknown', 'active': True}

Partial override:
{'name': 'Bob', 'age': 25, 'city': 'Unknown', 'active': True}

Full specification:
{'name': 'Charlie', 'age': 30, 'city': 'New York', 'active': False}
```

<br>

### Mutable Default Arguments

> Warning about using mutable defaults:

```python
# Bad practice - mutable default
def add_item_bad(item, items=[]):
    items.append(item)
    return items

# Good practice - using None
def add_item_good(item, items=None):
    if items is None:
        items = []
    items.append(item)
    return items

# Demonstrating the issue with mutable defaults
print("Bad practice results:")
print(add_item_bad("A"))  # First call
print(add_item_bad("B"))  # Second call shares the same list

print("\nGood practice results:")
print(add_item_good("A"))  # First call
print(add_item_good("B"))  # Second call gets fresh list
```

```sh
Bad practice results:
['A']
['A', 'B']

Good practice results:
['A']
['B']
```

<br>

### Dynamic Default Values

> Using function calls for default values:

```python
from datetime import datetime

def log_message(message, timestamp=None):
    if timestamp is None:
        timestamp = datetime.now()
    return f"[{timestamp}] {message}"

# Using default timestamp
print(log_message("First message"))

# Simulating time passing
import time
time.sleep(1)  # Wait 1 second

# Another message
print(log_message("Second message"))

# Providing specific timestamp
specific_time = datetime(2024, 1, 1, 12, 0)
print(log_message("Custom time message", specific_time))
```

```sh
[2024-03-15 14:30:00.123456] First message
[2024-03-15 14:30:01.123456] Second message
[2024-01-01 12:00:00] Custom time message
```

<br>

### Default Arguments with Type Hints

> Combining default arguments with type hints:

```python
from typing import Optional, List, Union

def process_data(
    value: Union[int, float],
    multiplier: float = 1.0,
    label: Optional[str] = None,
    tags: Optional[List[str]] = None
) -> dict:
    if tags is None:
        tags = []
        
    result = {
        "value": value * multiplier,
        "label": label or "No label",
        "tags": tags
    }
    
    return result

# Different usage patterns
print("Basic usage:")
print(process_data(10))

print("\nWith multiplier:")
print(process_data(10, 2.5))

print("\nWith all parameters:")
print(process_data(10, 2.5, "Test", ["important", "verified"]))
```

```sh
Basic usage:
{'value': 10.0, 'label': 'No label', 'tags': []}

With multiplier:
{'value': 25.0, 'label': 'No label', 'tags': []}

With all parameters:
{'value': 25.0, 'label': 'Test', 'tags': ['important', 'verified']}
```

<br>

---

<br>

## Keyword Arguments

> Keyword arguments allow you to pass arguments to functions using the parameter names, making code more readable and flexible.

<br>

### Basic Keyword Arguments

> Passing arguments by parameter name:

```python
def create_user(username, email, age):
    return {
        'username': username,
        'email': email,
        'age': age
    }

# Using positional arguments
user1 = create_user('alice123', 'alice@email.com', 25)
print(f"User 1: {user1}")

# Using keyword arguments
user2 = create_user(
    email='bob@email.com',
    age=30,
    username='bob456'
)
print(f"User 2: {user2}")
```

```sh
User 1: {'username': 'alice123', 'email': 'alice@email.com', 'age': 25}
User 2: {'username': 'bob456', 'email': 'bob@email.com', 'age': 30}
```

<br>

### Mixing Positional and Keyword Arguments

> Combining both argument types:

```python
def format_address(street, city, state, zip_code, country="USA"):
    return f"{street}\n{city}, {state} {zip_code}\n{country}"

# Mixed usage
address1 = format_address(
    "123 Main St",
    city="Springfield",
    state="IL",
    zip_code="62701"
)

print("Address 1:")
print(address1)

print("\nAddress 2:")
print(format_address(
    "456 Oak Ave",
    "Boston",
    state="MA",
    zip_code="02101",
    country="United States"
))
```

```sh
Address 1:
123 Main St
Springfield, IL 62701
USA

Address 2:
456 Oak Ave
Boston, MA 02101
United States
```

<br>

### Keyword-Only Arguments

> Forcing arguments to be passed by keyword:

```python
def configure_app(*, host="localhost", port=8000, debug=False):
    config = {
        "host": host,
        "port": port,
        "debug": debug
    }
    return config

# This works (keyword arguments)
config1 = configure_app(port=8080, debug=True)
print(f"Config 1: {config1}")

# This raises an error (positional arguments)
try:
    config2 = configure_app("127.0.0.1", 9000)
except TypeError as e:
    print(f"Error: {e}")
```

```sh
Config 1: {'host': 'localhost', 'port': 8080, 'debug': True}
Error: configure_app() takes 0 positional arguments but 2 were given
```

<br>

### Position-Only Arguments

> Forcing arguments to be passed by position (Python 3.8+):

```python
def divide(a, b, /):
    return a / b

# This works (positional arguments)
print(f"10 / 2 = {divide(10, 2)}")

# This raises an error (keyword arguments)
try:
    result = divide(a=10, b=2)
except TypeError as e:
    print(f"Error: {e}")
```

```sh
10 / 2 = 5.0
Error: divide() got some positional-only arguments passed as keyword arguments: 'a, b'
```

<br>

### Mixed Parameter Types

> Combining different parameter types:

```python
def process_data(x, y, /, standard, *, config):
    return {
        'x': x,
        'y': y,
        'standard': standard,
        'config': config
    }

# Correct usage
result1 = process_data(1, 2, 
                      standard="normal",
                      config={"mode": "test"})
print(f"Result 1: {result1}")

# Incorrect usage examples
try:
    # Can't use keyword for x, y
    result2 = process_data(x=1, y=2,
                          standard="normal",
                          config={})
except TypeError as e:
    print(f"\nError 1: {e}")

try:
    # Must use keyword for config
    result3 = process_data(1, 2, "normal", {})
except TypeError as e:
    print(f"Error 2: {e}")
```

```sh
Result 1: {'x': 1, 'y': 2, 'standard': 'normal', 'config': {'mode': 'test'}}

Error 1: process_data() got some positional-only arguments passed as keyword arguments: 'x, y'
Error 2: process_data() missing 1 required keyword-only argument: 'config'
```

<br>

---

<br>

## Variable-Length Arguments

> Python allows functions to accept any number of arguments using *args for positional arguments and **kwargs for keyword arguments.

<br>

### *args (Variable Positional Arguments)

> Accepting any number of positional arguments:

```python
def sum_all(*args):
    total = 0
    for num in args:
        total += num
    return total

# Different numbers of arguments
print(f"Sum of 1, 2: {sum_all(1, 2)}")
print(f"Sum of 1, 2, 3, 4: {sum_all(1, 2, 3, 4)}")
print(f"No arguments: {sum_all()}")
```

```sh
Sum of 1, 2: 3
Sum of 1, 2, 3, 4: 10
No arguments: 0
```

<br>

### **kwargs (Variable Keyword Arguments)

> Accepting any number of keyword arguments:

```python
def create_person(**kwargs):
    print(f"Creating person with attributes: {kwargs}")
    return kwargs

# Different keyword arguments
person1 = create_person(name="Alice", age=30)
print(f"Person 1: {person1}")

person2 = create_person(
    name="Bob",
    age=25,
    city="New York",
    occupation="Developer"
)
print(f"Person 2: {person2}")
```

```sh
Creating person with attributes: {'name': 'Alice', 'age': 30}
Person 1: {'name': 'Alice', 'age': 30}
Creating person with attributes: {'name': 'Bob', 'age': 25, 'city': 'New York', 'occupation': 'Developer'}
Person 2: {'name': 'Bob', 'age': 25, 'city': 'New York', 'occupation': 'Developer'}
```

<br>

### Combining *args and **kwargs

> Using both variable-length argument types:

```python
def process_data(*args, **kwargs):
    print(f"Positional arguments: {args}")
    print(f"Keyword arguments: {kwargs}")
    print("-" * 40)

# Different combinations
process_data(1, 2, 3)
process_data(x=1, y=2)
process_data(1, 2, name="test", value=42)
```

```sh
Positional arguments: (1, 2, 3)
Keyword arguments: {}
----------------------------------------
Positional arguments: ()
Keyword arguments: {'x': 1, 'y': 2}
----------------------------------------
Positional arguments: (1, 2)
Keyword arguments: {'name': 'test', 'value': 42}
```

<br>

### Argument Forwarding

> Passing arguments to other functions:

```python
def log_call(func_name, *args, **kwargs):
    print(f"Calling {func_name}")
    print(f"Args: {args}")
    print(f"Kwargs: {kwargs}")
    print("-" * 40)

def create_user(username, email, **extra):
    user = {
        'username': username,
        'email': email,
        **extra
    }
    # Log the call
    log_call('create_user', username, email, **extra)
    return user

# Create users with different extra fields
user1 = create_user("alice", "alice@email.com")
user2 = create_user("bob", "bob@email.com",
                   age=25,
                   city="London")
```

```sh
Calling create_user
Args: ('alice', 'alice@email.com')
Kwargs: {}
----------------------------------------
Calling create_user
Args: ('bob', 'bob@email.com')
Kwargs: {'age': 25, 'city': 'London'}
----------------------------------------
```

<br>

### Type Hints with Variable Arguments

> Using type hints for variable-length arguments:

```python
from typing import Any, Dict

def process_values(*args: int, **kwargs: Any) -> Dict[str, Any]:
    result = {
        'sum': sum(args),
        'count': len(args),
        'extras': kwargs
    }
    return result

# Test the function
result1 = process_values(1, 2, 3, name="test")
print(f"Result 1: {result1}")

result2 = process_values(10, 20, category="A", active=True)
print(f"Result 2: {result2}")
```

```sh
Result 1: {'sum': 6, 'count': 3, 'extras': {'name': 'test'}}
Result 2: {'sum': 30, 'count': 2, 'extras': {'category': 'A', 'active': True}}
```

<br>

---

<br>

## Unpacking Arguments

> Python allows you to unpack sequences into positional arguments using * and dictionaries into keyword arguments using **.

<br>

### Sequence Unpacking

> Unpacking lists and tuples into positional arguments:

```python
def calculate_stats(x, y, z):
    return {
        'sum': x + y + z,
        'average': (x + y + z) / 3,
        'max': max(x, y, z)
    }

# Using a list
numbers = [1, 2, 3]
result1 = calculate_stats(*numbers)
print(f"Stats from list: {result1}")

# Using a tuple
coordinates = (4, 5, 6)
result2 = calculate_stats(*coordinates)
print(f"Stats from tuple: {result2}")
```

```sh
Stats from list: {'sum': 6, 'average': 2.0, 'max': 3}
Stats from tuple: {'sum': 15, 'average': 5.0, 'max': 6}
```

<br>

### Dictionary Unpacking

> Unpacking dictionaries into keyword arguments:

```python
def create_user(username, email, age):
    return {
        'username': username,
        'email': email,
        'age': age
    }

# Unpack dictionary into keyword arguments
user_data = {
    'username': 'alice123',
    'email': 'alice@email.com',
    'age': 30
}

user = create_user(**user_data)
print(f"Created user: {user}")

# Partial dictionary with remaining direct arguments
partial_data = {
    'username': 'bob456',
    'age': 25
}

user2 = create_user(**partial_data, email='bob@email.com')
print(f"Created user 2: {user2}")
```

```sh
Created user: {'username': 'alice123', 'email': 'alice@email.com', 'age': 30}
Created user 2: {'username': 'bob456', 'email': 'bob@email.com', 'age': 25}
```

<br>

### Combined Unpacking

> Using both sequence and dictionary unpacking:

```python
def format_data(id_number, *values, **metadata):
    return {
        'id': id_number,
        'values': values,
        'metadata': metadata
    }

# Prepare data for unpacking
values = [1, 2, 3]
metadata = {
    'timestamp': '2024-03-15',
    'category': 'test'
}

# Combined unpacking
result = format_data(100, *values, **metadata)
print(f"Formatted data: {result}")

# Multiple sequence unpacking
sequences = [1, 2], [3, 4, 5]
result2 = format_data(200, *sequences[0], *sequences[1])
print(f"Multiple sequence unpacking: {result2}")
```

```sh
Formatted data: {'id': 100, 'values': (1, 2, 3), 'metadata': {'timestamp': '2024-03-15', 'category': 'test'}}
Multiple sequence unpacking: {'id': 200, 'values': (1, 2, 3, 4, 5), 'metadata': {}}
```

<br>

### Unpacking in List/Dict Literals

> Using unpacking within literals:

```python
def merge_configurations(*configs):
    base_config = {
        'debug': False,
        'port': 8000
    }
    
    return {
        **base_config,
        **dict(enumerate(configs))
    }

# Merge configurations
config1 = {'port': 9000}
config2 = {'debug': True}

merged = merge_configurations(config1, config2)
print(f"Merged config: {merged}")

# List unpacking
numbers = [1, 2, 3]
more_numbers = [0, *numbers, 4]
print(f"Extended numbers: {more_numbers}")
```

```sh
Merged config: {'debug': True, 'port': 8000, 0: {'port': 9000}, 1: {'debug': True}}
Extended numbers: [0, 1, 2, 3, 4]
```

<br>

### Common Patterns

> Useful patterns with argument unpacking:

```python
def demonstrate_patterns():
    # Merging dictionaries
    defaults = {'timeout': 30, 'retries': 3}
    user_config = {'timeout': 60}
    final_config = {**defaults, **user_config}
    print(f"Merged config: {final_config}")
    
    # Extending sequences
    base_items = [1, 2, 3]
    extended = [*base_items, *range(4, 6)]
    print(f"Extended sequence: {extended}")
    
    # Combining positional and keyword arguments
    def process(x, y, **options):
        return x + y, options
    
    coords = [10, 20]
    settings = {'unit': 'px', 'scale': 2}
    
    result = process(*coords, **settings)
    print(f"Processed result: {result}")

demonstrate_patterns()
```

```sh
Merged config: {'timeout': 60, 'retries': 3}
Extended sequence: [1, 2, 3, 4, 5]
Processed result: (30, {'unit': 'px', 'scale': 2})
```