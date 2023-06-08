
Whenever we need the page, only then we bring it in the memory. 

For this we need special provision, to check whether a page is in main memory or not. We use the valid/invalid bit. If its invalid then the page is not in the main memory. 

What happens if the process tries to access a page that was not brought into memory? This is known as *Page fault*.

How to handle page fault :
1. Trap to OS
2. Save register and process state
3. Determine that the interrupt was a page fault.
4. Check the page reference, is that legal? 
5. Issue a read from disk to free frame
6. While waiting allocate CPU to other (optional)
7. Receive interrupt from Disk that process has completed
....


At the start of the process, if no pages of the process are present then it is known as *Pure demand* paging. Never bring a page into memory until its required.

## Copy - on - write


----


# Page replacement

The page replacement algorithms decide which is the *victim frame*, and remove it from memory.

Whenever we remove a victim frame, we need to check whether the frame was modified. If it was modified then it needs to written back to the disk. For this purpose *Modify bit / Dirty Bit* is used. 

## FIFO

As name suggests, the first one in is the first one out.

Questions :

The process has 4 frames,

The reference string.

1,2,3,4,1,2,5,1,2,3,4,5

Find no. of page faults for frame size = 3 and frame size = 4. 


## Belady's Anomaly

We usually think that if we increase the number of frames, then the page fault would decrease. 

For some page replacement algorithms, the page-fault *increases* as the number of allocated frames increases. 


For *STACK Based* algorithms the belady's anomaly doesn't work. 
A stack algorithm is  an algorithm for which it can be shown that the set of pages in memory for n frames is always a subset of the set of pages that would be in memory with n+1 frames.

e.g LRU, optimal etc

FIFO suffers from belady's anomaly.

## Optimal Page replacement

- Replace the page that will not be used for the longest period of time.

## LRU Page replacement

- Least recently used page replacement
- Replace the page that hasn't been used in the longest. 
- We use stack based algorithm to implement LRU. 
- One another method to implement LRU is Counters. 
	- We associate a counter with every entry. 

## Most recently used 
- Replace the page that was used most recently


>[!question]
>Consider the following code, which multiplies two matrices.
>

```c
int a[1024][1024], b[1024][1024], c[1024][1024];
multiply()
{
   unsigned i, j, k;
   for(i = 0; i < 1024; i++)
       for(j = 0; j < 1024; j++)
           for(k = 0; k < 1024; k++)
               c[i][j] += a[i][k] * b[k][j];
}
```

>[!question]
>contd.
>Assume that the binary for executing this function fits in one page, and the stack also fits in one page. Assume further that an integer requires 4 bytes for storage. Compute the number of TLB misses if the page size is 4096 and the TLB has 8 entries with a replacement policy consisting of LRU.
>>[!answer]-
>>![[Demand Paging 2023-06-08 22.36.38.excalidraw]]
![[Demand Paging 2023-06-08 22.12.45.excalidraw]]


## Counting based page replacement
### Least Frequently used
### Most frequently used


# Thrashing

- High level  of paging activity is known as thrashing. A process is thrashing when it is spending more time paging rather than executing. 

## Cause 
- Very high level of degree of multi-programming. 


## Working Set model

Working set window. 

1,2,3,4,1,1,1,,2,5,1,2,3,4,5

We only keep the set of pages in the most recent "working set window". 