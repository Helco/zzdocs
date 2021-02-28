# setupGambling

`setupGambling` adds chances to a specific card or blank into the gambling result list. The actual percentage chance for a card/blank therefore depends on how many duplicates of it are in the list and the total number of entries in the gambling list (e.g. for a list `[A, A, A, B, B, B, B, C, D, E]` the chance for `A` is `3/10`).

The parameters are:

1. The number of entries to put into the gambling list
2. The type of the card (see [CardId](../CardId.md)), or `3` for blank (see also below)
3. The ID of the card

The short form is `B`

## Blanks

The decreasing blank chance when the player has clover leaf item is implemented into this command. If the player has it there is a 80% chance per entry that it will not be added to the gambling list.
