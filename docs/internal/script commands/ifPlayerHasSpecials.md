# ifPlayerHasSpecials

`ifPlayerHasSpecials` is a [control flow command](#control-flow) that skips based on some special conditions that probably were built as-needed during development. It takes two numerical parameters:

1. The type of condition (see below)
2. Some argument

The short-form is `@`.

## Condition types

| Condition | Description |
|:---------:|:------------|
| 0 | Checks if player has at least 5 pixies. <br/> Then also **removes** five pixies! |
| 1 | Checks whether the player has a fairy in the deck <br/> `arg==0` for has not, `arg==1` for has |
| 2 | Checks whether the player has at least `arg` fairies |
| 3 | Checks whether the player has at least one fairy of element class `arg` |
