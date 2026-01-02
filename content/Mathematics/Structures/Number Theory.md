**Number Theory** is the study of the integers ($\mathbb{Z}$) and their properties. While it was once considered "pure math," it is now the foundation of modern **Cryptography** and computer security (e.g., [[RSA Encryption]], Elliptic Curves).

#### Core Concepts
- **Divisibility:** $a \mid b$ means "$a$ divides $b$."
- **Primes:** Integers greater than 1 with exactly two positive divisors (1 and themselves).
- **Modular Arithmetic:** Doing math with a "clock" (remainders).

---
#### The Division Algorithm
> [!IMPORTANT]
> For any integer $n$ and divisor $d > 0$, there exist unique integers $q$ (quotient) and $r$ (remainder) such that:
> $$ n = d \cdot q + r, \quad 0 \le r < d $$
> - **Note:** This is proven using the [[Well Ordering Principle]].

---
#### Greatest Common Divisor (GCD)
The GCD of two numbers is the largest integer that divides both.
$$ \gcd(a, b) = \max \{ k \in \mathbb{Z} : k \mid a \text{ and } k \mid b \} $$
- **Euclidean Algorithm:** An efficient recursive method to calculate GCD. (See [[Divisibility and GCD]]).
- **Linear Combinations:** $\gcd(a, b)$ can always be written as $s \cdot a + t \cdot b$.

---
#### Modular Arithmetic
We say $a$ is **congruent** to $b$ modulo $n$ if they have the same remainder when divided by $n$.
$$ a \equiv b \pmod{n} \iff n \mid (a - b) $$
- See [[Modular Arithmetic]] for inverses and Euler's Theorem.

---
#### Applications
1.  **Cryptography:** [[RSA Encryption]] relies on the difficulty of factoring large numbers.
2.  **Hashing:** Hash tables use modular arithmetic to map keys to buckets.
3.  **Random Number Generation:** Linear Congruential Generators (LCGs).

---

