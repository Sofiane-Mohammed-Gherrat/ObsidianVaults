---
type: fleeting
created: 2025-09-21
tags: [fleeting, inbox]
---
# convert **float / int** to exponential
## example

```markdown
Input: 19.0
Output: 1.900000e+01
```

```python
float_num= 110.23
print(f)  # Output: 1101.02

exponent_num = '{:e}'.format(float_num)
print(exponent_num) # Output: 1.101020e+03
```

---
## ASCII ord() and chr()

|Operation|Python equivalent|Example|
|---|---|---|
|Get ASCII / Unicode code point (integer) from a character|`ord(char)`|`ord('A') → 65` ([GeeksforGeeks](https://www.geeksforgeeks.org/python/ord-function-python/?utm_source=chatgpt.com "ord() function in Python"))|
|Get character from an integer code / code point|`chr(num)`|`chr(65) → 'A'` ([DigitalOcean](https://www.digitalocean.com/community/tutorials/python-ord-chr?utm_source=chatgpt.com "Python ord(), chr() functions"))|

---

Some extra details:

- `ord()` 
	takes => 1 char
	**TypeError**: if more

- `chr()` takes an integer, and returns the character whose Unicode code point is that integer. The valid range is **0 through 1,114,111** (that is `0x10FFFF` in hex). If the integer is outside that range, `chr()` raises a `ValueError`. ([Programiz](https://www.programiz.com/python-programming/methods/built-in/chr?utm_source=chatgpt.com "Python chr() (With Examples) - Programiz"))
    

---

### Examples

```python
>>> ord('a')
97
>>> ord('€')
8364

>>> chr(97)
'a'
>>> chr(8364)
'€'
```

