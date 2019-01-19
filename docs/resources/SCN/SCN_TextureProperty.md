## Scene section "TextureProperties"

This section describes the kind of footstep applicable to this texture.

### Format

The section is an array of TextureProperty structures.

| Size | Type  | Description |
|------|-------|-------------|
|      |zstring| texture filename |
|  4B  | enum  | see [[FootstepType|#FootstepType]]|

#### FootstepType

Every footstep has four different sound files to play (all in the directory AUDIO/SFX/FOOTSTEPS, except for _s013 which can be found in AUDIO/SFX/SPECIALS)

| Value |       Description      | File1 | File2 | File3 | File4 |
|:-----:|------------------------|-------|-------|-------|-------|
|   0   | Wood/Stone?            | _f004 | _f005 | _f006 | _f007 |
|   1   | Snow                   | _f016 | _f017 | _f018 | _f019 |
|   2   | Metal                  | _f012 | _f013 | _f014 | _f015 |
|   3   | Wood                   | _f008 | _f009 | _f010 | _f011 |
|   4   | Grass                  | _f000 | _f001 | _f002 | _f003 |
|   5   | Mud                    | _f020 | _f021 | _f022 | _f023 |
|   6   | Marmor                 | _f024 | _f025 | _f026 | _f027 |
|   7   | Outdoor roads/pathways | _f028 | _f029 | _f030 | _f031 | 
|   8   | Stone in the mountains | _f032 | _f033 | _f034 | _f035 |
|   9   | Snow (edge to stone)   | _f036 | _f037 | _f038 | _f039 |
|  10   | Metal (lightly damped) | _f040 | _f041 | _f042 | _f043 |
|  11   | Wood, footbridges      | _f044 | _f045 | _f046 | _f047 |
|  12   | Grass __unused__       | _f048 | _f049 | _f050 | _f051 |
|  13   | Mud __unused__         | _f052 | _f053 | _f054 | _f055 |
|  14   | Damped wood or carpet  | _f056 | _f057 | _f058 | _f059 |
|  15   | Swamp soil             | _f060 | _f061 | _f062 | _f063 |
|  16   | Creaky wood (stairs?)  | _f064 | _f065 | _f066 | _f067 |
|  17   | Carpet                 | _f068 | _f069 | _f070 | _f071 |
|  18   | Hard soil              | _f076 | _f077 | _f078 | _f079 |
|  19   | Wood __unused__        | _f072 | _f073 | _f074 | _f075 |
|  N/A  | Water                  | _s013 | _s013 | _s013 | _s013 |

Unused in this list are _f080, _f081, _f082 and _f083 which are loud splash noises from when Amy jumps into water.
