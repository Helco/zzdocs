## General information

RWBS stands for RenderWare Binary Stream, this format is used for saving models (.dff) and worlds (.bsp) in ZanZarah. It is comprised by a hierachical structure of sections which either store binary data or other sections, so a common structure is:
* [Header]
     * RWStruct
     * [some Sections]
     * RWExtension
        * [some plugin section]
        * [some plugin section]

Thanks to the [GTA Modding Community](http://www.gtamodding.com) the format of many sections are known, some other are also more or less understood and described by [kabbi](https://github.com/kabbi). Unfortunately not all sections used in ZanZarah are decrypted yet :(

## Header format

| Size | Type | Description |
|------|------|-------------|
| 4b   | uint | section identifier
| 4b   | uint | section size, including child sections or data
| 4b   | uint | RenderWare version ID

## Section types used in ZanZarah

### List sections
* [[RWAtomic|RWAtomic]]
* [[RWAtomicSection|RWAtomicSection]]
* [[RWClump|RWClump]]
* [[RWExtension|RWExtension]]
* [[RWFrameList|RWFrameList]]
* [[RWGeometry|RWGeometry]]
* [[RWGeometryList|RWGeometryList]]
* [[RWMaterial|RWMaterial]]
* [[RWMaterialList|RWMaterialList]]
* [[RWPlaneSection|RWPlaneSection]]
* [[RWTexture|RWTexture]]
* [[RWWorld|RWWorld]]

### Data sections
* [[RWStruct|RWStruct]]
* [[RWString|RWString]]
* [[RWMorphPLG|RWMorphPLG]]
* [[RWSkinPLG|RWSkinPLG]]
* [[RWBinMeshPLG|RWBinMeshPLG]]
* [[RWAnimationPLG|RWAnimationPLG]]
* [[RWCollisionPLG|RWCollisionPLG]]
