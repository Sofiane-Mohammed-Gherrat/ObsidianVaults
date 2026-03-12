---
type: fleeting
created: 2025-09-19
tags: [fleeting, inbox]
---
## Summary Table

| Category                    | Method(s)                                                                                   |
| --------------------------- | ------------------------------------------------------------------------------------------- |
| Creation / Initialization   | `set(...)`, `{...}`, `frozenset(...)`                                                       |
| Membership & Size           | `len(s)`, `x in s`, `x not in s`                                                            |
| Adding Elements             | `add()`, `update()`                                                                         |
| Removing Elements           | `remove()`, `discard()`, `pop()`, `clear()`                                                 |
| Set Operations (−> new set) | `union()`, `intersection()`, `difference()`, `symmetric_difference()`                       |
| In-place / Augmented Ops    | `update()`, `intersection_update()`, `difference_update()`, `symmetric_difference_update()` |
| Comparison / Relationships  | `isdisjoint()`, `issubset()`, `issuperset()`                                                |
| Miscellaneous               | `copy()`                                                                                    |

---
## Cheatsheet for `set` Methods & Operations

### Creation & Initialization

```python
set(iterable)         # Creates a set from an iterable (removing duplicates).
{a, b, c, ...}        # Literal syntax for creating a set.
frozenset(iterable)   # Creates an immutable set.
```

**Examples:**

```python
s1 = set([1, 2, 2, 3])        # {1, 2, 3}
s2 = {"apple", "banana"}      # {"apple", "banana"}
fs = frozenset([1, 2, 2, 3])   # frozenset({1, 2, 3})
```

---

### Basic Properties & Membership

```python
len(s)                 # Number of elements in set.
x in s                 # True if x is an element of s.
x not in s             # True if x is not in s.
```

**Examples:**

```python
s = {1, 2, 3}
len(s)            # 3
2 in s            # True
5 not in s        # True
```

---

### Adding Elements

```python
add(elem)            # Adds one element.
update(iterable)     # Adds multiple elements from an iterable.
```

**Examples:**

```python
s = {1, 2}
s.add(3)                 # s becomes {1, 2, 3}
s.update([4, 5, 1])      # s becomes {1, 2, 3, 4, 5}  (duplicate 1 ignored)
```

---

### Removing Elements

```python
remove(elem)            # Remove elem; raises KeyError if not present.
discard(elem)           # Remove elem; no error if elem not present.
pop()                   # Remove and return an *arbitrary* element; KeyError if empty.
clear()                 # Remove all elements from set.
```

**Examples:**

```python
s = {1, 2, 3, 4}
s.remove(2)           # s -> {1, 3, 4}
s.discard(5)          # no error; s stays {1, 3, 4}
x = s.pop()           # removes an arbitrary element, e.g. 1; s now {3, 4}
s.clear()             # s -> set()
```

---

### Set Operations (Return New Sets)

```python
union(other, ...)                 # Elements in either set.
intersection(other, ...)          # Common elements.
difference(other, ...)            # Elements in this set but not in others.
symmetric_difference(other)       # Elements in either set, but not both.
```

**Examples:**

```python
a = {1, 2, 3}
b = {2, 3, 4}
a.union(b)                # {1, 2, 3, 4}
a.intersection(b)         # {2, 3}
a.difference(b)           # {1}
a.symmetric_difference(b) # {1, 4}
```

---

### In‐place / Augmented Set Operations

```python
update(other, ...)                      # Like union; modifies the set.
intersection_update(other, ...)         # Like intersection; modifies the set.
difference_update(other, ...)           # Like difference; modifies the set.
symmetric_difference_update(other)      # Like symmetric_difference; modifies the set.
```

**Examples:**

```python
a = {1, 2, 3}
b = {2, 3, 4}
a.update(b)                       # a -> {1, 2, 3, 4}
a = {1, 2, 3}
a.intersection_update(b)          # a -> {2, 3}
a = {1, 2, 3}
a.difference_update(b)            # a -> {1}
a = {1, 2, 3}
a.symmetric_difference_update(b)  # a -> {1, 4}
```

---

### Comparison & Relationship Testing

```python
isdisjoint(other)     # True if sets have no elements in common.
issubset(other)       # True if every element in this set is in other.
issuperset(other)     # True if this set has every element in other.
```

**Examples:**

```python
a = {1, 2}
b = {1, 2, 3}
c = {3, 4}
a.isdisjoint(c)       # True (no overlap)
a.issubset(b)          # True (1,2 both in b)
b.issuperset(a)        # True
```

---

### Miscellaneous Methods

```python
copy()                 # Returns a shallow copy of the set.
```

**Example:**

```python
s = {1, 2, 3}
t = s.copy()           # t -> {1, 2, 3}, separate object from s
```

