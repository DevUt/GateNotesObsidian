# Introduction
- We have reached the final stages of compilation, Optimization.
- Here we try to transform the code to consume less resources (Memory, CPU etc) and deliver high speeds. 
- We rearrange the tree produced by the parser to consume fewer resources and be faster.
- Meaning of the code isn't altered.

## Three rules
1. The output code must not in any way change the meaning of the program.
```c
int a = 0;
for(int  i=0;i<10;i++){
	a += i;
}
// output
int a = (direct answer);
```
2. Optimization should increase the speed of execution and  if possible demand  less resources.
3. The process of optimization should itself be fast and not delay the overall compiling process.

## Places which can do optimization
1. User can themselves write better algorithms
2. In intermediate code, compiler can modify the intermediate code by address calculation and loop optimization.
3. Target machine optimization using memory hierarchy and better CPU instructions.

# Types of Code Optimizations

## High Level Code Optimization
- It is a language dependent optimizations
- Done closer to vicinity of the source code
- We use the constructs of the programming language

E.g

Function inlining
![[Pasted image 20230415145814.png]]

Alignment of arrays
Padding
Layout
Elimination of tail recursion

## Intermediate Code optimization
#### Elimination of Common Sub expression
- Look for common subexpression and replace them with a single variable which holds the computed value
```c
a = 10;
b = a + 1 * 2;
c = 20 + 1 * 2;  

// 1*2 is the common sub expression
a = 10;
z = 1*2;
b = a + z;
c = 20 + z;
```

#### Constant propagation
- We evaluate some expressions at compile time rather than evaluation time

```kotlin
time = 1000 * 60 * 60;

// Optimized

time = 3600000;
```

- This may include evaluating 
	- Arithmetic expressions:
		- `2+3 = 5`
	- Logical expressions
	- Function arguments

#### Copy Propagation
- Aim: Avoid unnecessary copies of variables
- Process of replacing the occurrences of targets of direct assignments with their values
```c
y = x
z = 3 + y

/// 
z = 3 + x
```

#### Jump threading
- We try to reduce the number of branches and taking reduce taking conditional branches
```c
if (x > 0) {
    y = x + 1;
    if (y > 10) {
        z = y * 2;
        printf("%d", z);
    }
}

// Can be converted to 
if (x > 0 && x + 1 > 10) {
    z = (x + 1) * 2;
    printf("%d", z);
}
```

#### Loop invariant code motion
- It specifies on a condition if we perform some operations to be carried out
and then compare for a condition.
- Instead of that , perform the calculation outside the loop and assign a value in
the calculation.
- Known as *hoisting* or *scalar* promotion
```c
while(i <= limit -2){
	///
}


// Optimize it to

t1 = limit-2
while(i <= t1){

}
```


#### Dead code Elimination
- The code that do not affect the program are eliminated

#### Strength Reduction
- Strength reduction is a compiler optimization technique that replaces expensive operations with cheaper ones that produce the same result
- Multiplication by 2 powers
```c
int x = y * 8;
// to 
int x = y<<3;
```
- Exponentiation
```c
double x = pow(2.0, y);

// to

double x = 1<<y;
``` 

```c
if(i%2){

}else{

}

// optimize this to 
00001&1
if(!(i&1)){

}else{

}
```


## Low Level Optimization

####  Register allocation
```c
int x = 10;
for(int i=0;i<10;i++){
	i *= i;
}
```

- Better register allocation
- Instead of assigning variables to memory locations we can assign them to registers and then have faster access to them especially when they are more frequent in use.

#### Instructions Scheduling
- Reorder instructions to avoid pipeline stalls
```c
int i = 5;--------------
int x = 23;            |
int y = x *1;          |
int z = x*y;           |
<----------------------
for( ;i<10;i++){
	i += 10;
}
```

#### Floating point unit optimization
```c
double x = 2.0;
float y = 1.0;
double z = x*y;
```
- Use FPU units for floating point calculations
- Exists in pentium

#### Branch prediction
- Use dynamic branch prediction to guess if branch would be taken and save CPU cycles
```c
I1
I2 // Branch to I9
I3
I4
I5
```

#### Peephole and profile based optimizations
- Peephole optimization is a local optimization technique that examines a small window of instructions in the compiled code and makes changes to improve performance. 
- This technique is called "peephole" because it looks through a small window of instructions, similar to looking through a peephole in a door.


## Machine Independent Optimizations
### Types 

#### Function preserving

![[#Elimination of Common Sub expression |Common Sub-expression elimination]]

![[#Constant propagation|Constant Propogation]]

![[#Copy Propagation]]

![[#Dead code Elimination|Dead code elimination]]

#### Loop Optimization
![[#Loop invariant code motion|Code Motion]]

![[#Strength Reduction|Strength Reduction]]

##### Frequency reduction
- Move code out of loop optimization

```c
int x = 10;
while(true){

}
```

#####  Loop distribution
- Loop distribution is an optimization technique that splits a loop into multiple loops in order to improve performance. 
- The idea behind loop distribution is to break up a loop into smaller pieces that can be executed more efficiently.
```c
for (int i = 0; i < N; i++) {
    a[i] = b[i] + c[i];
    d[i] = e[i] * f[i];
}
```

```c
for (int i = 0; i < N; i++) {
    a[i] = b[i] + c[i];
}

for (int i = 0; i < N; i++) {
    d[i] = e[i] * f[i];
}
```
