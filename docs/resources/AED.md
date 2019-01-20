#  AED

ActorEx Description (AED) files are in Zanzarah mappings between body model, optional wings model and a set of animations per part. It is developed by Funatics, seen by the similar format for [scene files](./SCN/index.md).

## Data Format

- The first zstring in an AED file is ```[ActorExDescriptionFile]```
- After this there is a sequence of sections all started by a zstring containing the name in square brackets.
- Each section has his own data format.
- The end of the file is signaled by the section header ```[EOS]``` which does not have any other information.

## Sections

|       SectionName       |    Dataformat    |                                      Description                                      |
|:-----------------------:|------------------|---------------------------------------------------------------------------------------|
| ModelFilename_Body      | zstring          | The [[DFF]] file for the body                                                         |
| AnimationPoolID_Body    | int32            | An unused ID for the animation pool                                                   |
| AnimationFilename_Body  | zstring + enum   | A [[SKA]] in the body animation pool and its [AnimationType](#animationtype)          |
| ModelFilename_Wings     | zstring          | The [[DFF]] file for the (optional) wings                                             |
| AnimationPoolID_Wings   | int32            | An unused ID for the animation pool                                                   |
| AnimationFilename_Wings | zstring + enum   | A [[SKA]] in the wings animation pool and its [AnimationType](#animationtype)         |
| AttachWingsToBone       | int32            | The bone ID of the body to attach the wings root bone to                              |
| HeadBoneID              | int32            | The root head bone ID, usage yet to be known                                          |
| EffectBoneID            | int32            | The bone ID to attach a possible actor effect to                                      |

## AnimationType

| Value |       Name      |
|:-----:|-----------------|
|   0   | Idle0           |
|   1   | Jump            |
|   2   | Run             |
|   3   | RunForwardLeft  |
|   4   | RunForwardRight |
|   5   | Back            |
|   6   | Dance           |
|   7   | Fall            |
|   8   | Rotate          |
|   9   | Right           |
|  10   | Left            |
|  11   | Idle1           |
|  12   | Idle2           |
|  13   | Talk0           |
|  14   | Talk1           |
|  15   | Talk2           |
|  16   | Talk3           |
|  17   | Walk0           |
|  18   | Walk1           |
|  19   | Walk2           |
|  20   | SpecialIdle0    |
|  21   | SpecialIdle1    |
|  22   | SpecialIdle2    |
|  23   | FlyForward      |
|  24   | FlyBack         |
|  25   | FlyLeft         |
|  26   | FlyRight        |
|  27   | Loadup          |
|  28   | Hit             |
|  29   | Joy             |
|  30   | ThudGround      |
|  31   | UseFairyPipe    |
|  32   | UseSeaShel      |
|  33   | Smith           |
|  34   | Astonished      |
|  35   | Surprise0       |
|  36   | Surprise1       |
|  37   | Stop            |
|  38   | ThudGround2     |
|  39   | PixieFlounder   |
|  40   | JumpHigh        |
