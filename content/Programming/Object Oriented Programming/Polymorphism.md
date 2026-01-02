#concept #oop #systems
**Polymorphism** ("Many Forms") allows objects of different classes to be treated as objects of a common superclass. It is the ability to call the same method `draw()` on a list of objects, and have the `Circle` draw a circle and the `Square` draw a square.

---
#### 1. Dynamic Polymorphism (Runtime)
This uses **Method Overriding**. The specific method to call is determined at *runtime*.

> [!example]- C++ (Virtual Functions)
> Must use `virtual` keyword and pointers.
> ```cpp
> class Shape {
> public:
>     virtual void draw() { cout << "Generic Shape"; }
> };
> 
> class Circle : public Shape {
> public:
>     void draw() override { cout << "Drawing Circle"; }
> };
> 
> // Usage
> Shape* s = new Circle();
> s->draw(); // Calls Circle::draw()
> ```

> [!example]- Java (Interfaces)
> All non-static methods are virtual by default.
> ```java
> interface Shape { void draw(); }
> 
> class Circle implements Shape {
>     public void draw() { System.out.println("Circle"); }
> }
> ```

> [!example]- Rust (Traits)
> Uses **Trait Objects** (`Box<dyn Trait>`) for dynamic dispatch.
> ```rust
> trait Shape {
>     fn draw(&self);
> }
> 
> struct Circle;
> impl Shape for Circle {
>     fn draw(&self) { println!("Circle"); }
> }
> 
> // Usage
> let shapes: Vec<Box<dyn Shape>> = vec![Box::new(Circle {})];
> ```

---
#### 2. Static Polymorphism (Compile Time)
This uses **Method Overloading** (same name, different arguments) or **Generics**.

> [!example]- C++ / Java (Overloading)
> ```cpp
> void print(int i) { ... }
> void print(string s) { ... }
> ```

> [!example]- Rust (Generics)
> Rust does **not** support traditional overloading. It uses Generics (Monomorphization).
> ```rust
> fn print_item<T: Display>(item: T) {
>     println!("{}", item);
> }
> ```

---
#### Systems Context: The V-Table
How does the computer know which `draw()` to call at runtime?
- **The Virtual Method Table (V-Table):** The compiler creates a hidden lookup table of function pointers for every class with virtual methods.
- **Overhead:** Every object gets a hidden pointer (`vptr`) to this table. Calling a virtual function involves:
    1.  Fetching the `vptr`.
    2.  Looking up the correct function address in the table.
    3.  Jumping to that address.
- **Cost:** Slower than a direct function call. This is why Rust makes dynamic dispatch explicit (`dyn`).

---

