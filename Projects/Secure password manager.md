---
from: youtube
created: 2025-08-11
tags:
  - python
  - cyberSecurity
  - project
source:
---
---
### **Sources**
	https://www.youtube.com/watch?v=GjCnw2mmsxQ
	github: 
	https://github.com/leetCipher/passkeep

---

## **1. Core Concepts**

- **Database file format (`passwords.db`)**:
    
    - First **64 bytes** → SHA-256 hash of the database encryption key.
        
    - Remaining bytes → Encrypted credential records (AES-CBC encrypted).
        
- **Encryption**:
    
    - AES (Advanced Encryption Standard) in **CBC mode**.
        
    - Encryption key is the user’s decryption password, padded to a multiple of 16 bytes.
        
    - Initialization vector (IV) is taken from the first 16 bytes of the padded password.
        
- **Credential storage format (in memory)**:
    
```shell
"id-username/email-password-platform|id-username/email-password-platform|..."
```
    
    - Fields are separated by `-`
        
    - Records are separated by `|`
        
    - `id` is sequential.
        
- **Security**:
    
    - Passwords are never stored in plaintext on disk.
        
    - SHA-256 is used for key verification (not for encryption).
        
    - AES encryption ensures confidentiality.
        

---

## **2. Main Workflow**

```mysql
START
↓
Check if `passwords.db` exists
  ↳ If not, prompt for path or create new one with default password "password123"
↓
Read hash from first 64 bytes
↓
Prompt user for decryption key (max 3 tries)
↓
If correct:
    Decrypt stored credentials (AES-CBC)
    Load them into memory (`self.content`)
    Show menu with options
    Loop until user exits
Else:
    Exit program
```

---

## **3. Key Features & Functions**

### **Initialization**

```python
__init__()
```

- Opens `passwords.db` or calls `check_database()` if not found.
    
- Reads **stored password hash** and **encrypted data**.
    
- Asks user for the decryption key, hashes it, compares with stored hash.
    
- If valid, decrypts the database via `decrypt_db()`.
    

---

### **Decrypting the database**

```python
decrypt_db()
```

- Creates an AES instance with:
    
    - Key = padded decryption key
        
    - IV = first 16 bytes of the key
        
- Decrypts data and unpads it.
    
- Splits credentials into records.
    
- Calls `display_options()` to start the interactive menu.
    

---

### **Saving the database**

```python
save_db()
```

- Re-encrypts `self.content` using the same AES-CBC settings.
    
- Writes the hash + ciphertext back into `passwords.db`.
    

---

### **Database creation or path checking**

```python
check_database()
```

- Asks user for path to `passwords.db`.
    
- If not found and user presses Enter → Creates new DB with default password `"password123"`.
    

---

### **Viewing stored credentials**

```python
show_credentials()
```

- Converts stored content into a table using `tabulate`.
    
- Displays neatly formatted output with headers.
    

---

### **Adding credentials**

```python
add_credentials()
```

- Prompts for username/email, password (twice), and platform.
    
- Assigns incremental ID.
    
- Saves to database.
    

---

### **Editing credentials**

```python
edit_credentials()
```

- Displays all records.
    
- Asks for record ID.
    
- Lets user change username/email **or** password.
    
- Saves updated DB.
    

---

### **Deleting credentials**

```python
delete_credentials()
```

- Similar to editing but removes the record from memory.
    
- Updates DB file.
    

---

### **Changing DB encryption key**

```python
change_db_password()
```

- Verifies current key.
    
- Prompts for a new key (min 10 chars, confirmed twice).
    
- Updates stored hash and re-encrypts data.
    

---

### **Generating random secure passwords**

```python
generate_password()
```

- Creates a random 32-character password from letters, numbers, and symbols.
    

---

### **Backing up the database**

```python
backup_database()
```

- Copies `passwords.db` to `passwords.db.bak` after verifying the key.
    

---

### **Erasing the database**

```python
erase_database()
```

- Deletes all records after confirming the key.
    

---

### **Utility functions**

- **`pad_db_key()`** → Pads key to multiple of 16 bytes for AES.
    
- **`find_record()`** → Finds index of a record by ID.
    
- **`display_options()`** → Main menu loop with options 1–9.
    

---

## **4. Menu Options**

```markdown
[1] Show credentials
[2] Add credentials
[3] Edit credentials
[4] Delete credentials
[5] Change database password
[6] Generate password
[7] Backup database
[8] Erase database
[9] Exit
```

---

## **5. flow diagram** 

```mysql
 ┌────────────────────────────┐
 │ Program starts             │
 │ (PasswordManager object)   │
 └──────────────┬─────────────┘
                │
                ▼
   ┌───────────────────────────┐
   │ Check for passwords.db    │
   │ - If exists → open file   │
   │ - Else → check_database() │
   └──────────────┬────────────┘
                  │
                  ▼
     ┌────────────────────────────┐
     │ Read stored hash (64 bytes)│
     │ Read ciphertext            │
     └──────────────┬─────────────┘
                    │
                    ▼
         ┌──────────────────────────────┐
         │ Ask for decryption key (3x)  │
         │ Pad to multiple of 16 bytes  │
         │ Hash (SHA-256) & compare     │
         └──────────────┬───────────────┘
                        │
             ┌──────────┴────────────┐
             │ Match?                │
             │   Yes                 │ No
             ▼                       │
  ┌─────────────────────┐            │
  │ decrypt_db():       │            │
  │ - AES decrypt       │            │
  │ - Unpad & decode    │            │
  │ - Count records     │            │
  └───────────┬─────────┘            │
              │                      │
              ▼                      │
   ┌────────────────────────────┐    │
   │ Display main menu          │◄───┘
   │ [1] Show credentials       │
   │ [2] Add credentials        │
   │ [3] Edit credentials       │
   │ [4] Delete credentials     │
   │ [5] Change DB password     │
   │ [6] Generate password      │
   │ [7] Backup database        │
   │ [8] Erase database         │
   │ [9] Exit                   │
   └───────────┬────────────────┘
               │
    ┌──────────┴────────────────────────────────────────────┐
    │ User picks option:                                    │
    │ - 1: show_credentials()                               │
    │ - 2: add_credentials()                                │
    │ - 3: edit_credentials()                               │
    │ - 4: delete_credentials()                             │
    │ - 5: change_db_password()                             │
    │ - 6: generate_password()                              │
    │ - 7: backup_database()                                │
    │ - 8: erase_database()                                 │
    │ - 9: Exit → print Goodbye & break loop                │
    └───────────────────────────────────────────────────────┘
```

---
