---
layout: default
title: Basic Concepts
parent: The Problem
usemathjax: true
nav_order: 1
---

<!-- TODO: Correct citations, streamline description of the problem -->

## Resources
Times and physical resources:

<!--- 
  OLD VERSION LIST
* **Scheduling period:** The scheduling period is defined as a number $$D$$ of
  consecutive days; $$D$$ is always a multiple of seven, and it varies
  between 14 and 28 days.
* **Shifts:** We assume a fixed structure of working shift types for
  nurses, with three shifts per day, called _early_, _late_, and _night_.
  Therefore, there is a total of $$3D$$ shifts in the scheduling period.
* **Operating Theaters:**  All operating theaters are identical, and thus suitable for 
  accommodating all the different surgeries. Each theater has, for each day
  in the scheduling period, a maximum usage expressed in minutes. When theaters are unavailable
  on specific days, their maximum usage will be 0 minutes.
* **Rooms:**  Rooms host the patients
  during their recovery. Rooms are characterized by their capacity,
  expressed in terms of number of beds. Some rooms
  might be declared unsuitable for some specific patients.
  -->
<dl>
  <dt><b>Scheduling period</b></dt>
  <dd>The scheduling period is defined as a number $D$ of consecutive days; $D$ is always a multiple of seven, and it varies between 14 and 28 days.</dd>
  <dt><b>Shifts</b></dt>
  <dd>The structure of working shift types for
  nurses is fixed, with three shifts per day, called <i>early</i>, <i>late</i>, and <i>night</i>.
  Therefore, there is a total of $3D$ shifts in the scheduling period.</dd>
  <dt><b>Operating Theaters</b></dt>
  <dd>All operating theaters are identical, and thus suitable for 
  accommodating all the different surgeries. 
  The aggregated duration of all surgeries assigned to a theater on a given day must not exceed its capacity in minutes. When theaters are unavailable
  on specific days, their capacity will be 0 minutes.</dd>
  <dt><b>Rooms</b></dt>
  <dd>Rooms host the patients
  during their recovery. Rooms are characterized by their capacity,
  expressed in terms of number of beds. Some rooms might be declared 
  unsuitable for specific patients, and <u>no room transfers are allowed</u>.</dd>
</dl>
Next, we describe the human resources:
<dl>
<dt><b>Nurses</b></dt>
<dd>Each nurse has a skill level, which is an integer that
  goes from 0 (lowest) to $L-1$ (highest), where $L$ is the number of levels. Furthermore,
  each nurse has a predetermined roster, which is expressed as the set
  of shifts in which the nurse works. Each shift is an integer between
  0 and $3D - 1$. Finally, for each working shift, the nurse has a
  maximum workload that he/she can take in that shift.</dd>
<dt><b>Surgeons</b></dt>
<dd>Each surgeon and their team has a maximum operating time for each
  day. The time is set to 0 when the surgeon is not available. The team is assumed as an atomic
  indivisible resource (called surgeon for simplicity). All surgeons can operate in all operating theaters.</dd>
</dl>
<!--- 
  OLD VERSION LIST
* **Nurses:** Each nurse has a skill level, which is an integer that
  goes from 0 (lowest) to $$L-1$$ (highest), where $$L$$ is the number of levels. Furthermore,
  each nurse has a predetermined roster, which is expressed as the set
  of shifts in which the nurse works. Each shift is an integer between
  0 and $$3D - 1$$. Finally, for each working shift, the nurse has a
  maximum workload that he/she can take in that shift.
* **Surgeons:**  Each surgeon and their team has a maximum operating time for each
  day. The time is set to 0 when the surgeon is not available. The team is assumed as an atomic
  indivisible resource (called surgeon for simplicity). 
  -->

## Patients
The central entity of the problem is the patient:

<p style="margin-left: 30px;">
 <b>mandatory/optional</b>: mandatory patients must be admitted during the scheduling period, while the admission of optional patients can be postponed;
</p>

<p style="margin-left: 30px;">
<b>release date</b>: earliest possible admission date for the patient;
</p>

<p style="margin-left: 30px;">
<b>due date</b>: latest possible admission date, provided only for mandatory patients;
</p>

<p style="margin-left: 30px;">
<b>age group (category)</b>: a patient belongs to an age group (e.g.,~infant, youth, adult, elder); the list of age groups is fully ordered;
</p>

<p style="margin-left: 30px;">
<b>gender</b>: each patient belongs to a gender group (e.g. Gender A, Gender B);
</p>

<p style="margin-left: 30px;">
<b>length of stay</b>: duration of the hospitalization in days;
</p>

<p style="margin-left: 30px;">
  <b>incompatible rooms</b>: set of rooms that cannot be allocated to the
  patient because they do not have the specific equipment or the
  necessary isolation;
</p>

<p style="margin-left: 30px;">
<b>surgeon</b>: each patient needs a surgery with an expected duration
that will be performed by a <u>pre-assigned surgeon</u>; 
surgery day and admission day always coincide;
</p>

<p style="margin-left: 30px;">
<b>generated workload</b>: the workload profile generated by a patient is described by
a vector that starts from the early shift of the admission day and ends by the night shift on the discharge day; 
the length of the vector is 3 times his/her length of stay;
</p>

<p style="margin-left: 30px;">
<b>minimum skill level</b>: this is another vector of length 3 times the length of stay of the patient. It represents the minimum skill level of the nurse, required by the patient in each shift/day.
</p>

A patient's admission and discharge both occur after the night shift and before the early shift.
