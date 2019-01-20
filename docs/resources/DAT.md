# DAT
Savegames stored in DAT files consist of various sections. The main parts of it are the GameState and the Inventory. Also the [GlobalVars](../internal/GlobalVars.md) are saved here.

## Data format

| Size | Type |  Section  | Description |
|------|------|-----------|-------------|
|      |[ZZVersion](../internal/ZZVersion.md)| Header | This version has to be compatible with the internal savegame ZZVersion structure |
|      |zstring| Header   | The players name |
|  4B  | uint | Location  | The structure size of the location block (always 8) |
|  4B  | uint | Location  | Scene ID    |
|  4B  | uint | Location  | Entrance Trigger ID |
|  4B  | uint | GameState | Count of scenes for which are GameState Modifier saved |
|      |[GameStateScene[]](#gamestatescene)| GameState | The scene data |
|  4B  | uint | Inventory | The count of cards in the players inventory |
|      |[InventoryCard[]](#inventorycard)| Inventory | The inventory card data |
|  4B  | uint | PixieCount | The current amount of pixies hold on by the player |
|  4B  | uint | PixieCount | The total amount of pixies catched by the player |
|  4B  | uint | GlobalVars | The count of global variables (always 49) |
|      |[GlobalVar[]](../internal/GlobalVars.md#data-format)| GlobalVars | The global variables |
|  4B  | uint | SwitchGameMinTries | The minimal count of tries for the [[switch game|SwitchGame]] |

## GameStateScene

| Size | Type | Description |
|------|------|-------------|
|      |zstring| The scene name |
|  4B  | uint | The GameState modifier count for this scene |
|      |[GameStateMod](#gamestatemod)[]| The GameState modifiers |

## GameStateMod

| Size | Type | Description |
|------|------|-------------|
|  4B  | enum | The type of the GameStateMod (see [GameStateModType](#gamestatemodtype)) |
|      |      | [GameStateModType](#gamestatemodtype) specific data |

## GameStateModType

| Value | Description |
|:-----:|-------------|
|   0   | [DisableAttackTrigger](#gsmoddisableattacktrigger) |
|   1   | [RemoveItem](#gsmodremoveitem) |
|   2   | [ChangeNpcState](#gsmodchangenpcstate) |
|   3   | [DisableTrigger](#gsmoddisabletrigger) |
|   4   | [RemoveSimpleModel](#gsmodremovesimplemodel) |
|   5   | [SetTrigger](#gsmodsettrigger) |
|   6   | [SetNpcModifier](#gsmodsetnpcmodifier) |

## GSModDisableAttackTrigger

| Size | Type | Description |
|------|------|-------------|
|  4B  | uint | *triggerId*   |

## GSModRemoveItem

| Size | Type | Description |
|------|------|-------------|
|  4B  | uint | *modelId*     |

## GSModChangeNpcState

| Size | Type | Description |
|------|------|-------------|
|  4B  | uint | *triggerId* |
|  4B  | uint | *databaseId* - The [fb0x05](./FBS/fb0x05.md) UID of the NPC to change into |

## GSModDisableTrigger

| Size | Type | Description |
|------|------|-------------|
|  4B  | uint | *triggerId* |

## GSModRemoveSimpleModel

| Size | Type | Description |
|------|------|-------------|
|  4B  | uint | *modelId*   |

## GSModSetTrigger

| Size | Type |  Description  |
|------|------|---------------|
|  4B  | uint | *triggerId*   |
|  4B  | uint | *ii1* - The trigger parameters |
|  4B  | uint | *ii2* - If one of these are -1 |
|  4B  | uint | *ii3* - this said parameter is not set |
|  4B  | uint | *ii4*         |

## GSModSetNpcModifier

| Size | Type | Description |
|------|------|-------------|
|  4B  | uint | *triggerId*   |
|  4B  | uint | *value* - Actually just sets the triggers ii2 param |

## InventoryCard

| Size | Type | Description |
|------|------|-------------|
|  4B  |[CardId](../internal/CardId.md)| The CardId, thus also encodes the type |
|  4B  | uint | *atIdx* - The index at which Zanzarah puts this card in the internal inventory list |
|  4B  | uint | *dbUID* - The database ID (so either [fb0x01](./FBS/fb0x01.md), [fb0x03](./FBS/fb0x03.md) or [fb0x04](./FBS/fb0x04.md)) of the card |
|  4B  | uint | *amount*    |
|  1B  | bool | *isUsed*    |
|      |      | InventoryCard-specific data |

## InventoryItem
Items do not have any extra information

## InventorySlot

| Size | Type | Description |
|------|------|-------------|
|  4B  | uint | *usageCount* - How many times this spell was used |
|  4B  | uint | *curMana*   |

## InventoryFairy

| Size | Type | Description |
|------|------|-------------|
|  4B  | uint | *changeCountLevel* - How many times this fairy leveled up |
|  4B  | uint | *level*     |
|  4B  | uint | **unknown** |
|  4B  | uint | **unknown** |
|  4B  | uint | *changeCountXP* - How many times this fairy got XP |
|  4B  | uint | *curXP*     |
| 12B  |[SpellReq](#spellreq)[4]| The current spell requirements |
| 16B  |uint[4]| The spell indices (in the inventory of the player) |
|  4B  | uint | The slot index in the players deck |
|  4B  | uint | *statusEffect* |
| 20B  |uint[5]| **unknown** |
|  4B  | uint | Current health points |
|      |zstring| *name*     |

## SpellReq

| Size | Type | Description |
|------|------|-------------|
|  1B  | enum | *class1* - (see [Classes](../internal/Classes.md)) |
|  1B  | enum | *class2* - (see [Classes](../internal/Classes.md)) |
|  1B  | enum | *class3* - (see [Classes](../internal/Classes.md)) |
