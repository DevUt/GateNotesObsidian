$X \rightarrow X\beta$ (left recursion)
$X \rightarrow \alpha X\beta$ (recursion)
$X \rightarrow \beta X$ (right recursion)


$A \rightarrow Aa|c$
What would be the output?

ca, caa, caaaa ,caaaaa , ca^n

Now removing the left recursion
$A \rightarrow cA'$
$A' \rightarrow aA' | \epsilon$



$A \rightarrow A\alpha|\beta$
$A \rightarrow \beta A'$
$A' \rightarrow \alpha A' | \epsilon$

Q
$A \rightarrow A\alpha\,|\,\beta_1 \,|\, \beta_2$

$A \rightarrow \beta_1 A' \, |\beta_2 A'$
$A' \rightarrow  \alpha A' | \epsilon$

Q
$A \rightarrow A \alpha_1 | A \alpha_2 | \beta$

$A \rightarrow \beta A'$
$A' \rightarrow \alpha_1 A' | \alpha_2 A' | \epsilon$

![[Left recursion 2023-04-08 23.45.12.excalidraw]]

![[Left recursion 2023-04-08 23.52.02.excalidraw]]

## General rule (Direct)

$A \rightarrow A\alpha_1 | A\alpha_2 | \cdots | A\alpha_m | \beta_1 | \beta_2 | \cdots | \beta_n$

We write it like
$A \rightarrow \beta_1A'\, |\beta_2A'\,|\cdots |\beta_nA'$
$A' \rightarrow \alpha_1A'\, |\alpha_2A'\,|\cdots |\alpha_mA'$

## Indirect left recursion

$S \rightarrow Aa | b$
$A \rightarrow Ac | Sd | Bc | \epsilon$
$B \rightarrow d$


![[Left recursion 2023-04-09 00.03.10.excalidraw]]

Step 1 : Assign some order 

$A, A_1 , A_2 , A_3$

Step 2:  Substitute $A_1$ in $A$
![[Left recursion 2023-04-09 00.05.42.excalidraw]]

Step 3: Eliminate Left recursion

$A \rightarrow A_2 x A'  | A_3 c A' | db A'$
$A' \rightarrow bbA' | \epsilon$

Q
![[Left recursion 2023-04-09 00.08.57.excalidraw]]

Q
![[Left recursion 2023-04-09 00.21.42.excalidraw]]

Q
![[Left recursion 2023-04-09 00.25.42.excalidraw]]
