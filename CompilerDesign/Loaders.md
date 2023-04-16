The functions of the loader are
1. Allocation
2. Linking
3. Relocation
4. Loading
# Compile and Go Loader

- In this scheme the source code goes into the translator line by line and then the single line of code is loaded into the memory.
- The assembler is first executed and then causes the transfer of instruction of the program
- The assembler itself is present in the memory

## Advantages
1. Easy to implement
2. No extra procedures

## Disadvantages
1. Wastage of memory as assembler itself is present 
2. Retranslate the code every-time
3. Hard to handle multiple segments

![[Pasted image 20230416131035.png]]

# Absolute Loader
- The loader accepts the code given and directly loads it into the memory specified by the assembler
- No linking or relocation is done
- It only needs a single pass

## Databases
1. Header record
	1. Verify the correct program has been loaded
2. Text record
	1. Move object code into indicated address in memory
3. At End record
	1. Jump to specified address to begin execution of loaded program


## Advantages
- Simple and efficient  to implement

## Disadvantages
- Programmer must specify the address in code where the program should be loaded

![[Pasted image 20230416132306.png]]
1. Allocation - done by programmer
2. Linking - done by programmer
3. Relocation - loaded where assembler assigns
4. Loaded - By loader

