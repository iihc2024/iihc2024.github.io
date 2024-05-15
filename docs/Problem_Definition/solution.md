---
layout: default
title: Solution
parent: The Problem
usemathjax: true
nav_order: 2
---

<!-- TODO: Correct citations, streamline description of the problem -->

## Solution
The solution of an instance of the Integrated Healthcare Scheduling Problem (IHSP) consists of making the following decisions:

1. the admission date for patients, or, only for optional patients, the postponement to the next scheduling period; 
2. the assignment of admitted patients to operating theaters on their selected admission date;
3. the allocation of a room to admitted patients for the entirety of their length of stay (LOS) <!--length of their stay-->;
4. the assignment of a single nurse to each occupied room, for each shift within the scheduling period.

In addition, the solution is constructed taking into account the following assumptions:

- Patients cannot be moved from one room to another during their stay; so, each patient must be assigned to a single room for the entire LOS <!--length of their stay-->.
- All patients undergo surgery on the admission day.
- The surgeon for each patient is predetermined, i.e. the choice of admission day automatically determines the surgeon's duty. However, the operating theater must be chosen.
- When assigning patients to theaters, the exact time of the operation is not taken into account; only the date is taken into account, assuming that the duration of all operations does not exceed the availability of the theater.
- Is only necessary to assign nurses to a room on a given day if the room accomodates patients on that day.  Nonetheless, assigning nurses to empty rooms would be acceptable and bring no additional costs (see [Constraints](./constraints)).


