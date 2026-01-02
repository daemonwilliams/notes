A **Multi-Dimensional Array** is an array of arrays. The most common form is the **2D Array** (Matrix), used for grids, images, and linear algebra.

---
#### Memory Layout: The "Linear" Reality
There is no such thing as a "grid" in hardware. RAM is a linear strip of bytes, like a massive 1-D tape.

To store a 2-D grid, we must map it to this 1-D line. There are two ways to do this:
##### 1. Row-Major Order (C/C++, Rust)
We store the **first row** completely, then the **second row**, and so on.
- **Formula:** `Address(Row, Col) = Base + ((Row * Width) + Col) * ElementSize`

**Visual:**
Grid:
```
[ A, B ]
[ C, D ]
```
RAM (Linear):
```
| A | B | C | D |
```

##### 2. Column-Major Order (Fortran, MATLAB)
We store the **first column** completely, then the second.
RAM (Linear):
```
| A | C | B | D |
```

---
#### Cache Locality & Performance (Critical!)
Because of **Row-Major Order** in C, iterating "Row by Row" is **fast**, while iterating "Column by Column" is **slow**.

**Fast (Sequential Access = [[Cache]] Hits):**
```c
// Good! We read A, B, C, D...
for(int r=0; r<ROWS; r++) {
    for(int c=0; c<COLS; c++) {
        sum += matrix[r][c];
    }
}
```

**Slow (Strided Access = Cache Misses):**
```c
// Bad! We jump memory addresses wildly.
for(int c=0; c<COLS; c++) {
    for(int r=0; r<ROWS; r++) {
        sum += matrix[r][c];
    }
}
```

---
## 2-D Arrays on the Stack vs. Heap

**1. Stack (Static):**
```c
int matrix[10][10]; // Contiguous block of 100 ints.

```

**2. Heap (Dynamic) - The "Array of Pointers" Trap:**
```c
int **matrix = malloc(rows * sizeof(int*));
for(int i=0; i<rows; i++) matrix[i] = malloc(cols * sizeof(int));
```
- **Problem:** Each row is allocated separately. They might be scattered all over the RAM. *(Poor Cache Locality)*
- **Solution:** Allocate one massive 1-D block (`rows * cols`) and use the math formula to access it as 2-D.

---

