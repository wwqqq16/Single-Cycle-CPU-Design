# Single Cycle CPU Design

This project aims to build a single cycle CPU that is 8 bits wide and capable of performing various register transfers and ALU operations using point-to-point connections. The CPU will be built incrementally, starting with isolated components, and eventually, the components will be combined to create a functional CPU.

## Instruction Format

The 21-bit instruction format for this CPU is described as follows:

| **Name** | **Bits** | **Function in CPU** | **Description**                                   |
|----------|----------|---------------------|---------------------------------------------------|
| *op*     | 20 - 17  | ALU Control         | Determines the operation to perform and immediate mode. |
| *rd*     | 16 - 14  | Register File Select | Destination register specification.               |
| *rs1*    | 13 - 11  | A Select Unit Control | Primary source register specification.            |
| *rs2*    | 10 - 8   | B Select Unit Control | Secondary source register specification (not always used). |
| *imm*    | 7 - 0    | Immediate Value     | Unsigned input data (not always used).             |

## Operation Description

The table below provides the description of various operations based on their opcode:

| **Operation** | **op [20-17]** | **Description**                                                 |
|---------------|----------------|-----------------------------------------------------------------|
| NOP           | 0000           | No Operation. No registers, other than the PC, should change during this instruction cycle. |
| NOT           | 0001           | Negate *rs1*; place the result in *rd*.                         |
| AND           | 0010           | Bitwise AND of *rs1* and *rs2*; place the result in *rd*.       |
| XOR           | 0011           | Bitwise XOR of *rs1* and *rs2*; place the result in *rd*.       |
| OR            | 0100           | Bitwise OR of *rs1* and *rs2*; place the result in *rd*.        |
| ADD           | 0101           | Add *rs1* and *rs2*; place the result in *rd*.                   |
| SUB           | 0110           | Subtract *rs2* from *rs1*; place the result in *rd*.             |
| MOV           | 0111           | Copy *rs1* as is; place the result in *rd*.                      |
| MOVI          | 1000           | Copy *imm* as is; place the result in *rd*.                      |
| ADDI          | 1001           | Add *rs1* and *imm*; place the result in *rd*.                   |
| SUBI          | 1010           | Subtract *imm* from *rs1*; place the result in *rd*.             |
| SLL           | 1011           | Shift all bits of *rs1* to the left by 1; place the result in *rd*. |
| SRL           | 1100           | Shift all bits of *rs1* to the right by 1; place the result in *rd*. |
| CMP           | 1101           | Compare *rs1* and *rs2*; place the result in *rd*.               |
| HLT           | 1110           | Halt. Stop the CPU from executing any further instructions until a reset. |
| HCF           | 1111           | Halt and Catch Fire. Stop the CPU from executing any further instructions until a reset. |

## Implementation Phases

The CPU will be built incrementally in the following phases:

1. Implementing the ALU
2. Implementing PC and RAM
3. Implementing the Register File
4. Implementing the A Select Unit, B Select Unit, Control Unit, and connecting all components together

## Conclusion

The primary objective of this project is to build a functional single cycle CPU, understanding how various components fit together and build off each other. We combine the components to create a working CPU that performs various ALU operations and register transfers.

