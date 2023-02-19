---
layout: post
title: "[Study] Computer Architecture"
subtitle: "Study of Computer Architecture & Organization."
categories: Study
tags: [Computer Architecture]
---

### Introduction
My study notes of Computer Architecture & Organization.
Took the class during 22-2.
Note written during 22-Winter.

---

### What is Computer?
#### The Von Neumann Architectue
![](https://velog.velcdn.com/images/young170/post/693da0d8-4467-46e9-aeba-b0b5d0413c94/image.png)
Just like coding, the basic architecture of a computer has an input -> process -> output.

#### Typical computer organization
![](https://velog.velcdn.com/images/young170/post/bdd4f3cd-c430-483a-b0b7-2c4fcf11844e/image.png)

---

### Instruction Set Architecture
#### ISA
- Processor's Instruction set
    - The set of assembly language instructions
- Programmer accessible register within processor
    - Size of each programmer-accessible registers
    - Instruction that can use each register
- Information necessary to interact with memory
    - Memory alignment
- How processor reacts to interrupt from the programming view point
#### MIPS
- Goals of instruction set design for MIPS
    - Maximize performance and minimize cost, and reduce design time (of compiler and hardware)
    - ***By the simplicity of Hardware!***
- MIPS design principles
    - Simplicity favors regularity
    - Smaller is faster
    - Make the common case fast
    - Good design demands goom compromises

#### Basic Procedures

![](https://velog.velcdn.com/images/young170/post/d732445a-5c31-4029-af71-2f97b2dad9ea/image.png)

> How procedures are conducted. *Control* is transferred.

![](https://velog.velcdn.com/images/young170/post/cd0409f9-33ab-40c0-8759-46bb4fe74995/image.png)

> Uses *stack* to implement the design principles. Makes code simple, therefore making the common cases fast.

### Translation and Startup

> Like I learned in DS, the whole process is depicted as the following (In DS, the Linker & Loader was the focus; In CA, the Assembler was focused; Personally, I want to learn more about the Compiler..):

![](https://velog.velcdn.com/images/young170/post/e723a7ef-2f1b-44d6-9057-2d1943f43eb4/image.png)

### Loading a Program
#### Load from image file on disk into memory
1. Read header to determine segment sizes
2. Create virtual address space
    * Done by the OS
    * Virual address & memory explained later..
3. Copy text and initialized data into memory
4. Set up arguments on stack
5. Initialize registers (including $sp; stack pointer, $fp; frame pointer, $gp; global pointer)
6. Jump to startup routine
    * Copies arguments to $a0, ... and calls main
    * When main returns, do exit syscall

### Pipelining
#### Pipelined Datapath
![](https://velog.velcdn.com/images/young170/post/3674a097-830d-4674-8859-e60578de9b2d/image.png)

> There exists 5 stages
1. IF : Instruction Fetch
2. ID : Instruction Decode
3. EX : Execute Operation | Calculate Address
4. MEM : Access Memory
5. WB : Write Result Back to Register

> Control signals are also passed along the pipline because the next decoded instruction may *overwrite* the control signals. Saving the control preserves the action to be done.

#### Hazards
> As instructions are executed continuously right after another, conflicts may happen.
* There exists 3 classes
    * Structure Hazards
        * A required resource is busy
    * Data Hazards
        * Need to wait for previous instruction to compelete its data read/write
        * Solutions : forwarding, stalling, compiler scheduling
    * Control Hazards :
        * Deciding on control action depends on previous instruction
        * Solutions : stall, reducing branch delay, branch prediction

#### Exceptions and Interrupts
* Exceptions
    * "Unexpected" events within the CPU
        * overflow, ...
* Interrupt
    * From an external I/O controller
* Performance is sacrificed to deal with them
    1. Read the problem
    2. Transfer to related handler
    3. Determine the required action
    4. If restartable
        * Take corrective action
        * EPC (Exception Program Counter) to return to program
    4. Else terminate program

### Performance
> As one of the goals of DS, Algorithm, OS, etc. is ***efficiency***, calculating performance is crucial.

![](https://velog.velcdn.com/images/young170/post/902050e2-8b3f-4bc3-9960-4e6b48fd1b2e/image.png)

> CPI : Clocks Per Instruction

### Memory
#### Memory Hierarchy
![](https://velog.velcdn.com/images/young170/post/e36bf973-9cb1-4d38-865f-44aa2578341a/image.png)

> Nothing to explain.. as intuitive as it can be.

#### Principle of Locality
* Temporal Locality
    * Items accessed **recently** are likely to be accessed again soon
    * e.g. loops
* Spatial Locality
    * Items **near** those accessed reccently are likely to be accessed soon
    * e.g. array data

#### Memory Heirarchy Levels
* Hit : access satisfied by upper level
* Miss : accessed data is absent so block copied from lower level.

#### Cache
![](https://velog.velcdn.com/images/young170/post/c1c2707d-7706-4a75-9340-b9bc87f79dc6/image.png)
* Direct Mapped
    * One *tag* per *block*.
    * position of block = (num_block) % (num_cache_block)
* Set Associative
    * Multiple *tag* per *block*.
    * position of block = (num_block) % (num_cache_set)

#### Multilevel Caches
* Primary Cache
    * Attached to CPU
    * Small, but fast
* Level-2 Cache
    * Services misses from primary cache
    * Larger, slower, but still faster than main memory
* Main Memory
    * Services misses from L-2 cache
* Some high-end systems include L-3 cache

#### Cache Coherence
* Suppose 2 CPU cores share a physical address space
    * If CPU A writes 1 to X
        * CPU A and CPU B's content would be different
    * [Snoop protocol] (https://www.techopedia.com/definition/332/snooping-protocol)

#### Writes
* On data-write hit
    * Write Through
        * Update cache & memory
    * Write Back
        * Update cache only

### Virtual Memory
**This topic is very important**
![](https://velog.velcdn.com/images/young170/post/9fb2573d-a3b1-451c-aa59-7aa00e5c5527/image.png)
> Virtual page number is used to access virtual address in TLB or/then Page table. Then the actual physical page address in the table is used to access Physical memory or Disk storage.

![](https://velog.velcdn.com/images/young170/post/96433c0c-e19d-4a9b-88d6-28758b870355/image.png)
> This second diagram shows a better picture of the flow.

#### SIMD
* Operate elementwise on vectors of data
    * All processors execute the same instruction at the same time
    * Simplifies synchronization
    * Reduced instruction control hardware
    * Works best for highly data-parallel applications
        * e.g. GPU

### BUS
* Shortened form of the Latin *omnibus*.
* Shared communication channel
    * Parallel set of wires for data and synchronization of data transfer
    * Can become a [bottleneck] (https://www.techopedia.com/definition/14630/von-neumann-bottleneck)
* Performance limited by physical factors
    * Wire length, number of connections
* More recent alternative : high-speed serial connections with switches
    * Like networks

### I/O
#### Memory-Mapped I/O
* Certain adresses are not regular memory addresses
* Instead, they correspond to registers in I/O devices
* They are not accessed directly, only through through address + registers.

#### Polling and Interrrupt
* OS needs to know when
    * I/O has completed an operation
    * I/O has encountered an error
* Polling
    * OS checks the status register to check if it is time for next I/O operation
* Interrupt
    * When the I/O device completes an operation or needs attention, it "interrupts" the processor.
    
### Multithreading
* Performing multiple [threads] (https://www.geeksforgeeks.org/thread-in-operating-system/) of execution in parallel
* Fine-grain Multithreading
    * Switch threads after each cycle
* Coarse-grain Multithreading
    * Only switch on long stall
    * e.g. L-2 cache miss
* SMT
    * Schedule instructions from multiple threads
