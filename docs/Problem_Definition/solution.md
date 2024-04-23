---
layout: default
title: Solution
parent: The Problem
usemathjax: true
nav_order: 2
---

<!-- TODO: Correct citations, streamline description of the problem -->

## Solution
The solution of an instance of IHSP consists of making the following decisions:

1. the admission date in the hospital for patients, or, only for optional patients, the postponement to the next scheduling period; 
2. the allocation of a room to admitted patients;
3. the assignment of a single nurse to each occupied room, for each shift within the scheduling period; 
4. the assignment of surgeries of patients to operating theaters, for each day of the scheduling period.

We assume that patients are always admitted and discharged after the night shift and before the early shift. 

Note that we assign a patient to a single room for their entire length of stay, and so we assume that a patient cannot be transferred from one room to another during their stay.

We also assume that all patients undergo surgery, and this happens on the admission day. In addition, the surgeon of a patient is fixed, and so the selection of the admission day automatically determines the duty of the surgeon. On the contrary, the operating theater must be selected. Such assignment, however, does not include the precise operating time, but only the date, assuming that the order of the operations in the operating theater is decided at a lower level of detail.

Finally, note that it is only necessary to assign nurses to a room on a given day if the room contains patients on that day.  Nonetheless, assigning nurses to empty rooms would be acceptable and bring no additional costs (see [Constraints](./constraints)).
