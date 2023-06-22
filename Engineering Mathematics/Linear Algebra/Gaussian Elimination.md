# Echelon Form

$$\begin{pmatrix} 
\require{enclose}
{\scriptstyle \enclose{circle}{\kern .06em 5\kern .06em}}
& 1 & -6 & 0 \\ 0 & \require{enclose}
{\scriptstyle \enclose{circle}{\kern .06em 1\kern .06em}}  & -2 & 1 \\ 0 & 0 & 0 & \require{enclose}
{\scriptstyle \enclose{circle}{\kern .06em -6\kern .06em}}\end{pmatrix}$$
- All non-zeros rows are above any rows of all zeros.
- All entries in a column below leading entry are zero
- Leading entry are nonzero leftmost entry

In row echelon form,

A column whose coefficients is a leading non-zero is called a pivot column or basic variables.
Otherwise it is known as free column.

Column and variables are same.

$$\begin{pmatrix} 
\overbrace{\require{enclose}
{\scriptstyle \enclose{circle}{\kern .06em 5\kern .06em}}}^\text{pivot}
& \overbrace{1}^\text{pivot} & \overbrace{-6}^\text{free} & \overbrace{0}^\text{pivot} \\ 0 & \require{enclose}
{\scriptstyle \enclose{circle}{\kern .06em 1\kern .06em}}  & -2 & 1 \\ 0 & 0 & 0 & \require{enclose}
{\scriptstyle \enclose{circle}{\kern .06em -6\kern .06em}}\end{pmatrix}$$

$$
\begin{pmatrix} \overbrace{0}^{\text{free}} & \overbrace{\enclose{circle}{5}}^{\text{pivot}} & \overbrace{3}^{\text{free}} & \overbrace{-4}^{\text{free}} & \overbrace{5}^{\text{pivot}} & \overbrace{-2}^{\text{pivot}} \\ 0 &  0 & 0 & 0 & \enclose{circle}{7} & 3 \\ 0 & 0 & 0 & 0 & 0 & \enclose{circle}{3} \\ 0 & 0 &  0 & 0 & 0 & 0 \end{pmatrix}
$$ 


>[!question]
>Which are basic variable and which are free variable in the following matrix
>$$\left[\begin{array}{rrrrr|r} 1 & 2 & 0 & -1 & -2 & 0 \\  0  & 1 & 1 0 & 3 & 0 & 0\\ 0 & 0 & 0 & 1 & 1 & 0 \\ 0 & 0 & 0 & 0 & 0&0\end{array}\right]$$

>[!question]
>Which are the basic variable and which are the free variables in the following matrix 
>$\left[\begin{array}{rrr|r} 1 & 2 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & 0 &0 \end{array}\right]$

**FREE COLUMN IS ALWAYS A LINEAR COMBINATION OF PIVOT COLUMNS**
**PIVOT COLUMNS ARE LINEARLY INDEPENDENT**


# Elementary Row operations

- Swap Rows $R_{i} \leftrightarrow R_{j}$ 
- Multiply Row by non zero scalar $R_{i} \rightarrow cR_i$
- Add scalar multiple of one row to another $R_{i} \rightarrow R_{i}+ cR_{j}$

# Rank

- No. of Linearly independent rows
- No of linearly independent columns
- Pivot elements in echelon form
- Non zero rows in echelon form

>[!question]
>GATE 1995
>Find rank
>$\begin{pmatrix}0 & 0 & -3 \\ 9 & 3 & 5 \\ 3 & 1 & 1\end{pmatrix}$
>>[!answer]-
>>$\displaylines{ R_{1} \leftrightarrow R_{3} \\ \begin{pmatrix}3 & 1 & 1 \\ 9 & 3 & 5 \\ 0 & 0 & -3\end{pmatrix}}$
>>$\displaylines{ R_{2} \rightarrow R_{2} - 3 R_{1} \\ \begin{pmatrix}3 & 1 & 1 \\ 0 & 0 & 2 \\ 0 & 0 & -3\end{pmatrix}}$
>>
$\displaylines{ R_{3} \rightarrow R_{3} - \frac{3}{2} R_{2} \\ \begin{pmatrix}3 & 1 & 1 \\ 0 & 0 & 2 \\ 0 & 0 & 0\end{pmatrix}}$
>>Rank = no. of pivot columns = 2

**RANK is 0 only for Null matrix**

## Rank Nullity Theorem

![[Gaussian Elimination 2023-06-14 02.33.39.excalidraw]]


# Solving Ax  = b

1. Homogeneous (Ax = 0)
2. Heterogeneous (Ax = b b not zero)

>[!question]
>$\displaylines{\begin{align*}x_{1}+x_{2} - x_{3} &= 0 \\ x_{1}-x_{2}+ x_{3}&= 2 \\ 2x_{1}-x_{2}-x_{3}&= -3\end{align*}}$
>>[!answer]-
>>$$\left[\begin{array}{rrr|r} 1 & 1 & -1 & 0  \\  1  & -1 & 1 & 2 \\2&-1 & -1 & -3 \end{array}\right]$$ $$\displaylines{R_{3} \rightarrow R_{3}-2R_{1} \\ R_{2} \rightarrow R_{2} - R_{1}} \\  \left[\begin{array}{rrr|r}1 & 1 & -1 & 0  \\  0  & -2 & 2 & 2  \\ 0 & -3 & 1 & -3 \end{array}\right]$$ $$\displaylines{R_{3} \rightarrow -2R_{3}+3R_{1}  \left[\begin{array}{rrr|r} 1 & 1 & -1 & 0  \\  0  & -2 & 2 & 2  \\ 0 & 0 & 4 & 12\end{array}\right]}$$ $$\displaylines{4x_{3}= 12 \implies x_{3} = 3 \\ -2x_{2}+2x_{3} = 2 \implies x_{2} = 2 \\ x_{1}+x_{2}-x_{3}=0 \implies x_{1}=1}$$
>>


 >[!question]
 >$$\displaylines{\begin{align*} 5x_{1}- 11x_{2} &= -2 \\ -4x_{1}+9x_{2}&= 1 \\ x_{1}-2x_{2}&= -1\end{align*}}$$



>[!question]
>$$\displaylines{\begin{align*} x - 3y + z &= 4 \\ -x + 2y -5z &= 3 \\ 5x - 13y + 13z &= 8 \end{align*}}$$
>>[!answer]-
>>$$\displaylines{\left[\begin{array}{rrr|r}
   1 & -3 & 1 & 4  \\  0  & -1 & 4 & 7  \\ 0 & 0 & 0 & 2
 \end{array}\right] \\ 0 = 2? \\ \text{This is the case of no solution}}$$ 


 
**A SYSTEM WHICH HAS NO SOLUTION IS KNOWN AS INCONSISTENT**

**A SYSTEM HAVING AT LEAST ONE SOLUTION IS KNOWN AS CONSISTENT**


![[Gaussian Elimination 2023-06-14 03.09.39.excalidraw]]

>[!question]
>If homogeneous system with $5$ equation and $5$ unknown always have a unique solution.
>>[!answer]-
>>Not guaranteed.
>>Eg. 
>>$\displaylines{\begin{align*}x + y + z &= 0 \\ 2x + 2y+ 2z  &= 0 \\ 3x+3y+3z &= 0\end{align*}}$  

>[!question]
>Find numbers $a,b,c$ and such that the linear system corresponding to augmented matrix.
>$\left[\begin{array}{rrr|r}1 & 2 & 3 & a \\ 0 & 4 & 5 & b \\ 0 & 0 & d & c\end{array}\right]$
>
>a) No solution
>>[!answer]-
>>$d = 0, c \neq 0$
>
>b) Infinitely many solution
>>[!answer]-
>>$d =0, c=0$
>>$a,b \in \mathbb{R}$
>Referencing the chart above, 
>if $[000 \cdots 0|\text{non zero}] \rightarrow \text{Free variables?}  \rightarrow \text{Yes}$ 
>How free variable?
>Well as $d = 0$ there is no pivot element in the last column 
>

Imp don't see answer first attempt it

>[!question]
>Solve 
>$\left[\begin{array}{rrrr|r}2 & 1 & -1 & 2 & 0 \\ 1 & 1 & 0 & 3 & 0 \end{array}\right]$
>>[!answer]-
>>$R_{2}\rightarrow 2R_{2}-R_1$
>>$\left[\begin{array}{rrrr|r}2 & 1 & -1 & 2 & 0 \\ 0 & 1 & 1 & 4 & 0\end{array}\right]$
>>
>>So we now observe
>>$\left[\begin{array}{rrrr|r}\enclose{circle}{2} & 1 & -1 & 2 & 0 \\ 0 & \enclose{circle}{1} & 1 & 4 & 0\end{array}\right]$
>>As we see there are two pivot elements. Meaning two pivot columns. 
>>Let name each column from left $x,y,z,w$
>>So $x,y$ is pivot column. 
>>As $z,w$ is a free column, they are linearly dependent on pivot columns. 
>>So the logic is we assign variables to free variables.
>>Here we assign, $z =s, w = t$ 
>>
>>$\displaylines{\begin{align*}y + z + 4w  &=  0 \\ y + s + 4t &= 0 \\ y &= -s - 4t \\ \text{Now we solve the first equation} \\ 2x + y -z + 2 w &= 0 \\ 2x + (-s - 4t) - s + 2t &= 0 \\ x &= s + t \\ x &=  \begin{pmatrix}s+t \\ -s - 4t \\ s \\ t\end{pmatrix} \\ x &= \begin{pmatrix}s \\ -s \\ s \\ 0 \end{pmatrix} + \begin{pmatrix}t \\ -4t \\ 0 \\ t \end{pmatrix} \\ x &= s\begin{pmatrix}1 \\ -1 \\ 1 \\ 0 \end{pmatrix} + t \begin{pmatrix}1 \\ -4 \\ 0 \\ 1\end{pmatrix}\end{align*}}$
>>
>>The matrices  
>>$\begin{pmatrix}1 \\ -1 \\ 1 \\ 0 \end{pmatrix}$ $\begin{pmatrix}1 \\ -4 \\ 0 \\ 1\end{pmatrix}$
>>are linearly independent solutions to the system. Every other solution would be linear combination of the two solution. 
>>So what we can conclude?
>>Number of linearly independent solutions  = Number of free variables.
>>BUT REMEMBER
>>Number of linearly independent columns still = Number of basic variables.

^d02d9b

As we see in the above  question
**Number of linearly independent solution = Number of free variables**
Why? after assigning the free variables they are the only one we can isolate them. 

>[!question]
>Suppose the parametric form of solution to $Ax = b$  looks like
>$x = s \left[\begin{array}{c} \\ \vdots \\ \\  \end{array}\right] + t \left[\begin{array}{c} \\ \vdots \\ \\  \end{array}\right] + p \left[\begin{array}{c} \\ \vdots \\ \\  \end{array}\right]$
>A has the dimension $A_{20 \times 30}$
>Number of linearly independent columns in $A$?
>>[!answer]-
>>We know that the number of independent solutions = free variables.  
>>Hence Number of independent solutions = $3$ (s, t , p)
>>Now we know that, Number of linearly independent columns = Number of pivot columns.
>>Number of linearly independent solutions = Number of free variables(nullity)
>>By the [[#Rank Nullity Theorem]] we know $\text{rank + nullity = no. of columns}$ Rank is the number of pivot columns and nullity is the number of free columns. 
>>Nullity $n = 3$ $r = 30 -3 = 27$
>>Hence the number of independent columns - $27$

>[!question]
>Suppose $A_{20 \times 50}$  has 10 pivot columns.
>1. No of linearly independent solutions $Ax = 0$
>>[!answer]-
>>$50 -10 = 40$ the number of free variables.
>2. No. of Linearly independent columns in $A$
>>[!answer]-
>>Number of linearly independent column = number of pivot column
>>10
> 

>[!question]
>Gate 2014
>Suppose $P_{4 \times 5}$ such that every solution of equation $Px = 0$ is scalar multiple of $\begin{pmatrix}2 & 5 & 4 & 3 & 1\end{pmatrix}^\text{T}$
>Ranks of P is __
>>[!answer]-
>>Every solution being a scalar multiple of $\begin{pmatrix}2 & 5 & 4 & 3 & 1\end{pmatrix}^\text{T}$ indicates that there is one free variable. 
>>Hence the nullity is 1. 
>>By [[#Rank Nullity Theorem]] $1 + r = 5, r = 4$.
>>Hence rank is 4.
>>

>[!question]
>Consider a $3 \times 3$ matrix $A \neq 0$ which of following are possible number of free columns in $A$?
>1. 0
>2. 1
>3. 2
>4. 3
>>[!answer]-
>>All except last. All columns can't be free. Because We can always make atleast one column 0 by dividing the first by its value and subtracting everything below it by it.

>[!question]
>Mark correct statement
>a. A consistent system with no free columns will have unique solution
>b. A consistent system with free columns have no solution
>c. A consistent system with free columns have infinite solution
>d. A inconsistent system with free columns will have infinite solution.
>>[!answer]-
>>c is correct. Try to come up with why.

>[!question]
>Suppose a system $A_{8 \times 9}x = 0$ has some non trivial solution such that solutions are linear combinations of 3 linearly independent vectors. What is number of linear independent columns
>>[!answer]-
>>No. of linearly independent columns  =  $9 - 3 = 6$


The below question is IMPORTANT, match it with [[Gaussian Elimination#^d02d9b]]
>[!question]
>Solve this
>$A = \left[\begin{array}{cccc|c} 2 & 1 & -1 & 2 & 0 \\ 1 & 1 & 0 & 3 & -2 \end{array} \right]$
>>[!answer]-
>>After solving this 
>>$A = \left[\begin{array}{cccc|c} 2 & 1 & -1 & 2 & 0 \\ 1 & 1 & 0 & 3 & -2 \end{array} \right]$
>>We see that the reduction brings the coefficient matrix same as the previous question referenced. 
>>On solving the solution comes out to be 
>>$\begin{pmatrix}2 + s + t \\ -4 -s - 4t \\ s \\ t\end{pmatrix} = \begin{pmatrix}2 \\ -4 \\ 0 \\ 0 \end{pmatrix} + \begin{pmatrix}s +t \\ -s - 4t \\ s \\ t\end{pmatrix}$
>>As we can observe we have a just added a constant matrix to the solution in the previously referenced answer. 
>>![[Gaussian Elimination 2023-06-19 22.22.26.excalidraw]]
>>So we can see there is only a constant difference between homogeneous and heterogeneous solution.


Important question

>[!question]
>Let $Ax = b$ be a system of equation. If Rank(A) $\neq$ Rank(Ab) (We just appended the column of b to Right hand side A). 
>>[!answer]-
>>Lets establish what can happen with ranks
>>If $b$ is a linear combination of $A$ then the rank wouldn't increase as rank is the number of linearly independent columns(No. of pivot columns) doesn't increase.
>>If $b$ is not a linear combination of $A$ then rank of $Ab$ would be $\text{Rank}(A)+1$
>>Finally
>>$\begin{array}{drec}\text{b is not linear combination of A} & \text{Rank}(Ab) & = & \text{Rank}(A) \\ \text{b is linear combination of A} &  \text{Rank}(Ab) & = & \text{Rank}(A) + 1 \end{array}$

![[Gaussian Elimination 2023-06-19 22.51.08.excalidraw]]

>[!question]
>Consider a matrix of size $m \times n$ 
>1. Rank(A) = m  = n
>2. Rank(A) = n
>3. Rank(A)  = m , $m \neq n$
>4. Ranks(A) < m and Rank(A) < n
>
>For the following cases discuss about solution to $Ax = b$
>a. Infinite solution
>b. Exactly one solution
>c. There is 0 or 1 solution
>d. There is 0 or infinite solution.


---

>[!question]
>GATE 1996
>$A_{m \times n} x = b$ Which is false?
>1. System has a solution iff both $A$ and $A|b$ have same rank
>2. If $m<n$ and $b = 0$ then $\infty$ solutions
>3. If $m = n, b \neq 0$ system has a unique solution
>4. System have only trivial solution when $m = n, b = 0$ and rank(A) = n

# Why doing row ops doesn't affect column?

**Number of Linearly Independent row = Number of linearly independent column**

$\displaylines{\begin{align*}\begin{pmatrix}1 & 2 & 3 \\ 2 & 3 & 5 \\ 3 & 4 & 7 \end{pmatrix}& C_{3} = C_{1} +  C_{2} \\ & \big\downarrow R_{1} \rightarrow R_{1} + R_{2} \\\begin{pmatrix}3 & 5  & 8  \\ 2 & 3 & 5 \\ 3 & 4 & 7 \end{pmatrix}& C_{3} = C_{1} + C_{2}  \end{align*} }$

We see performing elementary row operation doesn't change the column dependency.
On an intuitive level we can understand this by thinking that each columns are affected by the row operation.

>[!question]
>$\begin{pmatrix}1 & 4 & 6 \\ 2 & 5 & 9 \\ 3 & 6 & 12\end{pmatrix} \xrightarrow{\text{Unknown elementary row op}} \begin{pmatrix}2 & 4 & a \\3 & 6 & b \\ 5 & 7 & c \end{pmatrix}$
>Whats value of a,b,c ?
>>[!answer]-
>>We can observe in the first matrix that $C_{3} = 2C_{1} + C_{2}$


**Linear dependence is preserved when doing elementary row operations**

---
>[!question]
>For which values of h and k the system has no solution
>$\begin{align*} x_{1} + 3x_{2} &= k \\ 4x_{1} + hx_{2} &= 8 \end{align*}$

>[!question]
>True / False
>1. A matrix can have more than one echelon form 
>2. If $v$ is a non-zero vector in $R^{n}$, then $v$ is linearly independent set
>3. A homogeneous system always has infinitely many solutions
>4. Every $5$ vector in $R^6$ are always linearly independent 

>[!question]
>For which $h,k$ no solution?
>$\begin{align*} 2x_{1} + hx_{2} &= -2 \\ x_{1} + 3x_{2} &= k \end{align*}$
>

>[!question]
>A $n \times n$ which are true for $A$ if $Ax = 0$ only has trivial solution
>Which one of them is right and explain why
>1. The linear system $Ax = 0$ has infinitely many solution
>2. Columns of $A$ are linearly dependent
>3. The reduced row echelon form of $A$ has $n-1$ pivot columns
>4. A is $0$ matrix
>5. None

>[!question]
>Find $x_{1}, x_{2}, x_3$ 
>$x_1\begin{pmatrix}1 \\ 0 \\ -1 \end{pmatrix} + x_{2}\begin{pmatrix}-3 \\ 2 \\ 5\end{pmatrix} + x_{3}\begin{pmatrix}3 \\ -2 \\ -1\end{pmatrix} = \begin{pmatrix}2 \\ 4 \\ -2\end{pmatrix}$

>[!question]
>$\displaylines{\begin{align*} x_{1} - x_{2} &= 2 \\ 2x_{1} + hx_{2}&= k \end{align*}}$
>1. For what values of $h$ and $k$ system has no solution?
>2. Only one solution
>3. Infinite solution


>[!question]
>Find values for unique solution
>$\displaylines{\begin{align*} x + y &= 5 \\ 2x + hy &= 3\end{align*}}$

>[!question]
>Number of linearly independent vectors in following set?
>$v = \left\{ \begin{pmatrix}a - 2b \\ -b + c \\ -2c\end{pmatrix} \middle| a,b,c \in R \right\}$

