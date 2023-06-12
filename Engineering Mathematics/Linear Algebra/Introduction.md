 
# Humble Beginnings

$\begin{bmatrix} 1 \\ 2 \\ 3 \end{bmatrix} \in \mathbb{R}^{3}$  the power $3$ denotes the number of rows in the vector.

In general,

$\begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix} \in \mathbb{R}^n$


 $A_{3 \times 4}$  has three rows and four columns.

$A_{m \times n} \times B_{p \times q}$ 

What would be the conditions for this matrix multiplication to be valid, and what dimensions would the resulting matrix be?

1. $n = p$ 
2. $AB_{m\times q}$ 

# Linearly Dependent vectors

- This concept always applies to a set of vectors.
	- It doesn't make sense to ask if a single vector or a vector within a set is independent.

$\begin{Bmatrix} \overbrace{\begin{bmatrix} 1 \\ 2 \\ 3\end{bmatrix}}^u & \overbrace{\begin{bmatrix} 2 \\ 4 \\ 6\end{bmatrix}}^v & \overbrace{\begin{bmatrix} 3 \\ 6 \\ 9\end{bmatrix}}^w \end{Bmatrix}$ Is this a set of linearly dependent vectors?

Yes, because $w = u + v, u = \frac{1}{2}v + 0w, v  =2u+0w$ 

What about

$\begin{Bmatrix} \overbrace{\begin{bmatrix} 1 \\ 2 \\ 3\end{bmatrix}}^u & \overbrace{\begin{bmatrix} 2 \\ 4 \\ 6\end{bmatrix}}^v & \overbrace{\begin{bmatrix} 3 \\ 6 \\ 10\end{bmatrix}}^w \end{Bmatrix}$ now?

>[!answer]-
>Yes, we need only one vector.
>$-v + 2u + 0w = 0$


## Definition

If we can represent at least one vector as a linear combination of other vector then the set is Linearly dependent.

We need only ONE vector, they maybe multiple but we need only ONE.

### Formal

$\exists\, v_{1}$ such that
$$v_{1} = c_{2}v_{2} +c_{3}v_{3}+\cdots + c_nv_{n}$$

OR

$$k_{1}v_{1} + k_{2}v_{2} +k_{3}v_{3}+\cdots + k_nv_{n} = 0$$
Has a solution in which all $k_i$ are not 0.

## Null Vector

$\begin{Bmatrix}\overbrace{\begin{pmatrix}1 \\ 2 \\ 3\end{pmatrix}}^{u} & \overbrace{\begin{pmatrix} 2\\ 4 \\ 5\end{pmatrix}}^{v} & \overbrace{\begin{pmatrix}0 \\ 0\\ 0\end{pmatrix}}^{w}\end{Bmatrix}$

$-w + 0u + 0v = 0$

## Questions

>[!question]
>If a set of vectors are Linearly dependent then
>
>1) There is at least ONE vector which can be represented by a linear combination of other vectors
>>[!answer]-
>>Yes that's the definition 
>2) All vectors can be represented by linear combination of other vectors
>>[!answer]-
>>False, it is not necessary that every vector can be represented by the linear combination of other vectors

>[!question]
>Let $u_{i}'s$ be vector in $R^n$ for i $\in \mathbb{N}$
>Which of the following are correct
>i) If $\{u_1,u_2,u_3\}$ is linearly dependent so is $\{u_1,u_2\}$
>ii) If $u_4$ is not linear combination of $\{u_1,u_2,u_3\}$, then $\{u_1,u_2,u_{3}, u_4\}$ is linearly independent.
> iii) Any set containing the zero vector is linearly dependent.
> iv) If  $\{u_1,u_2,u_3\}$ is linearly dependent so is $\{u_1,u_{2}, u_{3},u_4\}$
>>[!answer]-
>>i) It may be the case $u_{2}= 2u_1$
>>ii) False, $u_{2}= 2u_1$
>>iii) True
>>iv) True, the superset would be Linearly dependent.

# Linear Independence
If we can obtain zero vector only by trivial linear combination of other vectors. 
i.e
$$c_{1}v_{1} + c_{2}v_{2} +c_{3}v_{3}+\cdots + c_nv_{n} = 0 \iff c_{i}= 0 \, \forall \, i$$


>[!Question]
>Can we have more than two linearly independent vector in $\mathbb{R}^2$  
>>[!answer]-
>>No.

$\{a,b\}$ are linearly independent, then the question asks if $\exists$ a $c$ , $\{a,b,c\}$ is linearly independent. 

Checking,
$\begin{Bmatrix}\overbrace{\begin{pmatrix}1 \\ 2\end{pmatrix}}^{v_1}&\overbrace{\begin{pmatrix}2 \\5\end{pmatrix}}^{v_2}&\overbrace{ \begin{pmatrix}5 \\3\end{pmatrix}}^{v_3}\end{Bmatrix}$

## Vector Space

- Set of vectors maybe added together and multiplied with scalars.

If with a set of vectors we can get any vector in that space then that vector is said to span the space.

>[!example]
>$\begin{Bmatrix}\begin{pmatrix}0 \\ 1\end{pmatrix} & \begin{pmatrix}1 \\ 0\end{pmatrix}\end{Bmatrix}$ spans $\mathbb{R}^2$

Any two linearly Independent vectors span $\mathbb{R}^2$

>[!question]
>Does the vector below span $\mathbb{R}^2$
>$\begin{Bmatrix}\begin{pmatrix}0 \\ 1\end{pmatrix} & \begin{pmatrix}1 \\ 0\end{pmatrix} & \begin{pmatrix} 3 \\ 5\end{pmatrix}\end{Bmatrix}$ ?
>
>>[!answer]-
>>Yes, we can just set the  coefficient of $\begin{pmatrix} 3 \\ 5\end{pmatrix}$ to 0


If the set contains more than 2 vectors and it at least 2 linear independent vectors in the set $\mathbb{R}^2$ then the sets spans $\mathbb{R}^2$ 

>[!question]
>Can we have more than 3 independent vectors in $\mathbb{R}^3$?
>>[!answer]-
>>No we cannot, the $4^th$ vector has to be a linear combination. Because three linear independent vectors would span $\mathbb{R}^3$

>[!question]
>Can we have more than n independent vectors in $\mathbb{R}^n$?
>>[!answer]-
>>No we cannot, the $(n+1)^th$ vector has to be a linear combination. Because three linear independent vectors would span $\mathbb{R}^n$

>[!question]
>Determine which of the following pair of vectors are Linearly independent
>
>i)$\begin{pmatrix}-1 \\ 2\end{pmatrix} \begin{pmatrix}3 \\ -6\end{pmatrix}$ 
>ii) $\begin{pmatrix}2 \\ -1\end{pmatrix} \begin{pmatrix}3 \\ 4\end{pmatrix}$
 iii) $\begin{pmatrix}-1 \\ 1\end{pmatrix} \begin{pmatrix}1 \\-1\end{pmatrix}$ 
 iv) $\begin{Bmatrix}\begin{pmatrix}11 \\ -1 \\ 3\end{pmatrix} & \begin{pmatrix}0 \\ 5 \\ 5 \end{pmatrix} & \begin{pmatrix}0 \\ 1 \\ 0 \end{pmatrix}& \begin{pmatrix} 2 \\ 0 \\ 1\end{pmatrix}\end{Bmatrix}$ ?
 >>[!answer]-
 >>i) False $v = -3u$
 >>ii) True, note that in $\mathbb{R}^2$ the dependency would mean the other vector has to be scalar multiple.
 >>iii) False 
 >>iv) False, As it is in $\mathbb{R}^3$, no more than 3 vectors in the set can independent
 
 
>[!question]
>Can two vectors span $\mathbb{R}^3$ ?
>>[!answer]-
>>No. The linear combination would result in only in a 2D plane.


>[!question]
> If A is a $3\times 5$ matrix, are the columns of the matrix linearly independent or dependent?
> >[!answer]-
>> We have 5 vectors of 3 dimensions, hence Linearly dependent.

>[!question]
>In a set $\{v_{1}, v_{2}, v_{3}, \cdots , v_{p}\} \text{ in } \mathbb{R}^n$  is linearly dependent if $p>n$ True of False?
>>[!answer]-
>>True. For reasons check above.

>[!question]
>In a set $\{v_{1}, v_{2}, v_{3}, \cdots , v_{p}\} \text{ in } \mathbb{R}^n$  is linearly dependent, contains a zero vector, irrespective of p's relation with n True of False?
>>[!answer]-
>>True.

>[!question]
>Which is sufficient to fill $\mathbb{R}^6$
>1) 6 L.D vector
>2) 5 L.I vector
>3) Any 7 vectors
>4) 6 L.I vector
>>[!answer]-
>>4th fills $\mathbb{R}^6$

