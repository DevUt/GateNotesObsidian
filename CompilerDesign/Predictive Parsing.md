- Top down parser that looks at next few tokens
- Efficient: No backtracking required, parsing done in $O(n)$ time

Predictive parsing $LL(K)$ grammar

L -> Left to right
L -> Left most derivation
k -> Prediction is based upon k tokens of look ahead


$S \rightarrow aa | bc$
Input string: bc
$LL(1)$ can decide

$S \rightarrow ab | ac$
input string : aab
$LL(1)$ cannot decide


## Constructing a parsing table

For CFG $G$ 

- For each production $A \rightarrow \alpha$ in $G$ do
	- for each terminal $t$ $\epsilon\; \text{First}(\alpha)$ do
		- T[A,t] = A $\rightarrow \; \alpha$
		- if $\epsilon \in \text{First}(\alpha)$ for each $t\in \text{Follow}(A)$ do
			- T[A,T] = $A \rightarrow \alpha$


Q
$S \rightarrow aS | bS| c$

|     | a                 | b                 | c                 | $   |
|:--- |:----------------- |:----------------- |:----------------- | --- |
| S   | $S\rightarrow aS$ | $S\rightarrow bS$ | $S \rightarrow c$ |     | 


We inspect rule by rule 
so for 

$S \rightarrow aS$ we compute the $First(aS)$ 
$First(aS) = \{a\}$

For $S \rightarrow bS$
we would compute $First(bS) = \{b\}$ 

For $S \rightarrow c$
we would compute $First(c) = \{c\}$

> How we make use of this parsing table?

Input string abac

![[Predictive Parsing 2023-04-12 00.04.22.excalidraw]]

Q
$S \rightarrow \underbrace{SAa}_1 | \underbrace{\epsilon}_2$
$A \rightarrow \underbrace{Sb}_3 | \underbrace{Ac}_4 | \underbrace{\epsilon}_5$

|     | a     | b   | c   | $   |
|:--- |:----- |:--- |:--- |:--- |
| S   | 1,2   | 1,2 | 1,2 | 2   |
| A   | 3,4,5 | 3,4 | 3,4,5 |     |

For  rule 1,

$First(SAa) = \{a,b,c\}$
$First(S) = \{\epsilon,a,b,c\}$
$First(A) = \{a,b,c,\epsilon\}$

For rule 2,

$First(\epsilon) = {\epsilon}$
Now we have to consider the $Follow(S)$

$Follow(S) = \{b,\$, a,c\}$

For rule 3,

$First(Sb) = \{b, a,c\}$

For rule 4,
$First(Ac) = \{a,b,c\}$

For rule 5,
$First(\epsilon) = {\epsilon}$

$Follow(A) = \{a,c\}$

*When there are multiple entries in a cell it is known as a conflict*

*Whenever there is a conflict the grammar is not LL(1)*

Now we can say that this grammar is not $LL(1)$ grammar


Q

$E \rightarrow TX$
$T \rightarrow (E) | int Y$
$X \rightarrow +E | \epsilon$
$Y \rightarrow *T | \epsilon$


|     | int | (   | +   | *   | )   | $   |
|:--- |:--- |:--- |:--- |:--- |:--- |:--- |
| E   | 1   | 1   |     |     |     |     |
| T   | 3   | 2   |     |     |     |     |
| X   |     |     | 4   |     | 5   | 5   |
| Y   |     |     | 7   | 6   | 7    | 7   |


$First(E) = \{(,int\}$
$First(T) = \{(,int\}$
$First(X) = \{\epsilon, +\}$
$First(Y) = \{\epsilon, *\}$


$Follow(E) = \{\$,)\}$
$Follow(T) = \{\$,),+\}$
$Follow(X) = \{\$,)\}$
$Follow(Y) = \{\$, ) , +\}$


Q
$A \rightarrow BC | Ac$
$B \rightarrow a | \epsilon$
$C \rightarrow b | \epsilon$

|     | a   | b   | c   | $   |
|:--- |:--- |:--- |:--- |:--- |
| A   | 1,2 | 1,2 | 1,2 | 1   |
| B   | 3   | 4   | 4   | 4   |
| C   |     | 5   | 6   | 6   |

$First(A) = \{\epsilon,a,b,c \}$
$First(B) = \{\epsilon, a \}$ 
$First(C) = \{\epsilon, b \}$ 

$Follow(A) = \{c,\$\}$
$Follow(B) = \{b,c,\$\}$
$Follow(C) = \{c,\$\}$


Q
$E \rightarrow int | (\,E \,Op \,E\,)$
$Op \rightarrow +  | *$

|     | int | (   | +   | *   | )   | $   |
|:--- |:--- |:--- |:--- |:--- |:--- |:--- |
| E   | 1   | 2   |     |     |     |     |
| Op  |     |     | 3   | 4   |     |     |



$FIRST(E) = \{int, (\}$
$FIRST(Op) = \{+,*\}$

$\text{Follow}(E) = \{\$, FIRST(OpE)), )\}$ = $\{\$, +,*, )\}$
$\text{Follow}(Op) = \{FIRST(E))\} = \{FIRST(E) \} = \{\text{int},( \}$ 


A grammar is $LL(1)$ iff

$A \rightarrow \alpha_1 | \alpha_2 | \alpha_3$
1. $\text{First}(\alpha_i) \cap  \text{First}(\alpha_j) = \phi$
2. If $\alpha_1 \rightarrow ^{*} \epsilon$ then
	1.  $\text{Follow}(A) \cap \text{First}(\alpha_2) = \phi$
	2. $\text{Follow}(A) \cap \text{First}(\alpha_3) = \phi$

> Can Left recursive grammar be $LL(1)$ ?

NO!
$A \rightarrow Ac | a$

$First(Ac) = \{a\}$
$First(a) = \{a\}$

> Non left factored grammar cannot be $LL(1)$

$A \rightarrow \alpha \beta_1\,|\, \alpha \beta_2$
$First(\alpha)$ would be common hence conflict

> Can ambiguous grammar be $LL(1)$

NO!

We always keep on doing Left most derivation 

For ambiguous grammar we have more than one left most derivation


![[Predictive Parsing 2023-04-12 01.28.15.excalidraw]]
at this point there is conflict


> There may be a grammar that is
> Unambiguous
> Left factored
> Non left recursive
> 
> But still not $LL(1)$

