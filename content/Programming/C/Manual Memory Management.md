#systems #memory
**Manual Memory Management** is the defining characteristic of C. Unlike languages with [[Garbage Collection]] (Java, Python) or Ownership models ([[Rust]]), C places the burden of memory life-cycle entirely on the programmer.

- [[Memory Management Strategies (languages)]]

#### The [[Stack(s)]] vs. The [[Heap(s)]]
- **Stack:** Automatic. Variables declared inside functions (`int x;`) live here. They vanish when the function returns.
- **Heap:** Manual. Memory requested at runtime. Persists until explicitly freed.

---
#### The Standard API (`<stdlib.h>`)

1.  **`malloc(size_t size)`**
    - Allocates `size` bytes of uninitialized memory.
    - Returns a `void*` pointer to the first byte, or `NULL` if allocation fails.
    - *Usage:* `int *arr = malloc(10 * sizeof(int));`

2.  **`calloc(size_t num, size_t size)`**
    - Allocates space for an array of `num` objects of `size`.
    - **Crucial Difference:** It initializes all bytes to **zero**.
    - *Usage:* `struct Node *p = calloc(1, sizeof(struct Node));`

3.  **`realloc(void *ptr, size_t new_size)`**
    - Resizes a previously allocated block.
    - *Behavior:* Can expand in place (if space allows) or move the data to a new location.
    - *Risk:* If it moves, the old pointer is invalid.

4.  **`free(void *ptr)`**
    - Returns the memory to the operating system.
    - *Rule:* Every `malloc` must have exactly one corresponding `free`.

---
#### Critical Errors

> [!DANGER] 1. Memory Leaks
> Allocating memory but losing the pointer before freeing it. The memory remains "occupied" until the program terminates.
> ```c
> void leak() {
>     int *p = malloc(100);
>     return; // Error: 'p' goes out of scope, but the 100 bytes are still held.
> }
> ```

> [!DANGER] 2. Double Free
> Calling `free()` twice on the same pointer. This corrupts the allocator's internal structures (the "free list") and causes security vulnerabilities.
> ```c
> free(ptr);
> free(ptr); // CRASH or Exploit
> ```

> [!DANGER] 3. Use-After-Free (Dangling Pointer)
> Accessing a pointer after it has been freed.
> ```c
> char *msg = malloc(10);
> free(msg);
> strcpy(msg, "Hello"); // Undefined Behavior (and major security risk)
> ```

---
#### Best Practice
> [!TIP]
> 1.  **Always check for NULL:** `malloc` returns `NULL` if the system is out of memory (OOM).
> 2.  **Set to NULL after free:**
>     ```c
>     free(ptr);
>     ptr = NULL; // Safe. free(NULL) does nothing.
>     ```
> 3.  Always verify your code with [[Valgrind]] 

