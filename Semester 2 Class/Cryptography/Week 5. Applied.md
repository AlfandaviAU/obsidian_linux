1. key exchange, encrypt/decrypt, digital signatures
2. requirements
	1. one of two key must kept secret
	2. its impractical to decipher the message, without knowing the private key
3. trapdoor
	1. its easy to encrypt
	2. its hard to decrypt without knowing the private key
	3. its easy to decrypt with private key
	4. rsa is usually trapdoor, but it depends on key length (short -> easy)
4. why rsa ![[Pasted image 20250828131322.png | 100]]
	1. because, we want d to be integer

```sagemath
p = random_prime(2**512,2**512)
q = random_prime(2**512,2**512)

n = p * q
phi = (p-1)*(q-1)
e = 65537

print(gcd(e,phi))
d = inverse_mod(e,phi)
d


m = 288345945862291409139878602752136823616575384556045987668956997481864923804
enc = power_mod(m,e,n)
print(enc)

m1 = power_mod(enc,d,n)
print(m1)

print(m1==m)
```
