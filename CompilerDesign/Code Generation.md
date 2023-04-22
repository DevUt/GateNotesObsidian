
![[Pasted image 20230417002335.png]]

# Issues of Code Generation

- [[#Input to Code Generator|Input to Code Generator]]
- [[#Target Program|Target Program]]
- [[#Memory management|Memory management]]
- [[#Instruction Selection|Instruction Selection]]
- [[#Register Allocation|Register Allocation]]
- [[#Evaluation Order|Evaluation Order]]

## Input to Code Generator
- Input to Code Generator is the intermediate representation of the source program by the front end.
- It also contains the symbol table to determine the  addresses of the data object.
- Prior to code generation the parser has already done input sanitization 

## Target Program
- Output of the generator is the target program
- The output maybe
	- Absolute machine language 
		- Address is fixed
	- Relocatable machine language
	- Assembly language

##  Memory management
- Use symbol table to map objects to memory locations

## Instruction Selection
-  Instruction to machine should be complete
- Instruction speeds and machine idioms are important factors when efficiency of
target program is considered.
- The quality of the generated code is determined by its speed and size.

## Register Allocation
- Instructions involving register operands are shorter and faster than those involving
operands in memory.

The use of register is in two problems
1. Register allocation: Decides which variables would reside in registers
	1. `{a,b,c,d}`
2. Register assignment: Decide which specific register in which these values reside
	1. `{R1 = a, R2 = c, R4 =d, R2 = b}`


Certain machine requires odd even pair for some operands and result

An even-odd register pair is **a pair of consecutive registers that starts with an even register**, such as registers 2 and 3, registers 6 and 7, or registers 10 and 11. To perform a multiplication, the multiplicand is loaded into the odd register of the even-odd pair

## Evaluation Order
- The order in which the computations are performed can affect the efficiency of the
target code.

- Some computation orders require fewer registers to hold intermediate results than
others.


# Basic Block

- A basic block is a sequence of consecutive statements in which flow of control enters at the beginning and leaves at the end without any halt or possibility of branching except at the end.
- Single entry and single exit

## Basic 
- Leader : First line of basic block 

How to find leaders
1. First line of code is leader
2. Any statement that is the target of a conditional or unconditional goto is a leader.
3. Immediate next line to goto is leader


```c
*(1) P := 0
(2) I := 1
*(3) P := P + I
(4) IF P <= 60 GOTO (7)
*(5) P := 0
(6) I := 5
*(7) T1 := I * 2
(8) I := T1 + 1
(9) IF I <= 20 GOTO (3)
*(10) K := P * 3
```

Flow Graph
![[Code Generation 2023-04-16 01.02.10.excalidraw]]
