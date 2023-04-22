	## Parts of Compiler
![[Introduction 2023-04-08 22.14.12.excalidraw]]

## Lexical Analysis 

We try to make tokens out of the character stream

```c
int x = y;

int x <= == y;

```

| Token      | Pattern              | Sample lexeme |
|:---------- |:-------------------- |:------------- |
| if         | characters i,f       | if            |
| else       | characters e,l,s,e   | else          |
| comparison | <,>,<= , >=, == , != | <=            |
| number     |                      | 3.149, 160,0  |
| literal    | "....."              | "hello"              |

Lexeme may or may not be valid

e.g

```c
tin x = y;

"tin" <- literal
```

Lets see some uni level questions

> Identify the tokens in the following code :
> switch(func())
> 
> 'switch' '('  'func'  '('   ')'  ')'


```python
E = M*C**2
```

- <identifier, pointer to symbol table entry of E>
- < assignment-operator >
- <identifier, pointer to symbol table entry of M>
- < multiplication operator>
- < identifier, pointer to symbol table entry of C>
- < exponentiation-operator>
- < number, value 2>

```c
fi(a == f(x))
```

`fi` maybe function ?
These type of errors fall out of the scope of lexical analysis

```c
d = 2r

if(x==y)  // This works
```


![[Introduction 2023-04-08 22.38.41.excalidraw]]

### Specification of tokens

We use regex to formalize specification

Regular definition

$\displaylines{d_1 \, \rightarrow r_1 \\ d_2 \, \rightarrow r_2 \\ \vdots \\ d_n \rightarrow r_n}$

eg

$\displaylines{letters \,  \rightarrow A|B|\cdots|Z|a\cdots \\ digit \,  \rightarrow 0|1|\cdots \\ identifier \rightarrow letter(letter|digit)^{*}}$

Lexical Specification -> Regex -> NFA -> DFA


## Error analysis
### Lexical error
- no valid word 
- e.g `2f`

### Syntactic error
- Tokens are right but the syntax isn't right
e.g 

```c
if(){}switch else
```

### Semantic Error


Syntactic error
```Pascal
var i : Integer;
begin
	i = '1'
end
```

Syntax error at line 3
< identifier >< equal-op> < string >

There is no rule for this
(Pascal me assignment is done by `:=` )


Semantic error 

```Pascal
var i : Integer;
begin
	i := '1'
end
```

< identifier >< assign-op> < string >
Rule exists 

But we are trying to assign a Integer to a string that is **semantic error**


