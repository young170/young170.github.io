---
layout: post
title: "[Study] Programming Languages"
subtitle: "Study of Programming Languages."
categories: Study
tags: [Programming Languages]
---

### Introduction

While I was browsing on the Postech CS labrooms site, a certain topic caught my eye. Computing Systems. Feeling the enthusiasm I learned from my previous class in 22-2, Computer Architecture & Origanization (whew..), I instantly opened all three :
1. https://sslab.postech.ac.kr
2. https://hpc.postech.ac.kr/wordpress/
3. http://syslab.postech.ac.kr
The last one (#3) was a lab with 3 sup. profs. and one of them majored in Compilers. Seemed like a fun topic so I tried peeking into the topic. Searched on edX for courses and found one from Stanford (wow) , but realized some knowledge of PLT was needed.. This was also noted on my (HGU) course registeration information pdf. Fortunately, my _**supervising professor**_ (yes, because I'm very thankful) taught PLT. I emailed him right away and got access to the lecture materials + videos (also got a chance to peek around my lab's server) . My goal is to finish skimming (not enough time to master) PLT in the first half, and Compilers in the second half of my winter vacation.

---

### Purpose
This blog contains speedy notes on PLT (because my ultimate goal is to study about Compilers) .

---

### Racket Tutorial
As this is a note-style record, I will only write down stuff that I'm doomed to forget (i.e. Racket's grammer) .

First time I'm experiencing Functional Programming! Way better than playing video games:)

#### Basics
First, the building blocks of Racket, the function :
```
(define (function-name param1 …)  ; define a function
	body)
(function-name args1 … )		  ; call the function
```

How to write a test-case :
```
(test (function-name args1 …) expected_output)	; call the test function
```
Even the test-case is a function! Feels like Linux's "Everything is a file" concept.

Next, conditionals :
```
(define (function-name param1 …)  ; define a conditional function
	(cond						  ; or, and, etc.
    	[cond exp_1 body_1]
        ...
        [else body_n]))
```
A function calculates your annual interest :
```
(define (annual-interest depoist)  ; define a function
  (cond
    [(<= depoist 1000) 0.040]
    [(<= depoist 5000) 0.045]
    [(> depoist 5000) 0.050]))
```
Test-case :
```
(test (annual-interest 1000) 0.040)	; call the test function
(test (annual-interest 5000) 0.045)	; call the test function
```
Result :
```
good (annual-interest 1000) at line 9
  expected: 0.04
  given: 0.04

good (annual-interest 5000) at line 10
  expected: 0.045
  given: 0.045

```

#### Symbol
*Symbols* seemed like an important concept so I separated it with a different title.
```
"A symbol is an identifier preceded by a single forward quotation mark"
```
Not sure but from what I've heard from my lab mates (all of them took PLT except for me..) *parsing* is a huge part of PLT, and *symbols* feels somewhat similar to the concept of *parsing*. We'll see if *symbols* reappear..

#### Test-cases
I've also made test-cases as another section. This is because as the professor of the class is also the professor of SE (Software Engineering), and he highlights the importance of development processes.
In the lecture he connects the idea of test-cases with test-driven development.
Some core concepts that can be applied are :
```
a. Writing test cases before programming
b. First writing the simplest code to pass the tests
c. If your code is insufficient, *write more test and repeat the process.*
```

#### Type - Definition
```
(define-type type_id
		[variant_id1 	(field_id11 contract_expr11)
						… 
					(field_id1n contract_expr1n)]
		[variant_id2	(field_id21 contract_expr21)
					(field_id2m contract_expr2m)])
        …
```
*type_id* : Object/Group to define.
*variant_id* : A subsection of type.
*field_id* : Similar to Java's field; an atttribute of variant.
*contract_expr* : Sets a contract for the value of the field.
Example :
```
(define-type human
	[mother (name string?)
   		(age number?)
                    (job string?)]
	[father (name string?)
	            (age number?)
                     (hobby string?)
                      ...
```
**The "-" is the equivalent to the "." operator of Java.**

#### Type - Deconstruction
```
(type-case type-id expr
		[variant_id1 	(field_id11 …) expr1]
		…
		[variant_idn	(field_idn1 ...) exprn])
```
If multiple *fields* are what should be returned, then the return *expr* should be a *list* (also valid to return list with only one element).
List syntax :
```
(list 1 2 3) or '(1 2 3) or null/empty
```

#### Recursion
```
; list -> number
; to get the length of a list
; (test (my-length '(a b c)) 3)
; (test (my-length empty) 0)

(define (my-length lst)
	(cond
		[(empty? lst) 0]
		[else (+ 1 (my-length (rest lst)))] ))
```
Algorithm :
```
my-length '(a b c)    = 1 + (my-length '(b c))

my-length '(b c)       = 1 + (my-length (c))

my-length '(c)          = 1 + (my-length empty)
```
Similar to other programming languages. Recursion is solving the problem by solving it in a smaller state.

---

### Parsing and Interpreting Arithmetic
#### Arithmetic Expression (AE)
An example syntax of an arithmetic expression.
```
(define-type AE
  [num (n number?)]
  [add (lhs AE?) (rhs AE?)]
  [sub (lhs AE?) (rhs AE?)])
```
* Knowing the reason *AE* is used instead of *num* is very important
* It may seem like the same thing, but if AE is used it enables sub-expressions to be used (which is frequently used in arithmetic expressions).

#### Parser
>Parser : converts concrete syntax into abstract syntax

An example of parsing of the *ae* above.
```
(define (parse sexp)
	(cond
        [(number? sexp) (num sexp)]
        [(eq? (first sexp) '+) (add (parse (second sexp))
                                    (parse (third sexp)))]
        [(eq? (first sexp) '-) (sub (parse (second sexp))
                                    (parse (third sexp)))]
    ))
```
The tests :
```
(test (parse '3) (num 3))
(test (parse '{+ 3 4}) (add (num 3) (num 4)))

(parse '{+ {- 3 4} {+ 2 3}})
```
* Notice just like the definition, parsing converts concrete syntax ('{+ 3 4}) to abstract syntax ((add (num 3) (num 4))).
* The last statement "parse" will produce an abstract syntax of it.
    * (add (sub (num 3) (num 4)) (add (num 2) (num 3)))

**However**, what if the following statement was executed?
```
(parse '{+ 1 2 3})

```
It wouldn't produce the correct result or a result at all (syntax error)!

To solve it new parameters are needed.
For this example the # of operators per operands are what caused the problem so the # should be considered.
```
(define (parse sexp)
	(cond
        [(number? sexp) (num sexp)]
        [(and (= 3 (length sexp))
        		[(eq? (first sexp) '+) 
        (add (parse (second sexp)) 
                (parse (third sexp)))]
        [(and (= 3 (length sexp))
        		[(eq? (first sexp) '-)
        (sub (parse (second sexp))
        		(parse (third sexp)))]
        [else (error 'parse "bad syntax: ~a" sezp)]
    ))
```
#### Interpreter
Basic syntax :
```
(type-case type-id expr
		[variant_id1 (field_id11 ...) expr1]
        ...
        [variant_idn (field_idn1 ...) exprn]
```
Example (AE -> number):
```
(define (interp an-ae)
		[num (n) n]
        [add (lhs rhs) (+ (interp lhs) (interp rhs))]
        [sub (lhs rhs) (- (interp lhs) (interp rhs))]
        ))
```
* If num is read just return the number
* *add* is recognized as an actual addition of 2 AEs
* *sub* is recognized as an actual subtraction of 2 AEs
* The arithmetic operations should be done in the languages actual operation syntax (e.g.Racket)

### Substitution
####  Parser of WAE
If there is a complicated expression like that following :
```
{+ {+ 5 5} {+ 5 5}}
```
* We would like to use an identifier for the repeated expressions, *{+ 5 5}*
* We would like to use '*with*' keyword to define an identifier for an arithmetic expression and use the identifier for another arithmetic expression.
```
{with {x {+ 5 5}} {+ x x}}
```

#### Identifiers
* Bound Identifier
    * Identifiers to be replaced with values.
* Binding Identifier
    * Identifiers that replace the *Bound Identifier*.
* Free Identifier
    * Causes an error when a *variable* is used without definition.

Implementing a parser for the above example in **parser**.
The code below is identical to the previous example, but using *match*.
It checks for "matching" identifiers.
*Match* is unique to Racket enabling to find patterns of the input parameters :
* First defining the type :
```
(define-type WAE
  [num 	(n number?)]
  [add 	(lhs WAE?) (rhs WAE?)]
  [sub 	(lhs WAE?) (rhs WAE?)]
  
  [with (name symbol?) (name-exp WAE?) (body WAE?)]
  [id 	(name symbol?)]
  )
```
* Then, the implementation of the parser :
```
; parse: sexp -> WAE
(define (parse sexp)
	(match sexp
    	[(? number?) 		(num sexp)]
        [(list '+ lhs rhs) 	(add (parse lhs) (parse rhs))]
        [list '- lhs rhs) 	(sub (parse lhs) (parse rhs))]
                
        [(list 'with 		(list i v) e) (with i (parse v) (parse e))]
        [(? symbol?) 		(id sexp)]
                
        [else 				(error 'parse "bad syntax: ~a" sezp)]
    ))
    
(parse '{with {x {+ 5 5}} {+ x x}})
```
This will result :
```
(with 'x (add (num 5) (num 5)) (add (id 'x) (id 'x)))
```
To explain :
1. *[(list 'with (list i v) e) (with i (parse v) (parse e))]* will be executer.
2. *{x {+ 5 5}}* is the *(list i v)* part. Meaning it will parse to *'x (add (num 5) (num 5))*.
3. *{+ x x}* is the *e* part. Meaning it will parse to *(add (id 'x) (id 'x))*.

####  Interpreter of WAE
The process of interpreting a WAE relies heavily on **Substitution**.
The 3 parameters of Substitution :
```
(expression, binding_identifier, value)
```
```
; [contract] subst: WAE symbol number -> WAE
(define (subst wae idtf val)
	(type-case WAE wae
		[num (n) wae]
        ; no subst occurs
		[add (l r) (add (subst l idtf val) (subst r idtf val))]
        ; recursive call for subst, and add
		[sub (l r) (sub (subst l idtf val) (subst r idtf val))]
        ; recursive call for subst, and sub
		[with (i v e) (with i (subst v idtf val) (if (symbol=? i idtf) e (subst e idtf val)))]
        ; solves layered identifiers, by recurring
		[id (s) (if (symbol=? s idtf) (num val) wae)]
        ; where the actual subst happens, symbol is subst for num
        ; if the first branch (symbol=?) returns false, wae is executed. else num is subst
        ; so no subst happens when free idtf
     ))
```
* The actual implementaion, should throw an error when the last *[if]* occurs.

### Functions
#### Function BNF
```
<FunDef> ::= {deffun {<id> <id>} <F1WAE>}
<F1WAE> ::= <num>
			| {+ <F1WAE> <F1WAE>}
			| {- <F1WAE> <F1WAE>}
			| {with {<id> <F1WAE>} <F1WAE>}
			| <id>
			| {<id> <F1WAE>}
```
* The first line is for the function definition.
* The final line is for the function call.
* Similar to function pointers in C++, in functional programming, functions are also values.
    * So function definitions themselves can be returned.
* Function body should be an arithmetic expression.
    * That is why *F1WAE* is included.
#### F1WAE: Abstract Syntax
```
(define-type FunDef
	[fundef (fun-name symbol?)
    		(arg-name symbol?)
            (body F1WAE?)
    ])
```
```
; [contract] subst: F1WAE symbol number -> F1WAE
(define (subst f1wae idtf val)
	(type-case F1WAE f1wae
		[num	(n number?)]
		[add	(lhs F1WAE?) (rhs F1WAE?)]
		[sub	(lhs F1WAE?) (rhs F1WAE?)]
		[with	(name symbol?) (named-expr F1WAE?) (body F1WAE?)]
		[id		(name symbol?)]
        [app	(fun-name symbol?) (arg F1WAE?)]
     ))
```
* Notice a new line is appended.

Usage:
```
(fundef 'identify 'x (id 'x))
(app 'identify (num 8))
```
#### F1WAE Parser
Based on the grammer above, which defined the data-type & syntax.
Two parsers are needed,
```
; parse-fd: sexp -> FunDef
```
* Converts function definition
```
; parse: sexp -> F1WAE
```
* Converts function call
___
Example:
* Our goal is to parse the following:
```
{-20 (twice 10}}
```
The result would be:
```
(sub (num 20) (app 'twice(num 10)))
```
___
Implementation(function call):
```
; parse: sexp -> F1WAE
(define (parse sexp)
	(match sexp
    	[(? number?) 		(num sexp)]
        [(list '+ lhs rhs) 	(add (parse lhs) (parse rhs))]
        [list '- lhs rhs) 	(sub (parse lhs) (parse rhs))]
                
        [(list 'with 		(list i v) e) (with i (parse v) (parse e))]
        [(? symbol?) 		(id sexp)]
        [(list fn a)		(app fn (parse a))]
        [else 				(error 'parse "bad syntax: ~a" sezp)]
    ))
```
* *a* maybe an arithmetic expression

Implementation(function definition):
```
; parse-fd: sexp -> FunDef
(define (parse-fd sexp)
	(match sexp
    	[list 'deffun (list f x) b)	(fundef f x (parse b))]
    ))
```
If the list matches the pattern, 'deffun (list f x) b) -> fundef f x (parse b)).
* The body *b* is an arithmetic expression(F1WAE) so it needs parsing.

#### F1WAE Interpreter
```
; interp: F1WAE list-of-FuncDef -> number
(define (interp f1wae fundefs)
	(type-case F1WAE f1wae
    	[num	(n)		n]
        [add	(l r)	(+ (interp l fundefs) (interp r fundefs))]
        [sub	(l r)	(- (interp l fundefs) (interp r fundefs))]
        [with	(x i b)	(interp (subst b x (interp i fundefs)) fundefs)]
        [id		(s)		(error 'interp "free identifier")]
        [app	(fn a)
        				(local
                        	[(define a_fundef (lookup-fundef f fundefs))]
                            (interp (subst (fundef-body a_fundef)
                            			   (fundef-arg-name a_fundef)
                                           (interp a fundefs))
                                    fundefs
                            ))]
    ))
```
Update subset function
```
; [contract] subst: F1WAE symbol number -> F1WAE
(define (subst f1wae idtf val)
	(type-case F1WAE f1wae
		[num	(n)		f1wae]
		[add	(l r)	(add (subst l idtf val) (subst r idtf val))]
		[sub	(l r)	(sub (subst l idtf val) (subst r idtf val))]
		[with	(i v e)	(with i (subst v idtf val) (if (symbol=? i idtf) e
        					(subst e idtf val)))]
		[id		(s)		(if (symbol=? s idtf) (num val) f1wae)]
        [app	(fn a)	(app f (subst a idtf val))]
        ; idtf and val are given as parameters
     ))
```
