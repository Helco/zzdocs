# Model behaviors

This page lists certain special model behavior types and describes them in a bit more detail.

## Locked doors

This affects the following behaviors: _DoorGold, DoorSilver, CityDoorLock, DoorCopper, DoorBronze, DoorIron, DoorGlass, DoorRed, DoorYellow, DoorBlue_.

These are all doors, which are unlocked by standing near (< 3.0) the door whilst having the right item in the inventory.
The mapping which item unlocks what is hardcoded:

| Door behavior | CardId | Item name (maybe not be accurate) |
|---------------|:------:|-----------------------------------|
| DoorGold      |   21   | Catacomb key                      |
| DoorSilver    |   22   | Heavy iron key                    |
| CityDoorLock  |   22   | Heavy iron key                    |
| DoorCopper    |   23   | Key of the pixie guard            |
| DoorBronze    |   24   | Rufus' key                        |
| DoorIron      |   25   | Dwarf factory key                 |
| DoorGlass     |   27   | Towns hall key                    |
| DoorRed       |   71   | Red bone key                      |
| DoorYellow    |   72   | Green bone key                    |
| DoorBlue      |   73   | Blue bone key                     |

## Collectable

The collectable behavior is essentially an item, because the item id the player gets is determined by the model filename (itm###.dff), not all items can be collected by an item bag/catching sphere. <br/>
Additionally there are three special item models (itmxxx.dff / itmyyy.dff / itmzzz.dff) which have hardcoded random items they can give up on picking up:

### itmxxx
| Chance | Item                  |
|:------:|-----------------------|
|  40%   | 3-9 Gold              |
|  30%   | Small healing potion  |
|  15%   | Normal healing potion |
|  10%   | Big healing potion    |
|   5%   | Healing herb          |

### itmyyy
| Chance | Item                  |
|:------:|-----------------------|
|  40%   | Small healing potion  |
|  20%   | Garlic                |
|  10%   | Normal healing potion |
|  10%   | Big healing potion    |
|  10%   | Healing herb          |
|  10%   | Mana potion           |

### itmzzz
| Chance | Item               |
|:------:|--------------------|
|  33%   | Big healing potion |
|  16%   | Healing herb       |
|  16%   | Mana potion        |
|  16%   | Garlic             |
|  16%   | Golden carrot      |
||<sub>Of course the values are 33,3...% and 16,6...%</sub>
