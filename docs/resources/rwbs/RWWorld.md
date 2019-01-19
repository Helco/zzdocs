## RWWorld (0x000B)

The RWWorld section stores header information for the world geometry and is the root section of [[BSP files|BSP]]. The format was described by [kabbi](https://github.com/kabbi/zanzarah-tools/blob/master/bsp-parser.coffee#L101).

## Structure format

| Size | Type | Description |
|------|------|-------------|
|  4b  | bool | _rootIsWorldSector_
| 12b  |Vector| _invWorldOrigin_
|  4b  |float | _ambient_
|  4b  |float | _specular_
|  4b  |float | _diffuse_
|  4b  | uint | total count of triangles
|  4b  | uint | total count of plane sectors
|  4b  | uint | total count of world sectors
|  4b  | uint | _colSectorSize_
|  4b  | enum | _format_ (see below)

### _format_ enum 
| Name            | Value    |
|-----------------|----------|
| Tristrip        |0x00000001|
| Positions       |0x00000002|
| Textured        |0x00000004|
| Prelit          |0x00000008|
| Normals         |0x00000010|
| Light           |0x00000020|
|ModulateMaterialColor|0x00000040|
| Textured2       |0x00000080|
| Native          |0x01000000|
| NativeInstance  |0x02000000|
| SectorsOverlap  |0x40000000|

## Possible child sections

* [[RWMaterialList|RWMaterialList]]
* [[RWPlaneSection|RWPlaneSection]]
* [[RWAtomicSection|RWAtomicSection]]
* [[RWExtension|RWExtension]]
