**type**: fleeting
created: 2025-08-06 08:31
tags: #fleeting #to‑process
project: 
source: https://www.youtube.com/watch?v=wfL4o73swZI

---

# All Python Concept Explained

Here’s a complete walkthrough of _every_ Python concept from the video, each clearly explained with accompanying code snippets and verified references:

---

## 2. **`if __name__ == "__main__"` idiom**

Used to ensure certain code only executes when the file is run directly—not when imported. When executed directly, `__name__` is `"__main__"`; when imported, it's the module’s name.

```python
def main():
    print("Running as script")

if __name__ == "__main__":
    main()  # only runs when script is executed directly
```

---

## 3. **Everything Is an Object**

Python treats **all entities**—data types, functions, classes, modules, even code blocks—as objects with attributes and methods. This uniform model offers flexibility but can lead to higher memory usage.

---

## 6. **List Comprehensions**

Compact one-line syntax for building lists from sequences with optional filtering or nested loops.

```python
squares = [x*x for x in range(10) if x % 2 == 0]
```

---

## 7. **Multiple Assignment & Tuple Unpacking**

Assign multiple variables in one go—Python interprets right-hand values as a tuple.

```python
a, b, c = 1, 2, 3
```

---

## 11. **Dunder (Magic) Methods**

Special double-underscore methods like `__init__`, `__add__`, `__str__` implement built-in behaviors (initialization, operator overloading, string conversion) ([Python documentation](https://docs.python.org/3/tutorial/controlflow.html?utm_source=chatgpt.com "4. More Control Flow Tools — Python 3.13.5 documentation")).

```python
class Vector:
    def __init__(self, x, y):
        self.x, self.y = x, y
    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)
    def __str__(self):
        return f"Vector({self.x}, {self.y})"
```

---

## 12. **`*args` and `**kwargs`**

Let functions accept arbitrary numbers of positional (`*args`) and keyword (`**kwargs`) arguments.

```python
def f(*args, **kwargs):
    print(args, kwargs)

f(1, 2, a=3, b=4)
```

---

## 13. **Walrus Operator (`:=`)**

Introduced in Python 3.8, it enables assignment within an expression—helpful in loops or conditionals ([GeeksforGeeks](https://www.geeksforgeeks.org/python/walrus-operator-in-python-3-8/?utm_source=chatgpt.com "Walrus Operator in Python 3.8")).

```python
if (n := len([1,2,3])) > 2:
    print(n)
```

---

## 14. **Decorators**

Functions that wrap other functions or classes to extend behavior without modifying them. Common for timing, validation, caching.

```python
def decorator(fn):
    def wrapper(*args, **kwargs):
        print("Before")
        res = fn(*args, **kwargs)
        print("After")
        return res
    return wrapper

@decorator
def say_hi():
    print("Hi")
```

---

## 15. **Context Managers (`with` statement)**

Automate resource setup and cleanup with objects implementing `__enter__()` and `__exit__()`. Used for files, network connections, etc. ([GeeksforGeeks](https://www.geeksforgeeks.org/python/context-manager-in-python/?utm_source=chatgpt.com "Context Manager in Python")).

```python
with open("file.txt") as f:
    data = f.read()
# file auto-closed afterward
```

---

## 16. **`__slots__` Optimization**

Restricts allowable instance attributes, eliminating per-instance `__dict__` and reducing memory—but disallows dynamic attributes ([pythonmorsels.com](https://www.pythonmorsels.com/creating-a-context-manager/?utm_source=chatgpt.com "Creating a context manager in Python"), [pravash-techie.medium.com](https://pravash-techie.medium.com/python-context-manager-to-simplify-resource-handling-5959a36a0f58?utm_source=chatgpt.com "Python: Context Manager to Simplify Resource Handling")).

```python
class Point:
    __slots__ = ("x", "y")
    def __init__(self, x, y):
        self.x, self.y = x, y
```

---

## 17. **`else:` in `try/except` Blocks**

If no exception occurs in the `try` block, the `else:` block runs. This keeps handling of the success path separate from `except` logic ([Python documentation](https://docs.python.org/3/tutorial/errors.html?utm_source=chatgpt.com "8. Errors and Exceptions — Python 3.13.5 documentation"), [GeeksforGeeks](https://www.geeksforgeeks.org/python/try-except-else-and-finally-in-python/?utm_source=chatgpt.com "Try, Except, else and Finally in Python")).

```python
try:
    result = do_something()
except ValueError:
    handle_error()
else:
    process_success(result)
```

---

## 18. **Mutable Default Arguments**

Using mutable objects (like a list or dict) as a default argument means the same object is reused across calls—causing unexpected behavior.

```python
def f(a, l=[]):
    l.append(a)
    return l

print(f(1))  # [1]
print(f(2))  # [1,2]  # same list used
```

Workaround:

```python
def f(a, l=None):
    if l is None:
        l = []
    l.append(a)
    return l
```

---

## 19. **Global Interpreter Lock (GIL)**

A mutex in CPython that ensures only one thread executes Python bytecode at a time. It simplifies internal memory safety but limits parallelism in CPU-bound multi-threaded programs.

