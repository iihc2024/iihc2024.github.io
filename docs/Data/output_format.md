---
layout: default
title: Output
parent: Data
nav_order: 2
---
<!--TODO: expand the explanation of the .json output file (e.g. syntax patient is not admitted, nurse is not assigned to any room etc., add warning about data types)-->

The solution file format is divided into two sections: one about patients and one about nurses. 

The patient section comprises of the list of admitted patients. For each admitted patient it's necessary to state their ```id``` their ```admission_day``` as well as the ids representing the ```room``` and ```operating theater``` they have been assigned to.<br>
Non-admitted patients can be either omitted from the solution or be present with the syntax ```"admission_day": "none"```.

The nurse section should contain the list of assignments for each nurse. Each assignment should include the ```day``` and ```shift``` of the working shift and the list of rooms covered by the nurse. If no rooms are covered, the assignment may be omitted or the list of rooms may be empty. If a nurse does not cover any rooms in any of their work shifts, they can be omitted completely.

```js
{
  "patients": [
    {
      "id": "p00",
      "admission_day": 4,
      "room": "r3",
      "operating_theater": "t0"
    },
    //other patients
    {
      "id": "p02",
      "admission_day": "none"
    },
    //remaining patients
    ],
  "nurses": [
    {
      "id": "n00",
      "assignments": [
        {
          "day": 0,
          "shift": "early",
          "rooms": ["r1", "r4"]
        },
        {
          "day": 1,
          "shift": "night",
          "rooms": ["r4", "r5"]
        },
        {
          "day": 2,
          "shift": "night",
          "rooms": []
        },
        //other working shifts
        ]
    },
    //other nurses
    ]
}
```