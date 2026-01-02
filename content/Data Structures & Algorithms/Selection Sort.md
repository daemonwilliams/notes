**Selection Sort** is a simple comparison-based sorting algorithm. It works by repeatedly **selecting** the smallest (or largest) element from the unsorted portion of the list and moving it to the sorted portion.

Unlike [[Bubble Sort]], which swaps constantly, Selection Sort only makes one swap per pass.

---
#### The Algorithm
The array is conceptually divided into two parts:
1.  **Sorted Sub-array:** The left end (initially empty).
2.  **Unsorted Sub-array:** The right end (initially the whole array).

**Steps:**
1.  Start at index $i = 0$.
2.  Search the entire unsorted sub-array ($i$ to $n-1$) to find the **minimum element**.
3.  Swap that minimum element with the element at index $i$.
4.  Increment $i$ (the sorted boundary moves one step right).
5.  Repeat until the array is sorted.

---
#### Complexity Analysis

| Metric             | Rating   | Reason                                                                                                     |
| :----------------- | :------- | :--------------------------------------------------------------------------------------------------------- |
| **Time**           | $O(n^2)$ | It **always** scans the remaining array to find the min, even if the array is already sorted.              |
| **Space**          | $O(1)$   | **In-Place.** Requires only one temp variable for swapping.                                                |
| **Stability**      | **No**   | Swapping elements over long distances can change the relative order of equal items.                        |
| **Writes(swap())** | $O(n)$   | **Key Feature.** It performs the minimum number of swaps of any basic sorting algorithm ($n-1$ swaps max). |

---
#### Implementation (C)

```c
void selectionSort(int arr[], int n) {
    // Move boundary of unsorted subarray one by one
    for (int i = 0; i < n - 1; i++) {
      
        // Find the minimum element in unsorted array
        int min_idx = i;
        
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[min_idx]) {
                min_idx = j;
            }
        }
        
        // Swap the found minimum element with the first element
        // ONLY if the minimum is not already in place (micro-optimization)
        if (min_idx != i) {
            int temp = arr[i];
            arr[i] = arr[min_idx];
            arr[min_idx] = temp;
        }
    }
}
```

---
#### Use Case?
Selection Sort is generally slower than [[Insertion Sort]] and definitely slower than [[Quick Sort]]. However, it has one specific niche:

**Write-Heavy Constraints (Flash Memory)**
- In some embedded systems, **writing** to memory is much more expensive (in time or hardware lifespan) than **reading**.
- Selection Sort makes exactly **$O(n)$ writes.
- Bubble Sort and Insertion Sort can make up to $O(n^2)$ writes.

---

