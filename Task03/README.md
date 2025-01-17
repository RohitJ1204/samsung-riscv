# BASICS
 ## Instruction Types and Fields
The RISC-V instructions are categorized into types based on their field organization. Each type has specific fields like opcode, func3, func7, immediate values, and register numbers. The types include:
- **R-type**: Register type
- **I-type**: Immediate type
- **S-type**: Store type
- **B-type**: Branch type
- **U-type**: Upper immediate type
- **J-type**: Jump type
## Opcode and Function Fields
- **Opcode**: Determines the type of instruction.
- **func3** and **func7**: Further specify the operation within the instruction type.
  - Example: In R-type instructions, func3 and func7 differentiate between operations like addition and subtraction.
## Immediate Values and Registers
- **Immediate Values**: Encoded in specific fields within the instruction.
  - Example: I-type instructions use a 12-bit immediate value field along with source and destination registers.
- **Registers**: Specified in fields such as rd (destination register), rs1 (source register 1), and rs2 (source register 2).
  ## Arithmetic Instructions
- **ADD**: Adds values in two registers and stores the result in a third register.
  - Example: `ADD rd, rs1, rs2` (rd = rs1 + rs2)
- **ADDI**: Adds a register and an immediate value (constant) and stores the result.
  - Example: `ADDI rd, rs1, imm` (rd = rs1 + imm)
## Logical Instructions
- **AND, OR, XOR**: Perform bitwise operations.
  - Example: `AND rd, rs1, rs2` (rd = rs1 & rs2)
## Branch Instructions
- **BEQ**: Branch if equal.
  - Example: `BEQ rs1, rs2, offset` (if rs1 == rs2, PC = PC + offset)
- **BNE**: Branch if not equal.
  - Example: `BNE rs1, rs2, offset` (if rs1 != rs2, PC = PC + offset)
## Load and Store Instructions
- **LW**: Load word from memory.
  - Example: `LW rd, offset(rs1)` (rd = memory[rs1 + offset])
- **SW**: Store word to memory.
  - Example: `SW rs1, offset(rs2)` (memory[rs2 + offset] = rs1)
## Special Instructions
- **AUIPC**: Add upper immediate to PC.
  - Example: `AUIPC rd, imm` (rd = PC + imm << 12)
## Branch and Jump Instructions
- **Jump (J)**: Unconditional branch to a specified address.
- **Branch (B)**: Conditional branch based on a comparison.
### Detailed Decoding

#### 1. **Instruction: `addi sp, sp, -16`**
   - **Opcode**: `0010011` (I-type format)
   - **rs1**: `sp` (`x2`)
   - **rd**: `sp` (`x2`)
   - **Immediate**: `-16` (`0xFFF0`)
   - **Machine Code**: `ff010113`
![addi sp, sp, -16](https://github.com/RohitJ1204/samsung-riscv/blob/afc3dfd1d99219cfdddea8f3b042bcfc90ad05c0/Task03/Instruction1.png)
#### 2. **Instruction: `sd ra, 8(sp)`**
   - **Opcode**: `0100011` (S-type format)
   - **rs1**: `sp` (`x2`)
   - **rs2**: `ra` (`x1`)
   - **Immediate**: `8`
   - **Machine Code**: `00113423`
![sd ra, 8(sp)](https://github.com/RohitJ1204/samsung-riscv/blob/afc3dfd1d99219cfdddea8f3b042bcfc90ad05c0/Task03/Instruction1.png)
#### 3. **Instruction: `li a5, 50`**
   - Combines `lui` and `addi`.
   - **Machine Code**: `03200793`

#### 4. **Instruction: `addiw a5, a5, -1`**
   - **Opcode**: `0011011` (I-type format)
   - **rs1**: `a5` (`x15`)
   - **rd**: `a5` (`x15`)
   - **Immediate**: `-1` (`0xFFFFFFFF`)
   - **Machine Code**: `fff7879b`

#### 5. **Instruction: `bnez a5, 10190`**
   - Combines branch operation (`beq`) with zero comparison.
   - **Machine Code**: `fe079ee3`

#### 6. **Instruction: `lui a2, 0x1`**
   - **Opcode**: `0110111` (U-type format)
   - **rd**: `a2` (`x12`)
   - **Immediate**: `0x1`
   - **Machine Code**: `00001637`

#### 7. **Instruction: `addi a2, a2, -1546`**
   - **Opcode**: `0010011` (I-type format)
   - **rs1**: `a2` (`x12`)
   - **rd**: `a2` (`x12`)
   - **Immediate**: `-1546` (`0xFFFFF9EA`)
   - **Machine Code**: `9f660613`

#### 8. **Instruction: `li a1, 100`**
   - Combines `lui` and `addi`.
   - **Machine Code**: `06400593`

#### 9. **Instruction: `lui a0, 0x21`**
   - **Machine Code**: `00021537`

#### 10. **Instruction: `addi a0, a0, 400`**
    - **Machine Code**: `19050513`

#### 11. **Instruction: `jal ra, 10418`**
    - **Machine Code**: `26c000ef`

#### 12. **Instruction: `li a0, 0`**
    - **Machine Code**: `00000513`

#### 13. **Instruction: `ld ra, 8(sp)`**
    - **Machine Code**: `00813083`

#### 14. **Instruction: `addi sp, sp, 16`**
    - **Machine Code**: `01010113`

#### 15. **Instruction: `ret`**
    - **Machine Code**: `00008067`

| **Address** | **Instruction Code** | **Mnemonic**       | **Description**                 | **Type** | **Machine Code** |
|-------------|-----------------------|--------------------|---------------------------------|----------|------------------|
| `10184`     | `ff010113`           | `addi sp,sp,-16`   | Add immediate to stack pointer | I        | `ff010113`       |
| `10188`     | `00113423`           | `sd ra,8(sp)`      | Store doubleword               | S        | `00113423`       |
| `1018c`     | `03200793`           | `li a5,50`         | Load immediate                 | I        | `03200793`       |
| `10190`     | `fff7879b`           | `addiw a5,a5,-1`   | Add immediate word             | I        | `fff7879b`       |
| `10194`     | `fe079ee3`           | `bnez a5,10190`    | Branch if not equal to zero    | SB       | `fe079ee3`       |
| `10198`     | `00001637`           | `lui a2,0x1`       | Load upper immediate           | U        | `00001637`       |
| `1019c`     | `9f660613`           | `addi a2,a2,-1546` | Add immediate                  | I        | `9f660613`       |
| `101a0`     | `06400593`           | `li a1,100`        | Load immediate                 | I        | `06400593`       |
| `101a4`     | `00021537`           | `lui a0,0x21`      | Load upper immediate           | U        | `00021537`       |
| `101a8`     | `19050513`           | `addi a0,a0,400`   | Add immediate                  | I        | `19050513`       |
| `101ac`     | `26c000ef`           | `jal ra,10418`     | Jump and link                  | UJ       | `26c000ef`       |
| `101b0`     | `00000513`           | `li a0,0`          | Load immediate                 | I        | `00000513`       |
| `101b4`     | `00813083`           | `ld ra,8(sp)`      | Load doubleword                | I        | `00813083`       |
| `101b8`     | `01010113`           | `addi sp,sp,16`    | Add immediate to stack pointer | I        | `01010113`       |
| `101bc`     | `00008067`           | `ret`              | Return from subroutine         | I        | `00008067`       |

