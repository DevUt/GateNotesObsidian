# Bounded Buffer Problem

![[Classical Problems of Synchronization 2023-04-30 12.48.33.excalidraw]]

## Requirements
1) When the buffer is full producer can't produce
2) When buffer empty consumer can't consume
3) Production and consumption shouldn't occur simultaneously

## Variables

### Mutex 
This variable would allow us to take a lock on the buffer.
Initialised as : 1 

### Full
This is a counting semaphore to denote the number of occupied slots.
Initialised as : 0

### Empty
Counting semaphore denote number of empty slots. 
Initialised as : n


## Producer

```c++
Producer(){
	P(empty)
	// Produce
		P(mutex)
		// add item to buffer
		V(mutex)
	V(full)
}
```

## Consumer

```C++
Consumer(){
	P(full)
		P(mutex)
		//consume
		V(mutex)
	V(empty)
}
```

----
# Reader Writer Problem

## Requirements

1) If someone is reading, no one can write
2) If someone is reading, someone else can read
3) If someone is writing, no one can read or write

## Variable

### Semaphores
#### Mutex
Binary Semaphore for Mutual Exclusion protecting the [[#readcount|Reader's count]]
Initialised as : 1

#### write_lock
Binary semaphore to restrict writing access.
Initialised as: 1

### Integer
#### read_count
Integer variable denoting the number of active readers.
Initialised as: 0

>[!info]
>Mostly the case is we can't directly read or write to semaphores. We can just perform the `P()` and `V()` operations

## Readers

```c++
Reader(){
	P(mutex)
		read_count++;
		if(read_count == 1)
			P(write_lock) --> P1
	V(mutex)

	// read

	P(mutex)
		read_count--;
	if(readcount == 0)
		V(write_lock) --> P7 
	V(mutex)
}
```

>[!info]
>If $P_1$ takes the `write_lock` it is not necessary for $P_1$ to release the lock. Here the last reader releases the lock, $P_1$ could be long gone by that time.

## Writer

```c++
Writer() {
	P(write_lock)
		// write
	V(write_lock)
}
```

----

# Dinning Philosopher

## Requirements

![[Classical Problems of Synchronization 2023-05-01 13.11.15.excalidraw]]

$k$ philosophers seated around a round table. There is one chopstick between each bowl. One can take chopsticks that is in front of them.

i.e The $k^{th}$ philosopher can use $k$ and $k+1$ chopstick.

Both the chopsticks needed to be picked up.

## A naive solution

```c
pick(chopstick[i])
pick(chopstick[i+1])

// eat

release(chopstick[i])
release(chopstick[i+1])
```

*This leads to deadlock*

## Solution

1) There should be at most $k-1$ philosopher
2) A philosopher should only be able to pick their chopstick if both are available at same time

What I think
```c
P(mutex)
	P(chopsticks[i])
	P(chopsticks[i+1])
V(mutex)
```

3) One particular philosopher picks up the left fork before the right fork, and that all other philosophers pick up the right fork before the left fork 
