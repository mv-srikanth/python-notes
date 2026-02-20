# Module 3: Control Flow

## Overview
This module covers decision-making with conditionals (if/elif/else) and repetition with loops (for and while).

---

## 3.1 Conditional Statements (if/elif/else)

### Concept
Conditionals allow programs to make decisions and execute different code based on conditions.

### Theory
- **if**: Execute code if condition is True
- **elif**: Check additional conditions if previous ones were False
- **else**: Execute code if all previous conditions were False

### Comparison Operators
| Operator | Meaning | Example |
|----------|---------|---------|
| `==` | Equal to | `x == 5` |
| `!=` | Not equal to | `x != 5` |
| `>` | Greater than | `x > 5` |
| `<` | Less than | `x < 5` |
| `>=` | Greater or equal | `x >= 5` |
| `<=` | Less or equal | `x <= 5` |

### Examples

```python
# Basic if statement
age = 18
if age >= 18:
    print("You are an adult")

# if-else
temperature = 30
if temperature > 25:
    print("It's hot!")
else:
    print("It's cool!")

# if-elif-else (multiple conditions)
score = 85

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
elif score >= 60:
    grade = "D"
else:
    grade = "F"

print(f"Your grade is: {grade}")

# Nested if statements
age = 20
has_license = True

if age >= 18:
    if has_license:
        print("You can drive")
    else:
        print("You need a license")
else:
    print("You're too young to drive")
```

### Key Points
- Indentation is crucial in Python (use 4 spaces)
- Conditions evaluate to True or False
- Only the first True condition executes in if-elif-else chains
- Use `==` for comparison, not `=` (assignment)

---

## 3.2 Logical Operators

### Concept
Combine multiple conditions using logical operators.

### Theory
- **and**: Both conditions must be True
- **or**: At least one condition must be True
- **not**: Negates (reverses) the condition

### Examples

```python
# AND operator
age = 25
has_ticket = True

if age >= 18 and has_ticket:
    print("You can enter the concert")

# OR operator
day = "Saturday"

if day == "Saturday" or day == "Sunday":
    print("It's the weekend!")

# NOT operator
is_raining = False

if not is_raining:
    print("You don't need an umbrella")

# Combining operators
age = 30
is_member = True
has_coupon = False

if (age >= 25 and is_member) or has_coupon:
    print("You get a discount")

# Checking multiple values
choice = "yes"

if choice in ["yes", "y", "YES", "Yes"]:
    print("Confirmed!")

# Checking ranges
score = 75

if 70 <= score < 80:
    print("Grade: C")
```

### Truth Values
In Python, these values are considered False:
- `False`, `None`
- `0`, `0.0`
- Empty sequences: `""`, `[]`, `()`, `{}`

Everything else is considered True.

```python
# Truthy/Falsy examples
if "":
    print("This won't print")  # Empty string is falsy

if "hello":
    print("This will print")   # Non-empty string is truthy

if 0:
    print("This won't print")  # 0 is falsy

if 42:
    print("This will print")   # Non-zero number is truthy
```

---

## 3.3 For Loops

### Concept
Iterate over a sequence (list, string, range) a specific number of times.

### Theory
For loops execute code for each item in a sequence. They're used when you know how many times to repeat.

### Examples

```python
# Looping through a range
for i in range(5):
    print(i)  # Prints 0, 1, 2, 3, 4

# Range with start and end
for i in range(1, 6):
    print(i)  # Prints 1, 2, 3, 4, 5

# Range with step
for i in range(0, 10, 2):
    print(i)  # Prints 0, 2, 4, 6, 8

# Looping through a string
for char in "Python":
    print(char)  # Prints P, y, t, h, o, n

# Looping through a list
fruits = ["apple", "banana", "orange"]
for fruit in fruits:
    print(fruit)

# With index using enumerate()
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")
# Output:
# 0: apple
# 1: banana
# 2: orange

# Nested loops
for i in range(1, 4):
    for j in range(1, 4):
        print(f"{i} x {j} = {i*j}")
    print()  # Empty line between groups

# Loop with calculations
total = 0
for i in range(1, 11):
    total += i
print(f"Sum of 1-10: {total}")  # 55
```

### Key Points
- `range(n)` generates numbers from 0 to n-1
- `range(start, end)` generates from start to end-1
- `range(start, end, step)` allows custom increments
- Use `enumerate()` when you need both index and value

---

## 3.4 While Loops

### Concept
Repeat code while a condition is True.

### Theory
While loops continue until the condition becomes False. They're used when you don't know in advance how many iterations are needed.

### Examples

```python
# Basic while loop
count = 0
while count < 5:
    print(count)
    count += 1  # Important: update counter!

# User input validation
password = ""
while password != "python123":
    password = input("Enter password: ")
print("Access granted!")

# Break statement (exit loop early)
while True:
    response = input("Continue? (yes/no): ")
    if response.lower() == "no":
        break
    print("Continuing...")

# Continue statement (skip to next iteration)
count = 0
while count < 10:
    count += 1
    if count % 2 == 0:  # If even
        continue  # Skip the rest, go to next iteration
    print(count)  # Only prints odd numbers

# While with else (executes if loop completes normally)
count = 0
while count < 3:
    print(count)
    count += 1
else:
    print("Loop completed normally")

# Infinite loop with break condition
while True:
    num = int(input("Enter a positive number (0 to quit): "))
    if num == 0:
        break
    if num < 0:
        print("Please enter a positive number")
        continue
    print(f"You entered: {num}")
```

### Key Points
- Always ensure the condition will eventually become False
- Forgetting to update the loop variable causes infinite loops
- `break` exits the loop completely
- `continue` skips to the next iteration
- Use while loops when the number of iterations is unknown

---

## 3.5 Loop Control: break, continue, pass

### Concept
Special statements to control loop execution.

### Examples

```python
# break: Exit loop immediately
for i in range(10):
    if i == 5:
        break
    print(i)  # Prints 0, 1, 2, 3, 4

# continue: Skip current iteration
for i in range(5):
    if i == 2:
        continue
    print(i)  # Prints 0, 1, 3, 4 (skips 2)

# pass: Do nothing (placeholder)
for i in range(5):
    if i == 2:
        pass  # TODO: Add logic later
    print(i)  # Prints all numbers

# Practical example: Finding first match
numbers = [1, 3, 5, 8, 9, 11]
for num in numbers:
    if num % 2 == 0:
        print(f"First even number: {num}")
        break
else:  # Executes if loop completes without break
    print("No even numbers found")
```

---

## Practice Exercises

### Related Files
Based on your code, these exercises practice control flow:

1. **control_structures.py** - If/elif/else and loops
2. **if_prgm.py** - Conditional statements
3. **pgm6.py** - Conditionals
4. **pgm7.py** - Control flow practice
5. **pgm10.py** - Loops and conditions
6. **prgm12.py** - For loops
7. **notes1.py** - Control flow notes

### Exercise 1: Grade Calculator
Write a program that assigns letter grades based on scores.

```python
# Input: numerical score (0-100)
# Output: Letter grade (A, B, C, D, F)
# A: 90-100, B: 80-89, C: 70-79, D: 60-69, F: 0-59

score = int(input("Enter score: "))
# Your code here
```

### Exercise 2: Odd or Even
Determine if a number is odd or even.

```python
number = int(input("Enter a number: "))
# Your code here
# Hint: Use modulus operator %
```

### Exercise 3: FizzBuzz
Classic programming problem:
- Print numbers 1-100
- For multiples of 3, print "Fizz"
- For multiples of 5, print "Buzz"
- For multiples of both, print "FizzBuzz"

```python
for i in range(1, 101):
    # Your code here
```

### Exercise 4: Multiplication Table
Print the multiplication table for a given number.

```python
num = int(input("Enter a number: "))
# Print: 1 x num = result, 2 x num = result, ..., 10 x num = result
```

### Exercise 5: Number Guessing Game
Computer picks a random number (1-100), user guesses.

```python
import random
secret = random.randint(1, 100)
attempts = 0

# Your code here
# Give hints: "Too high" or "Too low"
# Track number of attempts
```

### Exercise 6: Prime Number Checker
Check if a number is prime.

```python
num = int(input("Enter a number: "))
# Your code here
# Prime: only divisible by 1 and itself
```

### Exercise 7: Factorial Calculator
Calculate factorial using a loop.

```python
# n! = n × (n-1) × (n-2) × ... × 1
# Example: 5! = 5 × 4 × 3 × 2 × 1 = 120

n = int(input("Enter a number: "))
# Your code here
```

---

## Common Mistakes to Avoid

1. **Using = instead of ==**
   ```python
   # Wrong
   if x = 5:  # Syntax error!

   # Correct
   if x == 5:
   ```

2. **Forgetting colons and indentation**
   ```python
   # Wrong
   if x > 5
       print("Big")  # Missing colon

   # Correct
   if x > 5:
       print("Big")
   ```

3. **Infinite loops**
   ```python
   # Wrong - never ends!
   count = 0
   while count < 5:
       print(count)  # Forgot to increment!

   # Correct
   count = 0
   while count < 5:
       print(count)
       count += 1
   ```

4. **Off-by-one errors**
   ```python
   # Prints 0-9, not 1-10
   for i in range(10):
       print(i)

   # Correct for 1-10
   for i in range(1, 11):
       print(i)
   ```

---

## Summary Checklist

- [ ] Write if/elif/else statements correctly
- [ ] Use comparison operators (==, !=, >, <, >=, <=)
- [ ] Combine conditions with and, or, not
- [ ] Understand truthy and falsy values
- [ ] Use for loops with range()
- [ ] Use while loops with proper termination
- [ ] Apply break and continue appropriately
- [ ] Avoid infinite loops
- [ ] Write nested loops when needed

---

**Previous Module**: [02_Strings.md](02_Strings.md)
**Next Module**: [04_Data_Structures.md](04_Data_Structures.md) - Lists, Tuples, Dictionaries
