# Project 1 Assignment

Your first project will require you to answer each of the 10 questions below.  You will be expected to open a pull request with your initial answers by the second class meeting, giving you one week to work on these problems. You and your peers will then have one week to work together to refine your respective initial answers, so they are ready for final submission. Once your pull requests have been reviewed and merged to the development branch, I will review them, then merge to the master branch. 

Tip #1: Carefully study the Hedman selections assigned, as several of the questions are taken directly from the textbook. 
Tip #2: Google is your friend. An important skill to pick up in this class is recognizing when to think hard and when to think smart. You might find answers to some of the questions below simply by googling; you might find pieces of answers to parts of some question below, which will need to be combined; then again, you might not find any help at all because the questions are more novel than they initially appear. I encourage you to use existing resources as guidance, but be careful. My reputation for asking students tricky questions is well-earned. 
Tip #3: Work _together_ to solve these problems, even for initial submissions and when you do, document this in github. For example, you might feel like you nearly have answers to question 1, but would love another pair of eyes. You can then open a post in your local github account, and tag folks from class requesting they check out your work. 
Tip #4: The work we do is challenging; that should be assumed. You are smart enough to be here; that should also be assumed. We have neither time nor space for shaming, but all of time and space for praising. Be cognizant of how your messages might be received, and err on the side of caution. It is hard to surmise intent from text alone. For my part, I treat text only communications the way modern musicals are written: Little subtext; emotions on the sleeve. 
```

Note: The standard interpretation of the logical symbols - "∨", "∧", "→", "¬", "∀", "∃" - is assumed throughout. 

1. Provide the truth tables for each of the following propositional logic formulas. State whether each is a tautology, a contradiction, or contingent:
  ```
  (a) (¬A→B)∨((A∧¬C)→B) 
  

  A | B | C | (a)
|---|---|---|---|
  T | T | F | T
  T | T | F | T
  T | F | T | T
  F | T | T | T
  T | F | F | T
  F | T | F | T
  F | F | T | T
  F | F | F | T
  
  Tautology

  (b) (A→B)∧(A→¬B) 

  A | B| (b)
|---|---|---|
  T | T | F
  T | F | F
  F | T | T
  F | F | T

  Contingent

  (c) (A→(B∨C))∨(C→¬A) 

  A | B | C | (c)
|---|---|---|---|
  T | T | F | T 
  T | T | F | T 
  T | F | T | T
  F | T | T | T 
  T | F | F | T 
  F | T | F | T 
  F | F | T | T 
  F | F | F | T

  Tautology

  (d) ((A→B)∧C)∨(A∧D) 

  A | B | C | D | (d)
|---|---|---|---|---|
  T | T | T | T | T
  T | T | T | F | T
  T | T | F | T | T
  T | T | F | F | F
  T | F | T | T | T
  T | F | T | F | F
  T | F | F | T | T
  T | F | F | F | F
  F | T | T | T | T
  F | T | T | F | T
  F | T | F | T | F
  F | T | F | F | F
  F | F | T | T | T
  F | F | T | F | T
  F | F | F | T | F
  F | F | F | F | F

  Contingent
  ```
	
2. A _literal_ is an atomic formula or the negation of an atomic formula. We say a formula is in _conjunctive normal form_ (CNF) if it is the conjunction of the disjunction of literals. Find propositional logic formulas in CNF equivalent to each of the following:
  ```
  (a) (A→B)→C
  (¬A∨B)→C
  ¬(¬A∨B)∨C
  (A∧¬B)∨C
  (A∨C)∧(¬B∨C)  
  
  (b) (A→(B∨C))∨(C→¬A)
  It is a tautology. A∨¬A
  
The related truth table shows this formula is a tautology. The calculator gives me the same result. Giacomo and Karl wrote it is a tautology. However, I was not able to transform it into a CNF using Morgan's rules. Should I check at first the truth table and if it is a tautology then directly state that?

  (c) (¬A∧¬B∧C)∨(¬A∧¬C)∨(B∧C)∨A 
 It is a tautology. A∨¬A
  
The related truth table shows this formula is a tautology. The calculator gives me the same result. Giacomo and Karl wrote it is a tautology. However, I was not able to transform it into a CNF using Morgan's rules. Should I check at first the truth table and if it is a tautology then directly state that? Isn't a parenthesis missed in the first part (¬A∧¬B∧C)? Is it a formula then?

  ```
  I solved this question, using the Morgan's rules and checking Giacomo and Karl's answers.
  I also used this logic calculator: https://www.erpelstolz.at/gateway/formular-uk-zentral.html

3. Let V be the vocabulary of first-order logic consisting of a binary relation P and a unary relation F. Interpret P(x,y) as “x is a parent of y” and F(x) as “x is female.” Where possible define the following formulas in this vocabulary; where not possible, explain why: 
  
  ```
  (a)  B(x,y) that says that x is a brother of y  
  (b)  A(x,y) that says that x is an aunt of y  
  (c)  C(x,y) that says that x and y are cousins   
  (d)  O(x) that says that x is an only child  
  (e)  T(x) that says that x has exactly two brothers 
  ```
(a) B(x,y) that says that x is a brother of y
B(x,y) := ¬F(x)∧∃z(P(z,x)∧P(z,y)∧¬(x=y)∧¬(x=z))

Explanation: x is a brother of y if x is not female (¬F(x)) and there exists some z such that z is a parent of both x and y (P(z,x)∧P(z,y)), and x is not the same person as y (¬(x=y)), and x is not z (¬(x=z)). 

(b) A(x,y) that says that x is an aunt of y
A(x,y) := F(x)∧∃z(P(z,y)∧∃w(P(w,z)∧P(w,x))∧¬(x=w)))

Explanation: x is an aunt of y if x is female (F(x)) and there exists some z such that z is a parent of y (P(z,y)) and there exists some w such that w is a parent of both z and x (P(w,z)∧P(w,x)).

(c) C(x,y) that says that x and y are cousins
C(x,y) := ∃z∃w((¬(z=w)∧P(z,x))∧(P(w,y))∧∃u((P(u,z)∧P(u,w))∧¬(x=u)))

Explanation: x and y are cousins if there exist z and w such that z is not the same person as w (¬(z=w)), z is a parent of x (P(z,x)), w is a parent of y (P(w,y)), and there exists some u such that u is a parent of both z and w (P(u,z)∧P(u,w)).

(d) O(x) that says that x is an only child
O(x) := ∀y(P(y,x)→∀z(P(y,z)→(z=x)))

Explanation: x is an only child if for all y such that y is a parent of x (P(y,x)), for all z, if y is a parent of z then z must be x (P(y,z)→(z=x)).

(e) T(x) that says that x has exactly two brothers
T(x) := ∃y∃z(B(y,x)∧B(z,x))∧∀w(B(w,x)→((w=y)v(w=z)∧¬(x=y)∧¬(x=z)∧¬(z=y))))

Explanation: x has exactly two brothers if there exist y and z such that y is not the same person as z (¬(y=z)), both y and z are brothers of x (B(y,x)∧B(z,x)), and for all w, if w is a brother of x then w must be either y or z (B(w,x)→((w=y)∨(w=z))).

I worked on this question together with the other participants of the "Ontology Sprint" Workshop. We asked to answer this question to ChatGTP. Then, we work together on the generated solution.
```

4. Let V be a vocabulary of the attribute (concept) language with complements (ALC) consisting of a role name "parent_of" and a concept name "Male". Interpret parent_of as "x is a parent of y" and M as "x is male". Where possible define the following formulas in this vocabulary; where not possible, explain why: 
  ```
  (a)  B that says that x is a brother of y
It is not possible to define this formula in V because it is not possible to denote the relations between individuals using V which is essential in expressing that x is not identical to y.
 
  (b)  A that says that x is an aunt of y
This formula implies that there is a parent of x which is z, z has a common parent with y, and y is not male. However, it is not possible to say that z is not identical to y in V. Therefore, it is not possible to define this formula in V.

  (c)  C that says that x and y are cousins
This formula implies that there is a parent of x which is z, there also is a parent of y which is W, and z and w have a common parent. However, it is not possible to express that z and w are not identical. Therefore, it is not possible to define this formula in V.

  (d)  O that says that x is an only child
This formula implies that x has a common parent with y and x and y are identical. However, it is not possible to express that x and y are identical in V. Therefore, it is not possible to define this formula in V.
  
  (e)  T that says that x has exactly two brothers
This formula implies that x is male or not male, there exist male y and male z who share a parent with x, and x, y, and z are non-identical. Since we can't express the (non)identical relation among individuals in V, we can't define the formula in V.
  ```


5. Select two formulas defined in ALC from question 4 to form the basis of a T-Box. Supplement this T-box with whatever other axioms you like, as well as an A-box, so that you ultimately construct a knowledge base K = (T,A). Provide a _model_ of K. This may be graphical or symbolic or both. 

6. Explain the difference - using natural language - between the first-order prefixes:
  ```
  (a) ∃x∀y and ∀x∃y
  (b) ∃x∀y∃z and ∀x∃y∀z 
  (c) ∀x∃y∀z∃w and ∃x∀y∃z∀w
```
	
7. Show that the following sentences are not equivalent by exhibiting a graph that models one but not both of these sentences:
```
∀x∃y∀z(R(x,y) ∧ R(x,z) ∧ R(y,z))
∃x∀y∃z(R(x,y) ∧ R(x,z) ∧ R(y,z))
```
	
8. Using an online tableau proof generator - such as the one found here `https://www.umsu.de/trees/` - provide tree proofs of the following entailments, which are known as the De Morgan's laws:
  ```
  (a) ∀x∀y(¬(Px ∧ Qx) → (¬Px ∨ ¬Qx))
![proof](https://github.com/JisooSeo/PHI-696/assets/143667668/d4614acb-864c-4996-a3b0-73cdf5d857cd)

  (b) ∀x∀y(¬(Px ∨ Qx) → (¬Px ∧ ¬Qx))
  (c) ∀x∀y((¬Px ∨ ¬Qx) → ¬(Px ∧ Qx))
  (d) ∀x∀y((¬Px ∧ ¬Qx) → ¬(Px ∨ Qx))
```
	
9. Using a natural deduction proof generator - such as the one found here `https://proofs.openlogicproject.org/` - provide natural deduction proofs for each of De Morgan's laws. 

10. Compare and contrast the proofs provided for (a) in your answers to questions 8 and 9. Explain the different assumptions, strategies, etc. exhibited in tree proofs vs natural deduction proofs. 
 
