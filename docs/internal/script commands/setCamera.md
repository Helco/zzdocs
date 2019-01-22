# setCamera

`setCamera` takes only a single numeric parameter, which determines where the camera should be located.
As this command is only allowed for [[scriptsystem implementation|Scripts#Implementations]] 1 and 3, therefore there is always a Npc to reference.

Its single-character version is `&`

| Value | Description |
|:-----:|-------------|
| 00XX  | at [[CameraPosition|Triggers#CameraPosition]] trigger XX (look at player) |
| 1000  | behind player (left top) |
| 1001  | behind player (left bottom) |
| 1002  | behind player (left center) |
| 1003  | behind player (right top) |
| 1004  | behind player (right bottom) |
| 1005  | behind player (right center) |
| 1006  | behind player (directly) |
| 1007  | front of player (directly) |
| 2000  | behind Npc (left top) |
| 2001  | behind Npc (left bottom) |
| 2002  | behind Npc (left center) |
| 2003  | behind Npc (right top) |
| 2004  | behind Npc (right bottom) |
| 2005  | behind Npc (right center) |
| 2100  | follow Npc |
| 30XX  | at [[CameraPosition|Triggers#CameraPosition]] trigger XX (use trigger direction) |
| 4000  | look at Npc |
| 50XX  | at [[CameraPosition|Triggers#CameraPosition]] trigger XX (look at Npc)