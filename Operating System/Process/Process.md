## Table of Contents
- [[#Process as Data Structure|Process as Data Structure]]
	- [[#Process as Data Structure#Definition|Definition]]
	- [[#Process as Data Structure#Implementation / Representation|Implementation / Representation]]
		- [[#Implementation / Representation#Stack|Stack]]
		- [[#Implementation / Representation#Heap|Heap]]
		- [[#Implementation / Representation#Data Section|Data Section]]
		- [[#Implementation / Representation#Code section|Code section]]
	- [[#Process as Data Structure#Operations available to perform|Operations available to perform]]
- [[#Attributes of Process|Attributes of Process]]
- [[#Context|Context]]
	- [[#Context#Context Switch|Context Switch]]
- [[#Process State|Process State]]
		- [[#Context Switch#New State :|New State :]]
		- [[#Context Switch#Ready state :|Ready state :]]
		- [[#Context Switch#Running State :|Running State :]]
		- [[#Context Switch#Terminated State:|Terminated State:]]
		- [[#Context Switch#Waiting / Blocked State:|Waiting / Blocked State:]]
- [[#CPU Bound vs I/O Bound|CPU Bound vs I/O Bound]]


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
- Stores returning address of function calls
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

**These attributes are stored in PROCESS CONTROL BLOCK (PCB)**
PCB is also known as process descriptor
Stores all GPR , SP etc

## Context 
- The content of the PCB collectively is known as context 

### Context Switch
- ALWAYS performed by **#DISPATCHER**
It happens in two steps

1. Context-save
2. Context-Load 

## Process State
![[Process 2023-03-23 02.07.45.excalidraw]]
Transitions that are made by process' own will
1. Running -> Terminated
2. Running -> Waiting

Lets now visit the  states
####  New State :
All installed processes are in the new state. 


#### Ready state : 
- **Resource allocation** happens 
	- It means that we allocate main memory
	- These process are now in waiting list to run on the processor

#### Running State :
- Doing work on the CPU
- It is of-course still in main memory

#### Terminated State:
- Process has completed its work
- It now does not exist in the main memory
- **Resource deallocation** happens

> Is the Terminated state the same as New State?
> 
> The underlying program is no longer executing, but the process remains in the [process table](https://en.wikipedia.org/wiki/Process_table "Process table") as a _[zombie process](https://en.wikipedia.org/wiki/Zombie_process "Zombie process")_ until its parent process calls the [wait](https://en.wikipedia.org/wiki/Wait_(system_call) "Wait (system call)") [system call](https://en.wikipedia.org/wiki/System_call "System call") to read its [exit status](https://en.wikipedia.org/wiki/Exit_status "Exit status"), at which point the process is removed from the process table, finally ending the process's lifetime. 
> 
> If the parent fails to call `wait`, this continues to consume the process table entry (concretely the [process identifier](https://en.wikipedia.org/wiki/Process_identifier "Process identifier") or PID), and causes a [resource leak](https://en.wikipedia.org/wiki/Resource_leak "Resource leak").

> Are we devoid of resources in terminated state?
> 
#### Waiting / Blocked State:

- Process is waiting for I/O event to happen

Q. $n$ Processes $m$ CPU's $m<n$ 
| State   | Min | Max |
|:------- |:--- |:--- |
| Running | 0   | m   |
| Blocked |   0  |  n   |
| Ready   | 0    |n     |


## CPU Bound vs I/O Bound

CPU Bound -> Intensive  CPU operations
I/O Bound -> Intensive I/O operations
