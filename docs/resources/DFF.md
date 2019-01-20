# DFF
DFF files are used to store information about models, static or actors. Therefore they not only contain geometry and material information but also information about animations, bones and skinning. They are structured in the [RWBS](./RWBS/index.md) format.

## Data format
Please see the [RWBS](./RWBS/index.md) articles.

## Common structure

* 1 [Clump](./RWBS/RWClump.md)
    * 1 [FrameList](./RWBS/RWFrameList.md)
        * 1-n [Extension](./RWBS/RWExtension.md)
            * 0-1 [AnimationPLG](./RWBS/RWAnimationPLG.md)
    * 1 [GeometryList](./RWBS/RWGeometryList.md)
        * 1 [Geometry](./RWBS/RWGeometry.md)
            * 1 [MaterialList](./RWBS/RWMaterialList.md)
                * 1-n [Material](./RWBS/RWMaterial.md)
                    * 1 [Texture](./RWBS/RWTexture.md)
            * 1 [Extension](./RWBS/RWExtension.md)
                * 1 [BinMeshPLG](./RWBS/RWBinMeshPLG.md)
                * 1 [MorphPLG](./RWBS/RWMorphPLG.md)
    * 1 [Atomic](./RWBS/RWAtomic.md)
        * 1 [Extension](./RWBS/RWExtension.md)
            * 1 [SkinPLG](./RWBS/RWSkinPLG.md)
    * 1 [Extension](./RWBS/RWExtension.md)
        * 1 [AnimationPLG](./RWBS/RWAnimationPLG.md)
