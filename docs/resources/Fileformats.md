## File formats
As one can imagine, ZanZarah uses many different file formats for its resources.
This file should give an overview and link to a detail page for them all.

### [[RWBS|RWBS]]
Renderware Binary Stream files are not really actual files, but rather a general format structure which is use by [[DFF|DFF]] as well as [[BSP|BSP]] to store hierachical data. As the name states, this format was developed by Criterion Software for Renderware.

### [[DFF|DFF]]
DFF files are used to store meshes and are generally structured by the [[RWBS|RWBS]] system. They contain geometry, materials, collision data, skinning and bone data. They do not contain most of the animation data and no texture data. This format was developed by Criterion Software for Renderware.

### [[BSP|BSP]]
BSP (Binary Space Partition) are used to store different world geometry and collision data. They use the [[RWBS|RWBS]] format. Like [[DFF|DFF]] files they do not contain texture data. This format was developed by Criterion Software for Renderware.

### [[SKA|SKA]]
SKA (Skeletal Animation) files are used to store model animations. This format was like the [[RWBS|RWBS]] file formats developed by Criterion Software for Renderware but they do __not__ follow the [[RWBS|RWBS]] file structure.

### [[ED|ED]]
ED (Effect description) files are used to describe various effects. This format was developed by Funatics Entertainment for ZanZarah.

### [[FBS|FBS]]
FBS files are used to store various numeric and/or textual data about various aspects of the gameplay. They store information about the texts displayed in the game, fairy, spell, item and NPC information. They are the biggest source for [[Scripts|Script]]. This format was developed by Funatics Entertainment for ZanZarah.

### [[AED|AED]]
AED (actorex description) files are used to combine the body mesh files with the wing mesh files and the animation files for both of them. The format was developed by Funatics Entertainment for ZanZarah. 

### [[SCN|SCN]]
SCN (scene) files are used to describe a scene. This does include a reference to the [[BSP|BSP]] file but also contains various other informations like models placed in the world, triggers, sound or graphical effects, etc.

### [[DAT|DAT]]
DAT (data) files are used to store a state of the game, so the player does not have to play all over again. Shocking, isn't it?

### CFG
Unfortunately there exists three different CFG formats which all are incompatible to each other:

| Link | Files | Description |
|:----:|-------|-------------|
| [[ [x] |CFG_Game]] | Configs/game.cfg | This file stores the game settings including input bindings |
| [[ [x] |CFG_Map]]  | System/map.cfg   | This file stores various map markers |
| [[ [x] |CFG_Vars]] | System/ai.cfg <br/> System/net.cfg <br/> System/wizform.cfg | These files store numeric variables, propably used to test and tweak the game during development |

### [[RAW|CFG_Map#IngameDisplay]]
There exists only one file with the extension RAW, it stores which pixel of the map texture correspond to the different world sections.
