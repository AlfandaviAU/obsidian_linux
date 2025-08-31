#### Malloc
1. Allocate memory in given size
2. Doesnt intialize memory (contain garbage values)
3. Return pointer to first byte

```c
int *p = (int*) malloc(5 * sizeof(int)); 
```


##### Calloc
1. Same like Malloc but initialize all elemenets to 0

```c
int *p = (int*) calloc(5, sizeof(int));
```

#### Realloc
1. Resize previously allocated memory block
2. If new size bigger -> extra memory allocated (new part is garbage)
3. If new size smaller -> Memory reduced
```c
int *p = (int*) malloc(3 * sizeof(int));
for (int i = 0; i < 3; i++) p[i] = i+1;   // p = {1,2,3}

p = (int*) realloc(p, 6 * sizeof(int));   // resize to 6 integers
for (int i = 3; i < 6; i++) p[i] = i+1;   // add more values

// Now p = {1,2,3,4,5,6}

```

|Feature|`malloc`|`calloc`|`realloc`|
|---|---|---|---|
|**Purpose**|Allocate memory block|Allocate memory & initialize|Resize existing block|
|**Initialization**|Garbage values|All zeros|Preserves old data, new part garbage|
|**Parameters**|`(size)` in bytes|`(num, size)` elements|`(ptr, new_size)`|
|**Return**|`void*`|`void*`|`void*`|
|**Typical use**|Simple allocation|Arrays needing zero-init|Expanding/shrinking arrays|
