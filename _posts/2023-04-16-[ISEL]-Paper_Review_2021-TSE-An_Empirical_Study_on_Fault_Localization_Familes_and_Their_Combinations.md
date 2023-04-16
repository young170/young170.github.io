---
layout: post
title: "[ISEL] Paper Review: An Empirical Study of Fault Localization Families and Their Combinations"
subtitle: "Review of papers."
categories: ISEL
tags: [SE]
---

### [An Empirical Study of Fault Localization Families and Their Combinations](https://ieeexplore.ieee.org/document/8607117)

#### Goal:
1. Resolve how techniques are correlated to each other.
2. Measure the time cost of different fault localization methods.

#### Points:
1. Background
	* Introduces 7 families of fault localization.
	* Introduces the learning to rank model for combining different techniques.
2. Experiment
* Determining faults.
* Case of multiple faults.
* Elements with identical suspiciousness scores.

#### Knowledge:
* FL Methods
	* Spectrum-Based FL
		* The program is measured per spectrum(code coverage).
		* Uses risk evaluation formulas(Ochiai, DStar, etc) to calculate suspiciousness.
	* Mutation-Based FL
		* Unlike SBFL, which considers if it(the program statement, or in some cases method) is executed, it considers whether it affects the result.
		* Usually, One order Mutants(mutations with a change of one expression) are used.
			* Metallaxis assigns each mutant a suspiciousness score using the Ochiai formula.
	* Program Slicing
		* Creates a subset of the program containing the elements that potentially affect the criterion.
		* Two methods of Program Slicing:
			* Static:
				* Uses source code and takes in mind all possible(potential) paths of the execution
			* Dynamic:
				* Take in mind the exact execution path of a specific input.
	* Stack Trace Analysis
		* Similar to debugging, stack trace contains active function calls at the point of defect.
	* Predicate Switching
		* Similar to MBFL, it examines the change of execution results.
		* Conditional expressions are forcefully switched to redirect the path(or outcome).
	* Information Retrieval-Based FL
		* Read the bug reports and rank via relevance to it.
		* Does not require program execution information.
	* History-Based FL
		* Maybe used for fault prediction.
		* Uses Development history.
* RQ1: Effectiveness of standalone FL
	* As expected SBFL is the best standalone.
	* Also, Stack trace is the best for crash faults
	* Surprisingly, Predicate switching is not the best on “predicate-related” faults.
		* MBFL performs better. They have similar mechanisms, but MBFL is able to specifically rank the predicates.
* RQ2: Correlation between techniques
	* Strongly correlated techniques only exist in the same family, but not all techniques in the same family are strongly correlated.
* RQ3: Effectiveness of combined FL
	* Significantly outperformed any standalone technique.
	* The performance when the technique was standalone, doesn’t determine the effectiveness as a combined one.
* RQ4: Run-time cost of standalone vs combined
	* Slower as the program requires multiple iterations.
	* Including techniques from the identical family always improves the result(not by much).
* RQ5: Statement vs Method granularity
	* RQ1 and RQ3 are the same at method granularity.
* RQ6: Combined approach vs state-of-the-art techniques
	* Outperformed all.
	* However, only the outputs were considered. In practice(real-life) run-time cost is a crucial standard.
		* reporting run-time costs of these approaches are left for future work.
* How to determine faults
	* When deleting:
		* The deleted statement is the fault.
	* When inserting:
		* The statement after the inserted statement is reported.
			* It indicates the location for a developer to change the defect.
* Implications
	* SBFL was the trend.
		* How about now?
	* Optimizing efficiency is just as important as quickly/accurately locating the fault.
		* Need to test: (accurate but expensive) vs (less accurate less expensive)
	* Information sources(data) may be the more critical topic to research.

#### Terminology:
* Mutation analysis
	* Looks(analyzes) for changes in mutations.
* Fault prediction
	* Ranks a program by the likelihood to be defective.
* Critical predicate
	* The predicate that makes a failed test case pass.
* Crash faults
	* Defects that cause the program to crash.
* Cross validation
	* Accuracy = Average(Accuracy^1, …, Accuracy^k)

#### Questions:
* What are other factors that could be criteria of a good fault localization approach other than performance and cost?
* What could be other inputs/outputs of a fault localization technique other than bug reports, development history?
* Why aren’t the statements before the inserted statement reported?
* Why are SBFLs strongly correlated with each other, but MBFLs not?
* How about combining FL and Fuzzing? Will RQ3 apply here too?
* When combining will the order of the techniques being executed matter?
* What if a statement shows opposite results? Which one is determined?
