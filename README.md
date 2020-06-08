# INSIDE THE MACHINE

1. [Introduction](https://github.com/c4arl0s/InsideTheMachine#1-introduction) 
2. [Basic Computing Concepts](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts) 
3. [The Mechanics of Program Execution](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 
4. [Pipelined Execution](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35) 
5. [Pipelined Execution]() 
6. [PowerPC Processors: 600 Series, 700 Series, and 7400]()
7. [Intel’s Pentium 4 vs. Motorola’s G4e: Approaches and Design Philosophies]()
8. [Intel’s Pentium 4 vs. Motorola’s G4e: The Back End]()
9. [64-Bit Computing and x86-64]()
10. [The G5: IBM’s PowerPC 970]()
11. [Understanding Caching and Performance]()
12. [Intel’s Pentium M, Core Duo, and Core 2 Duo]()
13. [Bibliography and Suggested Reading]()


# 1. [INTRODUCTION](https://github.com/c4arl0s/InsideTheMachine#inside-the-machine)

# 2. [BASIC COMPUTING CONCEPTS](https://github.com/c4arl0s/InsideTheMachine#inside-the-machine)

- [The Calculator Model of Computing](https://github.com/c4arl0s/InsideTheMachine#--the-calculator-model-of-computing)
- [The File-Clerk Model of Computing](https://github.com/c4arl0s/InsideTheMachine#--the-file-clerk-model-of-computing)
	* [The Stored-Program Computer](https://github.com/c4arl0s/InsideTheMachine#-the-stored-program-computer)
	* [Refining the File-Clerk Model](https://github.com/c4arl0s/InsideTheMachine#-refining-the-file-clerk-model)
- [The Register File](https://github.com/c4arl0s/InsideTheMachine#--the-register-file)
- [RAM: When Registers Alone Won’t Cut It](https://github.com/c4arl0s/InsideTheMachine#--ram-when-registers-alone-wont-cut-it)
	* [The File-Clerk Model Revisited and Expanded](https://github.com/c4arl0s/InsideTheMachine#-the-file-clerk-model-revisited-and-expanded) 
	* [An Example: Adding Two Numbers](https://github.com/c4arl0s/InsideTheMachine#-an-example-adding-two-numbers)
- [A Closer Look at the Code Stream: The Program](https://github.com/c4arl0s/InsideTheMachine#--a-closer-look-at-the-code-stream-the-program)
	* [General Instruction Types](https://github.com/c4arl0s/InsideTheMachine#-general-instruction-types)
	* [The DLW-1’s Basic Architecture and Arithmetic Instruction Format](https://github.com/c4arl0s/InsideTheMachine#-the-dlw-1s-basic-architecture-and-arithmetic-instruction-format)
  * [The DLW-1's Arithmetic Instructions Format]()
  * [The DLW-1's Memory Instruction Forma]()
  * [An example DLW-1 Program]()
- [A Closer Look at Memory Accesses: Register vs. Immediate](https://github.com/c4arl0s/InsideTheMachine#--a-closer-look-at-memory-accesses-register-vs-immediate)
	* [Immediate Values](https://github.com/c4arl0s/InsideTheMachine#-immediate-values)
	* [Register-Relative Addressing](https://github.com/c4arl0s/InsideTheMachine#-register-relative-addressing)

# 3. [THE MECHANICS OF PROGRAM EXECUTION](https://github.com/c4arl0s/InsideTheMachine#inside-the-machine)

- [Opcodes and Machine Language](https://github.com/c4arl0s/InsideTheMachine#--opcodes-and-machine-language)
	* [Machine Language on the DLW-1](https://github.com/c4arl0s/InsideTheMachine#-machine-language-on-the-dlw-1)
	* [Binary Encoding of Arithmetic Instructions](https://github.com/c4arl0s/InsideTheMachine#-binary-encoding-of-arithmetic-instructions)
	* [Binary Encoding of Memory Access Instructions](https://github.com/c4arl0s/InsideTheMachine#-binary-encoding-of-memory-access-instructions)
	* [Translating an Example Program into Machine Language](https://github.com/c4arl0s/InsideTheMachine#-translating-an-example-program-into-machine-language) 
- [The Programming Model and the ISA](https://github.com/c4arl0s/InsideTheMachine#--the-programming-model-and-the-isa) 
	* [The Programming Model](https://github.com/c4arl0s/InsideTheMachine#-the-programming-model)
	* [The Instruction Register and Program Counter](https://github.com/c4arl0s/InsideTheMachine#-the-instruction-register-and-program-counter) 
	* [The Instruction Fetch: Loading the Instruction Register](https://github.com/c4arl0s/InsideTheMachine#-the-instruction-fetch-loading-the-instruction-register) 
	* [Running a Simple Program: The Fetch-Execute Loop](https://github.com/c4arl0s/InsideTheMachine#-running-a-simple-program-the-fetch-execute-loop) 
- [The Clock](https://github.com/c4arl0s/InsideTheMachine#--the-clock)
- [Branch Instructions](https://github.com/c4arl0s/InsideTheMachine#--branch-instructions) 
	* [Unconditional Branch](https://github.com/c4arl0s/InsideTheMachine#-unconditional-branch) 
	* [Conditional Branch](https://github.com/c4arl0s/InsideTheMachine#-conditional-branch) 
- [Excursus: Booting Up](https://github.com/c4arl0s/InsideTheMachine#--excursus-booting-up) 


# 4. [PIPELINED EXECUTION 35](https://github.com/c4arl0s/InsideTheMachine#inside-the-machine)

- [The Lifecycle of an Instruction](https://github.com/c4arl0s/InsideTheMachine#--the-lifecycle-of-an-instruction)
- [Basic Instruction Flow](https://github.com/c4arl0s/InsideTheMachine#--basic-instruction-flow)
- [Pipelining Explained](https://github.com/c4arl0s/InsideTheMachine#--pipelining-explained)
- [Applying the Analogy](https://github.com/c4arl0s/InsideTheMachine#--applying-the-analogy)
	* [A Non-Pipelined Processor](https://github.com/c4arl0s/InsideTheMachine#-a-non-pipelined-processor) 
	* [A Pipelined Processor](https://github.com/c4arl0s/InsideTheMachine#-a-pipelined-processor)
	* [The Speedup from Pipelining](https://github.com/c4arl0s/InsideTheMachine#-the-speedup-from-pipelining) 
	* [Program Execution Time and Completion Rate](https://github.com/c4arl0s/InsideTheMachine#-program-execution-time-and-completion-rate) 
	* [The Relationship Between Completion Rate and Program Execution Time](https://github.com/c4arl0s/InsideTheMachine#-the-relationship-between-completion-rate-and-program-execution-time)
	* [Instruction Throughput and Pipeline Stalls](https://github.com/c4arl0s/InsideTheMachine#-instruction-throughput-and-pipeline-stalls)
	* [Instruction Latency and Pipeline Stalls](https://github.com/c4arl0s/InsideTheMachine#-instruction-latency-and-pipeline-stalls)
	* [Limits to Pipelining](https://github.com/c4arl0s/InsideTheMachine#-limits-to-pipelining)


# 1. [INTRODUCTION](https://github.com/c4arl0s/InsideTheMachine#inside-the-machine)

Inside the Machine is an introduction to computers that is intended to fill the gap that exist between classic but more challenging introductions to computer architecture.

# 2. [BASIC COMPUTING CONCEPTS](https://github.com/c4arl0s/InsideTheMachine#inside-the-machine)

Modern computers come in all shapes and sizes, and they aid us in a million different types of tasks ranging from the serious, like air traffic control and cancer research, ti the not-so-serious, like computer gaming.

At the heart of the modern computers is the **microprocessor** -also commonly called **central processing unit (CPU)** - a tiny, square silver of silicon that is etched with a microscopic network of gates and channels through which electricity flows. This netwoork of gates (transistors) and channels (wires or lines) is a very small version of the kind circuitry that we have all seen when cracking open a television remote or an old radio. In short, the microprocessor is not just the "heart" of a modern computer - It is a computer and of itself

# - [The Calculator Model of Computing](https://github.com/c4arl0s/InsideTheMachine#--the-calculator-model-of-computing)

A computer takes a stream of instructions (code) and a stream of data as input, and it produces a stream of results as output.

![Screen Shot 2019-08-26 at 3 43 05 PM](https://user-images.githubusercontent.com/24994818/63722147-35dda800-c818-11e9-9e40-599208836737.png)

Figure 1-1 is my own variation on the traditional way of representing a processor's arithmetic logic unit (ALU)

I have depicted code and data streams entering the top ports and a results stream leaving the bottom port.

![Screen Shot 2020-05-29 at 23 47 12](https://user-images.githubusercontent.com/24994818/83319751-bf3a6480-a206-11ea-83f7-6536b64b33c5.png)

The kind of simple calculation describe above represents the sort of thing that we intuitive think computers do.

# - [The File-Clerk Model of Computing](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

The "Calculator" model of computing, while useful in many aspects, is not the only or even the best way to think about what computers do. As an alternative, consider the following definition of a computer:

A computer is a device that shuffles numbers around from place to place, reading, writing, erasing, and rewriting different numbers in different locations according to a set of inputs, a fixed set of rules for processing those inputs, and the prior history of all the inputs that the computer has seen since it was last reset, until a predefined set of criteria are met that case the computer to halt.

We might, after Richard Feynman, call this idea of a computer as a reader, writer, and modifier of numbers the "file-clerk" model of computing (as opposed to the aforementioned calculator model). In the File-clerk model, the computer access a large (theoretically infinite) store of sequentially arranged numbers fr the purpose of altering that store to achieve a desired result. Once this desired result is achieved, the computer halts so that the now-modified store of numbers can be read and interpreted by humans.

The file-clerk mode of computing might not initially strike you as all that useful, but as this chapter progresses, you will begin to understand how important it is. This way of looking at computers is powerful because it emphasizes the end product of computation rather than the computation itself. After all, the purpose of computers is not just to compute in the abstract, but to produce the usable results from a given data set.

Those who have studied computer science will recognize in the preceding description the beginnings of a discussion of a Turing Machine. The Touring machine is, however, too abstract for our purposes here, so I won't actually describe one. The description that I develop here sticks closer to the classic **Reduced Instruction Set Computing (RISC) load-stored model, where the computer is "Fixed" along with the storage. The TToring model of a computer as a movable read-write head (with a state table) traversing a linear "tape" is too far from real-life hardware organization to be anythin but confusing in this discussion.**

In other words, what matters in computing is not that you did some math, but that you started with a body of numbers, applied a sequence of operations to it, and got a body of results. Those results could, again, represent pixel values for a rendered scene or an environmental snapshot in a weather simulation. Indeed the idea that computer is a device that transforms one set of numbers into another should be intuitively obvious to anyone who has ever used a Photoshop filter. Once we understand computers not in terms of math they do, but in terms of the numbers they move and modify, we can begin to get a fuller picture of how they operate.

In a nutshell, a computer is a device that reads, modifies, and writes sequences of numbers. These three functions - read, modify, and write- are the three most fundamental functions that a computer performs, and all the machine's component are designed to aid in carrying them out. This read-modify-write sequence is actually inherent in the three central bullet points of our initial file-clerk definition of a computer. Her is a sequence mapped explicitly onto the file-clerk definition:

> A computer is a device that shuffles numbers around from place to place, reading, writing, erasing, and rewriting different numbers in different locations according to a set of inputs [read], a fixed set of rules for processing those inputs [modify], and the prior history of all inputs that the computer has seen since it was last reset [write], until a predefined set of criteria are met that cause the computer to halt.

That sums up what a computer does. And, in fact, that's all a computer does. Whether you are playing a game or listening to music, everything that is going on under the computer's hood fits into this model.
---
**Note** 
All of this is fairly simple so far, and I have even seen a bit repetitive with the explanations to drive home the basic read-modify-write structure of all computer operations. It is important to grasp this structure in its simplicity, because as we increase our computing model's level of complexity, we will see this structure repeated at very level.
---

# 	* [The Stored-Program Computer](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

All computers consist of at least three fundamental types of structures needed to carry out the read-modify-write sequence:

- Storage.
- Arithmetic Logic Unit (ALU)
- Bus.

The data enters the ALU from a special storage area, but where does the code stream come from? 
One might imagine that it comes from the keypad of some person standing at the computer and entering a sequence of instructions, each of which is then transmitted to the code input port of the ALU, or perhaps that the code stream is a prerecorded list of instructions that is fed into the ALU, one instruction at a time, by some manual or automated mechanism. Figure 1-3 depicts the code stream as a prerecorded list of instructions that is stored in a special storage area just like the data stream, and modern computers do store the code stream in just such manner.

![Screen Shot 2020-05-31 at 19 39 09](https://user-images.githubusercontent.com/24994818/83366707-76092280-a376-11ea-87d7-9dc5da2c0568.png)

---
**Note**
More advance readers might notice that in figure 1-3 (and in figure 1-4 later) I have separated the code and data in main memory after the manner of a Harvard architecture level-one cache. In reality, blocks of code and data are mixed together in main memory, but for now I have chosen to illustrate them as logically separated.
---

The modern computer's ability to store and reuse prerecorded sequences of commands makes it fundamentally different from the simpler calculating machines that preceded it. Prior to the invention of the first **stored-program computer**, all computing devices, from the abacus to the earliest electronic computing machines, had to be manipulated by an operator or group of operators who manually entered a particular sequence of commands each time they wanted to make a particular calculation. In contrast, modern computers store and reuse such command sequences, and as such they have a level of flexibility and usefulness that sets them apart from everything that has come before.

In the rest of this chapter, you will get a first-hand look at the many ways that the stored-program concept affects the design and capabilities of the modern computer.


# 	* [Refining the File-Clerk Model](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

All computers operate.

Example

1. obtain two numbers to be added (the input operands) from the data storage.
2. Add the numbers.
3. Place the results back into data storage.

Those three steps are carried out billions of times per second on a modern CPU.

To return to our File-clerck analogy, a computer is like a file clerck who sits at his desk all day waiting for messages from his boss. Eventually, the boss sends him a message telling him a message telling him to perform a calculation, and where in his personal filling cabinet the necessary numbers are located. So the clerk first retrieves the numbers from his filing cabinet, then performs the calculation, and finally places the result back into the filing cabinet. It is boring, mindless, repetitive task that is repeated endlessly, day in day out, which is precisely why we have invented a machine that can do it efficiently and not complain.


# - [The Register File](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

Since numbers must first be fetched from the storage before they can be added, we want our data storage a space to be as fast as possible so that the operation can be carried out quickly. Since the ALU is the part of the processor that does the actual addition. We would like **to place the data storage as close as possible the ALU** so it can read the operands almost instantaneously. However, practical considerations, such as CUPs limited surface area, constrain the size of the storage area that we can stick next to the ALU. This fast data storage locations attached to the ALU. These storage locations called **registers**, and the first x86 computers only had eight of them to work with. These **registers**^, which are arrayed in a storage structure called a **register file**, stored only a small subset of the data that the code stream needs (and we will talk about where the rest of that data lives shortly).

Building on our previous,, three.step description of what goes on when a computer's ALU is commanded to add two numbers, we can modify it as follows. To execute an **add** instruction, the ALU must perform these steps:

1. Obtain the two numbers to be added (the input operands= from two source registers.ç
2. Add the numbers.
3. Place the results back in a **destination register**

For a concrete example, let's look at addition on a simple computer with only four registers, named A,B,C,D. Suppose each of these registers contains a number, and we want to add the contents of two registers together and overwrite the contents of a third register with the resulting sum, as in the following operation:

Code				Comments
A + B = C		Add the contents of register A and B, and place the result in C, overwriting whatever was there.

Upon receiving and instruction commanding it to perform this addition operation, the ALU in our simple computer would carry out the following three familiar steps:

1. Read the contents of register A and B
2. Add the contents of A and B
3. Write the result to register C

You should recognize these three steps as a more specific form of the read-modify-write sequence from earlier, where the generic modify steps is replaced with an addition operation.

This three-step sequence is a quite simple, but it is at the very core of how a microprocessor really works. In fact, if you glance ahead to Chapter 10 discussion of the PowerPC 9700s pipeline, you will see that it actually has separate stages for each of these three operations: stage 12 is the register read step, stage 13 is the actual execute step, and stage 14 i the write-back step. (dont worry if you dont know what a pipeline is, because that is the topic for chapter 3). So the 970's ALU reads two operands from the register file, adds them together, and writes the sum back to the register file. If we were to stop our discussion right here, you would already understand the three core stages of the 970's main integer pipeline- all the other stages are either just preparation to get to this point or they are cleanup work after it.


# - [RAM: When Registers Alone Won’t Cut It](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

Obviously, four (or even eight) registers are not even close to the theoretically infinite storage space I mentioned earlier in this chapter. In order to make a viable computer that does useful work. You need to be able to store very large data sets. This is where the computer's **main memory** comes in. Main memory, which in modern computers is always some type of **random access memory (RAM)**, stores the data set on which the computer operates, and only a small portion of that data set a time is moved to the registers and only a small portion of that data set at a time is moved to the registers for easy access from the **ALU** (as shown in Figure 1-4).



Figure 1-4 gives only the slightest indication of it, but **main memory** is situated quite a bit farther away from the **ALU** than are the registers. In fact, the ALU and the registers are internal parts of the microprocessor, but main memory is a completely separate component of the computer system that is connected to the processor via the **memory bus**. Transfering data between main memory and the registers via the memory bus takes a significant amount of time. Thus, if there were no registers and the ALU had to read data directly from main memory for each calculation, computers would run very slowly. However, because the registers enable the computer to store data near the ALU, where it can be accessed nearly instantaneously, the computer's computational speed is **decoupled** somewhat from the speed of **main memory**. 

We will discuss the problem of memory access speeds and computational performance in more detail in [Chapter 11](), when we talk about [caches]().

![Screen Shot 2020-06-03 at 11 22 31](https://user-images.githubusercontent.com/24994818/83663511-7f6cd780-a58e-11ea-85bf-c73da8f4985b.png)  

# 	* [The File-Clerk Model Revisited and Expanded](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts) 

To return to our file-clerk metaphor, we can think of **main memory** as a document storage room located on another floor and the registers as a small, personal filling cabinet where the file clerk places the papers on which he is currently working. The clerk does not really know anything about the document storage room. -what it is or where it is located- because his desk and his personal filing cabinet are all he concerns himself with. For documents that are in the storage room, there is another office worker, the office secretary, whose job it is to locate files in the storage room and retrieve them for the clerk.

This secretary represents a few different units within the processor, all of which we will meet Chapter 4. For now, suffice it to say that when the boss wants the clerk to work on a file that is not in the clerk's personal filing cabinet, the secretary must first be ordered, via a message from the boss, to retrieve the file from the storage room and place it in the clerk's cabinet so that the clerk can access it when he gets the order to begin working on it.

# 	* [An Example: Adding Two Numbers](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)
To translate this office example into computing terms, let's look at how the computer uses main memory, the register file, and the ALU to add two numbers.

To add two numbers stored in main memory, the computer must perform these steps.

1. Load the two operands from main memory into the two source registers.
2. Add the contents of the source registers and place the results in the destination register, using the ALU. To do so, the ALU must perform these steps.
	A. Read the contents of registers A and B into the ALUU's input ports.
	B. Add the contents of A and B in the ALU.
	C. Write the result to regiter C via the ALU's output port.
3. Store the contents of the destination register in **main memory**.

Since steps 2a, and 2c all take a trivial amount of time to complete, relative to steps 1 and 3, we can ignore them. Hence our addition looks like this:

1. Load the two operands from main memory into the two source registers.
2. Add the contents of the source registers, and place the results in the destination register, using the ALU.
3. Store the contents of the destination register in main memory.

The existence of **main memory** means that the user -the boss in our filing-clerk analogy- must manage the flow of information between main memory and the CPU's registers. This means that the user must issue instructions to more than just the processor's ALU; he or she must also issue instructions to the parts of the CPU that **handle memory traffic**. Thus, the preceding three steps are representative of the kinds of instructions you find when you take a close look at the code stream.

# - [A Closer Look at the Code Stream: The Program](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

At the beginning pf this chapter, I defined the **code stream**  consisting of **"an ordered sequence of operations** and this definition is fine as far as it goes. But in order to dig deeper, we need a more detailed picture of what the code stream is an how it woks.

The term **operations** suggests  series of simple arithmetic operations like addition or substraction, but the **code stream** consist of more than just arithmetic operations. Therefore, it would be better to say that **the code stream** consist of **an ordered sequence of instructions**. Instructions, generally speaking, are commands that tell the whole computer - not just the ALU, but simple parts of the machine -exactly what actions to perform. As we have seen, a computer's list of potential actions encompasses more than just simple arithmetic operations.

# 	* [General Instruction Types](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

Instructions are grouped into ordered lists that, when taken as a whole, tell the different parts of the computer how to work together to perform a specific task, like grayscaling and image or playing a file media. These ordered lists of instructions are called **programs**, and they consist of a few basic types of instructions.

In modern RISC microprocessors, the act of moving data between memory and the registers is under the explicit control of the code stream or program. So if a programmer wants to add two numbers that are located in main memory and then store the result back in main memory, he or she must write a list of instructions (a program) to tell the computer exactly what to do. The program must consist of:

	* a load instruction to move the two numbers from memory into the registers.
	* an add instruction to tell the ALU to add the two numbers.
	* a store instruction to tell the computer to place the result of the addition back into memory, overwriting whatever was previously there.

These operations fall into two main categories:

### Arithmetic Instructions

These instructions tell the ALU to perform an arithmetic calculation (for example add, sub, mul, div)

### Memory-access instructions

These instructions tell the parts of the processor that deal with main memory to move data from and to main memory (for example load and store)

We will discuss a third type of instruction, the branch instruction, shortly. Branch instructions are technically a special type of memory-access instructions, but they access code storage instead instead of data storage. Still, it is easier to treat branches as a third category of instruction.

The **arithmetic instruction** fits with our calculator metaphor and is the type of instructions most familiar to anyone who is worked with computers. Instructions, like integer and floating-point addition, subtraction, multiplication, and division all fall under the general category.

In order to simplify the discussion and reduce the number of terms, I am temporarily including logical operations like AND, OR, NOT, NOR,and so on, under the general heading of arithmetic instructions. The difference between arithmetic and logical operations will be introduced in Chapter 2

The **memory-access instructions** is just as important as the arithmetic instruction, because without access main memory's data storage regions, the computer would have no way to get data into or out of the register file. 

To show you how **memory-access** and arithmetic operations work together within the context of the code stream, the remainder of this chapter will use a series of increasingly detailed examples. All of the examples are based on a simple, hypothetical computer, which I will call the DLW-1 [^2]

# 	* [The DLW-1’s Basic Architecture and Arithmetic Instruction Format](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

The DLW-1 microprocessor consist of an ALU (along with a few other units that I will describe later) attached to four registers, named A,B,C,D for convenience. The **DLW-1** is attached to a bank of main memory that is laid out as a line of 256 memory cells, numbered #0 to #255 (The number that identifies an individual memory cell is called an **address**)

# - [The DLW-1's Arithmetic Instructions Format]()

All of the DLW-10's arithmetic instructions are in the following **instruction format**:

```assembly
instruction sourceOne, sourceTwo, destination
```

There are four parts to this instruction format, each of which is called a **field**. The **instruction** field specifies the type of operation being performed (for example, an addition, a subtraction, a multiplication, and so on.) The two source fields tell the computer which registers hold the two numbers being operated on, or the **operands**. Finally, the **destination** field tells the computer which register to place the result in.

As a quick illustration, an addition instruction that adds the numbers in register A and B (the two source registers) and places the result in register C (the destination register) would look like this:

```assembly
add A, B, C 
```

Add the contents of registers A and B and place the result in C, overwriting whatever was previously there.

[^2]: DLW in honor of the DLX architecture used by Hennessy and Patterson in their books on computer architecture.

# - [The DLW-1's Memory Instruction Forma]()

In order to get the process to move two operands from main memory into the source registers so they can be added, you need to tell the process explicitly that you want to move the data in two specific memory cells to two specific registers. This **"filing"** operation is done via a **memory-access** instruction called the **load**.

All of the memory-access instructions for the DLW-1 have the following instruction format:

```assembly
instruction source, destination
```

For all memory access, the instruction field specifies the type of memory operation to be performed (either a load or a store). In he case of a load, the source field tells the computer which memory address to fetch the data from, while the destination field specifies which register to put in. Conversely, in the case of a **store**, the source field tells the computer which register to take the data from, and the destination field specifies which memory address to write the data to.

# - [An example DLW-1 Program]()

Now consider program 1-1, which is a piece of DLW-1 code. Each of the lines in the program must be executed in sequence to achieve the desired result.

```assembly
1	load #12, A		; Read the contents of memory cell #12 into register A.
2 load #13, B		; read the contents of memory cell #13 into register B.
3 add A, B, C		; add the numbers in registers A and B and store the result in C
4 store C, #14	; Write the result of the addition from register C into memory cell #14
```

Suppose the main memory looked like the following before running Program 1-1

--------
#14	| 3
#13 | 2
#12 | 6
#11 | 12
--------

After doing our addition and storing the results, the memory would be changed so that the contents of cell #14 would be overwritten by the sum of cells #12 and #13, as shown here:

--------
#14	| 8
#13 | 2
#12 | 6
#11 | 12
--------


# - [A Closer Look at Memory Accesses: Register vs. Immediate](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

The examples so far presume that the programmer knows the exact memory location of every number that he or she wants to load and store. In other words, it presumes that in composing each program, the programmer has at his or her disposal a list of the contents of memory cells #0 through #255.

While such an accurate snapshot of the initial state of main memory may be feasible for a small example computer with only 256 memory locations, such snapshots almost never exist in the real world. Real computers have billions of possible locations in the which data can be stored, so programmers need more flexible way to access memory, a way that does not require each memory access to specify numerically an exact memory address.

Modern computers allow the **contents** of a register to be used as a memory address, a move that provides the programmer with the desired flexibility. But before discussing the effects of this move in more detail, let's take one more look at the basic **add** instruction.

# 	* [Immediate Values](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)
# 	* [Register-Relative Addressing](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

# 3. [THE MECHANICS OF PROGRAM EXECUTION](https://github.com/c4arl0s/InsideTheMachine#inside-the-machine)

# - [Opcodes and Machine Language](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution)
# 	* [Machine Language on the DLW-1](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution)
# 	* [Binary Encoding of Arithmetic Instructions](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution)
# 	* [Binary Encoding of Memory Access Instructions](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution)
# 	* [Translating an Example Program into Machine Language](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 
# - [The Programming Model and the ISA](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 
# 	* [The Programming Model](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution)
# 	* [The Instruction Register and Program Counter](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 
# 	* [The Instruction Fetch: Loading the Instruction Register](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 
# 	* [Running a Simple Program: The Fetch-Execute Loop](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 
# - [The Clock](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution)
# - [Branch Instructions](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 
# 	* [Unconditional Branch](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 
# 	* [Conditional Branch](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 
# - [Excursus: Booting Up](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 


# 4. [PIPELINED EXECUTION 35](https://github.com/c4arl0s/InsideTheMachine#inside-the-machine)

# - [The Lifecycle of an Instruction](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)
# - [Basic Instruction Flow](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)
# - [Pipelining Explained](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)
# - [Applying the Analogy](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)
# 	* [A Non-Pipelined Processor](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35) 
# 	* [A Pipelined Processor](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)
# 	* [The Speedup from Pipelining](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35) 
# 	* [Program Execution Time and Completion Rate](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35) 
# 	* [The Relationship Between Completion Rate and Program Execution Time](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)
# 	* [Instruction Throughput and Pipeline Stalls](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)
# 	* [Instruction Latency and Pipeline Stalls](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)
# 	* [Limits to Pipelining](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)










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


