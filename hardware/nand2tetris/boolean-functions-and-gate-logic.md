# Boolean Functions and Gate Logic

**In a nutshell:** We will start with a brief introduction of Boolean algebra, and learn how Boolean functions can be physically implemented using logic gates. We will then learn how to specify gates and chips using a _Hardware Description Language_ \(HDL\), and how to simulate the behaviour of the resulting chip specifications using a _hardware simulator_. This background will set the stage for Project 1, in which you will build, simulate, and test 15 elementary logic gates. The chipset that you will build this module will be later used to construct the computer's _Arithmetic Logic Unit_ \(ALU\) and memory system. This will be done in modules 2 and 3, respectively.

**Key concepts:** Boolean algebra, Boolean functions, gate logic, elementary logic gates, Hardware Description Language \(HDL\), hardware simulation.

## Logic Gates

{% file src="../../.gitbook/assets/boolean\_algebra.pdf" caption="Boolean Logic" %}

![](../../.gitbook/assets/image%20%282%29.png)

![](../../.gitbook/assets/image%20%2811%29.png)

![](../../.gitbook/assets/image%20%289%29.png)

### Elementary logic gates

![](../../.gitbook/assets/image%20%2814%29.png)

![](../../.gitbook/assets/image%20%288%29.png)

![](../../.gitbook/assets/image%20%287%29.png)

The chip interface describes what the chip is doing; the chip implementation specifies how the chip is doing it. The user of the chip is interested in the chip interface; the builder of the chip is interested in the chip implementation.

![](../../.gitbook/assets/image%20%284%29.png)

## Hardware Description Language

* HDL is a functional/declarative language
* The order of HDL statements is insignificant
* Before using a chip part, you must know its interface.

{% file src="../../.gitbook/assets/hdl.pdf" caption="Hardware Description Language" %}

![](../../.gitbook/assets/image%20%281%29.png)

![](../../.gitbook/assets/image%20%283%29.png)

## Hardware Simulation

![](../../.gitbook/assets/image%20%286%29.png)

![](../../.gitbook/assets/image%20%2810%29.png)

![](../../.gitbook/assets/image%20%2835%29.png)

## Multi-Bit Buses

![](../../.gitbook/assets/image%20%2858%29.png)

![](../../.gitbook/assets/image%20%2831%29.png)

![](../../.gitbook/assets/image%20%2868%29.png)

![](../../.gitbook/assets/image%20%2838%29.png)

![](../../.gitbook/assets/image%20%2822%29.png)

* How would you xor the first and last bits of a 16-bit bus named ‘bus’?
  * Xor\(a=bus\[0\], b=bus\[15\], out=out\)

![](../../.gitbook/assets/image%20%2821%29.png)

### Quiz

This is the interface declaration for an example chip named Example16, which we haven't discussed before:

```text
IN c, Bus1[16], Bus2[16];
OUT out, out2[16];
```

These lines are valid in HDL, when implementing the Example16 chip.

* Add16\(a=Bus1\[0..15\], b=Bus2\[0..15\], out\[0..14\]=out2\[0..14\]\);
  * out\[0..14\]=out2\[0..14\] means that we're discarding the most significant bit of Add16's out, and using the rest to connect to the 15 least significant bits of Example16's out2.
* Add16\(a=true, b=false, out=out2\); 
  * As was mentioned previously in the lecture, true and false can represent a bus with constant signal of arbitrary width.
* And\(a=c, b=Bus2\[7\], out=out\);
  * This works, because And expects single bits as input 'a' and 'b'.

## Project 1 Overview

![](../../.gitbook/assets/image%20%2853%29.png)

![](../../.gitbook/assets/image%20%2823%29.png)

![](../../.gitbook/assets/image%20%2880%29.png)

![](../../.gitbook/assets/image%20%2862%29.png)

* Suppose that 1 is fed into the "in" input of a Demux chip, and the output wires are fed into a Mux chip. What would be the output of the Mux?
  * It depends on the selection bits of the chips.
  * For example: If the selection bit of the Demux is set to 0 then it will output a=1 and b=0. Now, if the selection bit of the Mux is set to 0 it will output 1, but if the selection bit of Mux is set to 1 it will output 0.

![](../../.gitbook/assets/image%20%2820%29.png)

{% file src="../../.gitbook/assets/hcs.pdf" caption="The Hack Chip Set" %}



