---
title: Cybermen
layout: default
parent: Data Entity Variants
nav_order: 1
---

- TOC
{:toc}
* * *

# Cybermen
To add custom cyberman variants with a data pack, create a new JSON file in `data/{modid}/cyberman_variants/` folder.

## Cyberman Variants

To add a cyberman variant, create a new json file at `data/{modid}/cyberman_variants/`.

Here's the cybus cyberman for example:
```json
{
  "name": {
    "translate": "dalekmod.cyberman_type.cybus"
  },
  "max_health": 40,
  "gun_chance": 0.2,
  "laser_type": "dalekmod:orange",
  "attack_damage": 2,
  "move_speed": 0.35,
  "can_burn": false,
  "allergic_to_gold": {
    "easy": true,
    "normal": true,
    "hard": false
  },
  "entries": [
    {
      "id": "dalekmod:cybus_cyberman",
      "model": "dalekmod:cybus_cyberman"
    },
    {
      "id": "dalekmod:cybus_cyberleader",
      "model": "dalekmod:cybus_cyberleader"
    },
    {
      "id": "dalekmod:dark_cybus_cyberman",
      "model": "dalekmod:dark_cybus_cyberman"
    }
  ]
}
```

## Properties

| Property                | Type                                                         | Description                                                         | Default               | Required |
| --------                | ----                                                         | -----------                                                         | -------               | -------- |
| `name`                  | [Component](https://misode.github.io/text-component/)        | The name of the cyberman. Please use translatable components here   | N/A                   | ✅       |
| `entries`               | List\<[Entry](#entries)>                                     | The entries for this cyberman variant                               | N/A                   | ✅       |
| `max_health`            | [DifficultyBasedValue](./#difficulty-based-values)\<Float>   | The max health                                                      | `40`                  | ❌       |
| `gun_chance`            | [DifficultyBasedValue](./#difficulty-based-values)\<Float>   | The chance that the cyberman can have a gun (0 = never; 1 = always) | `0.2`                 | ❌       |
| `laser_type`            | ResourceLocation                                             | The laser type that will be fired                                   | `dalekmod:orange`     | ❌       |
| `sounds`                | [Sounds](#sounds)                                            | The sounds played by this cyberman                                  | (see default sounds)  | ❌       |
| `attack_damage`         | [DifficultyBasedValue](./#difficulty-based-values)\<Float>   | The attack damage                                                   | `2`                   | ❌       |
| `move_speed`            | [DifficultyBasedValue](./#difficulty-based-values)\<Float>   | The movement speed                                                  | `0.35`                | ❌       |
| `can_burn`              | [DifficultyBasedValue](./#difficulty-based-values)\<Boolean> | False if the cyberman is immune to fire                             | `true`                | ❌       |
| `allergic_to_gold`      | [DifficultyBasedValue](./#difficulty-based-values)\<Boolean> | True if the cyberman is allergic to gold                            | `true`                | ❌       |
| `cybermat_chance`       | [DifficultyBasedValue](./#difficulty-based-values)\<Float>   | The chance of spawning cybermats                                    | `0.14285715` (1/7)    | ❌       |
| `add_conditions`        | [AddConditions](../add_conditions)                           | Conditions for this cyberman variant to be added                    | (none)                | ❌       |

## Sounds
You can override the sounds that the cyberman plays. The sounds are specified as `ResourceLocation`s for the value.

All sounds are optional, and will play the default when unset. You can set it to `minecraft:intentionally_empty` if you want no sound to be played

| Property                | Default                          | Played when        |
| --------                | -------                          | -----------        |
| `shoot`                 | `dalekmod:entity.cyberman_shoot`,| Cyberman shoots    |
| `ambient`               | `dalekmod:entity.cyberman_living`| Ambient            |
| `hurt`                  | `dalekmod:entity.cyberman_hurt`  | Cyberman gets hurt |
| `attack`                | `dalekmod:entity.cyberman_living`| Cyberman shoots    |
| `death`                 | `minecraft:intentionally_empty`  | Cyberman dies      |
| `move`                  | `dalekmod:entity.cyberman_step`  | Cyberman walks     |

## Entries

Entries just need an `id`, and the `model` to use.
The `model` should be the asset subpath for the [defaulted geo model](https://github.com/bernie-g/geckolib/wiki/Geo-Models-(Geckolib4)#defaulted-models).

```json
{
  "id": "mymod:my_cyberman",
  "model": "mymod:my_cyberman"
}
```

The subtype for all cybermen is `entity/cyberman`, so for example, `mymod:my_cyberman` will have the following paths:
- Texture:   `mymod:textures/entity/cyberman/my_cyberman.png`
- Glowmask:  `mymod:textures/entity/cyberman/my_cyberman_glowmask.png`
- Model:     `mymod:geo/entity/cyberman/my_cyberman.geo.json`
- Animation: `mymod:animations/entity/cyberman/my_cyberman.animation.json`

For entries that need to share the same model with different textures, you can use a [model variant](../model_variants).

### Cyberman Heads

You will also need to make a model for the cyberman head block for each cyberman entry.

The heads use the subtype `block/cyberman_head` for the model, and `entity/cyberman` for the textures, and share the same name as the entity model.

For example, the head model for `mymod:my_cyberman` will be in `mymod:geo/block/cyberman_head/my_cyberman.geo.json`

For the head model, you can just copy the entity model, delete everything except for the head, and drop it down so it's not floating.
