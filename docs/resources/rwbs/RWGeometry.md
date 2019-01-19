## RWGeometry (0x000F)

This section stores geometric data of models.

It can be seen as child of [[RWGeometryList|RWGeometryList]] sections.

## Structure format

| Size | Type | Description |
|------|------|-------------|
|  4b  | enum | _format_ (see below)
|  4b  | uint | count of triangles
|  4b  | uint | count of vertices
|  4b  | uint | count of morph targets (should always be 1)
|  4b  |float | _ambient_ <br>__optional__ only after 0x33000
|  4b  |float | _specular_ <br>__optional__ only after 0x33000
|  4b  |float | _diffuse_ <br>__optional__ only after 0x33000

__optional__  only if  format does not contain Native :

| Size | Type | Description |
|------|------|-------------|
|  4b  |uint[]| _prelitcolor_ <br>__optional__ only if format contains Prelit
|      |TexCoord[,]| _texCoords_ (see below)
|      |GTriangle[]| _triangles_
|      |MorphTarget[]|__not optional__

### MorphTarget
| Size | Type | Description |
|------|------|-------------|
| 12b  |Vector| Center of bounding sphere
|  4b  |float | Radius of bounding sphere
|  4b  | bool | _hasVertices_
|  4b  | bool | _hasNormals_
|      |Vector[]| __vertices__
|      |Vector[]| __normals__ (1 per vertex)

### TexCoord
| Size | Type | Description |
|------|------|-------------|
|  4b  |float | _u_
|  4b  |float | _v_

### GTriangle
| Size | Type | Description |
|------|------|-------------|
|  2b  | uint | _v2_
|  2b  | uint | _v3_
|  2b  | uint | _m_
|  2b  | uint | _v1_

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

`Bits 16-23 (mask 0x00FF0000) in the format description give the number of texture coordinate sets (numTexSets).` - [gtamodding](http://www.gtamodding.com/wiki/RpGeometry) If this value is 0, _format_ decides over the number of texture coordinate sets.

## Possible child sections

* [[RWMaterialList|RWMaterialList]]
* [[RWExtension|RWExtension]]
    * [[RWBinMeshPLG|RWBinMeshPLG]]
    * [[RWMorphPLG|RWMorphPLG]]
