---
title: Daleks
layout: default
parent: Data Entity Variants
nav_order: 0
has_toc: false
---

- TOC
{:toc}
* * *

# Daleks
As of the 1.20.1 update, Dalek Mod supports adding custom daleks via data packs. To do this, create a new JSON file in `data/{modid}/dalek_variants/` folder.

Example dalek JSON file:
```json
{
  "name": {
    "translate": "dalekmod.dalek_type.chocolate"
  },
  "max_health": 14,
  "laser_type": "dalekmod:green",
  "can_fly": true,
  "attack_damage": {
    "easy": 4,
    "normal": 6,
    "hard": 8
  },
  "actions": {
    "interact": {
      "type": "dalekmod:eat",
      "food_level_modifier": 6,
      "saturation": 10,
      "damage": -1
    }
  },
  "sounds": {
    "shoot": "dalekmod:entity.dalek_laser_shoot"
  },
  "entries": [
    {
      "id": "dalekmod:chocolate_dalek",
      "model": "dalekmod:chocolate_dalek"
    },
    {
      "id": "dalekmod:chocolate_dalek_dark",
      "model": "dalekmod:chocolate_dalek_dark"
    },
    {
      "id": "dalekmod:chocolate_dalek_white",
      "model": "dalekmod:chocolate_dalek_white"
    },
    {
      "id": "dalekmod:chocolate_dalek_strawberry",
      "model": "dalekmod:chocolate_dalek_strawberry"
    },
    {
      "id": "dalekmod:chocolate_dalek_matcha",
      "model": "dalekmod:chocolate_dalek_matcha"
    }
  ]
}
```

## Properties

| Property           | Type                                                       | Description                                                | Default                                         | Required |
| --------           | ----                                                       | -----------                                                | -------                                         | -------- |
| `name`             | [Component](https://misode.github.io/text-component/)      | Name of the dalek. Please use translatable components here | N/A                                             | ✅       |
| `entries`          | List\<[Entry](#entries)>                                   | Entries for this dalek variant                             | N/A                                             | ✅       |
| `max_health`       | [DifficultyBasedValue]\<Float> | Max health                                                 | N/A                                             | ✅       |
| `laser_type`       | [ArmBasedValue]\<[Resource Location]>                      | The laser type that will be fired                          | N/A                                             | ✅       |
| `sounds`           | [Sounds]                                                   | The sounds played by this dalek                            | (see [Sounds])                                  | ❌       |
| `attack_damage`    | [DifficultyBasedValue]\<Float>                             | How much damage the dalek does                             | `2`                                             | ❌       |
| `move_speed`       | [DifficultyBasedValue]\<Float> | How fast the dalek can move                                | `0.35`                                          | ❌       |
| `can_fly`          | Boolean                                                    | Should this dalek be able to fly?                          | `false`                                         | ❌       |
| `can_burn`         | Boolean                                                    | False if the dalek is immune to fire                       | `false`                                         | ❌       |
| `left_arm_chance`  | [ArmChance]                                                | The left arms this dalek is able to have                   | (see [Default Left Arms](#default-left-arms))   | ❌       |
| `right_arm_chance` | [ArmChance]                                                | The right arms this dalek is able to have                  | (see [Default Right Arms](#default-right-arms)) | ❌       |
| `charge_time`      | Float                                                      | How long this dalek should take to charge its attacks      | `1`                                             | ❌       |
| `actions`          | [Actions]                                                  | [Actions] for this dalek                                   | (none)                                          | ❌       |
| `faction`          | [DalekFaction]                                             | The faction for this dalek                                 | `"misc"`                                        | ❌       |
| `add_conditions`   | [AddConditions](../add_conditions)                         | Conditions for this dalek variant to be added              | (none)                                          | ❌       |

<!-- ```java -->
<!-- 	public static final Codec<DalekVariant> CODEC = RecordCodecBuilder.create(inst -> inst.group( -->
<!-- 		// ExtraCodecs.COMPONENT.fieldOf("name").forGetter(DalekVariant::name), -->
<!-- 		// Codec.INT.fieldOf("max_health").forGetter(DalekVariant::maxHealth), -->
<!-- 		// ArmBasedValue.codecWithFallback(ResourceLocation.CODEC).fieldOf("laser_type").forGetter(DalekVariant::laserType), -->
<!-- 		// Sounds.CODEC.optionalFieldOf("sounds", Sounds.DEFAULT).forGetter(DalekVariant::sounds), -->
<!-- 		// DMExtraCodecs.withAlternative(DifficultyBasedValue.FLOAT_CODEC, floatToValue()).fieldOf("attack_damage").forGetter(DalekVariant::attackDamage), -->
<!-- 		// DMExtraCodecs.withAlternative(DifficultyBasedValue.FLOAT_CODEC, floatToValue()).optionalFieldOf("move_speed", new DifficultyBasedValue<>(0.2f, 0.2f, 0.2f)).forGetter(DalekVariant::moveSpeed), -->
<!-- 		// Codec.BOOL.optionalFieldOf("can_fly", false).forGetter(DalekVariant::canFly), -->
<!-- 		// Codec.BOOL.optionalFieldOf("can_burn", false).forGetter(DalekVariant::canBurn), -->
<!-- 		// ArmChance.CODEC.optionalFieldOf("left_arm_chance", ArmChance.DEFAULT_LEFT).forGetter(DalekVariant::leftArmChance), -->
<!-- 		// ArmChance.CODEC.optionalFieldOf("right_arm_chance", ArmChance.DEFAULT_RIGHT).forGetter(DalekVariant::rightArmChance), -->
<!-- 		// Codec.FLOAT.optionalFieldOf("charge_time", 1f).forGetter(DalekVariant::chargeTime), -->
<!-- 		// Entry.CODEC.listOf().fieldOf("entries").forGetter(DalekVariant::entries), -->
<!-- 		// Actions.CODEC.optionalFieldOf("actions", Actions.EMPTY).forGetter(DalekVariant::actions), -->
<!-- 		DalekFaction.CODEC.optionalFieldOf("faction", DalekFaction.MISC).forGetter(DalekVariant::dalekFaction), -->
<!-- 		// AddConditions.CODEC.optionalFieldOf("add_conditions", AddConditions.NONE).forGetter(DalekVariant::addConditions) -->
<!-- 	).apply(inst, DalekVariant::new)); -->
<!-- ``` -->

## Sounds
You can override the sounds that the dalek plays. The sounds are specified as [ArmBasedValue]s of [Resource Location]s for the value.

All sounds are optional, and will play the default when unset. You can set it to `minecraft:intentionally_empty` if you want no sound to be played

| Property                | Default                                 | Played when                                 |
| --------                | -------                                 | -----------                                 |
| `shoot`                 | `dalekmod:entity.dalek_spark_shoot`,    | Dalek shoots                                |
| `ambient`               | `dalekmod:entity.dalek_skaro_ambient`   | Ambient                                     |
| `hurt`                  | `dalekmod:entity.dalek_hurt`            | Dalek gets hurt                             |
| `attack`                | `dalekmod:entity.dalek_skaro_attack`    | Dalek charges/reloads gun                   |
| `death`                 | `minecraft:intentionally_empty`         | Dalek dies                                  |
| `move`                  | `dalekmod:entity.dalek_glide`           | Dalek glides                                |
| `hover`                 | `dalekmod:entity.dalek_hover`           | Dalek hovers (used for daleks that can fly) |

> **Example**: changing shoot sound depending on the arm:
> ```json
> {
>   "sounds": {
>     "shoot": {
>       "flamethrower": "dalekmod:entity.dalek_flame_thrower_shoot",
>       "default": "dalekmod:entity.dalek_laser_shoot"
>     }
>   }
> }
> ```

## Entries

Entries just need an `id`, and the `model` to use.
The `model` should be the asset subpath for the [defaulted geo model](https://github.com/bernie-g/geckolib/wiki/Geo-Models-(Geckolib4)#defaulted-models).

```json
{
  "id": "mymod:my_dalek",
  "model": "mymod:my_dalek"
}
```

The subtype for all daleks is `entity/dalek`, so for example, `mymod:my_dalek` will have the following paths:
- Texture:   `mymod:textures/entity/dalek/my_dalek.png`
- Glowmask:  `mymod:textures/entity/dalek/my_dalek_glowmask.png`
- Model:     `mymod:geo/entity/dalek/my_dalek.geo.json`
<!-- - Animation: `mymod:animations/entity/dalek/my_dalek.animation.json` -->

For entries that need to share the same model with different textures, you can use a [model variant](../model_variants).

## Factions
Daleks can have a faction, which will affect their behaviour towards other daleks. (i.e. imperials and renegades will fight eachother, and friendly fire won't do any damage)

The possible dalek factions are:
- `renegade`
- `imperial`
- `misc`

## Arm Types
Daleks can spawn with different arms.

The possible arm types a dalek can have are:
- `GunArm`
- `SuctionArm`
- `ClawArm`
- `FlameThrowerArm`
- `MachineGunArm`

### Arm chances
You can customize which arms the dalek is able to have by setting `left_arm_chance` and `right_arm_chance` on the dalek variant. The left arm is the one that the dalek will shoot from.

Each arm type has an integer with a weight for the arm to be chosen; for example if the gun arm has a weight of 2, and the flamethrower arm has a weight of 1, the flamethrower will have a 1/3 chance of being chosen.

The properties for `ArmChance` are:
- `gun_arm_chance`
- `suction_cup_arm_chance`
- `claw_arm_chance`
- `flame_thrower_arm_chance`
- `machine_gun_arm_chance`

If you specify the `ArmChance`, all unset values will default to `0`.

#### Default Left Arms
```json
{
    "gun_arm_chance": 1,
    "flame_thrower_arm_chance": 0,
    "machine_gun_arm_chance": 0
}
```

#### Default Right Arms
```json
{
    "suction_cup_arm_chance": 1,
    "claw_arm_chance": 0,
}
```

### Arm-Based Values
Some values in Dalek Variants can depend on which arm the dalek currently has.

> ```json       
> "laser_type": {
>     "flamethrower": "dalekmod:fire",
>     "default": "dalekmod:blue"
> }
> ```
> The dalek will shoot fire when it has the flamethrower, or blue lasers for other arms

It is also possible to give a constant value for all arms:
> ```json
> "laser_type": "dalekmod:blue"
> ```
> The dalek will shoot blue lasers no matter which arm it has

The properties for `ArmBasedValue`s are:
- `default` (required; the value that other arms will default to if unset)
- `gunstick`
- `suction_cup`
- `claw_arm`
- `flamethrower`
- `machine_gun`

All arm based values currently check the left arm and not the right one.

<!-- The arm that gets checked for an ArmBasedValue depends on the context. -->
<!-- (no it doesn't, but i made a table for it anyway before realizing they only use the left lmao) -->
<!-- | What for    | Arm | -->
<!-- | --------    | --- | -->
<!-- | Laser Types | Left | -->
<!-- | Shoot Sound | Left | -->
<!-- | Death Sound | Left | -->
<!-- | Move Sound  | Left | -->
<!-- | Hover Sound | Left | -->
<!-- | Hurt Sound  | Left | -->
<!-- | Attack Sound  | Left | -->


You can get the value of an ArmBasedValue with `getValue(ArmType armType)`
```java
DalekVariant variant = dalek.getEntityVariant();

dalek.playSound(variant.sounds().shootSound().getValue(dalek.leftArm()), 1.0F, 1.0F);
```

[Resource Location]: https://minecraft.wiki/w/Identifier
[ArmBasedValue]: #arm-based-values
[ArmChance]: #arm-chances
[DalekFaction]: #factions
[Sounds]: #sounds
[Actions]: ./#actions
[DifficultyBasedValue]: ./#difficulty-based-values
