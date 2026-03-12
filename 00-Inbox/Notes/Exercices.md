
---

## 🟢 **Level 1 — Class Basics**

Focus: defining classes, attributes, and methods.

1. **Class: `Car`**
    - Attributes: `brand`, `model`, `year`
    - Method: `start()` that prints `"The car is starting..."`

2. **Class: `Book`**    
    - Attributes: `title`, `author`, `price`
    - Method: `discount(percent)` → returns the discounted price

3. **Class: `Rectangle`**    
    - Attributes: `width`, `height`
    - Methods:
        - `area()` → returns area
        - `perimeter()` → returns perimeter

4. **Class: `Student`**    
    - Attributes: `name`, `age`, `grades` (list)
    - Methods:
        - `add_grade(value)`
        - `average_grade()`

---

## 🟡 **Level 2 — Constructors, Static & Class Methods**

Focus: `__init__`, `@staticmethod`, and `@classmethod`.

5. **Class: `TemperatureConverter`**
    - Static methods:
        - `to_celsius(fahrenheit)`
        - `to_fahrenheit(celsius)`

6. **Class: `Employee`**    
    - Attributes: `name`, `salary`
    - Class variable: `employee_count`
    - Each time you create a new employee, increase the count
    - Class method: `get_total_employees()`

7. **Class: `BankAccount`**    
    - Attributes: `owner`, `balance`
    - Methods:
        - `deposit(amount)`
        - `withdraw(amount)` (don’t allow negative balance)
        - `display()`


---

## 🟠 **Level 3 — Inheritance**

Focus: base and derived classes.

8. **Classes: `Person` and `Student`**
    - `Person`: name, age, introduce()
    - `Student(Person)`: adds attribute `student_id`, overrides introduce()

9. **Classes: `Vehicle`, `Car`, `Bus`**    
    - `Vehicle`: name, speed, mileage
    - `Car` and `Bus` inherit from it
    - Override a method `capacity()` differently in each subclass

10. **Classes: `Animal`, `Dog`, `Cat`**    
    - `Animal`: method `speak()` (prints generic sound)
    - Subclasses override `speak()` with `"Woof!"` and `"Meow!"`

---

## 🔵 **Level 4 — Encapsulation & Properties**

Focus: private/protected attributes and getters/setters.

11. **Class: `Account`**    
    - Private attribute: `__balance`
    - Methods: `deposit()`, `withdraw()`
    - Property: `balance` (read-only)

12. **Class: `Student`**    
    - Private attribute: `__gpa`
    - Property: `gpa` with setter that ensures `0 ≤ gpa ≤ 4.0`

---

## 🟣 **Level 5 — Polymorphism & Abstract Classes**

Focus: method overriding, `abc` module.

13. **Abstract class: `Shape`**    
    - Abstract method: `area()`
    - Subclasses: `Circle`, `Square`, `Triangle`  
        Each implements `area()`

14. **Class: `Payment` (base)**    
    - Subclasses: `CreditCardPayment`, `PayPalPayment`, ``
    - Each implements `pay(amount)` differently

15. **Function using polymorphism:**

```python
def make_sound(animal):
    animal.speak()
```

Works for any object with a `speak()` method (`Dog`, `Cat`, etc.)

---

## 🔴 **Level 6 — Realistic Mini Projects**

Apply everything you’ve learned.

16. **Library Management System**
    - Classes: `Book`, `Member`, `Library`
    - A member can `borrow()` and `return()` books
    - The library tracks available and borrowed books

17. **E-Commerce Simulation**    
    - Classes: `Product`, `Customer`, `Order`
    - Orders calculate total price automatically
    - Add discounts or shipping costs

18. **School System**    
    - Classes: `Teacher`, `Student`, `Course`
    - Teachers have courses, students enroll
    - Each student can view enrolled courses and calculate GPA

19. **Restaurant Ordering System**    🟢
    - Classes: `MenuItem`, `Order`, `Customer`
    - Customers can add menu items to their order and see total price

20. **Hospital Management System**    
    - Classes: `Patient`, `Doctor`, `Appointment`
    - A doctor can have multiple patients
    - Print appointment schedules


---
## 🚀 Mini Projects For Intermediate Dev 


## 🏨 1. Hotel Booking System (Intermediate Edition)

### Concept

Simulate a small hotel where guests can book rooms, cancel bookings, and check availability.

### Classes

- **Room** → attributes: `room_number`, `room_type`, `price`, `is_booked`
- **Guest** → attributes: `name`, `email`, `bookings`
- **Hotel** → manages rooms and guests
    - Methods: `book_room(guest, room_type)`, `cancel_booking(guest)`, `show_available_rooms()`

### Stretch ideas

- Automatically assign a random available room of the requested type
- Raise a custom `NoRoomAvailableError`
- Add method `get_total_revenue()`

💡 _OOP Focus:_ composition (Hotel has Rooms and Guests), state management, simple error handling.

---

## 🎓 2. School Management System (Realistic Small Version)

### Concept

Manage a school’s teachers, students, and subjects — with enrollment logic.

### Classes

- **Person** → base class with name, age
- **Teacher(Person)** → attribute: `subject`
- **Student(Person)** → attribute: `courses` (list of enrolled courses)
- **Course** → attributes: `title`, `teacher`, `students`
    - Methods: `enroll_student(student)`, `list_students()`

### Stretch ideas

- Prevent double-enrollment
- Add `assign_grade(student, grade)`
- Compute class average

💡 _OOP Focus:_ inheritance, relationships (many-to-many), method interaction between classes.

---

## 📚 3. Library Simulator (Compact Version)

### Concept

Build a library that tracks books, members, and borrowed books.

### Classes

- **Book** → `title`, `author`, `isbn`, `available`
- **Member** → `name`, `borrowed_books`
- **Library** → manages books and members
    - Methods:
        - `add_book(book)`
        - `register_member(member)`
        - `borrow_book(member, isbn)`
        - `return_book(member, isbn)`

### Stretch ideas

- Add `due_date` or `fine` system
- Prevent borrowing more than 3 books
- Save and load library data from a JSON file

💡 _OOP Focus:_ class interactions, collections, enforcing constraints, light persistence.

---

## 🛒 4. Marketplace System (Inspired by HomiTrack style)

### Concept

Simulate a small online marketplace for freelancers or sellers.

### Classes

- **User** → base for `Seller` and `Buyer`
- **Seller(User)** → `listings` (list of products)
- **Buyer(User)** → `cart` (list of products)
- **Product** → `title`, `price`, `category`
    
- **Marketplace** → manages users and transactions
    
    - Methods:
        - `add_user(user)`
        - `list_products()`
        - `purchase(buyer, product)`

### Stretch ideas

- Track total marketplace revenue
- Add product rating and reviews
- Limit cart size

💡 _OOP Focus:_ relationships, composition, and simple business logic flow (Seller → Product → Buyer).

---

## 🏠 5. Apartment Rental System

### Concept

Simulate an agency that rents apartments to tenants.

### Classes

- **Apartment** → `address`, `rent`, `is_rented`
- **Tenant** → `name`, `rented_apartment`
- **Agency** → manages apartments and tenants
    - Methods: `rent_apartment(tenant, apartment)`, `release_apartment(tenant)`

### Stretch ideas

- Automatically assign cheapest available apartment
- Add `calculate_total_income()`
- Handle custom exception `AlreadyRentedError`

💡 _OOP Focus:_ relationship mapping (1-to-1), class communication, and method chaining.

---

## 🧠 6. Quiz Game System

### Concept

Build a quiz platform that stores questions and evaluates players’ answers.

### Classes

- **Question** → `text`, `choices`, `correct_answer`
- **Player** → `name`, `score`
- **Quiz** → manages questions and players
    - Methods:
        - `add_question(question)`
        - `play(player)` (asks all questions, updates score)
        - `show_results()`

### Stretch ideas

- Add difficulty levels
- Randomize questions
- Track high scores in a file

💡 _OOP Focus:_ logic flow, encapsulation, interaction between instances, and light data handling.

---

## 🧩 Optional Challenge Mix

Want more creative combos?

- 🔋 **Energy Tracker App** – devices report energy consumption, app shows monthly total
- 🚗 **Ride Booking System** – like Uber Lite (Driver, Passenger, Ride)
- 🧾 **Expense Tracker** – manage categories, budgets, and summaries
- 👟 **Fitness Tracker** – users log workouts, calories, and goals

---

### 🧱 Recommended next step for you

You’re already intermediate, so I’d suggest:  
👉 Start with the **Hotel Booking System** (3–4 classes, natural logic)  
Then move to the **School Management System** or **Marketplace** — both require solid design thinking.

---
# Solutions:
## Restaurant Ordering System 
### 🧩 **Class Structure Overview**
#### **1️⃣ MenuItems**

**Responsibility:**  
Load menu data from a CSV file, display it, and make it accessible to other classes.

**Attributes:**

- `path`: str — path to CSV file
- `header`: list — CSV header row
- `rows`: list — menu rows (list of lists)

**Methods:**

- `_load_items()` → loads menu data
- `as_dict()` → returns list of dicts
- `show_menu()` → displays formatted menu

---

### **2️⃣ Client**

**Responsibility:**  
Represent a customer who places one or more orders.

**Attributes:**

- `name`: str — client’s name
    
- `phone`: str — contact number
    
- `orders`: list — stores `Order` objects
    

**Methods:**

- `add_order(order)` → adds an order to the client’s record
    
- `show_orders()` → lists all orders placed by this client
    
- `__str__()` → readable client summary
    

---

### **3️⃣ Order**

**Responsibility:**  
Manage a single customer order — items, quantities, and totals.

**Attributes:**

- `client`: Client — who placed the order
    
- `menu`: MenuItems — reference for menu data lookup
    
- `items`: list — ordered items (dicts with name, qty, price, etc.)
    
- `total`: float — running total price
    
- _(optional)_ `id`, `timestamp`, `status`
    

**Methods:**

- `add_item(code, quantity)` → add item by menu code
    
- `remove_item(code)` → remove or adjust item quantity
    
- `calculate_total()` → compute full order cost
    
- `show_summary()` → print order items and total
    
- `generate_receipt()` → show formatted receipt
    

---

### **4️⃣ (Optional) RestaurantSystem / OrderManager**

**Responsibility:**  
High-level system that coordinates everything — manages clients, orders, and menus.

**Attributes:**

- `menu`: MenuItems
    
- `clients`: list of Client
    
- `orders`: list of Order
    

**Methods:**

- `create_client(name, phone)`
    
- `create_order(client)`
    
- `find_client(name_or_phone)`
    
- `list_all_orders()`
    
- `save_orders()` / `load_orders()`
    

---

### 🔗 Relationships

- **MenuItems** → provides item info to `Order`
    
- **Client** ↔ **Order** → one-to-many (one client can have many orders)
    
- **Order** → references `Client` and `MenuItems`
    

---

Would you like me to sketch a **UML-style diagram** (text-based) showing how these classes connect and depend on each other?