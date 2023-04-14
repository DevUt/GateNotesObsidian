# Different Types of Parsing
1. Top Down Parsing
![[Parsing 2023-04-10 23.03.15.excalidraw]]
2. Bottom Up parsing
![[Parsing 2023-04-10 23.05.40.excalidraw]]

*Membership problem*

**Parsing -> Generate a parse tree of a string**

Parser for CFL requires $\Theta(n^3)$
- CYK Algorithm

Subset of CFL which require $O(n)$

# Top down parsing

| Uses backtracking | Without Backtracking |
|:----------------- |:-------------------- |
| Recursive         | Recursive            |
| Non Recursion     | Non Recursive        |


## With backtracking

$E \rightarrow T | T + E$
$T \rightarrow int | int * T | (E)$

We have to parse the string
> (int)

![[Parsing 2023-04-10 23.15.07.excalidraw]]


### Implementation

Implementation for the parser is very specific to the grammar production rules

**While implementing we assume that the string ends with $**

$E \rightarrow T | T + E$
$T \rightarrow int | int * T | (E)$

Such implementation is called as  *recursive descent* parser
> int(int)dfd
```cpp

void main(){
	x = E() // Call our start symbol
	y = match('$')
	if(!(x&&y))
		assert("Invalid")
}


bool E(){
	T()
}

bool T(){
	x = match('(')
	y = E()
	z = match(')')
	return x&&y&&z ;
}
```

- A recursive grammar can cause recursive descent parser to go into infinite loop
- OS handles parser stack

$S \rightarrow Sa$
```c
S(){
	a = S()
	b = match('a')
}
```

## Without Backtracking

### Predictive Parsing

- Idea : Predict the production rule that would be used
- Once we predicted we cannot go back

$E \rightarrow + E | num$

Old way
```c
E(){
	if(E1()) return true;
	if(E2()) return true;
	return false;
}
```

```c
E(){
	switch(curr_char){
	case '+':
		return E1();
	case 'num':
		return E2();
	}
}
```

![[Parsing 2023-04-10 23.41.27.excalidraw]]

