# RWAtomic (0x0014)

`Atomic is a container section used in DFF files as child of a Clump section. It is normally accompanied by a Struct section. An atomic section can associate a Frame with a Geometry.` - [gtamodding](http://www.gtamodding.com/wiki/Atomic_(RW_Section))

## Structure format

| Size | Type | Description |
|------|------|-------------|
| 4b   | uint | _frameIndex_
| 4b   | uint | _geometryIndex_
| 4b   |flags | Possible flags are __CollisionTest__(0x01) and __Render__(0x04)
| 4b   | uint | ___unused___

## Possible child sections

* [[RWGeometry]]
* [[RWExtension]]
    - [[RWSkinPLG]]
