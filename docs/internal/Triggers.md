# Trigger behaviors

This page lists trigger types and describes them in a bit more detail.

## Doorway

Doorway triggers have three parameters:

1. The own doorway id
2. The doorway id in the target scene
3. The target scene id

## SingleplayerStartpoint

The name of the SingleplayerStartpoint triggers are propably deprecated, as [Doorway](#doorway) took their place. Nevertheless these triggers appear in each
overworld scene and in many duel scenes. In duel scenes their meaning is yet to be known (propably identical to [MultiplayerStartpoint](#multiplayerstartpoint)),
in overworld scenes however describes this trigger where to place the Amy if she was teleported by the console.

## NpcAttackPosition

This trigger is mostly used for wild fairies to attack the player, but it is also used for a friendly fairy warning about wild ones and an elf wanting a fight.
These are the parameters:

1. The [NPC UID](../resources/FBS/fb0x05.md) to use, often just the dummy UID for wild fairies. The actual scripts are [generated on runtime](./Scripts.md#default-scripts).
2. __unknown__ parameter (either 0, 1, 2, 3 or 50), seems to describe the condition on which the trigger is enabled
    - 0 or 2 uses the percentage in ii3
3. The chance percentage whether the fairy does actually attack
4. An index to an internal list of fairies which may attack you at this specific position (see below).

| Idx | Fairies                    |
|:---:|----------------------------|
|  0  | Worgot, Blumella           |
|  1  | Corgot, Lana               |
|  2  | Tinefol, Viteria, Silia    |
|  3  | Pfoe, Tinefol              |
|  4  | Abery, Corgot              |
|  5  | Worgot, Abnobery           |
|  6  | Abery, Silia               |
|  7  | Cera                       |
|  8  | Goop, Cera                 |
|  9  | Goop, Tadana               |
| 10  | 2x Tadana, Amnis, Ceramnis |
| 11  | Vesbat                     |
| 12  | Jumjum, Vesbat             |
| 13  | Gremor, Stobat             |
| 14  | Grem, Jumjum               |
| 15  | Mencre, Mensec             |
| 16  | Mencre, Mentaur            |
| 17  | Mencre, Mentaur            |
| 18  | 2x Beltaur, Mencre         |
| 19  | Airia, Luria               |
| 20  | Gorael, Sirael             |
| 21  | Sirella, Sirael            |
| 22  | Dracwin                    |
| 23  | 2x Pix, Ferix              |
| 24  | Feez, Greez                |
| 25  | Greezloc, Glacess          |
| 26  | Rasrow, Skelbo             |
| 27  | Rasrow, Skelbo             |
| 28  | Rasrow, Akritar, Manox     |
| 29  | Manox, Turnox, Violectra   |
| 30  | Minari                     |
| 31  | Minari                     |
| 32  | Minari, Megari, Violectra  |
| 33  | 2x Lighane, Driane, Darbue |

## CameraPosition

CameraPosition triggers are used to set the camera view via scripts. For this the [```setCamera```](./script commands/setCamera.md) command is used.
The only parameter of this trigger is the Id of this CameraPosition.

## Waypoints

There are two types of waypoints: regular waypoints and animal waypoints. As the name might tell, regular waypoints are used by NPCs while animal waypoints are used by animals.

Waypoints are connected by a set of rules:
* The trigger type is the same (no Waypoint is connected to an AnimalWaypoint)
* Their group parameter (*ii2*) is the same
* Their distance from each other is at max 7 units

The first parameter seems to be some kind of Id, most likely to be used in [[Scripts]].
The third parameter (*ii3*) is not null if it is selected as a target for a NPC.

## Animal

Animals are non-interactive creatures wandering around the world of ZanZarah. *ii1* holds the animal type, while *ii2* and
*ii3* are animal-specific parameters. See [[Animals]] for detailed information.

## Platform

Platform is used by [CreatePlatforms](#createplatforms-createitems) trigger to state where the platforms should appear and how they should move.
As model there is always ```g_plt00h``` used, *ii1* states the Behavior which is connected to the model.

| Value |     Behavior     | Description |
|:-----:|-------------------|-------------|
|   0   | MagicBridgeStatic | as the name states, platforms with this Behavior do not move |
|   1   | MagicBridge0      | unused |
|   2   | MagicBridge1      |  |
|   3   | MagicBridge2      | |

## CreatePlatforms CreateItems

These trigger create on player collision either platforms or items, their respective triggers ([Platform](#platform) and [Item](#item)) describe the position.
The effect used at trigger position is unknown yet, but for each platform/item the effect 4022 is used. If the game finds an *EventCamera* trigger, the view switches to it.
The platforms/items appear after 1 second the player activated the trigger in a 0.3 second interval (so the first platform/item takes 1.3 seconds). The order they appear
in is reverse to the order they are saved in the scene.

## Item
Item is used by [CreateItems](#createplatforms-createitems) trigger to state where and which items should appear. *ii1* is the id of the item. For coins and crystals,
the Behavior *GenBehavior_EFF0* is used, for all other items *GenBehavior*.
