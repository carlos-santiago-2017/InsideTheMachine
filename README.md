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

   * [Branch Instructions and the Fetch-Execute Loop]()
   * [The Branch Instruction as a Special Type of Load]()
   * [Branch Instructions and Labels]()

- [Excursus: Booting Up](https://github.com/c4arl0s/InsideTheMachine#--excursus-booting-up) 

# 4. [PIPELINED EXECUTION 35](https://github.com/c4arl0s/InsideTheMachine#inside-the-machine)

- [The Lifecycle of an Instruction](https://github.com/c4arl0s/InsideTheMachine#--the-lifecycle-of-an-instruction)
- [Basic Instruction Flow](https://github.com/c4arl0s/InsideTheMachine#--basic-instruction-flow)
- [Pipelining Explained](https://github.com/c4arl0s/InsideTheMachine#--pipelining-explained)
- [Applying the Analogy](https://github.com/c4arl0s/InsideTheMachine#--applying-the-analogy)
	* [A Non-Pipelined Processor](https://github.com/c4arl0s/InsideTheMachine#-a-non-pipelined-processor) 
	* [A Pipelined Processor](https://github.com/c4arl0s/InsideTheMachine#-a-pipelined-processor)
  * [Shrink the clock]()
  * [Shrinking Program Execution Time]()
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

At the heart of the modern computers is the **microprocessor** -also commonly called **central processing unit (CPU)** - a tiny, square silver of silicon that is etched with a microscopic network of gates and channels through which electricity flows. This network of gates (transistors) and channels (wires or lines) is a very small version of the kind circuitry that we have all seen when cracking open a television remote or an old radio. In short, the microprocessor is not just the **"heart"** of a modern computer - It is a computer and of itself

# - [The Calculator Model of Computing](https://github.com/c4arl0s/InsideTheMachine#--the-calculator-model-of-computing)

A computer takes a stream of instructions (code) and a stream of data as input, and it produces a stream of results as output.

![Screen Shot 2019-08-26 at 3 43 05 PM](https://user-images.githubusercontent.com/24994818/63722147-35dda800-c818-11e9-9e40-599208836737.png)

Figure 1-1 is my own variation on the traditional way of representing a processor's arithmetic logic unit (**ALU**)

I have depicted code and data streams entering the top ports and a results stream leaving the bottom port.

![Screen Shot 2020-05-29 at 23 47 12](https://user-images.githubusercontent.com/24994818/83319751-bf3a6480-a206-11ea-83f7-6536b64b33c5.png)

The kind of simple calculation describe above represents the sort of thing that we intuitive think computers do.

# - [The File-Clerk Model of Computing](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

The **"Calculator"** model of computing, while useful in many aspects, is not the only or even the best way to think about what computers do. As an alternative, consider the following definition of a computer:

A computer is a device that shuffles numbers around from place to place, reading, writing, erasing, and rewriting different numbers in different locations according to a set of inputs, a fixed set of rules for processing those inputs, and the prior history of all the inputs that the computer has seen since it was last reset, until a predefined set of criteria are met that case the computer to halt.

We might, after Richard Feynman, call this idea of a computer as a reader, writer, and modifier of numbers the **"file-clerk"** model of computing (as opposed to the aforementioned calculator model). In the File-clerk model, the computer access a large (theoretically infinite) store of sequentially arranged numbers fr the purpose of altering that store to achieve a desired result. Once this desired result is achieved, the computer halts so that the now-modified store of numbers can be read and interpreted by humans.

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
- Arithmetic Logic Unit (**ALU**)
- Bus.

The data enters the **ALU** from a special storage area, but where does the code stream come from? 
One might imagine that it comes from the keypad of some person standing at the computer and entering a sequence of instructions, each of which is then transmitted to the code input port of the **ALU**, or perhaps that the code stream is a prerecorded list of instructions that is fed into the ALU, one instruction at a time, by some manual or automated mechanism. Figure 1-3 depicts the code stream as a prerecorded list of instructions that is stored in a special storage area just like the data stream, and modern computers do store the code stream in just such manner.

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

Those three steps are carried out billions of times per second on a modern **CPU**.

To return to our File-clerck analogy, a computer is like a file clerck who sits at his desk all day waiting for messages from his boss. Eventually, the boss sends him a message telling him a message telling him to perform a calculation, and where in his personal filling cabinet the necessary numbers are located. So the clerk first retrieves the numbers from his filing cabinet, then performs the calculation, and finally places the result back into the filing cabinet. It is boring, mindless, repetitive task that is repeated endlessly, day in day out, which is precisely why we have invented a machine that can do it efficiently and not complain.


# - [The Register File](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

Since numbers must first be fetched from the storage before they can be added, we want our data storage a space to be as fast as possible so that the operation can be carried out quickly. Since the **ALU** is the part of the processor that does the actual addition. We would like **to place the data storage as close as possible the ALU** so it can read the operands almost instantaneously. However, practical considerations, such as CUPs limited surface area, constrain the size of the storage area that we can stick next to the ALU. This fast data storage locations attached to the ALU. These storage locations called **registers**, and the first x86 computers only had eight of them to work with. These **registers**^, which are arrayed in a storage structure called a **register file**, stored only a small subset of the data that the code stream needs (and we will talk about where the rest of that data lives shortly).

Building on our previous,, three.step description of what goes on when a computer's **ALU** is commanded to add two numbers, we can modify it as follows. To execute an **add** instruction, the ALU must perform these steps:

1. Obtain the two numbers to be added (the input operands= from two source registers.
2. Add the numbers.
3. Place the results back in a **destination register**

For a concrete example, let's look at addition on a simple computer with only four registers, named A,B,C,D. Suppose each of these registers contains a number, and we want to add the contents of two registers together and overwrite the contents of a third register with the resulting sum, as in the following operation:

Code				Comments
A + B = C		Add the contents of register A and B, and place the result in C, overwriting whatever was there.

Upon receiving and instruction commanding it to perform this addition operation, the **ALU** in our simple computer would carry out the following three familiar steps:

1. Read the contents of register A and B
2. Add the contents of A and B
3. Write the result to register C

You should recognize these three steps as a more specific form of the read-modify-write sequence from earlier, where the generic modify steps is replaced with an addition operation.

This three-step sequence is a quite simple, but it is at the very core of how a microprocessor really works. In fact, if you glance ahead to Chapter 10 discussion of the PowerPC 9700s pipeline, you will see that it actually has separate stages for each of these three operations: stage 12 is the register read step, stage 13 is the actual execute step, and stage 14 i the write-back step. (don't worry if you don't know what a pipeline is, because that is the topic for chapter 3). So the 970's **ALU** reads two operands from the register file, adds them together, and writes the sum back to the register file. If we were to stop our discussion right here, you would already understand the three core stages of the 970's main integer pipeline- all the other stages are either just preparation to get to this point or they are cleanup work after it.


# - [RAM: When Registers Alone Won’t Cut It](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

Obviously, four (or even eight) registers are not even close to the theoretically infinite storage space I mentioned earlier in this chapter. In order to make a viable computer that does useful work. You need to be able to store very large data sets. This is where the computer's **main memory** comes in. Main memory, which in modern computers is always some type of **random access memory (RAM)**, stores the data set on which the computer operates, and only a small portion of that data set a time is moved to the registers and only a small portion of that data set at a time is moved to the registers for easy access from the **ALU** (as shown in Figure 1-4).

![Screen Shot 2020-06-03 at 11 22 31](https://user-images.githubusercontent.com/24994818/83663511-7f6cd780-a58e-11ea-85bf-c73da8f4985b.png)  

Figure 1-4 gives only the slightest indication of it, but **main memory** is situated quite a bit farther away from the **ALU** than are the registers. In fact, the ALU and the registers are internal parts of the microprocessor, but main memory is a completely separate component of the computer system that is connected to the processor via the **memory bus**. Transfering data between main memory and the registers via the memory bus takes a significant amount of time. Thus, if there were no registers and the ALU had to read data directly from main memory for each calculation, computers would run very slowly. However, because the registers enable the computer to store data near the ALU, where it can be accessed nearly instantaneously, the computer's computational speed is **decoupled** somewhat from the speed of **main memory**. 

We will discuss the problem of memory access speeds and computational performance in more detail in [Chapter 11](), when we talk about [caches]().


# 	* [The File-Clerk Model Revisited and Expanded](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts) 

To return to our file-clerk metaphor, we can think of **main memory** as a document storage room located on another floor and the registers as a small, personal filling cabinet where the file clerk places the papers on which he is currently working. The clerk does not really know anything about the document storage room. -what it is or where it is located- because his desk and his personal filing cabinet are all he concerns himself with. For documents that are in the storage room, there is another office worker, the office secretary, whose job it is to locate files in the storage room and retrieve them for the clerk.

This secretary represents a few different units within the processor, all of which we will meet Chapter 4. For now, suffice it to say that when the boss wants the clerk to work on a file that is not in the clerk's personal filing cabinet, the secretary must first be ordered, via a message from the boss, to retrieve the file from the storage room and place it in the clerk's cabinet so that the clerk can access it when he gets the order to begin working on it.

# 	* [An Example: Adding Two Numbers](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)
To translate this office example into computing terms, let's look at how the computer uses main memory, the register file, and the **ALU** to add two numbers.

To add two numbers stored in main memory, the computer must perform these steps.

1. Load the two operands from main memory into the two source registers.
2. Add the contents of the source registers and place the results in the destination register, using the **ALU**. To do so, the ALU must perform these steps.
	A. Read the contents of registers A and B into the ALUU's input ports.
	B. Add the contents of A and B in the **ALU**.
	C. Write the result to regiter C via the **ALU**'s output port.
3. Store the contents of the destination register in **main memory**.

Since steps 2a, and 2c all take a trivial amount of time to complete, relative to steps 1 and 3, we can ignore them. Hence our addition looks like this:

1. Load the two operands from main memory into the two source registers.
2. Add the contents of the source registers, and place the results in the destination register, using the **ALU**.
3. Store the contents of the destination register in main memory.

The existence of **main memory** means that the user -the boss in our filing-clerk analogy- must manage the flow of information between main memory and the **CPU**'s registers. This means that the user must issue instructions to more than just the processor's **ALU**; he or she must also issue instructions to the parts of the **CPU* that **handle memory traffic**. Thus, the preceding three steps are representative of the kinds of instructions you find when you take a close look at the code stream.

# - [A Closer Look at the Code Stream: The Program](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

At the beginning pf this chapter, I defined the **code stream**  consisting of **"an ordered sequence of operations** and this definition is fine as far as it goes. But in order to dig deeper, we need a more detailed picture of what the code stream is an how it woks.

The term **operations** suggests  series of simple arithmetic operations like addition or substraction, but the **code stream** consist of more than just arithmetic operations. Therefore, it would be better to say that **the code stream** consist of **an ordered sequence of instructions**. Instructions, generally speaking, are commands that tell the whole computer - not just the **ALU**, but simple parts of the machine -exactly what actions to perform. As we have seen, a computer's list of potential actions encompasses more than just simple arithmetic operations.

# 	* [General Instruction Types](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

Instructions are grouped into ordered lists that, when taken as a whole, tell the different parts of the computer how to work together to perform a specific task, like grayscaling and image or playing a file media. These ordered lists of instructions are called **programs**, and they consist of a few basic types of instructions.

In modern RISC microprocessors, the act of moving data between memory and the registers is under the explicit control of the code stream or program. So if a programmer wants to add two numbers that are located in main memory and then store the result back in main memory, he or she must write a list of instructions (a program) to tell the computer exactly what to do. The program must consist of:

	* a load instruction to move the two numbers from memory into the registers.
	* an add instruction to tell the **ALU** to add the two numbers.
	* a store instruction to tell the computer to place the result of the addition back into memory, overwriting whatever was previously there.

These operations fall into two main categories:

### [Arithmetic Instructions]()

These instructions tell the **ALU** to perform an arithmetic calculation (for example add, sub, mul, div)

### [Memory-access instructions]()

These instructions tell the parts of the processor that deal with main memory to move data from and to main memory (for example load and store)

We will discuss a third type of instruction, the branch instruction, shortly. Branch instructions are technically a special type of memory-access instructions, but they access code storage instead instead of data storage. Still, it is easier to treat branches as a third category of instruction.

The **arithmetic instruction** fits with our calculator metaphor and is the type of instructions most familiar to anyone who is worked with computers. Instructions, like integer and floating-point addition, subtraction, multiplication, and division all fall under the general category.

In order to simplify the discussion and reduce the number of terms, I am temporarily including logical operations like AND, OR, NOT, NOR,and so on, under the general heading of arithmetic instructions. The difference between arithmetic and logical operations will be introduced in Chapter 2

The **memory-access instructions** is just as important as the arithmetic instruction, because without access main memory's data storage regions, the computer would have no way to get data into or out of the register file. 

To show you how **memory-access** and arithmetic operations work together within the context of the code stream, the remainder of this chapter will use a series of increasingly detailed examples. All of the examples are based on a simple, hypothetical computer, which I will call the DLW-1 [^2]

# 	* [The DLW-1’s Basic Architecture and Arithmetic Instruction Format](https://github.com/c4arl0s/InsideTheMachine#2-basic-computing-concepts)

The DLW-1 microprocessor consist of an **ALU** (along with a few other units that I will describe later) attached to four registers, named A,B,C,D for convenience. The **DLW-1** is attached to a bank of main memory that is laid out as a line of 256 memory cells, numbered #0 to #255 (The number that identifies an individual memory cell is called an **address**)

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

A **data segment is a block of contiguous memory cells that a program stores all of its data in**, so if a programmer knows a data segment's starting address (**base address**) in memory, he or she can access all of the other memory locations in that segment using this formula:

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

The binary valyes representing both the opcodes and the register codes are arranged in one of a number of **16-bits** (or 2-byte) formats to get a complete **machine language instruction** which is a binary number that can be stored in **RAM** and used by the processor.

---
**Note**
Because programmer-written instructions must be translated into binary codes before a computer can read them, it is common to see programs in any format -binary, assembly, or a high-level language like BASIC or C, referred to generically as "code" or "codes" When referring to programs written in assembly, binary or C language. Programmers also often describe the act of programming as "writing code" or "coding", I have adopted this terminology in this book, and will henceforth use the term "code" regularly to refer generically to instructions sequences and programs.
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

For example, if you know something about binary notation, then you probably know that a 3-bit opcode allows the processor to map yo to 2^3 = 8 instructions in its **instruction set**, increasing the opcode size to 8 bits would allow the processor's instruction set to contain up to 256 instructions. Similarly, increasing the number of bits in the register field increases the possible number of registers that machine can have.

Arithmetic instructions containing an immediate value use an **immediate type** instruction format, which is slightly different from the register-type format we just saw. In an immediate-type instruction, the first byte contains the opcode, the source register, and the destination register, while the second byte contains the immediate value, as shown in Figure 2-2

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

Now let's translate the immediate-type **load** in line 1 of program 1-1 (12 is 1100 in binary notation)


| Assembly language Instruction | machine language instruction |
| ---------------------------  | ---------------------------  |
| load #12, A                  | 10100000 00001100            |

The 2-bute machine language instruction on the right is a binary representation of the assembly language instruction on the left. The first byte corresponds to an immediate-type **load** instruction that takes register A as its destination. The second byte is the binary representation of the number 12 which is the source address in memory that the data is to be loaded from.

The **second type of load** we have seen is the register type. A register-type load uses the register-type instruction format, but with the source2 field zeroed out and ignored, as shown in Figure 2-4.

In figure 2-4, the source1 field specifies the register containing the memory address that the processor is to load data from, and the destination field specifies the register that the loaded data is to be placed in.

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

The **ALU** performs arithmetic, the registers store numbers, and the **input-output unit (I/O unit)** is responsible for interacting with memory and the rest of the system (via loads and stores. The parts of the processor that we have not yet met lie in the **control unit**. Of these, we will cover the **program counter** and the **instruction register** now.

# 	* [The Instruction Register and Program Counter](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 

Because programs are stored in memory as ordered sequence of instructions and memory arranged as a linear series of addresses, each instruction in a program lives at its own memory address. In order to step through and execute the lines of a program, the computer simply begins at the program's starting address and the steps through each successive memory location, fetching each successive instruction from memory, placing it in a special register, and executing it as shown in Figure 2-8

![Screen Shot 2020-06-18 at 17 40 34](https://user-images.githubusercontent.com/24994818/85078796-d972bd00-b18a-11ea-98da-fa03ef1d01b6.png)

For example, if the starting address in Program 1-1 were #500, it would look like Figure 2-9 in memory (with the instructions rendered in machine language, not assembly language, of course).

![Screen Shot 2020-06-18 at 17 42 29](https://user-images.githubusercontent.com/24994818/85078890-1939a480-b18b-11ea-8bcd-7cd8dc15c4a8.png)

# 	* [The Instruction Fetch: Loading the Instruction Register](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 

An **instruction fetch** is a special type of load that happens automatically or every instruction. It always takes the address that is currently in the **program counter** register as its source and the instruction register as its destination. The control unit uses a fetch to load each instruction of a program from memory into the instruction register, where that instruction is **decoded** before being executed; and while that instruction is being decoded, the processor places the address of the next instruction into the program counter by incrementing the address that is currently in the program counter, so that the newly incremented address points to the next instruction the sequence. In case of our DLW-1, the program counter is incremented by two every time an instruction is fetched, because the two-byte instructions begin at every other byte in memory.

# 	* [Running a Simple Program: The Fetch-Execute Loop](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 

In Chapter 1 we discussed the steps a processor takes to perform calculations on numbers using the **ALU** in combination with a fetched arithmetic instruction. Now let's look at the steps the processor takes in order to fetch a series of instructions - a program - and feed them to either the ALU (in the case of arithmetic instructions) or the memory access hardware (in case of leads and stores).

1. **Fetch** the next instruction from the address stored in the program counter, and load that instruction into the instruction register. Increment the program counter.
2. **Decode** the instructions in the instruction register.
3. **Execute** the instruction in the instruction register, using the following rules:
     * a. If the instruction is an arithmetic instruction, execute it using the **ALU** and register file.
     * b. If the instruction is a memory access instruction, execute it using the memory-access hardware.

These three steps are fairly straightforward, and with one modification they describe the way that microprocessors execute programs (as we will see in the section "Branch Instructions" on page 30). Computer scientists often refer to these steps as the **fetch execute** or the **fetch-execute cycle**. The fetch-execute loop is repeated for as long as the computer is powered on. The machine iterates though the entire loop, from step 1 to step 3, over and over again many millions or billion of times per second in order to run programs.

Let's run through the three steps with our example program as shown in Figure 2-9. (this example presumes that #500 is already in the program counter). Here is what the processor does, in order:

1. Fetch the instruction beginning at #500, and load **load #12, A** into the instruction register. Increment the program counter to #502.
2. Decode **load #12, A** in the instruction register.
3. Execute **load #12, A** from the instruction register, using the memory-access hardware.
4. Fetch the instruction beginning at #502, and load **load #13, B** in the instruction register. Increment the program counter to #504.
5. Decode **load #13, B** in the instruction register.
6. Execute **load #13, B** from the instruction register, using the memory-access hardware..
7. Fetch the instruction at #504, and load **add A, B, C** into the instruction register. Increment the program counter to #506
8. Decode **add A, B, C** in the instruction register.
9. Execute **add A, B, C** from the instruction register, using the **ALU** and register file.
10. Fetch the instruction at #506, and load **store C, #14** in the instruction register. Increment the program counter to #508
11. Decode *+store C, #14** in the instruction register.
12. Execute **store C, #14** from the instruction register, using the memory-access hardware.

---
Note
To zoom in on the execute steps f the preceding sequence, revisit Chapter 1, and particularly the sections "Refining the File-Clerk Model" on page 6 and "RAM: When Register Alone Won't Cut it" on corresponding page If you do, you will gain a pretty good understanding of what is involved in executing a program on any machine. Sure, there are important machine-specific variations for most of what I have presented here, but the general outlines (and even a decent number of the specific) are the same
---

# - [The Clock](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution)

Steps 1 through 12 in the previous section don't take an arbitrary amount of time to complete. Rather, they are performed according to the pulse of the clock that governs every action the processor takes.

This clock pulse, which is generated by a **clock generator** module on the motherboard and is fed into the processor from the outside, times the functioning of the processor so that, on the DLW-1 at least, all three steps of the fetch-execute loop are completed in exactly one beat of the clock. Thus, the program in Figure 2-9, as I have traced its execution in the preceding section, tales exactly four clock beats to finishig execution, because a new instruction is fetched on each beat of the clock.

One obvious way to speed up the execution of prgrams on the DLW-1 would be to speed up its clock generator so that each step takes less time to complete. This is generally true of all microprocessors, hence the race among microprocessor designers to build and market chips with ever-higher clock speeds. (We will talk more about the relationship between clock speed and performance in Chapter 3)

# - [Branch Instructions](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 

As I have presented it so far, the processor moves throwgh each line in a program in sequence ultil it reaches the end of the program, at which point the program's output is available to the user.

There are certain instructions in the struction stream, however, that allow the processor to jump to a program line that is out of sequence. For instance, by inserting a **branch instruction** into line 5 of a program, we could cause the processor's control unit to jump all the way down to lin 20 and begin executing there (** a forward branch**), or we could cause it to jump back up to lin 1 (** a backward branch**). Because a program is an ordered sequence of instructions, by including forward and backward branch instructions, we can arbitrarily move about in the program. This is a powerful ability, and branches are en essential part of computing.

Rather than thinking about forward of backward branches, it is more useful for our present purposes to categorize all branches as being one of the following two types: **conditional brancges or unconditional branches**.

# 	* [Unconditional Branch](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 

An **unconditional brancg** instruction consist of two parts: the branch instruction and the target address.

```assembly
jum #target
```

An **unconditional branch**, #target can be either an immediate value, like #12, or an address stored in a register, like #D.

Unconditional branches are fairly easy to execute, since all that the computer needs to do upon decoding such a branch in the instruction register is to have the control unit replace the address currently in the program counter with branch's target address. Then the next time the processor goes to fetch the instruction at the address given by the program counter, it will fetch the address at the branch target instead.

# 	* [Conditional Branch](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 

Though it has the same basic instruction format as the unconditional branch (instruction #target), the **conditional branch** instruction is a little more complicated, because it involves jumping to the target address only if a certain condition is met.

Because of such conditional jumps, we need a special register or set of registers in which to store information about the results of arithmetic instructions - information such as whether the previous result was zero or nonzero, positive or negative, and so on.

| line | Assebly language Instruction |
| ---- | ---------------------------- |
| 16   | sub A, B, C                  |
| 17   | jumpz #106                   |
| 18   | add A, B, C                  |

DLW-1 handles this branch with **processor status word** (PSW) register

# - [Branch Instructions and the Fetch-Execute Loop]()

Now that we have looked at the basics branching, we can modify our three step summary of program execution to include the possibility of branch instruction:

1. **Fetch** the next instruction from the address stored in the program counter, and load that instruction into the instruction register. Increment the program counter.
2. **Decode** the instruction in the instruction register.
3. **Execute** the instruction in the instruction register, using the following rules
   * a. It the instruction is an arithmetic instruction, then execute it using the **ALU** and register file.
   * b. If the instruction is a memory-access instruction, then execute it using the memory hardware.
   * c. If the instruction is a branch instruction, then execute it using the control unit and the program counter. (For a taken branch, write the branch target address into the program counter.)

In short, you might say that branch instructions allow the programmer to redirect the **processor** as it travels through the instructions stream. Branches point the processor to different sections of code stream by manipulating its control unit, which, because it contains the instruction register and program counter, is the rudder of the **CPU**.

# - [The Branch Instruction as a Special Type of Load]()

Recall that an instruction fetch is a special type of load that happens automatically for every instruction and that always takes the address in the program counter as its source and the instruction register as its destination. With that in mind, you might think of a branch instruction as **a similar kind of load**, but **under the control of the programmer instead of the CPU**.. The branch instruction is a **load** that takes the address specified by #target as its source and the instruction registere as its destination.

Like a regular load, a branch instruction can take as its target an address stored in a register. In other words, **branch instructions can use register-relative addressing** just like regular **load** instructions. This capability is useful because it allows the computer to store blocks of code at arbitrary places in memory. The programmer does not need to know the address where the block of code will wind up before writing a branch instruction that jumps to the particular block; all he or she needs is a way to get to the memory location where the operating system, which is responsible for managing memory, has stored the starting address of the desired block of code.

| Line | Code         | Comments                                                                                                                                                                      |
|------|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 16   | Sub A, B, A  | Subtract the number in register A from the number in register B and store the result in A                                                                                     |
| 17   | jumps #C     | Check the PSW, and if the result of the previous instruction was zero, jump to the instruction at the address stored in C. If the result was nonzero, continue on to line 18. |
| 18   | add A, 15, A | Add 15 to the number in A and store the result in A                                                                                                                           |

Program 2-3 A conditional branch that uses an address stored in a register.

When a programmer uses **register-relative addressing** with a branch instruction, the operating system must load a certain register with the base address of the **code segment** inwhich the program resides. Like the data segment, **the code segment is a contiguous block of memory cells**, but its cells stoe instructions instead of data. So to jump to line 15 in the currently running program, assuming that the operating system has placed the base address of the code segmented in C, the programmer could use he following instruction:

| Code        | Comments                                                                                                                                                      |   |
|-------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|---|
| jum #(C+30) | Jump to the instruction located 30 bytes away from the start of the code segment. (each instruction is 2 bytes length, so this puts us at the 15 instruction) |   |



# - [Branch Instructions and Labels]()

In programs written for real-world architectures, branch targets don't usually take the form of either **immediate values or register-relative values**. Rather, the programmer places a **label** on the line of code to which he or she wants to jump, and then puts that label in the branch's target field. Program 2-4 shows a portion of assembly language code that uses labels.

```assembly
      sub A, B, A
      jumpz LBL1
      add A, 15, A
      store A, #(D+16)
LBL1: add A, B, B
      store B, #(D+16)
```
Program 2-4: Assembly language code that uses labels.

In this example, if the contents of A and B are equal, the computer will jump to the instruction with the label LBL1 and begin executing there, skipping the instructions between the jump and the labeled **add**. Just as the absolute memory addresses used in **load** and **store** instructions are modified at load time to fit the location in memory of program's data segment, labels like LBL1 are changed at load time into memory addresses that reflec the location in memory of the program's code segment.

# - [Excursus: Booting Up](https://github.com/c4arl0s/InsideTheMachine#3-the-mechanics-of-program-execution) 

If you have been around computers for any length of time, you have heard the terms **reboot** or **boot up** used in connections with either resetting the computer to its initial state or powering it in initially. The term **boot is a shortened version of the term **bootstrap**, which is itself a reference to the seemingly impossible task a computer must perform on start-up, namely, **"pulling itself up by its own bootstraps"**

I say **"seemingly impossible"** because when a computer is first powered on there is no program in memory, but programs contain the instructions that make the computer run. If the processor has no program running when it is the first powered on, then how does it know where to fetch the first instruction from ?

The solution to this dilemma is that the microprocessor, in its power-on default state, is hard-wired to fetch that first instruction from a predetermined address in memory. This first instruction, which is loaded into the processors instruction register, is the first line of a program called the **BIOS** that lives in a special set of storage locations - a small read-only memory (ROM) module attached to the computer's motherboard. It is the job of the BIOS to perform basic tests of the **RAM** and peripherals in order to  verify that everything is working properly. The boot process can continue.

At the end of the BIOS program lies a jump instruction, the target of which is the location of a **bootloader program**. By using a jump, the BIOS hands off control of the system to this second program, whose job it is to search for and load the computer's operating system from the hard disk. The operating system (OS) loads and unloads all of the other programs that run on the computer, so once the OS is up and running the computer is ready to interact with the user.


# 4. [PIPELINED EXECUTION 35](https://github.com/c4arl0s/InsideTheMachine#inside-the-machine)

All of the processor architectures that you have looked at so far are relatively simple, and they reflect the earliest stages of computer evolution.  This chapter will bring you closer to the modern computing era by introducing one of the key innovations that underlies the rapid performance increases that have characterized the past few decades of microprocessor development: **pipelined execution**.

---
Note
Pipelined execution is a technique that enables microprocessor designers to increase the speed at which a processor operates, thereby decreasing the amount of time that the processor takes to execute a program. This chapter will first introduce the concept of **pipelining** by means of a factory analogy, and it will then apply the analogy to microprocessors. You will the learn how to evaluate the benefits of **pipelining**, before I conclude with a discussion of the technique¡s limitations and costs.

---
Note
This chapter’s discussion of pipelined execution focuses solely **on the execution of arithmetic instructions**. Memory instructions and branch instructions are pipelined using the same fundamental principles as arithmetic instructions, and later chapters will cover the peculiarities of the actual execution process of each of these two types of instruction.
---

# - [The Lifecycle of an Instruction](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)

In the previous chapter, you learned that a computer repeats three basic steps over and over again in order to execute a program:

1. Fetch the next instruction from the address stored in the program counter and load that instruction into the instruction register. Increment the program counter.
2. Decode the instruction in the instruction register.
3. Execute the instruction in the instruction register.

You should also recall that **step 3**, the execute step, **itself can consist of
multiple sub-steps**, depending on the type of instruction being executed (arithmetic, memory access, or branch). In the case of the arithmetic instruction add A, B, C, the example we used last time, the three sub-steps are as follows:

1. Read the contents of registers A and B.
2. Add the contents of A and B.
3. Write the result back to register C.

Thus the expanded list of actions required to execute an arithmetic
instruction is as follows (substitute any other arithmetic instruction for add in the following list to see how it’s executed):

1. Fetch the next instruction from the address stored in the program counter and load that instruction into the instruction register. Increment the program counter.
2. Decode the instruction in the instruction register.
3. Execute the instruction in the instruction register. Because the instruction is not a branch instruction but an arithmetic instruction, send it to the arithmetic logic unit (**ALU**).
a. Read the contents of registers A and B.
b. Add the contents of A and B.
c. Write the result back to register C.

At this point, **I need to make a modification to the preceding list**. For reasons we will discuss in detail when we talk about the instruction window in Chapter 5. **Most modern microprocessors treat sub-steps 3a and 3b as a group**, while they treat step 3c, **the register write, separately**. To reflect this conceptual and architectural division, this list should be modified to look as follows:


1. Fetch the next instruction from the address stored in the program counter, and load that instruction into the instruction register. Increment the program counter.
2. Decode the instruction in the instruction register.
3. Execute the instruction in the instruction register. Because the instruction is not a branch instruction but an arithmetic instruction, send it to the **ALU**.
  * Read the contents of registers A and B.
  * Add the contents of A and B.
4. Write the result back to register C.

In a modern processor, these four steps are repeated over and over again until the program is finished executing. These are, in fact, **the four stages in a classic RISC pipeline**. ( I will define the term **pipeline** shortly; for now, just think of a pipeline as a series of stages that each instruction in the code stream must pass through when the code stream is being executed.). Here are the four stages in their abbreviated form, the form in which you will most often see them:

1. Fetch
2. Decode
3. Execute
4. Write (or “write-back”)

Each of these stages could be said to represent one **phase** in the **lifecycle** of an instruction. An instruction starts out in the **fetch phase**, moves to the **decode phase**, then to the **execute phase**, and finally to the **write phase**. As I mentioned in **"The clock"** on page 29, each phase takes a fixed, but by no means equal, amount of time. In most of the example processors with which you will be working in this chapter, all four phases take an equal amount of time; this is not usually the case in real-world processors. In any case, if the DLW-1 takes exactly 1 nanosecond (**[ns]**) to complete each phase, then the DLW-1 can finish one instruction ever 4 ns.

---
Note
The term RISC is an acronym for Reduce Instruction Set Computing. I Will cover this term in more detail in Chapter 5.
---

# - [Basic Instruction Flow](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)

One useful division that computer architects often employ when talking about **CPU** is that of **front end** versus **back end**. As you already know, when instructions are fetched from main memory, they must be decoded for execution. This fetching and decoding takes place in the processor's front end. You can see in Figure 3-1 that the front end roughly corresponds to the control and I/O units in the previous chapter's diagram of the DLW-1's programming model. The **ALU** and registers constitute the back end of the DWL-1. Instructions make their way from the front end down through the back end, where the work of number crunching gets done.

![Screen Shot 2020-07-03 at 11 05 22](https://user-images.githubusercontent.com/24994818/86484987-2626ce00-bd1d-11ea-8802-527b64d27c3e.png)

We can now modify figure 1-4 to show all four phases of execution. (see Figure 3-2)

![Screen Shot 2020-07-03 at 11 07 01](https://user-images.githubusercontent.com/24994818/86485054-553d3f80-bd1d-11ea-8357-7380952f3ff4.png)

From here on out, we are going to focus primarily on the code stream, and more specifically, on how instructions enter and flow through the microprocessor, so the diagrams will need to leave out the data and results streams entirely. Figure 3-3 presents a microprocessor's basic instruction flow in a manner that is straightforward, yet easily elaborated upon.

![Screen Shot 2020-07-03 at 11 09 02](https://user-images.githubusercontent.com/24994818/86485164-9f262580-bd1d-11ea-88d1-13f71ca8c6af.png)

In Figure 3-3, instruction flows from the from end's fetch and decode phases into the back end's execute and write. (Don't worry if this seems too simple. As the level of complexity of the architectures under discussion increases, so will the complexity of the diagrams.)

# - [Pipelining Explained](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)

Let’s say my friends and I have decided to go into the automotive manufacturing business and that our first product is to be a sport utility vehicle (SUV). After some research, we determine that there are five stages in the SUV-building process:

**Stage 1**: Build the chassis.
**Stage 2**: Drop the engine into the chassis.
**Stage 3**: Put the doors, a hood, and coverings on the chassis. 
**Stage 4**: Attach the wheels.
**Stage 5**: Paint the SUV.

Each of these stages requires the use of highly trained workers with very specialized skill sets—workers who are good at building chasses don’t know much about engines, bodywork, wheels, or painting, and likewise for engine builders, painters, and the other crews. So when we make our first attempt to put together an SUV factory, we hire and train five crews of specialists, one for each stage of the SUV-building process. There’s one crew to build the chassis, one to drop the engines, one to put the doors, hood, and coverings on the chassis, another for the wheels, and a painting crew. Finally, because the crews are so specialized and efficient, each stage of the SUV-building process takes a crew exactly one hour to complete.**

Now, since my friends and I are computer types and not industrial engi- neers, we had a lot to learn about making efficient use of factory resources. We based the functioning of our first factory on the following plan: Place all five crews in a line on the factory floor, and have the first crew start an SUV at Stage 1. After Stage 1 is complete, the Stage 1 crew passes the partially finished SUV off to the Stage 2 crew and then hits the break room to play some foos- ball, while the Stage 2 crew builds the engine and drops it in. Once the Stage 2 crew is done, the SUV moves down to Stage 3, and the Stage 3 crew takes over, while the Stage 2 crew joins the Stage 1 crew in the break room.

The SUV moves on down the line through all five stages in this way, with only one crew working on one stage at any given time while the rest of the crews sit idle. Once the completed SUV finishes Stage 5, the crew at Stage 1 starts on another SUV. At this rate, it takes exactly five hours to finish a single SUV, and our factory completes one SUV every five hours.

In Figure 3-4, you can see the SUV pass through all five stages. The SUV enters the factory floor at the beginning of the first hour, where the Stage 1 crew begins work on it. Notice that all of the other crews are sitting idle while the Stage 1 crew does its work. At the beginning of the second hour, the Stage 2 crew takes over, and the other four crews sit idle while waiting on Stage 2. This process continues as the SUV moves down the line, until at the beginning of the sixth hour, one SUV stands completed and while another has entered Stage 1.

![Screen Shot 2020-07-04 at 19 42 50](https://user-images.githubusercontent.com/24994818/86523194-9113fa00-be2e-11ea-8b6a-55c81eecf0d0.png)

Fast-forward one year. Our SUV, the Extinction LE, is selling like . . . well, it’s selling like an SUV, which means it’s doing pretty well. In fact, our SUV is selling so well that we’ve attracted the attention of the military and have been offered a contract to provide SUVs to the U.S. Army on an ongoing basis. The Army likes to order multiple SUVs at a time; one order might come in for 10 SUVs, and another order might come in for 500 SUVs. The more of these orders that we can fill each fiscal year, the more money we can make during that same period and the better our balance sheet looks. This, of course, means that we need to find a way to increase the number of SUVs that our factory can complete per hour, known as our factory’s SUV **completion rate**. By completing more SUVs per hour, we can fill the Army’s orders faster and make more money each year.

The most intuitive way to go about increasing our factory’s SUV comple- tion rate is to try and decrease the production time of each SUV. If we can get the crews to work twice as fast, our factory can produce twice as many SUVs in the same amount of time. Our crews are already working as hard
as they can, though, so unless there’s a technological breakthrough that increases their productivity, this option is off the table for now.

Since we can’t speed up our crews, we can always use the brute-force approach and just throw money at the problem by building a second assembly line. If we hire and train five new crews to form a second assembly line, also capable of producing one car every five hours, we can complete a grand total of two SUVs every five hours from the factory floor—double the SUV comple- tion rate of our present factory. This doesn’t seem like a very efficient use of factory resources, though, since not only do we have twice as many crews working at once but we also have twice as many crews in the break room at once. There has to be a better way.

Faced with a lack of options, we hire a team of consultants to figure out a clever way to increase overall factory productivity without either doubling the number of crews or increasing each individual crew’s productivity. One year and thousands of billable hours later, the consultants hit upon a solution. Why let our crews spend four-fifths of their work day in the break room, when they could be doing useful work during that time? With proper sched- uling of the existing five crews, our factory can complete one SUV each hour, thus drastically improving both the efficiency and the output of our assembly line. The revised workflow would look as follows:

1. The Stage 1 crew builds a chassis.
2. Once the chassis is complete, they send it on to the Stage 2 crew.
3. The Stage 2 crew receives the chassis and begins dropping the engine in,
while the Stage 1 crew starts on a new chassis.
4. When both Stage 1 and Stage 2 crews are finished, the Stage 2 crew’s work advances to Stage 3, the Stage 1 crew’s work advances to Stage 2, and the Stage 1 crew starts on a new chassis.

Figure 3-5 illustrates this workflow in action. Notice that multiple crews
have multiple SUVs simultaneously in progress on the factory floor. Compare this figure to Figure 3-4, where only one crew is active at a time and only one SUV is on the factory floor at a time.

![Screen Shot 2020-07-04 at 19 49 15](https://user-images.githubusercontent.com/24994818/86523263-755d2380-be2f-11ea-89dd-fdb2be3daf41.png)

So as the assembly line begins to fill up with SUVs in various stages of production, more of the crews are put to work simultaneously until all of the crews are working on a different vehicle in a different stage of production. (Of course, this is how most of us nowadays in the post-Ford era expect a good, efficient assembly line to work.) If we can keep the assembly line full and keep all five crews working at once, we can produce one SUV every hour: a fivefold improvement in SUV **Program Execution Time** over the previous comple- tion rate of one SUV every five hours. That, in a nutshell, is **pipelining**.

While the total amount of time that each individual SUV spends in pro- duction has not changed from the original five hours, the rate at which the factory as a whole completes SUVs has increased drastically. Furthermore, the rate at which the factory can fulfill the Army’s orders for batches of SUVs has increased drastically, as well. **pipelining** works its magic by making optimal use of already existing resources. We don’t need to speed up each individual stage of the production process, nor do we need to drastically increase the amount of resources that we throw at the problem; all that’s necessary is that we get more work out of resources that are already there.

WHY THE SUV FACTORY?
The preceding discussion uses a factory analogy to explain **pipelining**. Other books use simpler analogies, like doing laundry, for instance, to explain this technique, but there are a few reasons why I chose a more elaborate and lengthy analogy to illustrate what is a relatively simple concept. First, I use factory analogies throughout this book, because assembly line-based factories are easy for readers to visualize and there’s plenty of room for filling out the mental image in interesting ways in order to make a variety of related points. Second, and perhaps even more impor- tantly, the many scheduling-, queuing- and resource management–related problems that factory designers face have direct analogies in computer architecture. In many cases, the problems and solutions are exactly the same, simply translated into a different domain. (Similar queuing-related problem/solution pairs also crop up in the service industry, which is why analogies involving supermarkets and fast food restaurants are also favorites of mine.)


# - [Applying the Analogy](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)

Bringing our discussion back to microprocessors, it should be easy to see how this concept applies to the four phases of an instruction’s lifecycle. Just as the owners of the factory in our analogy wanted to increase the number of SUVs that the factory could finish in a given period of time, microprocessor designers are always looking for ways to increase the number of instructions that a **CPU** can complete in a given period of time. When you recall that a program is an ordered sequence of instructions, it becomes clear that increasing the number of instructions executed per unit time is one way to decrease the total amount of time that it takes to execute a program. (The other way to decrease a program’s execution time is to decrease the number of instructions in the program, but this chapter won’t address that approach until later.) In terms of our analogy, a program is like an order of SUVs from the military; just like increasing our factory’s output of SUVs per hour enabled us to fill orders faster, increasing a processor’s instruction **Program Execution Time** (the number of instructions completed per unit time) enables it to run programs faster.

# 	* [A Non-Pipelined Processor](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35) 

The previous chapter briefly described how the simple processors described so far (e.g., the DLW-1) use the clock to time its internal operations. These non-pipelined processors work on one instruction at a time, moving each instruction through all four phases of its lifecycle during the course of one clock cycle. Thus non-pipelined processors are also called **single-cycle processors**, because all instructions take exactly one clock cycle to execute fully (i.e., to pass through all four phases of their lifecycles).

Because the processor completes instructions at a rate of one per clock cycle, you want the **CPU**’s clock to run as fast as possible so that the processor’s instruction **Program Execution Time** can be as high as possible.

Thus you need to calculate the maximum amount of time that it takes to complete an instruction and make the clock cycle time equivalent to that length of time. It just so happens that on the hypothetical example **CPU**, the four phases of the instruction’s lifecycle take a total of 4 **[ns]** to complete. Therefore, you should set the duration of the **CPU** clock cycle to 4 ns, so that the **CPU** can complete the instruction’s lifecycle —**from fetch to write-back**—in a **single clock**. (A **CPU** clock cycle is often just called a **clock** for short.)

In Figure 3-6, the blue instruction leaves the code storage area, enters the processor, and then advances through the phases of its lifecycle over the course of the 4 **[ns]** clock period, until at the end of the fourth nanosecond, it completes the last phase and its lifecycle is over. The end of the fourth nanosecond is also the end of the first clock cycle, so now that the first clock cycle is finished and the blue instruction has completed its execution, the red instruction can enter the processor at the start of a new clock cycle and go through the same process. This 4 ns sequence of steps is repeated until, after a total of 16 ns (or four clock cycles), the processor has completed all four instructions at a **Program Execution Time** of 0.25 instructions/ns (= 4 instructions/ 16 ns).

![Screen Shot 2020-07-05 at 9 01 59](https://user-images.githubusercontent.com/24994818/86534454-36b28200-be9e-11ea-885f-4ea98618add0.png)

**Single-cycle processors** like the one in Figure 3-6 are simple to design, but they waste a lot of hardware resources. All of that white space in the diagram represents processor hardware that’s sitting idle while it waits for the instruction that’s currently in the processor to finish executing. By **pipelining the processor** in this figure, you can put more of that hardware to work every nanosecond, thereby increasing the processor’s efficiency and its performance on executing programs

Before moving on, I should clarify a few concepts illustrated in Figure 3-6. At the bottom is a region labeled **“Completed Instructions.”** Completed instructions don’t actually go anywhere when they’re finished executing; once they’ve done their job of telling the processor how to modify the data stream, they’re simply deleted from the processor. So the **“Completed Instructions”** box does not represent a real part of the computer, which is why I’ve placed a dotted line around it. This area is just a place for you to keep track of how many instructions the processor has completed in a certain amount of time, or **the processor’s instruction completion rate** (or **completion rate**, for short), so that when you compare different types of processors, you’ll have a place where you can quickly see which processor performs better. The more instructions a processor completes in a set amount of time, the better it performs on programs, which are an **ordered sequence of instructions**. Think of the **“Completed Instructions”** box as a sort of scoreboard for tracking each processor’s completion rate, and check the box in each of the subsequent figures to see how long it takes for the processor to populate this box.

Following on the preceding point, you may be curious as to why the blue instruction that has completed in the fourth nanosecond does not appear in the **“Completed Instructions”** box until the fifth nanosecond.
The reason is straightforward and stems from the nature of the diagram. Because an instruction spends **one complete nanosecond**, from start to finish,
in each stage of execution, the blue instruction enters the write phase at the beginning of the fourth nanosecond and exits the write phase at the end of the fourth nanosecond. This means that the fifth nanosecond is the first full nanosecond in which the blue instruction stands completed. Thus at the beginning of the fifth nanosecond (which coincides with the end of the fourth nanosecond), the processor has completed one instruction.

# 	* [A Pipelined Processor](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)

**Pipelining a processor** means breaking down its instruction execution process—what I’ve been calling the instruction’s lifecycle—into a series of discrete **pipeline stages** that can be completed in sequence by specialized hardware. Recall the way that we broke down the SUV assembly process into five discrete steps—with one dedicated crew assigned to complete each step— and you’ll get the idea.

Because an instruction’s lifecycle consists of four fairly distinct phases, you can start by breaking down the **single-cycle processor’s instruction execution process** into a sequence of four discrete pipeline stages, where each pipeline stage corresponds to a phase in the standard instruction lifecycle:

**Stage 1**: Fetch the instruction from code storage.
**Stage 2**: Decode the instruction.
**Stage 3**: Execute the instruction.
**Stage 4**: Write the results of the instruction back to the register file.
 
Note that the number  of pipeline stages is called the **pipeline depth**. So the four-stage pipeline has a pipeline depth of four.

For convenience's sake, let's say that each of these four pipeline stages takes exactly **1 [ns]** to finish its work on an instruction, just like each crew in our assembly line analogy takes one hour to finish its portion of the work on an SUV. So the original single-cycle processor's **4 [ns]** execution process is now broken down into four discrete, sequential pipeline stages of **1 [ns]** each in length.

Now let's step through another diagram together to see how a pipeline **CPU** would execute the four instructions depicted in Figure 3-7.

![Screen Shot 2020-07-07 at 9 15 45](https://user-images.githubusercontent.com/24994818/86794801-85912080-c032-11ea-86ee-bb47088c6eea.png)

At the beginning of the first nanosecond, the blue instruction enters the fetch state. After that nanosecond is complete, the second nanosecond begins and the blue instruction moves on to the decode stage, while the next instruction, the red one, starts to make its way from code storage to the processor (it enters the fetch stage). At the start of the third nanosecond, the blue instruction advances to the execute stage, the red instruction advances the decode stage, and the green instruction enters the fetch stage. At the fourth nanosecond, the blue instruction advances to the write stage, the red instruction advances to the execute stage, the green instruction advances to the decode stage, and the purple instruction advances to the fetch stage. After the fourth nanosecond has fully elapsed and the fifth nanosecond starts, the blue instruction has passed from the pipeline and is now finished executing. Thus we can say that at the end of **4 [ns]** (= four clock cycles), the pipelined processor depicted in Figure 3-7 has completed one instruction.

At start of the fifth nanosecond, the pipeline is now full and the processor can begin completing instructions at a rate of **one instruction per nanosecond**. This one **instruction / ns completion rate** is a fourfold improvement over the single-cycle processor's completion rate of 0.25 instructions / ns (or four instructions ever 16 ns).

#   * [Shrink the clock]()

You can see from Figure 3-7 that the role of the **CPU** clock changes slightly in a **pipelined** processor, compared to the single-cycle processor shown in Figure 3-6. Because all of the pipeline stages must now work together simultaneously and be ready at the start of each new nanosecond to hand over the results of their work to the next pipeline stage, the clock is needed to coordinate the activity of the whole pipeline. The way this is done is simple: Shrink the clock cycle time to match the time it takes each stage to complete its work so that at the start of each clock cycle, each pipeline stage hands off the instruction it was working on to the next stage in the pipeline. Because each pipeline stage in the example processor takes **1 ns** to complete its work, you can set the clock cycle to be **1 ns** in duration.
This new method of clocking the processor means that a new instruction will not necessarily be completed at the close of each clock cycle, as was the case with the single-cycle processor. Instead, a new instruction will be completed at the close of only those clock cycles in which the write stage has been working on an instruction. Any clock cycle with an empty write stage will add no new instructions to the **“Completed Instructions”** box, and any clock cycle with an active write stage will add one new instruction to the box. Of course, this means that when the pipeline first starts to work on a program, there will be a few clock cycles—three to be exact—during which no instructions are completed. But once the fourth clock cycle starts, the first instruction enters the write stage and the pipeline can then begin completing new instructions on each clock cycle, which, because each clock cycle is **1 ns**, translates into a **Program Execution Time** of one instruction per nanosecond.

#  * [Shrinking Program Execution Time]()

Note that the total execution time for each individual instruction is not changed by **pipelining**. It still takes an instruction **4 ns** to make it all the way through the processor; that **4 ns** can be split up into four clock cycles of **1 ns** each, or it can cover one longer clock cycle, but it’s still the same **4 ns**. [Thus pipelining doesn’t speed up instruction execution time, but it does speed up program execution time (the number of nanoseconds that it takes to execute an entire program) by increasing the number of instructions finished per unit of time](). Just like **pipelining** our hypothetical SUV assembly line allowed us to fill the Army’s orders in a shorter span of time, even though each individual SUV still spent a total of five hours in the assembly line, so does **pipelining allow a processor to execute programs in a shorter amount of time**, even though each individual instruction still spends the same amount of time traveling through the **CPU**. **Pipelining makes more efficient use of the CPU’s existing resources by putting all of its units to work simultaneously, thereby allowing it to do more total work each nanosecond**	.


# 	* [The Speedup from Pipelining](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35) 

In general, the speedup in **Program Execution Time** versus a single-cycle implementa- tion that’s gained from **pipelining** is ideally equal to the number of pipeline stages. A four-stage pipeline yields a fourfold speedup in the **Program Execution Time** versus a single-cycle pipeline, a five-stage pipeline yields a fivefold speedup, a twelve-stage pipeline yields a twelvefold speedup, and so on. This speedup is possible because the more pipeline stages there are in a processor, the more instructions the processor can work on simultaneously, and the more instruc- tions it can complete in a given period of time. So the more finely you can slice those four phases of the instruction’s lifecycle, the more of the hardware that’s used to implement those phases you can put to work at any given moment.
To return to our assembly line analogy, let’s say that each crew is made up of six workers, and that each of the hour-long tasks that each crew per- forms can be readily subdivided into two shorter, 30-minute tasks. So we can double our factory’s throughput by splitting each crew into two smaller, more specialized crews of three workers each, and then having each smaller crew perform one of the shorter tasks on one SUV per 30 minutes.

Stage 1: Build the chassis.
-􏱭 Crew 1a: Fit the parts of the chassis together and spot-weld the joints.
-􏱭 Crew 1b: Fully weld all the parts of the chassis. 
Stage 2: Drop the engine into the chassis.
-􏱭 Crew 2a: Place the engine into the chassis and mount it in place.
-􏱭 Crew 2b: Connect the engine to the moving parts of the car. 
Stage 3: Put the doors, a hood, and coverings on the chassis.
-􏱭 Crew 3a: Put the doors and hood on the chassis.
-􏱭 Crew 3b: Put the other coverings on the chassis. 
Stage 4: Attach the wheels.
-􏱭 Crew 4a: Attach the two front wheels.
-􏱭 Crew 4b: Attach the two rear wheels. 
Stage 5: Paint the SUV.
-􏱭 Crew 5a: Paint the sides of the SUV.
-􏱭 Crew 5b: Paint the top of the SUV.

After the modifications described here, the 10 smaller crews in our factory now have a collective total of 10 SUVs in progress during the course of any given 30-minute period. Furthermore, our factory can now complete a new SUV every 30 minutes, a tenfold improvement over our first factory’s **Program Execution Time** of one SUV every five hours. So by **pipelining** our assembly line even more deeply, we’ve put even more of its workers to work con- currently, thereby increasing the number of SUVs that can be worked on simultaneously and increasing the number of SUVs that can be completed within a given period of time.

Deepening the pipeline of the four-stage processor works on similar principles and has a similar effect on completion rates. Just as the five stages in our SUV assembly line could be broken down further into a longer sequence of more specialized stages, the execution process that each instruction goes through can be broken down into a series of much more than just four discrete stages. By breaking the processor’s four-stage pipeline down into a longer series of shorter, more specialized stages, even more of the processor’s specialized hardware can work simultaneously on more instructions and thereby increase the number of instructions that the pipeline completes each nanosecond.

We first moved from a single-cycle processor to a pipelined processor by taking the 4 ns time period that the instruction spent traveling through the processor and slicing it into four discrete pipeline stages of 1 ns each in length. These four discrete pipeline stages corresponded to the four phases of an instruction’s lifecycle. A processor’s pipeline stages aren’t always going to correspond exactly to the four phases of a processor’s lifecycle, though. Some processors have a five-stage pipeline, some have a six-stage pipeline, and many have pipelines deeper than 10 or 20 stages. In such cases, the **CPU** designer must slice up the instruction’s lifecycle into the desired number of stages in such a way that all the stages are equal in length.

Now let’s take that 4 ns execution process and slice it into eight discrete stages. Because all eight pipeline stages must be of exactly the same duration for **pipelining** to work, the eight pipeline stages must each be 4 ns 􏱮 8 = 0.5 ns in length. Since we’re presently working with an idealized example, let’s pretend that splitting up the processor’s four-phase lifecycle into eight equally long (0.5 ns) pipeline stages is a trivial matter, and that the results look like what you see in Figure 3-8. (In reality, this task is not trivial and involves a number of trade-offs. As a concession to that reality, I’ve chosen to use the eight stages of a real-world pipeline—the MIPS pipeline—in Figure 3-8, instead of just splitting each of the four traditional stages in two.)

![Screen Shot 2020-07-12 at 8 45 28](https://user-images.githubusercontent.com/24994818/87247885-15acdc80-c41c-11ea-81f6-2e100384d4ea.png)

Because **pipelining** requires that each pipeline stage take exactly one clock cycle to complete, the clock cycle can now be shortened to 0.5 ns in order to fit the lengths of the eight pipeline stages. At the bottom of Figure 3-8, you can see the impact that this increased number of pipeline stages has on the number of instructions completed per unit time. 

The single-cycle processor can complete one instruction every 4 ns, for a **Program Execution Time** of 0.25 instructions/ns, and the four-stage pipelined pro- cessor can complete one instruction every nanosecond for a **Program Execution Time** of one instructions/ns. The eight-stage processor depicted in Figure 3-8 improves on both of these by completing one instruction every 0.5 ns, for a completion rate of two instructions/ns. Note that because each instruction still takes 4 ns to execute, the first 4 ns of the eight-stage processor are still dedicated to filling up the pipeline. But once the pipeline is full, the processor can begin completing instructions twice as fast as the four-stage processor and eight times as fast as the single-stage processor.
This eightfold increase in **Program Execution Time** versus a single-cycle design means that the eight-stage processor can execute programs much faster than either a single-cycle or a four-stage processor. **But does the eightfold increase in completion rate translate into an eightfold increase in processor performance? Not exactly**.

# 	* [Program Execution Time and Completion Rate](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35) 

If the program that the single-cycle processor in Figure 3-6 is running consisted of only the four instructions depicted, that program would have a **Program Execution Time** of 16 ns, or 4 instructions 􏱮 0.25 instructions/ns. If the program consisted of, say, seven instructions, it would have a program execution time of 7 instructions 􏱮 0.25 instructions/ns = 28 ns. In general, a program’s execution time is equal to the total number of instructions in the program divided by the processor’s instruction **Program Execution Time** (number of instructions completed per nanosecond), as in the following equation:

Program Execution Time = (Number of instructions in Program ) / (instruction completion rate)

Most of the time, when I talk about **processor performance** in this book, I’m talking about **Program Execution Time**. One processor performs better than another if it executes all of a program’s instructions in a shorter amount of time, so **reducing program execution time is the key to increasing processor performance**.

In the case of a non-pipelined, single-cycle processor, the instruction **Program Execution Time** (x instructions per 1 ns) is simply the inverse of the instruc- tion execution time (y ns per 1 instruction), where x and y have different numerical values. Because the relationship between completion rate and **Instruction Execution Time** is simple and direct in a single-cycle processor, an nfold improvement in one is an nfold improvement in the other. So improving the performance of a single-cycle processor is really about reducing instruction execution times.

With pipelined processors, the relationship between **Instruction Execution Time** and **Program Execution Time** is more complex. As discussed previously, pipelined processors allow you to increase the processor’s completion rate without altering the instruction execution time. Of course, a reduction in instruction execution time still translates into a completion rate improvement, but the reverse is not necessarily true. In fact, as you’ll learn later on, **pipelining**’s improvements to completion rate often come at the price of **increased** instruction execution times. This means that for pipelining to improve performance, the processor’s completion rate must be as high as possible over the course of a program’s execution.
**


# 	* [The Relationship Between Completion Rate and Program Execution Time](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)
# 	* [Instruction Throughput and Pipeline Stalls](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)
# 	* [Instruction Latency and Pipeline Stalls](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)
# 	* [Limits to Pipelining](https://github.com/c4arl0s/InsideTheMachine#4-pipelined-execution-35)



