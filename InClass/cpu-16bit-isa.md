# Instruction Sets

An instruction is a binary number that encodes operations to perform on operands.
CPUs decode (split) instructions into an **operation** (opcode) and **operands**.
The **operation** corresponds to what the instruction does (akin to a function).
The **operand(s)** correspond to the data the instruction works on (akin to a list of parameters).
Operands can be literal values (immediate addressing), refer to registers (direct addressing), or refer to locations in memory (indirect addressing).

CPUs differ in their instruction sets.
In a [RISC (Reduced Instruction Set Computing)](http://en.wikipedia.org/wiki/Reduced_instruction_set_computing) CPU (e.g., the ARM CPU in your smartphone):

1. Instructions execute in a single cycle.
2. Instructions are of uniform width.
3. Instructions are limited to:
	* Arithmetic/logic instructions on registers
	* Program control (conditionals, gotos)
	* Load/Store
4. Instructions operate on a large file of general-purpose registers.

In a [CISC (Complex Instruction Set Computing)](http://en.wikipedia.org/wiki/Complex_instruction_set_computer) CPU (e.g., the Intel CPU in your laptop):

1. Instructions can execute in a variable number of cycles.
2. Instructiosn are of varying length.
3. Instructions may perform multiple operations.
4. Instructions operate on special-purpose registers.

## 16-bit CPU ISA
The RISC CPU in cpu-16bit.circ has 16 registers and the following **instruction set**.
The highest order nibble (four bits) are the opcode in this CPU.
This implies that the CPU has (2^4 = 16) instructions.

## Arithmetic/Logic
8 instructions are devoted to arithmetic and logic operations.
After the opcode, each subsequent nibble represents a register address for all instructions, except for the last instruction in this table.

Hex Opcode | Operands                | Assembler mnemonic | C++/Java equivalent
---------- | ----------------------- | ------------------ | ------------------
0          | 3 registers             | ADD  Rd, Ra, Rb    | Rd = Ra + Rb;
1          | 3 registers             | SUB  Rd, Ra, Rb    | Rd = Ra - Rb;
2          | 3 registers             | MUL  Rd, Ra, Rb    | Rd = Ra * Rb;
3          | 3 registers             | DIV  Rd, Ra, Rb    | Rd = Ra / Rb;
4          | 3 registers             | AND  Rd, Ra, Rb    | Rd = Ra & Rb;
5          | 3 registers             | OR   Rd, Ra, Rb    | Rd = Ra | Rb;
6          | 3 registers             | XNOR Rd, Ra, Rb    | Rd = Ra == Rb;
7          | 1 register, 1 immediate | MOV  Rd, mmm       | Rd = mmm; 

## Program Control
4 instructions are devoted to program control (if statements, gotos).
After the opcode, the next nibble represents the register to compare with zero.
The next byte represents an offset to goto relative to the program counter.

Hex Opcode | Operands                | Assembler mnemonic | C++/Java equivalent
---------- | ----------------------- | ------------------ | ------------------
8          | 1 register, 1 immediate | JZE  Ra, mmm       | if (Ra == 0) goto pc+mmm;
9          | 1 register, 1 immediate | JZN  Ra, mmm       | if (Ra != 0) goto pc+mmm;
a          | 1 register, 1 immediate | JZG  Ra, mmm       | if (Ra > 0) goto pc+mmm;
b          | 1 register, 1 immediate | JZL  Ra, mmm       | if (Ra < 0) goto pc+mmm;

## Load/Store
4 instructions are devoted to loading and storing data from/to memory.
After the opcode, the next nibble represents the register to read/write to/from.
The next byte represents a location in memory to read/write to/from.

Hex Opcode | Operands                | Assembler mnemonic | C++/Java equivalent
---------- | ----------------------- | ------------------ | ------------------
c          | 1 register, 1 immediate | LOAD Ra, mmm       | Ra = RAM[mmm];
d          | 1 register, 1 immediate | LOAD Ra            | Ra = RAM[Ra];
e          | 1 register, 1 immediate | STOR Ra, mmm       | RAM[mmm] = Ra;
f          | 1 register, 1 immediate | STOR Ra            | RAM[Ra & 0xff] = Ra;

