What does a determinant actually mean?

<iframe width="560" height="315" src="https://www.youtube.com/embed/Ip3X9LOh2dk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For our understanding we can take it as a scalar quantity associated with the matrix.

# Extreme Basics 

Determinant of a matrix $A$ is represented by $\det(A)$ or $|A|$  or $\triangle(A)$   

# Basic Property

## Property 1
The determinant of the identity matrix is 1.

$\det(\begin{pmatrix}1 & 0 & \cdots & 0 \\ 0 & 1 & \cdots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \ldots & 1  \end{pmatrix}) = 1$

## Property 2

The sign of determinant changes sign when two rows (or two columns) are exchanged

$\vert \begin{pmatrix}1 & 0 \\ 0 & 1\end{pmatrix} \vert = 1$ 
$\vert \begin{pmatrix}0 & 1 \\ 1 & 0\end{pmatrix} \vert = -1$ 

## Property 3

Linearity is for one row at a time

e.g.

$\begin{vmatrix}ta & tb \\ c & d\end{vmatrix} = t \begin{vmatrix}a & b  \\c & d \end{vmatrix}$ 

From one row we can remove the common multiple, this contrasts the matrix operation in which we have to take common from each element.

$\begin{vmatrix}a + a' & b + b' \\ c & d\end{vmatrix} = \begin{vmatrix}a & b \\ c & d\end{vmatrix} + \begin{vmatrix}a' & b' \\ c & d \end{vmatrix}$ 


>[!question]
>Can we ?
>$\begin{vmatrix}a + p & b + q \\ c + r & d + w \end{vmatrix} = \begin{vmatrix}a & b \\ c & d\end{vmatrix} + \begin{vmatrix}p & q \\ r & q\end{vmatrix}$ 
>>[!answer]-
>>No!
>>We can only expand one row at a time
>>$\begin{vmatrix}a & b \\ c + r & d +w\end{vmatrix} + \begin{vmatrix}p & q \\ c+r & d+w\end{vmatrix}$
>>
>>$\begin{vmatrix}a & b \\ c & d\end{vmatrix} + \begin{vmatrix}a & b \\ r & w\end{vmatrix} + \begin{vmatrix}p & q \\ c & d\end{vmatrix} + \begin{vmatrix}p & q \\ r & w\end{vmatrix}$


# Proving other stuff
Now using the Basic properties we can prove a lot of stuff. We would see proof of them each. 

*IT IS RECOMMENDED TO REMEMBER THE STUFF WE PROVE*

Even though we can prove it each time, it would be useless for GATE, because we would miss insights in the questions.

Try to prove them using only the property stated above.

>[!property]
>If two rows of $A$ are equal then $\det(A) = 0$
>>[!answer]-
>>Let $A = \begin{vmatrix}a & b \\ a & b\end{vmatrix} -(1)$ 
>>$R_{1} \leftrightarrow R_{2}$
>>Property 2 
>>$-A = \begin{vmatrix}a & b \\ a & b\end{vmatrix} -(2)$
>>Adding (1) & (2)
>>$0 = \begin{vmatrix}a & b \\ a & b\end{vmatrix}$

>[!Property]
>Subtracting a multiple of one row from another leaves $\det(A)$ unchanged 
>>[!answer]-
>>$\displaylines{\begin{align*}\begin{vmatrix}a & b \\ c - la & d -lb \end{vmatrix} &= \begin{vmatrix}a & b \\ c & d\end{vmatrix} +  \begin{vmatrix}a & b \\ -la & -lb\end{vmatrix} \\ &= \begin{vmatrix}a & b \\ c & d\end{vmatrix} - l\overbrace{\begin{vmatrix}a & b \\ a & b\end{vmatrix}}^{0} \\ &= \begin{vmatrix}a & b \\ c & d\end{vmatrix} \end{align*}}$

>[!Property]
>A matrix with a row of zeros has $\det(A) = 0$  
>>[!answer]-
>>$\displaylines{\begin{align*}t &= \begin{vmatrix}0 & \ldots & 0 \\ \vdots & \ddots & \vdots \\ \ldots & \ldots & \ldots\end{vmatrix} \\ kt &= \begin{vmatrix}k\times 0 & \ldots & k \times 0 \\ \vdots & \ddots & \vdots \\ \ldots & \ldots & \ldots\end{vmatrix} \end{align*}}$
>>
>>
>>$(k-1)t = \det(\text{Zero matrix})$
>>For $k \neq 1$
>>$t = 0$


>[!property]
>Determinant of diagonal matrix is product of diagonal elements 
>>[!answer]-
>>$\begin{vmatrix}a_{11}&  &  & \\ & a_{22}  &  &  \\ &  & \ddots & \\ &  &  & a_{nn}   \end{vmatrix}$
>>Take common from each row, and it becomes an Identity matrix
>>$a_{11}a_{22}\ldots a_{nn}\begin{vmatrix}1&  &  & \\ & 1  &  &  \\ &  & \ddots & \\ &  &  & 1  \end{vmatrix}$


>[!question]
>$A = \begin{vmatrix}a_{11} & a_{12} & a_{13} & a_{14} \\ a_{21} & a_{22} & a_{23} & a_{24} \\ a_{31} & a_{32} & a_{33} & a_{34} \\ a_{41} & a_{42} & a_{43} & a_{44}\end{vmatrix}$
>
>$\det(A) = 3$ Find out value of $B$
>
>$B = \begin{vmatrix}a_{12} & a_{11} & a_{13} & a_{14} + 3a_{13}\\ a_{22} & a_{21} & a_{23} & a_{24} + 3a_{23}\\ a_{32} & a_{31} & a_{33} & a_{34} + 3a_{33}\\ a_{42} & a_{41} & a_{43} & a_{44} + 3a_{43}\end{vmatrix}$
>>[!answer]-
>>$B = -3$

>[!question]
>Suppose that $A$ is $4 \times 4$ matrix and suppose $|A| = 11$ is $B$ is obtained from $A$ by interchanging row $2$ and $4$ what is $|B|$?
>>[!answer]-
>>-11

>[!question]
>$|A_{4\times 4}| = 11 \, \text{Let} \, a_{1},a_{2}, a_{3}, a_{4}$ rows of $A$  If $B$ is obtained by replacing $a_{3}$ by $3a_{1} + a_{3}$
>>[!answer]-
>>$B = A$

>[!question]
> $|A_{4\times 4}| = 11 \, \text{Let} \, a_{1},a_{2}, a_{3}, a_{4}$ rows of $A$  If $B$ is obtained by replacing $a_{3}$ by $7a_{1} + a_{3}$
>>[!answer]-
>>$|B| = 7|A|$

From the above question we can see that when we do $R_{i} \rightarrow R_{i} + kR_{j}$ doesn't change the determinant value. **BUT** $R_{i} \rightarrow pR_{i} + kR_{j}$ multiplies the determinant by $p$

# Calculating determinant

## 2x2

We can actually calculate the determinant using the basic properties.

$\displaylines{\begin{align*}\begin{vmatrix}a & b \\ c & d\end{vmatrix} &= \begin{vmatrix}a & 0 \\ c & d\end{vmatrix} + \begin{vmatrix}0 & b \\ c & d\end{vmatrix} \\ &= \begin{vmatrix}a & 0 \\ 0 & d\end{vmatrix} + \cancel{\begin{vmatrix}a & 0 \\ c & 0\end{vmatrix}}+\cancel{\begin{vmatrix}0 & b \\ 0 & d\end{vmatrix}} +\begin{vmatrix}0 & b \\ c & 0\end{vmatrix} \\ &= ab\begin{vmatrix}1 & 0 \\ 0 & 1\end{vmatrix}- cd\begin{vmatrix}1 & 0 \\ 0 & 1\end{vmatrix} \\ &= ab - cd\end{align*}}$

If we expand $n \times n$ matrix, we would get $n!$ terms in final


## 3x3

$\begin{vmatrix}a_{11} & a_{12} & a_{13}\\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33}\end{vmatrix}$

We know that we would get $3! = 6$ terms in end
How?

We know that each row would only have 1 element as we saw before to take common from. So we have to select 1  from each column 

We have 3 options from the first row. 
Let say I selected $a_{11}$, Now I can't select anything from the first column. 

Two chances from 2nd row $a_{22}, a_{23}$ 
Let say we choose $a_{23}$

Now I have choice from third row
$a_{32}$

$3 \times 2 \times 1 = 6$ choices

## Determining signs 

In expansion of the 3x3 we get a matrix 

$\begin{vmatrix} & a_{12} &  \\ a_{21} & & \\ & & a_{33}\end{vmatrix}$

We rearrange $R_{2}\leftrightarrow R_{1}$ 

So  $-a_{21}a_{12}a_{33}$ would be value from here.

>[!question]
>Let $A_{4 \times 4}$ be matrix. In expansion of $|A|$ is sign of product $a_{13}a_{22}a_{34}a_{41}$
>>[!answer]-
>>Positive 

>[!question]
>Circle the letter which are true for $5 \times 5$ matrices
>1. $\det(-A) = - \det(A)$
>2. $\det(3A) = 3\det(A)$
>3. $|A+B| = |A| + |B|$
>4. $|ABC| = |A||B||C|$

## More ways for Determinant

1. Use permutations (above method)
2. Convert to echelon form and take product of pivots 
3. Calculate co-factor 

# Co-factor

Determinant is dot product of any row (or column) with it's Co-factor. 

$\det(A) = a_{11}C_{11}+ a_{12}C_{12}+ \ldots + a_{1n}C_{1n}$

## Minor 

If **A** is a square matrix, then the minor of the entry in the $i^{ th}$   row and $j^{th}$ column (also called the (i, j) minor) is the determinant of the submatrix formed by deleting the $i^{th}$ row and $j^ th$ column. This number is often denoted $M_{i,j}$. The (_i_, _j_) _cofactor_ is obtained by multiplying the minor by $(−1)^{(i + j)}$ 

Consider,
$\begin{vmatrix}1 & 4 & 7 \\ 3 & 0 & 5 \\ -1 & 9 & 11 \end{vmatrix}$

The $M_{2,3}$ would be calculated 

$\begin{vmatrix}1 & 4 & \square \\ \square & \square & \square \\ -1 & 9 & \square \end{vmatrix}$  

$M_{2,3} = \det(\begin{vmatrix}1 & 4 \\ -1 & 9\end{vmatrix})$

The Co-factor $C_{i,j} = (-1)^{(i+j)}M_{i,j}$  

We can see that $C_{i,j}$ doesn't actually depend upon $a_{ij}$ It doesn't depend upon the row or the column $i,j$!

>[!question]
>$A_{i,j}$ is Co factor of $a_{ij}$ then $\triangle$ is given by ?
>1. $a_{11}A_{31} + a_{12}A_{32}+ a_{13}A_33$
>2. $a_{11}A_{11} + a_{12}A_{21}+a_{13}A_31$
>3. $a_{21}A_{11}+ a_{22}A_{12} + a_{23}A_13$
>4. $a_{11}A_{11} + a_{21}A_{21} + a_{31}A_{31}$
>>[!answer]-
>>4.

Continuing,

Let's analyze the statement $a_{22}C_{11} + a_{23}C_{12} + a_{21}C_{13}$

We can see the Co-factors are from the first row. We know that the Co-factors don't use element from their row

The above equation calculates the determinant of a matrix that looks like : ^868777

$\begin{vmatrix}a_{22} & a_{23} & a_{21} \\ a_{21} & a_{22}& a_{23} \\ a_{31} & a_{32} & a_{33} \end{vmatrix}$

If $x$ is multiplied by $C_{i,j}$ can be thought as it is replacing the calculating ${ij}^{th}$ element.


**So lets figure out** $a_{21}C_{11} + a_{22}C_{12} + a_{23}C_{13}$ represent

$\begin{vmatrix}a_{21} & a_{22} & a_{23} \\ a_{21} & a_{22}& a_{23} \\ a_{31} & a_{32} & a_{33} \end{vmatrix}$

**AND WE KNOW THIS MATRIX IS  0**

**Multiplying a row with the Co-factor of another row results in 0** (you can change row to column  and say the same).

# Towards Inverses

## Adjoint

Lets find the product of 
(i)
$\overbrace{\begin{vmatrix}a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22}& a_{23} \\ a_{31} & a_{32} & a_{33} \end{vmatrix}}^{A}\overbrace{\begin{vmatrix}C_{11} & C_{21} & C_{31} \\ C_{12} & C_{22} & C_{32} \\ C_{13} & C_{23} & C_{33}\end{vmatrix}}^{B} = \begin{vmatrix}\det(A) & 0 & 0 \\ 0 & \det(A) & 0 \\ 0 & 0 & \det(A)\end{vmatrix} = \vert A \vert I$

Now (ii)
$\overbrace{\begin{vmatrix}C_{11} & C_{21} & C_{31} \\ C_{12} & C_{22} & C_{32} \\ C_{13} & C_{23} & C_{33}\end{vmatrix}}^{B}  \overbrace{\begin{vmatrix}a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22}& a_{23} \\ a_{31} & a_{32} & a_{33} \end{vmatrix}}^{A}= \begin{vmatrix}\det(A) & 0 & 0 \\ 0 & \det(A) & 0 \\ 0 & 0 & \det(A)\end{vmatrix} = \vert A \vert I$

In (i),

$A\cdot B = |A|I$ 
In (ii)

$B\cdot A = |A|I$ 

We see that multiplying $B$ results in Identity matrix

$\displaylines{\begin{align*}A^{-1} &= \frac{1}{|A|}\overbrace{\begin{vmatrix}C_{11} & C_{21} & C_{31} \\ C_{12} & C_{22} & C_{32} \\ C_{13} & C_{23} & C_{33}\end{vmatrix}}^{B} \\ &= \frac{1}{|A|}C^{T}\end{align*}}$

This $C^{T}$ is known as the *adjoint matrix* 

>[!note]
>Completion of determinant properties

# Cramer's Rule

>[!question]
How do we find the third column of $A^{-1}$ ?
>>[!answer]-
>$A \cdot x = \begin{bmatrix} 0 \\ 0 \\ 1\end{bmatrix}$ 
>$x = A^{-1}\begin{bmatrix} 0 \\ 0 \\ 1\end{bmatrix}$


$$
\displaylines{
Ax = b \\ 
\text{Pre-multiplying } A^{-1} \text{ on both the sides} \\
x = A^{-1}b \\ 
x = \frac{1}{|A|}C^{T} b\\
\begin{bmatrix}x_{1}\\ x_{2}\\ x_{3}\end{bmatrix} = \frac{1}{|A|}\begin{bmatrix}C_{11} & C_{21} & C_{31} \\ C_{12} & C_{22} & C_{32} \\ C_{13} & C_{23} & C_{33}\end{bmatrix}\begin{bmatrix}b_{1}\\b_{2}\\ b_{3}\end{bmatrix}\\ \\
\text{What we think about } x_{1}? \text{ How would it be calculated?} 
 \\
x_{1} = C_{11}b_{1} + C_{21}b_{2} + C_{31}b_{3}
}
$$

We know about it from [[Determinant#^868777|above section]] 

Figure it out