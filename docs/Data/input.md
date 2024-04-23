---
layout: default
title: Input format
parent: Data
nav_order: 1
---
<!--TODO: Expand explanation of .json input, use toy instance, add link to allow download of entire toy instance-->

The input file contains a header part in addition to separate sections for nurses, rooms, operating theaters, surgeons, patients, and occupants.
Below is an example of the header part, containing the general data and the weights of the cost components.

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
  ...
}
```

Below is a fragment of an example of the section about nurses. For each nurse, we have the ID, the skill level and a list of working shifts with their respective maximum workload.

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
        ...
        ]
    },
    ...
    ]
```

The structure of the sections on rooms, operating theaters, and surgeons is rather simple, as shown by the following fragment.

``` js
 "surgeons": [
    {
      "id": "s0",
      "max_surgery_time": [0, 360, 0, 600, 480, 0, 0, 600]
    },
    ...
  ],
  "operating_theaters": [
    {
      "id": "t0",
      "availability": [0, 600, 720, 600, 600, 720, 720]
    },
    ...
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
   ... 
   ]
```

Finally, we introduce the structure of the patient data, divided into occupants (present at the beginning of the scheduling period) and regular patients.

```js
 "occupants": [
    {
      "id": "a0",
      "gender": "male",
      "age_group": "elderly",
      "length_of_stay": 2,
      "workload_produced": [2, 1, 1, 2, 3, 2],
      "skill_level_required": [1, 2, 0, 0, 0, 0],
      "room_id": "r21"
    },
    ...
    ]
 "patients": [   
    {
      "id": "p28",
      "mandatory": true,
      "gender": "male",
      "age_group": "elderly",
      "length_of_stay": 3,
      "surgery_release_day": 3,
      "surgery_due_day": 17,
      "surgery_duration": 90,
      "surgeon_id": "s0",
      "incompatible_room_ids": ["r2"],
      "workload_produced": [1, 1, 1, 2, 1, 1, 1, 2, 1],
      "skill_level_required": [1, 2, 0, 2, 0, 0, 2, 1, 1]
    }
    ...
 ]
```

Optional patients do not have a surgery due date.

[Download Toy file](../json_files/toy.json)