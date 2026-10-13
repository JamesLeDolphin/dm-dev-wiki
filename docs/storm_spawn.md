---
title: Storm Spawner Item Lists
layout: default
nav_order: 3
has_toc: false
---

# Storm Spawner Item Lists

You can add/modify the lists of items required to spawn the Dalek Storm.

To add a custom list, create a new json file at `data/{modid}/storm/spawn/`.

```json
{
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

| Property          | Type                  | Description                                  | Default               | Required |
| --------          | ----                  | -----------                                  | -------               | -------- |
| `items`           | List<[ItemWithCount]> | The items required to spawn the Dalek Storm. | N/A                   | ✅       |
| `add_conditions`  | [AddConditions]       | Conditions for this list to be added.        | (none)                | ❌       |


[AddConditions]: ./add_conditions
[ItemWithCount]: ./item_with_count
