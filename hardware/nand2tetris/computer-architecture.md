# Computer Architecture

**In a nutshell:** Let's recap the last four modules: we've built some elementary logic gates \(module 1\), and then used them to build an ALU \(module 2\) and a RAM \(module 3\). We then played with low-level programming \(module 4\), assuming that the overall computer is actually available. In this module we assemble all these building blocks into a general-purpose 16-bit computer called _Hack_. We will start by building the Hack Central Processing Unit \(CPU\), and we will then integrate the CPU with the RAM, creating a full-blown computer system capable of executing programs written in the Hack machine language.

**Key concepts:** Von Neumann and Harvard architectures, the stored program concept, fetch-execute cycle, data bus, instruction bus, CPU, computer design.

## Unit 5.1: Von Neumann Architecture

* The ALU loads information from the Data bus and manipulates it using the Control bits.
* Both Data and Addresses are stored in the registers.

![](../../.gitbook/assets/image%20%28115%29.png)

## Unit 5.2: The Fetch-Execute Cycle

### Fetching

* Put the location of the next instruction into the "address" of the program memory
* Get the instruction code itself by reading the memory contents at that location

![](../../.gitbook/assets/image%20%28113%29.png)

### Executing

* The instruction code specifies "what to do"
  * Which arithmetic or logical instruction
  * What memory to access \(read/write\)
  * if/where to jump
  * ...
* Often, different subsets of the bits control different aspects of the operation
* Executing the operation involves also accessing registers and/or data memory

![](../../.gitbook/assets/image%20%28108%29.png)

![](../../.gitbook/assets/image%20%28120%29.png)

![](../../.gitbook/assets/image%20%28119%29.png)

The fetch part of the cycle reads from the program memory, and the execute part reads from data memory.

### Simpler Solution: Harvard Architecture

* Variant of von Neumann
* Keeps Program and Data in two separate memory modules
* Complication avoided

## Unit 5.3: Central Processing Unit

* The Hack CPU Abstraction
  * a 16-bit processor designed to:
    * Execute the current instruction
    * Figure out which instruction to execute next \(written in the Hack language\)

![](../../.gitbook/assets/image%20%28112%29.png)

![](../../.gitbook/assets/image%20%28109%29.png)

![](../../.gitbook/assets/image%20%28114%29.png)

![](../../.gitbook/assets/image%20%28117%29.png)

![](../../.gitbook/assets/image%20%28110%29.png)

![](../../.gitbook/assets/image%20%28116%29.png)

![](../../.gitbook/assets/image%20%28111%29.png)

![](../../.gitbook/assets/image%20%28118%29.png)

## Unit 5.4: The Hack Computer

## Unit 5.5: Project 5 Overview

## Unit 5.6: Perspectives

