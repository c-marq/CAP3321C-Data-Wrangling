# Python Basics Quick Reference

Essential Python syntax for data analysis beginners.

---

## Variables and Data Types

```python
# Variables (no declaration needed)
name = "Carlos"           # String
age = 35                  # Integer
price = 19.99             # Float
is_student = True         # Boolean

# Check type
type(name)                # <class 'str'>
```

---

## Strings

```python
# Creating strings
text = "Hello, World!"
text = 'Hello, World!'    # Single or double quotes

# String operations
text.lower()              # "hello, world!"
text.upper()              # "HELLO, WORLD!"
text.strip()              # Remove whitespace
text.replace("Hello", "Hi")  # "Hi, World!"
text.split(",")           # ["Hello", " World!"]

# f-strings (formatted strings)
name = "Carlos"
f"Hello, {name}!"         # "Hello, Carlos!"
```

---

## Lists

```python
# Creating lists
fruits = ["apple", "banana", "cherry"]
numbers = [1, 2, 3, 4, 5]
mixed = [1, "two", 3.0, True]

# Accessing elements (0-indexed)
fruits[0]                 # "apple"
fruits[-1]                # "cherry" (last item)
fruits[1:3]               # ["banana", "cherry"] (slice)

# List operations
fruits.append("orange")   # Add to end
fruits.insert(0, "mango") # Add at position
fruits.remove("banana")   # Remove by value
len(fruits)               # Length of list
```

---

## Dictionaries

```python
# Creating dictionaries
person = {
    "name": "Carlos",
    "age": 35,
    "city": "Miami"
}

# Accessing values
person["name"]            # "Carlos"
person.get("name")        # "Carlos" (safer)
person.get("email", "N/A")  # Returns "N/A" if key missing

# Dictionary operations
person["email"] = "carlos@email.com"  # Add/update
person.keys()             # All keys
person.values()           # All values
person.items()            # Key-value pairs
```

---

## Conditionals

```python
# if-elif-else
age = 25

if age < 18:
    print("Minor")
elif age < 65:
    print("Adult")
else:
    print("Senior")

# Comparison operators
x == y    # Equal
x != y    # Not equal
x > y     # Greater than
x < y     # Less than
x >= y    # Greater than or equal
x <= y    # Less than or equal

# Logical operators
x and y   # Both true
x or y    # At least one true
not x     # Opposite
```

---

## Loops

```python
# For loop (iterate over items)
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# For loop with range
for i in range(5):        # 0, 1, 2, 3, 4
    print(i)

for i in range(2, 5):     # 2, 3, 4
    print(i)

# While loop
count = 0
while count < 5:
    print(count)
    count += 1
```

---

## Functions

```python
# Defining functions
def greet(name):
    return f"Hello, {name}!"

# Calling functions
message = greet("Carlos")   # "Hello, Carlos!"

# Default parameters
def greet(name="World"):
    return f"Hello, {name}!"

greet()                   # "Hello, World!"
greet("Carlos")           # "Hello, Carlos!"

# Lambda functions (anonymous)
double = lambda x: x * 2
double(5)                 # 10
```

---

## Importing Modules

```python
# Import entire module
import pandas
df = pandas.DataFrame()

# Import with alias (common practice)
import pandas as pd
df = pd.DataFrame()

# Import specific functions
from math import sqrt, pi
result = sqrt(16)         # 4.0
```

---

## List Comprehensions

```python
# Basic list comprehension
squares = [x**2 for x in range(5)]
# [0, 1, 4, 9, 16]

# With condition
evens = [x for x in range(10) if x % 2 == 0]
# [0, 2, 4, 6, 8]
```

---

## Common Built-in Functions

| Function | Description | Example |
|----------|-------------|---------|
| `len()` | Length | `len([1,2,3])` → 3 |
| `sum()` | Sum of items | `sum([1,2,3])` → 6 |
| `min()` | Minimum | `min([1,2,3])` → 1 |
| `max()` | Maximum | `max([1,2,3])` → 3 |
| `sorted()` | Sort items | `sorted([3,1,2])` → [1,2,3] |
| `round()` | Round number | `round(3.7)` → 4 |
| `abs()` | Absolute value | `abs(-5)` → 5 |
| `type()` | Check type | `type(5)` → int |
| `print()` | Display output | `print("Hi")` |

---

## Common Errors

| Error | Meaning | Fix |
|-------|---------|-----|
| `SyntaxError` | Typo in code | Check spelling, colons, parentheses |
| `NameError` | Variable not defined | Define variable first or check spelling |
| `TypeError` | Wrong data type | Convert types (e.g., `str()`, `int()`) |
| `IndexError` | Index out of range | Check list length |
| `KeyError` | Dictionary key not found | Use `.get()` method |

---

[← Back to Resources](../README.md)
