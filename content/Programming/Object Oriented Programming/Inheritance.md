#concept #oop
**Inheritance** allows a class (Child/Subclass) to derive attributes and behavior from another class (Parent/Superclass). It promotes code reuse.

- **Relationship:** "Is-A" (e.g., A `Car` **is a** `Vehicle`).
- **Mechanism:** The child gets all `public` and `protected` members of the parent.

---
#### Examples: Game Entities

> [!example]- C++
> Supports **Multiple Inheritance** (can inherit from many parents).
> ```cpp
> class Enemy {
> public:
>     void attack() { cout << "Attacking!"; }
> };
> 
> // Orc inherits from Enemy
> class Orc : public Enemy {
> public:
>     void grunt() { cout << "Zug zug"; }
> };
> ```

> [!example]- Java
> Supports **Single Inheritance** (one parent) via `extends`.
> ```java
> class Enemy {
>     public void attack() { System.out.println("Attacking!"); }
> }
> 
> class Orc extends Enemy {
>     public void grunt() { System.out.println("Zug zug"); }
> }
> ```

> [!example]- Rust (No Inheritance)
> Rust **does not** support struct inheritance. Instead, it uses **Composition** (containing a struct) or **Traits** (sharing behavior).
> ```rust
> struct Enemy {
>     hp: i32,
> }
> 
> struct Orc {
>     base: Enemy, // Composition: Orc "has an" Enemy struct inside
>     clan: String,
> }
> ```

---
#### The Diamond Problem
If Class D inherits from both B and C, and both B and C inherit from A... does D get two copies of A?
- **C++:** Yes, unless you use `virtual inheritance`.
- **Java:** Avoids this by banning Multiple Inheritance of State (Classes), but allows Multiple Inheritance of Types (Interfaces).
- **Rust:** Avoids this entirely by not having inheritance.

#### Composition over Inheritance
Modern software engineering prefers **Composition**.
- *Inheritance:* You are locked into the parent's structure. Fragile Base Class problem.
- *Composition:* You build complex objects by assembling smaller, independent components. (Lego blocks).

---
