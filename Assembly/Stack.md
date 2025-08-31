- Segment in the memory to store data
- <mark style="background: #FF5582A6;">rsp</mark> -> top stack pointer
- <mark style="background: #FFB86CA6;">rbp</mark> -> base stack pointer

```
push rax -> copy rax address to stack

pop rax -> remove item from top stack into rax
```

pakai stack karena ketika syscall, dia pakai register, maka disimpan sementara di stack biar ga hilang, nanti dibalikin

```
push rax
push rbx

pop rbx
pop rax
```
