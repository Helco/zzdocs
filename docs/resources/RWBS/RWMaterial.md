# RWMaterial (0x0007)

This section stores information about how the geometry should look like.

It is usually the child of a [[RWMaterialList]] section.

## Structure format

| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | _flags_ ___unused___
|  4b  | uint | color
|  4b  | uint | ___unused___
|  4b  | bool | _isTextured_
|  4b  |float | _ambient_ <br>__optional__ only after 0x30300
|  4b  |float | _specular_ <br>__optional__ only after 0x30300
|  4b  |float | _diffuse_ <br>__optional__ only after 0x30300

## Possible child sections

* [[RWTexture]]
* [[RWExtension]]
