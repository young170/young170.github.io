---
layout: post
title: "[Study] Operating Systems"
subtitle: "Study of Operating Systems Ch15+."
categories: Study
tags: [Operating Systems]
---

### Introduction
This entry contains the notes of ch15 of Operating Systems.

### Questions
* What if free had the size to be freed?
* Why does the header block have a magic number?
    > The magic number in the header block is a special value that is used to validate the integrity of the header block. It is typically a fixed value that is stored in a predefined location in the header block. When a memory allocation request is made, the operating system checks the magic number in the header block of the requested memory block to ensure that the block is valid and has not been corrupted.  If the magic number is not present or has been changed, this indicates that the header block has been corrupted and the memory allocation request is rejected. This helps to prevent memory-related errors, such as buffer overflows and memory leaks, which can cause system crashes or security vulnerabilities.
    * What are some cases it is corrupted?
    > Buffer overflow: If a process writes beyond the end of a memory block, it can overwrite the header block of the next memory block in the linked list, corrupting its contents including the magic number. Memory leak: If a process forgets to free a memory block, the operating system will eventually run out of memory, and the memory allocator may allocate a new block that overlaps with the header block of an existing block, corrupting it. Pointer errors: If a process mistakenly writes or reads to an invalid or uninitialized pointer, it can overwrite the header block of a memory block, causing the magic number to become corrupted. Hardware or software errors: Power outages, hardware failures, and software bugs can cause memory corruption, including the corruption of the header block.
    * Is the value constant for all memory?
    > The predetermined constant value used to check the magic number in the header block is usually hard-coded into the memory allocator or operating system code. In the case of the GNU C Library (glibc), the magic number used in the header block is 0xdeadbeef, and this value is defined as a constant in the source code of the glibc library. Other memory allocators or operating systems may use different magic numbers, and these values will be similarly defined as constants in the corresponding code.
