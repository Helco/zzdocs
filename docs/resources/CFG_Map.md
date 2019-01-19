## CFG for map.CFG

map.cfg stores various map markers, unfortunately there exists another internal but similar map marker list. The relationship between those two has yet to be analysed.

### Format

| Size | Type | Description          |
|------|------|----------------------|
|  4B  | uint | count of map markers |
|      |MapMarker[]| the array of [[map markers|#MapMarker]] |

#### MapMarker

| Size | Type | Description |
|------|------|-------------|
|  4B  | int  | X position on the map |
|  4B  | int  | Y position on the map |
|  4B  | enum | section of the marker (see [[sections|#Section]]) |
|  4B  | uint | scene id of the marker |

#### Section

| Value |       Name      |
|:-----:|-----------------|
|   1   | FairyGarden     |
|   2   | EnchantedForest |
|   3   | MountainWorld   |
|   4   | DarkSwamp       |
|   5   | ShadowRealm     |
|   6   | RealmOfClouds   |
|   7   | London          |

### Ingame display

The color bitmap of the map displayed in the game is stored in *BITMAPS/MAP001T.BMP*, but the game shows sections only if the player has the respective item.
The information what pixels to draw is stored in *BITMAPS/MAP001M.RAW* which is an array of bytes with size 640*480, where each byte is a [[section|#Section]] number.

The map markers stored in map.cfg are not always shown but the scene name is shown upon hovering the mouse near a marker (in a circle with radius 50px).
