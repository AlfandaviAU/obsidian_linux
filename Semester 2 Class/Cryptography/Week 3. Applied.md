1. 1, n(n-1)/2
	- high number of keys used for high number of peer -> make symmetric cipher not feasible
	- but secure enough, and efficient
2. Attack analytics, lower (powerful)

| Types | Known to Cryptanalyst                                                                 |
| ----- | ------------------------------------------------------------------------------------- |
| COA   | 1. Know some ciphertexts                                                              |
| KPA   | 1. No control over plaintext or ciphertext<br>2. Know some plaintext-ciphertext pairs |
| CPA   | 1. Encryption Algorithm<br>2. Key<br>3. Can choose Plaintext, get ciphertext          |
| CCA   | 1. Encryption Algorithm<br>2. Key<br>3. Can choose ciphertext, get plaintext          |
| CTA   | 1. Encryption Algorithm<br>2. Key<br>3. {(P1,C1),(P2,C2)....}                         |
3. ECB and CBC
	1. P2
		1. On Encryption : C2 on ECB will not affected, but CBC will be affected, until rest -> chaining 
		2. On Decryption : P2 on ECB will not affected, but CBC affected, but P3 not affected
		3. ECB using same key (not using IV), no connection between the blocks, but cannot hide the pattern, if 2 block exactly the same, then the ciphertext same, no dependence between blocks
		4. CBC dependent between blocks, init using IV, and result in being used in the next blocks, cannot be processed in parallel
	2. on ECB will affected only on that block, but on CBC all remaining will be affected
	3. enc => no, dec => yes
	4. error only on plaintext current, and next plaintext
	5. <mark style="background: #FF5582A6;">homework, if other mode happen, hows it</mark>
4. 
	1. 
		1. ae8059cbc43e9bbe588d46589b30e51e
		2. ae8059cbc43e9bbef40978e810a2d21a
	2. 
		1. c623565ce459fa2f1ae1c4ed85a592ea
		2. c623565ce459fa2fdd0e9a64381a230b
	3. 

5. nomer enam
	1. (20^20 / 2^3)*0,5 + 2
	2. 2^56 * 2,5 * 10^-6
