---
layout: default
title: Rules
parent: Competition setting
nav_order: 1
---

<!-- TODO: added clarification on rule 3 -->

This competition seeks to encourage research into automated timetabling and scheduling methods for solving an integrated healthcare problem,
and to offer prizes to the most successful methods.  With any set of
rules for any competition it is possible to work within the letter of
these rules but outside their spirit.
Therefore, the spirit of the following rules is important.


**Rule 1**: <u>The organisers reserve the right to update the
  rules at any time</u>, if they believe it is necessary for the sake of
  preserving the correct operation of the competition. Any change of
  rules will be notified in the repository.

**Rule 2**: The competition has deadlines when all
  submissions must be uploaded. These deadlines are strict and no
  extensions will be given under any circumstances.

**Rule 3**: Participants may use any programming
  language. The use of third-party software is allowed under the
  following restrictions:
   * it is [open source](https://opensource.org/osd) software;
   * its behavior is (reasonably) documented;
   * it runs under a commonly-used operating system (Unix/Linux, Windows, or MAC OS).

**Rule 4**: The solution method should take as input the
  files in the format described, and produce as output a solution file in the same format. 
  Timeout occurs after _10 minutes_ of CPU time using at most _4 cores_.

**Rule 5**: The solution method can be either deterministic or
  stochastic. In both cases, participants must be prepared to show
  that the results are repeatable in the given computational time. In
  particular, the participants who use a stochastic algorithm should
  code their program in such a way that the exact run that produced
  each submitted solution can be replicated (by recording the random
  seed). 

**Rule 6**: Along with the solution for each instance,
  the participants should also submit a concise and clear description
  of their algorithm.

**Rule 7**: A set of 5 finalists will be chosen after the
  competition deadline. The ordering of participants will be based on the
  scores on the provided instances. The actual list will be based
  on the ranks of solution methods on each single instance. The mean average of
  the ranks will produce the final place list. Section
  [Adjudication](adjudication) provides more details on how the
  orderings will be established.

**Rule 8**: The finalists' solution methods will be rerun by the organizers on the hidden dataset using 
the same timeout specified in **Rule 4**. The official PC will be a _AMD Ryzen Threadripper PRO 3975WX, 3.50 GHz,
running Ubuntu Linux 22.4_. A different operating environment might be used in exceptional cases if 
strictly necessary.  It is the responsibility of the participant to ensure that all files and 
information are provided to enable the organizers to run their code.
  
**Rule 9**: Finalists' eventual place listings will be
  based on the ranks on each single instance for a set of trials on
  all instances. As with **Rule 7**, Section [Adjudication](adjudication) provides an explanation 
  of the procedures to be used.