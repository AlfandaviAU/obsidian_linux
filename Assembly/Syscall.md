[Syscall List](https://filippo.io/linux-syscall-table/)

| Description                 | 64-bit Register | 8-bit Register |
| --------------------------- | --------------- | -------------- |
| Syscall Number/Return value | `rax`           | `al`           |
| Callee Saved                | `rbx`           | `bl`           |
| 1st arg                     | `rdi`           | `dil`          |
| 2nd arg                     | `rsi`           | `sil`          |
| 3rd arg                     | `rdx`           | `dl`           |
| 4th arg                     | `rcx`           | `cl`           |
| 5th arg                     | `r8`            | `r8b`          |
| 6th arg                     | `r9`            | `r9b`          |
rax bakalan nyimpen syscall number, dan nanti hasil dari syscall akan ditaruh di rax

misalkan kita mau write

**ssize_t write(int** _fd_**, const void** _buf_**[.**_count_**], size_t** _count_**);**

disini kita perlu 3 parameter
1. fd
2. buf
3. count

maka
1. rdi = 1 -> stdout
2. rsi = "Some text" -> Pointer ke string ini
	1. jangan lupa dikasi 0x0a buat newline
3. rdx = 10 -> Panjang text yang mau di print + newline

![[Pasted image 20250818222717.png | 400]]