---
tags:
- control-flow
---

<br>

# Python Loops

> Python provides several ways to perform iteration and looping, offering both simplicity for basic operations and flexibility for complex iteration patterns.

<br>

### Key Characteristics

> - Two main loop types: for and while
> - Loop control statements: break, continue
> - Unique else clause for loops
> - Iterator protocol support
> - Generator expressions
> - Comprehension syntax
> - Automatic memory management for iterables

<br>

---

<br>

## for Loops

> The for loop iterates over a sequence (list, tuple, string) or other iterable objects.

<br>

### Basic for Loop

> Iterating over a sequence:

```python
# Iterate over a list
fruits = ['apple', 'banana', 'cherry']

for fruit in fruits:
    print(f"Current fruit: {fruit}")
```

```sh
Current fruit: apple
Current fruit: banana
Current fruit: cherry
```

<br>

### Range-based Loops

> Using range() for numeric iteration:

```python
# Basic range
print("Basic range:")
for i in range(3):
    print(f"Count: {i}")

# Range with start and stop
print("\nRange with start and stop:")
for i in range(1, 4):
    print(f"Number: {i}")

# Range with step
print("\nRange with step:")
for i in range(0, 10, 2):
    print(f"Even number: {i}")
```

```sh
Basic range:
Count: 0
Count: 1
Count: 2

Range with start and stop:
Number: 1
Number: 2
Number: 3

Range with step:
Even number: 0
Even number: 2
Even number: 4
Even number: 6
Even number: 8
```

<br>

### Enumerate

> Getting both index and value during iteration:

```python
colors = ['red', 'green', 'blue']

# Basic enumeration
print("Basic enumeration:")
for index, color in enumerate(colors):
    print(f"Color {index}: {color}")

# Enumeration with start value
print("\nEnumeration starting at 1:")
for index, color in enumerate(colors, start=1):
    print(f"Color {index}: {color}")
```

```sh
Basic enumeration:
Color 0: red
Color 1: green
Color 2: blue

Enumeration starting at 1:
Color 1: red
Color 2: green
Color 3: blue
```

<br>

### Dictionary Iteration

> Different ways to iterate over dictionaries:

```python
person = {
    'name': 'Alice',
    'age': 30,
    'city': 'New York'
}

# Iterate over keys (default)
print("Keys:")
for key in person:
    print(key)

# Iterate over values
print("\nValues:")
for value in person.values():
    print(value)

# Iterate over key-value pairs
print("\nKey-value pairs:")
for key, value in person.items():
    print(f"{key}: {value}")
```

```sh
Keys:
name
age
city

Values:
Alice
30
New York

Key-value pairs:
name: Alice
age: 30
city: New York
```

<br>

### Nested Loops

> Using loops within loops:

```python
# Multiplication table
for i in range(1, 4):
    for j in range(1, 4):
        product = i * j
        print(f"{i} × {j} = {product}")
    print("-" * 10)  # Separator

# Matrix traversal
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

print("\nMatrix elements:")
for row in matrix:
    for element in row:
        print(element, end=' ')
    print()  # New line after each row
```

```sh
1 × 1 = 1
1 × 2 = 2
1 × 3 = 3
----------
2 × 1 = 2
2 × 2 = 4
2 × 3 = 6
----------
3 × 1 = 3
3 × 2 = 6
3 × 3 = 9
----------

Matrix elements:
1 2 3 
4 5 6 
7 8 9 
```

<br>

---

<br>

## while Loops

> The while loop repeats a block of code as long as a given condition is true.

<br>

### Basic while Loop

> Simple condition-based iteration:

```python
# Count down from 5
count = 5
while count > 0:
    print(f"Countdown: {count}")
    count -= 1
print("Blast off!")
```

```sh
Countdown: 5
Countdown: 4
Countdown: 3
Countdown: 2
Countdown: 1
Blast off!
```

<br>

### Input Validation

> Using while for input validation:

```python
def get_positive_number():
    while True:
        try:
            number = int(input("Enter a positive number: "))
            if number > 0:
                return number
            print("Please enter a positive number.")
        except ValueError:
            print("Please enter a valid number.")

# Simulated input for demonstration
inputs = ["invalid", "-5", "0", "10"]
for test_input in inputs:
    print(f"\nTesting input: {test_input}")
    if test_input.isdigit() and int(test_input) > 0:
        print(f"Valid input received: {test_input}")
        break
    print("Invalid input, try again.")
```

```sh
Testing input: invalid
Invalid input, try again.

Testing input: -5
Invalid input, try again.

Testing input: 0
Invalid input, try again.

Testing input: 10
Valid input received: 10
```

<br>

### Sentinel Values

> Using a sentinel value to control loop termination:

```python
def process_numbers():
    numbers = []
    print("Enter numbers (enter 0 to stop):")
    
    while True:
        # Simulate input with a list
        inputs = [5, 3, 8, 0]
        for num in inputs:
            print(f"Current input: {num}")
            if num == 0:
                return numbers
            numbers.append(num)

numbers = process_numbers()
print(f"Collected numbers: {numbers}")
print(f"Sum: {sum(numbers)}")
print(f"Average: {sum(numbers)/len(numbers):.2f}")
```

```sh
Enter numbers (enter 0 to stop):
Current input: 5
Current input: 3
Current input: 8
Current input: 0
Collected numbers: [5, 3, 8]
Sum: 16
Average: 5.33
```

<br>

### Flag-Controlled Loops

> Using a boolean flag to control loop execution:

```python
def find_number(numbers, target):
    found = False
    index = 0
    
    while not found and index < len(numbers):
        if numbers[index] == target:
            found = True
        else:
            index += 1
    
    return index if found else -1

# Test the function
numbers = [4, 2, 7, 1, 9, 3]
targets = [7, 5]

for target in targets:
    result = find_number(numbers, target)
    if result != -1:
        print(f"Found {target} at index {result}")
    else:
        print(f"{target} not found in list")
```

```sh
Found 7 at index 2
5 not found in list
```

<br>

### Dynamic Condition

> While loop with changing conditions:

```python
import random
random.seed(42)  # For reproducible results

def simulate_coin_flips():
    heads = 0
    flips = 0
    
    # Continue until we get 3 heads
    while heads < 3:
        flip = random.choice(['H', 'T'])
        flips += 1
        if flip == 'H':
            heads += 1
        print(f"Flip {flips}: {flip} (Total heads: {heads})")
    
    return flips

total_flips = simulate_coin_flips()
print(f"\nIt took {total_flips} flips to get 3 heads")
```

```sh
Flip 1: T (Total heads: 0)
Flip 2: H (Total heads: 1)
Flip 3: T (Total heads: 1)
Flip 4: H (Total heads: 2)
Flip 5: T (Total heads: 2)
Flip 6: H (Total heads: 3)

It took 6 flips to get 3 heads
```

<br>

### Error Recovery

> Using while for error recovery and retry logic:

```python
def simulate_operation(attempt):
    # Simulate success only on third attempt
    return attempt == 3

def perform_operation():
    max_attempts = 3
    attempt = 1
    
    while attempt <= max_attempts:
        print(f"\nAttempt {attempt} of {max_attempts}")
        
        if simulate_operation(attempt):
            print("Operation successful!")
            return True
        
        print("Operation failed, retrying...")
        attempt += 1
    
    print("Max attempts reached, operation failed.")
    return False

# Test the operation
success = perform_operation()
print(f"\nFinal result: {'Success' if success else 'Failure'}")
```

```sh
Attempt 1 of 3
Operation failed, retrying...

Attempt 2 of 3
Operation failed, retrying...

Attempt 3 of 3
Operation successful!

Final result: Success
```

<br>

---

<br>

## Loop Control

> Python provides break and continue statements to control loop execution flow.

<br>

### break Statement

> The break statement terminates the loop and continues execution after the loop:

```python
# Search in a list
numbers = [1, 3, 5, 7, 9, 11]
search_for = 7

print("Searching for number...")
for num in numbers:
    if num == search_for:
        print(f"Found {search_for}!")
        break
    print(f"Checking {num}")
print("Search complete")
```

```sh
Searching for number...
Checking 1
Checking 3
Checking 5
Found 7!
Search complete
```

<br>

### continue Statement

> The continue statement skips the rest of the current iteration and moves to the next one:

```python
# Process only even numbers
numbers = range(1, 6)
print("Processing even numbers:")
for num in numbers:
    if num % 2 != 0:
        continue
    print(f"Processing {num}")
    print(f"Square of {num} is {num**2}")
    print("---")
```

```sh
Processing even numbers:
Processing 2
Square of 2 is 4
---
Processing 4
Square of 4 is 16
---
```

<br>

### Nested Loop Control

> Using break and continue in nested loops:

```python
# Find factors of numbers
numbers = range(10, 13)

for n in numbers:
    print(f"\nFinding factors of {n}:")
    for potential_factor in range(2, n):
        # Skip if not divisible
        if n % potential_factor != 0:
            continue
            
        print(f"Found factor: {potential_factor}")
        
        # Stop if we find one factor
        break
    else:
        print(f"{n} is prime")
```

```sh
Finding factors of 10:
Found factor: 2

Finding factors of 11:
11 is prime

Finding factors of 12:
Found factor: 2
```

<br>

### Early Exit Pattern

> Using break to exit loops early when a condition is met:

```python
def find_invalid_data(data_list):
    for index, value in enumerate(data_list):
        print(f"Checking item {index}: {value}")
        
        # Check for invalid conditions
        if value < 0:
            print(f"Found invalid value {value} at position {index}")
            break
        
        if value > 100:
            print(f"Found invalid value {value} at position {index}")
            break
    else:
        print("All data is valid")

# Test with different lists
valid_data = [25, 65, 42, 83]
invalid_data = [25, 65, -42, 83]

print("Checking valid data:")
find_invalid_data(valid_data)

print("\nChecking invalid data:")
find_invalid_data(invalid_data)
```

```sh
Checking valid data:
Checking item 0: 25
Checking item 1: 65
Checking item 2: 42
Checking item 3: 83
All data is valid

Checking invalid data:
Checking item 0: 25
Checking item 1: 65
Checking item 2: -42
Found invalid value -42 at position 2
```

<br>

### Skip and Continue Pattern

> Using continue to skip specific iterations based on conditions:

```python
def process_transactions(transactions):
    total = 0
    skipped = 0
    
    for i, amount in enumerate(transactions, 1):
        print(f"\nProcessing transaction {i}: ${amount}")
        
        # Skip negative amounts
        if amount < 0:
            print("Skipping negative amount")
            skipped += 1
            continue
            
        # Skip zero amounts
        if amount == 0:
            print("Skipping zero amount")
            skipped += 1
            continue
            
        total += amount
        print(f"Running total: ${total}")
    
    return total, skipped

# Test with sample transactions
transactions = [100, -50, 75, 0, 125]
total, skipped = process_transactions(transactions)

print(f"\nFinal total: ${total}")
print(f"Skipped transactions: {skipped}")
```

```sh
Processing transaction 1: $100
Running total: $100

Processing transaction 2: $-50
Skipping negative amount

Processing transaction 3: $75
Running total: $175

Processing transaction 4: $0
Skipping zero amount

Processing transaction 5: $125
Running total: $300

Final total: $300
Skipped transactions: 2
```

<br>

---

<br>

## else Clause in Loops

> Python uniquely allows an else clause in loops. The else block executes when the loop completes normally (without encountering a break statement).

<br>

### Basic Loop else

> Demonstrating else clause execution:

```python
# Loop completes normally
print("Loop completing normally:")
for i in range(3):
    print(f"Value: {i}")
else:
    print("Loop completed!")

print("\nLoop with break:")
# Loop terminated by break
for i in range(3):
    if i == 1:
        print("Breaking loop")
        break
    print(f"Value: {i}")
else:
    print("This won't execute")
```

```sh
Loop completing normally:
Value: 0
Value: 1
Value: 2
Loop completed!

Loop with break:
Value: 0
Breaking loop
```

<br>

### Search Pattern

> Using loop else for search operations:

```python
def find_element(element, data):
    for index, value in enumerate(data):
        print(f"Checking index {index}")
        if value == element:
            print(f"Found {element} at index {index}")
            break
    else:
        print(f"{element} not found in data")
        return -1
    return index

# Test with different scenarios
numbers = [1, 3, 5, 7, 9]

print("\nSearching for 5:")
result = find_element(5, numbers)

print("\nSearching for 4:")
result = find_element(4, numbers)
```

```sh
Searching for 5:
Checking index 0
Checking index 1
Checking index 2
Found 5 at index 2

Searching for 4:
Checking index 0
Checking index 1
Checking index 2
Checking index 3
Checking index 4
4 not found in data
```

<br>

### Validation Pattern

> Using loop else for validation scenarios:

```python
def validate_numbers(numbers):
    print(f"Validating numbers: {numbers}")
    
    for num in numbers:
        if num < 0:
            print(f"Found invalid number: {num}")
            break
    else:
        print("All numbers are valid")
        return True
    
    print("Validation failed")
    return False

# Test with different lists
valid_list = [1, 2, 3, 4, 5]
invalid_list = [1, 2, -3, 4, 5]

print("\nTesting valid list:")
validate_numbers(valid_list)

print("\nTesting invalid list:")
validate_numbers(invalid_list)
```

```sh
Testing valid list:
Validating numbers: [1, 2, 3, 4, 5]
All numbers are valid

Testing invalid list:
Validating numbers: [1, 2, -3, 4, 5]
Found invalid number: -3
Validation failed
```

<br>

### Nested Loop else

> Using else clauses with nested loops:

```python
def find_divisor_pair(n):
    print(f"Finding divisor pair for {n}")
    
    for i in range(2, n):
        for j in range(i, n):
            if i * j == n:
                print(f"Found divisors: {i}, {j}")
                break
        else:
            continue
        break
    else:
        print(f"{n} is prime")

# Test with different numbers
numbers = [12, 13]

for num in numbers:
    print()  # Empty line for separation
    find_divisor_pair(num)
```

```sh
Finding divisor pair for 12
Found divisors: 2, 6

Finding divisor pair for 13
13 is prime
```

<br>

### Iteration Protocol

> Using else with iteration protocols:

```python
class CountDown:
    def __init__(self, start):
        self.start = start
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.start <= 0:
            raise StopIteration
        self.start -= 1
        return self.start + 1

def process_countdown(count):
    print(f"Starting countdown from {count}")
    
    for num in CountDown(count):
        if num == 2:
            print("Aborting countdown!")
            break
        print(num)
    else:
        print("Countdown completed!")

print("Normal countdown:")
process_countdown(3)

print("\nAborted countdown:")
process_countdown(5)
```

```sh
Normal countdown:
3
2
Aborting countdown!

Aborted countdown:
5
4
3
2
Aborting countdown!
```

<br>

---

<br>

## Iterators and Iteration

> Python's iterator protocol defines how objects can be iterated over. Any object that implements `__iter__()` and `__next__()` methods becomes iterable.

<br>

### Basic Iterator Protocol

> Implementing a simple iterator:

```python
class CountUp:
    def __init__(self, start, end):
        self.current = start
        self.end = end
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.current >= self.end:
            raise StopIteration
        self.current += 1
        return self.current - 1

# Using the iterator
counter = CountUp(1, 4)
for num in counter:
    print(f"Count: {num}")
```

```sh
Count: 1
Count: 2
Count: 3
```

<br>

### Custom Sequence Iterator

> Creating an iterator for a custom sequence:

```python
class FibonacciSequence:
    def __init__(self, limit):
        self.limit = limit
        self.previous = 0
        self.current = 1
        self.count = 0
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.count >= self.limit:
            raise StopIteration
            
        self.count += 1
        if self.count == 1:
            return self.previous
        if self.count == 2:
            return self.current
            
        next_val = self.previous + self.current
        self.previous = self.current
        self.current = next_val
        return next_val

# Using the Fibonacci iterator
print("First 7 Fibonacci numbers:")
for num in FibonacciSequence(7):
    print(num, end=' ')
```

```sh
First 7 Fibonacci numbers:
0 1 1 2 3 5 8 
```

<br>

### Iterator with State

> Creating an iterator that maintains state:

```python
class CyclicIterator:
    def __init__(self, items, max_cycles):
        self.items = items
        self.max_cycles = max_cycles
        self.cycle_count = 0
        self.index = 0
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.cycle_count >= self.max_cycles:
            raise StopIteration
            
        if self.index >= len(self.items):
            self.index = 0
            self.cycle_count += 1
            if self.cycle_count >= self.max_cycles:
                raise StopIteration
                
        item = self.items[self.index]
        self.index += 1
        return item

# Using the cyclic iterator
colors = ['red', 'green', 'blue']
print("Cycling through colors twice:")
for color in CyclicIterator(colors, 2):
    print(f"Color: {color}")
```

```sh
Cycling through colors twice:
Color: red
Color: green
Color: blue
Color: red
Color: green
Color: blue
```

<br>

### Iterable vs Iterator

> Demonstrating the difference between iterable and iterator:

```python
class NumberRange:
    def __init__(self, start, end):
        self.start = start
        self.end = end
    
    def __iter__(self):
        # Returns a new iterator each time
        return NumberRangeIterator(self.start, self.end)

class NumberRangeIterator:
    def __init__(self, start, end):
        self.current = start
        self.end = end
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.current >= self.end:
            raise StopIteration
        self.current += 1
        return self.current - 1

# Using the iterable
number_range = NumberRange(1, 4)

print("First iteration:")
for num in number_range:
    print(num)

print("\nSecond iteration:")
for num in number_range:
    print(num)
```

```sh
First iteration:
1
2
3

Second iteration:
1
2
3
```

<br>

### Manual Iterator Usage

> Using iterator methods directly:

```python
def demonstrate_iterator_methods():
    # Create an iterator
    numbers = [1, 2, 3]
    iterator = iter(numbers)
    
    print("Manual iteration:")
    try:
        while True:
            item = next(iterator)
            print(f"Got item: {item}")
    except StopIteration:
        print("Iterator exhausted")

    # Demonstrate default value with next()
    iterator = iter(numbers)
    print("\nUsing next() with default:")
    print(next(iterator, "default"))  # 1
    print(next(iterator, "default"))  # 2
    print(next(iterator, "default"))  # 3
    print(next(iterator, "default"))  # "default"

demonstrate_iterator_methods()
```

```sh
Manual iteration:
Got item: 1
Got item: 2
Got item: 3
Iterator exhausted

Using next() with default:
1
2
3
default
```

<br>

### Iterator Tools

> Using itertools for advanced iteration:

```python
from itertools import cycle, islice

def demonstrate_itertools():
    colors = ['red', 'green', 'blue']
    
    # Create an infinite cycle
    color_cycle = cycle(colors)
    
    # Take first 7 items from the infinite cycle
    print("First 7 colors from cycle:")
    for color in islice(color_cycle, 7):
        print(color)

demonstrate_itertools()
```

```sh
First 7 colors from cycle:
red
green
blue
red
green
blue
red
```

<br>

---

<br>

## Generator Expressions

> Generator expressions are similar to list comprehensions but create an iterator instead of a list, making them more memory efficient for large sequences.

<br>

### Basic Generator Expression

> Creating and using generator expressions:

```python
# List comprehension vs generator expression
numbers = range(5)

# List comprehension (creates list in memory)
squares_list = [x**2 for x in numbers]
print(f"List: {squares_list}")

# Generator expression (creates iterator)
squares_gen = (x**2 for x in numbers)
print(f"Generator object: {squares_gen}")
print("Generator values:")
for square in squares_gen:
    print(square, end=' ')
```

```sh
List: [0, 1, 4, 9, 16]
Generator object: <generator object <genexpr> at 0x...>
Generator values:
0 1 4 9 16 
```

<br>

### Memory Efficiency

> Demonstrating memory usage difference:

```python
import sys

def compare_memory():
    # Create large number sequence
    size = 1000000
    
    # List comprehension
    list_comp = [x for x in range(size)]
    list_size = sys.getsizeof(list_comp)
    
    # Generator expression
    gen_exp = (x for x in range(size))
    gen_size = sys.getsizeof(gen_exp)
    
    print(f"List size: {list_size:,} bytes")
    print(f"Generator size: {gen_size:,} bytes")
    print(f"Ratio: {list_size/gen_size:,.1f}x larger")

compare_memory()
```

```sh
List size: 8,448,728 bytes
Generator size: 192 bytes
Ratio: 44,003.8x larger
```

<br>

### Generator Chaining

> Combining multiple generator expressions:

```python
def process_numbers():
    # Generate numbers
    numbers = (x for x in range(10))
    
    # Square them
    squares = (x**2 for x in numbers)
    
    # Filter even squares
    even_squares = (x for x in squares if x % 2 == 0)
    
    print("Processing numbers lazily:")
    for num in even_squares:
        print(f"Got even square: {num}")

process_numbers()
```

```sh
Processing numbers lazily:
Got even square: 0
Got even square: 4
Got even square: 16
Got even square: 36
Got even square: 64
```

<br>

### Using in Functions

> Passing generator expressions to functions:

```python
def calculate_stats(numbers):
    # Convert to list only when needed
    nums = list(numbers)
    return min(nums), max(nums), sum(nums)/len(nums)

# Using generator expression as argument
numbers = (x for x in range(1, 6))
min_val, max_val, avg = calculate_stats(numbers)

print(f"Minimum: {min_val}")
print(f"Maximum: {max_val}")
print(f"Average: {avg}")

# Generator expression directly in function call
result = sum(x**2 for x in range(5))
print(f"\nSum of squares: {result}")
```

```sh
Minimum: 1
Maximum: 5
Average: 3.0

Sum of squares: 30
```

<br>

### Conditional Generation

> Using conditions in generator expressions:

```python
def filter_and_transform():
    # Generate word lengths for words starting with 'a'
    words = ['apple', 'banana', 'apricot', 'cherry', 'avocado']
    
    a_word_lengths = (len(word) for word in words if word.startswith('a'))
    
    print("Lengths of words starting with 'a':")
    for length in a_word_lengths:
        print(length, end=' ')
    
    # Generate word:length pairs
    word_lengths = ((word, len(word)) for word in words)
    
    print("\n\nWord length pairs:")
    for word, length in word_lengths:
        print(f"{word}: {length}")

filter_and_transform()
```

```sh
Lengths of words starting with 'a':
5 7 7 

Word length pairs:
apple: 5
banana: 6
apricot: 7
cherry: 6
avocado: 7
```

<br>

### Multiple Input Iterables

> Creating generators from multiple iterables:

```python
def combine_iterables():
    names = ['Alice', 'Bob', 'Charlie']
    ages = [25, 30, 35]
    cities = ['New York', 'London', 'Paris']
    
    # Create person data generator
    person_data = (
        f"{name} ({age}) from {city}"
        for name, age, city in zip(names, ages, cities)
    )
    
    print("Person information:")
    for person in person_data:
        print(person)
    
    # Generate pairs of adjacent items
    numbers = [1, 2, 3, 4]
    pairs = (
        (a, b)
        for a, b in zip(numbers, numbers[1:])
    )
    
    print("\nAdjacent pairs:")
    for pair in pairs:
        print(pair)

combine_iterables()
```

```sh
Person information:
Alice (25) from New York
Bob (30) from London
Charlie (35) from Paris

Adjacent pairs:
(1, 2)
(2, 3)
(3, 4)
```

<br>

### Best Practices

> Guidelines for using generator expressions effectively:

```python
def demonstrate_best_practices():
    # 1. Use generators for large sequences
    large_sum = sum(x for x in range(10**6))
    print(f"Sum of large sequence: {large_sum:,}")
    
    # 2. Chain generators instead of creating intermediate lists
    numbers = range(10)
    result = sum(x**2 for x in numbers if x % 2 == 0)
    print(f"\nSum of even squares: {result}")
    
    # 3. Use generator expressions in function arguments
    data = [1, 2, 3, 4, 5]
    average = sum(x for x in data) / len(data)
    print(f"\nAverage: {average}")
    
    # 4. Convert to list only when necessary
    top_three = list(x for x in range(10) if x % 3 == 0)[:3]
    print(f"\nTop three multiples of 3: {top_three}")

demonstrate_best_practices()
```

```sh
Sum of large sequence: 499,999,500,000

Sum of even squares: 120

Average: 3.0

Top three multiples of 3: [0, 3, 6]
```

<br>

---

<br>

## Comprehensions

> Comprehensions provide a concise way to create lists, dictionaries, and sets using a single expression. They combine creation and transformation into one step.

<br>

### List Comprehensions

> Creating lists with compact syntax:

```python
# Basic list comprehension
numbers = [1, 2, 3, 4, 5]
squares = [x**2 for x in numbers]
print(f"Squares: {squares}")

# With condition
even_squares = [x**2 for x in numbers if x % 2 == 0]
print(f"Even squares: {even_squares}")

# With transformation condition
number_type = ['even' if x % 2 == 0 else 'odd' for x in numbers]
print(f"Number types: {number_type}")
```

```sh
Squares: [1, 4, 9, 16, 25]
Even squares: [4, 16]
Number types: ['odd', 'even', 'odd', 'even', 'odd']
```

<br>

### Dictionary Comprehensions

> Creating dictionaries using comprehension syntax:

```python
# Basic dictionary comprehension
squares_dict = {x: x**2 for x in range(5)}
print(f"Number squares: {squares_dict}")

# Transforming existing dictionary
prices = {'apple': 0.40, 'orange': 0.35, 'banana': 0.25}
dollars = {k: f"${v:.2f}" for k, v in prices.items()}
print(f"Formatted prices: {dollars}")

# Filtering dictionary items
cheap_items = {k: v for k, v in prices.items() if v < 0.40}
print(f"Cheap items: {cheap_items}")
```

```sh
Number squares: {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
Formatted prices: {'apple': '$0.40', 'orange': '$0.35', 'banana': '$0.25'}
Cheap items: {'orange': 0.35, 'banana': 0.25}
```

<br>

### Set Comprehensions

> Creating sets using comprehension syntax:

```python
# Basic set comprehension
numbers = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
unique_squares = {x**2 for x in numbers}
print(f"Unique squares: {unique_squares}")

# Filtering with conditions
words = ['hello', 'world', 'python', 'programming']
long_words = {w.upper() for w in words if len(w) > 5}
print(f"Long words: {long_words}")

# Character sets
text = "hello world"
unique_chars = {c for c in text if c.isalpha()}
print(f"Unique letters: {unique_chars}")
```

```sh
Unique squares: {16, 1, 4, 9}
Long words: {'PYTHON', 'PROGRAMMING'}
Unique letters: {'e', 'h', 'l', 'o', 'r', 'w', 'd'}
```

<br>

### Nested Comprehensions

> Creating nested data structures:

```python
# Matrix creation
matrix = [[i + j for j in range(3)] for i in range(0, 9, 3)]
print("Matrix:")
for row in matrix:
    print(row)

# Flattening nested structures
nested = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened = [x for row in nested for x in row]
print(f"\nFlattened list: {flattened}")

# Complex transformations
matrix_ops = [[x*y for x in range(1, 4)] for y in range(1, 4)]
print("\nMultiplication table:")
for row in matrix_ops:
    print(row)
```

```sh
Matrix:
[0, 1, 2]
[3, 4, 5]
[6, 7, 8]

Flattened list: [1, 2, 3, 4, 5, 6, 7, 8, 9]

Multiplication table:
[1, 2, 3]
[2, 4, 6]
[3, 6, 9]
```

<br>

### Multiple Input Comprehensions

> Working with multiple input sequences:

```python
# Combining multiple lists
x_coords = [1, 2, 3]
y_coords = [4, 5, 6]

points = [(x, y) for x in x_coords for y in y_coords]
print(f"All possible points: {points}")

# Parallel iteration
names = ['Alice', 'Bob', 'Charlie']
ages = [25, 30, 35]
people = {name: age for name, age in zip(names, ages)}
print(f"\nPeople dictionary: {people}")

# Conditional pairing
nums1 = [1, 2, 3]
nums2 = [4, 5, 6]
pairs = [(a, b) for a in nums1 for b in nums2 if (a + b) % 2 == 0]
print(f"\nEven sum pairs: {pairs}")
```

```sh
All possible points: [(1, 4), (1, 5), (1, 6), (2, 4), (2, 5), (2, 6), (3, 4), (3, 5), (3, 6)]

People dictionary: {'Alice': 25, 'Bob': 30, 'Charlie': 35}

Even sum pairs: [(1, 5), (2, 4), (2, 6), (3, 5)]
```

<br>

### Performance and Best Practices

> Guidelines for using comprehensions effectively:

```python
import timeit

def compare_comprehensions():
    # List creation comparison
    list_comp_time = timeit.timeit(
        '[x**2 for x in range(1000)]',
        number=1000
    )
    
    loop_time = timeit.timeit(
        '''
        result = []
        for x in range(1000):
            result.append(x**2)
        ''',
        number=1000
    )
    
    print(f"List comprehension time: {list_comp_time:.4f} seconds")
    print(f"Loop time: {loop_time:.4f} seconds")
    
    # Examples of when not to use comprehensions
    # Bad: Complex logic
    bad_comp = ['long' if len(x) > 5 else 'short' if len(x) < 3 else 'medium'
                for x in ['a', 'abc', 'python']]
    
    # Better: Traditional loop
    result = []
    for x in ['a', 'abc', 'python']:
        if len(x) > 5:
            result.append('long')
        elif len(x) < 3:
            result.append('short')
        else:
            result.append('medium')
            
    print(f"\nResults are the same: {bad_comp == result}")

compare_comprehensions()
```

```sh
List comprehension time: 0.2345 seconds
Loop time: 0.3456 seconds

Results are the same: True
```
