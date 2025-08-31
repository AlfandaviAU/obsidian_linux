
| Pros                            | Cons                     |
| ------------------------------- | ------------------------ |
| Execution Efficiency            | Manual Memory Management |
| Require minimal runtime support | Prone to memory errors   |
| Low-level memory management     | High security risk       |
- C is a lower-level programming language
- Code -> Compiler -> Binary code (executable)

#### Assembly Code
- Arithmetic : add, sub, inc, mul, div
- Logical : and, or, not, xor, nop
- Control flow : 
	- Comparison : cmp, test
	- Jumps : 
		- Unconditional : jmp
		- Conditional : jle, je, jge
	- Function call : call, ret
- Copying data : mov
- Stack manipulation : push, pop
- [reference](https://www.cs.virginia.edu/~evans/cs216/guides/x86.html)
- learn more about x86 assembly

#### Memory Layout
- All programs are stored in memory
- Low address : 0x00000000, High address : 0xffffffff
- Using virtual memory, each cell is 32 bits -> because we use x86 architecture
![[Pasted image 20250804132312.png | 300]]

1. Code segment : program code, and constants
2. Data segment : init global and static variables
3. BSS (Block Started by Symbol) : unitialised global and static variables
4. Heap segment : dynamic program data (malloc)
5. Stack segment : Function local variables, arguments, and context
#### Registers
![[Pasted image 20250804132550.png | 400]]
- Computer accessible (Fastest) small amount of storage (in processor)
- ESP -> Stack Pointer (always points to frontier of the stack)
- EBP -> Base Pointer / Frame Pointer


#### C Data Types
- Primitive data types : int, short, float, char
	- Occupy specific memory
- Derived data types : arrays, strings, pointers
	- Only <mark style="background: #FF5582A6;">save the reference</mark> to the value, not the exact value
	- Vary in size
- User defined data types : struct

#### Programming in C
- addressof (`&`) and dereference (`*`) operator
```
int a = 5003;
int *addr = &a;
*addr = 3005;
```
a will be 3005, because dereference changed it


```c
//
// Created by davi on 8/4/25.
//
#include <stdio.h>
#include <stdlib.h>

int main()
{
    // create a signed short
    signed short a;

    // assign -5003 to it
    a = -5003;
    // print the size of the short value
    printf("%hd, size : %zu", a, sizeof(a));
}

```
we got 2, since short -> 2 bytes (-2^16 until 2^16)

```c
char arr[3] = {'a','b','c'};
char *str = "abc";
char str[] = "abc";
```
string would be represented as char of reference