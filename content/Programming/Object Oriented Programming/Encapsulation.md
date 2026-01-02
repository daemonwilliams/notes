#concept #oop
**Encapsulation** is the bundling of data (fields) and the methods that operate on that data into a single unit (Class/Struct), while restricting direct access to some of the object's components.

- **Goal:** Protect the internal state of an object from corruption.
- **Mechanism:** Access Modifiers (`public`, `private`, `protected`).

---
#### The "Black Box" Metaphor
You drive a car using the **Public Interface** (Steering Wheel, Pedals). You do not directly interact with the **Private Implementation** (Fuel Injection, Spark Plugs). This allows the engineer to change the engine without forcing you to relearn how to drive.

---
#### Examples: Bank Account
We want to prevent direct access to `balance` so users can't set it to negative values. They must use `deposit()` and `withdraw()`.

> [!example]- C++
> Uses header-style visibility blocks.
> ```cpp
> class BankAccount {
> private:
>     double balance; // Hidden
> 
> public:
>     BankAccount() { balance = 0.0; }
>     
>     void deposit(double amount) {
>         if (amount > 0) balance += amount;
>     }
> };
> ```

> [!example]- Java
> Explicit modifiers on every field/method.
> ```java
> public class BankAccount {
>     private double balance; // Hidden
> 
>     public void deposit(double amount) {
>         if (amount > 0) {
>             this.balance += amount;
>         }
>     }
> }
> ```

> [!example]- Rust
> Uses the `pub` keyword. Fields are private to the **module** by default.
> ```rust
> pub struct BankAccount {
>     balance: f64, // Private (no 'pub')
> }
> 
> impl BankAccount {
>     pub fn new() -> BankAccount {
>         BankAccount { balance: 0.0 }
>     }
>     
>     pub fn deposit(&mut self, amount: f64) {
>         if amount > 0.0 {
>             self.balance += amount;
>         }
>     }
> }
> ```

---
#### Systems Context
- **C:** C has no true encapsulation. Everything in a header is "public." To simulate "private," C developers use **Opaque Pointers** (Forward declaring a struct in `.h` but defining it in `.c`).
- **Rust:** Encapsulation is enforced at the **Module** level (`mod`), not just the Class level.

---
