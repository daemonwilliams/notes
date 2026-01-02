#systems #memory
**Structs** (Structures) and **Unions** are mechanisms for creating custom data types. In Systems Programming, understanding their exact **memory layout** is critical for interacting with hardware protocols and binary file formats.

#### Structs (`struct`)
A way to group related variables of different types under one name.
```c
struct Point {
    int x;
    int y;
};
```
- **Memory:** Members are stored sequentially in memory (with potential gaps, see Padding).

#### Unions (`union`)
A data type where all members share the **same memory location**. The size of the union is the size of its largest member.
```c
union Data {
    int i;
    float f;
    char str[4];
};
```
- **Use Case:** low-level type punning (interpreting bits of a `float` as an `int`) or saving memory when variables are mutually exclusive.

---
#### Memory Alignment & Padding
The [[Central Processing Unit(s) (CPU)]] prefers to access memory at aligned addresses (e.g., 4-byte integers at addresses divisible by 4). To enforce this, compilers insert **Padding Bytes**.

**Example:**
```c
struct Bad {
    char c;   // 1 byte
    // 3 bytes PADDING inserted here
    int i;    // 4 bytes
};
// sizeof(struct Bad) = 8 bytes (not 5!)
```

**Packing:**
To force exact layout (e.g., for network headers), you must tell the compiler to stop padding.
```c
struct __attribute__((packed)) NetworkHeader {
    char id;
    int size;
};
// sizeof = 5 bytes (Performance penalty on some CPUs)
```

---
#### Bit Fields
C allows you to specify the exact number of **bits** a member uses. Crucial for hardware registers.
```c
struct Flags {
    unsigned int is_visible : 1; // Uses 1 bit
    unsigned int is_admin   : 1; // Uses 1 bit
    unsigned int reserved   : 30;
};
```

---
