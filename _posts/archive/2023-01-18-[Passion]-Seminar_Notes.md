---
layout: post
title: "[Passion] Seminar Notes"
subtitle: "Collection of seminar notes."
categories: Passion
tags:
---
### Introduction

This is my collection of notes took during seminars I participated in. Sometimes as a presenter, discussion participant, or sometimes a normal listener:)

---

### November 25th, 2022

* Graduate school seminar - Jooyong Yi
* *Automated Bug Fixing*

Formal verification
	semi
SapFix

generate and validate (make and check)
	Search
		genetic-mutation (genprog)
	template
		the candidates are created(similar to both seach and learn) by a designer. [less training, more repairing please]
	learn
		training -> candidates -> validate
		challenge: syntactically incorrect(syntax guided edit decoder) -> similar to dynamical slicing?

Symbolic
	(JH) to dependent on test cases.

semantics
	theorem proval
Minimality:

1. syntactic(ex: limit edit to one edit)
   1. maxSMT(case that satisfies the most clauses)
2. What if the expression can’t be fixed?
   1. Don’t be limited to original. Use patch specifications to make new.
      1. How to get the patch specifications
      2. Find all possible execution paths and test
      3. Don’t know which works, collect
         Slow: FAngelix
         if(foo())
         Use delta debugging to keep it similar (keep some parts (binary search algorithms)) no need to keep all paths

Non-determinisms
**keeping close to the semantically original code, shows better results
	proven(minimal patches are better) -> direction is cleaner

MCMC sampling?

### November 29th, 2022

* Master's defense - Younho Choi
* *Mining and Ranking Static Analysis Alerts*

Terminology :

* Static analysis
  * Process of testing before executing.
* Corner case
* Static linking
* Cross entropy

Usual bug finders were conservative and lightweight. By *lightweight* he meant literally "lightweight". Less rules, etc. If less rules exist greater FP (False Positive) results occur because they don't satisfy the rules and get disregarded as bugs.

2 ways to improve: create super alerts and rank the static analysis alerts.
The second procedure may be executed by detecting the naturalness of software. Specifically, in bytecode.
Now a question is raised, even if naturalness is found, is it plausible for a fix?

Continuing on from this question, the paper answers the following questions: is it generalizable? is it not limited to single statements? is it able to expand?

### December 1st, 2022

* Graduate school seminar - Junghyeon Kim
* *Interdisciplinary Research using Machine Learning and Multi-objective Optimization*

본 강연에서는 최적화란 무엇인지, 최적설계의 과정은 어떻게 진행되는지, 더 나아가 현장에서 발생할 수 있는 다양한 공학 문제들을 해결하기 위해 기계학습(Machine Learning)과 다목적 최적설계 (Multi-objective Optimization) 기법이 어떻게 융합되고 관련 해결책을 제시하는지에 대한 내용을 간단한 수학문제와 실제 기업과의 공동연구사례 등을 활용하여 소개하고자 한다. 뿐만 아니라, 공학분야에서 적용될 수 있는 ASDL연구방법론 (https://www.asdl.gatech.edu/) 을 소개함에 따라 학부연구 혹은 대학원연구를 희망하는 학생들에게 연구방법에 대한 큰 그림을 제공하고자 한다.

최적화하는 과정:
The process of optimizing:

1. 실생활 문제 정의
2. 수학적 풀이
3. 일상 constraint 적용(?) 메일 드려보기.

It’s all about feasibility & optimization
Real world problems have unimaginable constraints
Recommends trying to solve real world problems

### January 18th, 2023

[Five Stones] 세미나(1월 18일 2023년, 이재훈 박사과정 학생), ChatGPT

Generative AI : create novel content.
GPT-3 : large language model
Reinforcement Learning from Human Feedback.

Transformer model

In the case of ChatGPT, how will the reward be given (Reinforcement Learning is based on actions & rewards)?
	- It is hard to decide if a question is right or wrong.
At this point Human Feedback comes in. https://docs.google.com/document/d/1MJCqDNjzD04UbcnVZ-LmeXJ04-TKEICDAepXyMCBUb8/edit
	- Human participants manually label the data to train it.

The unique feature that separates ChatGPT is, it adds description between answers.

The new paradigm of search :ChatGPT collects the data for you and proposes the “answer”.
	- Discussion :
		Technology is always a double edged sword.
			The training is process is maximized by human feedback, but that means bias is inevitable.

1,750억 parameters
GPT-4 has 500조 parameters..
	- What could happen?

Filter bubble
	- Nowadays, it is harder to view the entire picture.
	- Staying neutral.

Discussion :

1. Why is ChatGPT pre-trained? Why stop at 2021?
   1. There are two main categories, constant training vs pre-training.
   2. Monetary issues.
2. Will this overtake Google Search?
   1. It simplifies the process obtaining knowledge.
   2. But the final step of deciding if the answer is correct is a different issue.
3. Where does the copyright of ChatGPT’s answer reside?
   1. Answer : OpenAI has the rights for monetary expressions.
   2. Ben Kim : using the ideas based on its answer won’t have that much issues, but using the exact words may cause problems.
4. Flags occur when using words everyone knows (e.g. “n” word), but happens on Democrats but not Republicans.
5. Same sex marriage, it shows the argument of the opposing side, but represents its own “thoughts”.
   1. What is “hate speech”, etc. is not defined in the actual society, but enforced in ChatGPT.
   2. P Kim : It is inevitable.
6. Constantly training models have a greater issue of ethics and policies.
7. Very amazing that it is possible to capture an image of the wordings. “Attention models”
8. The performance of the model depends on the data (quantity).
   1. Korean is very difficult because of the language’s properties and data quantity.
9. It still can’t create (the act of creation) something that is new (unique). Only stuff we’ve missed.

### January 19th, 2023

* Seminar - 박준혁 석사과정 학생
* *Image Processing using Machine Learning*

영상처리 담당. 주로 classification. 영상처리가 무엇인지, outline대로 진행.
피드백대로 실행결과를 표시

> 다운 받은 데이터 셋 등 파일들을 깃허브 (파일 스트럭쳐) 어디에 넣어야하는지, 깃허브를 베이스로. 상대적 위치로 알리면 더 명확할것 같다는 피드백.
> data와 code를 같은 폴더에 넣으면 깃허브 푸쉬가 안된다 너무 커서.
> 상황을 설명하고, 해결방안 제시.
> 예시로, 깃허브 폴더가 아닌 다른 폴더.

encoder구현해보고, 비교하여 결과 보도록 구성.

> KMOOC처럼 강의 마지막에 퀴즈를 추가하여 제대로 읽었는지 확인할 수 있도록한다.

1. semantic segmentation소개
2. 다양한 모델 직접 구현할 수 있는 코드랩
3. 현대 제철때 사용한 자료 토대로
4. pytorch를 사용했었는데, 변형해서 다른 툴로

평가 매트릭 구현, 설명 추가.
NMS - segm, obj detection때 사용되는 기술들 설명.

* 이달 말까지 완성.

---

### April 4th, 2023

* Seminar - 김대석(ISEL)
* *Automated Vulnerability Detection in Source Code  Using Deep Representation Learning*

지금까지 관련 연구에 한계:

1. 딥러닝을 큰 규모의 소스 코드의 특징으로 학습시킨 것이 없다.
2. 사이즈 상으로나 다양성으로나 부족한 데이터 셋이 쓰였다. 이는 딥러닝을 더욱 잘 학습시킬 수 있는 가능성을 사용하지 않은 한계를 가졌다.

그래서 직접 데이터셋부터 구성하였다.

> Difference between *lexer* & *parser* is needed.

* Labels mainly done by static analysis.

![](https://lh6.googleusercontent.com/lDQEDIIcuaBiuuD105FENyFJrK_pc9tTxkF_NYrIDjSSe46dxlwVG7si8F7EmA7EGJne-BhK4_P4ptlvNh2Lo54smJmXQR5Xo7pTZSj6vH0R86B0LlWg1LVTw46sDkeMJofynVtlm7HFKxA=s2048)

* Used embedding - find more about this.
* Used k = 13, which is a magic number. Lots of values predetermined, maybe based on experience. No reason given in paper.
