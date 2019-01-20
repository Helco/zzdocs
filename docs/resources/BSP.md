# BSP
Binary Space Partition files are used to store information about scene geometry, their materials and the respective collision data. Therefore the file inherits a recursive structure which is encoded using the [RWBS](./RWBS/index.md) format.

## Data format
Please see the [RWBS](./RWBS/index.md) articles.

## Common RWBS structure

* 1 [World](./RWBS/RWWorld.md)
    * 1 [MaterialList](./RWBS/RWMaterialList.md)
        * 1-N [Material](./RWBS/RWMaterial.md)
            * 1 [Texture](./RWBS/RWTexture.md)
    * 1 [PlaneSection](./RWBS/RWPlaneSection.md) __or__ [AtomicSection](./RWBS/RWAtomicSection.md)
        * 2 [PlaneSection](./RWBS/RWPlaneSection.md) __or__ [AtomicSection](./RWBS/RWAtomicSection.md)
        * _for_ [AtomicSection](./RWBS/RWAtomicSection.md)
            * 1 [Extension](./RWBS/RWExtension.md)
                * 1 [BinMeshPLG](./RWBS/RWBinMeshPLG.md)
                * 1 [CollisionPLG](./RWBS/RWCollisionPLG.md)
