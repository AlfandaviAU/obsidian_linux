
#### MOV (Moving)
```
mov rax, 1
```
artinya rax = 1 dalam bentuk data


#### LEA (Load Effective Address)
```
lea rax, [rsp+5]
```
artinya rax = apa yang ditunjuk oleh [rsp+5]

```
xchg rax, rbx
```
artinya tukeran data, rax -> rbx dan rbx -> rax


kalau dia moving pointer value, misalkan
```
mov rax, rsp
```
dia bukan mindahin value isinya rsp ke rax, tapi mindahin pointernya (address) ke rax, kalau mau <mark style="background: #FF5582A6;">mindahin literal value</mark>, dia bisa pakai []
```
mov rax, [rsp]
```


![[Pasted image 20250818192753.png | 500]]
