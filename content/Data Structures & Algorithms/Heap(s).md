#algo #memory
In Computer Science, the term **"Heap"** can refer to two completely unrelated concepts. 

| Phrase                       | Meaning                        |
| :--------------------------- | :----------------------------- |
| *"It goes on the heap"*      | **Memory** (RAM)               |
| *"Implement a generic heap"* | **Data Structure** (Algorithm) |

---
## 1. The Memory Heap (Systems & OS)
**Context:** "Allocated on the heap," `malloc`, `new`, "Heap Overflow."

The **Heap** is a region of a process's memory reserved for **Dynamic Allocation**. unlike the [[Stack(s)]], which is managed automatically by the CPU (via the stack pointer), the Heap is managed manually by the programmer (in C/C++) or the [[Garbage Collection|Garbage Collector]] (in Java/Python/Go).

- **Indefinite.** Data persists until explicitly freed.
- **Slower** than the Stack (requires pointer dereferencing and potential cache misses).
- **Mechanism:** When you call `malloc(size)`, the allocator searches a list of free blocks to find a suitable chunk.
- **Key Risks:**
    - **Memory Leaks:** Forgetting to `free()`.
    - **Fragmentation:** Frequent allocation/deallocation leaving "holes" in memory.
    - **Use-After-Free:** Accessing memory after it has been returned to the OS.
**Visual of Process Memory:**
```text
High Address  |------------------|
              |       Stack      |  <- Grows Down
              |         |        |
              |         v        |
              |..................|
              |         ^        |
              |         |        |
              |       Heap       |  <- Grows Up
              |------------------|
              |    BSS / Data    |  (Global Variables)
              |------------------|
              |       Text       |  (Code Instructions)
Low Address   |------------------|
```

---
## 2. The Data Structure (Algorithms)
**Context:** "Min-Heap," "Max-Heap," "Heapsort," "Priority Queue."

A **Heap** is a specialized **Tree-based** data structure that satisfies the **Heap Property**. It is almost always implemented as an array, not using pointers.

- **Structure:** A complete [[Binary Tree]].
- **The Heap Property:**
    - **Max-Heap:** Parent nodes are always $\ge$ children. Root is the largest.
    - **Min-Heap:** Parent nodes are always $\le$ children. Root is the smallest.
- **Time Complexity:**
    - **Find Max/Min:** $O(1)$ (It's always at the root).
    - **Insert/Delete:** $O(\log n)$ (Requires "bubbling" nodes up or down).
- **Use Cases:**
    - **[[Priority Queue|Priority Queues]]:** (e.g., The [[Linux Process Scheduler]] uses a [[Red/Black Trees|Red-Black tree]] now, but historically heaps were common for simple scheduling).
    - **[[Heapsort]]:** An $O(n \log n)$ sorting algorithm that sorts in-place.
    - **Graph Algorithms:** [[Dijkstra's Algorithm|Dijkstra's Shortest Path]] and [[Prim's Algorithm|Prim's MST algorithm]].

---
