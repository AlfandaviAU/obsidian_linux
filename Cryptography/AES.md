- Advance Encryption Standard
- 3DES slow in software, use 64 bit block size (small enough), larger size preferable
- Flexible key size : 128 bits, 192 bits, and 256 bits
- Rijndael algorithm
- Good enough for today needs

small block size -> 64 bits, if we got very long message -> need to have a lot of blocks -> need performance

128 bit -> 10 rounds
192 bit -> 12 rounds
256 bit -> 14 rounds

![[Pasted image 20250901105050.png | 300]]

#### Round Function

##### First N-1 Rounds
1. Byte Substitution (SubBytes)
2. Shift Rows
3. Mix Columns
4. Add Round Key

##### Final Round
1. Byte Substitution (SubBytes)
2. Shift Rows
3. Add Round Key

![[Pasted image 20250901105504.png]]
![[Pasted image 20250901105621.png]]
![[Pasted image 20250901105716.png]]
![[Pasted image 20250901105737.png]]
![[Pasted image 20250901105811.png]]