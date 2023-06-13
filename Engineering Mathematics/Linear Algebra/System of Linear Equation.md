$\displaylines{a_{11}x_{1}+ a_{12}x_{2}+ \cdots a_{1n}x_{n}= b_{1}\\ a_{21}x_{1}+ a_{22}x_{2}+ \cdots a_{2n}x_{n}= b_{2} \\ \vdots \\ a_{m1}x_{1}+ a_{m2}x_{2}+ \cdots a_{mn}x_{n}= b_{m}}$

We have $n$ unknowns and  $m$ equations.

$\begin{pmatrix}a_{11} & a_{12} & \cdots & a_{1n} \\ \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn}\end{pmatrix}$  This the coefficient matrix

$\begin{pmatrix}x_{1} \\ \vdots \\ x_n\end{pmatrix}$ 

$\begin{pmatrix}b_{1} \\ \vdots \\ b_n\end{pmatrix}$ 

The above system of equation can be represented as such

$\begin{pmatrix}a_{11} & a_{12} & \cdots & a_{1n} \\ \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn}\end{pmatrix}$$\begin{pmatrix}x_{1} \\ \vdots \\ x_n\end{pmatrix}$ $=$ $\begin{pmatrix}b_{1} \\ \vdots \\ b_n\end{pmatrix}$ 

>[!question]
>Do we always have a solution to $Ax = b$?
>>[!answer]-
>Not necessary.


>[!question]
>Suppose a matrix $A_{3 \times 3}$  contains L.I columns. What can you say about the solution to $Ax = b$ $(b \neq 0)$
>> [!answer]-
>> We have 3 linearly independent vectors. They span $\mathbb{R}^3$.
>> Hence we can generate any vector $b$.
>> Hence the solution always exist.


>[!question]
>Suppose a matrix $A_{3 \times 4}$  contains 3 L.I columns. What can you say about the solution to $Ax = b$ $(b \neq 0)$
>> [!answer]-
>> We have 3 linearly independent vectors. They span $\mathbb{R}^3$.
>> Hence we can generate any vector $b$.
>> Hence the solution always exist.

----
>[!question]
>Consider a matrix $A_{m \times n}$. 
>For a system $Ax = b$ what can you say about below statement.
>Statement: If $m < n$ then $Ax = b$ always have a solution.
>>[!answer]-
>>False, 
>>Because we have $n$ vectors of dimension $n$.
>>The question doesn't mention, whether at least $m$ vectors are L.I. 
>>If there were $m$ L.I vectors then we would always have a solution.
>>We would infact have infinite solutions. The set of column vectors would have been L.D.
>>![[System of Linear Equation 2023-06-13 01.46.32.excalidraw]]
>>So when number of equations > no. of variables 
>>There are two cases
>>1. No solution (We don't have $m$ L.I vector)
>>2. Infinite solutions. 

>[!question]
>Every system of 3 equation in 8 unknown has a solution
>>[!answer]-
>>False. Reasons check above

>[!question]
>If A and B are $m \times n$ such that B can be obtained from A by column operation then A can also be obtained from B by column operation.
>

>[!question]
>GATE 2016
>$m$ linear equation $n$ variables
>1. If $m<n$ then all such system have a solution
>2. If  $m>n$ then none of these system have a solution 
>3. If $m == n$ then $\exists$ a system which has a solution
>>[!answer]-
>>1. Check the question above the 2 questions. 
>>2. We know that b is linear combination of A to have a solution. If we have less vectors than the dimension, they wouldn't span the ENTIRE space. But they still span some, so if b falls in that we have a solution. 
>>3. We always have the null vector having trivial solution.

$\begin{pmatrix}\\ a_{1} & a_2 & a_{3} \\ & \cdots \end{pmatrix}\begin{pmatrix}\\ b_{1} & b_2 & b_{3} \\ & \cdots  \end{pmatrix}= \begin{pmatrix}\\ c_{1} & c_{2} & c_{3} \\ & \cdots  \end{pmatrix}$

$c_{1} = b_{1}a_{1} + b_{1}a_{2} + b_{1}a_{3}$

>[!question]
>GATE 2014
>Is the set of column in resultant matrix independent ? If no, then what is the size of the set having maximum columns and still being independent
>$A  = \begin{pmatrix}2 \\ -4 \\ 7\end{pmatrix}\begin{pmatrix}1 & 9 & 5\end{pmatrix}$ 
>>[!answer]-
>>$\begin{pmatrix}1 \times \begin{pmatrix}2 \\ -4 \\ 7\end{pmatrix} & 9 \times \begin{pmatrix}2 \\ -4 \\ 7\end{pmatrix} & 5 \times \begin{pmatrix}2 \\ -4 \\ 7\end{pmatrix} \end{pmatrix}$


>[!question]
>$A_{m \times n}$ has $m$ linearly independent column then -
>a. There is always  solution to $Ax  = b$
>b. There is never solution of $Ax = b$ for any $b$
>c. There may or may not be solution of $Ax = b$
>>[!answer]-
>>There is always a solution because $m$ linearly independent columns would span the space and any $b$ can be hence produced.

![[System of Linear Equation 2023-06-13 02.39.25.excalidraw]]

Proof for unique case
Lets assume contradiction,
$\exists$ a vector $b$ which has more than one solution.

$b = c_{1}v_{1}+ c_{2}v_{2} + \cdots$
$b = k_{1}v_{1}+ k_{2}v_{2} + \cdots$

Subtract both equation

$0 = (c_{1}-k_{1})v_{1}+ \cdots$ 

Because $v_{1}, v_{2}, \cdots, v_n$ are L.I 
this means $(c_{1}-k_{1}) = 0$ 
$c_{1}= k_{1}$


>[!question]
>Let $c_{1}, \cdots, c_{n}$ be scalars, not all zero, such that $\sum\limits_{i=1}^{n} c_{i}a_{i} = 0$ where  $a_{i}$ are column vectors in $R^{n}$ 
>Consider the set of the linear equation
>$Ax=b$
>where $A = [a_{1}\cdots a_{n}]$ and $b = \sum\limits_{i}^{n}a_{i}$ 
>The set of equations has
>A. A unique solution at $x = J_{n}$ where $J_{n}$ denotes a n-dimensional vector of all 1
>B. no solution
>C. infinitely many solution
>D. finitely many solution
>>[!answer]-
>>From first statement we come to know that the columns are linearly dependent.
>>We know that b is a linear combination of column's of A. 
>>So there must be infinite solutions.

---
>[!question]
>Which of the following statement(s) is / are true
>a. Given a coefficient matrix $A_{m \times n}$ the number of solutions for $Ax = 0$ could be either zero or one.
>b. There exists a coefficient matrix $A_{m\times n}$ $m > n$ which doesn't give solution for any $b$
>c. There exists a coefficient matrix $A_{m\times n}$ $m=n$, which doesn't give solution for some $b$
>d. If a coefficient matrix $A_{m\times n}$ gives a solution for every b, then $m=n$
>>[!answer]- 
>>a. False, since the number of solutions can not be zero for the system, $Ax = 0$
>>b. False, There always exists the zero column vector which the given A would have solution.
>>c. is true, since $m = n$ doesn't mean that there a n linearly dependent vectors in $\mathbb{R}^n$
>>d. is false, If a gives solution for every b, then $m \leq n$
>>

>[!question]
>Given a coefficient matrix $A_{m\times n}$ what can be said about number of solutions
>if (zero) / unique / infinite
>1. $m=n$
>2. $m<n$
>3. $m>n$
>> [!answer]-
>> We cannot say for surely. Until we know about the linear in-dependency or dependency 

 
>[!question]
>Gilbert Strang
>For the give matrix A
>$\begin{pmatrix}1 & 1 & 1 \\ 1 & 2 & 5 \\ 2 & 3 & 8\end{pmatrix}$ 
>a. Find the linear combination of first and second column which obtains the third column vector.
>b. Check if there is a solution for the following $b$
>i. $b = \begin{pmatrix}2 \\ 3 \\ 5\end{pmatrix}$
>ii. $b = \begin{pmatrix}4 \\ 6 \\ 11\end{pmatrix}$
>>[!answer]-
>>1. $c_{1} + c_{2}$
>>2. i. $X = \begin{pmatrix}1 \\ 1 \\ 0\end{pmatrix}$
>>  ii. No solution

>[!question]
>The given matrix has solution for:
>$\begin{pmatrix}1 & 1 & 1 \\ 1 & 2 & 5 \\ 2 & 3 & 8\end{pmatrix}$ 
>a. A vectors $b$ in $\mathbb{R}^3$
>b. No vector $b$ in $\mathbb{R}^3$
>c. Some vector $b$ in $\mathbb{R}^3$
>>[!answer]-
>>C. Check above

>[!question]
>Check the number of solution (zero, unique, infinite) for the following system of linear equations.
>$A = \begin{pmatrix}1 & 4 & 3 \\ 3 & 8 & 9 \\ 0 & 0 & 0\end{pmatrix}$ 
>
>$b = 0$
>>[!answer]-
>>Infinite solutions. The third column is linearly dependent on the first column. And because we always have solution for $0$ matrix hence $\infty$ solutions

>[!question]
>The following matrix A, doesn't give solution for any b, since its columns are linearly dependent. True / False. 
>$\begin{pmatrix}1 & 3 & 0 \\ 4 & 8 & 0 \\ 3 & 9 & 0\end{pmatrix}$
>>[!answer]-
>>False. Always 0 has solution.

>[!question]
>Find a $b$ such that the system $Ax = b$ has no solution
>$\begin{pmatrix}1 & 3 & 0 \\ 4 & 8 & 0 \\ 3 & 9 & 0\end{pmatrix}$
>>[!answer]-
>>$\begin{pmatrix}4 \\ 12 \\ 13\end{pmatrix}$


>[!question]
>Give an example of each the following, explaining why it has the required property, or explain why no such example exists.
>a. A linear system with 3 equations in 2 variables which has solution
>b. A linear system with 2 equation in 3 variables  which has no solution. 
>c. A linear system with 2 equations in 3 variables which has solution for no b $b \neq 0$ 
>>[!answer]-
>>1. When the no. of equations is more than the number of variables then it is known as overdetermined system. In such systems solutions only exist when some equation is just the copy of another equations. 
>>  $\displaylines{\begin{align*}2x + 3y &= 5 \\ x + 5y &= 2 \\ 4x + 6y &= 10  \end{align*}}$
>>2. Parallel planes 
>> $\displaylines{\begin{align*} x_{1} + x_{2} + x_{3} &= 0 \\ x_{1} + x_{2} + x_{3} &= 1 \end{align*}}$
>>3. Parallel planes


$$\newenvironment{amatrix}[1]{%
  \left(\begin{array}{@{}*{\numexpr#1-1}{c}|c@{}}
}{%
  \end{array}\right)
}
\begin{amatrix}{2}
   1 & 2 & 3 \\  a & b & c
 \end{amatrix}
$$

