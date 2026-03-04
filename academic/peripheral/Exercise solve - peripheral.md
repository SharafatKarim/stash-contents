## Ch 2

1. What is the difference between a microprocessor and a single-chip micro-
computer?
	Intel CPU vs Arduino
2. What is a microcontroller? Name one commercially available microcontroller.
	Atmel (now Microchip) ATmega328P
3. What is the difference between:
	(a)  A program counter and the memory address register?
		counter = next instruction
			MAR = address of current location
	(b)  An  accumulator and an instruction register?
		Accumulator = general purpose register
	(c)  A general-purpose  register-based microprocessor and an accumulator 
	based microprocessor. Name a commercially available microprocessor of each type. 
		Accumulator based = operation result always goes to accumulator, 8085
			General purpose based = anything else, 8086
4. Assuming signed numbers, find the sign, carry, zero, and overflow flags of...
	Self study
5. What are PUSH and POP operations in the stack?
	1. Easy
6. Suppose that a 16-bit microprocessor has a 16-bit stack pointer and uses a 16-bit register to access the stack from the top. Assume that initially the stack pointer and the 16-bit register contain 20CO,, and 0205,, respectively. After the PUSH operation:
		(a) What are the contents of the stack pointer? **20BE**
		(b)  What are the contents of memory locations 20BEl, and 20BF,,?
			20BF= 02, 20BE = 05
7. Assuming the microprocessor architecture of Figure 2.9(a), write down a possible
sequence of microinstructions for finding the one’s complement of an 8-bit
number. Assume that the number is already in the register.
8. What is pipelining?
		overlapped instruction
9. Summarize the branch prediction feature of the Pentium.
	1. predicting which branch will run next
10. What is the basic difference between program execution by a conventional microprocessor and a 32-bit microprocessor.
	1. self study
11. What is the difference between Scalar and Superscalar microprocessors? Name one example of each.

| **Feature**    | **Scalar Microprocessor**                     | **Superscalar Microprocessor**                                       |
| -------------- | --------------------------------------------- | -------------------------------------------------------------------- |
| **Execution**  | Executes **one** instruction per clock cycle. | Executes **multiple** instructions per clock cycle.                  |
| **Pipelines**  | Has a single pipeline.                        | Has multiple, parallel pipelines.                                    |
| **Complexity** | Simpler; instructions are processed in order. | Complex; requires logic to is patch instructions to available pipes. |
| **Example**    | **Intel 80486**                               | **Intel Pentium** (or modern Core i7/Ryzen)                          |

12. Discuss the basic features of RISC and CISC in terms of the Pentium Pro.
	1. CISC = compatibility, RISC = performance

## Ch 3

1. What is the basic difference between main memory and secondary memory?
2. A microprocessor has 24 address pins. What is the maximum size of the main memory? 2^24
3. Can the microprocessor execute programs directly in hard disk? Explain your answer. **no**
4. What is the basic difference between: 
	1. (a) EPROM and EEPROM? 
	2. (b) SRAM and DRAM?
5. Given a memory with a 14-bit address and an 8-bit word size.
	1. (a) How many bytes can be stored in this memory? 2^14 x 8
	2. (b) If this memory were constructed from 1K x 1 RAMS, how many memory chips would be required? just divide them
	3. (c)  How many bits would be used for chip select? log 16
6. What are the main differences between CD and DVD memories?
7. Draw a block diagram showing the address and data lines for the 2732, and 2764 EPROM chips.
8. (a) How many address and data lines are required for a 1M x 16 memory chip?
	(b) What is the size of a decoder with one chip enable (E) to obtain a 64K x 32 memory from K x 8 chips? Where are the inputs and outputs of the decoder connected?
	