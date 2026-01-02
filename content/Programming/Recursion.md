**Recursion** is a programming technique and core [[Data Structures & Algorithms]] concept where a function calls itself to solve smaller instances of the same problem. It is a direct application of [[Divide-&-Conquer]] and essentially the programming equivalent of [[Mathematical Induction|Mathematical Induction]].

---
#### Properties of a Recursive Function
Every valid recursive function must have two parts:
1.  **Base Case:** The stopping condition. Without this, the function calls itself forever (Infinite Recursion).
2.  **Recursive Step:** The logic where the function calls itself with modified arguments, moving closer to the base case.
```c
// Factorial: n! = n * (n-1)!
int factorial(int n) {
    // 1. Base Case
    if (n <= 1) return 1;

    // 2. Recursive Step
    return n * factorial(n - 1);
}
```

**Classic Example: The Euclidean Algorithm**
Calculating the Greatest Common Divisor (GCD) is an efficient application of recursion (see [[Divisibility and GCD]]).
```c
int gcd(int a, int b) {
    if (b == 0) return a; // Base Case
    return gcd(b, a % b); // Recursive Step
}
```

---
#### Recursion & The Stack
Recursion relies heavily on the [[Stack(s)]]. Every recursive call creates a new [[Stack Frame]] to store its local `n` and return address.

**Trace for `factorial(3)`:**
1.  `factorial(3)` called. Stack: `[3]`
2.  `factorial(2)` called. Stack: `[3, 2]`
3.  `factorial(1)` called. Stack: `[3, 2, 1]` -> Returns 1.
4.  `factorial(2)` resumes. Returns `2 * 1 = 2`. Pop `2`.
5.  `factorial(3)` resumes. Returns `3 * 2 = 6`. Pop `3`.

**Risk:** Deep recursion can lead to **Stack Overflow** if the recursion depth exceeds the stack size. *(see [[Heap(s)]])*

---
#### Tail Call Optimization 
Often **Tail Recursion** is best. This is a special form where the recursive call is the *very last action* of the function.

Smart compilers (like `gcc -O2` or `clang`) can optimize this by reusing the *same* stack frame for the next call, effectively turning the recursion into a loop. This prevents Stack Overflow.

```c
// Tail Recursive Factorial
// The result is passed as an accumulator ('acc')
int factorial_tail(int n, int acc) {
    if (n <= 1) return acc;
    return factorial_tail(n - 1, n * acc); // Pure tail call
}
```

---

