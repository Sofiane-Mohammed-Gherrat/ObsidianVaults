
## What is `super()` and its syntax

### Basic idea

`super()` is a built-in function in Python that returns a proxy object that lets you call methods of a superclass (i.e. the parent class) from a subclass. Using `super()` lets you avoid hardcoding the parent class name, which is helpful especially when dealing with multiple inheritance or when the class hierarchy may change. ([GeeksforGeeks](https://www.geeksforgeeks.org/python-super/?utm_source=chatgpt.com "Python super() - GeeksforGeeks"))

### Syntax in Python 3

The most common usage in Python 3 is:

```python
super().method(args...)
```

Here, `super()` (with no arguments) returns a proxy object bound to the instance’s class, so that when you call `.method(...)`, it resolves to the method in the next class up in the method resolution order (MRO).

You would typically use `super()` in:

- An overridden method, to call the version in the parent class (before, after, or around your added logic).
    
- In a subclass’s `__init__`, to call the parent’s `__init__`, to ensure proper initialization of inherited attributes.
    
- In more complex multiple inheritance settings, to ensure correct chaining of method calls following the MRO.
    

### Alternative (less used) form

You can also explicitly pass the class and instance to `super`:

```python
super(CurrentClass, self).method(args...)
```

For example (in older style or when introspecting):

```python
class Bus(Vehicle):
    def seating_capacity(self, capacity=50):
        return super(Bus, self).seating_capacity(capacity=capacity)
```

But in Python 3, just `super()` is preferred.

---

## Where you’d use `super()`

Here are typical places:

1. **In `__init__` of subclass**: so you can extend the initializer without losing the parent’s initialization logic:
    
    ```python
    class Vehicle:
        def __init__(self, name, max_speed, mileage):
            self.name = name
            self.max_speed = max_speed
            self.mileage = mileage
    
    class Bus(Vehicle):
        def __init__(self, name, max_speed, mileage, route_number):
            super().__init__(name, max_speed, mileage)
            self.route_number = route_number
    ```
    
2. **When overriding a method but still wanting the parent’s behavior**: like your `seating_capacity` example — you override to add or change something (e.g. a default value) but still rely on the parent’s implementation for most of the work.
    
3. **In multiple inheritance**: to ensure that all relevant parent methods are called following the method resolution order (MRO), so subclasses in complex hierarchies cooperate correctly. `super()` helps avoid explicitly naming parent classes and dealing with diamond inheritance issues. ([realpython.com](https://realpython.com/python-super/?utm_source=chatgpt.com "Supercharge Your Classes With Python super()"))
    

---

## A clearer example to illustrate

Here’s a more extended example:

```python
class Vehicle:
    def seating_capacity(self, capacity):
        return f"The seating capacity of a {self.name} is {capacity} passengers"

class Bus(Vehicle):
    def seating_capacity(self, capacity=50):
        # maybe we want to log something or validate
        print("Bus.seating_capacity called")
        # then reuse parent logic
        return super().seating_capacity(capacity)

class MiniBus(Bus):
    def seating_capacity(self, capacity=20):
        print("MiniBus override")
        # you could do something extra here, then call parent
        return super().seating_capacity(capacity)
```

If you do:

```python
b = Bus("MyBus", 100, 10)
print(b.seating_capacity())      # calls Bus -> Vehicle method  

mb = MiniBus("Mini", 80, 8)
print(mb.seating_capacity())     # calls MiniBus -> Bus -> Vehicle
```

Each level can add or override behavior, but `super()` helps chain upward.


## Note:
#### Method signature / “contract” alignment
```python
def seating_capacity(self, capacity=50):
    return super().seating_capacity(capacity=50)
```
##### VS
```python
def seating_capacity(self, capacity):
    return super().seating_capacity(capacity=50)
```
#### ⚠️ Problem with second version
Even if the caller passes, say, `capacity=60`, the method will _ignore_ it and always call the parent with `capacity=50` (hardcoded). That defeats the idea of letting callers specify a different capacity.

<u>Best practice</u> to have the <mark class="hltr-mypurple">overriding method</mark> in <mark class="hltr-mypurple">alignment</mark> with the <mark class="hltr-myblue">parent method interface</mark> 

#### Returning the super().:
it's a good practice always return the value of the parent overriden method

```python
def seating_capacity(self, capacity=50):
	return super().seating_capacity(self, capacity=capacity)
```
#### Notice:

• Also, Python lets you change signatures arbitrarily, but doing so may violate the **Liskov substitution principle** (i.e. you should be able to use a `Bus` anywhere a `Vehicle` is expected) — overriding default arguments in a weird way might violate that.

• you can write `capacity=capacity` or simply `capacity` as positional, but using `capacity=capacity` in the `super()` call <mark class="hltr-mygreen-">keeps clarity</mark>.

