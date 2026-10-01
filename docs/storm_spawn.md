---
title: Storm Spawner Item Lists
layout: default
nav_order: 5
---

# Storm Spawner Item Lists

You can add/modify the lists of items required to spawn the Dalek Storm.

To add a custom list, create a new json file at `data/{modid}/storm/spawn/`.

```json
{
  "id": "dalekanium", // Name of the list
  "items": [ // Items required
    {
      "item": "dalekmod:emblemized_dalekanium_block",
      "count": 5
    },
    {
      "item": "dalekmod:refined_dalekanium_block",
      "count": 5
    },
    {
      "item": "dalekmod:plunger",
      "count": 1
    }
  ]
}
```
