> Program under execution
> An instance of a program
> Unit of execution
> Locus of control 
> Schedule-able / Dispatch-able Unit

## Process as Data Structure

### Definition
Code of the Process

### Implementation / Representation
How it is stored in memory
![[Process 2023-03-23 01.40.24.excalidraw]]

#### Stack
- It handle local variables
- Function calls (frames) are stored here
- Return address
#### Heap 
- Dynamic memory 

#### Data Section
- Stores static / global variables

#### Code section
- Code

### Operations available to perform 
- Create
- Terminate
- Schedule 
- Suspend 
- Wait / Block


## Attributes of Process
- Process ID (PID)
	- Unique Id give to the process
- Program Counter (PC)
	- Location of the **LAST** instruction *executed*
- General Purpose Registers (GPR)
- Stack Pointer
- List of devices
- Type
- Size
- Memory Limit
- Priority 
- State
- List of files

**These attributes are stored in PROCESS CONTROL  BLOCK (PCB)**
PCB is also known as process descriptor
Stores all GPR , SP etc

## Context 
- The content of the PCB collectively is known as context 

### Context Switch
- ALWAYS performed by **DISPATCHER**
It happens in two steps

1. Context-save
2. Context-Load 

## Process State
![[Process 2023-03-23 02.07.45.excalidraw]]
Transitions that are made by process' own will
1. Running -> Terminated
2. Running -> Waiting

