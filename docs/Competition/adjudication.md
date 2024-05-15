---
layout: default
title: Adjudication rules
parent: Competition setting
usemathjax: true
nav_order: 3
---
<!--TODO: Add adjudication rules-->

We follow the same adjudication procedure of the First and Second International Nurse Rostering Competitions (INRC-I, INRC-II)
<!--add citation -->
which in turn has been imported from the Second International
Timetabling Competition (ITC-2007)<!--add citation -->. It is repeated here
for the sake of self-containedness.

Let $$m$$ be the total number of instances and $$k$$ the number of
participants that produce a solution for all $$m$$ instances. Let
$$X_{ij}$$ be the result supplied (and verified) by participant $$i$$ for
instance $$j$$. 

Each $$X_{ij}$$ is the value of the objective function
$$s$$, for participant $$i$$ on instance $$j$$. In case participant $$i$$ is
unable to provide a feasible solution for instance $$j$$, $$X_{ij}$$ is
assigned a conventional value $$M$$ larger than all the results supplied
by the other participants for that instance.
 
The matrix $$X$$ of results is transformed into a matrix of ranks $$R$$
assigning to each $$R_{ij}$$ a value from $$1$$ to $$k$$. That is, for
instance $$j$$ the supplied $$X_{1j}$$, $$X_{2j}$$, $$\ldots$$ ,$$X_{kj}$$ are
compared with each other and rank $$1$$ is assigned to the smallest
observed value, rank $$2$$ to the second smallest, and so on to 
rank $$k$$, which is assigned to the largest value for instance $$j$$.
Ranks are assigned for all the instances. We use average ranks in
case of ties.  If a solution method produces an infeasible solution, it will be
assigned the highest rank for the corresponding instance. The rule of
average ranks for tie-breaking is not applied in 
infeasibility, i.e., solution methods giving infeasible solutions are all
assigned rank $$k$$ for the corresponding instance, in which k is the total
number of participating solution methods.
 
Consider the following example with $$m=6$$ instances and $$k=7$$ participants.

Assumen these are the scores of the submitted solutions: 

| Instance | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| Method 1 | 34 | 35 | 42 | 32 | 10 | 12 |
| Method 2 | 32 | 24 | 44 | 33 | 13 | 15 |
| Method 3 | 33 | 36 | 30 | 12 | 10 | 17 |
| Method 4 | 36 | 32 | 46 | 32 | 12 | 13 |
| Method 5 | 37 | 30 | 43 | 29 | 9 | 4 |
| Method 6 | 68 | 29 | 41 | 55 | 10 | 5 |
| Method 7 | 36 | 30 | 43 | 58 | 10 | 4 |

The corresponding solutions ranking is this:

| Instance | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| Method 1 | 3 | 6 | 3 | 3.5 | 3.5 | 4 |
| Method 2 | 1 | 1 | 6 | 5 | 7 | 6 |
| Method 3 | 2 | 7 | 1 | 1 | 3.5 | 7 |
| Method 4 | 4.5 | 5 | 7 | 3.5 | 6 | 5 |
| Method 5 | 6 | 3.5 | 4.5 | 2 | 1 | 1.5 |
| Method 6 | 7 | 2 | 2 | 6 | 3.5 | 3 |
| Method 7 | 4.5 | 3.5 | 4.5 | 7 | 3.5 | 1.5 |

For each solution method we compute the mean of the ranks. The finalists of the
competition will be the 5 solution methods with the lowest mean ranks. In case of
a tie for the last qualifying position, all solution methods with equal mean ranks
will be included, potentially resulting in more than 5 finalists.

The following Table shows the mean ranks of the example: 

| Method 1 |3.83|
| Method 2 |4.33|
| Method 3 |3.58|
| Method 4 |5.17|
| Method 5 |3.08|
| Method 6 |3.92|
| Method 7 |4.08|