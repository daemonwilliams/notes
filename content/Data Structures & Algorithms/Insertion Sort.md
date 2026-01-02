**Insertion Sort** is a simple, intuitive sorting algorithm that builds the final sorted array (or list) one item at a time. It works similarly to how you might sort playing cards in your hand: you take a new card and insert it into its correct position among the cards you are already holding.

Insertion Sort is heavily used as the "base case" for high-performance hybrid algorithms because it is extremely efficient for **small datasets** (typically $n < 32$) and has excellent **cache locality**.

---
#### Time & Space Complexity

| Case        | Time Complexity | Explanation                   |
| :---------- | :-------------- | :---------------------------- |
| **Best**    | $\Omega(n)$     | The array is already sorted.  |
| **Average** | $O(n^2)$        | The array is in random order. |

**Space Complexity:** $O(1)$ (In-place).

---
#### The Algorithm
1.  Start from the second element (index 1).
2.  Compare the current element (`key`) with the one before it.
3.  Shift all elements larger than the `key` one position to the right.
4.  Insert the `key` into the correct position.
5.  Repeat until the array is sorted.

**Visualizing Insertion Sort**
*Processing element '3' (Index 3)*

| State | Sorted Portion (Left) | Unsorted (Right) |
| :--- | :---: | :---: |
| **Start** | `2` `5` `8` | **`3`** `9` |
| **Step 1** | Key = 3. Compare 3 < 8? Yes. Shift 8 right. | |
| **Shift** | `2` `5` `_` `8` | `9` |
| **Step 2** | Compare 3 < 5? Yes. Shift 5 right. | |
| **Shift** | `2` `_` `5` `8` | `9` |
| **Step 3** | Compare 3 < 2? No. Insert 3 after 2. | |
| **Result** | `2` **`3`** `5` `8` | `9` |

---
#### Pros & Cons
**Advantages:**
1.  **Adaptive:** If the array is already nearly sorted, runtime approaches $O(n)$.
2.  **Stable:** Maintains the relative order of equal elements.
3.  **Low Overhead:** Very simple code, no recursion stack, $O(1)$ space.
4.  **Small Data Efficiency:** Faster than Quick Sort or Merge Sort for very small arrays (e.g., $n < 10-20$).

**Disadvantages:**
1.  **Scalability:** $O(n^2)$ makes it unusable for large datasets on its own.
2.  **Writes:** Performs many writes to memory (shifting elements), which can be costly if writes are expensive.
---
#### Implementation

```c
void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;

        // Move elements of arr[0..i-1] that are greater than key
        // to one position ahead of their current position
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j = j - 1;
        }
        arr[j + 1] = key;
    }
}
```

```rust
fn insertion_sort<T: Ord + Copy>(arr: &mut [T]) {
    for i in 1..arr.len() {
        let key = arr[i];
        let mut j = i;

        // Shift elements to the right to make room for 'key'
        while j > 0 && arr[j - 1] > key {
            arr[j] = arr[j - 1];
            j -= 1;
        }
        arr[j] = key;
    }
}
```

---
