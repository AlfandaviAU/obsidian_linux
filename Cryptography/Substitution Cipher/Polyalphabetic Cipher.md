- Use string to encrypt things
- Example : 
	- Vigenere cipher
	- Autokey cipher
	- One-time pad
		- using xor
##### One-time pad
In **One-Time Pad (OTP)**, **XOR happens when the cipher operates on binary data** — typically when the plaintext and key are **bytes** (not letters). This is the **bitwise XOR version** of OTP.

---

### 🧠 XOR-Based OTP – Binary Version

#### Let’s walk through an example:

#### 1. **Plaintext**: `A`

ASCII of `A` = **65** → binary = `01000001`

#### 2. **Key**: some random byte, say **X**

ASCII of `X` = **88** → binary = `01011000`

#### 3. **Encryption using XOR**:

```
Plaintext:  01000001   (A)
Key:        01011000   (X)
XOR result: 00011001   = 25 (→ ASCII = non-printable)
```

So the **ciphertext is the byte `00011001`**, which may not be printable.

---

### 🔓 Decryption using XOR again:

```
Ciphertext: 00011001
Key:        01011000
XOR again:  01000001 = 65 → A
```

That’s the magic of XOR:

```
A ⊕ B = C  ⇒  C ⊕ B = A
Let me know if you want to see a Python example too.```

So when using **OTP with XOR**, you typically:

- Represent plaintext and key as bytes (binary).
    
- Perform `cipher = plaintext ⊕ key`.
    
- Decrypt via `plaintext = cipher ⊕ key`.
    

---

### ✅ Summary

|OTP Method|Operation|Data Type|
|---|---|---|
|Letter-based|Modular addition (mod 26)|Characters (A-Z)|
|Bitwise OTP|XOR (⊕)|Binary/ASCII data|
