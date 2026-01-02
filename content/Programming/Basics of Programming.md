#concept #reference

**Basics of Programming** serves as a syntax lookup for core constructs across different languages. While syntax changes, the underlying concepts map to the same [[Central Processing Unit(s) (CPU)|CPU Instructions]].

---
#### 1. Variables & Mutability
Variables are named storage locations in memory.
- **Statically Typed (C, Rust):** The type is known at compile time, determining the exact memory size on the [[Stack(s)]].
- **Dynamically Typed (Python):** Variables are references to objects on the [[Heap(s)]], resolved at runtime.

> [!example]- C
> **Mutable by default.** You must specify the type explicitly.
> ```c
> int x = 5;       // 4 bytes on Stack
> x = 6;           // OK
> const int y = 10; // Immutable (Read-Only)
> ```

> [!example]- Rust
> **Immutable by default.** Focuses on safety.
> ```rust
> let x = 5;
> // x = 6; // Compile Error!
> let mut y = 5;
> y = 6; // OK
> ```

> [!example]- Python
> **Dynamic.** Variables are just name tags for objects.
> ```python
> x = 5
> x = "Hello" # x now points to a String object
> ```

---
#### 2. Conditionals (Branching)
Control flow allows the program to make decisions. At the hardware level, these compile down to **Jump** or **Branch** instructions based on flags set by the [[Central Processing Unit(s) (CPU)#Core Components|ALU]].

> [!example]- C
> *   **Truthy:** Any non-zero value is true. `if (1)` works.
> *   Parentheses `()` required.
> ```c
> if (x > 5) {
>     printf("Big");
> } else if (x == 5) {
>     printf("Equal");
> } else {
>     printf("Small");
> }
> ```

> [!example]- Rust
> *   **Strict Booleans:** `if (1)` is an error. Must be `true`/`false`.
> *   **Expression:** `if` returns a value, allowing functional patterns.
> ```rust
> let result = if x > 5 { "Big" } else { "Small" };
> ```

> [!example]- Python
> *   **Indentation** defines blocks.
> ```python
> if x > 5:
>     print("Big")
> elif x == 5:
>     print("Equal")
> else:
>     print("Small")
> ```

---
#### 3. Loops (Iteration)
Repeating code blocks. Loops are the primary driver of **[[Data Structures & Algorithms/Time Complexity|Time Complexity]]**. Correctness is often proven via **[[Mathematics/Proofs/The Invariant Principle|Loop Invariants]]**.

> [!example]- C
> The classic `for` loop gives you total control over the index.
> ```c
> // Init; Condition; Update
> for (int i = 0; i < 10; i++) {
>     printf("%d", i);
> }
> ```

> [!example]- Rust
> Prefers **Iterators** for safety (avoids out-of-bounds errors).
> ```rust
> // Exclusive range (0 to 9)
> for i in 0..10 {
>     println!("{}", i);
> }
> // Loop forever (cleaner than while(true))
> loop { break; }
> ```

> [!example]- Python
> Also Iterator-based.
> ```python
> for i in range(10):
>     print(i)
> ```

---
#### 4. Functions
Reusable blocks of code. Calling a function creates a new **[[Data Structures & Algorithms/Stack(s)#The "Call Stack" or "The Stack"|Stack Frame]]** in memory to hold arguments and local variables.

> [!example]- C
> Return type precedes the name.
> ```c
> int add(int a, int b) {
>     return a + b;
> }
> ```

> [!example]- Rust
> Uses `fn`. The last line (without semicolon) is an **implicit return**.
> ```rust
> fn add(a: i32, b: i32) -> i32 {
>     a + b // Expression return
> }
> ```

> [!example]- Python
> Uses `def`.
> ```python
> def add(a, b):
>     return a + b
> ```

---
#### 5. Arrays & Collections
Storing multiple values.

> [!example]- C
> **Raw Arrays.** Fixed size, contiguous memory. No bounds checking (Dangerous).
> ```c
> int arr[5] = {1, 2, 3, 4, 5};
> int val = arr[10]; // Segfault or Garbage (Undefined Behavior)
> ```

> [!example]- Rust
> **Arrays** (Fixed) vs **Vectors** (Dynamic). Strict bounds checking.
> ```rust
> let arr = [1, 2, 3]; // Fixed size Stack array
> let vec = vec![1, 2, 3]; // Dynamic Heap vector
> // let val = arr[10]; // Panic! (Crash safely)
> ```

> [!example]- Python
> **Lists.** Dynamic, heterogeneous (can hold mix of types).
> ```python
> lst = [1, "two", 3.0]
> lst.append(4)
> ```

---
#### 6. Error Handling
How the language deals with failure.

> [!example]- C
> **Return Codes.** Functions return `0` (Success) or `-1` (Error).
> ```c
> FILE *f = fopen("file.txt", "r");
> if (f == NULL) {
>     // Handle Error
> }
> ```

> [!example]- Rust
> **Result Type.** No exceptions. Errors are values.
> ```rust
> let f = File::open("file.txt");
> match f {
>     Ok(file) => { /* use file */ },
>     Err(e) => { /* handle error */ },
> }
> ```

> [!example]- Python
> **Exceptions.**
> ```python
> try:
>     f = open("file.txt")
> except FileNotFoundError:
>     print("Error")
> ```

---
#### 7. Data Structures (Structs)
Defining custom types.

> [!example]- C
> ```c
> struct Point {
>     int x;
>     int y;
> };
> ```

> [!example]- Rust
> ```rust
> struct Point {
>     x: i32,
>     y: i32,
> }
> ```

> [!example]- Python
> Classes or Dataclasses.
> ```python
> @dataclass
> class Point:
>     x: int
>     y: int
> ```

---
