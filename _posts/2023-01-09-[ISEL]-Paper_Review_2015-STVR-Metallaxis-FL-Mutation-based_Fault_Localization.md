---
layout: post
title: "[ISEL] Paper Review: Metallaxis-FL: mutation-based fault localization"
subtitle: "Review of papers."
categories: ISEL
tags: [SE]
---

### [Metallaxis-FL: mutation-based fault localization](https://onlinelibrary.wiley.com/doi/abs/10.1002/stvr.1509)

#### Goal:
1. A fault localization approach based on mutation analysis that uses mutants and links them with the faulty program places.
2. Show it is more efficient than other fault localization approaches such as spectrum-based, block-based or branch-based test suites.
3. Solve/Prove the most controversial aspect of mutation analysis: scalability.

#### Points:
1. Mutants could provide sufficient guidance for localizing known but not located faults.
2. Test cases that are able to kill mutants would enable accurate fault localization.
3. Mutation alternatives such as mutant sampling can be utilized to support the fault localization activity.

#### Knowledge:
* Provoking program failures forms the primary aim of the testing process.
* Debugging has two phases: (1) identifying the faulty program places, (2) fixing the fault.
* After the localization process, the programmer has to check the ranked statements in a decreasing suspiciousness order in order to find and fix the fault.
* It is preferable if faulty statements appear at a higher position because less effort is required.
* RQ1 : How effective is the mutation-based fault localization approach? Is this approach more effective in assisting fault localization process than the statement-based one?
	* Benefit researchers in seeking ways to reduce the program debugging expenses.
* Results indicate that the mutation-based approach out-performs the statement-based one.
* Additionally, suggests that whenever the statement-based approach achieves a better effectiveness, this difference is not so important.
* RQ2 : What is the impact of test adequacy criteria on the effectiveness of mutation and statement-based fault localization techniques? (block, branch and mutation adequate test suites were used)
	* Show whether the use of testing adequacy criteria is practical for the fault localization process.
	* Answers whether mutation-based localization approach is worthwhile when employing a basic testing approach.
* Significantly better score values when utilizing test suites adequate with respect to mutation than those based on random, branch or block criteria are experienced.
* A mutation-based localization approach outperforms the statement-based one in all cases, even when using block adequate test suites (statistically significant).
* RQ3 : How is the effectiveness of mutation-based fault localization technique affected by using randomly selected mutant sets? (10%, 20%, 30%, 40% and 50% were used)
	* Attempts towards dealing with the computational demands of mutation analysis.
* Mutation-based faults were able to localize faults better than statement-based ones. Even techniques with sampling ratios of 10%. This argues that mutation alternative methods can be effectively utilized to assist the fault localization process.
	* Why is this true? Maybe because statement-based & mutation analysis have similar approaches. They both check for the location by iteratively changing/mutating. The reason why mutation analysis scores better could be that mutation analysis has a concrete set of operators. These operators are utilized to fix the fault or find the fault. While statement-based has the burden to test countless times (for accuracy).
* RQ4 : How effective is the mutation-based fault localization approach when it is applied on large software subjects?
	* Explores the scalability of the mutation-based approach on larger programs.
* Whenever the mutation method is more effective, this indicates a huge difference. In the opposite situation, that is, when the statement-based approach is better, the difference of the two methods is not important.
	* Wish they would give exact criteria on the judgment.
	* The difference is evident, but sometimes there might be more to what is visible.
* Test sets were constructed from the available test suite pool using a certain procedure.
	* Randomly selects one test case that exposes the considered fault and put it in the CurrSet
	* If the CurrScore of the CurrScore is less than the SetScore (threshold), remove the test case from the CurrSet.
* Mutant-faults were removed from the considered mutant set utilized by the localization method.
	* This is to decrease the number of mutants that are used and its effectiveness
	* Mainly to avoid any bias introduced by the mutant-faults and the mutation-based fault localization approach.
* In cases of faults that involve omitted statements, assume that the faults are found if the programmer inspects a statement next to the missing statement (close enough).
	* Otherwise, there will never be such a mutated or executed statement.
	* Also variable initializations or constant assignment statements.
		* It is assumed that these faults will be located whenever the programmer inspects a statement using the constant or faulty defined variable.
* The key feature that attributed to the result of mutation-based fault localization outperforming the statement-based one is the fact that when a fault is executed, it is not always manifested to a failure.
* As mutants are considered only when they are “killed”, bias is applied to statements that affect the program’s output more (the consideration of killing is dependent on the output).
* Statement-based fault localization usually assigns identical ranks to statements in the same block. Mutant analysis is able to capture the data flow and differentiate between program statements belonging to the same blocks (not dependent on the program structure).
* The paper introduces a good future work idea & a possible solution.
	* Finally, it is noted that the efficient introduction and execution of the sought mutants is a matter not addressed by the present paper and has been left open for future research. A possible solution could be the use of an incremental process. Thus, some mutants could be selected either at random or on the basis of some of their characteristics, that is, their kind or their suspiciousness value as computed by lightweight fault localization approaches. Then, their suspiciousness can be calculated, and the statements with score 1 are reported to the user. Thus, the programmer can start the debugging process before the whole process is finished. In case the fault is not found, then the process could continue with other mutants.
* Errors affecting the generation, compilation and executions of mutants may influence the decision of whether a mutant is being killed or not.
	* Several manual checks have been undertaken on all the utilized subjects
#### Terminology:
* Fault Localization : Identifying defective program parts given test execution failures.
* Coupling Effect Assumption : Test data that distinguishes all programs differing from a correct one by only simple errors is so sensitive that it also implicitly distinguishes more complex errors.
#### Questions:
* If the paper is able to answer Point 1, then is it possible to use mutation FL after a quick and efficient (but less accurate) method? The other method is used to detect faults by some tests, and mutation FL is for finding the exact place.
* This paper keeps proposing that mutation is an alternative (to structural code coverage). However, should it be limited to be an alternative? What about cooperation?
	* Does Combine FL answer this question?
* Don’t understand the following paragraph : Only the executable statements were ranked in the present experiment because of the function of the developed tool (Section 4.3). Additionally, to avoid repeating the mutation analysis process for all considered faults, the localization process was performed on the original (correct) program versions by treating the ‘correct’ program as being faulty one and the faulty as being ‘correct’. This restriction was applied only on the programs of the benchmark set 1 in order to complete the experiment with reasonable resources (vast resources are typically needed by mutation analysis). Thus, it helped not to repeat the process for each considered fault (the number of faults considered by the benchmark set 1). It is noted that on the benchmark set 2, the fault localization process was performed on the faulty programs.
* Further room of improvement whether mutation adequate test suites can be improved to assist further fault localization process.
* How to judge whether samples show “statistically significant” differences.
* Page 18, second paragraph, it says, “Although there is no fair way to compare the results of the two sets, due to the differences in the construction of the test suites, an inspection of Figures 3, 5 and 7 reveal the effectiveness similarities between the two program sets”. What is meant by the difference in construction? How can they still conclude the similarity of effectiveness?

