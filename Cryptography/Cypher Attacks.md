1. Cryptanalytic attack
	1. Ciphertext only attack
		1. Attacker only know ciphertext (weakest)
	2. Known plaintext attack
	3. Chosen plaintext attack
	4. Chosen ciphertext attack
	5. Chosen text attack
2. Brute-force attack

| Attack Type              | Attacker Can Choose            | Description                            |
| ------------------------ | ------------------------------ | -------------------------------------- |
| Chosen Text Attack       | Plaintexts **and** Ciphertexts | Most powerful; can encrypt and decrypt |
| Chosen Ciphertext Attack | Ciphertexts                    | Submit ciphertexts, get plaintexts     |
| Chosen Plaintext Attack  | Plaintexts                     | Submit plaintexts, get ciphertexts     |
| Known Plaintext Attack   | Nothing (just observes pairs)  | Knows some plaintext–ciphertext pairs  |
| Ciphertext Only Attack   | Nothing (only ciphertexts)     | Weakest; only has encrypted messages   |
![[Pasted image 20250805165732.png]]