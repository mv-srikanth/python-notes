# Module 2: String Operations

## Overview
This module covers working with text data in Python, including string manipulation, formatting, and commonly used string methods.

---

## 2.1 String Basics

### Concept
Strings are sequences of characters used to represent text.

### Theory
- Strings can be created with single quotes `'...'` or double quotes `"..."`
- Strings are immutable (cannot be changed after creation)
- Strings are indexed (each character has a position starting from 0)

### Examples

```python
# Creating strings
name = "Alice"
message = 'Hello, World!'
multiline = """This is a
multiline string"""

# String indexing (0-based)
text = "Python"
print(text[0])    # 'P' (first character)
print(text[5])    # 'n' (last character)
print(text[-1])   # 'n' (negative indexing from end)
print(text[-2])   # 'o'

# String slicing [start:end:step]
text = "Programming"
print(text[0:4])     # 'Prog' (indices 0-3)
print(text[:4])      # 'Prog' (start from beginning)
print(text[4:])      # 'ramming' (to the end)
print(text[::2])     # 'Pormig' (every 2nd character)
print(text[::-1])    # 'gnimmargorP' (reverse)

# String length
print(len("Hello"))  # 5
```

### Key Points
- Indexing starts at 0
- Negative indices count from the end
- Slicing syntax: `[start:end]` (end is exclusive)
- Use `len()` to get string length

---

## 2.2 String Concatenation and Repetition

### Concept
Combining and repeating strings.

### Theory
- Use `+` to concatenate (join) strings
- Use `*` to repeat strings
- Cannot directly concatenate strings with other types

### Examples

```python
# Concatenation
first = "Hello"
second = "World"
greeting = first + " " + second  # "Hello World"

# Repetition
line = "=" * 20  # "===================="
echo = "Ha" * 3  # "HaHaHa"

# Cannot mix types directly
# Wrong:
# result = "Age: " + 25  # Error!

# Correct:
age = 25
result = "Age: " + str(age)  # "Age: 25"

# Building strings
name = "Alice"
age = 30
info = name + " is " + str(age) + " years old"
```

### Key Points
- Use `+` for concatenation
- Convert non-strings with `str()` before concatenating
- String concatenation creates new strings (immutability)

---

## 2.3 String Formatting

### Concept
Modern ways to insert values into strings.

### Theory
Python offers several formatting methods:
1. f-strings (Python 3.6+) - Recommended
2. `.format()` method
3. `%` operator (older style)

### Examples

```python
name = "Bob"
age = 25
height = 5.9

# f-strings (modern, preferred)
message = f"My name is {name} and I'm {age} years old"
precise = f"Height: {height:.2f} feet"  # 2 decimal places

# .format() method
message = "My name is {} and I'm {} years old".format(name, age)
message = "My name is {0} and I'm {1} years old".format(name, age)
message = "My name is {n} and I'm {a} years old".format(n=name, a=age)

# % operator (older)
message = "My name is %s and I'm %d years old" % (name, age)

# Formatting numbers
pi = 3.14159265
print(f"{pi:.2f}")      # "3.14" (2 decimals)
print(f"{pi:.4f}")      # "3.1416" (4 decimals)
print(f"{1000:,}")      # "1,000" (thousands separator)
print(f"{0.5:.0%}")     # "50%" (percentage)
```

### Key Points
- f-strings are the most readable and recommended
- Use `:.2f` for decimal precision
- Curly braces `{}` hold expressions in f-strings

---

## 2.4 String Methods

### Concept
Built-in functions that operate on strings.

### Theory
Strings have many built-in methods for manipulation and analysis. Remember: strings are immutable, so these methods return new strings.

### Examples

```python
text = "  Hello World  "

# Case conversion
print(text.upper())      # "  HELLO WORLD  "
print(text.lower())      # "  hello world  "
print(text.title())      # "  Hello World  "
print(text.capitalize()) # "  hello world  " (first char only)

# Whitespace removal
print(text.strip())      # "Hello World" (both ends)
print(text.lstrip())     # "Hello World  " (left end)
print(text.rstrip())     # "  Hello World" (right end)

# Searching
sentence = "Python is awesome and Python is powerful"
print(sentence.find("Python"))       # 0 (first occurrence)
print(sentence.find("Java"))         # -1 (not found)
print(sentence.count("Python"))      # 2 (occurrences)
print(sentence.startswith("Python")) # True
print(sentence.endswith("ful"))      # True

# Replacing
print(sentence.replace("Python", "Programming"))
# "Programming is awesome and Programming is powerful"

# Splitting and joining
words = sentence.split()  # Split by whitespace
print(words)              # ['Python', 'is', 'awesome', ...]

csv = "apple,banana,orange"
fruits = csv.split(",")   # ['apple', 'banana', 'orange']

# Join list into string
items = ["apple", "banana", "orange"]
result = ", ".join(items)  # "apple, banana, orange"
result = "-".join(items)   # "apple-banana-orange"

# Checking content
print("123".isdigit())    # True
print("abc".isalpha())    # True
print("abc123".isalnum()) # True
print("  ".isspace())     # True
```

### Common String Methods

| Method | Description | Example |
|--------|-------------|---------|
| `.upper()` | Convert to uppercase | `"hello".upper()` → `"HELLO"` |
| `.lower()` | Convert to lowercase | `"HELLO".lower()` → `"hello"` |
| `.strip()` | Remove whitespace from ends | `" hi ".strip()` → `"hi"` |
| `.replace(old, new)` | Replace substring | `"cat".replace("c", "b")` → `"bat"` |
| `.split(sep)` | Split into list | `"a,b,c".split(",")` → `["a","b","c"]` |
| `.join(list)` | Join list into string | `",".join(["a","b"])` → `"a,b"` |
| `.find(sub)` | Find substring index | `"hello".find("ll")` → `2` |
| `.count(sub)` | Count occurrences | `"aaa".count("a")` → `3` |
| `.startswith(sub)` | Check if starts with | `"hello".startswith("he")` → `True` |
| `.isdigit()` | Check if all digits | `"123".isdigit()` → `True` |

---

## Practice Exercises

### Related Files
Based on your code, these exercises practice string operations:

1. **strings2.py** - String methods practice
2. **prgm10.py** - String manipulation
3. **prgm13.py** - String operations
4. **prgm14.py** - Advanced string methods
5. **if_prgm.py** - Strings with conditionals

### Exercise 1: Name Formatter
Create a program that takes a full name and formats it properly.

```python
# Input: "jOHN dOE"
# Output: "John Doe" (title case)
# Also show: uppercase, lowercase, initials

name = input("Enter full name: ")
# Your code here
```

### Exercise 2: Email Validator
Check if an email is valid (contains @ and .)

```python
email = input("Enter email: ")
# Your code here
# Check: has @, has ., @ comes before .
```

### Exercise 3: Word Counter
Count words and characters in a sentence.

```python
sentence = input("Enter a sentence: ")
# Your code here
# Show: word count, character count, without spaces
```

### Exercise 4: Text Reverser
Reverse a string and check if it's a palindrome.

```python
text = input("Enter text: ")
# Your code here
# Show reversed text
# Check if palindrome (same forwards and backwards)
```

### Exercise 5: CSV Parser
Split a comma-separated string and display as a numbered list.

```python
# Input: "apple,banana,orange"
# Output:
# 1. apple
# 2. banana
# 3. orange
```

---

## Common Mistakes to Avoid

1. **Trying to modify strings directly**
   ```python
   # Wrong - strings are immutable!
   text = "hello"
   text[0] = "H"  # Error!

   # Correct
   text = "H" + text[1:]  # "Hello"
   text = text.replace("h", "H")  # "Hello"
   ```

2. **Forgetting that methods return new strings**
   ```python
   # Wrong - doesn't modify original
   text = "  hello  "
   text.strip()  # This returns a new string but doesn't save it

   # Correct
   text = text.strip()  # Save the result
   ```

3. **Case-sensitive comparisons**
   ```python
   # Might fail
   if input("Continue? (yes/no): ") == "yes":
       # Won't match "Yes", "YES", "YeS"

   # Better
   if input("Continue? (yes/no): ").lower() == "yes":
       # Matches any case variation
   ```

---

## Summary Checklist

- [ ] Understand string indexing and slicing
- [ ] Know how to concatenate and repeat strings
- [ ] Use f-strings for formatting
- [ ] Apply common string methods (.upper(), .lower(), .strip())
- [ ] Split strings into lists and join lists into strings
- [ ] Search within strings (.find(), .count(), .startswith())
- [ ] Replace text with .replace()
- [ ] Validate string content (.isdigit(), .isalpha())

---

**Previous Module**: [01_Basics.md](01_Basics.md)
**Next Module**: [03_Control_Flow.md](03_Control_Flow.md) - Conditionals and Loops
