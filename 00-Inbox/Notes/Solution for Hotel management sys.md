
---
# Design summary (short)

Classes:

- `Room` — basic room info (number, type, price).
    
- `Guest` — guest identity.
    
- `Booking` — represents one booking (room, guest, start/end, price, id).
    
- `Hotel` — manages rooms and bookings; API for `book_room`, `cancel_booking`, `available_rooms`, `revenue`, `guest_bookings`.
    

Important rules implemented:

- Date strings parsed with `datetime.strptime("%Y-%m-%d")`.
    
- Bookings are for a date range: `start_date` inclusive, `end_date` exclusive (common pattern).
    
- Overlap detection prevents double-booking of the same room.
    
- Custom exceptions for domain errors.
    
- Booking IDs are unique and incremental.
    

---

# Full implementation (copy / run in one file)

```python
from datetime import datetime, timedelta
from typing import List, Optional
import itertools

# ---- Exceptions ----
class BookingError(Exception):
    pass

class NoRoomAvailableError(BookingError):
    pass

class BookingNotFoundError(BookingError):
    pass

# ---- Models ----
class Room:
    def __init__(self, room_number: int, room_type: str, price_per_night: float):
        self.room_number = room_number
        self.room_type = room_type
        self.price_per_night = price_per_night

    def __repr__(self):
        return f"Room({self.room_number}, {self.room_type}, ${self.price_per_night:.2f})"

class Guest:
    def __init__(self, name: str, email: Optional[str] = None):
        self.name = name
        self.email = email

    def __repr__(self):
        return f"Guest({self.name})"

class Booking:
    _ids = itertools.count(1)

    def __init__(self, room: Room, guest: Guest, start_date: datetime, end_date: datetime):
        if end_date <= start_date:
            raise BookingError("end_date must be after start_date")
        self.id = next(Booking._ids)
        self.room = room
        self.guest = guest
        self.start_date = start_date
        self.end_date = end_date  # exclusive
        self.total_price = self._compute_price()

    def _compute_price(self) -> float:
        nights = (self.end_date - self.start_date).days
        return nights * self.room.price_per_night

    def overlaps(self, other_start: datetime, other_end: datetime) -> bool:
        # Ranges: [start_date, end_date)
        return not (self.end_date <= other_start or other_end <= self.start_date)

    def __repr__(self):
        sd = self.start_date.strftime("%Y-%m-%d")
        ed = self.end_date.strftime("%Y-%m-%d")
        return f"Booking(id={self.id}, room={self.room.room_number}, guest={self.guest.name}, {sd} -> {ed}, ${self.total_price:.2f})"

# ---- Hotel Manager ----
class Hotel:
    DATE_FMT = "%Y-%m-%d"

    def __init__(self, name: str):
        self.name = name
        self.rooms: List[Room] = []
        self.bookings: List[Booking] = []

    # Utility: parse date from string or pass through datetimes
    @staticmethod
    def _parse_date(d):
        if isinstance(d, datetime):
            return d.replace(hour=0, minute=0, second=0, microsecond=0)
        if isinstance(d, str):
            return datetime.strptime(d, Hotel.DATE_FMT)
        raise ValueError("Date must be a datetime or 'YYYY-MM-DD' string")

    def add_room(self, room_number: int, room_type: str, price_per_night: float):
        if any(r.room_number == room_number for r in self.rooms):
            raise ValueError(f"Room number {room_number} already exists.")
        room = Room(room_number, room_type, price_per_night)
        self.rooms.append(room)
        return room

    def _find_available_room_of_type(self, room_type: str, start: datetime, end: datetime) -> Optional[Room]:
        candidates = [r for r in self.rooms if r.room_type == room_type]
        for room in candidates:
            # check bookings for this room
            conflicts = [b for b in self.bookings if b.room.room_number == room.room_number and b.overlaps(start, end)]
            if not conflicts:
                return room
        return None

    def book_room(self, guest: Guest, room_type: str, start_date, end_date) -> Booking:
        start = self._parse_date(start_date)
        end = self._parse_date(end_date)
        if end <= start:
            raise BookingError("End date must be after start date.")

        room = self._find_available_room_of_type(room_type, start, end)
        if not room:
            raise NoRoomAvailableError(f"No available '{room_type}' room from {start.strftime(self.DATE_FMT)} to {end.strftime(self.DATE_FMT)}")
        booking = Booking(room, guest, start, end)
        self.bookings.append(booking)
        return booking

    def cancel_booking(self, booking_id: int) -> Booking:
        for i, b in enumerate(self.bookings):
            if b.id == booking_id:
                removed = self.bookings.pop(i)
                return removed
        raise BookingNotFoundError(f"Booking {booking_id} not found.")

    def available_rooms(self, room_type: Optional[str], start_date, end_date) -> List[Room]:
        start = self._parse_date(start_date)
        end = self._parse_date(end_date)
        available = []
        candidates = [r for r in self.rooms if room_type is None or r.room_type == room_type]
        for room in candidates:
            if all(not b.overlaps(start, end) for b in self.bookings if b.room.room_number == room.room_number):
                available.append(room)
        return available

    def get_total_revenue(self, start_date: Optional[str] = None, end_date: Optional[str] = None) -> float:
        # If start/end provided, sum bookings that intersect that window; else sum all bookings
        if start_date is None and end_date is None:
            return sum(b.total_price for b in self.bookings)
        start = self._parse_date(start_date)
        end = self._parse_date(end_date)
        total = 0.0
        for b in self.bookings:
            # compute overlap nights between [b.start, b.end) and [start, end)
            if b.overlaps(start, end):
                overlap_start = max(b.start_date, start)
                overlap_end = min(b.end_date, end)
                nights = (overlap_end - overlap_start).days
                total += nights * b.room.price_per_night
        return total

    def list_guest_bookings(self, guest: Guest) -> List[Booking]:
        return [b for b in self.bookings if b.guest.name == guest.name]

    def find_booking(self, booking_id: int) -> Booking:
        for b in self.bookings:
            if b.id == booking_id:
                return b
        raise BookingNotFoundError(f"Booking {booking_id} not found.")

    def __repr__(self):
        return f"Hotel({self.name}, rooms={len(self.rooms)}, bookings={len(self.bookings)})"
```

---

# Quick usage demo & tests

```python
# Setup
hotel = Hotel("Sofi Inn")
hotel.add_room(101, "single", 50.0)
hotel.add_room(102, "single", 55.0)
hotel.add_room(201, "double", 90.0)
hotel.add_room(202, "double", 95.0)
hotel.add_room(301, "suite", 200.0)

# Guests
alice = Guest("Alice", "alice@example.com")
bob = Guest("Bob", "bob@example.com")

# Book a single room for Alice (2 nights)
b1 = hotel.book_room(alice, "single", "2025-10-20", "2025-10-22")
print(b1)   # Booking(...)

# Try overlapping booking for same type -> another single room exists so it should succeed
b2 = hotel.book_room(bob, "single", "2025-10-21", "2025-10-23")
print(b2)

# Now both singles are booked for 2025-10-21 so a third single booking would fail
try:
    guest3 = Guest("Charlie")
    hotel.book_room(guest3, "single", "2025-10-21", "2025-10-22")
except NoRoomAvailableError as e:
    print("Expected:", e)

# Availability check
avail = hotel.available_rooms("double", "2025-10-21", "2025-10-22")
print("Available doubles:", avail)

# Revenue for all bookings
print("Total revenue (all):", hotel.get_total_revenue())

# Revenue for a window
print("Revenue between 2025-10-21 and 2025-10-22:", hotel.get_total_revenue("2025-10-21", "2025-10-22"))

# Cancel booking
cancelled = hotel.cancel_booking(b2.id)
print("Cancelled:", cancelled)

# List bookings for Alice
print("Alice bookings:", hotel.list_guest_bookings(alice))
```

Expected behavior:

- Two singles can be booked for overlapping nights because there are two single rooms.
    
- A third attempt on the same overlapping nights fails with `NoRoomAvailableError`.
    
- `get_total_revenue()` computes correct sums; windowed revenue accounts only overlapping nights.
    

---

# Exercises & Extensions (choose 1–2)

Make the system slightly more challenging:

1. **Add validation rules**
    
    - Block bookings longer than 30 nights or shorter than 1 night.
        
    - Require a minimum stay (e.g., 2 nights on weekends).
        
2. **Add cancellation policy**
    
    - If canceled less than X days before start, charge a penalty (percentage of total).
        
    - Implement `cancel_booking(booking_id, when_canceled)` returning refunded amount.
        
3. **Add room features & search**
    
    - Rooms have features (`sea_view`, `balcony` — store as set).
        
    - Allow booking requests like `room_type="double", must_have={"sea_view"}`.
        
4. **Persistence**
    
    - Save & load `rooms` and `bookings` to/from JSON.
        
    - Be careful serializing datetimes (ISO format works).
        
5. **Overbook handling**
    
    - Add waitlist: when no room available, add guest to a waitlist for specified dates; notify and auto-book if a cancellation frees a room.
        
6. **Thread-safety**
    
    - If the system is used in parallel (web server), wrap booking/cancel with a lock to avoid race conditions.
        
7. **Pricing rules**
    
    - Seasonal pricing, discounts for long stays, extra fees for extra guests.
        
8. **Unit tests**
    
    - Write `pytest` tests for overlap logic, revenue calc, booking/cancel flows.
        

---

# A few remarks & tips

- Use the `[start_date, end_date)` convention consistently — it avoids off-by-one date bugs.
    
- Overlap logic `not (end <= other_start or other_end <= start)` is standard and easier to reason about than many ad-hoc conditions.
    
- Keep business rules (cancellation policy, pricing) separate from storage logic to make the code maintainable.
    
- When adding JSON persistence, convert datetimes with `.strftime("%Y-%m-%d")` and parse on load.
    

---

Would you like me to:

- 1. convert the example into a small CLI interactive demo, or
        
- 2. add persistence (save/load to JSON), or
        
- 3. write a few `pytest` unit tests for overlap/revenue/cancel logic?
        
