# modifyWizform

`modifyWizform` changes the fairy it was triggered on in some way determined by its parameters. It can only be used in item scripts.

Its parameters are:

1. The category of change to execute
2. Some value related to the change

| Category | Name               | Description |
|:--------:|:-------------------|-------------|
|     0    | Heal               | Heals the fairies by the given amount (only if it is alive) |
|     1    | AddXP              | Adds a given amount of XP (only used by the cut item "Amulet of Experience") |
|     2    | ClearStatusEffects | Removes status effects like posioned, frozen, burned |
|     7    | Transform          | Changes the fairy type to the given id (e.g. as used by evolution stones or dwarven tool) |
|     8    | AddNearLevelXP     | Adds XP to be one less than for the next level |
|     9    | Set Unknown        | Sets an unknown fairy value (unused) |
|    10    | Set Unknown        | Sets an unknown fairy value (unused) |
|    11    | Set Unknown        | Sets an unknown fairy value (unused) |
|    12    | Set Unknown        | Sets an unknown fairy value (unused) |
|    13    | Set Unknown        | Sets an unknown fairy value (unused) |
|    14    | Add Unknown        | Adds the arg to some unknown fairy value (unused) |
|    16    | Revive             | Revives the fairy and heals a third of the max HP |
|    17    | Fill Mana          | Sets the mana of every spell to max |
|    18    | Rename             | Renames a fairy |

Its short-form is `:`.
