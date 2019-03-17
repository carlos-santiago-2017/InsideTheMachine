# INSIDE THE MACHINE

## 1 Basic Computing Concepts.

At the heart of the modern computer is the microprocessor —also commonly called the central processing unit (CPU)

## The calculator Model of Computing

A computer takes a stream of instructions (code) and a stream of data as input, and it produces a stream of results as output.

Figure 1-1

Figure 1-2

## The File-Clerk Model of Computing

In the file-clerck model, the computer accesses a large store of sequentially arranged numbers for the purpose of altering that store to achieve a desired result. Once this desired result is achived, the computer halts so that the now-modified store of numbers can be read and interpreted by humans.

## The stored-Program Computer

All computers consist of at least three fundamental types of structures needed to carry out the read-modify-write sequence:

- Storage.
- Arithmetic Logic Unit (ALU)
- Bus.

Figure 1.3

Prior to the invention of the first stored-program computer, all computing devices, from the abacus to the earliest electronic computer machines, had to be manipulated by an operator or group of operators who manually entered a particular sequence of commands each time they wanted to make a particular calculation.

## Refining the File-clerck Model.

All computers operate.

Example

1.- obtain two numbers to be added (the input operands) from the data storage.
2.- Add the numbers.
3.- Place the results back into data storage.

Those three steps are carried out billions of times per second on a modern CPU.


## The register file

Most computers have a relatively small number of very fast data storage locations attached to the ALU, these locations ara called registers.

Backing to the example.

1.- Obtain the two numbers to be added (the input operands) from the two source registers.
2.- Add the numbers.
3.- Place the results back in a destination register.

This three-step sequence is quite simple, but it's at the very core of how a microprocessor really works.

## The File-Clerck MOdel Revised and Expanded

We can think of main memory as a document storage room located on another floor and the registers as a small.
The clerk does not really know anything about the document storage room

# RAM: When Registers Alone Won't Cut It

Main Memory which in moder computers is always some type of random access memory (RAM), stores the data set on which the computer operates, and only a small portion of the data set at a time is moved to the registers for easy access from the ALLU.

In fact, the ALU an the registers are internal parts of the microprocessor, but main memory is a complete separeta component of the computer system that is connected to the processor via the Memory Bus. Transfering data between main memory and the registers via the memory bus takes a significant amount of time. This, if there were no registers and the ALU had to read data directly from the main memory for each calculation, computers would run very slowly. However, because the register enable the computer to store data near the ALU, where it can be access nearly instantaneously, the computer's computational speed is decoupled somewhat from the speed of main memory.


#The File-Clerk Model Revised and Expanded

we can think of main memory as a document storage room located on another floor and the registers as a small, personal filing cabinet where the file clerk places the papers on which he is currently working. The Clerk doesn not really know anything about the document storage room.

# A closer Look at the Code Stream: The Program

At the beginning did say, Code Stream: An ordered sequence of operatios, noiw operations becomes instructions, because not only operatations would do.

## General Instruction Types

These ordered lists of instructions are called programs. In modern RISC microprocessor, the act of moving data between memory and the registers is under the explicit control of the code stream, or program.


Modern RISC microprocessors the code stream is in charge to move data between memory and the registers. Operations are two main categories:

- Arithmethic instrucctions. (add, sub, mul, div)
- Memory-access instructions. (load, store)

To show you how memory-access and arithmetic operations work together within the context of the code stream.

# The DLW-1's Basic Architecture and Arithmetic Instruction Format

DLW1 

- ALU
- 4 registers: A,B,C y D
- Bank Main Memory 256 memory cells.
- The number that identifies an individual memory cell is called an address.

# The DLW-1's Arithmetic Instruction Format 

instruction source1, source2, destination

instruction field:
source1 field:
source2 field:
destination field:





