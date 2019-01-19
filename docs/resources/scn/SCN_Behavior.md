## Scene section "Behaviors"

This section describes how the game should process certain models.

### Format

| Size | Type  | Description |
|------|-------|-------------|
|  4B  | enum  | [[Behavior type|#BehaviorType]] |
|  4B  | uint  | model idx this Behavior should be connected to |

#### BehaviorType

The game groups certain Behavior types to one main functionality and then splits up accordingly.

| Value |        Name       | Description |
|:-----:|-------------------|-------------|
|  800  | Cloud             | unused |
|  900  | SmpleDoorLeft     | |
|  901  | SimpleDoorRight   | |
|  902  | MetalDoorLeft     | unused |
|  903  | CityDoorDown      | unused |
|  904  | CityDoorUp        | |
|  910  | DoorGold          | [[see details|Behaviors#locked-doors]] |
|  911  | DoorSilver        | [[see details|Behaviors#locked-doors]] |
|  912  | DoorCopper        | [[see details|Behaviors#locked-doors]] |
|  913  | DoorBronze        | [[see details|Behaviors#locked-doors]] |
|  914  | DoorIron          | [[see details|Behaviors#locked-doors]] |
|  915  | DoorPlating       | unused |
|  916  | DoorGlass         | [[see details|Behaviors#locked-doors]] |
|  917  | DoorWithLock      | unused |
|  918  | CityDoorLock      | [[see details|Behaviors#locked-doors]] |
|  919  | LockedMetalDoor   | |
|  920  | LockedWoodenDoor  | unused |
|  921  | DoorRed           | [[see details|Behaviors#locked-doors]] |
|  922  | DoorYellow        | [[see details|Behaviors#locked-doors]] |
|  923  | DoorBlue          | [[see details|Behaviors#locked-doors]] |
| 1000  | Collectable       | [[see details|Behaviors#Collectable]] |
| 1001  | Collectable_EFF0  | |
| 1002  | Collectable_EFF1  | unused |
| 1010  | *GenCollectable*    | only generated at runtime, not an original name |
| 1011  | *GenCollectable_EFF0* | only generated at runtime (used for coins/crystals), not an original name |
| 1012  | *GenCollectable_EFF1* | only generated at runtime (propably unused), not an original name |
| 1100  | Lock              | |
| 1500  | BlockerStone      | |
| 1501  | BlockerPlant      | unused |
| 1502  | MagicBridgeStatic | |
| 1503  | IronGate          | unused |
| 1504  | MagicBridge0      | |
| 1505  | MagicBridge1      | |
| 1506  | MagicBridge2      | |
| 2000  | LookAtPlayer      | unused |
| 2001  | Swing             | |
| 2002  | FlameAnimation    | unused |
| 2003  | SkyMovement       | |
| 2004  | River2            | |
| 2005  | River3            | |
| 2006  | River4            | unused |
| 2007  | WaterAnimation    | unused |
| 2008  | YRotate1          | |
| 2009  | YRotate2          | |
| 2010  | Bird              | unused |
| 2011  | TextureWobble     | unused |
| 2012  | SimpleCorona      | unused |
| 2013  | BirdCircle        | unused |
| 2014  | ZRotate1          | |
| 2015  | ZRotate2          | |
| 2016  | XRotate1          | |
| 2017  | XRotate2          | |
| 2018  | River5            | unused |
| 2019  | River6            | unused |
| 2020  | River7            | unused |
| 2021  | River8            | unused |
| 2100  | FlyAwayVisible    | unused |
| 2101  | FlyAwayInvisible  | unused |
| 2102  | FlyAwayStraight   | unused |
