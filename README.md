# Monty


`monty` is an interpreter for Monty ByteCodes files, a scripting language just like Python.


## About the Monty language
This is a language that contains specific instructions to manipulate data information (stacks or queues), where each instruction (*called opcode*) is sent per line. Files which contain Monty byte codes usually have the `.m` extension.


Example (`myfile.m`):
```bash
$ cat myfile.m
# Pushing element to the stack
push 0
push 1
push 2
# Printing all elements
pall
push 3
push 4
pop
# Rotating the stack to the bottom
rotr
pall
rotl
# Setting FIFO
queue
push 5
# Setting LIFO
stack
push 5
$
```


## Technologies
* Monty was written using the  C programming language
* C files were compiled using `gcc 4.8.4`
* Tested on Ubuntu 14.04 LTS


## Usage
To compile all files:

```bash
$ gcc -Wall -Werror -Wextra -pedantic -std=c89 *.c -o monty
$
```

The **synopsis** of the interpreter is the following:

```bash
$ ./monty [filename]
$
```

To run the interpreter:

```bash
$ ./monty myfile.m
2
1
0
0
3
2
1
$
```


## Features
### Opcodes
`monty` executes the following opcodes:

| Opcode | Description |
| -------- | ----------- |
| `push` | This pushes an element to the stack |
| `pall` | This prints all the values on the stack |
| `pint` | This prints the value at the top of the stack |
| `pop` | This removes the top element of the stack |
| `swap` | This swaps the top two elements of the stack |
| `queue` | This sets the format of the data to a queue (FIFO) |
| `stack` | This sets the format of the data to a stack (LIFO) |
| `nop` | This doesn't do anything |
| `add` | This adds the top two elements of the stack |
| `sub` | This subtracts the top element of the stack from the second top element of the stack |
| `mul` | This multiplies the second top element of the stack with the top element of the stack |
| `div` | This divides the second top element of the stack by the top element of the stack |
| `mod` | This computes the rest of the division of the second top element of the stack by the top element of the stack |
| `pchar` | This prints the char at the top of the stack |
| `pstr` | This prints the string starting at the top of the stack |
| `rotl` | This rotates the stack to the top |
| `rotr` | This rotates the stack to the bottom |

Comments, indicated with `#`, are not executed by the interpreter.

When a **nonextistent opcode** is passed, the interpreter prints an error message and then stops:

```bash
$ cat errormyfile.m
push 1
pint
pcx
$ ./monty errormyfile.m
1
L3: unknown instruction pcx
```


### Return value
When there is no error, `monty` returns `0`. Otherwise, returns `1`


## Authors
* Jesse Amarquaye - [GitHub](https://github.com/amarquaye)
* Eniola Olugbaike - [GitHub](https://github.com/eniolagbaike)
