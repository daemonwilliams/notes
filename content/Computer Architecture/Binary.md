**Binary** (Base-2) is the fundamental language of computers. Every piece of data (code, images, integers), is ultimately stored as a sequence of `0`s (off) and `1`s (on).

---

## Units of Binary Data

- **Bit (b):** A single 0 or 1.
- **Byte (B):** 8 bits. Range: $0$ to $255$ ($2^8 - 1$).
  - This is the smallest addressable unit of memory in C (`char`).
- **Word:** The natural size of the CPU architecture (usually 64-bit).

---

## Hexadecimal (Base-16)

We use Hex because it maps perfectly to binary. One Hex digit represents exactly **4 bits**

- `0b1111` = `15` (Decimal) = `0xF` (Hex).
- `0b1010` = `10` (Decimal) = `0xA` (Hex).

**Example:** A 32-bit memory address like `11000000101010000000000100000001` is unreadable. In Hex: `0xC0A80101`.

---

## Integer Overflow & Modular Arithmetic

Computer integers are finite. When a variable exceeds its maximum value (e.g., a standard `uint32_t` exceeds $2^{32}-1$), it wraps around to 0.

- This behavior is mathematically identical to [[Modular Arithmetic]].
- A 32-bit unsigned integer behaves like the ring of integers modulo $2^{32}$.

---

