Video Resources:
https://www.youtube.com/watch?v=REStjp3sP4s



![[Pasted image 20260430114906.png|298]]
source
https://en.wikipedia.org/wiki/File:Caesar_cipher_left_shift_of_3.svg


![[Pasted image 20260430115016.png|537]]

```plaintext
Plaintext:  THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG
Ciphertext: QEB NRFZH YOLTK CLU GRJMP LSBO QEB IXWV ALD
```

### Math formula for encoding 

![[Pasted image 20260430214643.png|323]]

### Python Implementation

```python
char:str = chr((ord(letter) - 97 + n) % 26 + 97)
```

### The Formula: $(x + n) \pmod{26}$

> In math, if you want to wrap a number around a range, you use the **Modulo operator (%)**. To use it for the alphabet, we have to temporarily map 'a'-'z' (which are ASCII 97-122) to the numbers **0-25**.

### Breaking down the code:

`chr((ord(char) + shift - 97) % 26 + 97)`

1. **`ord(char) - 97`**: This converts the ASCII value to a **0-indexed position**.
    
    - Example: If `char` is 'a' (97), $97 - 97 = \mathbf{0}$.
    - Example: If `char` is 'z' (122), $122 - 97 = \mathbf{25}$.
	
2. **`+ shift`**: This applies the actual rotation.
    
3. **`% 26`**: This is the "magic." If the new value is 26 or higher, it wraps it back to 0.
    
    - Example: If you are at 'z' (25) and shift by 1, you get 26. $26 \pmod{26} = \mathbf{0}$ (which is 'a').
    
4. **`+ 97`**: This converts the 0-indexed number **back into the ASCII range** for lowercase letters.
    
5. **`chr(...)`**: Finally, this converts that ASCII number back into a string character.


---
