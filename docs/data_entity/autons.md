---
title: Autons
layout: default
parent: Data Entity Variants
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

Model field in auton skin json file must point to a file in `assets/{id}/variants/entity/auton/` folder. This file is used by the client to actually get the autons model and texture.

```json
{
    "parent": "dalekmod:auton", //Model to use
    "texture": "dalekmod:blue_auton" //Texture to use
}
```