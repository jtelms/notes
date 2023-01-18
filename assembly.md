# Assembly: Intro to x86

These notes are taken from the video series: [Intro to x86 Assembly Language](https://youtube.com/watch?v=wLXIWKUWpSs&list=PLmxT2pVYo5LB5EzTPZGfFN0c2GDiSXgQe) by Davy Wybiral

## What is Assembly?
- A set of programming languages
- Almost no abstraction, human-readable machine code
- Trade Off: More CPU control v. More code required
- Not very portable, architecture dependent

## Understanding the CPU
- It is a machine that executes simple commands quickly
- Registers:
  1. Working Memory: used while needed, not for long-term storage
  2. Each are used for different purposes
  3. Of fixed width: architecture dependent
     - 32-bit = 32 bits per register, and so on
     - All backwards compatibility is achieved through register subsets
     - 64-bit register using 1/2 of itself to run 32-bit code
 - The Stack
   1. LIFO(Last-in, First-out) data structure
      - interact with pushes and pops
      - push: puts value on the top of the stack
      - pop: takes item from top of stack
   2. Is an array
   3. Top of stack is indicated by a stack pointer
   4. There is random access, either to data in stack or to the pointer

## Example 1: ex.asm
*A note: the semi-colon is the delimiter for comments, any text from it to the end of the line will be seen as a comment and not executed*

*A note: commands in assembly always take the form of a three letter mnemonic followed by operands: command operand1, operand2, etc.*
```assembly
global _start       ;makes the _start an identifier, where execution starts
_start:             ;makes _start a label, labels allow us to name locations in code
    mov eax, 1      ;moves the value, 1, into the eax register
    mov ebx, 42     ;moves 42 into ebx
    int 0x80        ;performs an interrupt that performs a syscall using the form of: syscall(eax=call #, other registers as parameters)
```

What we have here is a quick program that exits itself via the sys_exit system call. The exact system call is identified through the value of eax, which points to the "exit" call. Exit requires an exit status which we provide as a parameter through ebx. The int command is the interrupt, which since the value of the interrupt is hex 80(0x80), denotes a syscall interrupt.

To compile this program, enter the following commands into the terminal:
*A note: this tutorial and these notes are assuming a linux environment and uses the bash shell*

*A note: this course uses the nasm assembler as the default, as it is widely supported and allows the use of the relatively simple Intel syntax for Assembly*
```bash
$nasm -f elf32 ex1.asm -o ex1.o
$ld -m elf_i386 ex1.o -o ex1
$./ex1
$echo $?
```
These commands should fully compile, run our program, and allow us to check the exit status. The first command compiles our program: the -f followed elf32 denotes that this should be comiled as a linux executable; ex1.asm is out input file; -o ex1.o, denotes how we are going to output our finished 'object file'. The next command passes our object file to a linker, ld, -m elf_i386 denotes our format as a 32-bit file, then we specify our input file, and our output executable. The final two commands are to run our program and then print the exit status to the terminal, respectively.

## Example 2: Hello world
```assembly
global _start

section .data
    msg db "Hello World!", 0x0a
    len equ $-msg
    
section .text
    mov eax, 4      ;denotes the write syscall
    mov ebx, 1      ;prints text to stdout
    mov ecx, msg    ;bytes to write
    mov edx, len    ;# of bytes
    int 0x80        ;perform syscall, write
    mov eax, 1      ;new syscall, exit
    mov ebx, 0      ;set exit status
    int 0x80        ;perform syscall, exit
```

From here, we should just compile our program and run it like before, except we shouldn't need to echo to get output from the program, we can if the progrsm doesn't work properly to see if the exit status is correct. However, we should only need to see the Hello World that printed to the terminal. The .data section is where variables and any data needed to run the program.

## Intro to control flow
- There is none! At least natively
- Control flow like loops must be built in by hand using jump commands(jmp operand)

## Instruction pointer
- Labelled EIP
- Location of current code execution
- Not like a regular register, cannot be directly manipulated
- EIP is changed through jumps

## Example 3: ex3.asm
```assembly
global _start
_start:
    mov eax, 1      ;exit syscall
    mov ebx, 42     ;status=42
    jmp skip        ;this should jump over any code below it to the skip section
    mov ebx, 13     ;code to be skipped, would change exit status to 13 if used

skip:
    int 0x80        ;perform exit syscall
```
If this code is compiled and ran, upon echoing out the exit status, it should display 42 since the code skipped to executing the exit before changing ebx. This code is an example of an unconditional jump.

## Examples of other types of jumps
- je = jump if equal
- jne = jump if not equal
- jg = jump if greater than
- jge = jump if greater than or equal to
- jl = jump if less than
- jle = jump if less than or equal to

As can be seen by these commands, we have a piece of building decision-making structures, these jumps are examples of conditional jumps. The other part of decision-making is built into the compare(cmp) command, as well being able to add iterators(which will be in the next example).

## Example 4: ex4.asm
```assembly
global _start
_start:
    mov ecx, 4      ;# of iterations, iterator
    mov ebx, 1      ;ebx = 1
label:
    add ebx, ebx    ;double ebx by adding ebx to ebx
    dec ecx         ;decrement ecx by 1, ecx -= 1, reducing iterator to prevent infinite loops
    cmp ecx, 0      ;compare iterator in ecx to 0 
    jg label        ;if ecx is greater than 0, run another loop of label
    mov eax, 1      ;exit syscall, our result of the loop will be exit status
    int 0x80        ;perform exit
```

We have created a loop, much like in other languages: this one doubles the initial value of ebx by the amount of times determined by ecx.

## Memory Access
### Example 5: ex5.asm
```assembly
global _start
section .data
    addr db "yellow"
section .text
_start:
    mov eax, 4
    mov ebx, 1
    mov ecx, addr
    mov edx, 6
    int 0x80
    mov eax, 1
    mov ebx, 0
    int 0x80
```

This code should print the string, 'yellow' to stdout.

Now, we can arbitraily manipulate this memory address to change the output from 'yellow' to 'Hello!'
```assembly
global _start
section .data
    addr db "yellow"
    len equ $-addr        ;we add this adaptive length measure for our string, so we don't need to manually enter it or do math
section .text
_start:
    mov [addr], byte 'H'    ;change the first byte of addr to H
    mov [addr+5], byte '!'  ;change the byte at the addr with the offset of 5 to !
    mov eax, 4
    mov ebx, 1
    mov ecx, addr
    mov edx, 6
    int 0x80
    mov eax, 1
    mov ebx, 0
    int 0x80
```

The difference here is that the output should read 'Hello!'. In this example, it has been demonstrated the it is possible to directly manipulate arbitrary points in memory with assembly code, using offsets to place or replace characters.

## Other Common Data types
*A note: db is one byte wide, 8-bits*
- name1 db "string", this is an example of a byte string
- name2 db 0xff, is an example of a single byte, presented with its hex value
- name3 db 100, is an example of a decimal literal, this literal cannot start with 0. Floating point math is a more complicated process for later

*A note: dw is 2 bytes wide, 18-bits*
- name4 dw 0x1234
- name5 dw 1000

*A note: dd is 4 bytes wide, 32-bits*
- name6 dd 0x12345678
- name7 dd 100000

## The stack, again
- The stack pointer is labelled ESP
- ESP denotes the top of the stack
- Stack pointer index goes up and down in increments of 4, by 4 bytes
- ESP is always the top of the stack
- Moved by push and pop
- pop increases ESP and moves value elsewhere, such as eax

## Example 6: ex6.asm
```assembly
global _start

_start:
    sub esp, 4              ;allocate 4 bytes on the stack
    mov [esp], byte 'H'     ;move this byte to the stack at the bytes we allocated earlier
    mov [esp+1], byte 'e'
    mov [esp+2], byte 'y'
    mov [esp+3], byte '!'
    mov eax, 4              ;write syscall
    mov ebx, 1              ;print to stdout
    mov ecx, esp            ;bytes to write, specifically 'Hey!' as specified earlier
    mov edx, 4              ;# of bytes to write
    int 0x80
    mov eax, 1              ;exit syscall
    mov ebx, 0              ;exit status 0 if successful
    int 0x80
```

This code directly allocates the room for our string on the stack by moving esp and writing bytes one by one.

## functions
- They are bits of code that can be repeatably jumped to and from
- Functions allow for interaction with higher-level programming languages such as C
- Functions are invoked by a call:
  1. Push EIP to stack
  2. Perform a jump

## Example 7
```assembly
global _start

_start:
    call func
    mov eax, 1
    mov ebx, 2
    int 0x80
    
func:
    mov ebx, 42
    pop eax
    jmp eax
```

This is the simplest way to create a function in assembly, however it is a very dirty way to make a function because we did pay attention to how our code will affect the stack. This is okay in our very limited scope, yet when code gets more complicated and requires using outputs of functions as the input of other functions, this current approach to handling the stack(none) will result in performance issues and memory issues.

Here is a better approach to handling the stack, we'll also write some code to the stack as well:
```assembly
global _start

start:
    call func
    mov eax, 1
    mov ebx, 0
    int 0x80
    
func:
    mov ebp, esp        ;this moves our original esp to a place for safe-keeping, preserving our stack, known as a code Prologue
    sub esp, 2
    mov [esp], byte 'H'
    mov [esp+1], byte 'i'
    mov eax, 4
    mov ebx, 1
    mov ecx, esp
    mov edx, 2
    int 0x80
    mov esp, ebp        ;This restores the original esp value from before we called for func and ran the code, known as a code Epilogue
    ret                 ;we return back to the main code, starting at the instruction directly below the call
```

## Arguments, Parameters, and External code
- Arguments are passed on the stack
- Example:

*A note: arguments are passed on the stack, they must be passed in reverse order to which they are used in the function due to the nature of the stack*
```assembly
_start:
    push 21             ;passing our argument for our function to the stack
    call times2         ;calling our function 'times2', which will double our argument value
    mov ebx, eax        ;moving our result into our return status
    mov eax, 1          ;exiting the program
    int 0x80
times2:
    push ebp            ;prologue
    mov ebp, esp        ;prologue
    mov eax, [ebp+8]    ;this let's us access our argument
    add eax, eax        ;our operation, we double our argument by adding it to itself
    mov esp, ebp        ;epilogue
    pop ebp             ;epilogue
    ret                 ;return, so we can exit the program
```

- An example of using external code, bringing in C's printf function:

*A note: in this code we start popping values off the stack after we are donne with them, this is an automatic process in other languages called 'Garbage Collection', since assembly is an entirely manual language, we have to handle our stack data ourselves*
```assembly
global main     ;we need to make main our entry point so C can figure out where the code we want to use is
extern printf   ;we bring in the function that we want to use from C, it'll be properly linked to the code at compile times

section .data
    msg db "Testing %i...", 0x0a, 0x00      ;%i is the string literal for integers, which we'll insert later, 0x0a is the newline character, and 0x00 denotes the end of the line of code for C
    
main:
    push ebp        ;prologue to preserve the stack
    mov ebp, esp    ;moving our stack pointer to preserve the stack
    push 123        ;passing our second argument for printf, our integer literal
    push msg        ;passing our first argument to printf, the text we want to print
    call printf     ;calling the function, printf from C
    mov eax, 0      ;setting our return status
    mov esp, ebp    ;restoring the stack, epilogue
    pop ebp         ;epilogue
    ret             ;returning the fucntion and exiting the program
```

Since the code above uses C code from the standard library, we'll need to change our linker during the compilation pipeline. It is easiest to use gcc due to it being already available on any linux system. So here's the command for gcc to link our object file.

```bash
$gcc -m32 ex.o -o ex
```

In the command above to gcc, the m32 flag is meant to tell the linker that this a 32-bit program. The o flag just defines our output file, just like with ld. From here we can run the program as usual, the program should print 'Testing 123...' to stdout using printf from C.

## Making Assembly Code Accessible to C
```assembly
global add42            ;allow the linker to see our code, creating a custom entry point to this program other than start
add42:
    push ebp            ;we are pushing our stack base pointer
    mov ebp, esp        ;storing the original stack pointer at the bottom of the stack, finishing the prologue, preserving the stack
    mov eax, [ebp+8]    ;access our argument when we supply it, argument is stored in eax for operation
    add eax, 42         ;performing the desired operation, adding 42 to our passed argument
    esp, ebp            ;restoring the stack to its state before our function, finishing the epilogue
    ret                 ;returning to our program flow
```

From here we need to perform two more steps before we can access our function from C, one is to compile our object file as normal, the second though is specific to making custom functions for C. The next code block is just a quick header file for C code.

*Filename: add42.h, which is the name of the original object file but with the header file extension*
```c
int add42(int x)
```

All the header file does for us is define the syntax, parameters, and return type for our custom function. From here we will write a quick C file to demonstrate this custom function:

```c
#include <stdio.h>
#include "add42.h"

int main() {
    int result;
    result = add42(30);
    printf("Result: %i\n", result);
    return 0;
}
```

This program just takes takes a number, puts it through our custom function which adds 42 to the provided number, and prints the result to the screen. When we go to compile our C program, the process will be slightly different because we have to actively link to the object file of our custom function like this:

```bash
$gcc -m32 add42.o main.c -o ex
```

Alternatively there is the option to use assembly code inline in a C program, however, this makes the code unable to be easily ported other architectures because it will be using whatever assembly that is specific to the machine it is working on. A more portable solution is to use the external assembly above because only one line of code is needed to make the C compatible with the machine, the include statement: the only other work required is providing easily producible object files to be linked with other machines at compile time. The external code approach also makes the code more modular and easier to debug.
