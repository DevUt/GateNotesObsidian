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


$$\newenvironment{amatrix}[1]{%
  \left(\begin{array}{@{}*{\numexpr#1-1}{c}|c@{}}
}{%
  \end{array}\right)
}
\begin{amatrix}{2}
   1 & 2 & 3 \\  a & b & c
 \end{amatrix}
$$

