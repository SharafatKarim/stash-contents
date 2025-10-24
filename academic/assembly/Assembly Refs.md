# Minimal x86 Opcode Reference

|                            |                                                                                               |                                  |
| -------------------------- | --------------------------------------------------------------------------------------------- | -------------------------------- |
| **Opcode**                 | **Description**                                                                               | **Example**                      |
| **Data Transfer**          |                                                                                               |                                  |
| **MOV**                    | Move data (copy `src` to `dest`).                                                             | `mov eax, ebx`                   |
| **CMOV**                   | Conditional Move (e.g., `CMOVE` for "move if equal").                                         | `cmove eax, ebx ; move if ZF=1`  |
| **XCHG**                   | Exchange contents of two operands.                                                            | `xchg eax, ebx`                  |
| **LEA**                    | Load Effective Address (compute address of `src`, store in `dest`).                           | `lea eax, [ebx + 8]`             |
| **LDS/LES/LFS/LGS/LSS**    | Load Far Pointer (load `mem` into `reg` and segment register).                                | `lds esi, [my_ptr]`              |
| **MOVZX**                  | Move with Zero-Extend (copy small `src` to large `dest`, fill high bits with 0).              | `movzx eax, bl`                  |
| **MOVSX**                  | Move with Sign-Extend (copy small `src` to large `dest`, fill high bits with `src` sign bit). | `movsx eax, bl`                  |
| **XLAT**                   | Table Look-up Translation (replace `AL` with `[EBX + AL]`).                                   | `xlat`                           |
| **Stack Operations**       |                                                                                               |                                  |
| **PUSH**                   | Push onto stack (decrement stack pointer, store operand).                                     | `push eax`                       |
| **POP**                    | Pop from stack (load operand, increment stack pointer).                                       | `pop ebx`                        |
| **PUSHA/PUSHAD**           | Push all general-purpose registers.                                                           | `pushad`                         |
| **POPA/POPAD**             | Pop all general-purpose registers.                                                            | `popad`                          |
| **PUSHF/PUSHFD**           | Push `EFLAGS` register onto stack.                                                            | `pushf`                          |
| **POPF/POPFD**             | Pop `EFLAGS` register from stack.                                                             | `popf`                           |
| **Binary Arithmetic**      |                                                                                               |                                  |
| **ADD**                    | Add (unsigned/signed).                                                                        | `add eax, 10`                    |
| **ADC**                    | Add with Carry (add operands + carry flag).                                                   | `adc eax, ebx`                   |
| **SUB**                    | Subtract (unsigned/signed).                                                                   | `sub ecx, eax`                   |
| **SBB**                    | Subtract with Borrow (subtract operands - carry flag).                                        | `sbb eax, 0`                     |
| **INC**                    | Increment by 1.                                                                               | `inc ecx`                        |
| **DEC**                    | Decrement by 1.                                                                               | `dec edx`                        |
| **MUL**                    | Unsigned Multiply (`(EDX:EAX) = EAX * src`).                                                  | `mul ebx`                        |
| **IMUL**                   | Signed Multiply.                                                                              | `imul ebx`                       |
| **DIV**                    | Unsigned Divide (`EAX = (EDX:EAX) / src`).                                                    | `div ecx`                        |
| **IDIV**                   | Signed Divide.                                                                                | `idiv ecx`                       |
| **NEG**                    | Negate (two's complement).                                                                    | `neg eax`                        |
| **CMP**                    | Compare (sets flags by doing `dest - src` without storing result).                            | `cmp eax, 10`                    |
| **Logical & Bitwise**      |                                                                                               |                                  |
| **AND**                    | Bitwise AND.                                                                                  | `and eax, 0xFF`                  |
| **OR**                     | Bitwise OR.                                                                                   | `or ebx, 1`                      |
| **XOR**                    | Bitwise Exclusive OR.                                                                         | `xor eax, eax ; (zeros EAX)`     |
| **NOT**                    | Bitwise NOT (one's complement).                                                               | `not ecx`                        |
| **TEST**                   | Test (sets flags by doing `dest & src` without storing result).                               | `test al, 0x80`                  |
| **Shift & Rotate**         |                                                                                               |                                  |
| **SHL/SAL**                | Shift Logical/Arithmetic Left.                                                                | `shl eax, 2`                     |
| **SHR**                    | Shift Logical Right (fill with 0).                                                            | `shr ebx, 1`                     |
| **SAR**                    | Shift Arithmetic Right (fill with sign bit).                                                  | `sar edx, 4`                     |
| **ROL**                    | Rotate Left.                                                                                  | `rol al, 1`                      |
| **ROR**                    | Rotate Right.                                                                                 | `ror al, 1`                      |
| **RCL**                    | Rotate Left through Carry.                                                                    | `rcl ebx, 1`                     |
| **RCR**                    | Rotate Right through Carry.                                                                   | `rcr ebx, 1`                     |
| **Control Flow**           |                                                                                               |                                  |
| **JMP**                    | Unconditional Jump.                                                                           | `jmp my_label`                   |
| **CALL**                   | Call procedure (push return address, jump).                                                   | `call my_function`               |
| **RET**                    | Return from procedure (pop address, jump).                                                    | `ret`                            |
| **JCXZ/JECXZ**             | Jump if `CX`/`ECX` is zero.                                                                   | `jecxz is_zero`                  |
| **LOOP**                   | Loop (decrement `ECX`, jump if not zero).                                                     | `loop my_loop`                   |
| **LOOPE/LOOPZ**            | Loop while Equal/Zero (decrement `ECX`, jump if not zero AND `ZF=1`).                         | `loope my_loop`                  |
| **LOOPNE/LOOPNZ**          | Loop while Not Equal/Not Zero (decrement `ECX`, jump if not zero AND `ZF=0`).                 | `loopne my_loop`                 |
| **String Operations**      | _(Operate on `[ESI]` and/or `[EDI]`, update pointers based on `DF`)_                          |                                  |
| **MOVS**                   | Move String (`[ESI]` to `[EDI]`).                                                             | `movsb` (byte), `movsw`, `movsd` |
| **LODS**                   | Load String (`[ESI]` to `AL/AX/EAX`).                                                         | `lodsb` (byte), `lodsw`, `lodsd` |
| **STOS**                   | Store String (`AL/AX/EAX` to `[EDI]`).                                                        | `stosb` (byte), `stosw`, `stosd` |
| **CMPS**                   | Compare String (`[ESI]` with `[EDI]`).                                                        | `cmpsb` (byte), `cmpsw`, `cmpsd` |
| **SCAS**                   | Scan String (compare `AL/AX/EAX` with `[EDI]`).                                               | `scasb` (byte), `scasw`, `scasd` |
| **INS**                    | Input from Port to String (read from `DX` port to `[EDI]`).                                   | `insb` (byte), `insw`, `insd`    |
| **OUTS**                   | Output String to Port (write `[ESI]` to `DX` port).                                           | `outsb` (byte), `outsw`, `outsd` |
| **REP**                    | Repeat prefix (repeats string op `ECX` times).                                                | `rep movsb`                      |
| **REPE/REPZ**              | Repeat while Equal/Zero.                                                                      | `repe cmpsb`                     |
| **REPNE/REPNZ**            | Repeat while Not Equal/Not Zero.                                                              | `repne scasb`                    |
| **BCD & ASCII Arithmetic** |                                                                                               |                                  |
| **DAA**                    | Decimal Adjust after Addition (corrects `AL` after `ADD` on BCD).                             | `daa`                            |
| **DAS**                    | Decimal Adjust after Subtraction (corrects `AL` after `SUB` on BCD).                          | `das`                            |
| **AAA**                    | ASCII Adjust after Addition.                                                                  | `aaa`                            |
| **AAS**                    | ASCII Adjust after Subtraction.                                                               | `aas`                            |
| **AAM**                    | ASCII Adjust after Multiplication.                                                            | `aam`                            |
| **AAD**                    | ASCII Adjust before Division.                                                                 | `aad`                            |
| **Flag (EFLAGS) Control**  |                                                                                               |                                  |
| **CLC**                    | Clear Carry Flag (`CF=0`).                                                                    | `clc`                            |
| **STC**                    | Set Carry Flag (`CF=1`).                                                                      | `stc`                            |
| **CLI**                    | Clear Interrupt Flag (disable maskable interrupts).                                           | `cli`                            |
| **STI**                    | Set Interrupt Flag (enable maskable interrupts).                                              | `sti`                            |
| **CLD**                    | Clear Direction Flag (`DF=0`, string ops increment).                                          | `cld`                            |
| **STD**                    | Set Direction Flag (`DF=1`, string ops decrement).                                            | `std`                            |
| **LAHF**                   | Load `AH` from Flags (copy `SF,ZF,AF,PF,CF` to `AH`).                                         | `lahf`                           |
| **I/O & Interrupts**       |                                                                                               |                                  |
| **IN**                     | Input from port (read from port to `AL/AX/EAX`).                                              | `in al, 0x60`                    |
| **OUT**                    | Output to port (write `AL/AX/EAX` to port).                                                   | `out 0x61, al`                   |
| **INT**                    | Software Interrupt (call interrupt vector `n`).                                               | `int 0x80`                       |
| **INT3**                   | Breakpoint Interrupt (1-byte `INT 3`).                                                        | `int3`                           |
| **INTO**                   | Interrupt on Overflow (call `INT 4` if `OF=1`).                                               | `into`                           |
| **IRET/IRETD**             | Return from Interrupt.                                                                        | `iret`                           |