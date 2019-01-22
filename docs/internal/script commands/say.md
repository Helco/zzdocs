# say

The script command `say` is allowed when triggering NPCs and takes two parameters:

- A foreign key to a [dialog row](../../resources/FBS/fb0x06.md)
- A numeric flag I call _silent_

When executed the text in the [dialog row](../../resources/FBS/fb0x06.md) is displayed gradually at the bottom of the screen in a letterbox. The _silent_ flag does two things:

1. blinking symbol appears after the text has been displayed fully
2. a voice sample is played

The voice sample may come from the `Voice` column in the [dialog row](../../resources/FBS/fb0x06.md), but it isn't used in the original database. Alternatively the game appends at random a number between 1 and 3 to the model name and plays thereby choosen sample.

Its short form is `!`.
