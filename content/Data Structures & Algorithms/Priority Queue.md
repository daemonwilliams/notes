A **Priority Queue** is an Abstract Data Type (ADT) that operates like a regular [[Queue(s)]], but additionally, each element has a **priority** associated with it.

In a Priority Queue, an element with high priority is served before an element with low priority.

---
## Implementation
While you *can* implement a Priority Queue using an Array or a Linked List, it is inefficient. The standard implementation uses a **[[Binary Heap]]**.

| Implementation     | Enqueue              | Extract Max (Dequeue)  |
| :----------------- | :------------------- | :--------------------- |
| **Unsorted Array** | $O(1)$               | $O(n)$ (Must scan all) |
| **Sorted Array**   | $O(n)$ (Shift items) | $O(1)$                 |
| **Binary Heap**    | $O(\log n)$          | $O(\log n)$            |

The Heap provides the best balance, guaranteeing logarithmic performance for both operations.

---
## Use Case: Process Scheduling
The most famous use case is the Operating System's **Scheduler**.
- The CPU can only run one process at a time.
- There are hundreds of active processes (Browser, Music, System Services).
- The OS assigns each process a **priority** (e.g., "Real-time Audio" > "Background Update").
- The Scheduler uses a Priority Queue to decide which process gets the CPU next.

*Note: The Linux Kernel's Completely Fair Scheduler (CFS) actually uses a [[Red/Black Trees|Red-Black Tree]] to implement this priority queue for $O(\log n)$ fairness.*

---

