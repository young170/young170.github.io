---
layout: post
title: "[Study] Operating Systems"
subtitle: "Study of Operating Systems Ch02."
categories: Study
tags: [Operating Systems]
---
### Introduction

This entry contains the notes of intro & ch02 of Operating Systems.`<br>`
PDFs of my handwritten notes and lecture slides will be added.

#### Abbreviations

* HW : hardware
* SW : Software
* CA : Computer Architecture

### What is Operating System?

* A program **first** loaded when a computer starts
  * Then what is a computer?
  * If it computes instructions, then what is the difference between a calculator?
    * If you think about it, they both compute instructions, store memory, and have I/O. Then what is the difference?
    * The biggest difference can be found in **why** they are operated. Calculators process a specific operation, while a computer processes tasks given in a form of a program.
    * Simply, it can be viewed as a **generalized** calculator. Hence, a **Universal Computing Machine**.
      * It receives programs (sequence of instructions) and more importantly, the programs are reused.
      * The PC (Program Counter) makes this possible.
* As computers grew in size in both HW & SW, a suite of programs were needed to operate a computer system **effciently** and **effectively**.
* The main approach (which will be constantly reannounced throughout the series) is **virtualization**.
  * Many approaches are taken to realize this goal. It can all be summed up to the solution: **Kernel**.

### Kernel

* The kernel is HW specific and is always loaded. Then what is the difference with CA? CA provides **primitive** instructions, Kernel **enriches** instructions.

1. Helper

   * One of the key steps of virtualization is to provide a common interface among programs.

     * Why?

     > By providing a common interface, virtualization abstracts the underlying hardware and software details and provides a standardized way for programs to interact with the virtualized environment. This allows programs to be isolated from each other and from the underlying host, which enhances security, stability, and resource management.
     >
   * The kernel "helps" by containing libraries. These libraries have "helper" functions that provide control to HW devices, and communication between programs.
2. Officer

   * Let the "helper" functions **exclusively** process sensitive operations under protection.
   * This breaks the abstraction concept.

     * abstraction:

     > process of hiding complex details of a system and presenting a simpler and more manageable interface to users or other programs.
     >
3. Governor

   * Not only controlling the requests, it also regulates resources. In this perspective it is more like a governor.
