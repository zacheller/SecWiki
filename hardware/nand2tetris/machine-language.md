# Machine Language

**In a nutshell:** A critically important aspect of building a new computer system is designing the low-level _machine language_, or _instruction set_, with which the computer can be instructed to do various things. As it turns out, this can be done before the computer itself is actually built. For example, we can write a Java program that emulates the yet-to-be-built computer, and then use it to emulate the execution of programs written in the new machine language. Such experiments can give us a good appreciation of the bare bone "look and feel" of the new computer, and lead to decisions that may well change and improve both the hardware and the language designs. Taking a similar approach, in this module we assume that the Hack computer and machine language have been built, and write some low-level programs using the Hack machine language. We will then use a supplied CPU Emulator (a computer program) to test and execute our programs. This experience will give you a taste of low-level programming, as well as a solid hands-on overview of the Hack computer platform.

**Key concepts:** op codes, mnemonics, binary machine language, symbolic machine language, assembly, low-level arithmetic, logical, addressing, branching, and I/O commands, CPU emulation, low-level programming.

## Machine Languages: Overview

* What was von Neumann’s contribution on top of Turing’s ideas?
  * He formulated a practical architecture for a general computing machine.
* What is true about the instructions “010001000110010” and “ADD R3 R2” presented here?
  * They perform the same operation.
  * The second instruction is written in an assembly language.
  * The second is meant to be understood by humans, and the first is a bit-representation understood by the computer.

## Machine Languages: Elements

![](<../../.gitbook/assets/image (50).png>)

* Which of these trade-offs occur in the memory hierarchy?
  * Faster access means smaller memory size

![](<../../.gitbook/assets/image (32).png>)

![](../../.gitbook/assets/image.png)

![](<../../.gitbook/assets/image (108).png>)

Flow Control: Usually CPU executes machine instructions in sequence, but sometimes we need to jump to another location so we can loop, conditionally or unconditionally.

## The Hack Computer and Machine Language

![](<../../.gitbook/assets/image (156).png>)

![](<../../.gitbook/assets/image (75).png>)

![](<../../.gitbook/assets/image (39).png>)

* The CPU reads from both RAM and ROM.
* The reset button is only used once per program.

![M is currently selected register](<../../.gitbook/assets/image (2).png>)

![](<../../.gitbook/assets/image (128).png>)

![](<../../.gitbook/assets/image (146).png>)

```
@1
M=A-1;JEQ

# The first line sets the A register to 1.
# The second line computes A-1=0.
# It stores this computation in the M register, RAM[1]
# The JEQ jump directive checks whether the computation is equal to 0
# It is, so next instruction will be the value in A register (1)
```

## Hack Language Specification

![](<../../.gitbook/assets/image (168).png>)

* 0000000000000001 sets the A register to 1.

![](<../../.gitbook/assets/image (120).png>)

* The binary instruction 1111010101101100 translates to:
  * AM=D|M;JLT

## Input/Output

![](<../../.gitbook/assets/image (159).png>)

* If you want to change the bit in row 4, column 55, what address should you retrieve, and which bit should you change?
  * Screen\[131], 7th bit

![](<../../.gitbook/assets/image (92).png>)



## Hack Programming

![](<../../.gitbook/assets/image (1).png>)

```
# RAM[11]=10
@10
D=A
A=D+1
M=D
```

![](<../../.gitbook/assets/image (23).png>)

![](<../../.gitbook/assets/image (45).png>)

![](<../../.gitbook/assets/image (136).png>)

![](<../../.gitbook/assets/image (105).png>)

![](<../../.gitbook/assets/image (102).png>)

How would an assembler distinguish between a branching symbol and a variable symbol?

* A branching symbol has a label declaration somewhere in the program, and a variable symbol doesn't.

![](<../../.gitbook/assets/image (24).png>)

Accessing a pointer usually involves:

* Changing the address register to a value retrieved from memory.

![](<../../.gitbook/assets/image (52).png>)

![](<../../.gitbook/assets/image (122).png>)

## Project 4 Overview

### Mult and Fill

Mult: a program performing R2 = R0 \* R1

![](<../../.gitbook/assets/image (87).png>)
