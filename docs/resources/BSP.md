## BSP - Binary Space Partition
Binary Space Partition files are used to store information about scene geometry, their materials and the respective collision data. Therefore the file inherits a recursive structure which is encoded using the [[RWBS|RWBS]] format.

### Data format
Please see the [[RWBS|RWBS]] article.

### Common RWBS structure

* 1 [[World|RWWorld]]
    * 1 [[MaterialList|RWMaterialList]]
        * 1-N [[Material|RWMaterial]]
            * 1 [[Texture|RWTexture]]
    * 1 [[PlaneSection|RWPlaneSection]] __or__ [[AtomicSection|RWAtomicSection]]
        * 2 [[PlaneSection|RWPlaneSection]] __or__ [[AtomicSection|RWAtomicSection]]
        * _for_ [[AtomicSection|RWAtomicSection]]
            * 1 [[Extension|RWExtension]]
                * 1 [[BinMeshPLG|RWBinMeshPLG]]
                * 1 [[CollisionPLG|RWCollisionPLG]]
