Name : M. Alfandavi Aryo Utomo
Student ID : 35595108





#### 4. Format String Vulnerability
- We got a program that had format string vulnerability, when we look at the code, we can see that theres no input validation or any limitations that prohibit us to insert special symbols (%x and %s), so we can proceed to exploit the program

- Our goal is changing the secret from FIT5003 -> QITq003
	- My student ID = 35595108 % 26 = 16 -> Q

- First thing first, we compile the program
```
gcc -m32 -o format_string format_string.c
```

- And we run the program
![[Pasted image 20250910143611.png | 400]]
The program ask us to insert a string, so when we input multiple %x's...
![[Pasted image 20250910143655.png | 500]]
it does print out a lot of important memory contents, and when we input 123, and trying to print it again, it does return like this 
![[Pasted image 20250910160201.png | 500]]
notice how 8th argument changed, from 3e8 (1000) into 7b (123), so we can see that 8th argument does hold our int_input variable
![[Pasted image 20250910160356.png | 500]]
so when we want to change the secret, we can just change the value pointed by our heap (started from 9th arg), and move by 4byte per char

our initial secret is FIT5003 -> QITq003 so we need to change first and fourth one, distance between them is 3 byte -> 12 bits, so we craft a payload such we can change them, lets do it like below

![[Pasted image 20250910161051.png | 500]]
our 9th argument is 60f4c1a0 (first address of secret or secret[0]), since we know our secret is using sizeof(int), we can just get our secret[3] address  = 60F4C1A0 + 12bits = 1626653100 or 60F4C1AC

so we can feed 1626653100 into our program as 2nd input, and for the last input, we want to directly change our secret, because we already got 2 pointers at our address
![[Pasted image 20250910161135.png | 500]]

we want to write 81 times character into 9th argument in our stack, and 31 times character into 8th argument in our stack, why these numbers?
1. 81 since in ascii 81th is Q
2. 31 since in ascii 113th is q then 113 - 81(from Q) - 1(from ;) = 31
```
%.81x%9$hhn;%.31x%8$hhn
```
and when we enter that input
![[Pasted image 20250910161610.png | 500]]
The secret is changed as we expected
