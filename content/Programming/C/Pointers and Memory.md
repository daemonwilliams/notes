#systems #memory
**Pointers** are variables that store memory addresses rather than values. They are the primary tool for Systems Programming in C, allowing direct manipulation of memory, arrays, and hardware.

#### Basic Syntax
*   `int *p;` : Declares a pointer `p` that *points to* an integer.
*   `&x` : **Address-of Operator**. Returns the memory address of variable `x`.
*   `*p` : **Dereference Operator**. Accesses the value stored at the address `p`.

```c
int x = 10;
int *p = &x;  // p holds the address of x
int y = *p;   // y gets the value 10 (dereferencing p)
*p = 20;      // x is now 20
```

---
#### Pointer Arithmetic
Adding `1` to a pointer increases the address by `sizeof(type)`.
- `char *c = 0x1000; c++;` -> `0x1001` (1 byte)
- `int *i = 0x1000; i++;` -> `0x1004` (4 bytes on 32-bit/64-bit usually)

This is how **Arrays** work in C. `arr[i]` is syntactic sugar for `*(arr + i)`.

---
#### The Generic Pointer (`void*`)
A `void*` is a pointer to *something*, but we don't know the type.
- **Pros:** Can hold any pointer type (used in `malloc`, `qsort`, generic data structures).
- **Cons:** Cannot be dereferenced directly (must cast first). Cannot perform arithmetic (size unknown).

```c
void* generic_ptr = &x;
int* int_ptr = (int*)generic_ptr; // Cast back to int* to use
```

---
#### Common Pitfalls
> [!DANGER]
> 1.  **Segmentation Fault (Segfault):** Accessing memory you don't own (e.g., dereferencing `NULL` or a dangling pointer).
> 2.  **Memory Leaks:** Allocating memory with `malloc` (see [[Manual Memory Management]]) and losing the pointer before calling `free`.
> 3.  **Dangling Pointers:** Using a pointer after the memory it points to has been freed.

--
