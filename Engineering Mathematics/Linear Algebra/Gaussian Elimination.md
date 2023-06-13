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

>[!question]
>Which are basic variable and which are free variable in the following matrix
>$$
\left[\begin{array}{rrrrr|r}
   1 & 2 & 0 & -1 & -2 & 0 \\  0  & 1 & 1 & 0 & 3 & 0 \\ 0 & 0 & 0 & 1 & 1 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0
 \end{array}\right]
$$


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
>>
$$\left[\begin{array}{rrr|r}
   1 & 1 & -1 & 0  \\  1  & -1 & 1 & 2  \\ 2 & -1 & -1 & -3
 \end{array}\right]$$
 $$\displaylines{R_{3} \rightarrow R_{3}-2R_{1} \\ R_{2} \rightarrow R_{2} - R_{1}} \\  \left[\begin{array}{rrr|r}
   1 & 1 & -1 & 0  \\  0  & -2 & 2 & 2  \\ 0 & -3 & 1 & -3
 \end{array}\right]$$
  $$\displaylines{R_{3} \rightarrow -2R_{3}+3R_{1}  \left[\begin{array}{rrr|r}
   1 & 1 & -1 & 0  \\  0  & -2 & 2 & 2  \\ 0 & 0 & 4 & 12
 \end{array}\right]}$$
 $$\displaylines{4x_{3}= 12 \implies x_{3} = 3 \\ -2x_{2}+2x_{3} = 2 \implies x_{2} = 2 \\ x_{1}+x_{2}-x_{3}=0 \implies x_{1}=1}$$
>>


 >[!question]
 >$$\displaylines{\begin{align*} 5x_{1}- 11x_{2} &= -2 \\ -4x_{1}+9x_{2}&= 1 \\ x_{1}-2x_{2}&= -1\end{align*}}$$



>[!question]
>$$\displaylines{\begin{align*} x - 3y + z &= 4 \\ -x + 2y -5z &= 3 \\ 5x - 13y + 13z &= 8 \end{align*}}$$
>>[!answer]-
>>$$\displaylines{\left[\begin{array}{rrr|r}
>>   1 & -3 & 1 & 4  \\  0  & -1 & 4 & 7  \\ 0 & 0 & 0 & 2
>> \end{array}\right] \\ 0 = 2? \\ \text{This is the case of no solution}}$$ 

 
**A SYSTEM WHICH HAS NO SOLUTION IS KNOWN AS INCONSISTENT**
**A SYSTEM HAVING AT LEAST ONE SOLUTION IS KNOWN AS CONSISTENT**


![[Gaussian Elimination 2023-06-14 03.09.39.excalidraw]]