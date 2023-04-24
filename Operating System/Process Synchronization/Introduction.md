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



# Locks

## Using an naive Lock

```c
bool lock;
while(true){
	while(lock)
		;
	lock = true;
		// CS
	lock = false;
	// RS
}
```
