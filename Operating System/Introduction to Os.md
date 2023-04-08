# Parts of OS
![[Drawing 2023-03-23 00.23.49.excalidraw]]  
## Kernel 

This is the core of OS
It provides interface to the hardware and software
	The drivers are in the kernel
	Application -> Kernel -> Driver -> Hardware

It special, it has the highest **privilege** in the system
Privilege -> Authority it has

It handles memory directly


## Shell 
It allows us to directly interact with [[#Kernel]]

# Dual Mode
Any application runs in two modes
1. User mode 
2. Kernel/System/ Privileged Mode

We use `ModeBit` to set which mode we are in
UserMode | Kernel Mode
-------| -----
ModeBit = 1 | ModeBit = 0
We can remember this by Modebit tells us if we are in UserMode
The switch between the modebit happens automatically 

![[Drawing 2023-03-26 20.03.02.excalidraw]]
![[Drawing 2023-03-23 01.07.12.excalidraw]]

# Types of Operating System
1. Uni-Programming OS
2. Multi-Programming OS
3. Multi- Tasking OS / Time Sharing OS
4. Multi-User OS
5. Multi-Processing OS
6. Embedded OS
7. Real Time OS
8. Handheld device OS

## Uni-Programming OS
- OS allows only 1 process (except OS) to be in memory
- Single process can't keep CPU alive and do I/O simultaneously 
-  *Degree of Multi Programming  = 1* 

## Multi Programming OS
- Os allows more than 1 process to be in memory 
- Better Utilization of memory

### Types of Multi-programming OS
Types :
1. Preemptive ^3ead25
	- The OS can forcefully without the will of the process remove it from the CPU
	- [This requires Hardware support](https://cs.stackexchange.com/questions/135990/os-why-is-it-necessary-to-have-hardware-support-for-implementing-preemptive-sch)

1. Non- Preemptive / *Co-operative*  ^366a2a
	- The process leaves when it wishes[]()

### Degree of Multi-programming
- It is the number of processes that exist in **MAIN MEMORY**
- Degree of multi programming $\alpha$ CPU utilization

Qustions:
[Gate 2001](https://gateoverflow.in/738)




## Multi Tasking OS / Time Sharing

- Extension of multi programming OS
- Uses Round Robin

## Multi User OS

- This allows multiple users to use the same terminal simultaneously

## Multi Processing OS
- Multiple Processors
Types
1. Tightly Coupled (Shared Memory)
	1. Share the same RAM
2. Loosely Coupled  (Distributed System)
	1. Each CPU has different Memory

## Embedded OS

- Developed for specific device purpose to increase efficiency 

## RTOS 

- It should handle deadlines very precisely 
- e.g Rocket Launch, Pacemaker, Airline stuff

Types 
1. Hard RTOS 
2. Soft RTOS (some relaxations)