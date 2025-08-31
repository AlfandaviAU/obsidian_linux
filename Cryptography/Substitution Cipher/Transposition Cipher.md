- Permutation cipher
- rearrage the order of symbol, in the plaintext
- same freq distribution as original text
- example : 
	- rail fence cipher
	- row transposition cipher

#### Rail Fence Cipher

##### Encryption
1. choose the number of rails (lines)
2. write plaintext diagonally across the rails (top-left until bottom-right)
3. after reach bottom rail, write diagonally upwards until top rail
4. read the letter from each rail 

##### Decryption
1. Calculate the length of each rail (length of cipher text / number of rails)
2. Write ciphertext diagonally across the rails
3. until bottom, go up again
4. read the text

|     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| m   |     | e   |     | m   |     | a   |     | t   |     | r   |     | o   |     | a   |     | a   |     | t   |     |
|     | e   |     | t   |     | e   |     | f   |     | e   |     | t   |     | g   |     | p   |     | r   |     | y   |
C : memarthtgpryetefeteoaat


#### Row Transposition Cipher
##### Encryption
1. Choose key to determine column (n), and the order
2. Write letter of message, in rows and column
3. read column based on the key

##### Decyption
1. Determine number of column and row
2. Start writing based on row number
3. read it


