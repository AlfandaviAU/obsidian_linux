#### Registers
- Built in CPU core, fastest type of memory
- 2 Type of Registers
	- Data Registers -> Storing syscall arguments
		- rax, rbx, rcx, rdx -> primary
		- r8, r9, r10 -> secondary
	- Pointer Registers 
		- rbp -> base stack pointer
		- rsp -> current stack pointer
		- rip -> instruction pointer

#### Sub-Registers
|Size in bits|Size in bytes|Name|Example|
|---|---|---|---|
|`16-bit`|`2 bytes`|the base name|`ax`|
|`8-bit`|`1 bytes`|base name and/or ends with `l`|`al`|
|`32-bit`|`4 bytes`|base name + starts with the `e` prefix|`eax`|
|`64-bit`|`8 bytes`|base name + starts with the `r` prefix|`rax`|

| Description                     | 64-bit Register | 32-bit Register | 16-bit Register | 8-bit Register |
| ------------------------------- | --------------- | --------------- | --------------- | -------------- |
| **Data/Arguments Registers**    |                 |                 |                 |                |
| Syscall Number/Return value     | `rax`           | `eax`           | `ax`            | `al`           |
| Callee Saved                    | `rbx`           | `ebx`           | `bx`            | `bl`           |
| 1st arg - Destination operand   | `rdi`           | `edi`           | `di`            | `dil`          |
| 2nd arg - Source operand        | `rsi`           | `esi`           | `si`            | `sil`          |
| 3rd arg                         | `rdx`           | `edx`           | `dx`            | `dl`           |
| 4th arg - Loop counter          | `rcx`           | `ecx`           | `cx`            | `cl`           |
| 5th arg                         | `r8`            | `r8d`           | `r8w`           | `r8b`          |
| 6th arg                         | `r9`            | `r9d`           | `r9w`           | `r9b`          |
| **Pointer Registers**           |                 |                 |                 |                |
| Base Stack Pointer              | `rbp`           | `ebp`           | `bp`            | `bpl`          |
| Current/Top Stack Pointer       | `rsp`           | `esp`           | `sp`            | `spl`          |
| Instruction Pointer 'call only' | `rip`           | `eip`           | `ip`            | `ipl`          |
#### Little Endian vs Big Endian
- Little Endian using `right-to-left`
- easier to do arithmetic

#### Data Type
| Component           | Length            | Example              |
| ------------------- | ----------------- | -------------------- |
| byte                | 8 bits            | `0xab`               |
| word                | 16 bits - 2 bytes | `0xabcd`             |
| double word (dword) | 32 bits - 4 bytes | `0xabcdef12`         |
| quad word (qword)   | 64 bits - 8 bytes | `0xabcdef1234567890` |

| Sub-register | Data Type |
| ------------ | --------- |
| al           | `byte`    |
| ax           | `word`    |
| eax          | `dword`   |
| rax          | `qword`   |
