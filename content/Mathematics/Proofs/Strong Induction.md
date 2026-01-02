**Strong Induction** is a variation of [[Mathematical Induction]] where the inductive hypothesis assumes the property holds for *all* values smaller than $k$, not just the immediately preceding one 
($k-1$).

---
#### The Principle
To prove $\forall n \in \mathbb{N}, P(n)$:
1.  **Base Case:** Prove $P(0)$ (or base set $P(0), \dots, P(b)$).
2.  **Inductive Step:** Prove that for any $k \ge 0$:
    $$ [P(0) \land P(1) \land \dots \land P(k)] \implies P(k+1) $$

*Difference:* In ordinary induction, we only assume $P(k)$. In strong induction, we assume **everything** up to $k$.

---
#### When to Use It?
Use Strong Induction when the recursive step relies on values strictly smaller than $k$, but not necessarily $k$ itself.
- **Prime Factorization:** To prove $n$ is a product of primes, if $n$ isn't prime, $n = a \cdot b$. We need to know that *both* $a$ and $b$ (which are $< n$) have prime factorizations. Knowing it for $n-1$ is useless here.
- **Fibonacci Numbers:** $F_{n} = F_{n-1} + F_{n-2}$. To prove a property for $F_n$, you need assumptions about *two* previous steps.
- **Game Theory:** Breaking a pile of $n$ stones into piles of size $a$ and $b$.

---
#### Example: The Unstacking Game
**Game:** You have a stack of $n$ blocks. You split it into two stacks of size $a$ and $b$ (where $a+b=n$). You score $ab$ points. You repeat this until all stacks are size 1.
**Theorem:** The total score is always $\frac{n(n-1)}{2}$, regardless of strategy.

- **Inductive Hypothesis:** Assume for all 
 \le j \le k$, the score for a stack of $j$ blocks is $S(j) = \frac{j(j-1)}{2}$.

- **Step ($k+1$):** Split stack of size $k+1$ into $a$ and $b$.

- Score $= ab + S(a) + S(b)$

- By Strong Hypothesis, we know the formulas for $S(a)$ and $S(b)$ are true (since $a, b \le k$).

- Algebra yields the result $\frac{(k+1)k}{2}$.

---

