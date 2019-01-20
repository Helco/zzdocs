# Triggers

This section describes areas in the scene and how the game shall use them.

## Format

The section is an array of Trigger structures.

| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | some kind of index |
|  4B  | enum  | [collider type](#collider-type) |
|  4B  | uint  | flag if direction should be normalized |
| 12B  | Vec3f | direction |
|  4B  | enum  | [trigger type](#trigger-type) |
|  4B  | uint  | trigger type specific parameter |
|  4B  | uint  | trigger type specific parameter |
|  4B  | uint  | trigger type specific parameter |
|  4B  | uint  | trigger type specific parameter |
|      |zstring| Mostly empty and unused string |
| 12B  | Vec3f | position |
| 12B  | Vec3f | _collider type == Box_ size |
|  4B  | float | _collider type == Sphere_ radius |

### Collider Type

| Value | Description |
|:-----:|-------------|
|   0   | Box         |
|   1   | Sphere      |
|   2   | Point       |

Note that internally, there are more collider types, but these are the ones used in the game.

### Trigger Type

| Value |        Name        | Description |
|:-----:|--------------------|-------------|
|   0   | Doorway            | used as entrance/exit of a scene, [see detail page](../../internal/Triggers.md#doorway) |
|   1   | SingleplayerStartpoint | [see detail page](../../internal/Triggers.md#singleplayerstartpoint) |
|   2   | MultiplayerStartpoint  |  |
|   3   | NpcStartpoint      |  |
|   4   | CameraPosition     | used by [scripts](../../internal/Scripts.md) to change the camera view, [see detail page](../../internal/Triggers.md#cameraposition) |
|   5   | Waypoint           | used for NPCs, [see detail page](../../internal/Triggers.md#waypoints) |
|   6   | StartDuel          | unused |
|   7   | LeaveDuel          | unused |
|   8   | NpcAttackPosition  | used mostly for wild fairies, [see detail page](../../internal/Triggers.md#npcattackposition) |
|   9   | FlyArea            | unused |
|  10   | KillPlayer         |  |
|  11   | SetCameraView      | unused |
|  12   | SavePoint          | unused |
|  13   | SwampMarker        |  |
|  14   | RiverMarker        |  |
|  15   | PlayVideo          | unused |
|  16   | _Elevator_         | in the executable it is actually called teleporter |
|  17   | GettingACard       | unused |
|  18   | Sign               |  |
|  19   | GettingPixie       | unused |
|  20   | UsingPipe          | unused |
|  21   | DancePlatform      | unused |
|  22   | LeaveDancePlatform | unused |
|  23   | RemoveStoneBlocker | unused |
|  24   | RemovePlantBlocker | unused |
|  25   | EventCamera        | this trigger is used by the exectuable to set the camera on certain events like removing stone/plant blockers, [CreatePlatforms](../../internal/Triggers.md#createplatforms-createitems), etc. |
|  26   | Platform           | [see detail page](../../internal/Triggers.md#platform) |
|  27   | CreatePlatforms    | [see detail page](../../internal/Triggers.md#createplatforms-createitems) |
|  28   | ShadowLight        |  |
|  29   | CreateItems        | [see detail page](../../internal/Triggers.md#createplatforms-createitems) |
|  30   | Item               | [see detail page](../../internal/Triggers.md#item) |
|  31   | Shrink             | unused |
|  32   | WizformMarker      | unused |
|  -/-  | RemoveLock         | this name is in the executable, but it messes up with the rest of the types |
|  33   | IndoorCamera       | unused |
|  34   | LensFlare          | unused |
|  35   | FogModifier        |  |
|  36   | OpenMagicWaypoints | unused |
|  37   | _RuneTarget_       | not an original name, used to place Amy after teleporting with rune, *ii1* either 0 or 1000, meaning unknown |
|  38   | Unused38           | no name present in the executable |
|  39   | Animal             | [see detail page](../../internal/Triggers.md#animal) |
|  40   | AnimalWaypoint     | [see detail page](../../internal/Triggers.md#waypoints) |
|  41   | SceneOpening       | unused |
|  42   | CollectionWizform  | used in London to place the unused fairies |
|  43   | ElementalLock      |  |
|  44   | ItemGenerator      |  |
|  45   | Escape             |  |
|  46   | Jumper             | used to place air jump fields, effect number yet to be known |
|  47   | RefreshMana        | unused |
|  48   | StartSubgame       | unused |
|  49   | TemporaryNpc       |  |
|  50   | EffectBeam         |  |
|  51   | MultiplayerObserverPosition |  |
|  52   | MultiplayerHealingPool      |  |
|  53   | MultiplayerManaPool         |  |
|  54   | Ceiling            | used in arena scenes to limit flying height |
|  55   | HealAllWizforms    |  |
