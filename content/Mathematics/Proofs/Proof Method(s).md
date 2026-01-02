While the concept of a proof is universal, the **method** used to derive the theorem varies. Choosing the right method is often the key to solving the problem.

---
#### 1. Direct Proof
The standard approach. Assume the axioms and hypothesis ($P$) are true, and logically deduce the conclusion ($Q$). 
*   **Structure:** $P \implies \dots \implies Q$

#### 2. Proof by Contra-positive
Instead of proving $P \implies Q$, we prove its logical equivalent: $\neg Q \implies \neg P$.
-   **When to use:** When $Q$ looks complicated or "negative" (e.g., "then $n$ is *not* divisible by...").
-   **Example:** Prove "If $n^2$ is even, then $n$ is even."
    -   *Contrapositive:* "If $n$ is odd, then $n^2$ is odd." (Much easier to prove: $(2k+1)^2 = 4k^2 + 4k + 1 = 2(\dots) + 1$, which is odd).

#### 3. Proof by Contradiction
To prove $P$ is True, assume (for the sake of argument) that $P$ is **False**, and show that this assumption leads to a logical impossibility (e.g., $1=0$ or $R \land \neg R$).
*   **Structure:** Assume $\neg P \implies \dots \implies \text{Contradiction}$. Therefore, $\neg P$ is impossible, so $P$ must be True.
*   **Classic Example:** $\sqrt{2}$ is irrational.

#### 4. Proof by Cases
If a statement holds for all possible disjoint cases that cover the entire domain, it is true.
*   **Example:** Proving properties of absolute value $|x|$ often requires two cases: Case 1 ($x \ge 0$) and Case 2 ($x < 0$).
*   *Warning:* Ensure your cases are **exhaustive** (cover all possibilities).

#### 5. Non-Constructive Existence Proofs
Proving $\exists x, P(x)$ is true without actually telling you what $x$ is.
*   Often uses the [[Pigeonhole Principle]] or [[Intermediate Value Theorem]].
*   *Example:* "There exist two irrational numbers $x, y$ such that $x^y$ is rational." (Proof uses cases on $\sqrt{2}^{\sqrt{2}}$ without confirming if it's rational or not).

---
