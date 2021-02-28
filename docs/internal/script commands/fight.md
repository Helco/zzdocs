# fight

`fight` takes two numeric parameters and starts a duel. The parameters determine the arena the duel will take place in and whether the fight is against a single or multiple enemies.
It can only be triggered as part of a dialog interaction.

Its parameters are:

1. The scene ID of the arena or `-1` (see below)
2. `0` for single enemy, `1` for multiple enemies

Its short form is `*`

## Multiple enemies

When the duel spans multiple enemies the enemies are chosen based on:

1. They have to be NPCs
2. They have to have at least one fairy
3. They are at most 11 units away from the primary NPC

## Choosing the arena

The scene ID of the arena can be chosen directly, if however it is `-1` it is chosen semi-randomly based on the level of the first fairy of the primary NPC and whether the fight is against multiple enemies.

| Level-Range | IDs for single enemy | IDs for multiple enemies |
|:-----------:|:--------------------:|:------------------------:|
|     0-25    | 220 | 1020 |
|             | 223 | 1023 |
|             | 229 | 1029 |
||||
|    26-40    | 221 | 1021 |
|             | 224 | 1024 |
|             | 226 | 1026 |
|             | 230 | 1030 |
||||
|    41-...   | 222 | 1022 |
|             | 225 | 1025 |
|             | 227 | 1027 |
|             | 228 | 1028 |
