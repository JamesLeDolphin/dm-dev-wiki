---
title: TARDIS
layout: default
nav_order: 1
---

- TOC
{:toc}
* * *

# TARDIS
Dalek Mod allows adding custom TARDIS interiors, exteriors, destinations and exterior layers via data packs.

## Destinations
TARDIS destinations are used for determining whether the TARDIS can land in a dimension or if it needs to be unlocked with a dimension data card first. In 1.20.1+ all dimensions without a destination JSON file are unlocked by default.

Path: `data/{modid}/tardis/destinations/`

```json
{
    "name": "Overworld", //Optional: Pretty name of the dimension
    "dimension": "minecraft:overworld", //Required: Dimension
    "icon": "dalekmod:overworld", //Required: Path to the icon shown on Dimensional Selector Panel. Icon file must be in {modid}:textures/planets/{path}.
    "needs_card": false, //Optional: Whether the dimension needs to be unlocked with a dimension data card or not. Defaults to false.
    "coordinate": [0, 0] //Optional: Defaults to [0, 0]
}
```

## Layers

Layers were first introduced in 1.16 under the name "snowmaps". In 1.20 the snowmaps were reworked to allow multiple different layers, and have therefore been renamed to TARDIS Layers.

Path: `data/{modid}/tardis/layers/`

```json
{
    //List of blocks that would make the TARDIS exterior apply this layer. Accepts tags
    "blocks": [
        "minecraft:snow",
        "#minecraft:ice"
    ],
    //List of biomes that would make the TARDIS exterior apply this layer. Accepts tags
    "biomes": [
        "minecraft:snowy_plains"
    ] 
}
```
Name of the JSON file must be suffixed at the end of any layer texture.

<sup><sub>Ogres have layers - Shrek</sub></sup>

## Interiors
See [TARDIS Interiors](./interiors).

## Exteriors
See [TARDIS Exteriors](./exteriors).