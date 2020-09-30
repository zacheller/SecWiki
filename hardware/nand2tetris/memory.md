# Memory

**In a nutshell:** Having built the computer's ALU, this module we turn to building the computer's _main memory_ unit, also known as _Random Access Memory,_ or _RAM_. This will be done gradually, going bottom-up from elementary flip-flop gates to one-bit registers to _n_-bit registers to a family of RAM chips. Unlike the computer's processing chips, which are based on _combinational logic_, the computer's memory logic requires a clock-based _sequential logic_. We will start with an overview of this theoretical background, and then move on to build our memory chipset.

**Key concepts:** combinational vs sequential logic, clocks and cycles, flip-flops, registers, RAM units, counters.

## Sequential Logic

![](../../.gitbook/assets/image%20%2824%29.png)

![](../../.gitbook/assets/image%20%2839%29.png)

* Why do we use discrete time steps instead of continuous time?
  * To ensure the system state is stabilized.

![](../../.gitbook/assets/image%20%2859%29.png)

## Flip Flops

![](../../.gitbook/assets/image%20%2870%29.png)

![Little triangle means chip is dependent on time, sequential, has state](../../.gitbook/assets/image%20%2852%29.png)

* Implementation of the D Flip Flop
  * in this course: it is a primitive
  * in physical implementations, it may be built from actual Nand gates

![](../../.gitbook/assets/image%20%2840%29.png)

![](../../.gitbook/assets/image%20%2847%29.png)

* What are the differences between the DFF chip and the Bit chip?
  * DFF always stores the “in” bit, while Bit only stores it if “load” is set to 1.
  * DFF can store information for one time unit only, while Bit can store it for many cycles.

![](../../.gitbook/assets/image%20%2867%29.png)

## Memory Units

![](../../.gitbook/assets/image%20%2854%29.png)

![](../../.gitbook/assets/image%20%2828%29.png)

Current value of a register is always being outputted.

![](../../.gitbook/assets/image%20%2841%29.png)

* What is the difference between a register’s width and a register’s address?
  * Width is the amount of data a single register holds, address is the location of the register within a larger chip.

![](../../.gitbook/assets/image%20%2836%29.png)

![](../../.gitbook/assets/image%20%2863%29.png)

![](../../.gitbook/assets/image%20%2861%29.png)

## Counters

![](../../.gitbook/assets/image%20%2856%29.png)

![](../../.gitbook/assets/image%20%2830%29.png)

## Project 3 Overview

![](../../.gitbook/assets/image%20%2827%29.png)

![16 bit register can be built from multiple 1-bit registers](../../.gitbook/assets/image%20%2842%29.png)

![](../../.gitbook/assets/image%20%2864%29.png)

![](../../.gitbook/assets/image%20%2866%29.png)

![](../../.gitbook/assets/image%20%2855%29.png)

