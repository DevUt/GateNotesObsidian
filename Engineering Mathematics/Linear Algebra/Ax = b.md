# Matrix Multiplication

1) $\begin{bmatrix}2 & 4 \\ 3 & 5\end{bmatrix}$ $\begin{bmatrix}1 \\ 0\end{bmatrix}$ = $\begin{pmatrix}2 \\ 3\end{pmatrix}$
$1\begin{pmatrix}2 \\ 3\end{pmatrix} + 0 \begin{pmatrix}4 \\ 5\end{pmatrix}$
2) $\begin{pmatrix}4 & 7 \\ 6 & 0\end{pmatrix}\begin{pmatrix}1 \\ 2\end{pmatrix} = \begin{pmatrix}18 \\ 6\end{pmatrix}$ 

$1\begin{pmatrix}4 \\ 6\end{pmatrix} + 2 \begin{pmatrix}7 \\ 0\end{pmatrix}$


$\begin{pmatrix}a & b \\ c & d\end{pmatrix}\begin{pmatrix}e & f \\ g & h\end{pmatrix} = \begin{bmatrix}e\begin{pmatrix}a \\ c\end{pmatrix} + g\begin{pmatrix}b \\ d\end{pmatrix} & f\begin{pmatrix}a \\ c\end{pmatrix} + h\begin{pmatrix}b \\ d\end{pmatrix} \end{bmatrix}$ 


$Ax = b$

b is linear combination of the columns of A.
A is a $n \times n$ matrix 
x and b only have 1 column ^098c5f

>[!question]
>If $Ax = 0$ has some non trivial solution then columns of A are linearly dependent.
>True or false
>>[!answer]-
>>$\displaylines{\begin{align*} & \begin{bmatrix}a_{11} & a_{12} & \dots \\ \vdots & \ddots & \\  a_{n1} &        & a_{nn} \end{bmatrix} \begin{bmatrix}x_{0} \\ \vdots \\ x_{n}\end{bmatrix} \\ & x_{0}\begin{bmatrix}a_{11}\\ \vdots \\ a_{n1}\end{bmatrix} + x_{1}\begin{bmatrix}a_{12}\\ \vdots \\ a_{n2}\end{bmatrix} + \cdots = 0\end{align*}}$
>>As $x_{0}, \cdots , x_{n}$ are constants we can say that the columns of the matrix A  are linearly dependent

>[!question]
>$Ax = 0$ has some solution then what can you say about the linear dependence of columns of A?
>> [!answer]-
>> We cannot say, because the "some solution" maybe the trivial solution.


$\begin{pmatrix}k_{1} & k_{2} & k_{3} \\ p_{1} & p_{2} & p_{3}\end{pmatrix}_{2 \times 3} \begin{pmatrix}x_{1}\\ x_{2} \\ x_{3}\end{pmatrix}_{3 \times 1}=\begin{pmatrix}b_{1} \\ b_{2}\end{pmatrix}_{2 \times 1}$

$\displaylines{k_{1}x_{1}+k_{2}x_{2}+ k_{3}x_{3} &= b_{1}\\ p_{1}x_{1}+p_{2}x_{2}+p_{3}x_{3} &= b_{2} }$

Generalized
$\begin{pmatrix}a_{1} & a_{2} & a_{3} & \cdots &a_{n}\end{pmatrix}\begin{pmatrix}b_{1} & b_{2} & b_{3} & \cdots &b_{n}\end{pmatrix} = \begin{pmatrix}c_{1} & c_{2} & c_{3} & \cdots &c_{n}\end{pmatrix}$
$a_{1}$ and others are column vectors

$c_{1}= b_{1}a_{1}+ b_{1}a_{2}+  \cdots$
