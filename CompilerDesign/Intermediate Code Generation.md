- Intermediate code is the interface between the front end and the back end
Case Study 

[GCC](https://tldp.org/HOWTO/GCC-Frontend-HOWTO-4.html)
![[Pasted image 20230415230517.png]]



## Why?
- It also much more portability
## Types
1. Syntax Tree
2. Directed acyclic graph (DAG)
3. Three address code

## Three address code
- Intermediate code used by optimizer
- In three-address code, there is at most one operator on the right side of an  
instruction; that is, no built-up arithmetic expressions are permitted

```c
x+y*z
//
t1 = y*z
t2 = x + t1
```

Statements are in the form of
1. Assignment
```
x = y op z
```


E.g 
`-(a x b) + (c + d) – (a + b + c + d)`
```c
(1) t1 = a x b
(2) t2 = uminus t1
(3) t3 = c+d
(4) t4 = t2 + t3
(5) t5 = a + b
(6) t6 = t3 + t5
(7) t7 = t4 - t6
```

E.g
`If A < B then 1 else 0`

```c
(1) if (A<B) goto (4)
(2) T1 = 0
(3) goto (5)
(4) T1 = 1
(5)
```

`If A < B and C < D then t = 1 else t = 0`

```c
(1) If A < B goto(4)
(2) t = 0
(3) goto (7)
(4) if C < D goto (6)
(5) goto (2)
(6) t = 1
(7)
```

```c
(1) t1 = A < B
(2) t2 = C < D 
(3) if t1 && t2 goto (6) 
(4) t = 0 
(5) goto 7 
(6) t = 1 
(7)
```

Mam solution:
```c
(1) If (A < B) goto (3)
(2) goto (4)
(3) If (C < D) goto (6)
(4) t = 0
(5) goto (7)
(6) t = 1
(7)
```

```c
while (A < C and B > D) do
	if A = 1 then C = C + 1
	else
		while A <= D
			do A = A + B
```

```c
if (A < C) goto (3)
goto (15)
if (B > D) goto (5)
goto (15)
if (A = 1) goto (7)
goto (10)
T1 = c + 1
c = T1
goto (1)
if (A <= D) goto (12)
goto (1)
T2 = A + B
A = T2
goto (10)

```


## Implementation of Three Address code
1. Quadruple
2. Triple

`a = b * minus c + b * minus c`

```c
t1 = uminus c
t2 = b*t1
a = 2*t2
```

```c
t1 = minus c
t2 = b * t1
t3 = minus c
t4 = b * t3
t5 = t2 + t4
a = t5
```

Quadruple

| Location | Op             | Arg1 | Arg2 | Result |
|:-------- |:-------------- |:---- |:---- |:------ |
| (1)      | uminus         | c    |      | t1     |
| (2)      | multiplication | b    | t1   | t2     |
| (3)      | uminus         | c    |      | t3     |
| (4)      | multiplication | b    | t3   | t4     |
| (5)      | plus           | t2   | t4   | t5     |
| (6)      | =              | t5   |      | a      | 

Triple

| Location | Op             | Arg1 | Arg2 |
|:-------- |:-------------- |:---- |:---- |
| (1)      | uminus         | c    |      |
| (2)      | multiplication | b    | (1)  |
| (3)      | uminus         | c    |      |
| (4)      | multiplication | b    | (3)  |
|          |                |      |      |
|          |                |      |      |
