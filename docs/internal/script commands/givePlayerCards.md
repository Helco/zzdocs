# givePlayerCards

`givePlayerCards` takes three numerical parameters and adds a number of cards to the players inventory. Fairies are processed especially for starting spells and level.

The parameters are:

1. The number of cards to give
2. The type of the cards (see [CardId](../CardId.md))
3. The ID of the cards

Its short form is `1`.

## Fairy (based on v1.010)

The starting level and a first spell is based upon whether the player has any fairy in its deck. The starting level for a first fairy (in the *deck*) is 9 whilst for secondary fairies it is 3. The spells are more complicated:

### Spells for first fairies

The spell for a first fairy depends on its element class:

| Class  | SpellID | Spell-Name  |
|:-------|:-------:|:------------|
| Nature |    0    | Small quake |
| Water  |   10    | Small waves |
| Stone  |   30    | Small stone |
| *other*|   -1    | *Crashes the game* |

### Spells for secondary fairies

A single active spell is chosen based on the fairies element class and a random level between 3-9 (inclusive), even though the level is fixed at 3. The method for chosing the spell is the same as [for defaultWizform](defaultWizform.md).

> TODO: Is there some point in the original game where a fairy is given with a spell assigned it should not be able to cast?
