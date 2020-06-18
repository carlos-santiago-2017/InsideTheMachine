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
      + Arithmetic Instructions
      + Memory-access instructions
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
     * [The Load Instruction]()
     * [The store instruction]()
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

### [Arithmetic Instructions]()

These instructions tell the ALU to perform an arithmetic calculation (for example add, sub, mul, div)

### [Memory-access instructions]()

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
1 load #12, A		; Read the contents of memory cell #12 into register A.
2 load #13, B		; read the contents of memory cell #13 into register B.
3 add A, B, C		; add the numbers in registers A and B and store the result in C
4 store C, #14	; Write the result of the addition from register C into memory cell #14
```

Suppose the main memory looked like the following before running Program 1-1

```txt
---------
| #14	| 3
| #13 | 2
| #12 | 6
| #11 | 12
---------

After doing our addition and storing the results, the memory would be changed so that the contents of cell #14 would be overwritten by the sum of cells #12 and #13, as shown here:

```txt
---------
| #14	| 8
| #13 | 2
| #12 | 6
| #11 | 12
---------
```

# - [A Closer Look at Memory Accesses: Register vs. Immediate](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

The examples so far presume that the programmer knows the exact memory location of every number that he or she wants to load and store. In other words, it presumes that in composing each program, the programmer has at his or her disposal a list of the contents of memory cells #0 through #255.

While such an accurate snapshot of the initial state of main memory may be feasible for a small example computer with only 256 memory locations, such snapshots almost never exist in the real world. Real computers have billions of possible locations in the which data can be stored, so programmers need more flexible way to access memory, a way that does not require each memory access to specify numerically an exact memory address.

Modern computers allow the **contents** of a register to be used as a memory address, a move that provides the programmer with the desired flexibility. But before discussing the effects of this move in more detail, let's take one more look at the basic **add** instruction.

# 	* [Immediate Values](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

All of the arithmetic instructions so far have required two source registers as input. However, it is possible to replace one or both of the source registers with an explicit numerical value, called an **immediate value**. For instance, to increase whatever number is in register A by 2, we don't need to lead the value 2 into a second source register, like B, from some cell in main memory that contains that value. Rather, we can just tell the computer to add 2 to A directly, as follows.

```assembly
add A, 2, A ; add 2 to the contents of register A and place the result back into A, overwriting whatever was there.
```

I have actually been using immediate values all along in my examples, but just not in any arithmetic instructions. In all of the preceding examples, each load and store uses an immediate value in order to specify a memory address.

So the #12 in the load instruction in line 1 of Program 1-1 is just an immediate value (a regular whole number) prefixed by a # sign to let the computer know that this particular immediate value is a memory address that designates a cell in memory.

Memory address are just regular whole numbers that are specially marked with the # sign. Because they are regular whole numbers, the can be stored in registers- and stored in memory- just like any other number.

Thus, the whole number contents of a register, like D, could be construed by the computer as representing a memory address.

For example, say that we have stored the number 12 in register D, and that we intend to use the contents of D as the address of a memory cell in Program 1-2

```assembly
1 load #D, A   ; read the contents of the memory cell designated by the number stored in D (where D=12) into register A
2 load #13, B  ; read the contents of memory cell #13 into register B.
3 add A, B, C  ; add the numbers in register A and B and store the result in C
4 store C, #14 ; write the result of the addition from register C into memory cell #14
```

Program 1-2 is essentially the same as program 1-1, and given the same input, it yields the same results. The only difference is in line 1:

Program 1-1, Line 1
```assembly
load #12, A
```

Program 1-2, Line 1
```assembly
load #D, A
```

Since the content of D is the number 12, we can tell the computer to look in D for the memory cell address by substituting the register name (this time marked with a # sign for use as an address) for the actual memory cell number inn line 1's load instruction. Thus, the first lines of Program 1-1 and 1-2 are functionally equivalent.

This same trick words for **store** instructions, as well. For example, if we place the number 14 in D we can modify the **store** command in line 4 of Program 1-1 to read as follows: **store C, #D**. Again, this modification would not change the program's output.

Because memory addresses are just regular numbers, they can be stored in memory cells as well as in registers. Program 1-3 illustrates the use of a memory address that is stored in another memory cell. If we take the input for Program 1-1 and apply it to Program 1-3, we get the same output as if we would just run Program 1-1 without modifications:

```assembly
1 load #11, D  ; read the contents of memory cell #11 into D
2 load #D, A   ; read the contents of memory cell designated by the number in D (where D = 12) into register A.
3 load #13, B  ; read the contents of memory cell #13 into register B
4 add A, B, C  ; add the numbers in regisers A and B and store the result in C
5 store C, #14 ; write the result in C, into memory cell #14.
```

The first instruction in Program 1-3 loads the number 12 from memory cell #11 into register D. The second instruction then uses the content of D (which is the value 12) as a memory address in order to load register A into memory location #12.

But why go to the trouble of storing memory address in memory cells and the loading the addresses from main memory into the registers before they are finally ready to be used to access memory again ? Is not this an overly complicated way to do thins ? 

Actually, these capabilities are designed to make programmer's live easier, because when used with the register-relative addressing technique described next they make managing code and data traffic between the processor and massive amount of main memory much less complex.

# 	* [Register-Relative Addressing](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

In real world programs, **loads** and **stores** most often use **register-relative addressing**, which is a way of specifying memory addresses relative to a register that contains a fixed **base address**

For example, we have been using **D** to store memory addresses, so let`s say that on the DLW-1 we can assume that, unless it is explicitly told to do otherwise, the operating system always loads the starting address (or base address) of a program's data segment into D. Remember that code and data are logically separated in main memory, and that data flows into the processor from a data storage are, while code flows into the processor from a special code storage are. Main memory itself is just one long row of undifferentiated memory cells, each one **byte** in width, that store numbers. The computer carves up this long row of bytes into multiple segments, some of which store code and some of which store data.

A **data segment** is a block of contigous memory cells that a program stores all of its data in, so if a programmer knows a data segment's starting address (**base address**) in memory, he or she can access all of the other memory locations in that segment using this formula:

base address + offset

where **offset** is the distance in bytes of the desired memory location from the data segment`s base address.

Thus, **load** and **store** instructions in DLW-1 assembly would normally look something like this:

```assembly
load #(D+108), A  ; Read the contents of the memory cell at location #(D+108) into A.
store B, #(D+108) ; write the contents of B into the memory cell at locations #(D+108)
```

In the case of the **load**, the processor takes the number in D, which is the base address of the data segment, adds 108 to it, and uses the result as the load's destination memory address. The **store** works in the exact same way.

Of course, this technique requires that a quick addition operation (called an **address calculation**) be part of the execution of the **load** instruction, so this is why the **load-store units** on modern processors contain very fast integer addition hardware. (As we will learn in Chapter 4, the **load-store** unit is the execution unit resposible for executing **load** and **store** instructions, just like the arithmetic-logic unit is responsible for executing arithmetic instructions.)

By using register-relative addressing instead of **absolute addressing** (in which memory addresses are given as immediate values), a programmer can write programs without knowing the exact location of data in memory. All the programmer needs to know is which register the operating system will place the data segment's base address in, and he or she can do all memory accesses relative to the **base address**. In situations where a programmer uses absolute addressing, when the operating system loads the program into memory, all data seg ment's actual location in memory.

Because both memory addresses and regular integer numbers are stored in the same registers, these registers are called **general-purpose registers** (GPRs) On the DLW-1, A, B, C and D are all GPRs.


# 3. [THE MECHANICS OF PROGRAM EXECUTION](https://github.com/c4arl0s/InsideTheMachine#inside-the-machine)

Now that we understand the basics of computer organization, it is time to take a closer look at the nuts and bolds of how stored programs are actually executed by the computer. To that end, this chapter will cover core programming concepts like machine language. To that end, this chapter will cover core programming concepts like machine language, the programming model, the instruction set architecture, branch instructions, and the fetch-execute loop.

# - [Opcodes and Machine Language](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution)

If you have been following the discussion so far, it should not surprise you to lear that both **memory addresses** and **memory instructions** are **ordinary numbers** that can b stored in memory. Al of the instructions in a program like Program 1-1 are represented inside the computer as strings of numbers. Indeed, a program is one long string of numbers stored in a series of memory location.

How is a program like Program 1-1 rendered in numerical notation so that it can be stored in memory and executed by the computer ?. The answer is simpler than you might think.

As you may already know, a computer actually only understand 1s and 0s (or "high" and "low" electric voltages), not English words like **add, load and store**, or letters and base-10 numbers like A, B, or 12. In order for the computer to run a program, therefore, all of its instructions must be rendered in **binary notation**. Think of translating English words into Morse code's dots and dashes and you will have some idea of what I am talking about.

# 	* [Machine Language on the DLW-1](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution)

The translation of programs of any complexity into this binary-based **machine language** is a massive undertaking that's meant to be done by a computer, but I will show you the basics of how it works so you can understand what is going on. The following example is simplified, but useful nonetheless.

The english words in a program, like **add, load ad store**, are **mnemonics** (meaning the are ease for people to remember), and they are all mapped to strings of binary numbers, called **opcodes**, that the computer can understand. Each **opcode** designates a different operation that the processor can perform. Table 2-1 maps each of the mnemonics used in Chapter 1 to a **3-bit opcode** for the hypothetical DLW-1 microprocessor. We can also map the four register names to a **2-bit binary codes**, as shown in Table 2-2


table 2-1 Mapping of Mnemonics to Opcodes for the DLW-1

| Mnemonic  | Opcode   |
| --------  | -------- |
| add       | 000      |
| sub       | 001      |
| load      | 001      |
| store     | 011      |

Table 2-2 Mapping of Registers to binary Codes for the DLW-1

| Register| Binary code |
| ------  | ----------- |
| A       | 00          |
| B       | 01          |
| C       | 10          |
| D       | 111         |

The binary valyes representing both the opcodes and the register codes are arranged in one of a number of **16-bits** (or 2-byte) formats to get a complete **machine language instruction** which is a binary number that can be stored in RAM and used by the processor.

---
**Note**
Because programmer-written instructions must be translated into binary codes before a computer can read them, it is common to see programs in any format -binary, assembly, or a high-level language like BASIC or C, referred to generically as "code" or "codes" When referring to programs written in assembly, binary or C language. Programmers also often descrive the act of programming as "writing code" or "coding", I have adopted this terminology in this book, and will henceforth use the term "code" regularly to refer generically to instructions sequences and programs.
---

# 	* [Binary Encoding of Arithmetic Instructions](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution)

Arithmetic instructions have the simplest machine language instruction formats, so we will start with them Figure 2-1 shows the format for the machine language encoding of a **register-type** arithmetic instruction

![Screen Shot 2020-06-15 at 10 17 25](https://user-images.githubusercontent.com/24994818/84675115-6dc1f300-aef1-11ea-8fc9-67e1c849cb13.png)

In **register-type** arithmetic instructions (that is, an arithmetic instruction that uses only registers and no immediate values), the first bit of the instruction is the **mode bit**. If the mode bit is set to 0, then the instruction is a **register-type** instruction; if it is set to 1, then the instruction is of the immediat type.

Bits 1-3 of the instruction specify the opcode, which tells the computer what type of operation the instruction represents. Bits 4-5 specify the instruction's first resource register. The last six bits are not needed by register-to-register arithmetic instructions, so they are padded with 0s (the are **zeroed out** in computer jargon) and ignored.

Now, let`s use the binary values in Tables 2-1 and 2-2 to translate the add instruction in line 3 of program 1-1 into a 2-byte (or 16 bits) macho¡ine language instruction:


| Assebly language Instruction | machine language instruction |
| ---------------------------  | ---------------------------  |
| Add A, B, C                  | 00001011 00000000            |

Here are a few more examples of arithmetic instructions, just so you can get the hang of it:

| Assebly language Instruction | machine language instruction |
| ---------------------------  | ---------------------------  |
| Add C, D, A                  | 00001011 00000000            |
| Add D, B, C                  | 00001101 10000000            |
| Add A, D, C                  | 00010011 10000000            |

Increasing the number of binary digits in the opcode and register fields increases the total number of instructions the machine can use and the number of registers it can have. 

For example, if you kwno something about binary notation, then you probably kwno that a 3-bit opcode allows the processor to map yo to 2^3 = 8 instructions in its **instruction set**, increasing the opcode size to 8 bits would allow the processor's instruction set to contain up to 256 instructions. Similarly, increasing the number of bits in the register field increases the possible number of registers that machine can have.

Arithmetic instructions containing an immediate value use an **immediate type** instruction format, which is slightly different from the register-type format we just saw. In an immediate-type instruction, the first byte contains the opcode, the source register, and the destination register, whie the second byte contains the immediate value, as shown in Figure 2-2

![Screen Shot 2020-06-15 at 10 34 02](https://user-images.githubusercontent.com/24994818/84677011-c0041380-aef3-11ea-9500-8ae349d9aeeb.png)

Here are a few immediate-type arithmetic instructions translated from assembly language to machine language.


| Assebly language Instruction | machine language instruction |
| ---------------------------  | ---------------------------  |
| Add C, 8, A                  | 10001000 00001000            |
| Add 5, A, C                  | 10000010 00000101            |
| Add 25, D, C                 | 10011110 00011001            |



# 	* [Binary Encoding of Memory Access Instructions](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution)

Memory-access instructions use both **register-type** and **immediate-type** instruction formats exactly like those shown for arithmetic instructiions. The only difference lies in how they use them. Let's take the case of a load first.

### The Load Instruction

We have previously seen two types of **load**, the first of which was the immediate type. An immediate-type load (see Figure 2-3) uses the immediate-type instruction format, but because **the load's source is an immediate value (a memory address)** and not a register, the source file is unneeded and must be **zeroed out**. (The source field is not recognized, though, and in a momento we will se what happens if it is not zeroed out)

![Screen Shot 2020-06-16 at 16 37 40](https://user-images.githubusercontent.com/24994818/84830773-ba8bf380-afef-11ea-957d-47bb11ba5dda.png)

Now let's transate the immediate-type **load** in line 1 of program 1-1 (12 is 1100 in binary notation)


| Assebly language Instruction | machine language instruction |
| ---------------------------  | ---------------------------  |
| load #12, A                  | 10100000 00001100            |

The 2-bute machine language instruction on the right is a binary representation of the assambly language instruction on the left. The first bte correspoindsto an immediate-type **load** instruction that takes register A as its destination. The second byte is the binary representation of the number 12 which is the source address in memory that the data is to be loaded from.

The **second type of load** we have seen is the register type. A register-type load uses the register-type instruction format, but with the source2 field zeroed out and ignored, as shown in Figure 2-4.

In figure 2-4, the source1 field specifies the gister containing the memory address that the processor is to load data from, and the destination fiel specifies the register that the loaded data is to be placed in.

![Screen Shot 2020-06-16 at 16 44 29](https://user-images.githubusercontent.com/24994818/84831277-ae546600-aff0-11ea-947c-53e7ca82218d.png)

For a **register-relative** addressed **load**, we use a version of the immediate-type instruction format, shown in Figure 2-5, with the base field specifying the register that contains **the base address** and the **offset** stored in the second byte of the instruction.

![Screen Shot 2020-06-16 at 16 46 30](https://user-images.githubusercontent.com/24994818/84831453-f2e00180-aff0-11ea-8e11-6a8605fb6c97.png)

Recall from Table 2-2 that 00 is the binary number that designates register A. Therefore, as a result of the DLW-1's particular machine language **encoding scheme**, any register but A Could theoretically be used to store **the base address* for a **register-relative load**

### The store instruction

The **register-type** binary format for a **store instruction** is the same as it is for a **load**, except that destination field specifiesee a register containing a destination memory address, and the source1 field specifies the register containing the data to be stored to memory.

The **immediate-type** machine language format for a **store**, pictured in Figure 2-6, is also similar to the immediate-type format for a load, except that since the destination register is not needed (the destination is the immediate memory address) the destination fiel is zeroed out, while the source field specifies which register holds the data to be stored.

![Screen Shot 2020-06-16 at 16 53 05](https://user-images.githubusercontent.com/24994818/84831926-ddb7a280-aff1-11ea-92d8-2fca69cfaf78.png)

The register-relative store, on the other hand, uses the same immediate-type instruction format used for the register-relative load (Figure 2-5), but the destination fiel is set to a nonzero value, and the offset is stored in the second byte. Again, **the base address** for a **register-relative store** can theoretically be stored in any register other than A, although by convention it is stored in D.

# 	* [Translating an Example Program into Machine Language](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 

For our simple computer with four registers, three instructions, and 256 memory cells, it is tedious but trivial to translate Program 1-1 into machine-readable binary representation using the previous tables and instruction formats. Program 2-1 shows the translation 


| line | Assebly language Instruction | machine language instruction |
| ---- | ---------------------------  | ---------------------------  |
| 1    | load #12, A                  | 10100000 00001100            |
| 2    | load #13, B                  | 10100001 00001101            |
| 3    | add A, B, C                  | 00000001 10000000            |
| 4    | store C, #14                 | 10111000 00001110            |

The 1s and 0s in the rightmost column of program 2-1 represent the high and low voltages that the computer **"thinks"** in.

Real machine language instructions are usually longer and more complex than the simple ones I've given here, but the basic idea is exactly the same. Program instructions are translated into machine language in a mechanical, predefined manner, and even in the case of a fully modern microprocessor, doing such translations by hand is merely a matter of knowing the instruction formats and having access to the right charts an tables.
Of course for the most part the only people who do such translations by hand are computer engineering or computer science undergraduates who have been assigned them for homework. This was not always the case, though.
 
# - [The Programming Model and the ISA](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 

Bacj in the bad old days, programmers had to enter programs into the computer directly in machine language (after having walked five miles in the snow uphill to work). In the very early stages of computing, this was done by **flipping switches**. The programmer toggled strings of 1s and 0s into the computer's very limited memory, ran the program, and then pored over the resulting strings of 1s and 0s to decode the answer.

Once memory sizes and processing power increased to the point where programmer time and effort were valuate enough relative to computing time and memory space, computer scientists divised ways of allowing the computer to use  portion of its power and memory to take on some of the burden of making its cryptc input and output a little more human-friendly.

In short, the tedious task of converting human-readable programs into machine-readable binary code was automated; hence the birth pf **assembly language** programming. Programs could now be written using mnemonics, register names, and memory locations, before being converted by **assembler** into machine language for processing.

In order to write assembly language programs for a machine, you have to understand the machine's available resources: how many registers it has, what instructions it supports, and soon. In other words, you need a well defined model of the machine you are trying to program.

# 	* [The Programming Model](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution)

The **programming model** is the programmer's interface to the microprocessor. It hides all of the processors complex implementation details behind a relatively simple, clean layer of abstraction that exposes to the programmer all o the processor's functionality. (see Chapter 4 for more on the history and development of the programming model).

Figure 2-7 shows a diagram of a programming model for an eight-register machine. By now, most of the parts of the diagram should be familiar to you. 

![Screen Shot 2020-06-18 at 17 24 51](https://user-images.githubusercontent.com/24994818/85077759-a5969800-b188-11ea-95d8-517cf5c77274.png)

The ALU performs arithmetic, the registers store numbers, and the **input-output unit (I/O unit)** is responsible for interacting with memory and the rest of the system (via loads and stores. The parts of the processor that we have not yet met lie in the **control unit**. Of these, we will cover the **program counter** and the **instruction register** now.


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



