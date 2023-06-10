In order to be executed on a CPU, code must be written i a way that is understood by the CPU. This is called 'Machine Code' and consists of 1s and 0s.

Since it is far too inconvenient to use 0s and 1s for us humans, we prefer to abstract ourselves away using what are called "assembly" languages, which is a defined syntax of instructions that map desired outcomes to the binary machine code the CPUs run off of.

Assemblers[^1] do a 1 for 1 translation from assembly to binary. But we don't use assembly to write codes at all, we use higher-level languages which abstract away the complexity involved in dealing with CPUs. To do that we need compilers.

A compiler is a computer program that translates computer code written in one programming language (the source language) into another programming language (the target language), which is almost always assembly. 

Here is a program that prints hello world.

#### C

```c
#include <stdio.h> 
int main(void) {    printf("hello, world\n"); }
```

##### Assembly

```asm
   global  _main   
   extern  _printf   
   section .text
_main:  
   push    message   
   call    _printf   
   add     esp, 4   
   ret 
message:    
   db  'Hello, World', 10, 0
```

#### Machine code

```
b8 21 0a 00 00 a3 0c 10 00 06 b8 6f 72 6c 64 a3 08 10 00 06 b8 6f 2c 20 57 a3 04 10 00 06 b8 48 65 6c 6c a3 00 10 00 06 b9 00 10 00 06 ba 10 00 00 00 bb 01 00 00 00 b8 04 00 00 00 cd 80 b8 01 00 00 00 cd 80
```

[^1]: Sort of like translators which translate the code/instructions written in assembly to binary code understandable by computer.



The only people who ever have to deal with assembly or machine code are reverse engineers, exploit developers, and a few other jobs.