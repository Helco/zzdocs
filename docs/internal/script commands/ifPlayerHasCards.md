# ifPlayerHasCards

`ifPlayerHasCards` is a [control flow command](#control-flow) that skips based on whether the player has certain items and/or a minimum number of them. The command takes three numerical parameters:

1. Count of cards (see below)
2. The type of the card (see [CardId](../CardId.md))
3. The id of the card

Its short form is `6`.

## Count

The count parameter has some pieces of special behavior:

- For items/spells
  - if `count == 0` the condition is true if the player does not have the item/spell
  - otherwise it is true if the player has at least `count` of that item/spell
- For fairies
  - if `count == -1` the condition is true if the player has the fairy in their *inventory*
  - else it is true if the player has that fairy type as first in the deck (always false for empty decks)
