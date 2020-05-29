# INSIDE THE MACHINE

1. [Introduction]() 
2. [Basic Computing Concepts]() 
3. [The Mechanics of Program Execution]() 
4. [Pipelined Execution]() 
5. [Pipelined Execution]() 
6. [PowerPC Processors: 600 Series, 700 Series, and 7400]()
7. [Intel’s Pentium 4 vs. Motorola’s G4e: Approaches and Design Philosophies]()
8. [Intel’s Pentium 4 vs. Motorola’s G4e: The Back End]()
9. [64-Bit Computing and x86-64]()
10. [The G5: IBM’s PowerPC 970]()
11. [Understanding Caching and Performance]()
12. [Intel’s Pentium M, Core Duo, and Core 2 Duo]()
13. [Bibliography and Suggested Reading]()


# 1. [INTRODUCTION]()

# 2. [BASIC COMPUTING CONCEPTS]()

- [The Calculator Model of Computing]()
- [The File-Clerk Model of Computing]()
	* [The Stored-Program Computer]()
	* [Refining the File-Clerk Model]()
- [The Register File]()
- [RAM: When Registers Alone Won’t Cut It]()
	* [The File-Clerk Model Revisited and Expanded]() 
	* [An Example: Adding Two Numbers]()
- [A Closer Look at the Code Stream: The Program]()
	* [General Instruction Types]()
	* [The DLW-1’s Basic Architecture and Arithmetic Instruction Format]()
- [A Closer Look at Memory Accesses: Register vs. Immediate]()
	* [Immediate Values]()
	* [Register-Relative Addressing]()

# 3. [THE MECHANICS OF PROGRAM EXECUTION]()

- [Opcodes and Machine Language]()
	* [Machine Language on the DLW-1]()
	* [Binary Encoding of Arithmetic Instructions]()
	* [Binary Encoding of Memory Access Instructions]()
	* [Translating an Example Program into Machine Language]() 
- [The Programming Model and the ISA]() 
	* [The Programming Model]()
	* [The Instruction Register and Program Counter]() 
	* [The Instruction Fetch: Loading the Instruction Register]() 
	* [Running a Simple Program: The Fetch-Execute Loop]() 
- [The Clock]()
- [Branch Instructions]() 
	* [Unconditional Branch]() 
	* [Conditional Branch]() 
- [Excursus: Booting Up]() 


# 4. [PIPELINED EXECUTION 35]()

- [The Lifecycle of an Instruction]()
- [Basic Instruction Flow]()
- [Pipelining Explained]()
- [Applying the Analogy]()
	* [A Non-Pipelined Processor]() 
	* [A Pipelined Processor]()
	* [The Speedup from Pipelining]() 
	* [Program Execution Time and Completion Rate]() 
	* [The Relationship Between Completion Rate and Program Execution Time]()
	* [Instruction Throughput and Pipeline Stalls]()
	* [Instruction Latency and Pipeline Stalls]()
	* [Limits to Pipelining]()


## 1 Basic Computing Concepts.

At the heart of the modern computer is the microprocessor —also commonly called the central processing unit (CPU)

## The calculator Model of Computing

A computer takes a stream of instructions (code) and a stream of data as input, and it produces a stream of results as output.

![Screen Shot 2020-05-27 at 20 17 13](https://user-images.githubusercontent.com/24994818/83087521-20bbd100-a057-11ea-8692-ea35561d3de1.png)
![Screen Shot 2020-05-27 at 20 17 01](https://user-images.githubusercontent.com/24994818/83087522-21ecfe00-a057-11ea-8597-2bb367cfd575.png)
![Screen Shot 2020-05-27 at 20 16 51](http
![Screen Shot 2020-05-27 at 20 15 14](https://user-images.githubusercontent.com/24994818/83087533-23b6c180-a057-11ea-8627-b68a4c26a795.png)
![Screen Shot 2020-05-27 at 20 14 59](https://user-images.githubusercontent.com/24994818/83087534-23b6c180-a057-11ea-9e7e-f8abb864a5b1.png)
![Screen Shot 2020-05-27 at 20 14 44](https://user-images.githubusercontent.com/24994818/83087535-244f5800-a057-11ea-9b49-a335e2ffdd87.png)
![Screen Shot 2020-05-27 at 20 14 30](https://user-images.githubusercontent.com/24994818/83087537-244f5800-a057-11ea-8a36-37d407c495e0.png)
![Screen Shot 2020-05-27 at 20 14 17](https://user-images.githubusercontent.com/24994818/83087538-244f5800-a057-11ea-832c-0939e6b4ba89.png)
![Screen Shot 2020-05-27 at 20 13 49](https://user-images.githubusercontent.com/24994818/83087540-24e7ee80-a057-11ea-8c9c-59081720ff0a.png)
![Screen Shot 2020-05-27 at 20 12 08](https://user-images.githubusercontent.com/24994818/83087542-25808500-a057-11ea-8425-375ad8809116.png)
![Screen Shot 2020-05-27 at 20 16 40](https://user-images.githubusercontent.com/24994818/83087525-21ecfe00-a057-11ea-9f91-9a2249c5c2a9.png)
![Screen Shot 2020-05-27 at 20 16 27](https://user-images.githubusercontent.com/24994818/83087526-22859480-a057-11ea-9e39-7472afd89835.png)
![Screen Shot 2020-05-27 at 20 16 15](https://user-images.githubusercontent.com/24994818/83087527-22859480-a057-11ea-8653-5335fd98e500.png)
![Screen Shot 2020-05-27 at 20 15 59](https://user-images.githubusercontent.com/24994818/83087528-22859480-a057-11ea-9d6c-bd72244369a0.png)
![Screen Shot 2020-05-27 at 20 15 49](https://user-images.githubusercontent.com/24994818/83087529-231e2b00-a057-11ea-9c4e-f255a8189194.png)
![Screen Shot 2020-05-27 at 20 15 39](https://user-images.githubusercontent.com/24994818/83087530-231e2b00-a057-11ea-9d45-63fad093bacc.png)
![Screen Shot 2020-05-27 at 20 15 30](https://user-images.githubusercontent.com/24994818/83087531-231e2b00-a057-11ea-9eed-3149896d9f41.png)
![Screen Shot 2020-05-27 at 20 15 18](https://user-images.githubusercontent.com/24994818/83087532-23b6c180-a057-11ea-9388-2183270e46d3.png)
![Screen Shot 2019-08-26 at 3 43 05 PM](https://user-images.githubusercontent.com/24994818/63722147-35dda800-c818-11e9-9e40-599208836737.png)


## The File-Clerk Model of Computing

In the file-clerck model, the computer accesses a large store of sequentially arranged numbers for the purpose of altering that store to achieve a desired result. Once this desired result is achived, the computer halts so that the now-modified store of numbers can be read and interpreted by humans.

## The stored-Program Computer

All computers consist of at least three fundamental types of structures needed to carry out the read-modify-write sequence:

- Storage.
- Arithmetic Logic Unit (ALU)
- Bus.

![Screen Shot 2019-08-26 at 3 44 25 PM](https://user-images.githubusercontent.com/24994818/63722253-6c1b2780-c818-11e9-9a82-91fe5fa09e1e.png)
Figure 1.3

## Storage 

To say that a computer **"reads"** and **"writes"** numbers implies that there is at least one number-holding structures that it reads from and writes to. All Computers have a place to put numbers -a storage are thtat can be read from and write to.

## Arithmethic Logic Unit (ALU)

It is the part where the computer performs artithmetic operations.

## Bus

The network of transmission lines for shuttling numbers around inside the computer is called Data Bus.
The instructions travel into the ALU via the Instruction Bus.



In reality, blocks of code and data are mixed together in main memory.

Prior to the invention of the first stored-program computer, all computing devices, from the abacus to the earliest electronic computer machines, had to be manipulated by an operator or group of operators who manually entered a particular sequence of commands each time they wanted to make a particular calculation.

## Refining the File-clerck Model.

All computers operate.

Example

1. obtain two numbers to be added (the input operands) from the data storage.
2. Add the numbers.
3. Place the results back into data storage.

Those three steps are carried out billions of times per second on a modern CPU.

## The register file

Most computers have a relatively small number of very fast data storage locations attached to the ALU, these locations ara called registers.

Backing to the example.

1. Obtain the two numbers to be added (the input operands) from the two source registers.
2. Add the numbers.
3. Place the results back in a destination register.

This three-step sequence is quite simple, but it's at the very core of how a microprocessor really works.

## The File-Clerck MOdel Revised and Expanded

We can think of main memory as a document storage room located on another floor and the registers as a small.
The clerk does not really know anything about the document storage room

## RAM: When Registers Alone Won't Cut It

Main Memory which in moder computers is always some type of random access memory (RAM), stores the data set on which the computer operates, and only a small portion of the data set at a time is moved to the registers for easy access from the ALLU.

In fact, the ALU an the registers are internal parts of the microprocessor, but main memory is a complete separeta component of the computer system that is connected to the processor via the Memory Bus. Transfering data between main memory and the registers via the memory bus takes a significant amount of time. This, if there were no registers and the ALU had to read data directly from the main memory for each calculation, computers would run very slowly. However, because the register enable the computer to store data near the ALU, where it can be access nearly instantaneously, the computer's computational speed is decoupled somewhat from the speed of main memory.

## Instructions are combined with data to produce results.


## The File-Clerk Model Revised and Expanded

we can think of main memory as a document storage room located on another floor and the registers as a small, personal filing cabinet where the file clerk places the papers on which he is currently working. The Clerk doesn not really know anything about the document storage room.

## A closer Look at the Code Stream: The Program

At the beginning did say, Code Stream: An ordered sequence of operatios, noiw operations becomes instructions, because not only operatations would do.

## General Instruction Types

These ordered lists of instructions are called programs. In modern RISC microprocessor, the act of moving data between memory and the registers is under the explicit control of the code stream, or program.


Modern RISC microprocessors the code stream is in charge to move data between memory and the registers. Operations are two main categories:

- Arithmethic instrucctions. (add, sub, mul, div)
- Memory-access instructions. (load, store)

To show you how memory-access and arithmetic operations work together within the context of the code stream.

## The DLW-1's Basic Architecture and Arithmetic Instruction Format

DLW1 

- ALU
- 4 registers: A,B,C y D
- Bank Main Memory 256 memory cells.
- The number that identifies an individual memory cell is called an **address**.

## The DLW-1's Arithmetic Instruction Format 

instruction source1, source2, destination

- instruction field: 	Specifies the type of operation.
- source1 field: 			It Tells the computer which registers hold the two numberes or Operands 
- source2 field:			It Tells the computer which registers hold the two numberes or Operands 
- destination field: 	it Tells the computer which register to place the result in.
 
## The DLW-1's Memory Instruction Format 

Now you need to tell the processor explicitly that you want to move the data in two specificy memory cells.

The **"filling"** operation is done via memory-access instruction called the load.

The load instruction loads the appropriate data from main memory into the appropriate registers.

### Instruction Format:

instruction source, destination.

For all memory accesses, the instruction field specifies the type of memory operation to be performed.

## Program Example

``` assembly
load #12, A
load #13, B
add A, B, C
store C, #14
```

## A Closer Look at Memory Accesses: Register vs Immediate

Until now, programmer knows the exact memory location of every number that he or she wants to lead and store. It presumes that in composing each program, the programmer has at his or her disposal a list of the contents of memoery cells #0 through #255
**Programmers need a flexible way to access memory, a way that does not requiere each memory access to specify numerically an exact memory address.**
Modern computers allow the contents of a register to be used as a memory address.

## Immediate Values

All of the arithmetic instructions so far have required two source registers as input. However, it is possible to replace one or both of the source registers with an explicit numerical value, called an immediate value. 

## Example.

``` assembly 
add A, 2, A		Add 2 to the contents of register A and place the resulñt back into A, overwriting whatever was there.
``` 

The #12 in the load instruction in line 1 of Program 1-1 is just an immediate value (regular whole number) prefixed by a # sign to let the computer know that this particular immediate value is a memory address that designates a cell in memory.

Memory addresses ar just regilar whole numbers that are specially marked with the # sign. The whole-number contest of a register, like D, could be construed by the computer as representating a memory address.

## Example:

``` assembly
load #D, A		Read the contents of D into A
load #12, B		Read the contents of #12 into B
add A, B, C		Add A and B, and store the result in C
store C, #14	Store what is inside of C into #14
```

| program 1-1 line 1 | Program 1-2 line 1 |
|--------------------|--------------------|
| load #12, A        | load #D, A         |

(# Sign of address)

The first lines of these programs are funcionally equivalent.

### Because memory addresses are just regular numbers, they can be stored in Memory cells as well as in registers.

The next program ilustrates the use of a memory address that is stored in another memory cell.

``` assembly
load #11, D		
load #D, A
load #13, B		
add A, B, C		
store C, #14	
```

* The firts instruction in Program 1-3 loads the number 12 from memory cell #11 into register D
* The second instruction then uses the content of D as a memory address to load register A into memory location #12.

### Why go to trouble of storing memory addresses in memory cells and then loading the addresses in memory cells and then loading the addresses from main memory into the registers before they are finally ready to be used to access memory again ? Is not this an overly complicated way to do thins ?

When the programmers used with the register-relative addressing technique described next they make managing code and data traffic between the processor and massive amounts of main memory much less complex.

## Register-Relative Addressing


