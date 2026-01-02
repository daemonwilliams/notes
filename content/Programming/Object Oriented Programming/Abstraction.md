#concept #oop
**Abstraction** is the process of hiding complex implementation details and showing only the essential features of an object. It reduces complexity and allows the user to interact with a simplified **Interface**.

- **Example:** When you press the "Brake" pedal, you don't need to know if the car uses Hydraulic pads or Regenerative braking. You just know "Car Stops".

---
#### Mechanisms of Abstraction

**1. Abstract Classes (Partial Abstraction)**
A class that cannot be instantiated on its own and may contain a mix of implemented methods and abstract (empty) methods.
- *Use Case:* Sharing common code among related classes (e.g., `Animal` has `sleep()` logic, but `makeSound()` is abstract).

**2. Interfaces (Total Abstraction)**
A contract that specifies **what** a class must do, but not **how**. It contains only method signatures (and sometimes constants).
- *Use Case:* Defining a capability (e.g., `Drawable`, `Serializable`) that unrelated classes can share.

---
#### Language Comparison

> [!example]- C++ (Pure Virtual)
> No `interface` keyword. Uses classes with pure virtual functions (`= 0`).
> ```cpp
> class Drawable {
> public:
>     virtual void draw() = 0; // Pure Virtual
> };
> ```

> [!example]- Java
> Distinct keywords for `abstract class` and `interface`.
> ```java
> interface Drawable {
>     void draw(); // Implicitly public abstract
> }
> ```

> [!example]- Rust (Traits)
> **Traits** are the sole mechanism for abstraction.
> ```rust
> trait Drawable {
>     fn draw(&self);
>     
>     // Default Implementation (Optional)
>     fn description(&self) {
>         println!("I am drawable");
>     }
> }
> ```

---

