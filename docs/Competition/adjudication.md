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
instance $$j$$. Each $$X_{ij}$$ is the value of the objective function
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
 
Consider the example with $$m=6$$ instances and $$k=7$$ participants in
Table TODO.

Table TODO shows the ranks. 