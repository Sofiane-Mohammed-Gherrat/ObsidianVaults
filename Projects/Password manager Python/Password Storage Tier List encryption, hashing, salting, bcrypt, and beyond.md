---
from: youtube
created: 2025-08-11
tags:
  - fleeting
  - inbox
source: https://www.youtube.com/watch?v=qgpsIBLvrGY
---

---

## **1. Points Dealt with in the Video**

(with key snippets for clarity)

1. **Problem: Password Storage Risks**
    
    - Storing passwords opens risk of breaches → reputational & security damage.
        
2. **F-Tier: Plaintext Storage**
    
    - Store passwords directly in DB.
        
    - “If your database is breached, you’re done.”
        
    - No defense layer.
        
3. **D-Tier: Encryption**
    
    - Encrypt passwords, store key separately.
        
    - If key is stolen, attacker can decrypt all passwords.
        
    - Risk of insider threats.
        
4. **C-Tier: Hashing**
    
    - Store hashed passwords instead of actual ones.
        
    - Verify login by hashing input & comparing.
        
    - Properties: **One-way function**, **Collision resistance**.
        
    - Use modern secure hashes (SHA-2, not MD5/SHA-1).
        
5. **Dictionary Attacks & Rainbow Tables**
    
    - Weak passwords guessed by hashing common words.
        
    - Rainbow tables = precomputed hash databases.
        
6. **B-Tier: Salting**
    
    - Add a unique random string (salt) to each password before hashing.
        
    - Prevents rainbow tables, differentiates same-password users.
        
    - Doesn’t stop dictionary attacks.
        
7. **A-Tier: Slow Hash Functions**
    
    - Use password-specific slow hashes: **bcrypt**, **scrypt**, **Argon2**.
        
    - Built-in salting + configurable work factor.
        
    - Slows down brute-force to thousands/sec instead of billions/sec.
        
8. **S-Tier: Don’t Store Passwords**
    
    - Use third-party auth: Google, Facebook, etc.
        
    - Removes password handling from your system entirely.
        

---

## **2. Structured Plan of the Video**

```mysql

Password Storage Security Tier List

1. F-Tier: Plaintext Storage
   - Risks: instant breach if DB leaked

2. D-Tier: Encryption
   - Pros: hides raw password
   - Cons: key theft, insider risk

3. C-Tier: Hashing
   - One-way function
   - Collision resistance
   - Avoid weak/insecure hash functions

	  → Threats: Dictionary & Rainbow Table Attacks
	   - Weak password exploitation
	   - Precomputed hash databases

4. B-Tier: Salting
   - How salting works
   - Stops rainbow tables
   - Still vulnerable to brute-force

5. A-Tier: Slow Password Hashing Functions
   - bcrypt, scrypt, Argon2
   - Work factor
   - Slows brute-force attempts

6. S-Tier: No Password Storage
   - Use external authentication services

```

---

## **3. Workflow to Implement Secure Password Storage**

```mysql

Workflow: Secure Password Handling

Step 1 — Choose Approach:
    If possible → Use third-party authentication (Google, Facebook)
    Else → Proceed with secure password storage

Step 2 — Password Collection:
    - Collect password via secure HTTPS form
    - Enforce strong password policy

Step 3 — Salting:
    - Generate a cryptographically secure random salt (e.g., 16+ bytes)
    - Append or prepend salt to password

Step 4 — Slow Hashing:
    - Use bcrypt, scrypt, or Argon2
    - Configure work factor (cost parameter)
    - Store hash + salt together in DB

Step 5 — Verification:
    - Retrieve stored salt & hash
    - Append/prepend salt to submitted password
    - Hash using same work factor
    - Compare securely (constant-time comparison)

Step 6 — Protection Against Attacks:
    - Rate limit login attempts
    - Implement account lockouts after multiple failed attempts
    - Monitor for suspicious activity

Step 7 — Future-Proofing:
    - Periodically re-hash with stronger work factor as hardware improves
    - Avoid outdated hash algorithms

Step 8 — Incident Handling:
    - If breach occurs, force password resets
    - Rotate salts and hashes

Optional (Best): 
    - Skip storing passwords entirely by integrating OAuth/OpenID Connect
```
