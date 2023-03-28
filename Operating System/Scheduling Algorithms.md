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
Slow down because slower job is ahead of faster job

**Convoy effect exists due to the non preemptive nature of FCFS**
![[Scheduling Algorithms 2023-03-29 00.48.25.excalidraw]]

$P_4$ still has to wait for the processes that came before it. Even tho it has the lower burst time. This increases our Response Time, Average TAT and WT. 

## Shortest Job First (SJF)
- Criteria : Smallest [[Process Scheduling#Burst Time (BT) |Burst Time]]
	- Tie Breaker: FCFS
- Type: [[Introduction to Os#^366a2a|Co-operative Scheduling]]

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
- Criteria : Smallest [[Process Scheduling#Burst Time (BT) |Burst Time]]
	- Tie Breaker: FCFS
- Type: [[Introduction to Os#^3ead25|Preemptive]]

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