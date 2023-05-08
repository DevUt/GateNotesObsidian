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


