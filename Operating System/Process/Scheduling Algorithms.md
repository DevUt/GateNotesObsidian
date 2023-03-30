## Prerequisite 

## Starvation
- Indefinite waiting
	- Arbitrarily high response time
>Starve for CPU

> From : Galvin
> A major problem with priority scheduling algorithms is indefinite blocking, or starvation. A process that is ready to run but waiting for the CPU can be considered blocked.
> 
> Note blocked here is not the [[Process#Waiting / Blocked State:|Blocked State]] 



## First Come First Serve (FCFS)
#fcfs
- Criteria : Smallest [[Process Scheduling#Arrival Time (AT)|Arrival Time]] 
	- Tie Breaker : Smaller Process ID
- Type : [[Introduction to Os#^366a2a|Co-operative Scheduling]]
- Starvation : Yes(Gate 2023) and No? 
	- No: The response time here is not indefinite. Even if new process arrive they would have lesser priority to be scheduled (according to the criteria of arrival time)
	- Yes:
```cpp
		while(true){
			work();
		}
```
		
What about now? This is an process which has infinite burst time.

>Do Processes with infinite burst time exist in practicality?
>Daemons? Services? OS? These are the examples of infinite burst time.

**Infinite running programs can cause starvation in ALL non-preemptive scheduling algorithms** 

Q1. 
| PID   | AT  | BT  | CT  | TAT | WT  | RT  |
|:----- |:--- |:--- |:--- |:--- |:--- |:--- |
| $P_1$ | 0   | 30  | 30  | 30  | 0   | 0   |
| $P_2$ | 0   | 5   | 35  | 35  | 30  | 30  |
| $P_3$ | 0   | 5   | 40  | 40  | 35  | 35  | 

Ready Queue 
0 time -> $P_1, P_2, P_3$

![[Scheduling Algorithms 2023-03-29 00.25.27.excalidraw]]

$\text{Average TAT} = \dfrac{30 + 35 + 40}{3}$
$\text{Average WT} = \dfrac{0 + 30 + 35}{3}$

$\text{Scheduling Length} = max(CT)-min(AT) = 40-0 = 40$
$\text{Throughput} = \dfrac{3}{40}$
Q2

| PID   | AT  | BT  | CT  | TAT | WT  | RT  |
|:----- |:--- |:--- |:--- |:--- |:--- |:--- |
| $P_1$ | 0   | 4   |     |     |     |     |
| $P_2$ | 1   | 2   |     |     |     |     |
| $P_3$ | 2   | 3   |     |     |     |     |
| $P_4$ | 3   | 5   |     |     |     |     |
| $P_5$ | 4   | 6   |     |     |     |     |
| $P_6$ | 5   | 1    |     |     |     |     |


Q3
| PID   | AT  | BT  | CT  | TAT | WT  | RT  |
|:----- |:--- |:--- |:--- |:--- |:--- |:--- |
| $P_1$ | 4   | 4   |     |     |     |     |
| $P_2$ | 8   | 2   |     |     |     |     |
| $P_3$ | 6   | 3   |     |     |     |     |
| $P_4$ | 5   | 3   |     |     |     |     |
| $P_5$ | 2   | 1   |     |     |     |     |
| $P_6$ | 7   | 7   |     |     |     |     |


### Convoy Effect
Jobs having higher burst time take the CPU before the jobs having lower burst time

**Convoy effect exists due to the non preemptive nature of FCFS**
![[Scheduling Algorithms 2023-03-29 00.48.25.excalidraw]]

$P_4$ still has to wait for the processes that came before it. Even tho it has the lower burst time. This increases our Response Time, Average TAT and WT. 

## Shortest Job First (SJF)
- Criteria : Smallest [[Process Scheduling#Burst Time (BT) |Burst Time]]
	- Tie Breaker: FCFS
- Type: [[Introduction to Os#^366a2a|Co-operative Scheduling]]
- Starvation: Yes

*SJF gives minimum average waiting time for non preemptive*

Q1. 
| PID   | AT  | BT  | CT  | TAT | WT  | RT  |
|:----- |:--- |:--- |:--- |:--- |:--- |:--- |
| $P_1$ | 0   | 30  | 40  | 40  | 10  | 10  |
| $P_2$ | 0   | 5   | 5   | 5   | 0   | 0   |
| $P_3$ | 0   | 5   | 10    | 10  | 5   | 5   |

Q2.

| PID   | AT  | BT  | CT  | TAT | WT  | RT  |
|:----- |:--- |:--- |:--- |:--- |:--- |:--- |
| $P_1$ | 0   | 6   |     |     |     |     |
| $P_2$ | 0   | 3   |     |     |     |     |
| $P_3$ | 1   | 4   |     |     |     |     |
| $P_4$ | 2   | 2   |     |     |     |     |
| $P_5$ | 3   | 1   |     |     |     |     |
| $P_6$ | 4   | 5   |     |     |     |     |
| $P_7$ | 6   | 2   |     |     |     |     |

## Shortest Remaining Time First (SRTF)
- Criteria : Smallest Remaining Time
	- Tie Breaker: FCFS
- Type: [[Introduction to Os#^3ead25|Preemptive]]
- Starvation: Yes
- It has little overhead because evaluation takes place
	- Process has terminated
	- Process has  arrived

*SRTF gives minimum average waiting time for  preemptive*

Q1.
| PID   | AT  | BT  | CT  | TAT | WT  | RT  |
|:----- |:--- |:--- |:--- |:--- |:--- |:--- |
| $P_1$ | 0   | 6   |     |     |     |     |
| $P_2$ | 1   | 4   |     |     |     |     |
| $P_3$ | 2   | 1   |     |     |     |     |
| $P_4$ | 3   | 2   |     |     |     |     |
| $P_5$ | 4   | 1   |     |     |     |     |
| $P_6$ | 5   | 3   |     |     |     |     |


#### LRTF GATE 2006 Q

| PID   | AT  | BT  | CT  | TAT | WT  | RT  |
|:----- |:--- |:--- |:--- |:--- |:--- |:--- |
| $P_0$ | 0   | 2   |     |     |     |     |
| $P_1$ | 0   | 4   |     |     |     |     |
| $P_2$ | 0   | 8   |     |     |     |     |

## Problems with SJF and SRTF
- Starvation
- Practical implementation not possible (Burst time?)
- No fairness

## Highest Response Ratio Next (HRRN)
- So we saw that starvation was an issue in SRTF because it only considered burst times
- We may consider waiting times to address starvation
- By adding a more tracking overhead


- Criteria: Response Ratio
- Tie breaker : Smallest [[Process Scheduling#Burst Time (BT) |Burst Time]]

$\text{Response Ratio} = \dfrac{W + S}{S}$
$W = \text{Waiting time},\; S = \text{Burst time/ Service time}$


| PID   | AT  | BT  | CT  | TAT | WT  | RT  |
|:----- |:--- |:--- |:--- |:--- |:--- |:--- |
| $P_1$ | 0   | 3   |     |     |     |     |
| $P_2$ | 2   | 6   |     |     |     |     |
| $P_3$ | 4   | 4   |     |     |     |     |
| $P_4$ | 6   | 5   |     |     |     |     |
| $P_5$ | 8   | 2   |     |     |     |     |

## Priority Based Scheduling
### Types
1. Preemptive
2. Non Preemptive

- Criteria : Priority

#### Priority Types
1. Static -> Priority is Fixed
2. Dynamic -> Priority is dynamic

Suffers from: Starvation

**NEVER ASSUME PRIORITY ALWAYS LOOK IN QUESTION**

Solution to Starvation: #Aging 
- After a predetermined time period -> Increase priority of the waiting process
- Only Dynamic supports aging.

## Round - Robin / Time Sharing
Criteria : AT + Q (Time Quantum)
Type : Preemptive

Objective : Provides Inter-activeness, Fairness
Starvation : Nope

**Time quantum is NEVER infinite**

| PID   | AT  | BT  | CT  | TAT | WT  | RT  |
|:----- |:--- |:--- |:--- |:--- |:--- |:--- |
| $P_1$ | 0   | 4   | 8   |     |     |     |
| $P_2$ | 1   | 5   | 20  |     |     |     |
| $P_3$ | 2   | 6   | 24  |     |     |     |
| $P_4$ | 3   | 3   | 19  |     |     |     |
| $P_5$ | 4   | 2   | 12  |     |     |     |
| $P_6$ | 5   | 4   | 22  |     |     |     |
$Q = 2$

$\text{No. Of Context Switch} = 12$

Ready Queue
$$\displaylines{\begin{aligned} 0 &: P_1 \\ 1 &: P_2 \\ 2 &: P_2, P_3, P_1 \\ 3 &: P_3, P_1, P_4, \\ 4 &: P_3,P_1, P_4, P_5, P_2 \\ 6 &: \cdots \end{aligned}}$$

Note: Tricky case at 2nd we see that $P_1$ finished the job and  $P_3$ also arrives, we have to place $P_3$ before $P_1$ in ready queue.  

Q 
| PID   | AT  | BT  | CT  | TAT | WT  | RT  |
|:----- |:--- |:--- |:--- |:--- |:--- |:--- |
| $P_1$ | 0   | 8   |    |     |     |     |
 Time Quantum(Q) =  2   ^e24540

> In some question the number of Context switches for this 3
> [Galvin Reference](https://gateoverflow.in/147415/os-round-robin-scheduling?show=343480#a343480)

$\text{No of context switch} = (\Sigma \lceil \dfrac{m}{q} \rceil) - 1$

If there are $n$ processes in ready queue and the time quantum is $q$, then each of the  process gets $\frac{1}{n}$ of CPU time in chunks of at most $q$ time unit. Each process may wait no longer than $(n-1)q$ time units until its next time quantum.


#### Values of time quantum

##### Very Small : 
**This is also known as #processor-sharing (in theory)**
CPU spends more time in context switching than in execution. 

This creates an appearance that each of n process has its own processor that is running at $\frac{1}{n}$ speed of the real processor. 

This was used in CDC Control Data Corporation 

##### Small
Less Interactive

##### Very Large

Degrades to [[Scheduling Algorithms#First Come First Serve (FCFS)|FCFS]]. 
This degradation means that the all processes have completed their execution before the time quantum expires.

> Riddhi Gate 2023 Case Study
> 
> Q. If time quantum is very large round robin degrades to FCFS then can we say round robin has starvation?
> 
> No we cannot because time quantum is never infinite therefore we can say the process with infinite burst HAS to be preempted at some point causing a context switch and chance to other processes. This prevents starvation as the waiting time is not indefinite. 

## MultiLevel Queue Scheduling

![[Pasted image 20230330164654.png]]

## MultiLevel Feedback Queue Scheduling
![[Pasted image 20230330165156.png]]

In general, a multilevel feedback queue scheduler is defined by the  
following parameters:  
- The number of queues  
- The scheduling algorithm for each queue  
- The method used to determine when to upgrade a process to a higher priority queue  
The method used to determine when to demote a process to a lower priority queue  
The method used to determine which queue a process will enter when that process needs service

----

