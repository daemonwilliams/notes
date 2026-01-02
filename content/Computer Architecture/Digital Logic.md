**Digital Logic** is the foundation of all computing. At the physical level, computers are just vast networks of [[Transistor(s)]] that implement [[Boolean Logic]]
#### Logic Gates
A **Gate** is a physical device that implements a Boolean function.
- **0 (Low/No Voltage):** False.
- **1 (High Voltage):** True.

| Gate     |         Symbol         | Mathematic Symbol | Output                                 |
| :------- | :--------------------: | :---------------- | -------------------------------------- |
| **AND**  |      $A \cdot B$       | $\land$           | True if and only if both inputs are 1. |
| **OR**   |        $A + B$         | $\lor$            | True if at least one input is 1.       |
| **NOT**  |       $\bar{A}$        | $\neg$            | True if input is 0. (Inverts Input).   |
| **XOR**  |      $A \oplus B$      | $\oplus$          | True if inputs are different.          |
| **NOR**  |                        |                   | True if and only if both inputs are 0. |
| **NAND** | $\overline{A \cdot B}$ | $\neg(\land)$     | True unless both inputs are 1.         |

**Universal Gates:**
NAND and NOR are "Universal." You can build *any* other gate (AND, OR, NOT) using only NAND gates. This is crucial for manufacturing [[Central Processing Unit(s) (CPU)]] cheaply.

---
#### Combinational Logic
Circuits where the output depends *only* on the current inputs (no memory).
- **Adder:** A circuit that adds binary numbers.
    - *Half Adder:* Adds 2 bits (Sum + Carry). Uses XOR and AND.
    - *Full Adder:* Adds 3 bits (A, B, Carry-In).

#### Sequential Logic
Circuits that have **Memory** (State). The output depends on inputs *and* the previous state.
- **Flip-Flop:** A circuit that stores 1 bit of data.
- **Clock:** A signal that oscillates (0 -> 1 -> 0) to synchronize state updates.
- **Registers:** A collection of Flip-Flops used to store a "Word" (e.g., 64 bits).

---
#### From Logic to C
When you write `if (a && b)` or use bitwise operators like `a & b` (see **[[Bitwise Operations]]**), the [[Central Processing Unit(s) (CPU)]] executes instructions that physically route electrons through a series of AND gates in the ALU.

-> Expand Later
