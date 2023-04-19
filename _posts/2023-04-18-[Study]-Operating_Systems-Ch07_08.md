---
layout: post
title: "[Study] Operating Systems"
subtitle: "Study of Operating Systems Ch07+Ch08."
categories: Study
tags: [Operating Systems]
---

### Introduction
This entry contains the notes of ch07 & ch08 of Operating Systems.

### Prerequisites
* Mechanism
    * The actual implementation to solve the desired goal.
* Policy
    * A general algorithm to decide on what to execute.
* Assumptions
    1. Each job runs for the same amount of time.
    2. All jobs arrive at the same time.
    3. Once started, each job runs to completion.
    4. All jobs only use the CPU (i.e., they perform no I/O).
    5. The run-time of each job is know
* Throughput
    * the total number of processes completed per unit of time.
* Turnaround
    * the time at which the job completes minus the time at which the job arrived.
    * $\ T_{turnaround} = T_{completion} - T_{arrival}$
* Responsiveness
    * the time from when a job is arrived to the first time it is scheduled.
    * $\ T_{response} = T_{firstrun} - T_{arrival}$

### Multi-Level Feedback Queue
One of the explanations about MLFQ stood out to me.
> (KOR) 우선 순위를 조금씩 낮추어 다른 작업들과 **경쟁**하도록 조정하는 것이라 할 수 있겠다.
<br>(ENG) By lowering the rank, it makes the process **compete** with other processes.

### Tuning MLFQ And Other Issues
Other chapters I left out seem well noted enough on the notes.
Or I'm going to add after midterms..

After revising MLFQ multiple times, we finally arrived at a semi-feasible approach.
However, a few issues/questions remain.
* How many queues in a MLFQ?
* How long should the time slice for a queue be?
    * Should the time slice be different for each queue?
* How ofter should "boosting" occur, to deal with starvation?

These all connect to the idea: How does this concept affect throughput?
OS exists to maximize efficiency.

Some example problems one could try answering:
1. Suppose that there is a system using a multi-level feedback queue as the process scheduler.<br>Discuss the relation between the number of the priority levels in the process and the overall performance.
2. Suppose that you have a system that runs multiple similar processes with the Round-Robin scheduling algorithm. And you want to find a chance to improve the throughput of the system for using Round-Robin.<br>Explain how you can find this change and what kinds of actions you can possibly take for this system.

My answers:
1. Increasing the number of priority levels (or queues) will increase the performance, most of the time.
Before explaining why, I will set an assumption. As the priority gets lower, I assume the time slice gets longer. So this means the processes at the top priority are maximizing CPU burst due to their minimal need of time. Having a specific range of time slices divided up into multiple queues will help prioritize processes. However, if the number increases too much, the cost of managing the queues + boosting will be very costly.
<br>Even if the assumption is removed, the results will be similar. However, the processes will tend to gather up more at the lowest priority queue. Therefore, executing in a RR (RoundRobin) fashion until boosting happens. On the other hand, this may deal with starvation better than the first approach.
2. First, an analyzation is needed. Some possible analyzes that could be made are: measuring throughput, turnaround, reponse time. One of the main reasons RR may be underperforming is due to the time slice. If the timeslice is too small, the cost of context switch may be costly. If it is too large, it may cause other processes to wait causing a loss in throughput.