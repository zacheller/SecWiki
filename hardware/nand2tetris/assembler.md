# Assembler

**In a nutshell**: Every computer has a _binary machine language_, in which instructions are written as series of 0's and 1's, and a _symbolic machine language_, also known as _assembly language_, in which instructions are expressed using human-friendly mnemonics. Both languages do exactly the same thing, and are completely equivalent. But, writing programs in assembly is far easier and safer then writing in binary. In order to enjoy this luxury, someone has to translate our symbolic programs into binary code that can execute as-is on the target computer. This translation service is done by an agent called _assembler_. The assembler can be either a person who carries out the translation manually, or a computer program that automates the process. In this module and final project in the course we learn how to build an assembler. In particular, we'll develop the capability of translating symbolic Hack programs into binary code that can be executed as-is on the Hack platform. Each one of you can choose to accomplish this feat in two different ways: you can either implement an assembler using a high-level language, or you can simulate the assembler's operation using paper and pencil. In both cases we give detailed guidelines about how to carry out your work.

**Key concepts:** Binary and symbolic machine languages, parsing, symbol tables, code generation, cross assembler, assembler implementation.

## Unit 6.1: Assembly Languages and Assemblers

* Basic Assembler Logic
  * Repeat:
    * Read the next Assembly language command
    * Break it into the different fields it is composed of
    * Lookup the binary code for each field
    * Combine these codes into a single machine language command
    * Output this machine language command
* The assembler translates assembly language to machine language
* The assembler enters a symbol into the table only when that symbol has not appeared before.

## Unit 6.2: The Hack Assembly Language

* Assembly Program Elements
  * white space
    * Empty lines / indentation
    * Line comments
    * in-line comments
  * instructions
    * A
    * C
  * symbols
    * references
    * label declarations
* Ignore white space!

## Unit 6.3: The Assembly Process - Handling Instructions

* Translating A Instructions
  * if value is a decimal constant, generate the equivalent 15-bit binary constant
  * if value is a symbol, later
  * Example
    * What is the binary value of the instruction @9 ?
      * 0000000000001001
* Translating C Instructions
  * Parse statement and save it into 3 individual fields
    * dest = comp ; jump
  * Example
    * What is the binary value of the instruction MD=A-1;JGE ?
      * 111 0 110010 011 011
* For each instruction
  * parse, break into fields
  * A: translate dec to bin
  * C: generate bin for each field, assemble into full 16bit instruction
  * Write the 16 bit instructions to output file

## Unit 6.4: The Assembly Process - Handling Symbols

* Symbols
  * variable: represent memory locations where the programmer wants to maintain values
    * any symbol XXX appearing which is not predefined and is not defined elsewhere using \(XXX\) directive is treated as a variable
    * assigned a unique memory address, starting at 16
    * @variableSymbol
      * if first time, assign a unique memory address
      * else, replace with it's value
  * label: represent destinations of goto instructions
    * declared by the pseudo-command \(xxx\)
    * this directive defines the symbol XXX to refer to the memory location holding the next instruction in the program
    * @labelSymbol -&gt; replace with its value
  * pre-defined: represent special memory locations
    * 23 symbols
    * @preDefinedSymbol -&gt; replace with its value
* Symbol table

  * Contains symbol:value pairs
  * initialize with the predefined symbols
  * First pass: add the label symbols --look for '\(' symbols
  * Second pass: add the var. symbols

* The Assembly process
  * Initialization
    * Construct an empty symbol table
    * Add the predefined symbols to the symbol table
  * First pass
    * Scan the entire program
    * For each instruction of the form \(xxx\):
      * add the pair \(xxx, address\) to the symbol table, where address is the number of the instruction following \(xxx\)
  * Second pass
    * Set n to 16
    * Scan the entire program again; for each instruction:
      * If the instruction is @symbol, look up symbol in the table:
        * If \(symbol, value\) is found, use value to complete the instruction's translation;
        * if not found:
          * Add \(symbol, n\) to the symbol table
          * Use n to complete the instruction's translation
          * n++
      * If the instruction is a C instruction, complete the instruction's translation
      * Write the translated instruction to the output file

## Unit 6.5: Developing a Hack Assembler

* Main loop
  * Get the next command and parse it
  * select A or C, translate
  * output the resulting machine language command

## Unit 6.6: Project 6 Overview: Programming Option

* Contract
  * Develop a HackAssembler program
  * The source program is supplied: Xxx.asm
  * The generated code is written into a text file named Xxx.hack
  * Assumption: Xxx.asm is error-free
* Proposed design
  * Parser: unpacks each instruction into its underlying fields
  * Code: translates each field into its corresponding binary value
  * SymbolTable: manages the symbol table
  * Main: initializes the I/O files and drives the process
* Proposed implementation
  * staged development
    * develop a basic assembler that translates assembly programs without symbols
    * develop an ability to handle symbols
    * morph basic into one that can translate any assembly program
    * Supplied test programs
      * Add.asm: tests white space and instruction handling
      * Max.asm \(with symbols\) and MaxL.asm \(without symbols\)
* Testing Options
  * Hardware sim
    * load Xxx.hack into Hack Computer chip, then execute it
  * CPU Emulator
    * load Xxx.hack into supplied CPUEmulator, then execute it
  * Assembler
    * use supplied Assembler to translate Xxx.asm; compare resulting code with yours

