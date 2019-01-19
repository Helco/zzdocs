## RWSkinPLG (0x0116)

The RWSkinPLG section describes the bones of an actor and how these react with the vertices of the model mesh. It is usually found as [[[RWExtension|RWExtension]] child of a [RWAtomic|RWAtomic]] section.

Here is a discrepancy between the format described by [gtamodding](http://www.gtamodding.com/wiki/Skin_PLG_(RW_Section)) and the one described by [kabbi](https://github.com/kabbi/zanzarah-tools/blob/master/dff-parser.coffee#L288). The differences are not compatible to each other, but the format by kabbi seems to work, so this is what I will using as well, even though it has some strange properties (see bone matrix).

## Structure format

| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | bone count
|  4b  | uint | vertex count
| 4x1b |uint[]| _vertexIndices_ (1 set per vertex)
| 4x4b |float[]| _vertexWeights_ (1 set per vertex)
|      |Bone[]| _bones_

### Bone
| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | _i1_
|  4b  | uint | _idx_
|  4b  | uint | _i3_
| 12b  |Vector| _right_
|  4b  | uint | ___unused___
| 12b  |Vector| _up_
|  4b  | uint | ___unused___
| 12b  |Vector| _at_
|  4b  | uint | ___unused___
| 12b  |Vector| _pos_
|  4b  | uint | ___unused___
