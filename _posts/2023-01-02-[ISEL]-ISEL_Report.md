---
layout: post
title: "[ISEL] ISEL Report"
subtitle: "Report of lab work."
categories: ISEL
tags: [SE]
---

### Introduction
Gonna record what I've learned; as a learner (Studies + Humanities).
ISEL, Intelligent Software Engineering Laboratory

---

### 22-2 Fall
I actually joined the lab during my 4th semester. However, didn't do much + started writing blogs during the winter vacation.

---

### 22-2 ~ 23-1 Winter Vacation
#### 02/01/2023
After a day in the lab, I went to the study room in Papyrus Hall to do my personal studies. My goal was to study till 23:00. When it was 22:48 I lost concentration and was about to go home (meaning the floor above), but remembered what JC told me.

> *KOR* : 랩실에 나오는 것을 기본 원칙으로 합니다. 혹시 조금이라도 늦거나 일찍 떠나야 한다면, 언제든지 JC에게 알려주세요!! (소통 훈련, 소통할 때 죄송하다 할 필요는 없음.)
(9시 부터 18시까지 자리를 지키는 것을 원칙으로 합니다.)
*ENG* : Showing up should be the number one ruls. If you are going to be late, or have to leave early tell JC!! (Practice communicating, don't say sorry.) (staying from 9 to 6 should be practiced.)

So I tried to focus for 10 more minutes.
It felt really weird, it's just 10 minutes but it felt like a acheived a goal I've set with myself. I was determined to keep my goals.

___

#### 05/01/2023
Heard from one of my lab mates that keeping track of what you've learned and writing blogs is really important (whether you are aiming for employment of education). Felt more drive when I heard this. Thanks.
Realized I really should keep up with studying research papers.

___

#### 16/01/2023
Had a weekly meeting, mainly discussed about how SC was doing. Also learned a lot while reviewing the *big picture* of APR and FL.
* The reason FL is needed is because the "buggy lines" are usually not the actual faulty line.

Additionally, JC taught us about AST (Abstract Syntax Tree). This is needed because it makes the process of extracting a matrix (feature) from source / byte code easier.
<img src="https://velog.velcdn.com/images/young170/post/125f7dec-17cb-4d23-855a-60114c7e6087/image.png" alt="drawing" width="600"/>
> As it is shown in the image, all requirements of the language (e.g. Java) are separated into various sections (somtimes recursion happens!). For example, if an AST is used to extract the data of local variables from the BNF, then it can get the entire data by finding the root of *<class member declaration\>* -> *<method declaration\>* or *<field declaration\>*.

Q. Are there programs that construct AST from source code?
A. Yes. They are called *Parsers*.

Realizing more and more, questioning is the best, if not the most effective, way of learning.

___

#### 25/01/2023
JC told us 3 values a professor is asked time and time again.
1. Research
2. Education
3. Volunteer
First, research is the most obvious one. As a researcher assigned to a university, a professor has the duty to constantly participating in researching.
Second, Education. Professors are priveleged to be able to be part of a university and have the chance to educate. This ties into the third topic nicely..
Third, volunteering to take up positions that are avoided by others show leadership. It is not about the person's personality, the dedication to the community is all that is needed.

___

#### 13/02/2023
It has been two weeks since my last entry.. Only 14 days till the start of 23-1..
Feeling real tired everyday, and I can see I don't have much energy as before.
The past two weeks I was mostly working on finishing my first paper and the presentation. I actually learned a lot during this time period and wish I didn't forget anything(that is why you should record stuff right away..).

1. Before going to [KCSE2023] (http://sigsoft.or.kr/kcse2023/). CJH presented the paper [UniAPR] (https://ieeexplore.ieee.org/abstract/document/9402121) in our lab team meeting. Together with JC and Sc, we tried understand each step of the framework. As we did, we got to understand the code behind and found out the process was not that complicated. It just analyzed the static Class and checked whether it was initialized or not. JC said this was a perfect example of pioneer researchers. He guessed the paper [PraPR] (https://dl.acm.org/doi/abs/10.1145/3293882.3330559) and UniAPR could have been combined. However, the researchers were the only team researching the field so separated it into two papers. He said it was also possible because the paper was well wrote. Meaning it explained clearly and in detail what each research achieved.
Later I viewed the professor that conducted the research, [Lingming Zhang] (https://lingming.cs.illinois.edu). His publications were crazy.. Several papers were ones I downloaded sometime ago to read because I was interested. I think it'll help a lot even just by reading his papers.
1. Connected to previoius point, after KCSE, my vision of going to a graduate school got clearer. The process of researching papers, presenting my work and acquiring insight from other researchers was a very unique experience. I guess it really ignited my passion. As CG said I guess I might try submitting a paper to ICSE(International Conference on Software Engineering). Plus, I can write it in English:)
1. Expanding on the topic of presenting my work, I guess I'm quite good at [presentations] (https://docs.google.com/presentation/d/1_QmDw-AnvvIlvWzSh0MgCqsyhWD4qTHr/edit?usp=share_link&ouid=117009470843218326544&rtpof=true&sd=true). JC recalled several times that I didn't seem nervous, and that the presentation was very funny. Of course I do feel nervous before going up, but when I'm up there it all goes away.
Also, reduce slides/contents as much as possible.. Learned it the hard way..haha. It's much clearer and delivers your goal way better.
1. While coming back to home(Pohang, South Korea), I rode shotgun next to JC. I told him the above 3 points and he replied by saying, "going to small conferences like KCSE doesn't help my career at all. However, I'm investing in the lab members to experience experiences like yours. It feels worthwhile when I here gratitude like you told me". Damn he gained my respect.
1. Occasionally, our lab has a day off to get time to be together. It's called *ISEL Day*. Through ISEL Day & spending time at KCSE, I got to know my lab mates better, especially CG. He told us his life story. It was verrrry dynamica and insightful. What impacted me the most was when he talked about JC's personality. He told us JC once coded till 4am at the last KCSE(2020) just to try out something he was curious about.

Most of the reflections from KCSE are recorded [here] (https://docs.google.com/presentation/d/19jE0d0Z_nHjEBTsr1dDuekrqSRgoJjcqOXG01EwPMZE/edit).

___

#### 18/02/2023
These days, I'm feeling humbled. There are several reasons for this:
* My lab mates are more focused on researching then I am.
    * I always had the thought that I was the only person passionate and willingly researching this area.
* Web applications are actually useful to learn.
    * I really hate Web & Mobile applications, but JC told me it makes the process of initializing very simple and concise.
    * Guess it's another example of my stubborness. I don't like to do tasks that are forced/required.
* I used to solve algorithm problems, such as [leetcode] (https://leetcode.com) and [baekjun] (https://www.acmicpc.net). However, lost enthusiasm when I thought I didn't need it since I was planning on to go to a graduate school, instead of getting a job.
    * But I learned it is not only the problem solving, but the grit.
    * Solved the following [problem] (https://www.acmicpc.net/problem/1000) using Rust. The reason I chose Rust will be discussed later on(hopefully..).