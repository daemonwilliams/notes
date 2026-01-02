**Rust** is a programming language that runs fast like c/c++, but attempts to prevents segfaults and guarantee thread safety. 

#### Core Philosophy
1.  **Memory Safety Without Garbage Collection:** Rust uses a unique **[[Ownership]]** system with compile-time checks to ensure memory safety. There is no runtime GC (like Java/Python) and no manual `malloc/free` (like C).
2.  **Zero-Cost [[Abstraction|Abstractions]]:** High-level concepts (iterators, closures, generics) compile down to the same efficient machine code as hand-written loops.
3.  **Concurrency Without Data Races:** The type system tracks ownership across threads, making it impossible to write code that introduces data races at compile time.

---
#### Key Concepts
- **[[Ownership]]:** The rule set that governs how memory is managed.
- **[[Borrowing and References]]:** How to access data without taking ownership.
- **[[Structs and Enums]]:** Custom data types and pattern matching.
- **[[Error Handling]]:** The `Result<T, E>` and `Option<T>` types (no Exceptions).
- **[[Traits]]:** Defining shared behavior (similar to Interfaces).
---
#### Comparison to C
| Feature          | C                        | Rust                                  |
| :--------------- | :----------------------- | :------------------------------------ |
| **Memory**       | Manual (`malloc`/`free`) | Automatic (Scope-based)               |
| **Pointers**     | Raw Pointers (unsafe)    | References (checked) & Smart Pointers |
| **Strings**      | Null-terminated `char*`  | `String` (owned) & `&str` (slice)     |
| **Build System** | Make/CMake               | Cargo (Package Manager + Build)       |

---
#### References
- [The Rust Programming Language Documenation](https://doc.rust-lang.org/stable/book/)