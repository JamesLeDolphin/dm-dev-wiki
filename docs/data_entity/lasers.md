---
title: Lasers
layout: default
parent: Data Entity Variants
nav_order: 3
has_toc: false
---

- TOC
{:toc}
* * *

# Lasers
As of the 1.20.1 update, Dalek Mod supports adding custom laser types via data packs. To do this, create a new JSON file in `data/{modid}/laser_types/` folder.
> **Example**: Orange laser (<span style="color: rgb(255,140,60);">rgb(255,140,60)</span>)
> ```json
> {
>   "red": 255,
>   "green": 140,
>   "blue": 60,
>   "damage": 2.5
> }
> ```

> **Example**: Hearts
> ```json
> {
>   "render_model": false,
>   "damage": 0,
>   "particle": "minecraft:heart",
>   "hit_effect": {
>     "type": "dalekmod:effect",
>     "effect": "minecraft:regeneration",
>     "duration": 5,
>     "amplifier": 500
>   }
> }
> ```

> **Example**: Bullet
> ```json
> {
>   "red": 255,
>   "green": 255,
>   "blue": 255,
>   "damage": 2.5,
>   "model": "dalekmod:bullet"
> }
> ```


## Properties

| Property                | Type                                   | Description                              | Default            | Required |
| --------                | ----                                   | -----------                              | -------            | -------- |
| `damage`                | Float                                  | Amount of damage this laser deals on hit | N/A                | ✅       |
| `red`                   | Integer ([rgb])                        | Red (0-255)                              | `0`                | ❌       |
| `green`                 | Integer ([rgb])                        | Green (0-255)                            | `0`                | ❌       |
| `blue`                  | Integer ([rgb])                        | Blue (0-255)                             | `0`                | ❌       |
| `alpha`                 | Integer                                | Alpha/Opacity (0-255)                    | `255`              | ❌       |
| `hit_effect`            | [LaserHitEffect]                       | What to do when the laser hits something | (empty)            | ❌       |
| `particle`              | [ResourceLocation] to a [ParticleType] | Particle to spawn                        | (empty)            | ❌       |
| `render_model`          | Boolean                                | Whether to render the model or not       | `true`             | ❌       |
| `ticks_alive`           | Integer                                | How long until the laser gets discarded  | `25`               | ❌       |
| `model`                 | [ResourceLocation]                     | Model to render the laser as             | `dalekmod:laser`   | ❌       |

## Hit Effects

Hit effects can be used to do something on hit.

Dalek Mod provides three hit effects; more can be added by registering them to `DMLaserHitEffects#HIT_EFFECTS`.

### Explosion

```json
"type": "dalekmod:explosion",
```

Spawns an explosion on hit

| Property         | Type                                   | Description                             | Default | Required |
| --------         | ----                                   | -----------                             | ------- | -------- |
| `explosion_size` | Integer                                | Size of the explosion                   | `2`     | ❌       |
| `causes_fire`    | Boolean                                | True if the explosion should cause fire | `false` | ❌       |

### Effect

```json
"type": "dalekmod:effect",
```

Inflicts a potion effect when hitting an entity.

| Property         | Type                                   | Description                                | Default | Required |
| --------         | ----                                   | -----------                                | ------- | -------- |
| `effect`         | [ResourceLocation] to a [MobEffect]    | Size of the explosion                      | N/A     | ✅       |
| `duration_ticks` | Integer                                | Amount of ticks the effect should last for | N/A     | ✅       |
| `amplifier`      | Integer                                | Amplifier for the effect                   | `0`     | ❌       |

### Fire
```json
"type": "dalekmod:fire",
```

Sets entity on fire on hit.

| Property   | Type                                   | Description                              | Default | Required |
| --------   | ----                                   | -----------                              | ------- | -------- |
| `duration` | Integer                                | Amount of ticks the fire should last for | N/A     | ✅       |


[LaserHitEffect]: #hit-effects
[ParticleType]: https://minecraft.wiki/w/Particles#Types_of_particles
[MobEffect]: https://minecraft.wiki/w/Effect#List_of_effects
[ResourceLocation]: https://minecraft.wiki/w/Identifier
[rgb]: https://www.w3schools.com/colors/colors_picker.asp
