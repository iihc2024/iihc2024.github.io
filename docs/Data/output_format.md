---
layout: default
title: Output
parent: Data
nav_order: 2
---
<!--TODO: expand the explanation of the .json output file (e.g. syntax patient is not admitted, nurse is not assigned to any room etc., add warning about data types)-->

The solution file format is divided into two sections: one about patients and one about nurses. The following fragment illustrates both sections.

```js
{
  "patients": [
    {
      "id": "p00",
      "admission_day": 4,
      "room": "r3",
      "operating_theater": "t0"
    },
    ...
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
        ...
        ]
    },
    ...
    ]
}
```