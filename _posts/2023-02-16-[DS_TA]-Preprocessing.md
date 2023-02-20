---
layout: post
title: "[DS TA] Preprocessing"
subtitle: "Creation of lab work - Preprocessing"
categories: DS TA
tags: [DS, Linux]
---

### Introduction
This is my notes on the order + details of lectures/labs as a TA.

---

### Code
```
#if 1
#include "stdio.h"
#endif

#ifdef DEBUG
#define DPRINT(func) func;
#else
#define DPRINT(func) ;
#endif



int main() {
    #if 1

    #ifdef DEBUG
    printf("\nDEBUG - Hello World!\n");
    #else
    printf("\nHello World!\n");
    printf("Well Done! Now try compiling with the DEBUG option.\n\n");
    #endif

    DPRINT( printf("Notice these lines are also executed.\n"); );
    DPRINT( printf("Next try switching the #if 1 -> 0 at line 41 & 54\n"); );
    DPRINT( printf("Then compare the results of the file main.i with step(1).\n\n"); );

    #else
    /*
    Will this line appear in the main.i file?
    If you add comments explaining at least 3 lines of the code you might get some bonus points!
    */
    #endif
}
```

### Instructions
```
 * Usage:
 * 	step(1). $ gcc -E main.c > main.i
 *  - This redirects the output of the preprocessed main.c to the main.i file.
 *      - More about output redirection: @link https://www.guru99.com/linux-redirection.html
 *  - Take a screenshot of the contents of main.i
 *      - $ cat main.i
 *          - To view the contents.
 * 
 *  2. gcc -o filename main.c
 *  - To create an executable file with a desirable name.
 * 	- Then follow the instructions printed!
 * 	- Have fun!
 * 
 * God is good, all the time!
 * Happy Coding~~
```

### Explanation
I suggested to remove all materials related to sortings. This was a very bold thing to do because(as far as I know) all Data Structures taught sorting algorithms.
The reason behind this was from my experience(2022-1). The corresponding chapter also taught debugging, assertion, NMN, DRY, etc.
However, I missed the important concepts and was too focused on implementing the algorithms. I wanted to fix this problem.

I made an easier lab to be involved with so that students could learn the concepts easier.
The lab deals with the following topics: #ifdef, #if 0/1, #else, #endif, #include.

By using #ifdef, students can learn the applications of the DEBUG statements.
By using #if 0/1, students can learn to quickly switch between algorithms.
By using #include, students can learn optimization is also applied to "minor" statements.