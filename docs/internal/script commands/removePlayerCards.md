# removePlayerCards

`removePlayerCards` takes three numerical parameter and is used to remove cards from the players inventory.
It can only be used for script 1, 4 and 5 of NPCs.

> This command is buggy for spells and fairies, instead of removing some number of cards it removes *every* card of the selected type and id (e.g. instead of removing one Silia it would be remove all Silia fairies).

Its parameters are:

1. The number of cards to remove
2. [The card type](../CardId)
3. The card id

Its short-form is `9`.
