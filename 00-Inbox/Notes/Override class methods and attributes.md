
## 🧩 What “overriding” means

When a **child class** (subclass) inherits from a **parent class** (superclass), it automatically gets all its methods and attributes.  
If the child **redefines** any of them with the same name, it **overrides** (replaces) the parent version.

Overriding allows customizing or extending behavior in subclasses.

---

| **#** | **Type of Override**                            | **Description**                                                                                                                 |
| :---: | :---------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------ |
| **1** | **Basic Method Override**                       | The child redefines a parent method with the same name and parameters.                                                          |
| **2** | **Override + Call Parent (`super()`)**          | The child overrides a method but calls the parent version inside to extend its behavior.                                        |
| **3** | **Override Class Attributes**                   | The child redefines a class-level variable from the parent.                                                                     |
| **4** | **Override Instance Attributes (`__init__`)**   | The child customizes initialization, possibly changing parent-set attributes.                                                   |
| **5** | **Override Special (Magic) Methods**            | The child overrides Python’s special methods to modify built-in behavior.                                                       |
| **6** | **Override with Default Arguments**             | The child redefines a method while changing or adding default parameter values.                                                 |
| **7** | **Multi-level / Multiple Inheritance Override** | The most specific class in the inheritance chain overrides parent behavior; Python uses MRO to determine which version applies. |

---

## ⚙️ 1. Overriding Methods (Basic)

The simplest form — you redefine the same method name in the child class.

```python
class Parent:
    def greet(self):
        print("Hello from Parent")

class Child(Parent):
    def greet(self):  # override
        print("Hello from Child")

c = Child()
c.greet()  # → "Hello from Child"
```

✅ Use when the child should behave differently.  
⚠️ The parent version is ignored unless you call it manually.

---

## ⚙️ 2. Overriding and Calling the Parent Method (`super()`)

You can override a method but still use the parent’s version with `super()`.

```python
class Parent:
    def setup(self):
        print("Parent setup")

class Child(Parent):
    def setup(self):
        super().setup()      # call parent’s method
        print("Child setup") # extend behavior

c = Child()
c.setup()
```

Output:

```
Parent setup
Child setup
```

✅ Use when you want to **extend** instead of replace the parent logic.

---

## ⚙️ 3. Overriding Class Attributes

If the parent has a **class-level variable**, the child can redefine it.

```python
class Parser:
    file_type = "TXT"

class JSONParser(Parser):
    file_type = "JSON"

print(JSONParser.file_type)  # → JSON
```

✅ Great for changing constants or configurations.  
⚠️ Avoid doing this with mutable objects (like lists or dicts).

---

## ⚙️ 4. Overriding Instance Attributes (in `__init__`)

You can also override values set in the parent’s constructor.

```python
class Vehicle:
    def __init__(self, name, max_speed):
        self.name = name
        self.max_speed = max_speed

class SportsCar(Vehicle):
    def __init__(self, name, max_speed):
        super().__init__(name, max_speed)
        self.max_speed = max_speed * 2  # override value

car = SportsCar("Ferrari", 200)
print(car.max_speed)  # → 400
```

✅ Use when the child’s attributes differ.  
⚠️ Always call `super().__init__()` to keep parent initialization.

---

## ⚙️ 5. Overriding Special (Magic) Methods

These are methods like `__str__`, `__len__`, `__eq__`, etc.  
You can override them to customize built-in behavior.

```python
class MyList(list):
    def __len__(self):  # override built-in behavior
        return 0

nums = MyList([1, 2, 3])
print(len(nums))  # → 0
```

✅ Lets you define how your objects behave with built-in functions.

---

## ⚙️ 6. Overriding with Default Arguments

You can override a method and provide **default argument values**.

```python
class Vehicle:
    def seating_capacity(self, capacity):
        return f"Capacity: {capacity}"

class Bus(Vehicle):
    def seating_capacity(self, capacity=50):  # override + default
        return super().seating_capacity(capacity)

bus = Bus()
print(bus.seating_capacity())    # → Capacity: 50
print(bus.seating_capacity(30))  # → Capacity: 30
```

✅ Adds a default behavior while keeping flexibility.

---

## ⚙️ 7. Multi-Level or Multiple Inheritance Overrides

In deeper or multiple inheritance, the **most specific class** wins.  
Python uses the **MRO (Method Resolution Order)** to decide which method to use.

```python
class A:
    def show(self): print("A")

class B(A):
    def show(self): print("B")

class C(B):
    def show(self): print("C")

class D(A):
    def show(self): print("D")

class E(C, D):
    pass

E().show()  # → "C" (comes first in MRO)
```

✅ Lets you override methods across several inheritance levels.  
⚠️ Understand the MRO to avoid confusion or unexpected behavior.

---

## 📘 Best Practices

- ✅ Keep the **method signature compatible** with the parent version.
- ✅ Use `super()` whenever you need to reuse parent logic.
- ✅ Don’t duplicate code; extend instead.
- ⚠️ Avoid overriding mutable class variables.
- ⚠️ Respect the parent’s contract — your method should behave consistently.
- 🧾 Add docstrings or comments when overriding methods intentionally.
