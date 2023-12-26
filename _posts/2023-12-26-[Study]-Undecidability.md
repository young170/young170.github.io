---
layout: post
title: "Undecidablity"
subtitle: "Turing Machine, Universal Turing Machine, Decidable, Recognizable"
categories: Study
tags: [Computability]
---

## Turing's Proof

1. Design a turing machine (TM) that can compute all decidable languages
1. Prove there exists a TM that can simulate a TM, i.e. the Universal Turing Machine (UTM)
1. With the hypothesis, can the UTM compute all (not only decidable) languages?
1. Using Cantor's Diagonalization theorem, prove there exists uncomputable languages
1. Show relation between an uncomputable language (Language of the diagonalization, $L_d$) and the complement of the language of the UTM ($\overline{A}_{TM}$)
1. By constructing a UTM ($H$) over a recognizer ($R$) over the language ($\overline{A}_{TM}$), prove $H$ is a TM of $L_d$
1. This makes $H$ and $R$ both have identical accept and reject conditions
1. Because $\overline{A}_{TM}$ is the complement works as the complement of the UTM, the input TM ($M$) rejects when the given input string is the encoded version of itself ($\langle M \rangle$).
1. This makes the language of $H$ ($L_H$) the language of the diagonalization $L_D$
1. $L_D$ is $\notin$ $RE$ (Recursively Enumerable, Turing-Recognizable)
1. Therefore, $\overline{A}_{TM}$ $\notin$ $RE$ $\blacksquare$

## Is $R \subseteq RE$ ?
Proving this quite simple:

### Theorem
$A_{TM} \notin R$

### Proof
By contradiction, assume $A_{TM} \in R$. Since $R$ is closed under complement, $\overline{A}_{TM} \in R$ is also true.<br>
Using our assumption, $\overline{A}_{TM} \in RE$ follows. However, this is proven false in Turing's Proof (prev heading).<br>
$\therefore A_{TM} \notin R$ and $R \not = RE$ $\blacksquare$

## Halting Problem
This leads us to the famous *Halting Problem*

### Problem Definition
The problem definition itself is simple: "Given a TM $M$ and string $w$, does $M$ halt on $w$?"<br>
We shall define this problem as a languag, $HALT$. Is $HALT \in R$? Is $HALT \in RE$?<br>

### Is $HALT \in RE$ ?
This is quite simple.<br>
Using a UTM, $H$, and input $\langle M, w\rangle$, $L_H = HALT$.<br>
$\therefore HALT \in RE$ $\blacksquare$

### Is $HALT \in R$ ?
Our goal is to prove the $HALT$ language is undecidable.

### Theorem
$HALT \notin R$

### Proof
Steps:
* Using proof by contradiction, assume $HALT \in R$
* Using a decider for $HALT$, construct a decider for $A_{TM}$
* Since $A_{TM} \notin R$
* Conclude, $HALT \notin R$

## Conclusion
It is important to remember a few things. Although $A_{TM}$ and $HALT$ are undecidable, they are recognizable.<br>
Meaning, we can't know for sure (decide) the correct outcome, but we can recognize (in other words... accept/reject) it. However, $RE$ mays never halt at all!<br>
