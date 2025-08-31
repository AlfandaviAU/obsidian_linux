![[Pasted image 20250813211527.png | 300]]
- rax 1 : linux `write` syscall
- rdi 1 : stdout
- rsi message : pointer to buffer to write
- rdx length : write on stdout how many bytes
- syscall : trigger the system call

- rax 60 : linux `exit` syscall
- rdi 0 : exit code 0
- syscall : trigger the system call

```
nasm -f elf64 helloWorld.s
```
```
ld -o helloWorld helloWorld.o
```
```
./helloWorld
```

##### Disassembling
1. whole program
```
objdump -M intel -d <program_name>
```

2. specific section
```
objdump -sj .data <program_name>
```





![[Pasted image 20250813214928.png]]![[Pasted image 20250813214958.png]]