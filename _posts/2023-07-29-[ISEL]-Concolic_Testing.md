---
layout: post
title: "[ISEL] Concolic Testing 07/29/23"
subtitle: "Study of concolic testing"
categories: ISEL
tags: [SE]
---

### Introdution to Concolic Testing
**Conc**rete + Symb**olic** Testing<br>
Referenced the following source: [DART: Directed Automated Random Testing, Presented by Markus](https://people.cs.vt.edu/~ryder/6304/lectures/12-DART_Godefried_PLDI2005_MarkusK-slides.pdf)

### Overview of Concolic Testing
1. Execute with random (**concrete**) inputs (when you have no information go for the low computation approach)
2. Collect path constraints (dynamic execution)
    * Each statemnent of the program is modeled (**symbolic**) to their semantic meaning
3. One of the branches in the path constraint is negated
    * The formula is given to the solver
4. The solver finds values that explore new paths based on the path constraints
5. Repeat step 2

### Effectiveness of DART
Detecting bugs that require a certain sequence (e.g. two integer sequences) lead to high complexities (e.g. 1 out of 2^64). Using DART's aprroach this is solved quite quickly

### Review for Myself
Random testing **requires** low computation (may result in the other), but fails to explore **diverse** paths (leads to low **coverage**)
* Seems to contradict intuition
* This behaviour is due to the characteristics of programming. Conditions, etc.

When increasing coverage by exploring new paths (branches), the **last** condition is negated
* Compared to negating the first condition (breadth-first-search), it is a depth-first-search approach

DSE (Dynamic Symbolic Execution) is the contains Concolic testing & EGT (Execution-Generated Testing)<br>
One of the key advantages in mixing concrete and symbolic execution is that imprecision caused by the interaction with external code or constraint solving timeouts can be alleviated using concrete values. However, due to simplification, it could loose completeness.

### Questions & Possible Answers
* If modifying a single variable's value successfully explores a desired path would changing the other variable(s) value(s) be better?
    * No, provide same context to concretize the condition
    * Yes, it could possibly update a new condition without harming the execution path
        * Considers paths taken after the condition doesn't matter
* Why would a DFS (depth-first search) be utilized?
    * Not sure.. has more applications, the idea may be connected with sorting? or penetrating?
    * The approach seems to exclude the details so may be its an experimental thought
* Is NULL considered in the generation phase?

### Discussion
In programs that are not small, *path explosion* occurs. Prioritizing exploration paths is needed in the least.
* Execute paths ran the fewest number of times
* Favor mutating paths that explore "deeper"
    * [*Hybrid Concolic Testing*](https://wcventure.github.io/FuzzingPaper/Paper/ICSE07_Hybrid.pdf), R. Majumdar and K. Sen
    * They bring a similar idea of interleaving random testing and concolic execution