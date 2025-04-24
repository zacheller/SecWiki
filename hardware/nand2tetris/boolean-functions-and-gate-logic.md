# Boolean Functions and Gate Logic

**In a nutshell:** We will start with a brief introduction of Boolean algebra, and learn how Boolean functions can be physically implemented using logic gates. We will then learn how to specify gates and chips using a _Hardware Description Language_ (HDL), and how to simulate the behaviour of the resulting chip specifications using a _hardware simulator_. This background will set the stage for Project 1, in which you will build, simulate, and test 15 elementary logic gates. The chipset that you will build this module will be later used to construct the computer's _Arithmetic Logic Unit_ (ALU) and memory system. This will be done in modules 2 and 3, respectively.

**Key concepts:** Boolean algebra, Boolean functions, gate logic, elementary logic gates, Hardware Description Language (HDL), hardware simulation.

## Logic Gates

{% file src="../../.gitbook/assets/boolean_algebra.pdf" %}
Boolean Logic
{% endfile %}

![](<../../.gitbook/assets/image (82).png>)

![](<../../.gitbook/assets/image (4).png>)

![](<../../.gitbook/assets/image (29).png>)

### Elementary logic gates

![](<../../.gitbook/assets/image (97).png>)

![](<../../.gitbook/assets/image (145).png>)

![](<../../.gitbook/assets/image (36).png>)

The chip interface describes what the chip is doing; the chip implementation specifies how the chip is doing it. The user of the chip is interested in the chip interface; the builder of the chip is interested in the chip implementation.

![](<../../.gitbook/assets/image (103).png>)

## Hardware Description Language

* HDL is a functional/declarative language
* The order of HDL statements is insignificant
* Before using a chip part, you must know its interface.

{% file src="../../.gitbook/assets/HDL.pdf" %}
Hardware Description Language
{% endfile %}

![](<../../.gitbook/assets/image (62).png>)

![](<../../.gitbook/assets/image (155).png>)

## Hardware Simulation

![](<../../.gitbook/assets/image (37).png>)

![](<../../.gitbook/assets/image (150).png>)

![](<../../.gitbook/assets/image (7).png>)

## Multi-Bit Buses

![](<../../.gitbook/assets/image (124).png>)

![](<../../.gitbook/assets/image (164).png>)

![](<../../.gitbook/assets/image (147).png>)

![](<../../.gitbook/assets/image (41).png>)

![](<../../.gitbook/assets/image (76).png>)

* How would you xor the first and last bits of a 16-bit bus named ‘bus’?
  * Xor(a=bus\[0], b=bus\[15], out=out)

![](<../../.gitbook/assets/image (123).png>)

### Quiz

This is the interface declaration for an example chip named Example16, which we haven't discussed before:

```
IN c, Bus1[16], Bus2[16];
OUT out, out2[16];
```

These lines are valid in HDL, when implementing the Example16 chip.

* Add16(a=Bus1\[0..15], b=Bus2\[0..15], out\[0..14]=out2\[0..14]);
  * out\[0..14]=out2\[0..14] means that we're discarding the most significant bit of Add16's out, and using the rest to connect to the 15 least significant bits of Example16's out2.
* Add16(a=true, b=false, out=out2);&#x20;
  * As was mentioned previously in the lecture, true and false can represent a bus with constant signal of arbitrary width.
* And(a=c, b=Bus2\[7], out=out);
  * This works, because And expects single bits as input 'a' and 'b'.

## Project 1 Overview

![](<../../.gitbook/assets/image (113).png>)

![](<../../.gitbook/assets/image (42).png>)

![](<../../.gitbook/assets/image (139).png>)

![](<../../.gitbook/assets/image (101).png>)

* Suppose that 1 is fed into the "in" input of a Demux chip, and the output wires are fed into a Mux chip. What would be the output of the Mux?
  * It depends on the selection bits of the chips.
  * For example: If the selection bit of the Demux is set to 0 then it will output a=1 and b=0. Now, if the selection bit of the Mux is set to 0 it will output 1, but if the selection bit of Mux is set to 1 it will output 0.

![](<../../.gitbook/assets/image (93).png>)

{% file src="../../.gitbook/assets/hcs.pdf" %}
The Hack Chip Set
{% endfile %}

