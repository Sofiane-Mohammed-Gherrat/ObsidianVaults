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
## 1. Detailed Points Covered in the Video

The video walks through **47 built-in methods of Python strings** (excluding dunder methods). Here's a summary of each method explained, with short code snippets to illustrate:

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