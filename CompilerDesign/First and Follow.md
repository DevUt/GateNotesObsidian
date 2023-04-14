
# First

- Set of terminals that can be at a start of the string for a variable
- Epsilon is allowed

$A \, \rightarrow \,aA \,|\, c$
$FIRST(A) \rightarrow \{a,c\}$


Q
$S \rightarrow aS | bA$
$A \rightarrow aS | dA | f$

$FIRST(S) = \{a,b\}$
$FIRST(A) = \{a,d,f\}$


Q

$S \rightarrow Ab | a$
$A \rightarrow aA | \epsilon$

$FIRST(S) = \{a,b\}$
$FIRST(A) = \{\epsilon, a\}$

Lets say there is production 

$A \rightarrow \alpha \beta$
$FIRST(A) = \{FIRST(\alpha \beta)\}$

First case 
if $\alpha$ is nullable

$\{FIRST(\alpha) - \epsilon\}\, \cup \, FIRST(\beta)$

if $\alpha$ is not  nullable
just $FIRST(\alpha)$

Q

$S \rightarrow a | bA$
$A \rightarrow AB | a | \epsilon$
$B \rightarrow c | d | e | f$

$FIRST(S) = \{a,b\}$
$FIRST(A) = \{a,FIRST(AB),\epsilon\}$
$FIRST(B) = \{c,d,e,f\}$

$FIRST(AB) = \{FIRST(A)-\epsilon \cup FIRST(B)\}$

Q

$S \rightarrow ab | ABSd | BC$
$A \rightarrow eS | Se | \epsilon$
$B \rightarrow dS | Sd | \epsilon$
$C \rightarrow AB | Sf | \epsilon$

$FIRST(S) = \{\epsilon, a, FIRST(ABSd), FIRST(BC)\}$
$FIRST(A) = \{\epsilon, e, FIRST(S)\}$
$FIRST(B) = \{\epsilon,  d, FIRST(S)\}$
$FIRST(C) = \{\epsilon, FIRST(AB), FIRST(S)\}$

$FIRST(S) = \{\epsilon,a,FIRST(A),FIRST(B),d,FIRST(C)\}$
...

Everything is $\{\epsilon,a,e,d,f\}$


Q
$E \rightarrow int$
$E \rightarrow (E\; Op\; E)$
$Op \rightarrow +$
$Op \rightarrow *$

$FIRST(E) = \{int, (\}$
$FIRST(Op) = \{+,*\}$

# Follow

The follow set represents the set of terminals that might come after a given non terminal


$\text{Follow}(A)= \{t \; | \; S =>^{*} \alpha A t \beta \text{  for some }\alpha \, \beta\}$

- $\text{Follow}(S) \text{ contains } \$$
- Epsilon is not in follow

Q
$S \rightarrow Sa | Sb | \epsilon$

$\text{Follow}(S) = \{a,b,\$\}$

Q
$E \rightarrow int$
$E \rightarrow (E\; Op\; E)$
$Op \rightarrow +$
$Op \rightarrow *$

$\text{Follow}(E) = \{\$, FIRST(OpE)), )\}$ = $\{\$, +,*, ))\}$
$\text{Follow}(Op) = \{FIRST(E))\} = \{FIRST(E) \} = \{\text{int},( \}$ 

Q
$P \rightarrow ABC$

$\text{Follow(B)} = FIRST(C)$

What if C is nullable?
![[First and Follow 2023-04-11 00.51.41.excalidraw]]

$\text{Follow(B)} = \{FIRST(C),Follow(P)\}$

General Rule

$A \rightarrow B_1 B_2 B_3 \cdots B_k$
$\text{Follow}(B_1) = \{First(B_2B_3B_4\cdots B_k)\}$

If $B_2$ is nullable

$\text{Follow}(B_1) = \{First(B_2), \text{First}(B_3B_4\cdots B_k)\}$

in end if all are nullable


$\text{Follow}(B_1) = \{First(B_2), First(B_3), \cdots, \text{Follow}(A)\}$
![[First and Follow 2023-04-11 23.21.49.excalidraw]]


![[First and Follow 2023-04-11 01.03.50.excalidraw]]


Q

$S \rightarrow aS | SAb | BC$
$A \rightarrow AS | a | \epsilon$
$B \rightarrow BA | AB | \epsilon$
$C \rightarrow e | \epsilon$

$FIRST(S) = \{\epsilon, a,b,e\}$
$FIRST(A) = \{\epsilon, a,b,e\}$
$FIRST(B) = \{\epsilon, a,b,e\}$
$FIRST(C) = \{\epsilon, e\}$

$Follow(S) = \{\$, FIRST(Ab), Follow(A)\}$
$Follow(A) = \{b,FIRST(S), FIRST(B), Follow(B)\}$
$Follow(B) = \{FIRST(C), FIRST(A), Follow(S)\}$
$Follow(C) = \{Follow(S)\}$

Q
$E \rightarrow TX$
$T \rightarrow (E) | int\,Y$
$X \rightarrow +E | \epsilon$
$Y \rightarrow * T| \epsilon$

$FIRST(E) = \{(, int\}$
$FIRST(T) = \{(,int\}$
$FIRST(X) = \{\epsilon,+\}$
$FIRST(Y) = \{\epsilon, *\}$

$Follow(E) = \{), \$\}$
$Follow(T) = \{+,),\$\}$
$Follow(X) = \{), \$\}$
$Follow(Y) = \{+,),\$\}$


Q
$E \rightarrow T E^{'}$
$E^{'} \rightarrow  +TE{'} | \epsilon$
$T \rightarrow FT^{'} | \epsilon$
$T^{'} \rightarrow *FT^{'} | \epsilon$
$F \rightarrow (E) |  id$

$FIRST(E) = \{\epsilon,(,id,+\}$
$FIRST(E^{'}) = \{\epsilon, +\}$
$FIRST(T^{'}) = \{*,\epsilon\}$
$FIRST(T) = \{\epsilon, (,id\}$
$FIRST(F) = \{(, id\}$

$Follow(E) = \{),\$\}$
$Follow(E^{'}) = \{),\$\}$
$Follow(T^{'}) = \{+,),\$\}$
$Follow(T) = \{+, ) , \$ \}$
$Follow(F) = \{*,+, ),\$\}$
