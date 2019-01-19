# RWPlaneSection (0x000A)

The plane section section presumably stores information about a dividing plane of a world (as ZanZarah uses Binary Space Partition) and thus usually has one or two [[RWAtomicSection]] or other plane sections as childs.

The format was decrypted by [kabbi](https://github.com/kabbi/zanzarah-tools/blob/master/bsp-parser.coffee#L171) but some meaning remains hidden for now.

## Structure format

| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | sector type
|  4b  |float | _value_
|  4b  |bool  | _leftIsWorldSector_
|  4b  |bool  | _rightIsWorldSector_
|  4b  |float | _leftValue_
|  4b  |float | _rightValue_

## Possible child sections

* [[RWAtomicSection]]
