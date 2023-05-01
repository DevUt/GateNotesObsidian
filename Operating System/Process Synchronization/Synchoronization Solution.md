
# Hardware

## Atomic Instruction
These instructions happen completely or not at all. There is not in between.

## TestAndSet()

Atomic operation provided by the hardware.
```c
*target -> value of lock
&lock -> address of lock
target -> pointer to lock

lock = false
&lock -> 12434
target -> 12434
*target = false
&target -> 43324 // Location of the target variable
```


```c
bool TestAndSet(bool *target){
	bool return_value = *target;
	*target = true; 
	return return_value;
}
```


How to Use?

```c
while(true){
	while(TestAndSet(&lock))
		; // Do Nothing
	// Critical Section
	lock = false;
	// RS
}
```

>This above solution is not free from Bounded waiting, why? and fix it.

If I finish the remainder section, I can re-enter the critical section quickly without giving any other process any consideration. This violates the bounded waiting solution. 
![[Synchoronization Solution 2023-04-30 12.32.03.excalidraw]]

```c
while(true){
	waiting[i] = true;
	while(waiting[i] && TestAndSet(&lock))
		; // No OP
	waiting[i] = false;
	// CS

	int j = (i+1)%n;
	while((j!= i) && !waiting[j])
		j = (j+1)%n;

	if(j == i){
		lock = false;
	}else {
		waiting[j] = false;
	}
}
```


## Swap()

```c
void swap(bool *a, bool *b){
	bool temp = *a;
	*a = *b;
	*b = temp;
}
```

```c
while(true) {
    KEY = TRUE; //local variable, not shared.
    while(KEY == True)
        Swap(lock, key);
    // CS
    lock = false;
    // RS
}
```


> [!question]
> 
>Check if meets all the requirements.

# Semaphores

It is an integer value that is used for synchronization.
The value of Semaphore denotes whether a particular resources is available or not.

`S=1` denotes there is 1 unit resource that is available. 

There are mainly two operations

## Wait() / P()

Running this on a Semaphore denotes that we are taking 1 of its resource.

```c
P(S){
	while(S <= 0)
		;
	S--;
}
```


## Signal()/ V()

Running this on semaphore indicates we are done with the resource and we return it.
```c
V(S) {
	S++;
}
```


## Usage
```c
while(true) {
	P(S);
	// CS
	V(S);
}
```

## Types of Semaphore

### Binary Semaphore
Range is \[0,1\]

### Counting Semaphore
Range is \[0, $\infty$+\]

## Concept of Busy Waiting

The main disadvantage of the semaphore  definition above it that it requires *busy waiting*.

A process would continuously P() on the semaphore until it gets it. This wastes CPU cycle. So this type implementation of P and V causes busy waiting.

And this is also called sometimes SPINLOCK because the process "spins" while waiting for the lock.


Below are a solution to the busy waiting.

```c
typedef struct {
    int value; // current value
    struct process *list; // List of process waiting for the semaphore
} semaphore;
```

```c
P(Semaphore *S) {
    S->value--;
    if (S->value <= 0) {
        add processs to S->list;
        block();
    }
}
```

```c
V(Semaphore *S) {
    S->value++;
    if(S-> value <=0) {
        remove "some" process P from S->list;
        wakeup(P);
    }
}
```


# Deadlock

The implementation of a semaphore with a waiting queue may result in a situation where two or more processes are waiting indefinitely for a resource that they share.


$P_0$
```c
P(S)
P(Q)
....

V(S)
V(Q)
```


$P_1$
```c
P(Q)
P(S)
....

V(Q)
V(S)
```
