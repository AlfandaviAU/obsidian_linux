- exploit and mitigation


| Higher
|
| ID
| STR
| Name -> Name[0] < Name[1]
| DI
|
|
| Lower


<mark style="background: #FF5582A6;">retrun address always ebp + 4</mark>

![[Pasted image 20250811140901.png]]


![[Pasted image 20250813182243.png]]

![[Pasted image 20250813182233.png]]

![[Pasted image 20250813190631.png]]

ptr stored on stack, and it points to heap ptr[0] and ptr[1]
##### Disable randomization
	sudo sysctl -w kernel.randomize_va_space=0

#### Install GCC Multilib
	sudo apt-get install gcc-multilib 


#### Compile GCC
	gcc -m32 -fno-stack-protector -z execstack -g -o example example.c


#### Load Program GDB
	gdb example

#### Set Breakpoints
![[Pasted image 20250813184402.png]]


0x565561e7


