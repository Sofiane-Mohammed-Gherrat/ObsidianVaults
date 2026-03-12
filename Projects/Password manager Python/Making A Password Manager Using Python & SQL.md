---
from: youtube
created: 2025-08-11
tags:
  - fleeting
  - inbox
source: https://www.youtube.com/watch?v=hkhyKJj28Ac
---
---

## **1. Points Covered in the Video**

**Intro / Context**

- Casual start, explains why he wears a hat indoors (personal touch, unrelated to coding).

- Goal: Build a password manager using **Python** + **PostgreSQL** (SQL database).
 
- Project idea has been in mind for a while, first time implementing it.


**Initial Planning**

- Writes requirements & questions on iPad.

- Discusses:
	
	- Basic password manager concept (hashing passwords).
    
    - Two approaches:
        
        1. Store hashed passwords for each site.
        
        2. Use a **master password** that generates other passwords automatically.
        
- Decides to build a **terminal-based interface** (no GUI for now).

- Requirements:
    
    - User can enter site/URL + password → store in SQL DB.
    
	- User can retrieve password from DB.
    
    - Password auto-copies to clipboard.
    
- Features brainstormed:
    
    - Menu system in terminal.
    
    - Password hashing.
    
    - SQL database setup.
    
    - Clipboard integration.

**Database Setup**

- Creates a PostgreSQL database & table (`accounts`) with fields:  
    `password`, `email`, `username`, `url`, `app_name`.

- Writes Python script to insert test data into DB.

- Demonstrates a `SELECT * FROM accounts` query to verify insertions.

- Next step: turn DB insert into a Python function for automation.

**Hashing Discussion**

- Clarifies a misconception:
    
    - **Hashing is one-way** → cannot be “unhashed”.
    
    - Idea: Combine **master password + site name + secret key** → hash → use as password.
    
- Notes current implementation is **not yet highly secure** (prototype stage).

**Menu System**

- Implements:
    
    1. Create new password.
    
    2. Find all sites/apps for an email.
    
    3. Find password for a site/app.
    
    4. Exit.
    
- Demonstrates creating and retrieving passwords from the DB.
    
- Clipboard auto-copy works when retrieving passwords.

**Extra Features / Polish**

- Adds retrieval by email to list all linked accounts.

- Adds retrieval by app/site name to get specific password.

- Mentions potential for more features (sorting, export, etc.).

**Workflow & Challenges**

- Development time: Started 7 AM, finished ~5:40 PM.

- Main delays: PostgreSQL setup issues on Windows → switched to Linux (Kali).

- Frustration at solving DB setup after hours of trial and error.


**Final Remarks**

- Working but basic password manager.

- Not production-safe but a good starting point.

- Plans to improve it.

- Repository will be on GitHub for others to clone and build upon.


---

## **2. Tools / Workflow**

**Languages / Libraries**

- **Python** (core logic, terminal interface).

- **PostgreSQL** (database).

- Likely `psycopg2` Python library for PostgreSQL connection.

- Clipboard library (e.g., `pyperclip` or similar).

- Python’s `hashlib` for hashing passwords.


**Environment**

- Initially tried **Windows** → PostgreSQL setup issues.

- Switched to **Kali Linux** (Linux OS).

- Used terminal for both coding & DB queries.


**Workflow**

1. Plan requirements & structure on paper/iPad.
    
2. Set up PostgreSQL database and `accounts` table.
    
3. Write Python scripts for:
    
    - Inserting records into DB.
        
    - Retrieving records from DB.
        
    - Hashing passwords.
        
    - Menu-driven CLI interaction.
        
    - Clipboard copy feature.
        
4. Debug & iterate features.
    
5. Add more utility functions (search by email/site).
    
6. Test with example data.
    
7. (Optional) Publish code to GitHub.
    

---

## **3. Clear Plan to Implement**

```mysql
1. PLANNING
   - Decide password manager approach (store hashed or master password-based).
   - Define database fields (site/app, email, username, hashed password, URL).

2. SETUP DATABASE
   - Install PostgreSQL.
   - Create a database: password_manager_db.
   - Create table: accounts(password, email, username, url, app_name).

3. PYTHON PROJECT STRUCTURE
   - db.py → handles DB connection and queries.
   - hashing.py → hashing functions.
   - clipboard.py → clipboard handling.
   - main.py → main menu and program flow.

4. CORE FEATURES
   A) CREATE PASSWORD:
      - Prompt: site/app name, email, easy-to-remember password.
      - Combine with master password + secret key → hash.
      - Insert into DB.
      - Copy to clipboard.

   B) RETRIEVE PASSWORD:
      - By site/app name OR email.
      - Fetch from DB.
      - Copy to clipboard.

5. MENU SYSTEM (CLI)
   - 1. Create new password
   - 2. Find all sites/apps for email
   - 3. Find password for site/app
   - 4. Exit

6. HASHING IMPLEMENTATION
   - Use hashlib (e.g., SHA-256).
   - Store only hashed password in DB (not plain text).

7. CLIPBOARD FEATURE
   - Use pyperclip (or platform-specific tool) to copy retrieved password.

8. TESTING
   - Insert test data.
   - Verify creation, retrieval, clipboard functions.
   - Check DB directly with SQL queries.

9. IMPROVEMENTS (Future)
   - Encrypt DB (not just hash).
   - Add GUI (Tkinter, PyQt).
   - Auto-generate strong passwords.
   - Multi-user support.
```

---
Got it — you want me to go ahead and actually **prepare the flow diagram** for the password manager process.

Here’s a clean, logical **flow diagram** of the data path from user input to clipboard:

```mysql
   ┌────────────┐
   │   User     │
   │  Input     │
   │(choice)    │
   └─────┬──────┘
         │
         ▼
 ┌─────────────────┐
 │ Generate/Enter  │
 │   Password      │
 └─────┬───────────┘
       │
       ▼
┌───────────────────┐
│ Hash Password     │
│  (SHA256)         │
└──────┬────────────┘
       │
       ▼
┌───────────────────┐
│ Store in Database │
│ (local file)      │
└──────┬────────────┘
       │
       ▼
┌───────────────────┐
│ Copy to Clipboard │
│ (optional)        │
└───────────────────┘
```

**Legend**:

- **User Input** → Selecting whether to create, view, or retrieve a password.
    
- **Hash Password** → Protects raw passwords before saving.
    
- **Database** → Could be a `.txt` file, SQLite DB, etc.
    
- **Clipboard** → Allows quick paste into login forms.
    