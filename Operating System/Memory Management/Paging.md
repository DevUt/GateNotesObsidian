Paging is a memory management scheme that allows the process memory to be non contiguous. 

# Basic Method

![[Paging 2023-05-07 02.42.38.excalidraw]]

Physical memory is broken into fixed sized blocks known as frames.
Logical memory is broken into fixed sized blocks known as pages.
Pages are loaded into frames.

>[!Question]
>How does the address generated by a CPU usually look?
>> [!Answer]-
>> 000000111111, we can represent it in hex also.

![[Pasted image 20230507025314.png]]
The logical address is divided into two parts
1. Page number (p)
2. Page offset (d)

Lets imagine 4 bits
2 bits for page number and 2 bits for page offset.

Lets take about frames.
0000 -> 0th byte -> first frame
	0010 -> 2nd byte -> first frame
0100 -> 8th byte -> second frame
1000 -> 16th byte -> third frame

![[Paging 2023-05-07 03.02.36.excalidraw]]

In decimal
0000 -> 0th -> first 
0100 -> 100th  -> second 
0200 -> 200th -> third 
0300 -> 300th -> fourth
1300 -> 1300th  -> fourteenth 

The page size (like the frame size) is defined by the hardware. This is typically a power of two. It makes the translation easy.

If the logical address space is $2^m$ , page size is $2^n$ 

Page number = $\frac{\text{address}}{\text{page size}}$ 
(address >> $n$) divides by $2^n$ 

Page offset = $\text{address} \mathbin{\%} \text{page size}$
(address&(page_size - 1)) 
![[Paging 2023-05-07 03.45.13.excalidraw]]


![[Paging 2023-05-07 03.17.18.excalidraw]]

>[!question]
>What if the logical address space and the page size were of power of 3? Lets say address is x. What is the page number and the page offset?
>>[!answer]-
>>Divide by page size for page number. The reason it is not used because it is inefficient to perform with respect to binary which just requires truncation digits.

>[!info]
>1 kilo = $2^{10}$
>1 Mega = $2^{20}$
>1 Giga = $2^{30}$

>[!Question]
>We have 4GB of memory. The logical address and physical address is of 32 bits and the page size is of 8KB. Each page table entry is of 4 bytes. What would be the size of the page table?
>>[!answer]-
>>Number of pages = $\frac{2^{32}}{2^{13}}$ = $2^{19}$
>>Size of page table = $4\times 2^{19}$ = $2^{21}$ bytes = 2 MB
>

>[!question]
>Suppose that the virtual address space is 16 MB, the physical memory is 128 KB, and the page size is 2 KB. Show how to determine the following.
>
>1. Number of bits for virtual address.
>2. Number of bits for physical address.
>3. Number of bits for offset
>4. Number of bits for page number
>5. Number of bits for frame number
>
>>[!answer]-
>>1. $2^{24}$ = 24 bits needed
>>2. $2^7 \times 2^{10}$ = $2^{17}$ = 17 bits needed
>>3. $2^{11}$ = 11 bits needed
>>4. $\frac{2^{24}}{2^{11}} =  2^{13}$ 13 bits needed
>>5. $\frac{2^{17}}{2^{11}}$  6 bits needed


Notice that the user process by definition is unable to access any memory that it doesn't own.

---

When we use paging we don't have external fragmentation.
But we do have internal fragmentation. 

![[Paging 2023-05-07 17.45.04.excalidraw]]
Process sizes are independent of page size.

If we had smaller page sizes -> we would less internal fragmentation.

![[Paging 2023-05-07 17.46.24.excalidraw]]
But if we have smaller pages -> We would need more pages.
It would lead  to a larger page table -> More overhead

---

Since the OS manages the memory it should be aware about the status of each frame. This information is kept in a *frame table*. 

![[Paging 2023-05-07 17.51.22.excalidraw]]

The address we provide of the buffer would a logical address. The OS has to map it to the physical address and also map the I/O device's output to the same physical address.

![[Paging 2023-05-07 17.53.17.excalidraw]]

Suppose the I/O device is keyboard.

Os would convert this to a physical address and give it to the I/O device.

# Hardware Support

We see there is a clear separation between process view of memory and actual memory.
The user process thinks that its the only one and views the whole memory as a single space.

To join these world we need - translation hardware.

The hardware implementation of the page table in the simplest way is done by set of dedicated registers. Page table is in the register. The bottleneck becomes the size of the register. 

In modern computers, the page table is in the main memory. And a page table base register (PTBR) is used to point to the page table. Changing the page table requires only changing this PTBR. 

Now lets look how would we access an address `x`.

1. Using PTBR we find the page table in MM (1st MM access)
2. It provides us with frame number
3. We combine it with page offset and access the location in MM (2nd MM access)

Thus, we can see that memory access is slowed by a factor of 2.

The standard solution to this is build a fast lookup hardware cache, called as *translation look-aside buffer(TLB)*

## TLB

The TLB is a associative, high-speed memory.
Each entry in TLB has two parts 
1. Key  (Tag)
2. Value

We compare the item, with all the keys simultaneously. If found it is returned.
TLB is small and expensive.

1. First check with TLB If exist goto 3
2. Check page table 
3. Combine and access data


![[Pasted image 20230507180921.png]]

If page number is found in page table then it is known as *page hit.*
If page number is not found in page table then it is known as *page miss*.

Some TLBs allow entries to be *wired down*, meaning they cannot be removed from the TLB. 

### Address Space Identifier (ASIDs)
Some TLB store ASIDs in each TLB entry. An ASID uniquely identifies each process and used to provide address space protection for it.

If this is not present then we would have to flush the TLB every time we execute another process.

![[Pasted image 20230507181710.png]]


### Effective memory access.

> [!Question]
> Consider a system with memory mapping done on a page basis, and using a single level page table. Assume that the page table is always in memory.
> (a) If a memory reference takes 100 ns. Then how long does it take to access the data at a given address. Assume no TLB is present.
> (b) Now we add we add TLB which imposes a 15 ns overhead on either hit or miss. If we assume that 90 percent of all memory accesses are a TLB hit, what is the Effective memory access time?
> > [!answer]-
> > a) $\overbrace{100}^{\text{page table access}} + \overbrace{100}^{\text{data access}}$
> >  
> >  $\text{b) }0.9(\text{time take with TLB hit}) + 0.1(\text{time take with TLB miss})$
> > $0.9(115) + 0.1(215)$


# Protection

Memory protection is associated with each frame. Normally these bits are kept in the page table. 

Valid invalid bit. 

![[Pasted image 20230507183236.png]]
