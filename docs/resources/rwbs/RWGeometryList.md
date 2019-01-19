## RWGeometryList (0x001A)

RWGeometryList is usually the child of a [[RWClump|RWClump]] section and only contains [[RWGeometry|RWGeometry]] sections besides its own [[RWStruct|RWStruct]], which does not have very interesting data.

## Structure format

| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | number of geometries

## Possible child sections

* [[RWGeometry|RWGeometry]]
