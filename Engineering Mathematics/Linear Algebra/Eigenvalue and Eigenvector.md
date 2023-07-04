<iframe width="560" height="315" src="https://www.youtube.com/embed/PFDu9oVAE-g" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

Taking the above video as reference. We see that when we see something like $Ax$ it can be thought as if $A$ is transforming every vector in space.

*Eigenvector corresponding to a matrix is the vector which only scales after transformation*


![[Eigenvalue and Eigenvector 2023-07-04 15.03.10.excalidraw]]


Eigenvectors only make sense for transformation matrices which are square.
$A_{m \times n}x_{n \times 1} = \lambda x'_{m \times 1}$  we can see that $x$ and $x'$ are in different dimensions. Hence the concept of eigenvector doesn't hold here.

>[!question]
>How many eigenvector exist for identity matrix?
>>[!answer]-
>>Infinite.
>>Every vector remains same, that's scaling the vector by 1.


>[!question]
>How many linearly independent eigenvector for $n \times n$ identity matrix?
>>[!answer]-
>>n. There can be at max n linearly independent vectors in that space.

>[!question]
>Suppose x is eigenvector of $A$ then $kx$ is also eigenvector of $A$
>>[!answer]-
>>Yes. We can see it both visually and through equations.
>>Visually.
>>![[Eigenvalue and Eigenvector 2023-07-04 15.22.03.excalidraw]]
>>Through equation
>>$\displaylines{\begin{align*} Ax &= \lambda x \\ Akx &= kAx \\ Ax &= \lambda x \\ Akx &= k\lambda x = \lambda (kx) \end{align*}}$

$\displaylines{\begin{align*} Ax &= \lambda x \\ Ax - \lambda x &= 0 \\ (A - \lambda I)x &= 0 \end{align*}}$ 

The above equation is characteristic equation.

Let's consider $A - \lambda I$ as $B$ 
$Bx = 0$ 

as $x$ is nonzero.

[[Ax = b#^098c5f|Remember that in Ax = b, b is the linear combination of columns of A and the elements in x are the coefficients]]. 

So here we can say that there is a linear combination of columns of $B$ such that the sum is $0$. So we can [[Engineering Mathematics/Linear Algebra/Introduction#Linearly Dependent vectors#|say that the columns are linearly dependent. ]] 

>[!Property]
>When columns are linearly dependent the determinant is 0.
>>[!answer]-
>>When reduced to row echelon form there would be at least one $0$ row. We know that the determinant of row  echelon form matrix is the product of the diagonal, as one row is 0. determinant would be 0. 
>>
>>You can also think about it determinant being area, if one of the col is linearly dependent it can't span the whole space, hence 0 determinant.
>>


So the $\det(B)$ is $0$ 
$\det(A - \lambda I) = 0$  

>[!Question]
>Find the eigenvalue and eigenvector
>$\begin{pmatrix}1 & 2 \\ 2 & 1\end{pmatrix}$ 
>>[!answer]-
>>$\begin{vmatrix}1 - \lambda & 2 \\ 2 & 1-\lambda \end{vmatrix} =0$
>>$(1- \lambda)^{2}-4 =0$
>>$\lambda = 3, \lambda = -1$
>>
>>
>>For $\lambda = 3$
>>
>>$\left[\begin{array}{rr|r} -2 & 2 & 0 \\ 2 & -2 & 0\end{array}\right]$
>>$R_{2} \rightarrow R_{2} + R_{1}$
>>$\left[\begin{array}{rr|r} -2 & 2 & 0 \\ 0 & -0 & 0\end{array}\right]$
>>The second column is the free variable (We would refer this afterwards).
>>$\displaylines{\begin{align*} x_{2} &= k \\ -2x_{1} + 2x_{2}&= 0\\ x_{1}&= k \\ x &= k \begin{pmatrix} 1 \\ 1 \end{pmatrix}\end{align*}}$
>>
>>
>>For  $\lambda  = -1$
>>$\left[\begin{array}{rr|r} 2 & 2 & 0 \\ 2 & 2 & 0\end{array}\right]$
>>$R_{2} \rightarrow R_{2} - R_{1}$
>>$\left[\begin{array}{rr|r} 2 & 2 & 0 \\ 0 & 0 & 0\end{array}\right]$
>>$\displaylines{\begin{align*} x_{2} &= k \\ 2x_{1} + 2x_{2}&= 0\\ x_{1}&= -k \\ x &= k \begin{pmatrix} -1 \\ 1 \end{pmatrix}\end{align*}}$
>

We see that we have a free variable. 

Is it necessary to have a free variable? Let's explore visually first.

![[Eigenvalue and Eigenvector 2023-07-04 23.42.08.excalidraw]]

Hence the solution, should contain infinite vectors. 

Now lets also look at it logically,

$(A - \lambda I)x = 0$  We saw that the columns must be linearly dependent in $A - \lambda I$ hence the $\text{rank} < n$ (n is the dimension). 

>[!question]
>Find eigenvalue and eigenvector 
>$\begin{bmatrix}9 & 0 & -8 \\ 15 & 3 & -15 \\ 0 & 0 & 1 \end{bmatrix}$

**MUST REMEMBER PROPERTY**
>[!Property]
>Eigenvector from different eigenvalue are linearly independent. 

We can easily prove it but alas I'm not in mood.

>[!question]
>Find eigenvector and eigenvalue 
>$\begin{bmatrix}3 & -2 \\ 1 & 0\end{bmatrix}$

>[!question]
>Find eigenvalue and eigenvector
>$\begin{bmatrix}3 & 1 \\ 0 & 3\end{bmatrix}$
>>[!answer]-
>>$\begin{vmatrix}3 - \lambda & 1  \\ 0 & 3 - \lambda \end{vmatrix} = 0$
>>$(3 - \lambda)^{2} = 0$
>>$\lambda = 3,3$
>>$\left[\begin{array}{rr|r} 0 & 1 & 0 \\ 0 & 0 & 0\end{array}\right]$
>>$x_{1} =k$
>>$x2 = 0$
>>$x = k\begin{bmatrix}1 \\ 0\end{bmatrix}$
>>**NOW NOTICE WE GET REPEATING EIGENVALUE,  BUT EIGENVECTOR is only ONE**
>

>[!question]
>Find eigenvalue and eigenvector.
>$\begin{bmatrix}5 & -1 & 0 \\ -1 & 5 & 0 \\ \frac{1}{3} & \frac{-1}{3} & 4\end{bmatrix}$
>>[!answer]-
>>We get $\lambda = 6,4,4$
>>
>>For $\lambda = 6$
>>$\left[\begin{array}{rrr|r} -1 & -1  & 0 & 0 \\ -1 & -1 & 0 & 0 \\ \frac{1}{3} & \frac{-1}{3} & -2 & 0 \end{array}\right]$
>>$\left[\begin{array}{rrr|r} -1 & -1  & 0 & 0 \\ 0 & -2 & 6 & 0 \\ 0 & 0 & 0 & 0 \end{array}\right]$
>>$\displaylines{\begin{align*}x_{3} &= k \\ -2x_{2} - 6x_{3} &= 0 \\ x_{2} &= -3k \\ x_{1} &= 3k \\ x &= k\begin{bmatrix}3 \\ -3 \\ 1 \end{bmatrix}  \end{align*}}$
>>
>>For $\lambda = 4$
>> $\left[\begin{array}{rrr|r} 1 & -1 & 0 & 0 \\ 0 & 0 & 0 & 0 \\ 1 & -1 & 0 & 0\end{array}\right]$
>> $\left[\begin{array}{rrr|r} 1 & -1 & 0 & 0 \\ 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0\end{array}\right]$ 
>> $x_{2} = s , x_{3}= t$
>> $x_{1}- s = 0$
>> $x = \begin{bmatrix}s \\ s \\ t\end{bmatrix}$
>> $x = s\begin{bmatrix} 1 \\ 1 \\ 0 \end{bmatrix} + t\begin{bmatrix}0 \\ 0 \\ 1\end{bmatrix}$
>> **Now here we see that for repeating eigenvalues we had TWO eigenvector**
>> 

Now if we see above two question there are two situations that arise :
1. Repeating eigenvalue but number of eigenvectors is less than the power of eigenvalue.
2. Repeating eigenvalue but eigenvectors are equal to the power of eigenvalues.

We can have multiple linearly independent for same $\lambda$ 

>[!question]
>For $(\lambda -1)^{2}(\lambda - 5)(\lambda - 7)^{3} = 0$
>What are the possible number of linearly independent eigenvectors
>1. at least 6
>2. at most 6
>3. exactly 6
>4. at least 3
>>[!answer]
>>For each of the eigenvalue we should have different eigenvector which are linearly independent. Hence at least 3 eigenvectors.
>>
>>But if each of the lambda have linearly independent eigenvectors for each power, then we would have $2 + 1 + 3 = 6$ eigenvectors, no more than that. Hence at most 6. 

In general 
$(\lambda - \lambda_{1})^m_{1}(\lambda - \lambda_{2})^{m_{2}}\ldots (\lambda - \lambda_{k})^{m_{k}}$
$m_{1} + m_{2} + \cdots + m_{k} = n$

We would have
1. atleast $k$ eigenvectors.
2. at most $n$ eigenvectors

>[!question]
>$A_{20 \times 20}$ we solve following homogeneous equation $(A - \lambda I)x = 0$ for $\lambda = 3$ and we found out that there are $7$ free variables then corresponding to $\lambda = 3$ how many linearly independent eigenvectors?
>>[!answer]-
>>$7$ free variables = $7$ linearly independent vectors in solution.
>
>What could be the power of $\lambda = 3$ in the characteristic equation
>A. 3
>B. 7
>C. 4
>D. 20
>>[!answer]-
>>The power would be at least 7 as it would have 7 independent eigenvectors. At most the power could be at most 7
>
>

