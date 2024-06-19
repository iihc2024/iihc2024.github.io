---
layout: default
title: Constraints
parent: The Problem
usemathjax: true
nav_order: 3
---

<!-- TODO: Correct citations, streamline description of the problem -->

## Constraints

The constraint set is also split into hard (starting with **H**) and soft
constraints (starting with **S**).  The former must always be
satisfied, while violations of the latter contribute to the objective function. Violations of soft constraint **S**$$_i$$
are multiplied by weight ($$W_i$$), which is not fixed but may vary across the different instances (for details see [Input Format](../Data/input)).

### Constraints on Patient Admission Scheduling

* **H1** No gender mix: Patients of different gender group may not share a room on any day.
* **H2** Compatible rooms: Patients can only be assigned to one of their compatible rooms.
* **S1** Age groups: For each day of the scheduling period and for each room, the maximum difference between age groups of patients sharing the room should be minimized. 

### Constraints on Nurse-to-Room Assignment

While the IHTP does not explicitly require the assignment of nurses to patients, the combination of patient-to-room assignments and nurse-to-room assignments determines which nurses are responsible for which patients. The following constraints (**S2**, **S3**, and **S4**) depend on the resulting nurse-patient assignment.
* **S2** Minimum skill level: 
      A nurse must have a minimum skill level to provide the required care for a patient during each shift of their stay.
      As a consequence, if the skill level of the nurse assigned to their room in a shift is inferior to the minimum level required by the patient, the penalty is equal to the difference between the two skill levels.
      Notice that a nurse with a skill level greater than the minimum one can be assigned to that room at no additional cost.     
* **S3** Continuity of care: To ensure the continuity of care, the total number of distinct nurses providing care to a patient during their entire stay should be minimized.
    Note that a nurse can work at most one shift per day, hence the number of different nurses who take care of a patient is larger than or equal to $$3$$. 
* **S4** Maximum workload: 
     The total workload induced by patients staying in rooms assigned to the nurse should not exceed the maximum workload expected of the nurse in that shift. 

### Constraints on Surgical Case Planning

* **H3** Surgeon overtime: The maximum daily surgery time of a surgeon must not be exceeded.
* **H4** Operating theater's overtime: The duration of all surgeries allocated to an operating theater on a day must not exceed its maximum usage.
* **S5** Open operating theaters: 
         The number of operating theaters opened on each day should be minimized.
* **S6** Surgeon transfer: The number of different operating theaters a surgeon is assigned to per working day should be minimized.

### Global constraints

* **H5**  Mandatory versus optional patients:  All mandatory patients must be admitted within the scheduling period, whereas optional patients may be postponed to future scheduling periods.
* **H6**  Admission day:
 A patient can be admitted on any day from the release date to the due date. Given that optional patients do not have a due date, they can be admitted on any day after their release date.

* **S7**  Admission delay: 
        The number of days between an admitted patient’s release date and their actual date of admission should be minimized. 
* **S8**   Unscheduled patients: The number of optional patients who are not admitted in the current scheduling period should be minimized. 

### Border data

We assume that some patients are already present in the hospital on the initial day of the scheduling period. We use the term _Occupants_ to refer to these special patients. While these patients contribute to the occupancy of the rooms and to all related constraints, they are already assigned to a specific room and do not require surgery during the scheduling period.

For patients whose stay ends after the end of the scheduling period, no penalties are incurred after the end of the horizon.
