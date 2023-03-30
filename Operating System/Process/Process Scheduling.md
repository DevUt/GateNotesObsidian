# Scheduling Queues

## Job Queue
- All the processes which are in the new state
## Ready Queue
- All processes in ready state are in ready queue
## Device Queues
- Process waiting for a specific device
- Each device has its own device queue

> Does this [[#Device Queues]] has anything to do with [[Process#Waiting / Blocked State: |Waiting State]]?

^794402

*All these queues have the PCB*

# Types of Scheduler
1. Long term scheduler (Job) $$\boxed{\text{New}} \rightarrow \, \boxed{Ready}\,$$
2. Short term scheduler (CPU)$$\boxed{\text{Ready}} \rightarrow \, \boxed{Running}\,$$
3. Mid term scheduler

## Long Term Scheduler
- Resource allocation 
- New -> Ready
- Admits the process in memory
- **Controls the [[Introduction to Os#Degree of Multi-programming|Degree of Multi-Programming]]**
- It is mostly absent in modern OS i.e User is the scheduler


## Short Term Scheduler
- Selects process to be sent to run on CPU
- *DOES NOT* actually do the [[Process#Context Switch|Context Switch]]
- #Dispatcher does the actual job
- If you want to search more search "Linux Schedulers"
- In Linux world sometimes also known as *CPU governor*

## Mid Term Scheduler
- This also controls the [[Introduction to Os#Degree of Multi-programming|Degree of Multi-programming]]

Lets imagine a scenario
We are playing Call of Duty. You get an E-mail. You click the notification and the App opens up.

Now the Call of Duty shifted to the background. We open up another app. 
Memory low. :(

Now the mid term scheduler selects a process and moves it from ram to disk in a special area called #Swap 

Now when we go back and re-open COD then it has to reload from disk to memory. 

This is known as *Swapping*. Also known as *Rolling*

Processes that are swapped out are known as **Suspended** 

![[Process Scheduling 2023-03-27 01.51.00.excalidraw]]

**These schedulers are named on the frequency they are required**

## What are our goals in terms of scheduling?
We want to minimize the waiting time and the turn-around time and maximize the throughput with fairness. 

> Does the scheduler interrupt the process?
> No it doesn't. #Dispatcher  does

# Scheduling Times
## Arrival Time (AT)
- Time at which process arrives in the system
- Time at which process arrives in ready queue

## Burst Time (BT)
- Amount of time for which process spends on CPU running
- It is time spent on CPU

## Completion Time (CT) / Exit time
- Termination Time

## Turn around Time (TAT)
- Time from arrival to completion
- $CT - AT$

## Waiting Time (WT)
- $TAT-BT$
- It is the amount of time that it didn't spend on CPU

## Response Time (RT)
- Amount of time from arrival till the first time it gets CPU
	For e.g a process arrives at 2 seconds and gets CPU at 5 seconds then 5-2 = 3 is the  response time.

**Note: RT = WT for [[Introduction to Os#^366a2a|Co-operative]] scheduling**

## Extra measurements

### Scheduling Length (L)
- The amount of time we scheduled something
- $\text{max}(CT) - \, \text{min}(AT)$

### Throughput 
- No of process per unit time
- $\dfrac{n}{L}$ where $\text{n is the number of process}$ and $L$ is [[#Scheduling Length (L)]]
