

```gef
info functions
```

```gef
info variables
```

```gef
disas _start
```
![[Pasted image 20250818160907.png | 500]]
	di run dulu, terus nanti dia bisa set breakpoint

```
b _start
```
artinya breakpoint di fungsi start, kalau mau lebih detail line

```
b *_start+5
```
atau by memory address

```
b *0x40100a
```

examine, 4 next instruction, i (format), g (size) 8bytes
```
x/4ig $rip
```

![[Pasted image 20250818162710.png | 500]]
ngambil isi variabel
```
x/s <memory_address>
```
![[Pasted image 20250818163220.png | 500]]
tapi jangan lupa set breakpoint dulu

kalau kita pingin dapet instruksi dalam bentuk hex
```
x/wx <memory_address>
```
![[Pasted image 20250818163526.png | 500]]
konversinya jadi b8 01 00 00 -> mov eax, 0x1
sama kaya diatasnya

```
si
```
buat iterasi ke next step, satu-satu <mark style="background: #FF5582A6;">si</mark>, tapi kalau <mark style="background: #FF5582A6;">s</mark>, dia langsung ke akhir function

```
patch string <memory_address> <desired_string>
```
buat ganti string di memory itu, tapi kaya digabung didepannya, jadi `ayamgoreng` + `nasi` -> `nasigoreng`

`\x0a` -> untuk nambahin newline

patch string dulu, terus ganti variabel registernya
```
set $rdx=<size_in_hex>
```
nanti dia bisa nampilin sesuai jumlah yang diinginkan


kalau mau nampilin dalam bentuk string
```
p/d $rbx
```
![[Pasted image 20250818205224.png | 300]]
