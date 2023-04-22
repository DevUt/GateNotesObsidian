#regular-language
# Definition
Language is **#regular** if some [[Theory of Computation/Introduction#Definite Finite Automata |Definite Finite Automata]] exists that accepts the string.

### Examples
For the ![[Drawing 2023-03-22 00.25.34.excalidraw]] we saw it in [[Theory of Computation/Introduction |Introduction]] 
$L(M) = \{w \, | \,w\,\text{contains sub-string 11}\} = A$

As we can see that $M$ exist which accepts $A$
$\therefore \, A \, \text{is regular}$  

$B \, = \, \{w \,| \, \text{has even number of }1's \}$  is Regular 
$C = \{w \,| \, \text{has equal number of } 0's\,\text{and}\, 1's \}$ is *NOT* regular
$D = \{ w \, | \, \text{w is a string that has 001 as a substring} \}$ is Regular

P.S $C$ is #DCFL.

----- 

# Regular Expressions


1. $\phi,\,\Sigma$ are primitive regular expression

$R  = a$
![[Regular Languages 2023-04-23 00.45.02.excalidraw]]

$R = \epsilon$
![[Regular Languages 2023-04-23 00.46.10.excalidraw]]

$R = \phi$

![[Regular Languages 2023-04-23 00.47.26.excalidraw]]

If $R$ is composite

$$
	\text{Use Closure properties}\left\{
    \begin{array}{ll}
        R_1 \cup R_2 \\
        R_1 \cdot R_2 \\
        R_1^{*}
    \end{array}
\right.$$

$(a \cup a \cdot b)^*$

Closure properties

![[Regular Languages 2023-04-23 00.53.15.excalidraw]]