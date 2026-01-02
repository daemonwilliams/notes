Recurrence Relation:  $T(n) = aT(n/b) + f(n)$

- $n$: Size of the problem.
- $a$: Number of sub-problems in the recursion.
- $b$: Factor by which the sub-problem size decreases.
- $f(n)$: Cost of the work done outside the recursive calls (Dividing + Combining).

**Simplified Rules:**
1.  **$f(n)$ dominates (Heavy Combine):** $O(f(n))$
2.  **Balanced:** $O(n^{\log_b a} \log n)$  *(e.g., Merge Sort: $2T(n/2) + n \to O(n \log n)$)*
3.  **Leaves dominate (Many tiny problems):** $O(n^{\log_b a})$

---
