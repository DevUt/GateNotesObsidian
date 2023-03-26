- [[#Testing Strings|Testing Strings]]
- [[#Formal Definition|Formal Definition]]
- [[#What does if mean M accepts W?|What does if mean M accepts W?]]
- [[#What does if mean M accepts W?#Definition|Definition]]

# Definite Finite Automata
![[Drawing 2023-03-22 00.25.34.excalidraw]]
States $: \{q_{0} , \, q_{1} ,\, q_{2}\}$ 
Transition : $\to$
Start state : $\to O$
Accept/ Final state: Double circle


### Testing Strings
$01101 \to accept$ 
$00101 \to reject$


$M_{1}$ accepts exactly those string in A where
$A = \{w \; | w \; \text{contains substring}\; 11\}$ 

## Formal Definition
A DFA $M$ is defined as $M \,=\, (Q, \epsilon, \Sigma, \delta, q_0, F)$
$$\displaylines{Q \; : \; \text{finite set of states} \newline 
	\Sigma \; : \; \text{finite set of alphabet} \\
	\delta \; : \; \text{tranisiton function} \; \delta(q,a)\;=\;r,\text{where }r \, \epsilon \,Q \\ 
	q_0 : \epsilon \;Q \; \text{start state} \\
	F  : \text{set of accepting states}}$$
	
For the machine we saw, 
$\begin{align}\displaylines{Q = \{q_1, q_2, q_3\} \\ \Sigma = \{0,1\} \\ F = \{q_3\}}\\ \end{align}$
| $\delta$ | $0$   | $1$   |
| ------- | ----- | ----- |
| $q_1$   | $q_1$ | $q_2$ |
| $q_2$   | $q_1$ | $q_3$ |
| $q_3$   | $q_3$ | $q_3$ |

## What does if mean M accepts W?

$w \, = \, w_1w_2w_3\dots w_r$  where each $w_i \, \epsilon \, \Sigma$ 

if $\exists$ a sequence of states $r_0r_1r_2 \dots r_n$ where $r_0 = q_0$ and $r_i = \delta(r_{i-i},w_i)$  and $r_n \; \epsilon \; F$ then we can say that $w$ is accepted by $M$ 

$L(M) = \{ w\; | \; M \,\text{accepts}\, w \}$ 

### Definition 
Language of machine is the string that when *executed* ends in an accept state of the fine automaton.

**[[Regular Languages |Next]]** 