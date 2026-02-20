# Module 5: Functions

## Overview
This module covers writing reusable code with functions, including parameters, return values, scope, and advanced function concepts.

---

## 5.1 Function Basics

### Concept
Functions are reusable blocks of code that perform specific tasks.

### Theory
- Functions help organize code and avoid repetition (DRY principle)
- Defined with `def` keyword
- Can accept inputs (parameters) and produce outputs (return values)
- Called by name with parentheses

### Examples

```python
# Basic function (no parameters, no return)
def greet():
    print("Hello, World!")

greet()  # Call the function

# Function with parameters
def greet_person(name):
    print(f"Hello, {name}!")

greet_person("Alice")  # Hello, Alice!
greet_person("Bob")    # Hello, Bob!

# Function with multiple parameters
def add_numbers(a, b):
    result = a + b
    print(f"{a} + {b} = {result}")

add_numbers(5, 3)  # 5 + 3 = 8

# Function with return value
def multiply(a, b):
    return a * b

result = multiply(4, 5)  # result = 20
print(result)

# Multiple return values (returns a tuple)
def get_stats(numbers):
    total = sum(numbers)
    count = len(numbers)
    average = total / count
    return total, count, average

total, count, avg = get_stats([1, 2, 3, 4, 5])
print(f"Average: {avg}")
```

### Key Points
- Use `def` to define functions
- Function names should be descriptive and use snake_case
- Use `return` to send values back to caller
- Functions without `return` implicitly return `None`

---

## 5.2 Parameters and Arguments

### Concept
Parameters are variables in function definitions; arguments are values passed when calling.

### Theory
Python supports several types of parameters:
- **Positional**: Order matters
- **Keyword**: Named arguments
- **Default**: Parameters with default values
- **Variable-length**: Accept any number of arguments

### Examples

```python
# Positional parameters (order matters)
def divide(numerator, denominator):
    return numerator / denominator

result = divide(10, 2)  # 5.0
# divide(2, 10) would give 0.2 (different!)

# Keyword arguments (order doesn't matter)
result = divide(denominator=2, numerator=10)  # 5.0

# Default parameters
def greet(name, greeting="Hello"):
    return f"{greeting}, {name}!"

print(greet("Alice"))              # Hello, Alice!
print(greet("Bob", "Hi"))          # Hi, Bob!
print(greet("Eve", greeting="Hey"))  # Hey, Eve!

# Variable-length arguments (*args)
def sum_all(*numbers):
    total = 0
    for num in numbers:
        total += num
    return total

print(sum_all(1, 2, 3))        # 6
print(sum_all(1, 2, 3, 4, 5))  # 15

# Keyword variable-length arguments (**kwargs)
def print_info(**info):
    for key, value in info.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=25, job="Engineer")
# Output:
# name: Alice
# age: 25
# job: Engineer

# Combining parameter types
def complex_function(pos1, pos2, default="value", *args, **kwargs):
    print(f"Positional: {pos1}, {pos2}")
    print(f"Default: {default}")
    print(f"Args: {args}")
    print(f"Kwargs: {kwargs}")

complex_function(1, 2, 3, 4, 5, key1="a", key2="b")
```

### Key Points
- Default parameters must come after non-default ones
- `*args` captures extra positional arguments as tuple
- `**kwargs` captures extra keyword arguments as dictionary
- Use keyword arguments for clarity

---

## 5.3 Scope and Lifetime

### Concept
Scope determines where variables are accessible; lifetime is how long they exist.

### Theory
- **Local scope**: Variables inside a function
- **Global scope**: Variables outside all functions
- **LEGB Rule**: Local → Enclosing → Global → Built-in

### Examples

```python
# Global variable
counter = 0

def increment():
    global counter  # Declare we're using global variable
    counter += 1

increment()
print(counter)  # 1

# Local variable (separate from global)
x = 10  # Global

def my_function():
    x = 5  # Local (doesn't affect global x)
    print(f"Inside function: {x}")  # 5

my_function()
print(f"Outside function: {x}")  # 10

# Enclosing scope (nested functions)
def outer():
    x = "outer"

    def inner():
        nonlocal x  # Modify enclosing scope variable
        x = "inner"
        print(f"Inner: {x}")

    inner()
    print(f"Outer: {x}")  # "inner" (modified by inner())

outer()

# Best practice: avoid global variables
# Pass data as parameters instead
def better_increment(counter):
    return counter + 1

counter = 0
counter = better_increment(counter)
print(counter)  # 1
```

### Key Points
- Variables created in functions are local (private to function)
- Use `global` keyword to modify global variables (avoid when possible)
- Use `nonlocal` for nested function variables
- Pass data as parameters rather than using globals

---

## 5.4 Lambda Functions

### Concept
Small anonymous functions defined with `lambda` keyword.

### Theory
- Syntax: `lambda parameters: expression`
- Can have any number of parameters but only one expression
- Returns the result of the expression automatically
- Useful for simple, one-time operations

### Examples

```python
# Regular function
def square(x):
    return x ** 2

# Equivalent lambda
square_lambda = lambda x: x ** 2

print(square(5))         # 25
print(square_lambda(5))  # 25

# Lambda with multiple parameters
add = lambda a, b: a + b
print(add(3, 4))  # 7

# Common use: with sorted()
students = [
    {"name": "Alice", "grade": 85},
    {"name": "Bob", "grade": 92},
    {"name": "Charlie", "grade": 78}
]

# Sort by grade
sorted_students = sorted(students, key=lambda s: s["grade"])
print([s["name"] for s in sorted_students])  # Charlie, Alice, Bob

# Use with map() - apply function to all items
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, numbers))
print(squared)  # [1, 4, 9, 16, 25]

# Use with filter() - keep items that match condition
evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)  # [2, 4]

# Use with sorted()
words = ["banana", "apple", "cherry", "date"]
sorted_by_length = sorted(words, key=lambda w: len(w))
print(sorted_by_length)  # ['date', 'apple', 'banana', 'cherry']
```

### Key Points
- Use lambdas for simple, one-line functions
- For complex logic, use regular functions with `def`
- Common with `map()`, `filter()`, `sorted()`, etc.
- Don't assign lambdas to variables (use `def` instead)

---

## 5.5 Docstrings and Type Hints

### Concept
Document your functions and specify expected types.

### Examples

```python
# Docstring - explains what function does
def calculate_area(radius):
    """
    Calculate the area of a circle.

    Args:
        radius (float): The radius of the circle

    Returns:
        float: The area of the circle

    Example:
        >>> calculate_area(5)
        78.53981633974483
    """
    import math
    return math.pi * radius ** 2

# Access docstring
print(calculate_area.__doc__)

# Type hints (Python 3.5+)
def greet(name: str, age: int) -> str:
    """Greet a person with their name and age."""
    return f"Hello {name}, you are {age} years old"

# Type hints for complex types
from typing import List, Dict, Tuple, Optional

def process_scores(scores: List[int]) -> Dict[str, float]:
    """Calculate statistics from a list of scores."""
    return {
        "average": sum(scores) / len(scores),
        "max": max(scores),
        "min": min(scores)
    }

def find_user(user_id: int) -> Optional[Dict[str, str]]:
    """Find a user by ID, return None if not found."""
    # Returns either a dict or None
    pass
```

### Key Points
- Use docstrings to explain what functions do
- Type hints improve code readability
- Type hints don't enforce types (Python is still dynamically typed)
- Use typing module for complex types

---

## 5.6 Recursion

### Concept
Functions that call themselves to solve problems.

### Examples

```python
# Classic example: Factorial
def factorial(n):
    """Calculate n! = n × (n-1) × ... × 1"""
    if n <= 1:  # Base case
        return 1
    else:  # Recursive case
        return n * factorial(n - 1)

print(factorial(5))  # 120 (5 × 4 × 3 × 2 × 1)

# Fibonacci sequence
def fibonacci(n):
    """Get the nth Fibonacci number."""
    if n <= 1:
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)

print([fibonacci(i) for i in range(8)])  # [0, 1, 1, 2, 3, 5, 8, 13]

# Countdown
def countdown(n):
    """Print countdown from n to 1."""
    if n <= 0:
        print("Blast off!")
    else:
        print(n)
        countdown(n - 1)

countdown(5)

# Sum of list (recursive)
def sum_list(numbers):
    """Sum all numbers in a list recursively."""
    if not numbers:  # Empty list
        return 0
    return numbers[0] + sum_list(numbers[1:])

print(sum_list([1, 2, 3, 4, 5]))  # 15
```

### Key Points
- Every recursive function needs a base case (stopping condition)
- Recursion can be elegant but may be slower than loops
- Risk of stack overflow with deep recursion
- For most tasks, iteration (loops) is more efficient

---

## Practice Exercises

### Exercise 1: Temperature Converter
Create functions to convert between Celsius and Fahrenheit.

```python
def celsius_to_fahrenheit(celsius):
    # Formula: F = (C × 9/5) + 32
    pass

def fahrenheit_to_celsius(fahrenheit):
    # Formula: C = (F - 32) × 5/9
    pass

# Test your functions
print(celsius_to_fahrenheit(0))    # Should be 32
print(fahrenheit_to_celsius(212))  # Should be 100
```

### Exercise 2: Prime Number Checker
Write a function to check if a number is prime.

```python
def is_prime(n):
    """Return True if n is prime, False otherwise."""
    # Your code here
    pass

# Test
print(is_prime(17))  # True
print(is_prime(20))  # False
```

### Exercise 3: List Statistics
Create a function that returns statistics about a list of numbers.

```python
def get_statistics(numbers):
    """
    Return a dictionary with min, max, average, and sum.
    """
    # Your code here
    pass

numbers = [10, 20, 30, 40, 50]
stats = get_statistics(numbers)
print(stats)
# Should print: {'min': 10, 'max': 50, 'average': 30.0, 'sum': 150}
```

### Exercise 4: Password Validator
Check if a password meets requirements.

```python
def is_valid_password(password):
    """
    Password must:
    - Be at least 8 characters long
    - Contain at least one uppercase letter
    - Contain at least one lowercase letter
    - Contain at least one digit

    Returns: True if valid, False otherwise
    """
    # Your code here
    pass
```

### Exercise 5: Palindrome Checker
Check if a string is a palindrome (reads same forwards and backwards).

```python
def is_palindrome(text):
    """Return True if text is a palindrome."""
    # Your code here
    # Hint: compare text with text[::-1]
    pass

print(is_palindrome("racecar"))  # True
print(is_palindrome("hello"))    # False
```

### Exercise 6: Fibonacci with Memoization
Optimize Fibonacci using a cache to store results.

```python
def fibonacci_memo(n, cache={}):
    """Calculate Fibonacci with memoization."""
    # Your code here
    pass
```

---

## Common Mistakes to Avoid

1. **Forgetting to return**
   ```python
   # Wrong - prints but doesn't return
   def add(a, b):
       print(a + b)

   result = add(2, 3)  # result is None!

   # Correct
   def add(a, b):
       return a + b
   ```

2. **Mutable default arguments**
   ```python
   # Wrong - the list persists between calls!
   def add_item(item, items=[]):
       items.append(item)
       return items

   # Correct
   def add_item(item, items=None):
       if items is None:
           items = []
       items.append(item)
       return items
   ```

3. **Missing base case in recursion**
   ```python
   # Wrong - infinite recursion!
   def countdown(n):
       print(n)
       countdown(n - 1)  # Never stops!

   # Correct
   def countdown(n):
       if n <= 0:
           return
       print(n)
       countdown(n - 1)
   ```

---

## Summary Checklist

- [ ] Define functions with `def`
- [ ] Use parameters to accept inputs
- [ ] Return values with `return`
- [ ] Understand scope (local vs global)
- [ ] Use default parameters
- [ ] Work with *args and **kwargs
- [ ] Write lambda functions for simple operations
- [ ] Document functions with docstrings
- [ ] Apply type hints for clarity
- [ ] Understand when to use recursion

---

**Previous Module**: [04_Data_Structures.md](04_Data_Structures.md)
**Next Module**: [06_Advanced_Topics.md](06_Advanced_Topics.md) - Classes, File I/O, and more
