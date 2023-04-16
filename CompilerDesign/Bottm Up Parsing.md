# Sentinel Form 

$S \rightarrow^{*} \alpha$
$\alpha$ is called the sentinel form

Lets consider this
$S \rightarrow aA | \epsilon$
$A \rightarrow bA | \epsilon$


Lets see a derivation

$S \rightarrow aA \rightarrow abA \rightarrow abbA \rightarrow abb$
So all the "strings" here are in sentinel form

**Sentence: a sentinel form that only consists of terminals**

Left Sentinel form : These occur when doing Left most derivation
Right Sentinel form : These occur when doing right most derivation

# Handle

$S \rightarrow^{*} \alpha A w \rightarrow \alpha \beta w$ 
So what would have been the substitution?
$A \rightarrow \beta$

We say 
$\beta$ is the handle here 
Handle contains
1. Production (which rule did the substitution followed. Here : $\alpha \rightarrow \beta$
2. Position (where did the substitution happen)

Q
Given following grammar 
$S \rightarrow aAcBe$
$A \rightarrow Ab | b$
$B \rightarrow d$

List out all the handles in right most derivation of string $abbcde$

$\displaylines{\begin{align*}S & \rightarrow aAcBe\,\, [aAcBe \text{ is the handle}] \\ & \rightarrow aAcde\,\, [d \text{ is the handle}] \\ & \rightarrow aAbcde  \, \, [Ab \text{ is the handle}] \\ & \rightarrow abbcde \, \, [b \text{ is the handle}]\end{align*}}$

Q
$S \rightarrow aAS | c$
$A \rightarrow ba | SB$
$B \rightarrow bA | S$
list out all handles in right most derivation of string $acbbac$
$S \rightarrow aAS \rightarrow aAc \rightarrow aSBc \rightarrow aSbAc \rightarrow aSbbac \rightarrow acbbac$

# Viable  prefix 
Not now


# Actual Start 

What is the idea for bottom up parsing?

$S \rightarrow y_0 \rightarrow y_1 \rightarrow y_2 \cdots \rightarrow y_n = w$

```python 
for i=n to 1:
	find  handle in Ai -> Bi in y_i
	replace Bi with Ai // THIS IS REDUCTION
```

Idea in action:

$E \rightarrow E+E | E*E | id$
Parse string $id + id*id$

Now parsing
$id \,\,|\,+ id*id$  

**THE BAR IS INPUT MARKER IT SHOWS TILL WHERE DID I READ**
The left of the bar is read and right of the bar is yet to read

I have two choices
1. Reduce like this $E \,\, | + id*id$ 
2. Shift $id + | id*id$ 

$\displaylines{\begin{align*}id \,\,|\,+ id*id \\ & \rightarrow^{\text{reduce}} E |+ id*id \\ & \rightarrow^{\text{shift}} E + | id*id \\ & \rightarrow^{\text{shift}} E+id|*id \\ & \rightarrow^{\text{reduce}} E + E |*id \\ & \rightarrow^{\text{reduce}} E | *id \\ & \rightarrow^{\text{shift}} E * | id\end{align*}}$   
We have a decision to make
- Either to Shift
- Or to Reduce

**REDUCE = HANDLE**

So our question boils down, whether are we dealing with a handle

We use *stack* to store

$\underbrace{w_1w_2w_3}_{\text{read}} | \underbrace{w_4w_5w_6}_{\text{yet to read}}$

Then we ask ourselves the  questions
1. Is $w_3$ a handle?
2. Is $w_3w_2$ a handle?
3. Is $w_3w_2w_1$ a handle?

**Handles are on top of the stack**

## How to find handle?

### Strategy 1: LR(0)
L -> Left to right
R -> Right most derivation
Always reduce if you can

$S \rightarrow aa | bb | aab$ For input string $aa$
$|aa\$$
$a|a\$$
$aa|\$$
$S|\$$  Directly reduce


As you have guessed this doesn't work in many cases
For eg

$S \rightarrow aA$
$A \rightarrow a$

For input string $aa$

$|aa\$$
$a|a\$$
$A|a\$$ // reduction
$Aa| \$$
Now we are stuck 

### Strategy 2 : SLR(1)

Stands for 
Simple 
L -> Left to right
R -> Right most derivation

(1) lookahead is 1
Next symbol in input is in the follow of the variable we would reduce to


$S \rightarrow aA$
$A \rightarrow a$
For input string $aa$

$|aa\$$
$a|a\$$
does $a \in \text{Follow}(A)$
No it doesn't hence don't reduce
$aa|\$$
does $\$ \in \text{Follow}(A)$ 
Yes it does 
hence replace 



### Strategy 3: CLR

### Strategy 4: LALR


## LR(0) Items

Strategy 1 and Strategy 2 use the $LR(0)$ items

For $X \rightarrow \alpha \beta$ We have the following $LR(0)$ items

1. $X \rightarrow \cdot \alpha\beta$
2. $X \rightarrow  \alpha \cdot \beta$
3. $X \rightarrow \alpha\beta\cdot$

 $\overbrace{X}^{\text{will reduce to}} \rightarrow  \underbrace{\alpha}_{\text{seen}} \cdot \overbrace{\beta}^{\text{expect to see}}$
 
## Closure of items

$S \rightarrow BCD$
$B \rightarrow AD$
$A \rightarrow a$
$C \rightarrow c$
$D \rightarrow d$

$\text{Closure}(S)$

$S \rightarrow \cdot BCD$
$B \rightarrow \cdot AD$
$A \rightarrow \cdot a$

## Building LR(0) automaton

$S \rightarrow aa | ab$

We add an augmented production

$S^{'} \rightarrow \cdot S\$$
$S \rightarrow \cdot aa$
$S \rightarrow \cdot ab$

![[Drawing 2023-04-14 00.47.53.excalidraw]]

Q
$E \rightarrow E + T | T$
$T \rightarrow num$

![[Bottm Up Parsing 2023-04-14 01.01.03.excalidraw]]

Parse string $num + num + num\$$

**AFTER EVERY TRANSACTION RERUN DFA$

$| num + num + num \$$
$num | + num + num \$$
$T |  + num + num \$$
$E|  + num + num \$$
$E + | num + num \$$
$E +  num |+ num \$$
$E +  T |+ num \$$
$E |+ num \$$
$E + |  num \$$
$E +  T |\$$
$E|\$$
$E\$|$
$E^{'}$


Q

1. $E \rightarrow E*B$
2. $E \rightarrow E+B$
3. $E \rightarrow B$
4. $B \rightarrow 0$
5. $B \rightarrow 1$

![[Bottm Up Parsing 2023-04-14 01.24.46.excalidraw]]

LR(0)

|     | +   | *   | 0   | 1   | $      | E   | B   |
|:--- |:--- |:--- |:--- |:--- |:------ |:--- |:--- |
| 0   |     |     | S_4 | S_5 |        | 1   | 3   |
| 1   | S_8 | S_6 |     |     | accept |     |     |
| 2   |     |     |     |     |        |     |     |
| 3   | R_3 | R_3 | R_3 | R_3 | R_3    |     |     |
| 4   | R_4 | R_4 | R_4 | R_4 | R_4    |     |     |
| 5   | R_5 | R_5 | R_5 | R_5 | R_5    |     |     |
| 6   |     |     | S_4 | S_5 |        |     | 7   |
| 7   | R_1 | R_1 | R_1 | R_1 | R_1    |     |     |
| 8   |     |     | S_4 | S_5 |        |     | 9   |
| 9   | R_2 | R_2 | R_2 | R_2 | R_2    |     |     |

SLR(1)
We only reduce if entry is in the follow

|     | +   | *   | 0   | 1   | $      | E   | B   |
|:--- |:--- |:--- |:--- |:--- |:------ |:--- |:--- |
| 0   |     |     | S_4 | S_5 |        | 1   | 3   |
| 1   | S_8 | S_6 |     |     | accept |     |     |
| 2   |     |     |     |     |        |     |     |
| 3   | R_3 | R_3 |     |     | R_3    |     |     |
| 4   | R_4 | R_4 |     |     | R_4    |     |     |
| 5   | R_5 | R_5 |     |     | R_5    |     |     |
| 6   |     |     | S_4 | S_5 |        |     | 7   |
| 7   | R_1 | R_1 |     |     | R_1    |     |     |
| 8   |     |     | S_4 | S_5 |        |     | 9   |
| 9   | R_2 | R_2 |     |     | R_2    |     |     | 

$\text{Follow}(E)= \{*,+,\$\}$ 
$\text{Follow}(B) = \{*,+,\$\}$


Q
$S \rightarrow AA$
$A \rightarrow aA | b$
