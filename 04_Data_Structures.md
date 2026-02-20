# Module 4: Data Structures

## Overview
This module covers Python's built-in data structures: lists, tuples, dictionaries, and sets. These allow you to organize and store collections of data efficiently.

---

## 4.1 Lists

### Concept
Lists are ordered, mutable (changeable) collections that can hold items of any type.

### Theory
- Lists are created with square brackets `[]`
- Items are ordered and indexed (starting from 0)
- Lists can contain duplicates
- Lists are mutable (can be modified after creation)

### Examples

```python
# Creating lists
numbers = [1, 2, 3, 4, 5]
fruits = ["apple", "banana", "orange"]
mixed = [1, "hello", 3.14, True]
empty = []

# Accessing elements (indexing)
fruits = ["apple", "banana", "orange"]
print(fruits[0])    # "apple" (first item)
print(fruits[-1])   # "orange" (last item)
print(fruits[1:3])  # ["banana", "orange"] (slicing)

# Modifying lists
fruits[1] = "mango"  # Change element
print(fruits)  # ["apple", "mango", "orange"]

# List length
print(len(fruits))  # 3

# Adding elements
fruits.append("grape")         # Add to end
fruits.insert(1, "pineapple")  # Insert at index 1
fruits.extend(["kiwi", "peach"])  # Add multiple items

# Removing elements
fruits.remove("apple")  # Remove by value
popped = fruits.pop()   # Remove and return last item
popped = fruits.pop(0)  # Remove and return item at index 0
del fruits[1]           # Delete by index
fruits.clear()          # Remove all items

# Finding elements
fruits = ["apple", "banana", "orange", "banana"]
print(fruits.index("banana"))  # 1 (first occurrence)
print(fruits.count("banana"))  # 2 (number of occurrences)
print("apple" in fruits)       # True (membership test)

# Sorting
numbers = [3, 1, 4, 1, 5, 9, 2, 6]
numbers.sort()           # Sort in place [1, 1, 2, 3, 4, 5, 6, 9]
numbers.sort(reverse=True)  # Sort descending
sorted_nums = sorted(numbers)  # Return new sorted list

# List operations
list1 = [1, 2, 3]
list2 = [4, 5, 6]
combined = list1 + list2    # [1, 2, 3, 4, 5, 6]
repeated = list1 * 3        # [1, 2, 3, 1, 2, 3, 1, 2, 3]

# Reversing
numbers = [1, 2, 3, 4, 5]
numbers.reverse()  # [5, 4, 3, 2, 1]
```

### Common List Methods

| Method | Description | Example |
|--------|-------------|---------|
| `.append(x)` | Add item to end | `list.append(5)` |
| `.insert(i, x)` | Insert at index | `list.insert(0, 'first')` |
| `.remove(x)` | Remove first occurrence | `list.remove('apple')` |
| `.pop([i])` | Remove and return item | `item = list.pop()` |
| `.clear()` | Remove all items | `list.clear()` |
| `.index(x)` | Find first index of value | `i = list.index('banana')` |
| `.count(x)` | Count occurrences | `n = list.count(5)` |
| `.sort()` | Sort in place | `list.sort()` |
| `.reverse()` | Reverse in place | `list.reverse()` |
| `.extend(list2)` | Add all items from list2 | `list.extend([4,5,6])` |

---

## 4.2 Tuples

### Concept
Tuples are ordered, immutable (unchangeable) collections.

### Theory
- Tuples are created with parentheses `()`
- Items are ordered and indexed
- Tuples cannot be modified after creation (immutable)
- Tuples are faster and use less memory than lists
- Use tuples for data that shouldn't change

### Examples

```python
# Creating tuples
coordinates = (10, 20)
person = ("Alice", 25, "Engineer")
single_item = (42,)  # Note the comma for single-item tuple
empty = ()

# Accessing elements
point = (10, 20, 30)
print(point[0])     # 10
print(point[-1])    # 30
print(point[1:3])   # (20, 30)

# Cannot modify tuples
# point[0] = 15  # Error! Tuples are immutable

# Tuple unpacking
coordinates = (10, 20)
x, y = coordinates  # x=10, y=20

name, age, job = ("Bob", 30, "Designer")
print(f"{name} is {age}")

# Tuple with one element (note the comma!)
single = (42,)   # This is a tuple
not_tuple = (42) # This is just an int!

# Tuple methods (only 2!)
numbers = (1, 2, 3, 2, 4, 2)
print(numbers.count(2))   # 3
print(numbers.index(3))   # 2

# Converting between lists and tuples
my_list = [1, 2, 3]
my_tuple = tuple(my_list)   # Convert list to tuple
back_to_list = list(my_tuple)  # Convert tuple to list

# Tuples are useful for multiple return values
def get_user():
    return ("Alice", 25, "Engineer")

name, age, job = get_user()
```

### Key Points
- Use parentheses `()` for tuples
- Tuples are immutable (cannot change)
- Use tuples for fixed data (coordinates, RGB values, etc.)
- Tuple unpacking is powerful for multiple assignment
- Single-item tuples need a trailing comma: `(42,)`

---

## 4.3 Dictionaries

### Concept
Dictionaries store key-value pairs, allowing fast lookup by key.

### Theory
- Dictionaries are created with curly braces `{}`
- Format: `{key: value}`
- Keys must be unique and immutable (strings, numbers, tuples)
- Values can be any type
- Dictionaries are mutable
- Order is preserved (Python 3.7+)

### Examples

```python
# Creating dictionaries
student = {
    "name": "Alice",
    "age": 20,
    "grade": "A"
}

empty_dict = {}
also_empty = dict()

# Accessing values
print(student["name"])      # "Alice"
print(student.get("age"))   # 20
print(student.get("phone", "Not found"))  # "Not found" (default)

# Adding/modifying entries
student["email"] = "alice@example.com"  # Add new key-value
student["age"] = 21  # Modify existing value

# Removing entries
del student["grade"]  # Delete by key
age = student.pop("age")  # Remove and return value
student.clear()  # Remove all items

# Checking keys
if "name" in student:
    print("Name exists")

# Dictionary methods
student = {"name": "Alice", "age": 20, "grade": "A"}

# Get all keys, values, or items
print(student.keys())    # dict_keys(['name', 'age', 'grade'])
print(student.values())  # dict_values(['Alice', 20, 'A'])
print(student.items())   # dict_items([('name', 'Alice'), ...])

# Iterating over dictionary
for key in student:
    print(key, student[key])

for key, value in student.items():
    print(f"{key}: {value}")

# Dictionary comprehension
squares = {x: x**2 for x in range(5)}
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# Merging dictionaries (Python 3.9+)
dict1 = {"a": 1, "b": 2}
dict2 = {"c": 3, "d": 4}
merged = dict1 | dict2  # {'a': 1, 'b': 2, 'c': 3, 'd': 4}

# Update dictionary
student.update({"email": "alice@mail.com", "phone": "123-456"})
```

### Common Dictionary Methods

| Method | Description | Example |
|--------|-------------|---------|
| `.get(key, default)` | Get value with default | `d.get('name', 'Unknown')` |
| `.keys()` | Get all keys | `for key in d.keys()` |
| `.values()` | Get all values | `for val in d.values()` |
| `.items()` | Get key-value pairs | `for k,v in d.items()` |
| `.pop(key)` | Remove and return value | `val = d.pop('age')` |
| `.update(dict2)` | Add/update from dict2 | `d.update({'new': 123})` |
| `.clear()` | Remove all items | `d.clear()` |

---

## 4.4 Sets

### Concept
Sets are unordered collections of unique elements.

### Theory
- Sets are created with curly braces `{}` or `set()`
- Elements must be unique (duplicates are removed)
- Elements must be immutable (strings, numbers, tuples)
- Sets are unordered (no indexing)
- Useful for removing duplicates and set operations

### Examples

```python
# Creating sets
numbers = {1, 2, 3, 4, 5}
fruits = {"apple", "banana", "orange"}
empty_set = set()  # Note: {} creates an empty dict, not set!

# Duplicates are automatically removed
numbers = {1, 2, 2, 3, 3, 3}
print(numbers)  # {1, 2, 3}

# Adding and removing
fruits.add("grape")
fruits.remove("apple")  # Error if not exists
fruits.discard("apple")  # No error if not exists
popped = fruits.pop()  # Remove and return arbitrary element

# Set operations
set1 = {1, 2, 3, 4}
set2 = {3, 4, 5, 6}

union = set1 | set2          # {1, 2, 3, 4, 5, 6}
intersection = set1 & set2   # {3, 4}
difference = set1 - set2     # {1, 2}
symmetric_diff = set1 ^ set2 # {1, 2, 5, 6}

# Set methods
print(set1.union(set2))
print(set1.intersection(set2))
print(set1.difference(set2))

# Subset and superset
set1 = {1, 2, 3}
set2 = {1, 2, 3, 4, 5}
print(set1.issubset(set2))    # True
print(set2.issuperset(set1))  # True

# Membership testing (fast!)
if 3 in set1:
    print("Found 3")

# Removing duplicates from list
numbers = [1, 2, 2, 3, 3, 3, 4]
unique = list(set(numbers))  # [1, 2, 3, 4]

# Frozen sets (immutable sets)
frozen = frozenset([1, 2, 3])
# frozen.add(4)  # Error! Frozen sets are immutable
```

### Common Set Methods

| Method | Description | Example |
|--------|-------------|---------|
| `.add(x)` | Add element | `s.add(5)` |
| `.remove(x)` | Remove (error if not exists) | `s.remove(3)` |
| `.discard(x)` | Remove (no error) | `s.discard(3)` |
| `.pop()` | Remove arbitrary element | `x = s.pop()` |
| `.union(s2)` | Combine sets | `s1.union(s2)` |
| `.intersection(s2)` | Common elements | `s1.intersection(s2)` |
| `.difference(s2)` | Elements in s1 not s2 | `s1.difference(s2)` |

---

## Practice Exercises

### Related Files
Based on your code, these exercises involve data structures:

1. **pgm7.py** - Tuple operations
2. **pgm8.py** - Tuple practice
3. **prgm14.py** - Dictionary operations
4. **prgm12.py** - Tuples and loops
5. **prm2.py** - Dictionary practice

### Exercise 1: Shopping List
Create a shopping list program using lists.

```python
# Features:
# 1. Add items
# 2. Remove items
# 3. Display all items
# 4. Count total items
shopping_list = []
# Your code here
```

### Exercise 2: Student Records
Store student information in dictionaries.

```python
# Create a dictionary for each student with:
# name, age, grade, subjects (list)
student1 = {
    "name": "Alice",
    "age": 20,
    "grade": "A",
    "subjects": ["Math", "Physics", "CS"]
}

# Your code here:
# Add 3 students
# Print all student names
# Find student with highest grade
```

### Exercise 3: Word Frequency Counter
Count how many times each word appears in a sentence.

```python
sentence = "the quick brown fox jumps over the lazy dog the fox"
# Your code here
# Output: {"the": 3, "quick": 1, "brown": 1, ...}
```

### Exercise 4: Remove Duplicates
Remove duplicates from a list while preserving order.

```python
numbers = [1, 2, 3, 2, 4, 3, 5, 1, 6]
# Your code here
# Output: [1, 2, 3, 4, 5, 6]
```

### Exercise 5: Contact Book
Create a simple contact book using dictionaries.

```python
contacts = {}
# Add contacts: name -> phone number
# Search for contact
# Display all contacts
# Delete contact
```

### Exercise 6: Set Operations
Given two lists, find common elements and unique elements.

```python
list1 = [1, 2, 3, 4, 5]
list2 = [4, 5, 6, 7, 8]

# Find: common elements, elements only in list1, all unique elements
```

---

## Comparison Table

| Feature | List | Tuple | Dictionary | Set |
|---------|------|-------|------------|-----|
| Syntax | `[...]` | `(...)` | `{k:v}` | `{...}` |
| Ordered | ✓ | ✓ | ✓ (3.7+) | ✗ |
| Mutable | ✓ | ✗ | ✓ | ✓ |
| Duplicates | ✓ | ✓ | ✗ (keys) | ✗ |
| Indexed | ✓ | ✓ | By key | ✗ |
| Use case | Collections | Fixed data | Key-value | Unique items |

---

## Summary Checklist

- [ ] Create and manipulate lists
- [ ] Use list methods (.append(), .remove(), .sort(), etc.)
- [ ] Understand list indexing and slicing
- [ ] Work with tuples and understand immutability
- [ ] Use tuple unpacking
- [ ] Create and access dictionaries
- [ ] Iterate over dictionary keys, values, and items
- [ ] Use sets to find unique elements
- [ ] Perform set operations (union, intersection, etc.)
- [ ] Choose the right data structure for the task

---

**Previous Module**: [03_Control_Flow.md](03_Control_Flow.md)
**Next Module**: [05_Functions.md](05_Functions.md) - Writing reusable code
