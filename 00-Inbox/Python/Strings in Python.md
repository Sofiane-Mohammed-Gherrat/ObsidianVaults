---
From: youtube
created: 2025-08-10
tags:
  - fleeting
  - inbox
source: https://www.youtube.com/watch?v=bnSYeYFRCaA
---
---
## Cheatsheet: All 47 String Methods
	
```python
# Case Conversion Methods
capitalize()     # Capitalizes first character, lowers rest.
casefold()       # Aggressive lowercase for caseless comparison.
lower()          # Converts all characters to lowercase.
upper()          # Converts all characters to uppercase.
title()          # Title-cases the string.
swapcase()       # Swaps casing of all characters.

# Searching & Inspection Methods
find(sub)        # Finds first index of sub; –1 if not found.
rfind(sub)       # Finds last index of sub; –1 if not found.
index(sub)       # Like find(), but errors if not found.
rindex(sub)      # Like rfind(), but errors if not found.
startswith(pref) # Checks if string starts with prefix pref.
endswith(suf)    # Checks if string ends with suffix suf.

# Testing Methods
isalnum()        # Letters or digits only?
isalpha()        # Letters only?
isascii()        # ASCII characters only?
isdecimal()      # Decimal digits only?
isdigit()        # Digits (incl. superscripts)?
isnumeric()      # Numeric (incl. fractions etc.)?
isidentifier()   # Valid Python identifier?
islower()        # All cased characters lowercase?
isupper()        # All cased characters uppercase?
istitle()        # Title-cased string?
isspace()        # Only whitespace?
isprintable()    # All characters printable?

# Trimming & Padding Methods
strip(chars)     # Strips leading/trailing chars (default whitespace).
lstrip(chars)    # Removes leading chars.
rstrip(chars)    # Removes trailing chars.
ljust(w, f)      # Left-justifies text in width w, filled with f.
rjust(w, f)      # Right-justifies text in width w, filled with f.
center(w, f)     # Centers text in width w, padded with f.
zfill(width)     # Pads numeric string on the left with zeros.

# Replacement & Partitioning Methods
replace(o, n, c) # Replaces old o with new n, up to c times.
partition(sep)   # Splits at first sep into (head, sep, tail).
rpartition(sep)  # Splits at last sep.
split(sep, m)    # [Not in list but common—could be here if needed]

# Splitting & Joining Methods
splitlines(k)    # Splits at line breaks; keep breaks if k=True.
expandtabs(ts)   # Replaces tabs with ts spaces.
join(iter)       # Joins iterable of strings using this string as separator.

# Mapping & Formatting Methods
format(*a, **k)  # Formats using {} placeholders.
format_map(m)    # Formats using a mapping (e.g., dict).
maketrans()      # Creates character translation mapping.
translate(tab)   # Replaces characters based on translation mapping.

# Encoding Method
encode(enc, err) # Encodes to bytes using encoding enc and error policy.
```

---
## Accessing a String:

![[frame_3086.webp]]
source: https://www.geeksforgeeks.org/python/python-string/

## 1. Detailed Points Covered 

**47 built-in methods of Python strings** (excluding dunder methods) :

1. **`capitalize()`** – Capitalizes the first character.

```python
"hello".capitalize()  # "Hello"
```

2. **`casefold()`** – For caseless string comparison.

```python
"MaRiO".casefold() == "mario".casefold()
```

3. **`center(width, fillchar)`** – Centers text.

```python
"text".center(10, "-")
```

4. **`count(sub)`** – Counts occurrences.

```python
"AB_AB_AB".count("AB")  # 3
```

5. **`encode(encoding, errors)`** – Returns a bytes representation.

```python
"Elon Musk".encode("utf-8")
```

6. **`endswith(suffix)`** – Checks if string ends with suffix.

```python
"Apple".endswith(("e", "a"))  # True
```

7. **`expandtabs(tabsize)`** – Replaces `\t` with spaces.

```python
"a\tb".expandtabs(4)
```

8. **`find(sub)`** – Finds first index of substring or -1.

```python
"subscribe".find("sub")  # e.g., 24
```

9. **`format()`** – Inserts values using `{}` placeholders.

```python
"{} is {}".format("cat", "meow")
```

10. **`format_map(map)`** – Uses a dictionary to substitute values.

```python
"{x}, {y}".format_map({"x": 10, "y": -5})
```

11. **`index(sub)`** – Like `find()` but raises an error if not found.

12. **`isalnum()`** – Checks if string is alphanumeric.

13. **`isalpha()`** – Checks if string contains only letters.

14. **`isascii()`** – True if all characters are ASCII.


15–17. **`isdecimal()`, `isdigit()`, `isnumeric()`** – Various numeric checks:  
- `isdecimal()`: strict decimal,  
- `isdigit()`: includes digits like circled numbers,  
- `isnumeric()`: broader, includes numeric characters.

18. **`isidentifier()`** – Valid Python variable identifier.

19. **`islower()`** – True if all letters are lowercase.

20. **`isprintable()`** – True if string contains only printable characters.

21. **`isspace()`** – True if string is all whitespace.

22. **`istitle()`** – Checks if string is title-cased.

23. **`isupper()`** – Checks if all letters are uppercase.

24. **`join(iterable)`** – Joins strings from an iterable with a separator.

```python
"-".join(["text1", "text2", "text3"])
```

25. **`ljust(width, fillchar)`** – Left-justifies text.

26. **`lower()`** – Converts to lowercase.

27. **`lstrip(chars)`** – Removes characters from the left.


28–29. **`maketrans()` & `translate()`** – Used together to replace characters via translation mapping.

30. **`partition(sep)`** – Splits string into a tuple of three parts at first occurrence:

```python
"a=b=c".partition("=")  # ("a", "=", "b=c")
```

31. **`removeprefix(prefix)`** – Removes a starting prefix.

32. **`removesuffix(suffix)`** – Removes an ending suffix.

33. **`replace(old, new, count)`** – Replaces substrings, optionally limited by count.

34. **`rfind(sub)`** – Finds the highest index of substring or -1.

35. **`rindex(sub)`** – Like `rfind`, but errors if not found.

36. **`rjust(width, fillchar)`** – Right-justifies text.

37. **`rpartition(sep)`** – Partition starting from the right.

38. **`rsplit(sep, maxsplit)`** – Splits from the right with an optional max number of splits.

39. **`rstrip(chars)`** – Strips characters from the right.

40. **`splitlines(keepends)`** – Splits string at line breaks, optionally keeping newline characters.

41. **`startswith(prefix)`** – Checks if string starts with a prefix.

42. **`strip(chars)`** – Removes characters from both ends.

43. **`swapcase()`** – Swaps case of all letters.

44. **`title()`** – Converts to title case (capitalizes first letter of each word).

45. **`upper()`** – Converts to uppercase.

46. **`zfill(width)`** – Left-pads the string with zeros to reach the given width.


---

## Summary Table

| Category                   | Method(s)                                                                                                                                                               |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Case Conversion            | `capitalize()`, `casefold()`, `lower()`, `upper()`, `title()`, `swapcase()`                                                                                             |
| Searching & Inspection     | `find(sub)`, `rfind(sub)`, `index(sub)`, `rindex(sub)`, `startswith(pref)`, `endswith(suf)`                                                                             |
| Testing                    | `isalnum()`, `isalpha()`, `isascii()`, `isdecimal()`, `isdigit()`, `isnumeric()`, `isidentifier()`, `islower()`, `isupper()`, `istitle()`, `isspace()`, `isprintable()` |
| Trimming & Padding         | `strip(chars)`, `lstrip(chars)`, `rstrip(chars)`, `ljust(w, f)`, `rjust(w, f)`, `center(w, f)`, `zfill(width)`                                                          |
| Replacement & Partitioning | `replace(o, n, c)`, `partition(sep)`, `rpartition(sep)`, `split(sep, m)`                                                                                                |
| Splitting & Joining        | `splitlines(k)`, `expandtabs(ts)`, `join(iter)`                                                                                                                         |
| Mapping & Formatting       | `format(*a, **k)`, `format_map(m)`, `maketrans()`, `translate(tab)`                                                                                                     |
| Encoding                   | `encode(enc, err)`                                                                                                                                                      |

---
---

## Summary Table

| Category                         | Method(s) / Function(s)                                                                                                                     |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Case & Letter-Style Conversion   | `upper()`, `lower()`, `title()`, `capitalize()`, `swapcase()`, `casefold()`                                                                 |
| Stripping / Padding / Justifying | `strip()`, `lstrip()`, `rstrip()`, `zfill()`, `center()`, `ljust()`, `rjust()`, `expandtabs()`                                              |
| Searching / Finding Substrings   | `find()`, `rfind()`, `index()`, `rindex()`, `count()`, `startswith()`, `endswith()`                                                         |
| Splitting & Partitioning         | `split()`, `rsplit()`, `splitlines()`, `partition()`, `rpartition()`                                                                        |
| Replacing & Translating          | `replace()`, `translate()`, `maketrans()`                                                                                                   |
| Validation / Testing Properties  | `isalpha()`, `isdigit()`, `isnumeric()`, `isspace()`, `islower()`, `isupper()`, `istitle()`, `isidentifier()`, `isprintable()`, `isascii()` |
| Encoding / Bytes Conversion      | `encode(enc, err)`                                                                                                                          |
| Miscellaneous / Other Utilities  | `removeprefix()`, `removesuffix()`, method chaining                                                                                         |

---

## Cheatsheet for `str` Methods & Operations

Here’s a categorized quick‐reference cheat sheet. It shows what each group of methods is good for, with syntax hints and common usage.

---

### Case & Letter‐Style Conversion

- **Purpose:** Change the capitalization or case pattern of strings.
    
- **Common Methods:**
    
    - `upper()` – convert all letters to uppercase
        
    - `lower()` – convert all letters to lowercase
        
    - `title()` – capitalize first letter of each word
        
    - `capitalize()` – uppercase first character, lowercase the rest
        
    - `swapcase()` – swap uppercase ↔ lowercase
        
    - `casefold()` – for caseless matching (more aggressive lowercasing) ([Python 3](https://python3.pl/basics/type-string/methods.html?utm_source=chatgpt.com "5.4. String Methods — Python - from None to AI"))
        

---

### Stripping / Padding / Justifying

- **Purpose:** Remove whitespace or other characters from ends; pad or align strings in fixed widths.
    
- **Common Methods:**
    
    - `strip([chars])`, `lstrip([chars])`, `rstrip([chars])` – strip whitespace or given set of chars from both / left / right ends ([Python 3](https://python3.pl/basics/type-string/methods.html?utm_source=chatgpt.com "5.4. String Methods — Python - from None to AI"))
        
    - `zfill(width)` – pad with `'0'`s on the left to reach a given width ([W3Schools](https://www.w3schools.com/python/python_ref_string.asp?utm_source=chatgpt.com "Python String Methods"))
        
    - `center(width[, fillchar])`, `ljust(width[, fillchar])`, `rjust(width[, fillchar])` – align text in given width, padding with spaces (or other fill character) ([New Mexico Tech Computer Science](https://www.cs.nmt.edu/~jeffery/Shipman/www/docs/tcc/help/pubs/lang/pytut27/web/str-methods.html?utm_source=chatgpt.com "3.3. String methods"))
        
    - `expandtabs(tabsize=8)` – replace `\t` with spaces ([Dive into Python](https://diveintopython.org/functions/string-methods?utm_source=chatgpt.com "String Methods in Python - Python Language Reference"))
        

---

### Searching / Finding Substrings

- **Purpose:** Locate substrings, check presence, count occurrences.
    
- **Common Methods:**
    
    - `find(sub[, start[, end]])` – first occurrence, returns −1 if not found ([Pynerds](https://www.pynerds.com/python-string-methods/?utm_source=chatgpt.com "Python String Methods"))
        
    - `index(...)` – like find, but raises `ValueError` if not present ([Pynerds](https://www.pynerds.com/python-string-methods/?utm_source=chatgpt.com "Python String Methods"))
        
    - `rfind(...)`, `rindex(...)` – search from the right end ([Pynerds](https://www.pynerds.com/python-string-methods/?utm_source=chatgpt.com "Python String Methods"))
        
    - `count(sub[, start[, end]])` – number of non-overlapping occurrences ([Pynerds](https://www.pynerds.com/python-string-methods/?utm_source=chatgpt.com "Python String Methods"))
        
    - `startswith(prefix[, start[, end]])`, `endswith(suffix[, start[, end]])` – boolean tests of beginning or end of string ([Pynerds](https://www.pynerds.com/python-string-methods/?utm_source=chatgpt.com "Python String Methods"))
        

---

### Splitting & Partitioning

- **Purpose:** Break a string into parts / lines based on delimiters.
    
- **Common Methods:**
    
    - `split(sep=None, maxsplit=-1)` – split on separator (default whitespace) ([Pynerds](https://www.pynerds.com/python-string-methods/?utm_source=chatgpt.com "Python String Methods"))
        
    - `rsplit(sep=None, maxsplit=-1)` – from right side ([Pynerds](https://www.pynerds.com/python-string-methods/?utm_source=chatgpt.com "Python String Methods"))
        
    - `splitlines([keepends])` – split at line breaks with optional keeping line breaks ([Pynerds](https://www.pynerds.com/python-string-methods/?utm_source=chatgpt.com "Python String Methods"))
        
    - `partition(sep)` / `rpartition(sep)` – split into (head, sep, tail) at the first / last occurrence of separator ([Pynerds](https://www.pynerds.com/python-string-methods/?utm_source=chatgpt.com "Python String Methods"))
        

---

### Replacing & Translating

- **Purpose:** Modify content of strings by replacing substrings, mapping characters.
    
- **Common Methods:**
    
    - `replace(old, new[, count])` – replace occurrences of `old` with `new`, optionally up to `count` times ([Pynerds](https://www.pynerds.com/python-string-methods/?utm_source=chatgpt.com "Python String Methods"))
        
    - `translate(table)` with `maketrans(...)` – map individual characters to other characters or remove them ([DevTut](https://devtut.github.io/python/string-methods.html?utm_source=chatgpt.com "Python - String Methods"))
        

---

### Validation / Testing Properties

- **Purpose:** Test characteristics of a string, returning `True` or `False`.
    
- **Common Methods:**
    
    - `isalpha()`, `isdigit()`, `isnumeric()`, `isspace()` – check all (or some) characters for being alphabetic / digit / numeric / whitespace ([Pynerds](https://www.pynerds.com/python-string-methods/?utm_source=chatgpt.com "Python String Methods"))
        
    - `islower()`, `isupper()`, `istitle()` – check casing patterns ([Pynerds](https://www.pynerds.com/python-string-methods/?utm_source=chatgpt.com "Python String Methods"))
        
    - `isidentifier()` – valid Python identifier ([Pynerds](https://www.pynerds.com/python-string-methods/?utm_source=chatgpt.com "Python String Methods"))
        
    - `isprintable()`, `isascii()` – whether all characters printable / ASCII ([Dive into Python](https://diveintopython.org/functions/string-methods?utm_source=chatgpt.com "String Methods in Python - Python Language Reference"))
        

---

### Encoding / Bytes Conversion

- **Purpose:** Convert text to bytes, specify encoding.
    
- **Common Methods:**
    
    - `encode(encoding='utf-8', errors='strict')` – return `bytes` representation of string in given encoding ([Codecademy](https://www.codecademy.com/resources/docs/python/strings?utm_source=chatgpt.com "Python | Strings | Codecademy"))
        

---

### Miscellaneous / Other Utilities

- **Purpose:** Other helpful operations not fitting above neatly.
    
- **Common Methods:**
    
    - `removeprefix(prefix)`, `removesuffix(suffix)` – remove a starting or ending substring (new in Python 3.9) ([Python3.info](https://python3.info/basics/type-string/methods.html?utm_source=chatgpt.com "5.5. String Methods — Python - from None to AI"))
        
    - Method chaining – combining multiple methods in one expression, e.g. `s.strip().lower().replace(...)` ([Python3.info](https://python3.info/basics/type-string/methods.html?utm_source=chatgpt.com "5.5. String Methods — Python - from None to AI"))
        

---

## Syntax & Examples by Category

Here are the general syntax templates for each category, followed by multiple examples in code blocks.

---

### Case & Letter‐Style Conversion

**Syntax:**

```python
s.upper()
s.lower()
s.title()
s.capitalize()
s.swapcase()
s.casefold()
```

**Examples:**

```python
s = "hello WORLD"

print(s.upper())       # "HELLO WORLD"
print(s.lower())       # "hello world"
print(s.title())       # "Hello World"
print(s.capitalize())  # "Hello world"
print(s.swapcase())    # "HELLO world"
print(s.casefold())    # "hello world"  (more aggressive for caseless matching)
```

---

### Stripping / Padding / Justifying

**Syntax:**

```python
s.strip([chars])
s.lstrip([chars])
s.rstrip([chars])
s.zfill(width)
s.center(width[, fillchar])
s.ljust(width[, fillchar])
s.rjust(width[, fillchar])
s.expandtabs(tabsize=8)
```

**Examples:**

```python
s = "  Hello\t\n"
print(s.strip())       # "Hello"
print(s.lstrip())      # "Hello\t\n"
print(s.rstrip())      # "  Hello"

print("42".zfill(5))    # "00042"

print("cat".center(7))           # "  cat  "
print("cat".center(7, "*"))      # "**cat**"
print("dog".ljust(5))            # "dog  "
print("dog".rjust(5))            # "  dog"

print("1\t2\t3".expandtabs(4))   # "1   2   3"   (tabs expanded to spaces)
```

---

### Searching / Finding Substrings

**Syntax:**

```python
s.find(sub[, start[, end]])
s.rfind(sub[, start[, end]])
s.index(sub[, start[, end]])
s.rindex(sub[, start[, end]])
s.count(sub[, start[, end]])
s.startswith(prefix[, start[, end])
s.endswith(suffix[, start[, end])
```

**Examples:**

```python
s = "abracadabra"

print(s.find("bra"))           # 1
print(s.find("bra", 2))        # 8
print(s.rfind("bra"))          # 8

print(s.index("a"))            # 0
# print(s.index("z"))          # ValueError

print(s.count("a"))            # 5
print(s.count("abra"))         # 2

print(s.startswith("abra"))    # True
print(s.startswith("bra"))     # False
print(s.endswith("bra"))       # True
print(s.endswith("dab"))       # False
```

---

### Splitting & Partitioning

**Syntax:**

```python
s.split(sep=None, maxsplit=-1)
s.rsplit(sep=None, maxsplit=-1)
s.splitlines([keepends=False])
s.partition(sep)
s.rpartition(sep)
```

**Examples:**

```python
s = "one two three   four"

print(s.split())               # ["one", "two", "three", "four"]
print(s.split(" ", 2))         # ["one", "two", "three   four"]

print(s.rsplit(" ", 2))        # ["one two", "three", "four"]

multilines = "Line1\nLine2\nLine3"
print(multilines.splitlines())        # ["Line1", "Line2", "Line3"]
print(multilines.splitlines(True))    # ["Line1\n", "Line2\n", "Line3"]

s2 = "key:value:detail"
print(s2.partition(":"))       # ("key", ":", "value:detail")
print(s2.rpartition(":"))      # ("key:value", ":", "detail")
```

---

### Replacing & Translating

**Syntax:**

```python
s.replace(old, new[, count])
table = s.maketrans(dict_or_fromto)
s.translate(table)
```

**Examples:**

```python
s = "banana"

print(s.replace("a", "o"))         # "bonono"
print(s.replace("na", "NA", 1))    # "baNAna"

tbl = str.maketrans("abc", "123")
print("abcabc".translate(tbl))     # "123123"

# Removing certain characters via translate
tbl2 = str.maketrans("", "", "aeiou")
print("beautiful".translate(tbl2)) # "btfl"
```

---

### Validation / Testing Properties

**Syntax:**

```python
s.isalpha()
s.isdigit()
s.isnumeric()
s.isspace()
s.islower()
s.isupper()
s.istitle()
s.isidentifier()
s.isprintable()
s.isascii()
```

**Examples:**

```python
print("Hello".isalpha())         # True
print("Hello123".isalpha())      # False

print("123".isdigit())           # True
print("½".isnumeric())           # True  # numeric includes some unicode

print("   \t\n".isspace())        # True
print("abc".islower())            # True
print("ABC".isupper())            # True
print("Title Case String".istitle())  # True

print("variable_name".isidentifier())  # True
print("123abc".isidentifier())          # False

print("Line feed:\n".isprintable())    # False
print("Normal text".isascii())         # True
```

---

### Encoding / Bytes Conversion

**Syntax:**

```python
s.encode(encoding='utf-8', errors='strict')
```

**Examples:**

```python
s = "café"

b1 = s.encode()                     # b'caf\xc3\xa9'   (default utf-8)
b2 = s.encode('utf-16')             # maybe includes BOM depending on environment
b3 = s.encode('ascii', errors='ignore')  # b'caf'   accents removed via ignore
```

---

### Miscellaneous / Other Utilities

**Syntax:**

```python
s.removeprefix(prefix)
s.removesuffix(suffix)
# method chaining:
# s.method1(...).method2(...).method3(...)
```

**Examples:**

```python
filename = "report_final.txt"
print(filename.removeprefix("report_"))   # "final.txt"
print(filename.removesuffix(".txt"))      # "report_final"

# Example of chaining:
s = "   Hello_world.TXT  "
result = s.strip().lower().replace("_", " ").title()
print(result)   # "Hello World Txt"
```

