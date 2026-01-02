A **Hash Function** is defined as any function that can be used to map data of arbitrary size to fixed-size values. The values returned by a hash function are called *hash values*, *hash codes*, *digests*, or simply *hashes*. They are primarily used to index data in [[Hash Table(s)]].

The core idea is to transform a given input (`key`) into an integer that can be used as an array index, allowing for very fast data retrieval.

---
#### Properties of a Good Hash Function
For a hash function to be effective, especially for data structures like hash tables, it should exhibit several key properties:

1.  **Deterministic:** The same input key must always produce the same hash value.
2.  **Efficient Computation:** The hash value should be quick to compute. A complex hash function defeats the purpose of fast lookups.
3.  **Uniform Distribution:** It should distribute keys as evenly as possible across the entire range of possible hash values. This minimizes Collisions.

---
#### Why Hash Functions are Used
- **Fast Data Retrieval (Hash Tables):** Provides $O(1)$ average-case lookup, insertion, and deletion times.
- **Data Integrity (Checksums):** Verifying that data has not been altered (e.g., file downloads, network packets).
- **Cryptography:** Used in digital signatures, password storage, and message authentication codes. (These are specialized cryptographic hash functions).
- **Uniqueness Identification:** Quickly checking if an item has been seen before (e.g., in caches).

---
#### Common Techniques & Implementations

**1. Simple Summation (Illustrative, but Flawed)**
This method sums the ASCII values of characters in a string. It's easy to understand but results in many collisions for different strings with the same characters.

```c
// Limitations: Poor distribution, sensitive to character order only (not position)
int simple_hash_sum(const char* key, int table_size) {
    int hash_value = 0;
    int i = 0;
    while (key[i] != '\0') {
        hash_value += key[i];
        i++;
    }
    return hash_value % table_size; // Modulo operation maps to table size (see [[Modular Arithmetic]])
}
```

**2. Polynomial Rolling Hash (Better Distribution)**
This method considers the position of each character, giving more weight to characters earlier in the string. It involves multiplying by a prime number `p` at each step.

```c
// More robust, considers character position
unsigned int polynomial_rolling_hash(const char* key, int table_size) {
    unsigned int hash_value = 0;
    unsigned int p = 31; // A prime number, often used
    unsigned int p_power = 1;

    for (int i = 0; key[i] != '\0'; i++) {
        hash_value = (hash_value + (key[i] - 'a' + 1) * p_power) % table_size;
        p_power = (p_power * p) % table_size; // Re-calculate p_power for next char
    }
    return hash_value;
}
```

**Rust Implementation Example (using `std::collections::hash::Hasher`)**
In Rust, you typically use the built-in `std::hash::Hash` trait and `std::collections::HashMap` which uses a cryptographic-ally secure, yet fast, default hash function ([[SipHash]]). For custom hashing, you'd implement the `Hasher` trait.

```rust
use std::hash::{Hash, Hasher};
use std::collections::hash_map::DefaultHasher;

// Example of hashing a string using the default hasher
fn get_string_hash(s: &str) -> u64 {
    let mut hasher = DefaultHasher::new();
    s.hash(&mut hasher);
    hasher.finish()
}

// Example of a simple custom hash function (for learning, not production)
// This is analogous to the polynomial_rolling_hash concept
fn custom_hash(key: &str, table_size: usize) -> usize {
    let mut hash_value: usize = 0;
    let p: usize = 31; // Prime number
    let mut p_power: usize = 1;

    for c in key.chars() {
        hash_value = (hash_value + (c as usize - 'a' as usize + 1) * p_power) % table_size;
        p_power = (p_power * p) % table_size;
    }
    hash_value
}
```

---
#### Collision Handling
Since a hash function maps a potentially large set of inputs to a smaller, fixed-size output range, **collisions are inevitable**. Effective hash tables require strategies to handle these collisions, such as:
- **Separate Chaining:** Store colliding elements in a linked list at each hash table index.
- **Open Addressing:** Find another open spot in the hash table when a collision occurs (e.g., Linear Probing, Quadratic Probing, Double Hashing).

*(See [[Hash Table(s)]] for more details on collision resolution.)*

---
