---
layout: default
title: Adjudication
parent: Competition
usemathjax: true
nav_order: 3
---
<!--TODO: Add adjudication rules-->

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
case of ties. 

If a solution method produces an infeasible solution, it will be
assigned the highest rank for the corresponding instance. The rule of
average ranks for tie-breaking is not applied in 
infeasibility, i.e., solution methods giving infeasible solutions are all
assigned rank $$k$$ for the corresponding instance, in which k is the total
number of participating solution methods.
 
For each solution method we compute the mean of the ranks. <u>The finalists of the
competition will be the 5 solution methods with the lowest mean ranks</u>.

In case of a tie for the last qualifying position, all solution methods with equal mean ranks
will be included, potentially resulting in more than 5 finalists.

## Final

The evaluation process is repeated for the
finalists with the following new elements:

<ol>
<li> The hidden dataset will be used.</li>
<li> The solution methods will be run by the organizers, thus the finalist
  should give support to the organizers in the process of compiling
  and running the solution methods.</li>
<li> For each instance, the organizers will run 10 independent trials
  with random seeds. For each trial, we will compute the
  ranks and average them over all trials on all instances.</li>
</ol>
 
The winner is the one with the lowest mean rank. In case of a tie, an additional 
trial will be run for all instances until a single winner is found.

## Example

Consider the following example with $$m=6$$ instances and $$k=7$$ participants.

Suppose these are the scores of the solutions submitted: 

| Instance | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| Method 1 | 34 | 35 | 42 | 32 | 10 | 12 |
| Method 2 | 32 | 24 | 44 | 33 | 13 | 15 |
| Method 3 | 33 | 36 | 30 | 12 | 10 | 17 |
| Method 4 | 36 | 32 | 46 | 32 | 12 | 13 |
| Method 5 | 37 | 30 | 43 | 29 | 9 | 4 |
| Method 6 | 68 | 29 | 41 | 55 | 10 | 5 |
| Method 7 | 36 | 30 | 43 | 58 | 10 | 4 |

The corresponding solution ranking is therefore:

| Instance | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| Method 1 | 3 | 6 | 3 | 3.5 | 3.5 | 4 |
| Method 2 | 1 | 1 | 6 | 5 | 7 | 6 |
| Method 3 | 2 | 7 | 1 | 1 | 3.5 | 7 |
| Method 4 | 4.5 | 5 | 7 | 3.5 | 6 | 5 |
| Method 5 | 6 | 3.5 | 4.5 | 2 | 1 | 1.5 |
| Method 6 | 7 | 2 | 2 | 6 | 3.5 | 3 |
| Method 7 | 4.5 | 3.5 | 4.5 | 7 | 3.5 | 1.5 |

Meaning the mean ranks are: 

| Method 1 |3.83|
| Method 2 |4.33|
| Method 3 |3.58|
| Method 4 |5.17|
| Method 5 |3.08|
| Method 6 |3.92|
| Method 7 |4.08|

In this case, the finalists would be solution methods 5, 3, 1, 6 and 7.