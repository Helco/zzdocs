## CardId

### General information
The CardId is used by ZanZarah to have a (or another) unique identifier to address items, fairies and spells. The CardId can be split up in three distinct numbers which hold information:

| Bits  |                     Description                     |
|-------|-----------------------------------------------------|
|  0-7  | Unknown field, propably a validation (set to 0xff)  |
|  8-15 | Type of the CardID (0 = Item, 1 = Spell, 2 = Fairy) |
| 16-31 | ID of entity                                        |
