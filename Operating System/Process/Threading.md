Thread is a unit execution.

![[Pasted image 20230610025620.png]]

Every thread has its own stack. 
*Heap memory is same for all threads*. 

Per process items             | Per thread items
------------------------------|-----------------
Address space                 | Program counter
Global variables              | Registers
Open files                    | Stack
Child processes               | State
Pending alarms                |
Signals and signal handlers   |
Accounting information        |


# Types

## User level threads
These are created by the help of library. 

Like Go and POSIX threads. These are managed by the library, inside the process. 
These are extremely efficient. 

The OS doesn't recognize these different threads. For it everything is just inside one process.

![[Threading 2023-06-10 03.01.25.excalidraw]]

When one thread is blocked, everything gets blocked.

## Kernel Level threads

These threads are managed and created the kernel. The operating system schedules them individually. 
But these are expensive. 

# Mapping

We actually need to map user threads to the kernel threads. 

![[Pasted image 20230610030630.png]]



