---
title: Data Entity Variants
layout: default
parent: Home
---

# Data Entity Variants
Dalek Mod 1.20.1 allows adding custom variants to specific entities, all through data- and resource packs. 

This system is currently supported by three entities:

- [Daleks](./data_entity/daleks)
- [Cybermen](./data_entity/cybermen)
- [Autons](./data_entity/autons)

While Dalek and Cyberman variants allow for more modifications, auton variants only allow adding new skins.

## Difficulty Based Values 
Some values in Entity Variants can depend on the game's difficulty.

```json
"attack_damage": {
    "easy": 4,
    "normal": 6,
    "hard": 8
  }
```
> Different values depending on the difficulty

It is also possible to give a constant value for all difficulties like so:
```json
"attack_damage": 6
```
> Same value on all difficulties

## Actions
Entity Actions are a simple way of modifying entity actions under certain conditions.

### Death Action
Action run when entity dies. Currently Dalek Mod provides two death actions. Addon mods can add more by implementing `EntityDeathAction` interface and registering it to `DMEntityActions.DEATH_ACTIONS` registry.

#### Explode
Explodes the entity on death.

ID: dalekmod:explode
```json
{
    "type": "dalekmod:explode", //Required: Specify Death Action type.
    "power": 2, //Optional: Explosion Power. Defaults to 2.
    "causes_fire": false, //Optional: Whether explosion causes nearby terrain to be on fire.
    "chance": 1.0 //Optional: Chance the entity explodes.
}
```

#### Summon
Summons an entity on death.

ID: dalekmod:summon
```json
{
    "type": "dalekmod:summon", //Required: Specify Death Action type.
    "entity_type": "minecraft:pig", //Required: Type of entity to summon.
    "chance": 1.0 //Optional: Chance the entity will be summoned.
}
```

### Hurt Action
Action run when entity is hurt. Currently Dalek Mod provides three hurt actions. Addon mods can add more by implementing `EntityHurtAction` interface and registering it to `DMEntityActions.HURT_ACTIONS` registry.

#### Multiply
Multiplies the damage by the multiplier.

ID: dalekmod:mul
```json
{
    "type": "dalekmod:mul", //Required: Specify Hurt Action type.
    "multiplier": 2.0 //Required: Multiplier with which the damage is multiplied.
}
```

#### Teleport
Teleports the entity.

ID: dalekmod:teleport
```json
{
    "type": "dalekmod:teleport", //Required: Specify Hurt Action type.
    "chance": 1.0 //Optional: Chance of the entity teleporting when hurt. Defaults to 1.
}
```

#### Pickaxe Mine
Doubles the incoming damage if the tool used is a pickaxe.
This is currently only used for Stone Dalek and will be removed in future releases.

ID: dalekmod:mine_pickaxe

```json
{
    "type": "dalekmod:mine_pickaxe" //Required: Specify Hurt Action type.
}
```

### Interact Action
Action run entity is interacted with (ie. right-clicked). Dalek Mod currently only adds one entity interact action. Addon mods can add more by implementing `EntityInteractAction` interface and registering it to `DMEntityActions.INTERACT_ACTIONS` registry.

#### Eat
Hurts the entity and fills the players food level and saturation.

ID: dalekmod:eat
```json
{
    "type": "dalekmod:eat", //Required: Specify Interaction Action type.
    "food_level_modifier": 1, //Required: Food level modifier. Must be an integer
    "saturation": 1.0, //Required: Saturation to give to player.
    "damage": -1 //Required: Damage to deal to the entity being eaten. -1 removes the entity from world without killing it.
}
```