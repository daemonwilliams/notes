#systems #memory #security
**Ownership** is Rust's most unique feature. It enables memory safety without a garbage collector by enforcing a strict set of rules at **compile time**. If these rules are violated, the program will not compile.

#### The Three Rules
> [!IMPORTANT]
> 1.  Each value in Rust has a variable that’s called its **owner**.
> 2.  There can only be **one** owner at a time.
> 3.  When the owner goes out of **scope**, the value will be dropped (memory freed).

---
#### Stack vs. Heap
Understanding [[Stack(s)]] and [[Heap(s)]] is crucial for Ownership.
- **Stack:** Fast, fixed size. Stores primitives (`int`, `bool`, `char`) and fixed-size arrays. Values are "copied" cheaply.
- **Heap:** Slower, dynamic size. Stores complex types (`String`, `Vector`). Pointers to the heap data are stored on the stack.

#### The "Move" Semantics
In many languages, assigning variable `a` to `b` copies the value. In Rust, for heap data, it **moves** ownership.

```rust
let s1 = String::from("hello");
let s2 = s1; // s1 is MOVED to s2. s1 is now INVALID.

// println!("{}", s1); // Compile Error! "Value used after move"
```
> [!CAUTION] Why?
> To prevent **Double Free** errors. If both `s1` and `s2` owned the memory, both would try to free it when they go out of scope, causing memory corruption.

#### Clone vs. Copy
- **Copy:** Types stored entirely on the stack (integers, bools) implement the `Copy` trait. Assignment makes a bitwise copy. `s1` remains valid.
- **Clone:** For heap data, if you *want* a deep copy (new heap allocation), you must call `.clone()`.
    ```rust
    let s1 = String::from("hello");
    let s2 = s1.clone(); // Deep copy. Both s1 and s2 are valid.
    ```

---
#### Ownership and Functions
Passing a variable to a function follows the same rules:
- Passing a heap variable **moves** ownership to the function.
- Passing a stack variable **copies** it.

```rust
fn main() {
    let s = String::from("hello");
    takes_ownership(s); 
    // s is no longer valid here!
}

fn takes_ownership(some_string: String) { // some_string comes into scope
    println!("{}", some_string);
} // some_string goes out of scope and `drop` is called. Memory freed.
```
*To use `s` again, we would need to return it, or use [[Borrowing and References]].*

---

