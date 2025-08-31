- Specified syntax and semantics on each architecture

| Component        | Description                                                 | Example                            |
| ---------------- | ----------------------------------------------------------- | ---------------------------------- |
| Instructions     | opcode operand_list                                         | add rax, 1, mov rsp, rax, push rax |
| Registers        | Store operands, address, and instructions temporarily       | rax, rsp, rip                      |
| Memory Addresses | Address in which instructions are stored, (point/registers) | 0x44d0, $rax                       |
| Data Types       | Type of stored data                                         | byte, word, double word            |
#### 2 Types of ISA widely used
1. CISC (Complex Instruction Set Computer) -> Intel/AMD
2. RISC (Reduced Instruction Set Computer) -> ARM/Apple

| Area                             | CISC                                                        | RISC                                                |
| -------------------------------- | ----------------------------------------------------------- | --------------------------------------------------- |
| `Complexity`                     | Favors complex instructions                                 | Favors simple instructions                          |
| `Length of instructions`         | Longer instructions - Variable length 'multiples of 8-bits' | Shorter instructions - Fixed length '32-bit/64-bit' |
| `Total instructions per program` | Fewer total instructions - Shorter code                     | More total instructions - Longer code               |
| `Optimization`                   | Relies on hardware optimization (in CPU)                    | Relies on software optimization (in Assembly)       |
| `Instruction Execution Time`     | Variable - Multiple clock cycles                            | Fixed - One clock cycle                             |
| `Instructions supported by CPU`  | Many instructions (~1500)                                   | Fewer instructions (~200)                           |
| `Power Consumption`              | High                                                        | Very low                                            |
| `Examples`                       | Intel, AMD                                                  | ARM, Apple                                          |
