**Mathematical Induction** is a powerful [[Proof Method(s)]] used to prove a statement $P(n)$ for all natural numbers $n$. It is often compared to the "Domino Effect": if you can knock down the first domino, and knocking down any domino guarantees the next one falls, then all dominos will fall.

---
#### The Principle
To prove that $\forall n \in \mathbb{N}, P(n)$ is true (see [[Logic and Propositions|Universal Quantifier]]), we must establish two things:
1.  **Base Case:** Verify that $P(0)$ (or the first element $P(1)$) is true.
2.  **Inductive Step:** Prove that for any $k \ge 0$, if $P(k)$ is true, then $P(k+1)$ is also true.
    - $P(k) \implies P(k+1)$

If both hold, then $P(n)$ is true for all $n$.

---
#### Standard Induction Structure
A rigorous induction proof follows this template:
1.  **State the Hypothesis:** Let $P(n)$ be the proposition that [statement].
2.  **Base Case:** Show that $P(0)$ is true.
3.  **Inductive Hypothesis:** Assume $P(k)$ is true for some arbitrary integer $k \ge 0$.
4.  **Inductive Step:** Show that $P(k+1)$ must be true, using the assumption from step 3.
5.  **Conclusion:** By the principle of mathematical induction, $P(n)$ is true for all $n$.

**Example: Sum of First $n$ Integers**
Theorem: $\forall n \ge 1, \sum_{i=1}^{n} i = \frac{n(n+1)}{2}$

- **Base Case ($n=1$):** $1 = \frac{1(2)}{2} = 1$. (True)
- **Inductive Hypothesis:** Assume $\sum_{i=1}^{k} i = \frac{k(k+1)}{2}$.
- **Inductive Step:** We want to show $\sum_{i=1}^{k+1} i = \frac{(k+1)(k+2)}{2}$.
    $$
    \begin{aligned}
    \sum_{i=1}^{k+1} i &= \left( \sum_{i=1}^{k} i \right) + (k+1) \\
    &= \frac{k(k+1)}{2} + (k+1) \quad (\text{by Hypothesis}) \\
    &= (k+1) \left( \frac{k}{2} + 1 \right) \\
    &= (k+1) \left( \frac{k+2}{2} \right) \\
    &= \frac{(k+1)(k+2)}{2} \quad (\text{Q.E.D.}) \\
    \end{aligned}
    $$

---
#### Variations
1.  **[[Strong Induction]]:** Assumes the property holds for *all* values up to $k$, not just $k$. Useful for recursion and number theory.
2.  **[[Well Ordering Principle]] (WOP):** The axiom that every nonempty set of nonnegative integers has a smallest element. It is logically equivalent to Induction.

---
#### Common Pitfalls
- **Base Case Omission:** Forgetting the base case leads to false proofs.
- **Build-Up Error:** Assuming $P(k+1)$ can be built *uniquely* from $P(k)$.

---
