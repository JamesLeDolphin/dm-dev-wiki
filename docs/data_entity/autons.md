---
title: Autons
layout: default
parent: Data Entity Variants
nav_order: 2
has_toc: false
---

# Autons
Auton variants are not as advanced as Dalek and Cyberman variants, and can only have custom skins.

To add a custom auton skin, create a new json file at `data/{modid}/auton_skins/`.
```json
{
    "id": "dalekmod:blue_auton", //Required: ID of the auton
    "model": "dalekmod:blue_auton", //Required: Variant model.
    "add_conditions": {}, //Optional: Conditions when to add the skin
    "spawn_conditions": {} //Optional: Contitions when to spawn an auton with this skin.
}
```

Model field in auton skin json file can be a subpath for the [defaulted geo model](https://github.com/bernie-g/geckolib/wiki/Geo-Models-(Geckolib4)#defaulted-models) (the subtype is `entity/auton`).

[Model Variants](../model_variants) are also supported.

```json
// dalekmod:variants/entity/auton/blue_auton.variant.json
{
    "parent": "dalekmod:auton", //Model to use
    "texture": "dalekmod:blue_auton" //Texture to use
}
```
