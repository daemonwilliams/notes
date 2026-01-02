#math #security
**RSA** (Rivest–Shamir–Adleman) is a public-key cryptosystem widely used for secure data transmission. Its security relies on the practical difficulty of factoring the product of two large prime numbers.

---
#### The Setup (Key Generation)
1.  **Select Primes:** Choose two distinct large prime numbers $p$ and $q$.
2.  **Modulus:** Compute $n = p \cdot q$.
    - $n$ is used as the modulus for both public and private keys.
3.  **Totient:** Compute $\phi(n) = (p-1)(q-1)$.
4.  **Public Exponent:** Choose an integer $e$ such that $1 < e < \phi(n)$ and $\gcd(e, \phi(n)) = 1$.
    - *Common choice:* $e = 65537$.
5.  **Private Exponent:** Determine $d$ as the **modular multiplicative inverse** of $e$ modulo $\phi(n)$.
    - $d \cdot e \equiv 1 \pmod{\phi(n)}$
    - Use the **Pulverizer** ([[Divisibility and GCD]]) to find $d$.

**Keys:**
- **Public Key:** $(n, e)$ (Given to everyone).
- **Private Key:** $(d)$ (Kept secret, along with $p, q$).

---
#### Encryption & Decryption
Let $M$ be the message (converted to an integer $< n$).

**Encryption:**
$$ C \equiv M^e \pmod{n} $$
Sender uses the recipient's **Public Key**.

**Decryption:**
$$ M \equiv C^d \pmod{n} $$
Recipient uses their **Private Key**.

---
#### Why It Works (Correctness)
We need to prove that $(M^e)^d \equiv M \pmod{n}$.
$$ M^{ed} = M^{1 + k\phi(n)} = M \cdot (M^{\phi(n)})^k $$
By **Euler's Theorem** ([[Modular Arithmetic]]), $M^{\phi(n)} \equiv 1 \pmod{n}$.
$$ M \cdot (1)^k \equiv M \pmod{n} $$

- *Note:* The security rests on the fact that if you only know $n$, finding $\phi(n)$ is equivalent to factoring $n$ into $p$ and $q$. There is no known efficient algorithm for this on classical computers.

---

