# AmbientSoundMgr

The AmbientSoundMgr plays at random intervals 3D soundeffects near the player. The collection of sound files it uses is one of 17 hardcoded collections selected by the [[SCN_AmbientSound]] scene section. Also the interval it plays new sounds are hardcoded chances selected by the scene file.

## Behaviour

For each entry in the sound collection the AmbientSoundMgr has one emitter, even though it might not be playing. On each update (which happens for the AmbientSoundMgr only every 100ms) if some emitter is not playing, there is a random number generated between 1 and 100 (inclusive). If this number is smaller than the chanced declared by the collection a new sound may start. If multiple emitters are free a random emitter is chosen. It is placed randomly in a cube around the player with a side length of 20 units, but only on integer coordinates.

## Collections

| Value | Sounds | Description |
|:-----:|-------------------------------------|-------------|
|   0   | |
|   1   | |
|   2   | |
|   4   | |
|   5   | |
|   6   | |
|   7   | |
|   8   | |
|   9   | |
|  10   | |
|  11   | |
|  12   | |
|  14   | |
|  15   | |
|  16   | |
