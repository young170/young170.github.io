---
layout: post
title: "[DS TA] DS TA Report"
subtitle: "Report of DS TA work."
categories: DS TA
tags: [DS, Linux]
---

### Introduction
This is my notes on the order + details of lectures as a TA.

---

### Order
#### 1. Installation Process
#### 2. Debugging
I realized debugging should be the first to be taught (installation doesn't count) because it is crucial in the later parts of the class and getting a habit of it is important to survive. This is a [link] (https://www.youtube.com/watch?v=9H6muyZjms0&list=PLUl4u3cNGP63WbdFxL8giv4yhgdMGaZNA&index=23) to a lecture by Harvard on debugging. It is an introductory course, but debugging is being taught. It was very shocking to me when I saw debugging being taught in an intro. class especially in one the world's finest universities (even unit testing!) . But the more I think of it, it should be. It is one of the most (personally) underrated and undertaught subject because it is assumed students already know innately. The following is the process of debugging as introduced in the video lecture.
```
The Process :
	a. Being systematic is the most important part. Whatever tachnique you use.
    b. When using the print method to debug, place the print statements in logical locations in the program.
    	(e.g. When returning from a function, receiving an input, accessing a variable, etc.)
```

#### 3. Preprocess
```
gcc -E <filename>
```
To create a preprocessed output file.

---

### Introduction
Similarly to my [Lab Journal] (https://velog.io/@young170/Lab-Journal), gonna record what I've learned; as a learner (Studies + Humanities).
As this is a class I've already took, I guess it will be mostly about my thoughts during TA activities.

### 22-2 ~ 23-1 Winter Vacation
#### Preperation
Started off my Data Structures TA career on the 2nd semester of 2022 (Started my TA career on 2021 winter, C Programming). After having a cold start, got the hang of it during the final weeks of the semester.
Prof. said he wanted to fix most of the lectures to lower the difficulty a tad. The reason was students after the covid pandemic tended to have less grit and gave up easily.
Our main fixes were :
* Translate lab materials, ENG -> KOR.
* Translate lab materials, .md -> .docx
* Split Problem Sets into easier pieces.
* Create new Problem Sets with less advanced operations.
    * Create several Problem Sets for each topics to create a rotation that cycles every semester (maybe 2 ~3 ).
* Create new bonus Problem Sets.
* Create a new schedule for both Spring & Fall semesters.

#### Class Schedule
I really.. really.. really... really...... wanted to take a class in POSTECH.. and applied for Algorithms. The class was from 9:30 ~ 10:45 (Mon, Wed) so it was possible to attend the Thur DS class. However, it was impossible to attend the Mon class.... I had to give it up..... It was hard.. That's the only way to describe it. Slightly feeling better from writing this.
One of my goals was to let down some of my greed for studying. It took over things in my life that were more essential. After letting it go, I realized if it wasn't for this DS class I wouldn't have even thought of going to POSTECH. I owed so much. Also, another thing to take away is that I am more determined to take a class at POSTECH. Before, I was kinda scared if I would be able to ~~survive~~ pass.

#### Lab Translation
Originally, the lab materials (and some Problem Sets) were written in English. Some Korean students had a hard time catching up because they weren't fluent. The first job I did was to convert the materials into Korean. I couldn't just simply use Google Translate other tools because they ~~suck~~ are wrong most of the time.
One of the most difficult jobs was to decide whether to leave the word in English or go out of one's way to translate it. For example, *map* or even *pointer*.
Later, prof. taught me how to apply [styles] (https://support.microsoft.com/en-us/office/customize-or-create-new-styles-d38d6e47-f6fc-48eb-a607-1eb120dec563) to .docx files which helps keep constant format.

#### Bonus Psets
My notes about Chat-GPT:
```
It generates new implementations of non-existent concepts

Its good at understanding quite implicit English: “I don't see the difference between the current code and a normal binary tree”

It automatically removes unnecessary information. Using the options I gave differently from the previous chat.
Ex)

Question:
> “good job. however this still doesn't feel like a mangrove tree in real life. 
> I will give you an idea (you can add more if you want):
> how about using the concept of salt tolerance.
> Add a state of the water leve, and
> as the tree needs water to survive, it should "follow" the water.”

- Previously there was a variable for location.
- However, chatgpt removes it after the question above.
- I asked the reason and it said,
> “As an AI language model, I don't have personal opinions or motivations, and
> I can only provide code based on the information and specifications given to me by the user.
> In this case, the omission of the location variable was an oversight on my part and
> I apologize for any confusion it may have caused.”
    - Maybe its programmed to deal with accusive words?

Asked for other ideas to implement:
1. Mangrove Trees: As we have already discussed, mangrove trees are salt-tolerant trees that grow in tidal wetlands and can help to prevent erosion and protect coastlines from storms and flooding.
2. Banyan Trees: A type of fig tree that is native to India and is known for its distinctive aerial roots that grow into the ground and provide additional support for the tree.
3. Redwoods: The tallest trees in the world, growing up to 379 feet tall. They are native to the west coast of North America and are known for their resistance to fire, insects, and disease.
4. Baobab Trees: A type of tree that is native to Africa and Madagascar and is known for its large trunk and branches that resemble roots. Some species of baobab trees are believed to be over 2,000 years old.
5. Douglas Firs: A type of coniferous tree that is native to western North America and is one of the tallest trees in the world. It is commonly used for lumber and paper production.

Amazing..

When I asked if I could get some basic code snippets
It said something shocking..
1. Mangrove Trees: As we have already discussed, a basic implementation of mangrove trees could include a class to represent the tree and its properties, such as its salt tolerance and water level. You could also implement a method for the tree to move based on the water level.
- It actually took the idea I gave him and learned(?)

I love the code for the Redwood
void respondToFire() {
      // implement logic for responding to a fire
    }

    void respondToInsects() {
      // implement logic for responding to an insect attack
    }
- Because Redwood are known to be fire, insect resistant.
```

#### Grading
##### Auto-grader
Gotta ask Chat-GPT to make me a auto-grader before he becomes premium.
##### Cheating
Really concerned of how I will be able to discern who cheated. Applications like Chat-GPT are everywhere.