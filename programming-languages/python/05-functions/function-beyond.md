# Advanced Functions

> Python provides several advanced function features that enable functional programming paradigms, code optimization, and enhanced type safety.

<br>

### Key Characteristics

> - Anonymous functions with lambda
> - Function closures and state retention
> - Function modification with decorators
> - Type information with annotations
> - Static type checking with type hints
> - Function composition with partial functions
> - Self-referential calls with recursion
> - Performance optimization with caching

<br>

---

<br>

## Lambda Functions

> Lambda functions are small anonymous functions that can have any number of arguments but can only have one expression.

<br>

### Basic Lambda Syntax

> Creating and using simple lambda functions:

```python
# Lambda function
square = lambda x: x**2

# Regular function equivalent
def square_regular(x):
    return x**2

# Compare both
print(f"Lambda result: {square(5)}")
print(f"Regular result: {square_regular(5)}")

# Lambda type
print(f"Lambda type: {type(square)}")
```

```sh
Lambda result: 25
Regular result: 25
Lambda type: <class 'function'>
```

<br>

### Lambda with Multiple Arguments

> Using lambda functions with multiple inputs:

```python
# Multiple arguments
multiply = lambda x, y: x * y
average = lambda *args: sum(args) / len(args)

print(f"Multiply: {multiply(3, 4)}")
print(f"Average: {average(1, 2, 3, 4)}")

# With optional arguments
power = lambda x, n=2: x**n
print(f"Square: {power(3)}")
print(f"Cube: {power(3, 3)}")
```

```sh
Multiply: 12
Average: 2.5
Square: 9
Cube: 27
```

<br>

### Common Lambda Use Cases

> Typical scenarios where lambda functions are useful:

```python
# Sorting with custom key
points = [(1, 2), (3, 1), (0, 4)]
sorted_by_y = sorted(points, key=lambda p: p[1])
print(f"Sorted by y-coordinate: {sorted_by_y}")

# Filter with lambda
numbers = range(-5, 6)
positives = list(filter(lambda x: x > 0, numbers))
print(f"Positive numbers: {positives}")

# Map with lambda
numbers = [1, 2, 3, 4]
squares = list(map(lambda x: x**2, numbers))
print(f"Squares: {squares}")
```

```sh
Sorted by y-coordinate: [(3, 1), (1, 2), (0, 4)]
Positive numbers: [1, 2, 3, 4, 5]
Squares: [1, 4, 9, 16]
```

<br>

### Lambda in Higher-Order Functions

> Using lambda functions as arguments to other functions:

```python
def apply_operation(x, y, operation):
    """Apply given operation to x and y."""
    return operation(x, y)

# Different operations as lambda functions
add = lambda x, y: x + y
subtract = lambda x, y: x - y
maximum = lambda x, y: x if x > y else y

# Apply operations
print(f"Add: {apply_operation(5, 3, add)}")
print(f"Subtract: {apply_operation(5, 3, subtract)}")
print(f"Maximum: {apply_operation(5, 3, maximum)}")

# Inline lambda
print(f"Multiply: {apply_operation(5, 3, lambda x, y: x * y)}")
```

```sh
Add: 8
Subtract: 2
Maximum: 5
Multiply: 15
```

<br>

---

<br>

## Closures

> A closure is a nested function that has access to variables from its enclosing (containing) function's scope, even after the outer function has returned.

<br>

### Basic Closure

> Creating and using a simple closure:

```python
def make_multiplier(factor):
    # Inner function that uses factor
    def multiplier(x):
        return x * factor
    
    return multiplier

# Create specific multipliers
double = make_multiplier(2)
triple = make_multiplier(3)

# Use the multipliers
print(f"Double 5: {double(5)}")
print(f"Triple 5: {triple(5)}")

# Verify closure
print(f"Closure variables: {double.__closure__[0].cell_contents}")
```

```sh
Double 5: 10
Triple 5: 15
Closure variables: 2
```

<br>

### State Retention

> Using closures to maintain state:

```python
def make_counter():
    count = 0
    
    def counter():
        nonlocal count
        count += 1
        return count
    
    return counter

# Create counters
counter1 = make_counter()
counter2 = make_counter()

# Use counters
print(f"Counter 1: {counter1()}")
print(f"Counter 1: {counter1()}")
print(f"Counter 2: {counter2()}")
print(f"Counter 1: {counter1()}")
```

```sh
Counter 1: 1
Counter 1: 2
Counter 2: 1
Counter 1: 3
```

<br>

### Multiple Values in Closure

> Capturing multiple values in a closure:

```python
def make_range_checker(minimum, maximum):
    def check_range(value):
        return minimum <= value <= maximum
    
    def get_bounds():
        return (minimum, maximum)
    
    return check_range, get_bounds

# Create a range checker
check_valid_age, get_age_bounds = make_range_checker(0, 120)

# Use the functions
print(f"Is 25 valid age? {check_valid_age(25)}")
print(f"Is 150 valid age? {check_valid_age(150)}")
print(f"Age bounds: {get_age_bounds()}")
```

```sh
Is 25 valid age? True
Is 150 valid age? False
Age bounds: (0, 120)
```

<br>

### Function Factory Patterns

> Using closures to create specialized functions:

```python
def create_formatter(prefix='', suffix='', separator=': '):
    def format_text(key, value):
        return f"{prefix}{key}{separator}{value}{suffix}"
    
    return format_text

# Create different formatters
log_formatter = create_formatter(prefix='[LOG] ')
json_formatter = create_formatter(prefix='"', suffix='"', separator='": "')
html_formatter = create_formatter(prefix='<', suffix='>', separator='=')

# Use formatters
text = "Hello"
print(log_formatter("Message", text))
print(json_formatter("greeting", text))
print(html_formatter("msg", text))
```

```sh
[LOG] Message: Hello
"greeting": "Hello"
<msg=Hello>
```

<br>

### Closures with Arguments List

> Creating closures that handle variable arguments:

```python
def create_aggregator(func):
    values = []
    
    def aggregate(*args):
        nonlocal values
        values.extend(args)
        return func(values)
    
    return aggregate

# Create different aggregators
running_sum = create_aggregator(sum)
running_avg = create_aggregator(lambda x: sum(x) / len(x))

# Use aggregators
print(f"Sum after 1,2: {running_sum(1, 2)}")
print(f"Sum after 3,4: {running_sum(3, 4)}")
print(f"Avg after 1,2: {running_avg(1, 2)}")
print(f"Avg after 3,4: {running_avg(3, 4)}")
```

```sh
Sum after 1,2: 3
Sum after 3,4: 10
Avg after 1,2: 1.5
Avg after 3,4: 2.5
```

<br>

### Closure Gotchas

> Common pitfalls and their solutions:

```python
def wrong_closures():
    # Wrong: Late binding closure
    funcs = []
    for i in range(3):
        funcs.append(lambda: i)
    return funcs

def correct_closures():
    # Correct: Early binding closure
    funcs = []
    for i in range(3):
        funcs.append(lambda x=i: x)
    return funcs

# Compare behaviors
wrong = wrong_closures()
correct = correct_closures()

print("Wrong closures:")
for f in wrong:
    print(f())

print("\nCorrect closures:")
for f in correct:
    print(f())
```

```sh
Wrong closures:
2
2
2

Correct closures:
0
1
2
```

<br>

---

<br>

## Decorators

> Decorators are functions that modify the behavior of other functions or classes. They use the @ syntax and are a powerful way to modify or enhance functionality.

<br>

### Basic Decorator

> Creating and using a simple decorator:

```python
def log_calls(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__} with args: {args}, kwargs: {kwargs}")
        result = func(*args, **kwargs)
        print(f"{func.__name__} returned: {result}")
        return result
    return wrapper

# Using the decorator
@log_calls
def add_numbers(a, b):
    return a + b

# Test the decorated function
print("Calling add_numbers:")
result = add_numbers(3, 5)
print(f"Final result: {result}")
```

```sh
Calling add_numbers:
Calling add_numbers with args: (3, 5), kwargs: {}
add_numbers returned: 8
Final result: 8
```

<br>

### Preserving Function Metadata

> Using functools.wraps to maintain function information:

```python
from functools import wraps

def debug(func):
    @wraps(func)  # Preserve metadata
    def wrapper(*args, **kwargs):
        print(f"DEBUG: Entering {func.__name__}")
        result = func(*args, **kwargs)
        print(f"DEBUG: Exiting {func.__name__}")
        return result
    return wrapper

@debug
def greet(name):
    """Greet someone by name."""
    return f"Hello, {name}!"

# Test the function
print(greet("Alice"))
print(f"\nFunction name: {greet.__name__}")
print(f"Documentation: {greet.__doc__}")
```

```sh
DEBUG: Entering greet
Hello, Alice!
DEBUG: Exiting greet

Function name: greet
Documentation: Greet someone by name.
```

<br>

### Decorators with Arguments

> Creating decorators that accept arguments:

```python
def repeat(times):
    def decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            results = []
            for _ in range(times):
                results.append(func(*args, **kwargs))
            return results
        return wrapper
    return decorator

@repeat(times=3)
def generate_random():
    import random
    return random.randint(1, 10)

# Test the decorated function
results = generate_random()
print(f"Generated numbers: {results}")

# Another example with different repeat count
@repeat(times=2)
def greet(name):
    return f"Hello, {name}!"

print(f"\nGreetings: {greet('Bob')}")
```

```sh
Generated numbers: [7, 3, 9]

Greetings: ['Hello, Bob!', 'Hello, Bob!']
```

<br>

### Multiple Decorators

> Applying multiple decorators to a single function:

```python
def bold(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        return f"<b>{func(*args, **kwargs)}</b>"
    return wrapper

def italic(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        return f"<i>{func(*args, **kwargs)}</i>"
    return wrapper

@bold
@italic
def format_text(text):
    return text

# Test multiple decorators
print(format_text("Hello, World!"))

# Show order of execution
@italic
@bold
def format_text_reversed(text):
    return text

print(format_text_reversed("Hello, World!"))
```

```sh
<b><i>Hello, World!</i></b>
<i><b>Hello, World!</b></i>
```

<br>

### Class Decorators

> Creating decorators that work with classes:

```python
def singleton(cls):
    instances = {}
    
    @wraps(cls)
    def get_instance(*args, **kwargs):
        if cls not in instances:
            instances[cls] = cls(*args, **kwargs)
        return instances[cls]
    
    return get_instance

@singleton
class Configuration:
    def __init__(self):
        self.settings = {}
    
    def set(self, key, value):
        self.settings[key] = value

# Test singleton behavior
config1 = Configuration()
config1.set('debug', True)

config2 = Configuration()
print(f"Same instance: {config1 is config2}")
print(f"Settings: {config2.settings}")
```

```sh
Same instance: True
Settings: {'debug': True}
```

<br>

### Practical Decorator Examples

> Common use cases for decorators:

```python
import time
from functools import wraps

# Timing decorator
def measure_time(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.4f} seconds")
        return result
    return wrapper

# Cache decorator
def memoize(func):
    cache = {}
    
    @wraps(func)
    def wrapper(*args):
        if args not in cache:
            cache[args] = func(*args)
        return cache[args]
    return wrapper

# Use the decorators
@measure_time
@memoize
def fibonacci(n):
    if n < 2:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

# Test the decorated function
print(f"Fibonacci(10): {fibonacci(10)}")
print(f"Fibonacci(10) again: {fibonacci(10)}")  # Should be faster
```

```sh
Fibonacci(10): 55
fibonacci took 0.0002 seconds
Fibonacci(10) again: 55
fibonacci took 0.0001 seconds
```

<br>

---

<br>

## Function Annotations

> Function annotations provide a way to attach metadata to a function's parameters and return value. While they don't affect the function's execution, they can be used for documentation, type hints, or custom processing.

<br>

### Basic Annotations

> Adding simple annotations to functions:

```python
def process_data(x: int, y: str) -> bool:
    print(f"Processing x={x} ({type(x)})")
    print(f"Processing y={y} ({type(y)})")
    return True

# Inspect annotations
print(f"Function annotations: {process_data.__annotations__}")

# Call function
result = process_data(42, "hello")
print(f"Result: {result}")
```

```sh
Function annotations: {'x': <class 'int'>, 'y': <class 'str'>, 'return': <class 'bool'>}
Processing x=42 (<class 'int'>)
Processing y=hello (<class 'str'>)
Result: True
```

<br>

### Complex Annotations

> Using more complex annotation types:

```python
from typing import List, Dict, Optional

def analyze_data(
    values: List[int],
    options: Dict[str, str],
    threshold: Optional[float] = None
) -> Dict[str, any]:
    result = {
        'count': len(values),
        'options': options
    }
    if threshold is not None:
        result['threshold'] = threshold
    return result

# Use the function
data = [1, 2, 3]
opts = {'mode': 'test'}
result = analyze_data(data, opts, 1.5)
print(f"Result: {result}")

# Show annotations
print(f"\nAnnotations: {analyze_data.__annotations__}")
```

```sh
Result: {'count': 3, 'options': {'mode': 'test'}, 'threshold': 1.5}

Annotations: {'values': typing.List[int], 'options': typing.Dict[str, str], 'threshold': typing.Optional[float], 'return': typing.Dict[str, any]}
```

<br>

### Variable Annotations

> Annotating variables in and outside functions:

```python
from typing import List, Dict

class DataProcessor:
    data: List[int]
    config: Dict[str, str]
    
    def __init__(self):
        self.data = []
        self.config = {}
    
    def process(self, value: int) -> None:
        # Local variable annotation
        result: List[int] = []
        result.append(value)
        self.data.extend(result)

# Create and use processor
processor = DataProcessor()
processor.process(42)
print(f"Processed data: {processor.data}")

# Show class annotations
print(f"\nClass annotations: {DataProcessor.__annotations__}")
```

```sh
Processed data: [42]

Class annotations: {'data': typing.List[int], 'config': typing.Dict[str, str]}
```

<br>

### Using Annotations for Documentation

> Annotations can be used for documentation purposes:

```python
def calculate_area(
    length: "The length of the rectangle",
    width: "The width of the rectangle" = 1.0
) -> "Area of the rectangle":
    """Calculate the area of a rectangle."""
    return length * width

# Inspect annotations and docstring
print(f"Function annotations: {calculate_area.__annotations__}")
print(f"Function documentation: {calculate_area.__doc__}")

# Use the function
area = calculate_area(5.0, 3.0)
print(f"\nCalculated area: {area}")
```

```sh
Function annotations: {'length': 'The length of the rectangle', 'width': 'The width of the rectangle', 'return': 'Area of the rectangle'}
Function documentation: Calculate the area of a rectangle.

Calculated area: 15.0
```

<br>

### Accessing and Using Annotations

> Working with annotations programmatically:

```python
def validate_annotations(func):
    def wrapper(*args, **kwargs):
        # Check arguments against annotations
        annotations = func.__annotations__
        
        for arg_name, arg_value in zip(func.__code__.co_varnames, args):
            if arg_name in annotations:
                expected_type = annotations[arg_name]
                if not isinstance(arg_value, expected_type):
                    raise TypeError(
                        f"Argument {arg_name} should be {expected_type}"
                    )
        
        result = func(*args, **kwargs)
        
        # Check return value
        if 'return' in annotations:
            expected_type = annotations['return']
            if not isinstance(result, expected_type):
                raise TypeError(
                    f"Return value should be {expected_type}"
                )
        
        return result
    return wrapper

@validate_annotations
def process_number(value: int, factor: int = 1) -> int:
    return value * factor

# Test with valid inputs
print(f"Valid calculation: {process_number(5, 2)}")

# Test with invalid input
try:
    process_number("invalid", 2)
except TypeError as e:
    print(f"\nError: {e}")
```

```sh
Valid calculation: 10

Error: Argument value should be <class 'int'>
```

<br>

---

<br>

## Type Hints

> Type hints provide a standardized way to indicate the expected types of function arguments, return values, and variables. They enhance code readability and enable static type checking.

<br>

### Basic Type Hints

> Using basic type hints for variables and functions:

```python
from typing import List, Dict, Set, Tuple

# Basic type hints
name: str = "Alice"
age: int = 30
height: float = 1.75
active: bool = True

def process_user(
    name: str,
    age: int,
    scores: List[int]
) -> Dict[str, any]:
    return {
        "name": name,
        "age": age,
        "scores": scores
    }

# Using the function
result = process_user("Bob", 25, [85, 90, 95])
print(f"Processed user: {result}")
```

```sh
Processed user: {'name': 'Bob', 'age': 25, 'scores': [85, 90, 95]}
```

<br>

### Complex Types

> Using more complex type hints with generics:

```python
from typing import List, Dict, Tuple, Set, Union

def process_data(
    items: List[Union[int, float]],
    mapping: Dict[str, List[str]],
    coordinates: Tuple[int, int] = (0, 0)
) -> Set[float]:
    
    # Process the data
    result = set()
    for item in items:
        result.add(float(item))
    
    print(f"Mapping: {mapping}")
    print(f"Coordinates: {coordinates}")
    
    return result

# Test the function
numbers = [1, 2.5, 3, 4.5]
mapping = {"group1": ["a", "b"], "group2": ["c", "d"]}
result = process_data(numbers, mapping, (10, 20))
print(f"Result: {result}")
```

```sh
Mapping: {'group1': ['a', 'b'], 'group2': ['c', 'd']}
Coordinates: (10, 20)
Result: {1.0, 2.5, 3.0, 4.5}
```

<br>

### Optional and Union Types

> Working with optional and union types:

```python
from typing import Optional, Union

def process_value(
    value: Union[int, float],
    modifier: Optional[float] = None
) -> float:
    if modifier is None:
        return float(value)
    return float(value) * modifier

# Test different combinations
print(f"No modifier: {process_value(10)}")
print(f"With modifier: {process_value(10, 1.5)}")
print(f"Float input: {process_value(3.14, 2.0)}")

# Type aliases for complex types
Number = Union[int, float]
def calculate(x: Number, y: Number) -> Number:
    return x * y

print(f"\nCalculation: {calculate(3, 2.5)}")
```

```sh
No modifier: 10.0
With modifier: 15.0
Float input: 6.28

Calculation: 7.5
```

<br>

### Generic Types

> Using generic types for flexible type hints:

```python
from typing import TypeVar, Generic, List

T = TypeVar('T')

class Stack(Generic[T]):
    def __init__(self) -> None:
        self.items: List[T] = []
    
    def push(self, item: T) -> None:
        self.items.append(item)
    
    def pop(self) -> T:
        return self.items.pop()
    
    def peek(self) -> Optional[T]:
        return self.items[-1] if self.items else None

# Use with different types
int_stack: Stack[int] = Stack()
str_stack: Stack[str] = Stack()

int_stack.push(1)
int_stack.push(2)
str_stack.push("hello")

print(f"Integer stack peek: {int_stack.peek()}")
print(f"String stack peek: {str_stack.peek()}")
```

```sh
Integer stack peek: 2
String stack peek: hello
```

<br>

### Callable Types

> Type hints for callable objects and functions:

```python
from typing import Callable, List

def apply_operation(
    numbers: List[int],
    operation: Callable[[int], int]
) -> List[int]:
    return [operation(x) for x in numbers]

# Define operations
def square(x: int) -> int:
    return x * x

def double(x: int) -> int:
    return x * 2

# Test with different operations
numbers = [1, 2, 3, 4]
squares = apply_operation(numbers, square)
doubles = apply_operation(numbers, double)

print(f"Original: {numbers}")
print(f"Squares: {squares}")
print(f"Doubles: {doubles}")
```

```sh
Original: [1, 2, 3, 4]
Squares: [1, 4, 9, 16]
Doubles: [2, 4, 6, 8]
```

<br>

### Type Checking at Runtime

> Using type hints for runtime validation:

```python
from typing import Any, Type
from dataclasses import dataclass

@dataclass
class TypeChecker:
    def validate_type(self, value: Any, expected_type: Type) -> bool:
        return isinstance(value, expected_type)
    
    def ensure_type(self, value: Any, expected_type: Type) -> None:
        if not self.validate_type(value, expected_type):
            raise TypeError(
                f"Expected {expected_type.__name__}, "
                f"got {type(value).__name__}"
            )

# Use the type checker
checker = TypeChecker()

try:
    # Valid types
    checker.ensure_type("hello", str)
    checker.ensure_type(42, int)
    print("Valid types passed")
    
    # Invalid type
    checker.ensure_type("hello", int)
except TypeError as e:
    print(f"Type error: {e}")
```

```sh
Valid types passed
Type error: Expected int, got str
```

<br>

---

<br>

## Partial Functions

> Partial functions allow you to fix a certain number of arguments of a function and generate a new function. This is implemented through the `functools.partial` class.

<br>

### Basic Partial Functions

> Creating simple partial functions:

```python
from functools import partial

def power(base: float, exponent: float) -> float:
    return base ** exponent

# Create partial functions
square = partial(power, exponent=2)
cube = partial(power, exponent=3)

# Test the partial functions
number = 4
print(f"Number: {number}")
print(f"Square: {square(number)}")
print(f"Cube: {cube(number)}")
```

```sh
Number: 4
Square: 16
Cube: 64
```

<br>

### Multiple Arguments

> Working with multiple fixed arguments:

```python
def format_text(text: str, prefix: str = '', suffix: str = '', 
                wrapper: str = '') -> str:
    result = f"{prefix}{text}{suffix}"
    if wrapper:
        result = f"{wrapper}{result}{wrapper}"
    return result

# Create specialized formatters
html_bold = partial(format_text, prefix='<b>', suffix='</b>')
markdown_italic = partial(format_text, wrapper='_')
quote = partial(format_text, wrapper='"')

# Test formatters
text = "Hello, World"
print(f"Bold: {html_bold(text)}")
print(f"Italic: {markdown_italic(text)}")
print(f"Quote: {quote(text)}")
```

```sh
Bold: <b>Hello, World</b>
Italic: _Hello, World_
Quote: "Hello, World"
```

<br>

### Partial with Methods

> Using partial functions with class methods:

```python
class DataProcessor:
    def process_data(self, data: list, operation: str, 
                     factor: float = 1.0) -> list:
        if operation == 'multiply':
            return [x * factor for x in data]
        elif operation == 'add':
            return [x + factor for x in data]
        return data

# Create processor instance
processor = DataProcessor()

# Create specialized processors
double_values = partial(processor.process_data, 
                       operation='multiply', factor=2)
add_ten = partial(processor.process_data,
                 operation='add', factor=10)

# Test processors
numbers = [1, 2, 3, 4]
print(f"Original: {numbers}")
print(f"Doubled: {double_values(numbers)}")
print(f"Added 10: {add_ten(numbers)}")
```

```sh
Original: [1, 2, 3, 4]
Doubled: [2, 4, 6, 8]
Added 10: [11, 12, 13, 14]
```

<br>

### Partial with Keyword Arguments

> Managing keyword arguments in partial functions:

```python
def send_message(message: str, *, 
                prefix: str = '', 
                suffix: str = '',
                separator: str = ': ') -> str:
    parts = []
    if prefix:
        parts.append(f"{prefix}{separator}")
    parts.append(message)
    if suffix:
        parts.append(f"{suffix}")
    return ' '.join(parts)

# Create specialized senders
log_error = partial(send_message, prefix='ERROR', 
                   separator=' >> ')
log_info = partial(send_message, prefix='INFO',
                  suffix='[OK]')

# Test message senders
print(log_error("File not found"))
print(log_info("Operation completed"))
```

```sh
ERROR >> File not found
INFO: Operation completed [OK]
```

<br>

### Combining with Other Features

> Using partial functions with decorators and type hints:

```python
from typing import Callable, TypeVar, Any

T = TypeVar('T')

def log_calls(func: Callable[..., T]) -> Callable[..., T]:
    def wrapper(*args: Any, **kwargs: Any) -> T:
        print(f"Calling {func.__name__}")
        result = func(*args, **kwargs)
        print(f"Finished {func.__name__}")
        return result
    return wrapper

@log_calls
def calculate(x: float, y: float, operation: str = 'add') -> float:
    if operation == 'add':
        return x + y
    elif operation == 'multiply':
        return x * y
    return 0

# Create specialized calculators
add_numbers = partial(calculate, operation='add')
multiply_numbers = partial(calculate, operation='multiply')

# Test calculators
print(f"\nResult of add: {add_numbers(5, 3)}")
print(f"\nResult of multiply: {multiply_numbers(5, 3)}")
```

```sh
Result of add:
Calling calculate
Finished calculate
8.0

Result of multiply:
Calling calculate
Finished calculate
15.0
```

<br>

---

<br>

## Recursive Functions

> Recursive functions are functions that call themselves to solve problems by breaking them down into smaller, similar subproblems.

<br>

### Basic Recursion

> Simple recursive function example:

```python
def factorial(n):
    if n <= 1:  # Base case
        return 1
    return n * factorial(n - 1)  # Recursive case

# Test the function
print(factorial(5))  # 120
print(factorial(3))  # 6
```

```sh
120
6
```

<br>

### Recursive List Processing

> Using recursion to process lists:

```python
def sum_list(numbers):
    if not numbers:  # Base case: empty list
        return 0
    return numbers[0] + sum_list(numbers[1:])  # Recursive case

# Test the function
numbers = [1, 2, 3, 4]
print(sum_list(numbers))  # 10
```

```sh
10
```

<br>

### Tree Recursion

> Recursive function that branches into multiple recursive calls:

```python
def fibonacci(n):
    if n <= 1:  # Base cases
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)  # Recursive cases

# Test the function
for i in range(5):
    print(f"fibonacci({i}) = {fibonacci(i)}")
```

```sh
fibonacci(0) = 0
fibonacci(1) = 1
fibonacci(2) = 1
fibonacci(3) = 2
fibonacci(4) = 3
```

<br>

### Tail Recursion

> Recursive function that makes the recursive call the last operation:

```python
def count_down(n):
    if n <= 0:  # Base case
        print("Done!")
        return
    print(n)
    count_down(n - 1)  # Tail recursive call

# Test the function
count_down(3)
```

```sh
3
2
1
Done!
```

<br>

---

<br>

## Function Caching

> Function caching stores the results of expensive function calls and returns the cached result when the same inputs occur again.

<br>

### Basic Caching

> Using the `@lru_cache` decorator for simple caching:

```python
from functools import lru_cache

@lru_cache
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

# Test with caching
print(fibonacci(10))  # Calculates and caches
print(fibonacci(10))  # Uses cached result
```

```sh
55
55
```

<br>

### Cache Size Limit

> Setting maximum cache size:

```python
from functools import lru_cache

@lru_cache(maxsize=2)  # Only keep last 2 results
def get_square(n):
    print(f"Computing square of {n}")
    return n ** 2

# Test cache behavior
print(get_square(2))  # Computes
print(get_square(3))  # Computes
print(get_square(2))  # Uses cache
print(get_square(4))  # Computes, removes 3 from cache
```

```sh
Computing square of 2
4
Computing square of 3
9
4
Computing square of 4
16
```

<br>

### Cache Info

> Viewing cache statistics:

```python
@lru_cache
def multiply(x, y):
    return x * y

# Use function several times
multiply(2, 3)
multiply(2, 3)  # Cache hit
multiply(3, 4)  # Cache miss

# Show cache info
print(multiply.cache_info())
```

```sh
CacheInfo(hits=1, misses=2, maxsize=128, currsize=2)
```

<br>

### Clearing Cache

> Manually clearing the cached results:

```python
@lru_cache
def add(a, b):
    print(f"Computing {a} + {b}")
    return a + b

print(add(1, 2))     # Computes
print(add(1, 2))     # Uses cache
add.cache_clear()     # Clear cache
print(add(1, 2))     # Computes again
```

```sh
Computing 1 + 2
3
3
Computing 1 + 2
3
```
