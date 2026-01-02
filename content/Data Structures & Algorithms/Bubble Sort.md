**Bubble Sort** is the simplest sorting algorithm to understand, but one of the least efficient. It works by repeatedly stepping through the list, comparing adjacent elements and **swapping** them if they are in the wrong order.

The pass through the list is repeated until the list is sorted. The algorithm gets its name because smaller elements "bubble" to the top of the list (start of the array) while larger elements "sink" to the bottom.

---
#### The Algorithm
1.  Start at the beginning of the array.
2.  Compare the first two elements ($i$ and $i+1$).
3.  If $arr[i] > arr[i+1]$, swap them.
4.  Move to the next pair.
5.  Repeat this for the entire array.
6.  **Optimization:** If a full pass occurs without any swaps, the array is sorted, and we can stop early.

---
#### Time & Space Complexity
[[Time Complexity]]

| Metric          | Rating   | Reason                                                                                   |
| :-------------- | :------- | :--------------------------------------------------------------------------------------- |
| **Normal Case** | $O(n^2)$ | Nested loops. $n + (n-1) + ... + 1$.                                                     |
| **Best Case**   | $O(n)$   | **Only** if the `swapped` flag optimization is used **and** the array is already sorted. |
| **Space**       | $O(1)$   | **In-Place.** Requires only one temp variable for swapping.                              |
| **Stability**   | **Yes**  | Equal elements are never swapped, preserving original order.                             |

---
#### Implementation (C)
```c
#include <stdbool.h>
void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        bool swapped = false;
        // Last i elements are already in place
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                swapped = true;
            }
        }

        // OPTIMIZATION: If no two elements were swapped by inner loop,
        // then the array is sorted.
        if (!swapped) {
            break;
        }
    }
}
```

---
#### Why learn this?
If Bubble Sort is so slow, why do we study it?
1.  **Simplicity:** It is the easiest algorithm to implement from scratch without references.
2.  It illustrates the concept of $O(n^2)$ complexity perfectly.

**Reality Check:**
In production systems code (Linux Kernel, Embedded Systems, Game Engines), **you will almost never use Bubble Sort.**
- For small arrays ($n < 50$), **[[Insertion Sort]]** is usually faster because it has less overhead.
- For large arrays, **[[Quick Sort]]** or **[[Merge Sort]]** ($O(n \log n)$) are mandatory.

---
