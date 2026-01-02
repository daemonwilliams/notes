#math #reference
**Discrete Mathematics** is the backbone of Computer Science. Unlike Calculus, which deals with continuous change, Discrete Math deals with distinct, separate objects like integers, graphs, and logical statements.

*Correctness* is the primary goal here. While DSA focuses on how *fast* code runs, this module focuses on proving it gives the *right answer* and terminates.

The main way we express the *certainty* of a system is through **[[Proof(s)]]**. This connects directly to [[Data Structures & Algorithms]] - for example, [[Mathematical Induction]] is the theoretical basis for [[Recursion]].

---
#### Key Concepts

**Proofs & Logic**
- [[Logic and Propositions]]
- [[Proof Method(s)]]
- [[Mathematical Induction]]
- [[Strong Induction]]
- [[The Invariant Principle]]
- [[Well Ordering Principle]]

**Structures**
- [[Number Theory]]
- [[Modular Arithmetic]]
- [[RSA Encryption]]

---
#### Real-World Context: Why Math Matters
These examples highlight what happens when the underlying mathematical assumptions of a system fail.

#### Ariane 5 Flight 501 (1996)
- **The Failure:** A 64-bit float was converted to a 16-bit integer, causing an **[[Binary#Integer Overflow & Modular Arithmetic|Integer Overflow]]**.
- **Result:** The rocket self-destructed 37 seconds after launch.
- **Cost:** $370 Million.
- **Math Lesson:** [[Modular Arithmetic]] and Data Types.

#### The Pentium FDIV Bug (1994)
- **The Failure:** A lookup table for division in the Intel CPU FPU had missing entries.
- **Result:** Rare but consistent calculation errors in high-precision math.
- **Cost:** $475 Million (Recall).
- **Math Lesson:** Verification of [[Central Processing Unit(s) (CPU)|CPU Logic]].

#### RSA & Internet Security
- **The Context:** Every secure connection (HTTPS) relies on the fact that factoring large numbers is hard.
- **The Scale:** Breaking a 2048-bit RSA key would take classical computers trillions of years.
- **Math Lesson:** [[RSA Encryption]] and [[Divisibility and GCD]].

#### Toyota Unintended Acceleration (2000s)
- **The Failure:** Stack Overflow in the Engine Control Unit (ECU) caused memory corruption.
- **Result:** Loss of throttle control.
- **Math Lesson:** [[Mathematics/Proofs/The Invariant Principle|Invariants]] and Recursion depth.

---
#### Resources
- [MIT 6.042J: Mathematics for Computer Science](https://ocw.mit.edu/courses/6-042j-mathematics-for-computer-science-fall-2010/)
