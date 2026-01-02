#systems #math
**Bitwise Operations** allow you to manipulate individual bits within a byte or word. These operators map directly to the [[Computer Architecture/Digital Logic|Logic Gates]] (AND, OR, XOR) inside the [[Central Processing Unit(s) (CPU)|CPU]]'s ALU. In Systems and Embedded programming, this is how you interact with hardware registers.

---

#### The Operators

| Operator | Name            | Function                              | Example (A=5 `0101`, B=3 `0011`) |
| :------: | :-------------- | :------------------------------------ | :------------------------------- |
|   `&`    | **AND**         | 1 if both bits are 1.                 | `A & B` = `0001` (1)             |
|   `\|`   | **OR**          | 1 if either bit is 1.                 | `A \| B` = `0111` (7)            |
|   `^`    | **XOR**         | 1 if bits are different.              | `A ^ B` = `0110` (6)             |
|   `~`    | **NOT**         | Inverts all bits (One's Complement).  | `~A` = `1010` (unsigned 4-bit)   |
|   `<<`   | **Left Shift**  | Shifts bits left (Multiply by $2^n$). | `A << 1` = `1010` (10)           |
|   `>>`   | **Right Shift** | Shifts bits right (Divide by $2^n$).  | `A >> 1` = `0010` (2)            |

---

#### Bitmasking Techniques

Controlling specific bits without affecting others (e.g., turning on an LED connected to Pin 5).

**1. Setting a Bit (Turn ON)**
Use **OR** (`|`) with a mask.

```c
// Turn on the 3rd bit (index 2)
x = x | (1 << 2);
```

**2. Clearing a Bit (Turn OFF)**
Use **AND** (`&`) with the **NOT** (`~`) of the mask.

```c
// Turn off the 3rd bit
x = x & ~(1 << 2);
```

**3. Toggling a Bit (Flip)**
Use **XOR** (`^`) with a mask.

```c
// Flip the 3rd bit
x = x ^ (1 << 2);
```

**4. Checking a Bit**
Use **AND** (`&`).

```c
if (x & (1 << 2)) {
    // 3rd bit is set
}
```

---
