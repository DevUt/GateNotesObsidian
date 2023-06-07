
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