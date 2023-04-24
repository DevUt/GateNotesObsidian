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

Examples

1) $0^*10^*$ Contains only single 1 and any number of 0
2) $\Sigma^*1 \Sigma^*$  Contains at least single 1 and any other number of other alphabet
3) $1^*(01^+)^*$ Any number of 1 followed by any number of (0 followed by atleast a single 1
4) $(\Sigma\Sigma)^*$  Even length strings
5) $(\Sigma\Sigma\Sigma)^*$  Multiple of three
6) $A \cdot \emptyset = \emptyset$  
$A \cdot B = \{ab, a \in A \text{ and } b \in B\}$ 

7) $r = (a+b)^*(a+bb)$ $L(r) = \{a, bb, aa, ba, abb, bbb,\cdots\}$
8) $L(r) = \{w \in \Sigma^* : \: w \: \text{has at least one pair of consecutive zeros} \}$ 
8) $L(r) = \{w \in \Sigma^* : \: w \: \text{has no pair of consecutive zeros} \}$ 
9) What does $(\emptyset ^ *)^*$ represent? > $\{\epsilon\}$
10) what does $a\emptyset$ represent? $\emptyset$ 
11) Regex for string with even number of $a's$ followed by odd number of $b's$ $(aa)^*b(bb)^*$ 
$L(r) = \{a^{2n}b^{2m+1} \: : \: n \geq 0, m \geq 0\}$

12) 