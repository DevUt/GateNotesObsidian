What does a process do with a resource

1. `Request`
2. `Use`
3. `Release`

## Definition
Processes are waiting for an event which is never occur.

## Condition for possibility of deadlock

### Mutual exclusion
If there is mutual exclusion, there maybe deadlock.

>[!example]
>Nisarg wants $R_0$ $R_1$. 
>Utkarsh wants $R_1$ $R_0$.
> Toh if nisarg acquires $R_0$ to use mutual exclusively then utkarsh may cry.

*At least one resource must be held in a non shareable way*

### Hold & Wait

*A process must be holding at least one resource and waiting to acquire additional resources that are currently being held by other processes*

>[!example]
> [[Classical Problems of Synchronization#Dinning Philosopher|Dining Philosopher]]

### NoPremption (Resource)

*Resources cannot be preempted; that is, a resource can be released only voluntarily by the process holding it, after that process has completed its task*

### Circular Wait

*A set $\{P_0\;,P_1\;,P_2\; \cdots\;, P_n\}$ of waiting processes must exist such that $P_0$ is waiting for a resource that is held by $P_1$ ....*

**ALL THESE HAVE TO EXIST SIMULTANEOUSLY**

## Resource allocation graph

Deadlocks can be described more precisely in terms of a directed graph called a system resource allocation graph.

![[Deadlock 2023-05-01 16.02.29.excalidraw]]

>[!example]
>![[Pasted image 20230501160813.png]]

## Methods for handling deadlock

1) Ensure the system never enters deadlock
	1) We can ensure this by making sure one of the [[#Condition for possibility of deadlock|four conditions]] is not satisfied.
	2) This is known as [[#Deadlock prevention|Deadlock prevention]]
2) We allow deadlock to occur, we detect and we recover.
	1) This is known as [[#Deadlock Avoidance|Deadlock avoidance]]
3) Ignore and pretend deadlock never occurs

## Deadlock prevention

We would know try to make sure at least one the [[#Condition for possibility of deadlock|four conditions]] is violated.

### Mutual Exclusion

Mutual exclusion must hold for non shareable resources. For example, a printer cannot be  simultaneously shared by several processes. Shareable resources, in contrast do not require mutually exclusive access. 

### Hold & Wait

#### Method one
Each process to request and be allocated all its resources before it begins execution.

#### Method two
A process may request some resources and use them. Before it can request any additional resources, it must release all the resources that it is currently allocated. 

#### Difference between two
We consider the following process, it copies data from a DVD drive to a file on disk, sorts the file and then prints the results to a printer. 

##### Method one
We request all the resources at the beginning. 

**This would hold the printer from start till end, but it only requires it at the end**

##### Method two
1) Initially only request DVD drive and disk file
2) Copy from DVD to disk
3) Release DVD and disk
4) Request disk file & printer
5) Sort file
6) release printer & disk

**Resource utilization is very low and starvation is possible** // Both methods have this

### No Preemption 

When process requests resources, check if they are available, if yes grant them else preempt all the resources currently held by the process. When everything becomes available then start the process again.

This protocol is applied to resources whose state can be easily saved and restored later.

### Circular wait

We let $R = \{R_1, R_2, \cdots, R_n\}$ be the set of resource types. We assign to each resource type a unique integer number. 

We have a one-to-one function $F:R \rightarrow \mathbb{N}$

For example $F( \text{tape\_drive}) = 1$  $F( \text{disk\_drive}) = 5$  

We define a protocol, 
Each process can request resources only in an increasing order of enumeration. 
If process requests $R_i$ then requests $R_j$  this only happens if $F(R_i) \geq F(R_j)$ 

![[Deadlock 2023-05-06 01.28.01.excalidraw]]

---
## Deadlock Avoidance
We can use our knowledge on how resources are requested and utilize it to avoid deadlocks. 
We know the sequence of actions that would take place.

**The simplest and most useful model requires that the process declare the maximum number of resources to be used**

This information would be provided a priori.

### Safe state.
A state is considered to be safe if the system can allocate resources to each process in some order and still avoid a deadlock. 

![[Pasted image 20230502164447.png]]

### Resource allocation graph
Graph dekh ke bata ki deadlock aaega ki nahi

We search for a cycle in the graph

- Not applicable for multiple resource instance type systems
![[Pasted image 20230501160813.png]]

### Banker's Algorithm 
Max is the max amount of resources we would need
Allocation is the current amount of resources we have
Available is the number of resources present with the system

![[Pasted image 20230506015526.png]]

We create a #Need matrix. 

$\text{Need}[i] = \; \text{Max}[i] -\text{Allocation}[i]$ 

![[Pasted image 20230506020307.png]]

>[!note]
>We add the allocated matrix to available

We found the safe sequence to be $< P_3, P_1, P_0, P_4, P_2 >$

>[!question]
>Homework: Implement the bankers algorithm

When we cannot find any such sequence then the system is in unsafe state.

![[Pasted image 20230506021301.png]]

#### Resource Request Algorithm

1. If $\text{Request}_i \leq \text{Need}_i$ goto step 2, Otherwise, raise an error condition, since the process has exceeded its maximum claim.
2. If $\text{Request}_i \leq \text{Available}$ goto 3, Otherwise wait
3. Now the system pretends that it has allocated the resources```

```c++
Available = Available - Request
Allocation = Allocation + Request
Need = Need - Request
```

If the resulting state is safe, then we grant the resources. 

---
## Deadlock Detection
 
- An algorithm that examines the state of system to determine whether a deadlock has occurred
- An algorithm to recover from the deadlock

### Single Instance of Each Resource Type

By resource allocation graph.
We create a wait graph if there is a cycle then bad.

![[Pasted image 20230506023515.png]]

### Multiple resource

Use bankers

### Recovery from Deadlock

Two methods
1. Process termination
2. Resource Preemption

