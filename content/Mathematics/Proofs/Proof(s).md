A **Proof** is a rigorous method for establishing the truth of a mathematical statement. In Computer Science, a proof is a verification of a [[Logic and Propositions|Proposition]] by a chain of logical deductions starting from a set of **Axioms**. It allows us to certify that a system (or algorithm) works correctly for *all* possible inputs, which is impossible to do via testing alone.

---
#### Components
1.  [[Logic and Propositions|Proposition]]: A statement that is definitive either True or False.
    - *Example:* $2 + 2 = 4$ (True)
    - *Example:* $\forall n \in \mathbb{N}, n > 0$ (False for $n=0$)
2.  [[Axiom]]: A proposition that is assumed to be true without proof. These form the foundation (ground truth) of the logical system.
    - *Example:* "It is possible to draw a straight line from any point to any other point."
3.  **Inference Rule:** A logical rule that allows the deduction of a new proposition from existing ones.
    - *Example:* If $P$ is true and $P \implies Q$ is true, then $Q$ is true.

---
#### The Structure of a Proof
A proof connects axioms to theorems through a sequence of logical steps. See [[Logic and Propositions]] for details on logical connectives ($\implies, \forall, \exists$).
$$ \text{Axioms} \xrightarrow{\text{Logical Deductions}} \dots \xrightarrow{\text{Inference Rules}} \text{Theorem} $$

> [!NOTE] The Limits (Gödel)
> Any consistent axiomatic system powerful enough to describe arithmetic is **incomplete**. There are true statements that cannot be proven within the system.

---
#### Common Pitfalls
**False Proofs** often rely on hidden assumptions, division by zero, or misleading visualizations.

> [!BUG] Example: The $1 = -1$ Fallacy
> $$
> \begin{aligned}
> -1 &=-1 \\
> \frac{1}{-1} &= \frac{-1}{1} \\
> \sqrt{\frac{1}{-1}} &= \sqrt{\frac{-1}{1}} \\
> \frac{\sqrt{1}}{\sqrt{-1}} &= \frac{\sqrt{-1}}{\sqrt{1}} \\
> \frac{1}{i} &= \frac{i}{1} \\
> 1 &= i^2 \\
> 1 &= -1 \quad (\text{False})
> \end{aligned}
> $$
> **The Flaw:** The rule $\sqrt{a/b} = \sqrt{a}/\sqrt{b}$ is only valid for positive real numbers. Applying it to negatives leads to contradictions.

---
#### Methods of Proof
See [[Proof Method(s)]] for a detailed breakdown.
- **[[Proof Method(s)#1. Direct Proof|Direct Proof]]:** Proceed linearly from $P$ to $Q$.
- **[[Proof Method(s)#2. Proof by Contrapositive|Proof by Contrapositive]]:** Prove $\neg Q \implies \neg P$.
- **[[Proof Method(s)#3. Proof by Contradiction|Proof by Contradiction]]:** Assume $\neg P$, derive a contradiction.
- **[[Mathematical Induction]]:** Prove a property holds for all natural numbers by proving a base case and an inductive step.

---
#### Why Proofs Matter
- **Correctness:** Ensuring an algorithm produces the correct output for *all* valid inputs.
- **Security:** Verifying that a cryptographic protocol cannot be breached.
- **Reliability:** Preventing bugs in critical hardware/software systems (e.g., flight control, banking).

---

