#systems #memory #hardware
**The Memory Hierarchy** illustrates the trade-off between speed, size, and cost. Faster memory is expensive and small; slower memory is cheap and large.

---
#### The Pyramid of Latency

| Level | Component             | Size    | Latency (Approx Cycles) | Analogy                    |
| :---- | :-------------------- | :------ | :---------------------- | :------------------------- |
| **1** | **Registers**         | < 1 KB  | 1 cycle                 | The thought in your brain. |
| **2** | **L1 Cache**          | ~64 KB  | 4 cycles                | Paper on your desk.        |
| **3** | **L2 Cache**          | ~512 KB | 10 cycles               | Book on the shelf.         |
| **4** | **L3 Cache**          | ~8 MB   | 40 cycles               | Book in the next room.     |
| **5** | **Main Memory (RAM)** | 16 GB+  | **100+ cycles**         | Library down the street.   |
| **6** | **Disk (SSD/HDD)**    | TBs     | **Millions of cycles**  | Ordering from Amazon.      |

---
#### Cache & Locality
The [[Central Processing Unit(s) (CPU)]] is incredibly fast, but it spends most of its time waiting for [[Random Access Memory (RAM)]]. To fix this, we use [[Cache Memory]].

**Principle of Locality:**
1.  **Temporal Locality:** If you access data `x`, you will likely access it again soon. (Cache keeps `x`).
2.  **Spatial Locality:** If you access data `x`, you will likely access its *neighbors* (`x+1`) soon. (Cache loads a whole "Cache Line" of 64 bytes).

**Impact on Data Structures:**
- **[[Data Structures & Algorithms/Basic Array(s)|Arrays]]:** High Spatial Locality. Data is contiguous. The CPU loads the whole chunk into L1 Cache. Very fast iteration.
- **[[Data Structures & Algorithms/Linked List(s)|Linked Lists]]:** Poor Spatial Locality. Nodes are scattered on the [[Heap(s)]]. Following pointers causes frequent **Cache Misses** (fetching from slow RAM).

---
#### Virtual Memory 
Programs do not access physical RAM directly. They use **Virtual Addresses**.
- [[Memory Management Unit (MMU)]]:** Hardware that translates Virtual -> Physical addresses.
- [[Paging]] The OS moves chunks of memory (pages) between RAM and Disk (Swap). If you access a page on Disk, it's a **Page Fault** (massive performance penalty).
