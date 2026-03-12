---
source: https://github.com/Asabeneh/30-Days-Of-Python/blob/master/06_Day_Tuples/06_tuples.md?plain=1
created: 2025-09-14
tags:
  - fleeting
  - inbox
---


# 📝 Python Tuples Cheatsheet

```python
# Tuple Creation
tuple()              # Creates an empty tuple.
()                   # Empty tuple literal.
('a', 'b', 'c')      # Tuple with initial values.

# Tuple Methods
count(x)             # Counts occurrences of x in tuple.
index(x)             # Returns first index of x, error if not found.

# Length Function
len(tpl)             # Returns number of items in tuple.

# Accessing Elements
tpl[i]               # Positive indexing.
tpl[-i]              # Negative indexing (from end).

# Slicing
tpl[start:end]       # Sub-tuple from start to end-1.
tpl[start:]          # From start to end.
tpl[:end]            # From beginning to end-1.
tpl[-n:]             # Last n items.

# Conversion
list(tpl)            # Convert tuple → list (mutable).
tuple(lst)           # Convert list → tuple (immutable).

# Membership
x in tpl             # True if x exists in tuple.
x not in tpl         # True if x does not exist in tuple.

# Joining Tuples
tpl1 + tpl2          # Concatenates tuples into new one.

# Deletion
del tpl              # Deletes entire tuple (not individual items).

```

## ✅ Application Examples

```python
# Tuple Creation
empty = tuple()                         # ()
fruits = ('banana', 'orange', 'mango')  # ('banana', 'orange', 'mango')

# Tuple Methods
fruits.count('orange')   # 1
fruits.index('mango')    # 2

# Length
len(fruits)              # 3

# Accessing Elements
fruits[0]    # 'banana'
fruits[-1]   # 'mango'

# Slicing
fruits[0:2]   # ('banana', 'orange')
fruits[1:]    # ('orange', 'mango')
fruits[-2:]   # ('orange', 'mango')

# Conversion
lst = list(fruits)       # ['banana', 'orange', 'mango']
lst[0] = 'apple'
fruits = tuple(lst)      # ('apple', 'orange', 'mango')

# Membership
'banana' in fruits       # True
'pear' not in fruits     # True

# Joining Tuples
vegetables = ('carrot', 'onion')
food = fruits + vegetables  # ('apple', 'orange', 'mango', 'carrot', 'onion')

# Deletion
tpl = (1, 2, 3)
del tpl
# tpl is now undefined

```
