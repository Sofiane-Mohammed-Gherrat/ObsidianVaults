Source: https://www.youtube.com/watch?v=xEZkR9BFXOI&t=132s

### Classes:
Blueprints for making the instances
### Objects:
units of Data of a particular type or class having 1 or more attributes with associated methods
### Attributes

### Methodes

---
## The Pillars Of OOP
### 1. Encapsulation:
Bundling of **attributes** and **methods** that operate on the instance in a single unit called **class** -> ensuring integrity of the data and only allowing interaction through a set of rules in the `getter`and `setter` methods.

## 2. Inheritance:
mechanism for sharing attributes between classes.

### 3. Polymorphism:
Having methods with the same name through out a number of classes but that operate differently.

```python
# a, b, c: are instances of different classes 
for ele in [a, b, c]:
	ele.get_val()
```

## Lookup Order
- instance
- class to which it belongs 
- any parent class
### check for mro
## Static / Class Methods 
```python
@staticmethod
@classmethod
```

## <mark class="hltr-mygreen2">Abstract Base Classes</mark> 

```python
import abc

class GetterSetter(object):
	__metaclass__ =	abc.ABCMeta
	
	@abc.abstractclass
	def set_val(self, value) -> None:
		"set a value in the instance"
		return
	
	@abc.abstractclass
	def get_val(self):
		"returns the value from the instance"
		return
```

```python
# below class inherits from GetterSetter
# => requires set_val() and get_vall()
# => any change in the name of the methods or absance results in error
class MyClass(GetterSetter):
	
	def set_val(self, value):
		# ....
	def get_val(self):
		# ....
```

## Breaking Encapsulation With <mark class="hltr-myblue">@property</mark> 

```python
class MyClass(Object):
	def __init__(self, value):
		self.val = value
	
	def getter(self):
		print(f'This is the value {self.val} ')
	
	@property
	def setter(self, value):
		self.val = value
```

```python
inst = MyClass()
# We can assign securely a value to val using:
inst.val = 5
```
## Note:
<mark class="hltr-mygreen-">@poroperty</mark> is considered cheap because it can mislead the user to think that that action is not doing a big thing whilst in fact it could be assigning a configuration value to maybe one of the routers in a network.


## Magic methods | Usage In Custom Classes:

```python
'abc' in var    =>   var.__contains__('abc')
var == 'abc'    =>   var.__eq__('abc')
var[1]          =>   var.__getitem__(1)
var[1:3]        =>   var.__getslice__(1, 3)
len(var)        =>   var.__len__()
print(var)      =>   var.__repr__()
```

### Attention:
We allow the usage of <mark class="hltr-myblue">Python Operators</mark> in a class by **defining the method with the name of the respective magic method** ex: `.__add__() for +` 

```python
# [1, 2, 3, 4, 5]
# [100, 200, 300, 400, 500]
# we wanna concatenate each parallel elements

class SumList(Object):
	
	def __init__(self, this_list):
		self.mylist = this_list
	
	def __add__(self, other):
		new_list = [x + y for x, y in zip(self.mylist, other.mylist)]
		return SumList(new_list) # Returning a and instance of SumList
	
	def __repr__(self):
		return str(self.mylist)


aa = SumList([1, 2, 3, 4, 5])
bb = SumList([100, 200, 300, 400, 500])
cc = aa + bb
print(cc) # [101, 202, 303, 404, 505]
```

## Note:
Checking the type ahead of time is **`unpythonic`** that's why => Polymorphism exists = to allow performing the same methods *`although behaving differently`* on different classes without caring about the `type`


## Simple analogy about Private / Protected Attributes

Think of it like this: Python’s “private” is more like locking a door but leaving the key under the mat. You don’t make it truly impossible to enter, but you make it inconvenient and signal “don’t go there unless you know what you're doing.”

If you didn’t have underscores at all, you’d have less of a signal. Everyone might treat every attribute as fair game, making it harder to maintain and evolve your classes.

---
# Improved by Qwen 

# 🧠 Object-Oriented Programming (OOP) in Python — A Practical Guide

> *“OOP is not just about classes and objects — it’s about thinking in structured, reusable, and maintainable ways.”*

---

## 📚 What is OOP?

**Object-Oriented Programming** is a programming paradigm that organizes software design around **objects** — data structures that contain both data (attributes) and behavior (methods).

### Core Concepts:

| Term             | Definition |
|------------------|------------|
| **Class**        | Blueprint for creating objects. Defines attributes and methods. |
| **Object**       | An instance of a class. Holds data and can execute methods. |
| **Attributes**   | Variables that store data associated with an object. |
| **Methods**      | Functions defined inside a class that define behavior. |

---

## 🏗️ The Three Pillars of OOP

### 1. 🔒 Encapsulation

> *“Bundling data and functions that operate on that data together.”*

- Encapsulation hides internal details and exposes only what’s necessary.
- Use **getter** and **setter** methods to control access.
- Use `@property` for a Pythonic, readable way to access attributes.

```python
class MyClass:
    def __init__(self, value):
        self._value = value  # _ indicates "private" (convention)

    @property
    def value(self):
        return self._value

    @value.setter
    def value(self, value):
        if value < 0:
            raise ValueError("Value must be non-negative")
        self._value = value
```

> 💡 **Improvement Suggestion**:  
> - Add **validation** inside setters to prevent misuse.
> - Use `@property` for read-only attributes too — e.g., `@property def name(self)`.
> - Use `__slots__` to reduce memory usage and prevent accidental attribute assignment.

---

### 2. 🔄 Inheritance

> *“Reusing code by creating new classes based on existing ones.”*

- A child class can inherit attributes and methods from a parent class.
- Use `class Child(Parent):` to define inheritance.
- **Abstract Base Classes (ABC)** enforce contract: child classes must implement required methods.

```python
import abc

class GetterSetter(metaclass=abc.ABCMeta):
    @abc.abstractmethod
    def set_val(self, value):
        pass

    @abc.abstractmethod
    def get_val(self):
        pass

class MyClass(GetterSetter):
    def set_val(self, value):
        self._value = value

    def get_val(self):
        return self._value
```

> 💡 **Improvement Suggestion**:  
> - Use `@classmethod` to create factory methods.
> - Use `@staticmethod` for utility functions that don’t need the instance.
> - Add `__init_subclass__` to enforce custom behavior in subclasses.

---

### 3. 🌀 Polymorphism

> *“Same method name, different behavior depending on the object type.”*

```python
for ele in [a, b, c]:
    ele.get_val()  # Each object responds differently
```

- Enables **flexible code** — you don’t need to know the exact type.
- Use **duck typing**: If it walks like a duck, it quacks.

> 💡 **Improvement Suggestion**:  
> - Use **type hints** to improve code clarity and IDE support.
> - Show **real-world examples** (e.g., shapes: `Circle`, `Square` — both have `area()` method, but implement differently).

---

## 🧭 Method Resolution Order (MRO)

> *“Where to look for a method? Instance → class → parent classes.”*

Use `help(ClassName)` or `ClassName.__mro__` to see the inheritance hierarchy.

```python
class A:
    def method(self):
        print("A")

class B(A):
    def method(self):
        print("B")

class C(B):
    def method(self):
        print("C")

c = C()
c.method()  # Output: C
print(C.__mro__)  # Shows inheritance chain: C -> B -> A -> object
```

> 💡 **Improvement Suggestion**:  
> - Add a **diagram or tree** to visualize MRO.
> - Use `super()` to call parent methods cleanly.

---

## 🧩 Static and Class Methods

```python
class MyClass:
    @staticmethod
    def static_method():
        # No access to instance or class state
        pass

    @classmethod
    def class_method(cls):
        # Accesses the class, not instance
        pass
```

> 💡 **Improvement Suggestion**:  
> - Use `@staticmethod` for utility functions.
> - Use `@classmethod` for factory methods (e.g., `MyClass.from_string()`).
> - Add `@property` to expose computed values.

---

## 🚫 Breaking Encapsulation With `@property`

> *“Python doesn’t have true private variables — but it’s a convention.”*

```python
class MyClass:
    def __init__(self, value):
        self._val = value

    @property
    def val(self):
        return self._val

    @val.setter
    def val(self, value):
        self._val = value
```

```python
inst = MyClass()
inst.val = 5  # ✅ Clean, readable
print(inst.val)  # ✅ Readable
```

> 💡 **Improvement Suggestion**:  
> - Use `@property` to expose computed values (e.g., `area`, `length`, etc.).
> - Use `__slots__` to prevent accidental attribute assignment.
> - Add validation or logging inside setters.

---

## 🎮 Magic Methods (Dunder Methods)

> *“Overload Python operators and built-in functions.”*

```python
class SumList:
    def __init__(self, this_list):
        self.mylist = this_list

    def __add__(self, other):
        return SumList([x + y for x, y in zip(self.mylist, other.mylist)])

    def __repr__(self):
        return str(self.mylist)

aa = SumList([1, 2, 3, 4, 5])
bb = SumList([100, 200, 300, 400, 500])
cc = aa + bb
print(cc)  # [101, 202, 303, 404, 505]
```

| Operator      | Magic Method     |
|---------------|------------------|
| `+`           | `__add__`        |
| `==`          | `__eq__`         |
| `in`          | `__contains__`   |
| `len()`       | `__len__`        |
| `print()`     | `__repr__`       |

> 💡 **Improvement Suggestion**:  
> - Add **error handling** for invalid operations (e.g., `aa + bb` if `bb` is not a `SumList`).
> - Show **real-world examples** (e.g., `Vector`, `Point`, `Time`).
> - Use `__str__` for human-readable output, `__repr__` for developers.

---

## 🧠 Abstract Base Classes (ABC)

> *“Force subclasses to implement required methods.”*

```python
import abc

class GetterSetter(metaclass=abc.ABCMeta):
    @abc.abstractmethod
    def set_val(self, value):
        pass

    @abc.abstractmethod
    def get_val(self):
        pass

class MyClass(GetterSetter):
    def set_val(self, value):
        self._value = value

    def get_val(self):
        return self._value
```

> 💡 **Improvement Suggestion**:  
> - Use `@abc.abstractmethod` with docstrings for clarity.
> - Add `@abc.abstractproperty` for abstract properties.
> - Use `@abc.abstractclassmethod` for abstract factory methods.

---

## 🚫 Avoid “Unpythonic” Code

> *“Avoid checking types manually — use polymorphism instead.”*

```python
# ❌ Unpythonic
if isinstance(obj, MyClass):
    obj.do_something()
elif isinstance(obj, OtherClass):
    obj.do_something_else()

# ✅ Pythonic — use polymorphism
for obj in objects:
    obj.do_something()
```

> 💡 **Improvement Suggestion**:  
> - Use **type hints** to improve code clarity.
> - Use **protocol-based interfaces** (e.g., `Protocol`) for more flexible typing.
> - Use **duck typing** with `isinstance` or `hasattr`.

---

## 🧩 Private / Protected Attributes

> *“Python doesn’t have true private variables — but conventions exist.”*

```python
class MyClass:
    def __init__(self, value):
        self._value = value  # convention: protected
        self.__value = value  # convention: private (but can be accessed)

    def _protected_method(self):
        pass

    def __private_method(self):
        pass
```

> 💡 **Improvement Suggestion**:  
> - Use `__slots__` to reduce memory usage.
> - Use `@property` to expose internal state.
> - Use `@property` with `@property.setter` for controlled access.
> - Use `dataclasses` for simple, readable, and maintainable classes.

---

## 🧪 Summary: What You Should Know

| Concept             | Purpose                             | Example                          |
|---------------------|-------------------------------------|----------------------------------|
| Encapsulation       | Hide data, expose methods           | `@property`                     |
| Inheritance         | Reuse code                          | `class Child(Parent)`            |
| Polymorphism        | Same method, different behavior     | `for obj in [a, b, c]: obj.method()` |
| Magic Methods       | Overload operators                  | `__add__`, `__repr__`           |
| ABCs               | Enforce contract                    | `@abc.abstractmethod`           |
| `@property`         | Controlled access                   | `@property def name(self)`      |
| `__slots__`         | Reduce memory usage                 | `__slots__ = ['x', 'y']`        |

---

## 🧭 Suggested Improvements to the Lesson

### 1. **Add Visual Aids**
- Diagrams of inheritance trees.
- Flowcharts for MRO.
- UML diagrams for classes.

### 2. **Hands-On Examples**
- Create a `BankAccount` class with `deposit()`, `withdraw()` methods.
- Build a `Shape` class with `area()` method — implement for `Circle`, `Square`.

### 3. **Use Real-World Scenarios**
- Use `datetime`, `json`, `os`, `requests` — show how OOP is used in real code.

### 4. **Add Type Hints**
- Use `def method(self) -> None: ...` to improve code clarity.

### 5. **Include Debugging Tips**
- Use `print(dir(obj))` to see what methods are available.
- Use `help(obj)` to see docstrings.

### 6. **Use `dataclasses` for Simplicity**
```python
from dataclasses import dataclass

@dataclass
class Point:
    x: int
    y: int

    def __add__(self, other):
        return Point(self.x + other.x, self.y + other.y)
```

---

## ✅ Final Thoughts

> *“OOP is not a magic trick — it’s a way of thinking.”*

Master OOP by:
- Writing clean, readable code.
- Using Python’s built-in features (magic methods, `@property`, `ABCs`).
- Avoiding “unpythonic” code.
- Thinking in terms of **objects, not functions**.

---

## 📚 Resources

- [Python Official Docs — OOP](https://docs.python.org/3/tutorial/classes.html)
- [Python ABCs — Abstract Base Classes](https://docs.python.org/3/library/abc.html)
- [Python Magic Methods — Dunder Methods](https://docs.python.org/3/reference