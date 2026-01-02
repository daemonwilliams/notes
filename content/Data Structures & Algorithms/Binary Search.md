**Binary Search** is the "Hello World" of efficient [[Data Structures & Algorithms|algorithms]]. It is the primary reason we sort data. If you have a sorted dataset, you never need to check every element. You can simply keep dividing the search space in half.

---
#### The Algorithm
1. Compare the target value to the middle element of the array.
2. If they are equal, the search is successful.
3. If the target is smaller than the middle element, repeat the search on the left half.
4. If the target is larger than the middle element, repeat the search on the right half.
5. Continue until the element is found or the search interval is empty.
---
#### Time Complexity: $O(\log n)$
Every step cuts the problem size in half.
- $n = 16$ elements $\to$ 4 steps.
- $n = 1,000,000$ elements $\to$ ~20 steps.
- $n = 4,000,000,000$ (entire 32-bit integer range) $\to$ 32 steps.
---
#### Implementation & Space Complexity (Iterative vs Recursive) 

**1. Iterative Approach**
-  Recursion adds overhead to the [[Stack(s)]]. Iteration uses constant $O(1)$ memory.
```c
int binarySearch(int arr[], int size, int target) {
    int left = 0;
    int right = size - 1;

    while (left <= right) {
        // Prevent overflow: mid = left + (right - left) / 2
        int mid = left + (right - left) / 2;

        if (arr[mid] == target) {
            return mid; // Found match
        }
        
        if (arr[mid] < target) {
            left = mid + 1; // Target is in right half
        } else {
            right = mid - 1; // Target is in left half
        }
    }
    return -1; // Not found
}
```

**2. Recursive Approach**
Elegant, but technically uses $O(\log n)$ stack space.
```c
int binarySearchRecursive(int arr[], int left, int right, int target) {
    if (left > right) return -1;

    int mid = left + (right - left) / 2;

    if (arr[mid] == target) return mid;
    
    if (arr[mid] < target) {
        return binarySearchRecursive(arr, mid + 1, right, target);
    }
    return binarySearchRecursive(arr, left, mid - 1, target);
}
```

---
#### The Integer Overflow Bug
For decades, standard libraries (including Java's `Arrays.binarySearch`) contained a bug.

**Wrong:** `mid = (left + right) / 2;`
**Why?** If `left` and `right` are both large numbers (near `INT_MAX`), their sum will overflow into a negative number, crashing the program.

**Correct:** `mid = left + (right - left) / 2;`
This mathematically calculates the same average but ensures the intermediate value never exceeds `right`.

---
#### Use Cases
1.  **Database Indices:** [[SQL]] indices rely on this algorithm to find records instantly.
2.  **Debugging (Git Bisect):** When searching for a bug in a large commit history, `git bisect` uses binary search to find the "bad commit" by checking the middle commit, marking it good/bad, and repeating.
3.  **Standard Libraries:** `bsearch()` in C's `<stdlib.h>`.

---