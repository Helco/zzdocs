## DFF
DFF files are used to store information about models, static or actors. Therefore they not only contain geometry and material information but also information about animations, bones and skinning. They are structured in the [[RWBS|RWBS]] format.

### Data format
Please see the [[RWBS|RWBS]] article.

### Skeleton bone hierachy
I have implemented two different methods of finding the bone hierachy, the first one was developed by [kabbi](https://github.com/kabbi/zanzarah-tools/), the other one by me (Helco):

#### Kabbi's method
This method seems to work for every single actor of ZanZarah except those (two) which do not have [[AnimationPLG|RWAnimationPLG]] sections in their [[FrameList|RWFrameList]] (a020sa20 and a021sa20).

- Every bone has a unique ID beside its index in the [[SkinPLG|RWSkinPLG]] sections
- There exists at least one [[AnimationPLG|RWAnimationPLG]] for every bone ID
- The first frame in the [[FrameList|RWFrameList]] with a corresponding [[AnimationPLG|RWAnimationPLG]] carries the bone matrix (without parents?).

#### Helco's method
With the help of Kabbi's method and under the precondition that there is no node which doesn't have children nor siblings, the following pattern about the bone flags can be found:

| Value | Has at least one child | Has at least one other sibling |
|:-----:|:----------------------:|:------------------------------:|
|   8   |          true          |              false             |
|   9   |          false         |              false             |
|  10   |          true          |              true              |

This works for every actor in ZanZarah, looking at the data 11 could be the value for "No child but another sibling", but this value is never used in the ZanZarah files.

### Common structure

* 1 [[Clump|RWClump]]
    * 1 [[FrameList|RWFrameList]]
        * 1-n [[Extension|RWExtension]]
            * 0-1 [[AnimationPLG|RWAnimationPLG]]
    * 1 [[GeometryList|RWGeometryList]]
        * 1 [[Geometry|RWGeometry]]
            * 1 [[MaterialList|RWMaterialList]]
                * 1-n [[Material|RWMaterial]]
                    * 1 [[Texture|RWTexture]]
            * 1 [[Extension|RWExtension]]
                * 1 [[BinMeshPLG|RWBinMeshPLG]]
                * 1 [[MorphPLG|RWMorphPLG]]
    * 1 [[Atomic|RWAtomic]]
        * 1 [[Extension|RWExtension]]
            * 1 [[SkinPLG|RWSkinPLG]]
    * 1 [[Extension|RWExtension]]
        * 1 [[AnimationPLG|RWAnimationPLG]]
