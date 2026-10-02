---
title: Model Variants
layout: default
nav_order: 4
has_toc: false
---

# Model Variants

"Model variants" are Dalek Mod 1.20's equivalent to the model inheritance systems from [JavaJSON](https://github.com/Bug1312/JavaJSONLib) and [block/item](https://minecraft.wiki/w/Tutorial:Models) models, because geckolib doesn't have a way to do that normally.

> **"Wouldn't be dalekmod without a special dalekmod-specific model system."**
>
> &mdash; <cite>Sam Tees</cite>

Model variants are used by some entities that need to share the same model with different textures.

Supported entities/blocks will use the values provided in the model variant if it exists; otherwise, it will look for a normal geo model with the same name.

Model variants are in the `variants/` folder, with the extension `.variant.json`, and should share the same subtype as the [defaulted geo model](https://github.com/bernie-g/geckolib/wiki/Geo-Models-(Geckolib4)#defaulted-models). e.g. daleks should be in `entity/dalek`

```json
// nether_special_weapons_dalek.variant.json
{
    "texture": "dalekmod:nether_special_weapons_dalek",  // The texture this  model variant should use
    "glowmask": "dalekmod:nether_special_weapons_dalek", // The glowmask this model variant should use
    "parent": "dalekmod:special_weapons_dalek"           // The parent model to use
}
```

## Supported Entities:
* [Autons](./data_entity/autons)
* [Cybermen](./data_entity/cybermen#entries)
* [Daleks](./data_entity/daleks)

## Supported Blocks:
* [Cyberman Heads](./data_entity/cybermen#cyberman-heads)
