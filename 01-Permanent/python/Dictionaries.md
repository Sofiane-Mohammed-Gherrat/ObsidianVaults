---
source: https://github.com/Asabeneh/30-Days-Of-Python/blob/master/08_Day_Dictionaries/08_dictionaries.md
created: 2025-09-15
tags:
  - inbox
---


# 📝 Python Dictionaries Cheatsheet

```python
# Dictionary Creation
{}                        # Empty dictionary literal.
dict()                    # Creates an empty dictionary.
{'k1': 'v1', 'k2': 'v2'}  # Dictionary with initial pairs.

# Length
len(dct)                  # Number of key:value pairs.

# Accessing Items
dct[key]                  # Access value by key, error if not found.
dct.get(key, default)     # Returns value if key exists, else default.
dct.setdefault(key, val)  # Returns value if key exists; inserts key:val if not.

# Adding / Modifying Items
dct[key] = value          # Add or update key:value pair.
dct.update(d2)            # Updates dictionary with another dict or iterable.

# Membership
key in dct                # True if key exists.
key not in dct            # True if key does not exist.

# Removing Items
dct.pop(key, default)     # Removes item by key, returns default if missing.
dct.popitem()             # Removes and returns last inserted key:value.
del dct[key]              # Deletes item with given key.
dct.clear()               # Removes all items.
del dct                   # Deletes dictionary itself.

# Copying
dct.copy()                # Returns a shallow copy.

# Conversions / Views
dct.items()               # All key:value pairs as dict_items.
dct.keys()                # All keys as dict_keys.
dct.values()              # All values as dict_values.
dict.fromkeys(seq, val)   # Creates new dict from seq with given default val.
```

---

## ✅ Application Examples

```python
# Dictionary Creation
person = {'name': 'Alice', 'age': 25}

# Length
len(person)                   # 2

# Accessing Items
person['name']                # 'Alice'
person.get('city', 'N/A')     # 'N/A'
person.setdefault('country', 'France')  # Adds 'country': 'France'

# Adding / Modifying Items
person['age'] = 26            # Updates existing
person.update({'job': 'Dev'}) # {'name':'Alice','age':26,'country':'France','job':'Dev'}

# Membership
'name' in person              # True
'city' not in person          # True

# Removing Items
person.pop('job', 'No job')   # Removes 'job'
person.popitem()              # Removes last inserted pair
del person['age']             # Deletes 'age'
person.clear()                # {}

# Copying
d1 = {'a': 1, 'b': 2}
d2 = d1.copy()
d2['a'] = 99                  # d1 unaffected

# Conversions / Views
d = {'x': 10, 'y': 20}
list(d.items())               # [('x', 10), ('y', 20)]
list(d.keys())                # ['x', 'y']
list(d.values())              # [10, 20]
dict.fromkeys(['a','b'], 0)   # {'a': 0, 'b': 0}
```
