# Module 1: Python Basics

## Overview
This module covers the fundamental building blocks of Python programming: input/output, variables, data types, and basic arithmetic operations.

---

## 1.1 Basic Input and Output

### Concept
- **`print()`**: Displays output to the console
- **`input()`**: Reads user input as a string

### Theory
Python programs interact with users through input and output operations. The `print()` function sends data to the screen, while `input()` captures user input.

### Examples

```python
# Simple output
print("Hello, World!")

# Multiple outputs
print("Python", "is", "awesome")

# Formatted output
name = "Alice"
print(f"Hello, {name}!")

# Basic input
name = input("Enter your name: ")
print(f"Welcome, {name}!")

# Input with type conversion
age = int(input("Enter your age: "))
print(f"You are {age} years old")
```

### Key Points
- `input()` always returns a string
- Use type conversion (`int()`, `float()`) for numeric input
- f-strings (f"...") provide clean formatting

---

## 1.2 Variables and Assignment

### Concept
Variables are named containers that store data values.

### Theory
In Python, variables are created when you assign a value to them. Python is dynamically typed, meaning you don't need to declare variable types explicitly.

### Examples

```python
# Variable assignment
x = 10
name = "John"
pi = 3.14159
is_student = True

# Multiple assignment
a, b, c = 1, 2, 3

# Same value to multiple variables
x = y = z = 0

# Variable naming rules
user_name = "Alice"    # Valid (snake_case)
userName = "Bob"       # Valid (camelCase)
_private = 10          # Valid (starts with underscore)
# 2fast = 10           # Invalid (starts with number)
```

### Key Points
- Variable names are case-sensitive (`age` ≠ `Age`)
- Use descriptive names (`user_age` better than `x`)
- Follow PEP 8: use `snake_case` for variables

---

## 1.3 Data Types

### Concept
Python has several built-in data types for different kinds of values.

### Theory
The main basic data types are:
- **int**: Whole numbers (e.g., 42, -17)
- **float**: Decimal numbers (e.g., 3.14, -0.5)
- **str**: Text (e.g., "Hello")
- **bool**: True or False

### Examples

```python
# Integer
age = 25
year = 2026

# Float
height = 5.9
temperature = -3.5

# String
name = "Alice"
message = 'Hello World'

# Boolean
is_valid = True
is_complete = False

# Type checking
print(type(age))        # <class 'int'>
print(type(height))     # <class 'float'>
print(type(name))       # <class 'str'>

# Type conversion
x = "100"
y = int(x)              # Convert string to int
z = float(x)            # Convert string to float
s = str(42)             # Convert int to string
```

### Key Points
- Use `type()` to check data type
- Type conversion functions: `int()`, `float()`, `str()`, `bool()`
- Mixing types requires explicit conversion

---

## 1.4 Arithmetic Operations

### Concept
Python supports standard mathematical operations and some special operators.

### Theory
Arithmetic operators perform calculations on numeric values.

### Examples

```python
# Basic operations
a = 10
b = 3

addition = a + b        # 13
subtraction = a - b     # 7
multiplication = a * b  # 30
division = a / b        # 3.333... (always returns float)
floor_division = a // b # 3 (integer division)
modulus = a % b         # 1 (remainder)
exponent = a ** b       # 1000 (power)

# Order of operations (PEMDAS)
result = 2 + 3 * 4      # 14 (not 20)
result = (2 + 3) * 4    # 20 (use parentheses)

# Compound assignment
x = 5
x += 3   # x = x + 3 → 8
x -= 2   # x = x - 2 → 6
x *= 4   # x = x * 4 → 24
x /= 3   # x = x / 3 → 8.0
```

### Key Points
- Division `/` always returns float
- Floor division `//` returns integer (rounds down)
- Modulus `%` gives remainder
- Use parentheses to control order of operations

---

## Practice Exercises

### Related Files
Based on your code, these exercises practice these concepts:

1. **pgm1.py** - Basic I/O and arithmetic
2. **prgm1.py** - Variables and calculations
3. **pgm3.py** - Data type conversions
4. **pgm4.py** - Arithmetic operations
5. **pgm5.py** - Combined basic concepts
6. **exp1.py** - Week 1 basics exercise

### Exercise 1: Calculator
Create a simple calculator that takes two numbers and performs all arithmetic operations.

```python
# Your code here
num1 = float(input("Enter first number: "))
num2 = float(input("Enter second number: "))

# Perform and display all operations
```

### Exercise 2: Temperature Converter
Convert temperature from Celsius to Fahrenheit.
Formula: F = (C × 9/5) + 32

```python
# Your code here
```

### Exercise 3: Age Calculator
Ask for birth year and calculate current age.

```python
# Your code here
current_year = 2026
```

---

## Common Mistakes to Avoid

1. **Forgetting type conversion**
   ```python
   # Wrong
   age = input("Age: ")
   next_year = age + 1  # Error! Can't add int to string

   # Correct
   age = int(input("Age: "))
   next_year = age + 1
   ```

2. **Integer division when float needed**
   ```python
   # Might not be what you want
   average = (10 + 15) // 2  # 12 (floor division)

   # Usually better
   average = (10 + 15) / 2   # 12.5
   ```

3. **Variable naming errors**
   ```python
   # Wrong
   my-variable = 10  # Hyphens not allowed
   2fast = 20        # Can't start with number

   # Correct
   my_variable = 10
   fast_2 = 20
   ```

---

## Summary Checklist

- [ ] Understand `print()` and `input()` functions
- [ ] Know how to create and name variables
- [ ] Recognize the four basic data types (int, float, str, bool)
- [ ] Perform type conversions with `int()`, `float()`, `str()`
- [ ] Use all arithmetic operators (+, -, *, /, //, %, **)
- [ ] Apply compound assignment operators (+=, -=, etc.)
- [ ] Follow proper naming conventions

---

**Next Module**: [02_Strings.md](02_Strings.md) - Working with text data
