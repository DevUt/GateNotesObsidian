
# Closure Property

$\text{If a and b} \in \mathbb{N} \text{ would a + b} \in \mathbb{N}$ ?
Yes!

$\text{If a and b} \in \mathbb{N} \text{ would a - b} \in \mathbb{N}$?
No! Because a=2 b=5

$\forall a,b \in A \implies a*b \in A$   then we can say $A$ is closed under $*$


# Union
$\displaylines{A = \{a,b,c,d\} \\ B = \{e,f,g,h\}}$

$A \cup B = \{a,b,c,d,e,f,g,h\}$

When we talk about union of two DFA, we usually mean $L(DFA_1) \cup L(DFA_2)$
Similarly for all the automata. 

$A \cup B = \{x | x \in \text{A or x} \in \text{B}\}$


## Closure Property

### Regular Language

The class of Regular languages is closed under union operation.

$\displaylines{\text{Let } M_1 \text{ and } M_2 \text{ be two dfa and }L(M_1) = A \, , L(M_2) = B \\ \text{ then } \exists M \text{ where } L(M) = A\cup B}$   


#### Construction

##### One Wrong approach
We process the string with $M_1$ if it accepts then we accept else we pass the string to $M_2$ If $M_2$ accepts then accept else reject.

Why Wrong?

We can only process the string once.

##### Correct Way
How to construct M ?

![[Regular Operations 2023-04-22 17.01.37.excalidraw]]

$\text{if } a \in F_1 \text{ or } d \in F_2 \implies (a,d) \in F$

$F = (F_1 \times B) \cup (F_2 \times A)$ 


###### NFA WAY
![[Operations 2023-04-22 17.43.55.excalidraw]]

# Intersection

$A \cap B = \{x | x \in \text{A and x} \in \text{B}\}$

## Closure Property

### Regular Languages
The class of regular languages is closed under intersection operation

$\displaylines{\text{Let } M_1 \text{ and } M_2 \text{ be two dfa and }L(M_1) = A \, , L(M_2) = B \\ \text{ then } \exists M \text{ where } L(M) = A\cap B}$

#### Construction

##### Direct Construction

![[Regular Operations 2023-04-22 17.01.37.excalidraw]]

$\text{if } a \in F_1 \text{ and } d \in F_2 \implies (a,d) \in F$
$F = F_1\times F_2$ 

##### Proof using complementation 


# Concatenation

$A = \{a,b,c\}$
$B = \{d,e,f\}$

$A\cdot B = \{ad,ae,af,bd,be,bf,cd,ce,cf\}$

$A \cdot B = \{xy | x \in \text{A and y} \in \text{B}\}$

## Regular Languages

The class of regular languages is closed under intersection operation

$\displaylines{\text{Let } M_1 \text{ and } M_2 \text{ be two dfa and }L(M_1) = A \, , L(M_2) = B \\ \text{ then } \exists M \text{ where } L(M) = A\cdot B}$

#### Construction

![[Operations 2023-04-22 17.36.38.excalidraw]]


# Star Operation
Unary operation

$A = \{a,b,c\}$
$A^* = \{\epsilon, a, b, c, aa, ab, ba, bb, bc, ac , bc, aaab_\cdots \}$ 

$A^* = \{x_1x_2x_3\cdots x_k | k \geq 0 \text{ and each } x_i \in A\}$

## Closure Property

### Regular Language
The class of regular language of is closed under $*$ operation

#### Construction

![[Operations 2023-04-22 18.09.41.excalidraw]]
