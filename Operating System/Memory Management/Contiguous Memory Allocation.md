Our memory is divided into two portion, one for user and one for operating system. 

We can place the operating system in either high memory or low memory. The major factor in the decision is the location of the interrupt vector. Since the interrupt vector is often in the  low memory. Thus we usually place the operating system in a low memory as well. ^cf2703

>[!homework]
>Find what the above para is trying to convey.

We now need to allocate memory to the user processes.

In contiguous memory allocation each process is contained in a single contiguous section of memory.

>[!example]
>Non contiguous memory allocation
0x100 -> a
0x102 -> b
0x200 ->a

Operating system's memory utilization is also not fixed. For example, the device drivers when not in use are not allocated memory. Such code is sometimes called as *transient* operating system code; it comes and goes as needed. 

# Memory allocation

Now one of the simplest method for allocating memory is to divide the memory into several fixed sized partitions. Each partition may contain only process. Thus the [[Introduction to Os#Degree of Multi-programming|degree of multi-programming]] is bound by the number of partitions. This is known as the fixed sized partition scheme.

![[Contiguous Memory Allocation 2023-05-07 01.30.43.excalidraw]]

An empty block is known as a *hole*.

When a process arrives if the hole is too large for the process we split that hole. One is utilized another one remains a hole. If a hole is adjacent to another hole, they maybe merged to form a larger hole. This procedure is a particular instance of the general *dynamic storage allocation*.

How to search for holes?

### First fit
- Allocate the first hole that is big enough. 
- Searching can start either at the beginning of the set of hole or where the \[previous first fit search ended.\] (Next fit)
- We stop searching as soon as we find a free hole.
- $\Theta(n)$ for a single process
- $\Theta(m\times n)$  for $m$ process and $n$ holes

### Best fit
- Allocate the smallest hole that is big enough
- **This strategy produces the smallest leftover hole**

### Worst fit
- Allocate the largest hole
- **This strategy produces the largest leftover hole**

# Fragmentation

## External fragmentation
Both the first fit and the best fit strategy suffer from *external fragmentation*.

![[Contiguous Memory Allocation 2023-05-07 01.49.29.excalidraw]]
When there is enough total memory to satisfy a request but the available spaces are not contagious, i.e storage is fragments into a large number of holes. This is known as external fragmentation.

Statistical analysis of first fit, for instance, reveals that, even with some optimization given N allocated blocks, another $0.5N$ blocks would be lost to fragmentation. This property is known as the *50-percent rule.*

### Solution: Compaction
Shuffle memory contents so that all the available space forms a single large hole. Squeeze to one side.

>[!Question]
>Which of the compile time, load time and execution time would support compaction?
>>[!answer]-
>>Neither compile time, load time support compaction. Only execution time supports. Because  compile and load time has the physical address in the binary image of the process.

## Internal Fragmentation

Suppose there is a process which requires 18,524 bytes and the available hole is of 18,526 bytes. After placing the process it would create a hole of 2 bytes. The overhead of tracking this hole would be higher than the hole itself. To solve this we allocate the process the entire hole of 18,526 bytes. This causes internal fragmentation - memory internal to a partition but is not being used.
