# Dataset

This section stores various gameplay information about the current scene. Unfortunately the functionality of many flags are not known to this date.

## Format

| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | size of inner data, either 32 or 36 |
|  4B  | uint  | scene id |
|  4B  | enum  | [scene type](#scene-type) |
|  4B  | uint  | a [string](../FBS/fb0x02.md) UID containing the name of the scene |
|  1B  | uint  | __unknown flag__ |
|  1B  | uint  | __unknown flag__ |
|  2B  |       | _structural padding_ |
|  4B  | bool  | __unknown__ |
|  1B  | bool  | can the player change his deck here |
|  3B  |       | _structural padding_ |
|  4B  | uint  | __unknown__ always 0 |
|  4B  | bool  | __unknown__ |
|  4B  | bool  | _if size == 36_ __unknown__ |
|      |zstring| always empty |
|      |zstring| always empty |

### Scene type

| Value |    Description    |
|:-----:|-------------------|
|   0   | Overworld scene   |
|   1   | Arena             |
|   2   | Multiplayer scene |
