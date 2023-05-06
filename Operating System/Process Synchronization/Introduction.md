# Race Condition

![[Introduction 2023-04-24 23.56.33.excalidraw]]

```c
counter--;

// Actually how it is done
register = counter; // Load from memory to register
register--; // Perform operation on register
counter = register; // Store the result back
```

Lets say we perform `counter--;` and `counter++;` simultaneously. 

	![[Introduction 2023-04-25 00.00.46.excalidraw]]
![[Drawing 2023-04-26 15.45.10.excalidraw]]

This phenomenon is known as #race-condition

The outcome of the execution depends upon the  order in which the access of data takes place is called a race condition.

# Critical Section 

This is a section where we access shared variables, open files etc. The important feature of the system is that, when one process is executing under its critical section, no other process would be allowed to execute its critical section.

```
critical-section-start
openfile()
// do operations
closefile()
critical-section-end
```

*The Critical section problem is to design a protocol that the processes can use to co-operate.* 

## Section of Code

![[Introduction 2023-04-25 00.15.31.excalidraw]]

### Entry Section

We announce to everyone that we are entering the critical section. This is also the place to check if any other processes are in their critical section. 

### Critical Section

The area we access shared variables. 

### Exit Section

We announce to everyone that we are exiting the critical section. 

### Remainder Section

Remaining Code.

# Requirements To Solution

## Mutual Exclusion
If a process is in its critical section, then no other process can be executing in their critical section.

## Progress 
If no process is executing in its critical section and some processes wish to enter their critical sections, then only those processes that are not executing in their remainder sections can participate in deciding which will enter its critical section next, and this selection cannot be postponed indefinitely

### How to check progress?

Imagine $P_i$ wants to enter the critical section.

Now there can be two cases
1. $P_j$ doesn't exist
2. $P_j$ is running in its remainder section.

Is $P_i$ able to enter the critical section?

## Bounded Waiting
There exists a bound, or limit, on the number of times that other processes are allowed to enter their critical sections after a process has made a request to enter its critical section and before that request is granted

### How to check Bounded waiting?

Mostly in bounded waiting cases we when the process ends it passes the lock to some other process. 

# Locks

## Using an Naive Lock

```c
bool lock; // This is shared
while(true){
	while(lock)
		;
	lock = true;
		// CS
	lock = false;
	// RS
}
```

```c
register = lock;
register = true;
lock = register;
```

What  happens when `lock` becomes false  and we preempt just before  line 5?
![[Introduction 2023-04-26 16.09.09.excalidraw]]
*Mutual Exclusion* is violated. Because `lock` variable itself was shared and not protected. 

## Using Turn Based

First process
```c
int turn =0;

-------
while(true){
	while(turn != 0)
		;
	// CS
	turn = 1;
	// RS
}
```

Second process
```c
int turn =0;

------
while(true){
	while(turn != 1)
		;
	// CS
	turn = 0;
	// RS
}
```

*Progress is violated*.

If the first process doesn't exist the second process will wait infinitely for the turn to be 1.

## Peterson's Solution

Process 0
```c
bool flag[2]; // Denote wishes
int turn; // Denote turns

while(true){
	flag[0] = true; // Mera icha hai
	turn = 1; // But tu phele ja

	while(flag[1] && turn == 1)
		; // No Op
	// CS
	flag[0] = false;
}
```

Process 1
```c
bool flag[2];
int turn;

while(true){
	flag[1] = true;
	turn = 0;

	while(flag[0] && turn == 0)
		;
	// CS
	flag[1] = false;
}
```

[This solution doesn't work in modern CPU architectures due to the reordering of load and store instructions](https://stackoverflow.com/a/15676084/5019937). 

*[Peterson solution for more than one process](https://cs.stackexchange.com/a/99032)*
### HW : Prove all the requirements satisfy for this solution.

#### Mutual exclusion
Mutual exclusion is guaranteed by the turn variable. It can only be 0 or a 1.

#### Progress
The turn variable is changed only in the entry section. 

#### Bounded waiting

Bounded waiting is satisfied because if the process wants to re-enter the critical section it gives up its turn and sets it for the different process.