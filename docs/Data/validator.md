---
layout: default
title: Validator
parent: Data
nav_order: 4
---
## Validator

The validator that certifies the quality of a given solution is provided as a C++ source code and should be compiled using, for example, the GNU compiler g++.
The compilation requires that file `json.hpp` is in the path. 
The validator receives as command line parameters the instance and the solution files, like in the following example.

`./IHSP_Validator.exe toy.json sol-toy.json`

The output delivered by the validator for this solution is the following.

``` 
VIOLATIONS:
RoomGenderMix.....................0
PatientRoomCompatibility..........0
SurgeonOvertime...................0
OperatingTheaterOvertime..........0
MandatoryUnscheduledPatients......0
AdmissionDay......................0
RoomCapacity......................0
NursePresence.....................0
UncoveredRoom.....................0
Total violations = 0

COSTS (weight X cost):
RoomAgeMix.............................5 (  5 X   1)
RoomSkillLevel........................21 (  1 X  21)
ContinuityOfCare......................43 (  1 X  43)
ExcessiveNurseWorkload.................0 (  1 X   0)
OpenOperatingRoom....................100 ( 50 X   2)
SurgeonTransfer........................0 (  5 X   0)
PatientDelay..........................50 ( 10 X   5)
ElectiveUnscheduledPatients............0 (300 X   0)
Total cost = 219
``` 

If `verbose`  is added as a third parameter, the details of each single cost element are also printed:
```
Room r0 is age-mixed 1/2 in day 1
Nurse n5 is underqualified for occupant a1 in room r0 in shift 3 (day1@early)
Nurse n6 is underqualified for patient p5 in room r0 in shift 4 (day1@late)
...
6 distinct nurses for occupant a0
4 distinct nurses for occupant a1
..
Operating theater t0 is open on day 1
Operating theater t0 is open on day 4
Patient p0 has been delayed for 1 days
Patient p1 has been delayed for 2 days
...
```