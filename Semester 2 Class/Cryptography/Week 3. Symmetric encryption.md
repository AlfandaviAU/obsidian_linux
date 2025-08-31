- private key encryption
![[Pasted image 20250812133342.png]]
- using the same key to enc, and dec
- use KDC as 3rd party to share the same key
- Enc(R,P) and Dec(R,C) -> P

##### Brute Force Attack
1. try any possibilities of key -> to get plaintext
2. ![[Pasted image 20250812133649.png | 400]]
3. more key -> longer time to get plaintext


#### Stream Ciphers
![[Pasted image 20250812133806.png | 400]]
- process element bit by bit
- produce one element at a time
- example : RC4 and rabbit
- used in one-time pad 
- pseudo-random cipher
![[Pasted image 20250812134031.png | 400]]
1. use seed (small key) to generate long key stream
2. XOR keystream with the message
3. Decryption same with enc

![[Pasted image 20250812134257.png | 500]]
- seed should be long enough and random (128-256 bits) 2^128
-  KSG function hard to invert
	- KSG(IV,R) -> K
	- but K -/-> KSG(IV,R)
- k should be hidden
- we should use IV, since we can generate 3 different key streams using single key, instead of remembering 3 different key (without IV)
- IV can be randomed (128bit purely random)
![[Pasted image 20250812153412.png]]

#### Block Ciphers
- DES, AES