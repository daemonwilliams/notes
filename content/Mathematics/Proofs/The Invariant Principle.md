**The Invariant Principle** is a proof technique used to verify properties of **State Machines** or iterative processes. It is a specific application of [[Mathematical Induction]].

---
A **State Machine** consists of:
1.  **States:** A set of possible configurations.
2.  **Transitions:** Rules for moving from one state to another ($q \to q'$).
3.  **Start State:** The initial configuration ($q_0$).

#### Definition: Preserved Invariant
A predicate $P$ is a **preserved invariant** of a state machine if:
- If $P(q)$ is true for a state $q$, and there is a transition $q \to q'$, then $P(q')$ is also true.
- *Formally:* $\forall q, q', (P(q) \land (q \to q')) \implies P(q')$
- **Base Case:** $P(q_0)$ is true (Given).
- **Inductive Step:** If state $q_k$ is reachable and $P(q_k)$ is true, any transition leads to $q_{k+1}$. Since $P$ is preserved, $P(q_{k+1})$ is true.

---
#### Example: The Die Hard Water Jugs
**Problem:** You have a 3-gallon jug and a 5-gallon jug. Can you measure exactly 4 gallons?
**Transitions:**
1.  Fill a jug completely.
2.  Empty a jug completely.
3.  Pour from one jug to another until the first is empty or the second is full.

**Invariant Analysis:**
- Let the state be $(x, y)$, the amount of water in the 3-gal and 5-gal jugs.
- Start state: $(0, 0)$.
- **Invariant:** $x$ and $y$ are always linear combinations of 3 and 5. Specifically, $x + y$ is a multiple of $\gcd(3, 5)$.
- Since $\gcd(3, 5) = 1$, we *can* reach any integer amount between 0 and 8.
- *this shows we CAN do it.*

**Counter-Example: The 3 and 6 Gallon Jugs**
- Can you measure 4 gallons with a 3-gal and 6-gal jug?
- **Invariant:** The amount of water is always a linear combination of 3 and 6.
- $W = 3a + 6b = 3(a + 2b)$.
- Therefore, any amount of water must be a **multiple of 3**.
- **Conclusion:** Since 4 is not a multiple of 3, it is **impossible** to reach 4 gallons. The state $(?, 4)$ is unreachable.
---
#### Application in Systems
- **Loop Invariants:** Used to prove correctness of algorithms (e.g., sorting).
- **Rust's Memory Safety:** The [[Rust|Rust]] compiler enforces specific invariants (like "Every value has exactly one owner") at compile time. If the code compiles, the invariant holds for all executions.

---

