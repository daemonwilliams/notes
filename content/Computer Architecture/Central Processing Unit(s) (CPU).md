**The Central Processing Unit (CPU)** is often called "the brain" of the computer. It executes instructions fetched from memory. And while

---
#### Core Components
1.  **Control Unit (CU):** The conductor. It directs the flow of data and tells the ALU what to do.
2.  **Arithmetic Logic Unit (ALU):** The calculator. Performs Math (`ADD`, `SUB`) and Logic (`AND`, `XOR`) operations. (See [[Digital Logic]]).
3.  **Registers:** Fast, on-chip memory locations.
    - **Program Counter (PC):** Holds the memory address of the *next* instruction.
    - **Instruction Register (IR):** Holds the *current* instruction being executed.
    - **Accumulator / General Purpose:** Stores data for ALU operations.
    - **Stack Pointer (SP):** Points to the top of the Call [[Stack(s)]]

> [!INFO] Context Switching 
> The CPU can only run one process at a time (per core). To multitask, the OS saves the current state of **all registers** to RAM (the Process Control Block) and loads the registers of the next process. This is a **Context Switch**.

---
#### The Machine Cycle (Fetch-Decode-Execute)
1.  **Fetch:** The CPU asks RAM for the instruction at the address in the **PC**.
2.  **Decode:** The Control Unit figures out what the bytes mean (e.g., `0101` might mean `ADD`).
3.  **Execute:** The signal is routed to the ALU or I/O to perform the action.
4.  **Store:** Results are written back to a Register or RAM.

---
#### Instruction Set Architecture (ISA)
The ISA is the interface between Hardware and Software. It defines the set of machine instructions a CPU understands.
- **CISC (Complex Instruction Set):** [[x86 Assembly]] (Intel/AMD). Many complex instructions.
- **RISC (Reduced Instruction Set):** ARM (Mobile/Mac), RISC-V. Fewer, simpler instructions.

**From C to CPU:**
$$ \text{C Code} \xrightarrow{\text{Compiler (gcc)}} \text{Assembly (ISA)} \xrightarrow{\text{Assembler}} \text{Machine Code (Binary)} $$

---
