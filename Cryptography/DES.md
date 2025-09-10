1. based on feistel structure
	![[Pasted image 20250831212344.png | 300]]
2. block size 64 bits
3. key size 56 bits
	1. 8 parity bits stripped

initial permutation -> reorder the bits of the input, based on IP table
inside each round :
1. plaintext splitted into 32 bit halves (Li and Ri)


![[Pasted image 20250831212613.png | 400]]
#### Round Function
1. Expansion E
	1. convert 32 bits -> 48 bits
	2. using E bit-selection table
	![[Pasted image 20250831212729.png | 400]]
2. XOR with round key
	1. 48 bits xor with 48 bits
	2. round keys derived from DES key schedule
3. S-box substitution
	1. 48 bits input, because we only got8 boxes, we only take 6 from each boxes, and returning 4 from each boxed, and combine resulting in 32 bits output
	![[Pasted image 20250831213039.png | 400]]
	row : 11, and column : 0010 -> 3 and 2 -> 08
4. Permutation
	1. bitwise permutation
	![[Pasted image 20250831213254.png | 400]]

#### DES IP Inverse
![[Pasted image 20250831213358.png | 400]]
we want to ensure the enc, and dec are symmetric (because in the begining we use IP also)


#### DES Subkey Generation
![[Pasted image 20250831213520.png | 400]]
![[Pasted image 20250901110155.png | 400]]


#### DES Security
- major issue : key length too small
- we solve it by 3DES
![[Pasted image 20250831213803.png | 400]]
- we use des algo 3 times, and 3 different keys (EDE)
- because backward compability, if older system cant do 3DES, we can just use ED use same key -> cancel out each other, and E for encrypt