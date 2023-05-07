# Humble Beginnings

$\begin{bmatrix} 1 \\ 2 \\ 3 \end{bmatrix} \in \mathbb{R}^{3}$  the power $3$ denotes the number of rows in the vector.

In general,

$\begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix} \in \mathbb{R}^n$


# Linearly Dependent vectors

- This concept always applies to a set of vectors.
	- It doesn't make sense to ask if a single vector or a vector within a set is independent.

$\begin{Bmatrix} \overbrace{\begin{bmatrix} 1 \\ 2 \\ 3\end{bmatrix}}^u & \overbrace{\begin{bmatrix} 2 \\ 4 \\ 6\end{bmatrix}}^v & \overbrace{\begin{bmatrix} 3 \\ 6 \\ 9\end{bmatrix}}^w \end{Bmatrix}$ Is this a set of linearly dependent vectors?

Yes, because $w = u + v, u = \frac{1}{2}v, v  =2u$ 

What about

$\begin{Bmatrix} \overbrace{\begin{bmatrix} 1 \\ 2 \\ 3\end{bmatrix}}^u & \overbrace{\begin{bmatrix} 2 \\ 4 \\ 6\end{bmatrix}}^v & \overbrace{\begin{bmatrix} 3 \\ 6 \\ 10\end{bmatrix}}^w \end{Bmatrix}$ now?

>[!answer]-
>yes
