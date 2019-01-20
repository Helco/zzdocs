# Basic information

The scene format contains all gameplay-specific informations about a world the player might travel. This also includes all duel arenas where the player is controlling a fairy instead of Amy. <br/>
This does not include any form of geometry, which would be stored in [BSP](../BSP) and [DFF](../DFF) files.

## General format

* The scene format consists of several sections each of which may only occur once in the file and each of which has its own binary format.
* Each sections starts with a section name as a *zstring* and its size is determined by its content.
* A section name is always contained in brackets ```[...]```
* The first section name to occur is ```Scenefile``` which does not have any further content.
* The last section name is ```EOS``` which also does not have any further content.
* Many sections contain an structure array whose count is the first unsigned 32bit integer in the section content.
* The following sections may occur:

## Sections

|             Link             |      Name(s)      | Description |
|:----------------------------:|:-----------------:|-------------|
| [ [x] ](/internal/ZZVersion) | Version           | information about build version, date/time, author, release country...|
| [ [x] ](SCN_Misc)            | Misc              | __mostly unknown__ information about the scene in general |
| [ [x] ](SCN_WaypointSystem)  | WaypointSystem    | __mostly unknown__ information about the waypoints |
| [ [x] ](SCN_Dataset)         | Dataset           | various gameplay information like scene id or name |
| -/-                          | SceneOrigin       | A vector to the middle of the world |
| [ [x] ](SCN_Backdrop)        | Backdrop          | A specifier about the background of the scene |
| [ [x] ](SCN_Light)           | Lights            | A collection of light information |
| [ [x] ](SCN_FOModel) | FOModels <br/> FOModels_v2 <br/> FOModels_v3 <br/> FOModels_v4 | A collection of optional models |
| [ [x] ](SCN_Model) | Models <br/> Models_v2 <br/> Models_v3 <br/> Models_v4 | A collection of important models |
| [ [x] ](SCN_DynamicModel)    | DynamicModels     | A collection of apparence-changing models |
| [ [x] ](SCN_Trigger)         | Triggers          | A collection of triggers |
| [ [x] ](SCN_Sample) | Samples <br/> 2DSamples_v2 | A collection of 2D samples |
| [ [x] ](SCN_3DSample)        | 3DSamples_v2      | A collection of 3D samples |
| [ [x] ](SCN_Effect) | Effects <br/> Effects_v2 | A collection of effects |
| [ [x] ](SCN_VertexModifier)  | VertexModifiers   | __mostly unknown__ collection of vertex modifiers |
| [ [x] ](SCN_TextureProperty) | TextureProperties | Footsteps applicable to certain textures |
| [ [x] ](SCN_Behavior)        | Behaviors         | collection of Behaviors tied to models |
| [ [x] ](SCN_Scene)           | Scene             | __completly unknown__ collection about scene items |
| -/-                          | SoundProvider     | An unused specifier (32bit uint) about some kind of sound settings |
| [ [x] ](SCN_AmbientSound)    | AmbientSound      | A specifier about the ambient sounds |
| [ [x] ](SCN_Music)           | Music             | A specifier about the music |
