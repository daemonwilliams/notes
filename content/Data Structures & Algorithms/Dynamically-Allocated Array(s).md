A **Dynamically Allocated Array** is an array whose size is determined at *runtime* rather than *compile time*. Unlike standard (static) arrays which live on the **[[Stack(s)]]**, dynamic arrays live on the **[[Heap(s)]]**. 

This is the foundational concept behind high-level structures like `std::vector` in C++, `ArrayList` in Java, or `Vec` in Rust.
**Related:** [[Basic Array(s)]], [[Time Complexity]]

---
#### Core Concepts
In C/C++, we manage this manually using **[[Pointers and Memory|Pointers]]**. The OS gives us a block of memory, and it is our responsibility to manage its life-cycle.

**Key Operations:**
1.  **Allocation (`malloc`):** Request a contiguous block of $N$ bytes.
    - *Risk:* If the [[Heap(s)]] is full, this returns `NULL`. Always check!
2.  **Resizing (`realloc`):** Change the size of the block.
    - *Under the Hood:* If the adjacent memory is free, the OS extends the block ($O(1)$). If not, it allocates a new block, copies all data over, and frees the old block ($O(n)$).
3.  **Freeing (`free`):** Return the memory to the OS.
    - *Risk:* Forgetting this causes a [[Memory Leak]].

---
#### Time Complexity

| Operation | Complexity | Notes |
| :--- | :--- | :--- |
| **Access** | $O(1)$ | Same as static arrays (pointer arithmetic). |
| **Append (Amortized)** | $O(1)$ | If capacity exists. |
| **Resize** | $O(n)$ | Requires copying the entire array to a new address. |
| **Insertion/Deletion** | $O(n)$ | Shifting elements is still required. |

---
#### Pros & Cons

| Feature | Dynamic Array (Heap) | Static Array (Stack) |
| :--- | :--- | :--- |
| **Size** | Mutable (can grow/shrink) | Fixed at compile time |
| **Lifetime** | Manual (`free`) | Automatic (Scope-based) |
| **Performance** | Slower (Indirection + Cache misses) | Faster (Hot cache) |
| **Safety** | High Risk (Leaks, Dangling Pointers) | Low Risk |

---
