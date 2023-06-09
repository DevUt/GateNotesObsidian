# Fork 
Creates a replica of the process.
The created copy is known as the child process and the creator is known as the parent process. 

Parent process : 
```c
int main(){
	int a = 0;
	int child_pid = fork();
	print("%d",child_pid);
}
```
Output : 686(pid of child)

Child process :
```c
int main(){
	int a = 0;
	int child_pid = fork();
	print("%d",child_pid);
}
```
Output : 0

Because it is a separate process it has its own PCB. And it of course, has it's own PID.  

From where does the child process, start running?
It would start from the line 3. 

We can break the execution of line 3 in two parts
1. Execution of fork (i.e creation of the new process)
2. Returning of value from `fork()`

Both parent and child start executing from 2nd point. 


**FORK RETURNS DIFFERENT VALUE TO BOTH PARENT AND CHILD**

Parent receives the PID of the child. 
Child receives `0` as the returning value.

>[!question]
>Which process will run after `fork()` has been called?
>>[!answer]-
>>We don't know


# Wait()

When a process creates a new process, two possibilities exist in terms of execution
1. The parent continues to execute concurrently with its children. 
2. The parent waits until some or all of its children have terminated.


This waiting is done by calling the `wait()`

When a process dies, a notification is sent to its parent. If the parent never acknowledges the notification, then the child turns into a *zombie process*. 

>[!question]

```c
int main(){
	int i = 0;
	for(i=0;i<3;i++){
		fork();
	}
	puts("Hello World");
}
```

>[!question]
>How many "Hello World"s would be printed?
>>[!answer]-
>>![[Fork() and exec() 2023-06-10 02.15.50.excalidraw]]
>>![[Fork() and exec() 2023-06-10 02.23.58.excalidraw]]

```c
int main(){
	puts("A");
	int child = fork();
	puts("B");
	if(child)
		wait(NULL);
	puts("C");
}
```

>[!question]
>What are the different strings that can be created?
>>[!answer]-
>>![[Fork() and exec() 2023-06-10 02.39.10.excalidraw]]

# Exec()

Instead of replicating the process, a new binary image is loaded into the current process.

We provide location to the `exec()` system call
As it is loaded in the same process, the process id doesn't change.

[Reference](https://linuxhint.com/linux-exec-system-call/) 

![[Fork() and exec() 2023-06-10 02.49.19.excalidraw]]
