**Quick Sort** is a highly efficient, [[Divide-&-Conquer]] sorting algorithm. It works by selecting a 'pivot' element from the array and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot. The sub-arrays are then sorted recursively.

It is often faster in practice than other $O(n \log n)$ algorithms like [[Merge Sort]] because it is an **in-place** sort (requiring little additional memory) and has excellent **cache locality**, making it a favorite in Low-level Systems Programming (e.g., `qsort` in C's standard library).

---
#### Time & Space Complexity

| Case      | Time Complexity | Explanation                                                                             |
| :-------- | :-------------- | :-------------------------------------------------------------------------------------- |
| **Best**  | $O(n \log n)$   | Partition splits array exactly in half every time.                                      |
| **Worst** | $O(n^2)$        | Partition creates one empty sub-array (e.g., sorted array with first element as pivot). |

**Space Complexity:** $O(\log n)$ due to the recursive [[Stack Frame]]s.

---
#### Pros & Cons

**Pros:**
1.  **Speed:** In practice, it is often faster than Merge Sort because of efficient cache usage (linear scanning of memory).
2.  **In-Place:** Requires minimal extra memory ($O(\log n)$ stack space), unlike Merge Sort which needs $O(n)$ space.
3.  **Systems Standard:** It is the standard sorting algorithm in many standard libraries (C/C++, Java).

**Cons:**
1.  **Worst Case:** If the pivot is poorly chosen (e.g., smallest element in a sorted array), complexity degrades to $O(n^2)$. *Solution: Median of a sample size as a pivot.*
2.  **Unstable:** Relative order of equal elements is NOT preserved (unlike [[Merge Sort]]).

---
#### The Algorithm (Partitioning)
The core of Quick Sort is the **Partition** logic.
1.  **Choose a Pivot:** Select an element (first, last, middle, or random).
2.  **Reorder:** Move all elements *smaller* than the pivot to its left, and all elements *larger* to its right.
3.  **Recursion:** Apply the same logic to the left and right sub-arrays.

**Visualizing Partition**
*Pivot is chosen as the last element (4).*

| State | Array | Action |
| :--- | :---: | :--- |
| **Initial** | `2` `6` `5` `1` `3` **`4`** | Pivot = 4 |
| **Step 1** | `2` `6` `5` `1` `3` **`4`** | 2 < 4? Yes. Keep. |
| **Step 2** | `2` `6` `5` `1` `3` **`4`** | 6 < 4? No. Mark as larger. |
| **Step 3** | `2` `6` `5` `1` `3` **`4`** | 5 < 4? No. Mark as larger. |
| **Step 4** | `2` `1` `5` `6` `3` **`4`** | 1 < 4? Yes. Swap 1 with first large (6). |
| **Step 5** | `2` `1` `3` `6` `5` **`4`** | 3 < 4? Yes. Swap 3 with next large (5). |
| **Final** | `2` `1` `3` **`4`** `6` `5` | Move Pivot to sorted position (index 3). |

---
#### Implementation
```c
void swap(int *a, int *b) {
    int t = *a;
    *a = *b;
    *b = t;
}

// Partition: Returns the index where the Pivot ends up
int partition(int array[], int low, int high) {
    int pivot = array[high]; // Selecting last element as pivot
    int i = (low - 1); // Index of smaller element

    for (int j = low; j < high; j++) {
        // If current element is smaller than the pivot
        if (array[j] < pivot) {
            i++;
            swap(&array[i], &array[j]);
        }
    }
    swap(&array[i + 1], &array[high]);
    return (i + 1);
}

void quickSort(int array[], int low, int high) {
    if (low < high) {
        int pi = partition(array, low, high);

        // Separately sort elements before and after partition
        quickSort(array, low, pi - 1);
        quickSort(array, pi + 1, high);
    }
}
```

```rust
fn quick_sort<T: Ord>(arr: &mut [T]) {
    let len = arr.len();
    if len <= 1 {
        return;
    }

    match partition(arr) {
        pivot_index => {
            let (left, right) = arr.split_at_mut(pivot_index);
            quick_sort(left);
            quick_sort(&mut right[1..]); // Skip the pivot itself
        }
    }
}

fn partition<T: Ord>(arr: &mut [T]) -> usize {
    let len = arr.len();
    let pivot_index = len - 1;
    let mut i = 0;
    
    for j in 0..len - 1 {
        if arr[j] <= arr[pivot_index] {
            arr.swap(i, j);
            i += 1;
        }
    }
    arr.swap(i, len - 1);
    i
}
```

---
