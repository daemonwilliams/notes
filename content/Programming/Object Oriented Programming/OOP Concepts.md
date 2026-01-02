#concept
**Object-Oriented Programming (OOP)** is a programming paradigm based on the concept of "objects," which can contain data (fields) and code (methods). It dominates enterprise software and GUI development.

#### The Core Philosophy
Unlike Procedural Programming (C), which separates Data and Logic, OOP bundles them together.
- **Procedural:** `process_data(data)`
- **OOP:** `data.process()`

---
#### The Four Pillars of OOP
1.  **[[Encapsulation]]:** Hiding the internal state and requiring all interaction to occur through an object's methods. (Private vs Public).
2.  **[[Inheritance]]:** Creating new classes based on existing ones to reuse code. (Dog *is-a* Animal).
3.  **[[Polymorphism]]:** The ability of different classes to respond to the same message/function call in different ways. (The "Shape" class has a `draw()` method, but Circle and Square implement it differently).
4.  **[[Abstraction]]:** Hiding complex implementation details and showing only the necessary features of an object.

---
#### OOP in Systems Programming
- **C++:** The classic Systems OOP language. Adds Classes to C.
- **C:** Simulates OOP using `structs` and function pointers (e.g., the Linux Kernel `file_operations` struct).
- **Rust:** Not strictly OOP, but uses `structs` and `impl` blocks to achieve Encapsulation, and `Traits` to achieve Polymorphism.

---

