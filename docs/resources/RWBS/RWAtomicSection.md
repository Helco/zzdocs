# RWAtomicSection (0x0009)

This section is used to define a piece of the world geometry, it is usually child of a [[RWPlaneSection]] and propagated through other [[RWPlaneSection]] to a [[RWWorld]] section.

The format of this section was decrypted by [kabbi](https://github.com/kabbi/zanzarah-tools/blob/master/bsp-parser.coffee#L180).

## Structure format

| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | _materialIdBase_
|  4b  | uint | _triangleCount_
|  4b  | uint | _vertexCount_
| 12b  | Vector | _bbox1_
| 12b  | Vector | _bbox1_
|  4b  | uint | ___unused1___
|  4b  | uint | ___unused2___
|      | Vector[] | _vertices_
|      | Normal[] | _normals_ (1 per vector)<br>__optional__ only if world flags contain Normals
|  4b  |  uint[]  | _colors_ (1 per vector)<br>__optional__ only if world flags contain Prelit
|      |TexCoord[]| _texCoords1_ (1 per vector)<br>__optional__ only if world flags contain Textured or Textured2
|      |TexCoord[]| _texCoords2_ (1 per vector)<br>__optional__ only if world flags contain Textured2
|      |Triangle[]| _triangles_

### Normal
| Size | Type | Description |
|------|------|-------------|
|  1b  | uint | _x_
|  1b  | uint | _y_
|  1b  | uint | _z_
|  1b  |  int | _p_

### TexCoord
| Size | Type | Description |
|------|------|-------------|
|  4b  |float | _u_
|  4b  |float | _v_

### Triangle
| Size | Type | Description |
|------|------|-------------|
|  2b  | uint | _m_
|  2b  | uint | _v1_
|  2b  | uint | _v2_
|  2b  | uint | _v3_

## Possible child sections

* [[RWExtension]]
    * [[RWBinMeshPLG]]
    * [[RWCollisionPLG]]
