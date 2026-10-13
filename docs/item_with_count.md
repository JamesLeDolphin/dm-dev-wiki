---
title: Item With Count
layout: default
has_toc: false
---

# Item With Count

`ItemWithCount`s are used for specifying an item with a specific quantity (hence the name).

They're used in:
- [Storm Spawner lists](./storm_spawn)
- [Tardis Interior Recipes](./tardis/interiors#recipe)

> Example: 768 Quartz Blocks
> ```json
> {
>   "item": "minecraft:quartz_block",
>   "quantity": 768
> }
> ```

| Property   | Type                          | Description               | Required |
| --------   | ----                          | -----------               | -------- |
| `item`     | [ResourceLocation] to an item | The ID of the item.       | ✅       |
| `quantity` | Integer                       | The quantity of the item. | ✅[^1]    |
| `count`    | Integer                       | The quantity of the item. | ✅[^1]    |


[^1]: `quantity` and `count` are the same; either name can be used.

[ResourceLocation]: https://minecraft.wiki/w/Identifier
