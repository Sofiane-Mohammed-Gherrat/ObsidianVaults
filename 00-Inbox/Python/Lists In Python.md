---
From: youtube
created: 2025-08-10
tags:
  - fleeting
  - inbox
source: https://www.youtube.com/watch?v=0yySumZTxJ0&t=159s
---

---

## **1. Detailed Points from the Video**

### **Intro**

- The video covers **11 built-in Python list methods** (not dunder methods like `__len__` or `__getitem__`).
- These methods are accessed via dot notation, e.g. `mylist.method()`.

---
## **Python List Methods Cheatsheet**

```python
# 1. Append item
L.append(item)

# 2. Clear all items
L.clear()

# 3. Copy (shallow)
Cp_L = L.copy()

# 4. Count occurrences
L.count(value)

# 5. Extend with another iterable
L.extend(iterable)

# 6. Get index of item
L.index(value)

# 7. Insert at position
L.insert(pos, value)

# 8. Pop item at index (default: last)
L.pop([index])

# 9. Remove first occurrence
L.remove(value)

# 10. Reverse in place
L.reverse()

# 11. Sort list
L.sort(key=None, reverse=False)
```

---
### **1. `append()`**

- **Purpose**: Adds a single element to the end of the list.
- **Syntax**: `list.append(element)`
- **Example**:

```python
people = ["Mario", "Trump", "Elon"]
people.append("Luigi")
print(people)  
# ['Mario', 'Trump', 'Elon', 'Luigi']
```

---

### **2. `clear()`**

- **Purpose**: Removes all elements from the list, leaving it empty.
- **Syntax**: `list.clear()`
- **Example**:

```python
people.clear()
print(people)  # []
```

---

### **3. `copy()`**

- **Purpose**: Returns a shallow copy of the list (1D safe, but nested lists still reference the same objects).
- **Syntax**: `list.copy()`
- **Example**:

```python
people = ["Mario", "Trump", "Elon"]
copy_people = people.copy()
copy_people.remove("Trump")
print(people)       # ['Mario', 'Trump', 'Elon']
print(copy_people)  # ['Mario', 'Elon']
```

⚠️ With nested lists:

```python
people = ["Mario", ["Elon", "Bob"]]
copy_people = people.copy()
copy_people[1][1] = "Cat"
print(people)       # ['Mario', ['Elon', 'Cat']]  <-- changed in both
```

---

### **4. `count()`**

- **Purpose**: Counts how many times a specific value appears in the list.
- **Syntax**: `list.count(value)`
- **Example**:

```python
people = ["Mario", "Elon", "Elon"]
print(people.count("Elon"))  # 2
print(people.count("Apple")) # 0
```

---

### **5. `extend()`**

- **Purpose**: Appends all elements from another iterable to the end of the list.
- **Syntax**: `list.extend(iterable)`
- **Example**:

```python
people = ["Mario", "Elon"]
more_people = ["Apple", "Banana"]
people.extend(more_people)
print(people)  
# ['Mario', 'Elon', 'Apple', 'Banana']
```

---

### **6. `index()`**

- **Purpose**: Returns the index of the first occurrence of a value.
- **Syntax**: `list.index(value)`
- **Example**:

```python
people = ["Mario", "Trump", "Elon"]
print(people.index("Trump"))  # 1
```

⚠️ If the element doesn’t exist → `ValueError`.

---

### **7. `insert()`**

- **Purpose**: Inserts an element at a specific index.
- **Syntax**: `list.insert(position, value)`
- **Example**:

```python
people = ["Mario", "Trump"]
people.insert(1, "Luigi")
print(people)  
# ['Mario', 'Luigi', 'Trump']
```

If index > length → appends at end.  
If index is negative and too small → inserts at start.

---

### **8. `pop()`**

- **Purpose**: Removes and returns the element at a given index (default: last item).
- **Syntax**: `list.pop([index])`
- **Example**:

```python
people = ["Mario", "Trump", "Elon"]
last = people.pop()
print(last)     # Elon
print(people)   # ['Mario', 'Trump']
```

---

### **9. `remove()`**

- **Purpose**: Removes the first occurrence of a specific value (no return value).
- **Syntax**: `list.remove(value)`
- **Example**:

```python
people = ["Mario", "Elon"]
people.remove("Elon")
print(people)  # ['Mario']
```

⚠️ Raises `ValueError` if not found.

---

### **10. `reverse()`**

- **Purpose**: Reverses the list in place.
- **Syntax**: `list.reverse()`
- **Example**:

```python
people = ["Mario", "Elon", "Trump"]
people.reverse()
print(people)  # ['Trump', 'Elon', 'Mario']
```

---

### **11. `sort()`**

- **Purpose**: Sorts the list in place (default: ascending, alphabetical for strings).
- **Syntax**: `list.sort(key=None, reverse=False)`
- **Example**:

```python
people = ["Bob", "elon", "Mario", "trump"]
people.sort(key=str.lower)  # Case-insensitive
print(people)  # ['Bob', 'elon', 'Mario', 'trump']
```

Other custom sorting:

```python
people.sort(key=len)  # Sort by length of name
people.sort(reverse=True)  # Descending order
```


---

