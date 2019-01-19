## RWMaterialList (0x0008)

The material list section stores one or many [[RWMaterial|RWMaterial]] sections.

It is usually the child of a [[RWGeometry|RWGeometry]] or [[RWWorld|RWWorld]] section.

## Structure format

| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | number of materials including material instances
|  4b  |uint[]|material indices

`A material index equals -1 if it is a material. If the material is an instance of a previously defined material, the index equals the base materials one.` - [gtamodding](http://www.gtamodding.com/wiki/Material_List_(RW_Section))

## Possible child sections

* [[RWMaterial|RWMaterial]]
