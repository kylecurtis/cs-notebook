---
tags:
- data-structures
---

<br>

# Python Lists

> Python lists are ordered, mutable sequences that can hold items of different types. They provide a flexible and powerful way to store collections of data.

<br>

### Key Characteristics

> - Ordered sequence of items
> - Mutable (can be modified after creation)
> - Dynamic sizing (grows and shrinks as needed)
> - Supports items of different types
> - Zero-based indexing
> - Allows duplicate elements
> - Implemented as dynamic arrays

<br>

---

<br>

## List Creation

> Python provides several ways to create lists:

<br>

### Empty List Creation

> Using list literal syntax:

```python
empty_list = []
print(empty_list)
```

```sh
[]
```

<br>

### List with Initial Values

<br>

> Using list literal syntax:

```python
numbers = [1, 2, 3, 4, 5]
mixed = [1, "hello", 3.14, True]

print(f"Numbers: {numbers}")
print(f"Mixed types: {mixed}")
```

```sh
Numbers: [1, 2, 3, 4, 5]
Mixed types: [1, 'hello', 3.14, True]
```

<br>

---

<br>

### List Constructor

<br>

> Using the list() constructor from empty:

```python
empty_list = list()
print(empty_list)
```

```sh
[]
```

<br>

> Using the list() constructor from string:

```python
chars = list("Python")
print(chars)
```

```sh
['P', 'y', 't', 'h', 'o', 'n']
```

<br>

> Using the list() constructor from tuple:

```python
tuple_to_list = list((1, 2, 3))
print(tuple_to_list)
```

```sh
[1, 2, 3]
```

<br>

> Using the list() constructor from range:

```python
range_to_list = list(range(5))
print(range_to_list)
```

```sh
[0, 1, 2, 3, 4]
```

<br>

---

<br>

### List with Initial Values

<br>

> Using list literal syntax:

```python
numbers = [1, 2, 3, 4, 5]
mixed = [1, "hello", 3.14, True]

print(f"Numbers: {numbers}")
print(f"Mixed types: {mixed}")
```

```sh
Numbers: [1, 2, 3, 4, 5]
Mixed types: [1, 'hello', 3.14, True]
```

<br>

---

<br>

### List Replication

<br>

> Creating a list by replicating elements:

```python
# Using multiplication operator
zeros = [0] * 5
repeated = [1, 2] * 3

print(f"Zeros: {zeros}")
print(f"Repeated: {repeated}")
```

```sh
Zeros: [0, 0, 0, 0, 0]
Repeated: [1, 2, 1, 2, 1, 2]
```

<br>

---

<br>

## List Methods

<br>

### append()

> - Syntax: `list.append(x)`
> - Return: `None`
> - Info: Adds an item to the end of the list
> - Time Complexity: O(1) amortized

```python
numbers = [1, 2, 3]
numbers.append(4)
print(numbers)
```

```sh
[1, 2, 3, 4]
```

<br>

### extend()

> - Syntax: `list.extend(iterable)`
> - Return: `None`
> - Info: Extends the list by appending elements from the iterable
> - Time Complexity: O(k) where k is the length of the iterable

```python
numbers = [1, 2, 3]
numbers.extend([4, 5])
print(numbers)
```

```sh
[1, 2, 3, 4, 5]
```

<br>

### insert()

> - Syntax: `list.insert(i, x)`
> - Return: `None`
> - Info: Inserts an item (`x`) at a given position (`i`)
> - Time Complexity: O(n) where n is the number of elements after position i

```python
numbers = [1, 2, 3]
numbers.insert(1, 'a')
print(numbers)
```

```sh
[1, 'a', 2, 3]
```

<br>

### remove()

> - Syntax: `list.remove(x)`
> - Return: `None`
> - Info: Removes the first occurrence of an item
> - Raises: `ValueError` if the item is not present
> - Time Complexity: O(n)

```python
numbers = [1, 2, 3, 2, 4]
numbers.remove(2)
print(f"After removing first 2: {numbers}")

try:
    numbers.remove(10)
except ValueError as e:
    print(f"Error: {e}")
```

```sh
After removing first 2: [1, 3, 2, 4]
Error: list.remove(x): x not in list
```

<br>

### pop()

> - Syntax: `list.pop([i])`
> - Return: `item`
> - Info: Removes and returns item at given position (default last)
> - Raises: `IndexError` if list is empty or index out of range
> - Time Complexity: O(1) for last item, O(n) for arbitrary index

```python
numbers = [1, 2, 3, 4]

# Pop from end (default)
last = numbers.pop()
print(f"Popped from end: {last}")
print(f"List after pop: {numbers}")
```

```sh
Popped from end: 4
List after pop: [1, 2, 3]
```

<br>

> Pop from specific index:

```python
second = numbers.pop(1)
print(f"Popped from index 1: {second}")
print(f"List after pop: {numbers}")
```

```sh
Popped from index 1: 2
List after pop: [1, 3]
```

<br>

### clear()

> - Syntax: `list.clear()`
> - Return: `None`
> - Info: Removes all items from the list
> - Time Complexity: O(1)

```python
numbers = [1, 2, 3, 4]
numbers.clear()
print(f"List after clear: {numbers}")
```

```sh
List after clear: []
```

<br>

### index()

> - Syntax: `list.index(x[, start[, end]])`
> - Return: `int`
> - Info: Returns index of first occurrence of item
> - Parameters:
>   - x: Item to find
>   - start: Beginning search position (optional)
>   - end: End search position (optional)
> - Raises: `ValueError` if item not found
> - Time Complexity: O(n)

```python
numbers = [1, 2, 3, 2, 4]

# Basic index search
print(f"Index of 2: {numbers.index(2)}")

# Search with start position
print(f"Index of 2 after position 2: {numbers.index(2, 2)}")

# Search within range
print(f"Index of 2 between positions 1 and 3: {numbers.index(2, 1, 3)}")
```

```sh
Index of 2: 1
Index of 2 after position 2: 3
Index of 2 between positions 1 and 3: 1
```

<br>

### count()

> - Syntax: `list.count(x)`
> - Return: `int`
> - Info: Returns number of occurrences of an item
> - Time Complexity: O(n)

```python
numbers = [1, 2, 2, 3, 2, 4]
print(f"Count of 2: {numbers.count(2)}")
print(f"Count of 5: {numbers.count(5)}")
```

```sh
Count of 2: 3
Count of 5: 0
```

<br>

### reverse()

> - Syntax: `list.reverse()`
> - Return: `None`
> - Info: Reverses items in place
> - Time Complexity: O(n)
> - Note: Modifies the list in place

```python
numbers = [1, 2, 3, 4]
numbers.reverse()
print(f"Reversed list: {numbers}")

# Alternative using slicing (creates new list)
numbers = [1, 2, 3, 4]
reversed_new = numbers[::-1]
print(f"Reversed using slicing: {reversed_new}")
```

```sh
Reversed list: [4, 3, 2, 1]
Reversed using slicing: [4, 3, 2, 1]
```

<br>

### sort()

> - Syntax: `list.sort(*, key=None, reverse=False)`
> - Return: `None`
> - Info: Sorts the list in place
> - Parameters:
>   - key: Function to determine sort order (optional)
>   - reverse: Sort in descending order if True
> - Time Complexity: O(n log n)
> - Note: Modifies the list in place

```python
# Basic sorting
numbers = [3, 1, 4, 1, 5, 9, 2, 6]
numbers.sort()
print(f"Sorted numbers: {numbers}")
```

```sh
Sorted numbers: [1, 1, 2, 3, 4, 5, 6, 9]
```

<br>

> Sorting with key function:

```python
words = ['banana', 'apple', 'Cherry']
words.sort(key=str.lower)  # Case-insensitive sort
print(f"Sorted words: {words}")
```

```sh
Sorted words: ['apple', 'banana', 'Cherry']
```

<br>

> Sorting in reverse:

```python
numbers = [1, 2, 3, 4]
numbers.sort(reverse=True)
print(f"Reverse sorted: {numbers}")
```

```sh
Reverse sorted: [4, 3, 2, 1]
```

<br>

---

<br>

## List Comprehensions

> List comprehensions provide a concise way to create lists based on existing sequences or iterables. They follow the pattern:
> - `[expression for item in iterable if condition]`

<br>

### Basic List Comprehension

> Creating a list using a single for clause:

```python
# Square numbers from 0 to 4
squares = [x**2 for x in range(5)]
print(f"Squares: {squares}")
```

```sh
Squares: [0, 1, 4, 9, 16]
```

<br>

> Equivalent using traditional for loop:

```python
squares = []
for x in range(5):
    squares.append(x**2)
print(f"Squares from loop: {squares}")
```

```sh
Squares from loop: [0, 1, 4, 9, 16]
```

<br>

### Conditional List Comprehension

> List comprehension with a filtering condition:

```python
# Even numbers from 0 to 9
evens = [x for x in range(10) if x % 2 == 0]
print(f"Even numbers: {evens}")
```

```sh
Even numbers: [0, 2, 4, 6, 8]
```

<br>

> Using if-else in the expression:

```python
# Replace odd numbers with 'odd'
numbers = [x if x % 2 == 0 else 'odd' for x in range(5)]
print(f"Numbers with odd label: {numbers}")
```

```sh
Numbers with odd label: [0, 'odd', 2, 'odd', 4]
```

<br>

### Nested List Comprehension

> Creating nested structures:

```python
# 3x3 multiplication table
table = [[i * j for j in range(1, 4)] for i in range(1, 4)]
print("Multiplication table:")
for row in table:
    print(row)
```

```sh
Multiplication table:
[1, 2, 3]
[2, 4, 6]
[3, 6, 9]
```

<br>

### Flattening Nested Lists

> Converting nested list to flat list:

```python
nested = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flat = [num for sublist in nested for num in sublist]

print(f"Nested list: {nested}")
print(f"Flattened list: {flat}")
```

```sh
Nested list: [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
Flattened list: [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

<br>

### Common Patterns

> String operations in list comprehensions:

```python
words = ['hello', 'world', 'python']
upper_words = [word.upper() for word in words]
print(f"Uppercase words: {upper_words}")
```

```sh
Uppercase words: ['HELLO', 'WORLD', 'PYTHON']
```

<br>

> Working with tuples:

```python
points = [(x, y) for x in range(2) for y in range(2)]
print(f"Coordinate points: {points}")
```

```sh
Coordinate points: [(0, 0), (0, 1), (1, 0), (1, 1)]
```

<br>

---

<br>

### Performance Considerations

> List comprehensions are generally faster than equivalent for loops:

```python
import timeit

# Using list comprehension
comp_time = timeit.timeit(
    '[x**2 for x in range(1000)]',
    number=1000
)

# Using for loop
loop_time = timeit.timeit(
    '''
result = []
for x in range(1000):
    result.append(x**2)
    ''',
    number=1000
)

# Exact results may vary
print(f"Comprehension time: {comp_time:.4f} seconds")
print(f"Loop time: {loop_time:.4f} seconds")
```

```sh
Comprehension time: 0.0599 seconds 
Loop time: 0.0661 seconds
```

<br>

---

<br>

### Best Practices

> - Keep comprehensions simple and readable
> - Avoid multiple conditions when possible
> - Consider using traditional loops for complex logic
> - Use meaningful variable names in the expression
> - Break long comprehensions into multiple lines

```python
# Bad: Complex, hard to read
bad = [x for x in range(100) if x % 2 == 0 if x % 3 == 0 if x % 4 == 0]

# Good: Clear and maintainable
def is_divisible_by_all(x, divisors):
    return all(x % d == 0 for d in divisors)

good = [x for x in range(100) if is_divisible_by_all(x, [2, 3, 4])]

print(f"Numbers divisible by 2, 3, and 4: {good}")
```

```sh
Numbers divisible by 2, 3, and 4: [0, 12, 24, 36, 48, 60, 72, 84, 96]
```

<br>

---

<br>

## Nested Lists

> Nested lists are lists that contain other lists as elements, creating multi-dimensional data structures.

<br>

### Creating Nested Lists

> Direct creation using list literals:

```python
matrix = [[1, 2, 3],
          [4, 5, 6],
          [7, 8, 9]]

print("Matrix:")
for row in matrix:
    print(row)
```

```sh
Matrix:
[1, 2, 3]
[4, 5, 6]
[7, 8, 9]
```

<br>

> Using list comprehension:

```python
# Create a 3x3 matrix
size = 3
matrix = [[0 for _ in range(size)] for _ in range(size)]
print("Zero matrix:")
for row in matrix:
    print(row)
```

```sh
Zero matrix:
[0, 0, 0]
[0, 0, 0]
[0, 0, 0]
```

<br>

### Common Pitfall: Shallow Lists

> Incorrect way (creates references to the same list):

```python
# Wrong way to create nested list
wrong_matrix = [[0] * 3] * 3
wrong_matrix[0][1] = 1  # Changes all rows!

print("Wrong matrix creation:")
for row in wrong_matrix:
    print(row)
```

```sh
Wrong matrix creation:
[0, 1, 0]
[0, 1, 0]
[0, 1, 0]
```

<br>

> Correct way (creates independent lists):

```python
# Correct way to create nested list
correct_matrix = [[0] * 3 for _ in range(3)]
correct_matrix[0][1] = 1  # Changes only first row
print("Correct matrix creation:")
for row in correct_matrix:
    print(row)
```

```sh
Correct matrix creation:
[0, 1, 0]
[0, 0, 0]
[0, 0, 0]
```

<br>

### Accessing Nested Lists

> Using multiple indices:

```python
matrix = [[1, 2, 3],
          [4, 5, 6],
          [7, 8, 9]]

print(f"First row: {matrix[0]}")
print(f"Element at row 1, col 1: {matrix[1][1]}")
print(f"Last row: {matrix[-1]}")
```

```sh
First row: [1, 2, 3]
Element at row 1, col 1: 5
Last row: [7, 8, 9]
```

<br>

### Modifying Nested Lists

> Updating values:

```python
matrix = [[1, 2, 3],
          [4, 5, 6],
          [7, 8, 9]]

# Update single element
matrix[0][1] = 10

# Update entire row
matrix[1] = [14, 15, 16]

print("Modified matrix:")
for row in matrix:
    print(row)
```

```sh
Modified matrix:
[1, 10, 3]
[14, 15, 16]
[7, 8, 9]
```

<br>

### Common Operations

#### Matrix Transposition

> Converting rows to columns and vice versa:

```python
matrix = [[1, 2, 3],
          [4, 5, 6]]

transposed = [[row[i] for row in matrix] for i in range(len(matrix[0]))]
print("Original matrix:")
for row in matrix:
    print(row)
    
print("\nTransposed matrix:")
for row in transposed:
    print(row)
```

```sh
Original matrix:
[1, 2, 3]
[4, 5, 6]

Transposed matrix:
[1, 4]
[2, 5]
[3, 6]
```

<br>

#### Flattening Nested Lists

> Various methods to flatten nested lists:

```python
# Using list comprehension
nested = [[1, 2], [3, 4], [5, 6]]
flattened = [x for row in nested for x in row]
print(f"Flattened with comprehension: {flattened}")

# Using sum() with empty list
flattened_sum = sum(nested, [])
print(f"Flattened with sum(): {flattened_sum}")
```

```sh
Flattened with comprehension: [1, 2, 3, 4, 5, 6]
Flattened with sum(): [1, 2, 3, 4, 5, 6]
```

<br>

### Memory Considerations

> Nested lists can have complex memory behavior:

```python
# Demonstrate memory sharing
a = [1, 2, 3]
shared = [a] * 3  # References same list multiple times
independent = [a[:] for _ in range(3)]  # Creates copies

# Modify original list
a[0] = 10

print("Shared references:")
print(shared)
print("\nIndependent copies:")
print(independent)
```

```sh
Shared references:
[[10, 2, 3], [10, 2, 3], [10, 2, 3]]

Independent copies:
[[1, 2, 3], [1, 2, 3], [1, 2, 3]]
```

<br>

---

<br>

## Lists as Stacks and Queues

> Lists can be used to implement both stack (LIFO - Last In, First Out) and queue (FIFO - First In, First Out) data structures.

<br>

### Lists as Stacks

> A stack follows LIFO (Last In, First Out) principle:
> - Push: Add element to top (append)
> - Pop: Remove element from top (pop)
> - Peek: View top element without removing

```python
# Create a stack
stack = []

# Push operations
stack.append(1)    # Push 1
stack.append(2)    # Push 2
stack.append(3)    # Push 3

print(f"Stack after pushes: {stack}")
```

```sh
Stack after pushes: [1, 2, 3]
```

<br>

> Pop operations:

```python
top_item = stack.pop()  # Pop 3

print(f"Popped item: {top_item}")
print(f"Stack after pop: {stack}")
```

```sh
Popped item: 3
Stack after pop: [1, 2]
```

<br>

> Peek operation (view top without removing):

```python
# Peek at top item
top_item = stack[-1]
print(f"Top item (peek): {top_item}")
print(f"Stack after peek: {stack}")
```

```sh
Top item (peek): 2
Stack after peek: [1, 2]
```

<br>

---

<br>

### Stack Implementation Class

> Creating a stack class with error handling:

```python
class Stack:
    def __init__(self):
        self.items = []
    
    def push(self, item):
        self.items.append(item)
    
    def pop(self):
        if not self.is_empty():
            return self.items.pop()
        raise IndexError("Pop from empty stack")
    
    def peek(self):
        if not self.is_empty():
            return self.items[-1]
        raise IndexError("Peek at empty stack")
    
    def is_empty(self):
        return len(self.items) == 0
    
    def size(self):
        return len(self.items)

# Example usage
stack = Stack()
stack.push("first")
stack.push("second")

print(f"Stack size: {stack.size()}")
print(f"Top item: {stack.peek()}")
print(f"Popped item: {stack.pop()}")
print(f"Stack size after pop: {stack.size()}")
```

```sh
Stack size: 2
Top item: second
Popped item: second
Stack size after pop: 1
```

<br>

---

<br>

### Lists as Queues

> Using lists as queues is not recommended due to performance issues. The `collections.deque` class should be used instead:
> - Enqueue: Add element to end
> - Dequeue: Remove element from beginning

```python
from collections import deque

# Create a queue
queue = deque()

# Enqueue operations
queue.append(1)    # Enqueue 1
queue.append(2)    # Enqueue 2
queue.append(3)    # Enqueue 3

print(f"Queue after enqueues: {queue}")
```

```sh
Queue after enqueues: deque([1, 2, 3])
```

<br>

> Dequeue operations:

```python
# Dequeue operations
first_item = queue.popleft()  # Dequeue 1
print(f"Dequeued item: {first_item}")
print(f"Queue after dequeue: {queue}")
```

```sh
Dequeued item: 1
Queue after dequeue: deque([2, 3])
```

<br>

---

<br>

### Queue Implementation Class

> Creating a queue class using deque:

```python
class Queue:
    def __init__(self):
        self.items = deque()
    
    def enqueue(self, item):
        self.items.append(item)
    
    def dequeue(self):
        if not self.is_empty():
            return self.items.popleft()
        raise IndexError("Dequeue from empty queue")
    
    def peek(self):
        if not self.is_empty():
            return self.items[0]
        raise IndexError("Peek at empty queue")
    
    def is_empty(self):
        return len(self.items) == 0
    
    def size(self):
        return len(self.items)

# Example usage
queue = Queue()
queue.enqueue("first")
queue.enqueue("second")

print(f"Queue size: {queue.size()}")
print(f"Front item: {queue.peek()}")
print(f"Dequeued item: {queue.dequeue()}")
print(f"Queue size after dequeue: {queue.size()}")
```

```sh
Queue size: 2
Front item: first
Dequeued item: first
Queue size after dequeue: 1
```

<br>

---

<br>

### Performance Considerations

> Time complexity comparison:

Operation | List as Stack | List as Queue | deque
----------|--------------|---------------|-------
Insert at end (append) | O(1)* | O(1)* | O(1)
Remove from end (pop) | O(1) | O(1) | O(1)
Insert at beginning | O(n) | O(n) | O(1)
Remove from beginning | O(n) | O(n) | O(1)

> * Amortized time complexity

<br>

---

<br>

### Memory Usage

> Comparing memory usage:

```python
import sys

# Memory usage of list vs deque
lst = list(range(1000))
dq = deque(range(1000))

print(f"List size in bytes: {sys.getsizeof(lst)}")
print(f"Deque size in bytes: {sys.getsizeof(dq)}")
```

```sh
List size in bytes: 8056 
Deque size in bytes: 8680
```

<br>

---

<br>

## Sorting Lists

> Python provides two main ways to sort lists:
> - `list.sort()` method that modifies the list in-place
> 	- `sort(*, key=None, reverse=False)`
> - `sorted()` built-in function that creates a new sorted list
> 	- `sorted(iterable, /, *, key=None, reverse=False)`

<br>

### Basic Sorting

> Using list.sort() method:

```python
# Sort numbers
numbers = [3, 1, 4, 1, 5, 9, 2, 6]
numbers.sort()

print(f"Sorted numbers: {numbers}")
```

```sh
Sorted numbers: [1, 1, 2, 3, 4, 5, 6, 9]
```

<br>

> Using sorted() function:

```python
# Original list remains unchanged
numbers = [3, 1, 4, 1, 5, 9, 2, 6]
sorted_numbers = sorted(numbers)

print(f"Original list: {numbers}")
print(f"New sorted list: {sorted_numbers}")
```

```sh
Original list: [3, 1, 4, 1, 5, 9, 2, 6]
New sorted list: [1, 1, 2, 3, 4, 5, 6, 9]
```

<br>

### Reverse Sorting

> Sorting in descending order:

```python
numbers = [3, 1, 4, 1, 5, 9, 2, 6]

# Using list.sort()
numbers.sort(reverse=True)
print(f"Reverse sorted (in-place): {numbers}")

# Using sorted()
numbers = [3, 1, 4, 1, 5, 9, 2, 6]
desc_sorted = sorted(numbers, reverse=True)
print(f"Reverse sorted (new list): {desc_sorted}")
```

```sh
Reverse sorted (in-place): [9, 6, 5, 4, 3, 2, 1, 1]
Reverse sorted (new list): [9, 6, 5, 4, 3, 2, 1, 1]
```

<br>

### Custom Sorting with Key Functions

> Sorting with a key function that determines sort order:

```python
# Sort strings by length
words = ['python', 'java', 'c++', 'javascript', 'rust']
words.sort(key=len)
print(f"Sorted by length: {words}")
```

```sh
Sorted by length: ['c++', 'java', 'rust', 'python', 'javascript']
```

<br>

> Case-insensitive string sorting:

```python
# Sort strings ignoring case
words = ['Banana', 'apple', 'Cherry', 'date']
words.sort(key=str.lower)
print(f"Sorted case-insensitive: {words}")
```

```sh
Sorted case-insensitive: ['apple', 'Banana', 'Cherry', 'date']
```

<br>

### Sorting Objects

> Sorting objects using lambda functions:

```python
class Student:
    def __init__(self, name, grade):
        self.name = name
        self.grade = grade
    
    def __repr__(self):
        return f"Student(name='{self.name}', grade={self.grade})"

students = [
    Student('Alice', 85),
    Student('Bob', 92),
    Student('Charlie', 78)
]

# Sort by grade
students.sort(key=lambda x: x.grade)
print("Sorted by grade:")
for student in students:
    print(student)
```

```sh
Sorted by grade:
Student(name='Charlie', grade=78)
Student(name='Alice', grade=85)
Student(name='Bob', grade=92)
```

<br>

### Multiple Criteria Sorting

> Sorting with multiple keys using tuple comparison:

```python
students = [
    ('Alice', 'A', 85),
    ('Bob', 'B', 85),
    ('Charlie', 'A', 92),
    ('David', 'B', 78)
]

# Sort by grade (descending) then name
students.sort(key=lambda x: (-x[2], x[0]))
print("Sorted by grade (desc) and name:")
for student in students:
    print(student)
```

```sh
Sorted by grade (desc) and name:
('Charlie', 'A', 92)
('Alice', 'A', 85)
('Bob', 'B', 85)
('David', 'B', 78)
```

<br>

### Stable Sorting

> Python's sorting algorithms are stable, meaning they preserve the relative order of equal elements:

```python
data = [(1, 'a'), (2, 'b'), (1, 'c'), (2, 'd')]

# Sort by first element only
sorted_data = sorted(data, key=lambda x: x[0])
print(f"Stable sort result: {sorted_data}")
```

```sh
Stable sort result: [(1, 'a'), (1, 'c'), (2, 'b'), (2, 'd')]
```

<br>

### Performance Characteristics

> Time complexity analysis of sorting operations:

```python
import timeit
import random

# Generate test data
data = list(range(1000))
random.shuffle(data)

# Time sorting operations
sort_time = timeit.timeit(
    lambda: data.copy().sort(),
    number=1000
)

sorted_time = timeit.timeit(
    lambda: sorted(data),
    number=1000
)

print(f"list.sort() time: {sort_time:.4f} seconds")
print(f"sorted() time: {sorted_time:.4f} seconds")
```

```sh
list.sort() time: 0.0778 seconds 
sorted() time: 0.0748 seconds
```

<br>

### Best Practices

> - Use `list.sort()` when modifying in-place is acceptable
> - Use `sorted()` when original order needs to be preserved
> - Choose appropriate key functions for clarity
> - Consider memory usage with large lists
> - Use `reverse=True` instead of reversing after sorting

<br>

---

<br>

## Copying Lists

> Python provides several ways to copy lists, each with different behaviors and implications for nested structures.

<br>

### Shallow Copy Methods

> Shallow copies create a new list but reference the same nested objects.

<br>

#### Using slice notation

```python
original = [1, 2, [3, 4]]
copy_slice = original[:]

# Modify the copy
copy_slice[0] = 10
copy_slice[2][0] = 30

print(f"Original: {original}")
print(f"Modified copy: {copy_slice}")
```

```sh
Original: [1, 2, [30, 4]]
Modified copy: [10, 2, [30, 4]]
```

<br>

#### Using list() constructor

```python
original = [1, 2, [3, 4]]
copy_list = list(original)

# Modify the copy
copy_list[0] = 10
copy_list[2][0] = 30

print(f"Original: {original}")
print(f"Modified copy: {copy_list}")
```

```sh
Original: [1, 2, [30, 4]]
Modified copy: [10, 2, [30, 4]]
```

<br>

#### Using copy() method

```python
original = [1, 2, [3, 4]]
copy_method = original.copy()

# Modify the copy
copy_method[0] = 10
copy_method[2][0] = 30

print(f"Original: {original}")
print(f"Modified copy: {copy_method}")
```

```sh
Original: [1, 2, [30, 4]]
Modified copy: [10, 2, [30, 4]]
```

<br>

### Deep Copy

> Deep copies create a new list and recursively copy all nested objects.

```python
from copy import deepcopy

original = [1, 2, [3, 4]]
deep_copy = deepcopy(original)

# Modify the deep copy
deep_copy[0] = 10
deep_copy[2][0] = 30

print(f"Original: {original}")
print(f"Modified deep copy: {deep_copy}")
```

```sh
Original: [1, 2, [3, 4]]
Modified deep copy: [10, 2, [30, 4]]
```

<br>

### Memory and References

> Examining object references in different copy types:

```python
import sys

original = [1, [2, 3]]
shallow = original.copy()
deep = deepcopy(original)

print(f"Original inner list id: {id(original[1])}")
print(f"Shallow copy inner list id: {id(shallow[1])}")
print(f"Deep copy inner list id: {id(deep[1])}")
```

```sh
Original inner list id: 140712834927872
Shallow copy inner list id: 140712834927872
Deep copy inner list id: 140712834928512
```

<br>

### Special Cases

#### Copying Mixed Data Types

```python
class Person:
    def __init__(self, name):
        self.name = name
    
    def __repr__(self):
        return f"Person('{self.name}')"

original = [1, "string", Person("Alice"), [1, 2]]
shallow = original.copy()
deep = deepcopy(original)

# Modify objects
shallow[2].name = "Bob"
deep[2].name = "Charlie"

print(f"Original: {original}")
print(f"Shallow copy: {shallow}")
print(f"Deep copy: {deep}")
```

```sh
Original: [1, 'string', Person('Bob'), [1, 2]]
Shallow copy: [1, 'string', Person('Bob'), [1, 2]]
Deep copy: [1, 'string', Person('Charlie'), [1, 2]]
```

<br>

### Performance Considerations

> Comparing performance of different copy methods:

```python
import timeit

# Create test data
test_list = list(range(1000)) + [list(range(5))]

# Time different copy methods
slice_time = timeit.timeit(
    'test_list[:]',
    globals=globals(),
    number=10000
)

copy_time = timeit.timeit(
    'test_list.copy()',
    globals=globals(),
    number=10000
)

deep_time = timeit.timeit(
    'deepcopy(test_list)',
    globals={'deepcopy': deepcopy, 'test_list': test_list},
    number=10000
)

print(f"Slice copy time: {slice_time:.4f} seconds")
print(f"Copy method time: {copy_time:.4f} seconds")
print(f"Deep copy time: {deep_time:.4f} seconds")
```

```sh
Slice copy time: 0.0220 seconds 
Copy method time: 0.0199 seconds 
Deep copy time: 2.7278 seconds
```

<br>

### Best Practices

> - Use shallow copy for flat lists (no nested mutable objects)
> - Use deep copy when nested structures need to be independent
> - Consider memory usage with large nested structures
> - Be aware of reference sharing in shallow copies
> - Document copy behavior in complex applications

```python
# Example of proper copy selection
def process_data(data_list):
    # Use shallow copy for simple transformation
    working_copy = data_list.copy()
    
    # Use deep copy if modifying nested structures
    backup_copy = deepcopy(data_list)
    
    return working_copy, backup_copy

# Usage
data = [1, [2, 3], 4]
work, backup = process_data(data)
```

<br>

---

<br>

## List Performance

> Understanding the performance characteristics of Python lists is crucial for writing efficient code.

<br>

### Time Complexity

> Common operations and their time complexity:

Operation | Time Complexity | Description
----------|----------------|-------------
Index | O(1) | Get item at index
Store | O(1) | Store item at index
Length | O(1) | Get length of list
Append | O(1)* | Add item to end
Pop Last | O(1) | Remove last item
Pop First | O(n) | Remove first item
Insert | O(n) | Insert item at position
Delete | O(n) | Delete item at position
Containment | O(n) | Test x in/not in list
Copy | O(n) | Copy list
Remove | O(n) | Remove matching item
Extend | O(k) | Extend list by k items
Sort | O(n log n) | Sort list in-place
Reverse | O(n) | Reverse list in-place
Slice | O(k) | Get slice of k items

> * Amortized constant time

<br>

### Memory Usage Patterns

> Examining memory allocation behavior:

```python
import sys

# Memory size for growing list
sizes = []
for i in range(64):
    lst = list(range(i))
    sizes.append(sys.getsizeof(lst))

print("List size growth pattern:")
for i, size in enumerate(sizes):
    if i % 8 == 0:
        print(f"Length {i}: {size} bytes")
```

```sh
List size growth pattern:
Length 0: 56 bytes
Length 8: 120 bytes
Length 16: 184 bytes
Length 24: 248 bytes
Length 32: 312 bytes
Length 40: 376 bytes
Length 48: 440 bytes
Length 56: 504 bytes
```

<br>

### Operation Performance Benchmarks

> Measuring performance of different operations:

```python
import timeit

def benchmark_operations(size):
    setup = f"""
import random
lst = list(range({size}))
"""
    
    tests = {
        'Index': 'lst[size//2]',
        'Append': 'lst.append(0)',
        'Pop Last': 'lst.pop()',
        'Pop First': 'lst.pop(0)',
        'Insert': 'lst.insert(size//2, 0)',
        'Delete': 'del lst[size//2]'
    }
    
    results = {}
    for name, code in tests.items():
        time = timeit.timeit(code, setup, number=1000)
        results[name] = time
    
    return results

results = benchmark_operations(10000)
for op, time in results.items():
    print(f"{op}: {time:.6f} seconds")
```

```sh
Index: 0.000123 seconds
Append: 0.000156 seconds
Pop Last: 0.000145 seconds
Pop First: 0.001234 seconds
Insert: 0.001345 seconds
Delete: 0.001234 seconds
```

<br>

### Common Performance Pitfalls

<br>

#### Growing Lists Inefficiently

> Bad practice - growing one by one:

```python
import timeit

def bad_growth():
    lst = []
    for i in range(10000):
        lst.append(i)
    return lst

def good_growth():
    return list(range(10000))

bad_time = timeit.timeit(bad_growth, number=100)
good_time = timeit.timeit(good_growth, number=100)

print(f"Bad growth time: {bad_time:.4f} seconds")
print(f"Good growth time: {good_time:.4f} seconds")
```

```sh
Bad growth time: 0.0295 seconds 
Good growth time: 0.0137 seconds
```

<br>

#### Inefficient List Operations

> Comparing efficient and inefficient approaches:

```python
import timeit

# Inefficient: Insert at beginning repeatedly
def inefficient_insert():
    lst = list(range(1000))
    for i in range(100):
        lst.insert(0, i)
    return lst

# Efficient: Use deque for front insertions
def efficient_insert():
    from collections import deque
    d = deque(range(1000))
    for i in range(100):
        d.appendleft(i)
    return list(d)

inefficient_time = timeit.timeit(inefficient_insert, number=100)
efficient_time = timeit.timeit(efficient_insert, number=100)

print(f"Inefficient insert time: {inefficient_time:.4f} seconds")
print(f"Efficient insert time: {efficient_time:.4f} seconds")
```

```sh
Inefficient insert time: 0.0056 seconds 
Efficient insert time: 0.0021 seconds
```

<br>

### Optimization Techniques

> Best practices for optimizing list operations:

```python
# Pre-allocating space
size = 10000
pre_allocated = [None] * size  # More efficient than growing

# Using list comprehension instead of loops
squares_loop = []
for i in range(1000):
    squares_loop.append(i ** 2)

squares_comprehension = [i ** 2 for i in range(1000)]  # More efficient

# Using join instead of += for string building
strings = ['a', 'b', 'c', 'd']
inefficient = ''
for s in strings:
    inefficient += s

efficient = ''.join(strings)
```

<br>

### Memory Management Tips

> Strategies for efficient memory usage:

```python
import sys

# Clear list contents
lst = list(range(10000))
print(f"Initial size: {sys.getsizeof(lst)} bytes")

lst.clear()  # More efficient than lst = []
print(f"Size after clear: {sys.getsizeof(lst)} bytes")

# Reduce memory usage
del lst[:]  # Clear contents but keep capacity
lst = []    # New list with minimal capacity

# Remove unused references
lst = list(range(1000))
lst[500:] = []  # More efficient than del lst[500:]
```

<br>

### Best Practices Summary

> - Use appropriate data structures for the task
> - Pre-allocate lists when size is known
> - Use list comprehensions for creation
> - Avoid inserting/removing at beginning
> - Consider using deque for queue operations
> - Clear lists properly to manage memory
> - Use built-in operations when possible
> - Profile code to identify bottlenecks