---
layout: default
title: Input format
parent: Data
usemathjax: true
nav_order: 1
---
<!--TODO: Expand explanation of .json input, use toy instance, add link to allow download of entire toy instance-->

The input file contains a header part in addition to separate sections for occupants, patients, nurses, surgeons, operating theaters and rooms.

## Header
The header contains the length of the the basic data as well as the cost components instance-specific weights.
<!--Below is an example of the header part, containing the general data and the weights of the cost components.-->

The header section specifies some general information such the total number of ```days``` in the scheduling period, the number of different nurses ```skill levels```, the list of types of daily shifts ```shift_types```, the enumeration of different ```age groups``` considered in the scheduling as well as the instance-specific weight associated to each of the cost components.

```js
{
  "days": 7,
  "skill_levels": 3,
  "shift_types": [
    "early",
    "late",
    "night"
  ],
  "age_groups": [
    "infant",
    "adult",
    "elderly"
  ],
  "weights": {
    "room_mixed_age": 5,
    "room_nurse_skill": 1,
    "continuity_of_care": 1,
    "nurse_eccessive_workload": 1,
    "open_operating_theater": 50,
    "surgeon_transfer": 5,
    "patient_delay": 10,
    "unscheduled_optional": 300
  }
  // ...
}
```

## Occupants

This section presents the list of occupants, each characterized by a unique ```id```along with their ```gender``` group and ```age_group``` as well as the duration of their stay ```length_of_stay```.
Two arrays indicate the ```workload_produced```, and the ```skill_level_required``` for each shift of their stay (totaling $$3 LOS$$).
Additionally, each occupant is linked to a ```room_id```, specifying their assigned room.

```js
 "occupants": [
    {
      "id": "a0",
      "gender": "A",
      "age_group": "elderly",
      "length_of_stay": 2,
      "workload_produced": [2, 1, 1, 2, 3, 2],
      "skill_level_required": [1, 2, 0, 0, 0, 0],
      "room_id": "r21"
    },
    //other occupants
    ]
```
## Patients

As observed in the previous section for occupants, each patient is identified by an ```id```, assigned a ```gender``` group, an ```age_group```, and their ```length_of_stay``` in the hospital. Information regarding the ```workload_produced```, and the ```skill_level_required``` for each shift of their stay is also provided.

However, the patient section includes additional details pertaining to scheduled surgeries.
The ``` "mandatory" ``` field denotes whether a patient is required to be scheduled must be scheduled within the given period, while ```surgery_release_day``` indicates the earliest day for surgery (and hospital admission).
For mandatory patients, the field ```surgery_due_day``` signifies the latest possible surgery date, while optional patients do not have this attribute. Further surgery details include the ```surgery_duration``` (in minutes) and the pre-assigned surgeon surgeon (```surgeon_id```).

Additionally, each patient is accompanied by a list of ```incompatible_room_ids``` which specifies all the rooms the patient cannot be assigned to.

```js
 "patients": [   
    {
      "id": "p0",
      "mandatory": false,
      "gender": "B",
      "age_group": "elderly",
      "length_of_stay": 3,
      "surgery_release_day": 3,
      "surgery_duration": 120,
      "surgeon_id": "s0",
      "incompatible_room_ids": [
        "r1"
      ],
      "workload_produced": [3, 3, 1, 1, 3, 1, 3, 2, 2],
      "skill_level_required": [2, 2, 1, 1, 2, 1, 0, 0, 0 ]
    },
    //other patients
    {
      "id": "p5",
      "mandatory": true,
      "gender": "A",
      "age_group": "adult",
      "length_of_stay": 2,
      "surgery_release_day": 1,
      "surgery_due_day": 1,
      "surgery_duration": 30,
      "surgeon_id": "s0",
      "incompatible_room_ids": [],
      "workload_produced": [3, 2, 1, 1, 1, 1],
      "skill_level_required": [0, 2, 0, 2, 1, 0]
    }
    //other patients
 ]
```
## Nurses

The nurses section comprises a list of individual nurses, each with their unique identifier ```id```, ```skill_level```, and the list of their working shifts. Each working shift includes the ```day``` of the shift, the shift type (```shift```), and the maximum workload ```max_load``` allowed for that shift.

```js
"nurses": [
    {
      "id": "n00",
      "skill_level": 0,
      "working_shifts": [
        {
          "day": 0,
          "shift": "early",
          "max_load": 10
        },
        {
          "day": 1,
          "shift": "night",
          "max_load": 5
        },
        // other working shifts
        ]
    },
    // other nurses
    ]
```

## Surgeons, OT and Rooms

To each surgeon is assigned an ```id``` and a ```max_surgery_time``` list specifying their availability (in minutes) on each day of the scheduling period. 

Similarly, each operating theater is identified by an ```id``` accompanied by an ```availability```list indicating the theater's availability (in minutes) for each day of the scheduling period.

Finally, to each room is associated an ```id``` and a ```capacity``` (constant during the entire scheduling period).

``` js
 "surgeons": [
    {
      "id": "s0",
      "max_surgery_time": [0, 360, 0, 600, 480, 0, 0, 600]
    },
    //other surgeons
  ],
  "operating_theaters": [
    {
      "id": "t0",
      "availability": [0, 600, 720, 600, 600, 720, 720]
    },
    //other operating theaters
  ],
  "rooms": [
    {
      "id": "r0",
      "capacity": 2
    },
    {
      "id": "r1",
      "capacity": 3
    },
   //other rooms
   ]
```

An example of a full instance is available below:

[Download Toy file](../json_files/toy.json)