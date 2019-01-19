## RWTexture (0x0006)

`A texture section is used to store identifying information about a texture and it's alpha layer.` - [gtamodding](http://www.gtamodding.com/wiki/Texture_(RW_Section))

It is usually the child of a [[RWMaterial|RWMaterial]] section. It has one to two [[RWString|RWString]] sections which define the color/alpha texture filename.

## Structure format

| Size | Type | Description |
|------|------|-------------|
|  1b  | enum | _filterMode_ (see below)
| 4bit | enum | U addressing mode (see below)
| 4bit | enum | V addressing mode (see below)
|15bit | uint | ___unused___

### _filterMode_ enum
| Name             | Value    | 
|------------------|----------|
| NAFilterMode     | 0
| Nearest          | 1
| Linear           | 2
| MipNearest       | 3
| MipLinear        | 4
| LinearMipNearest | 5
| LinearMipLinear  | 6

### X addressing mode
| Name             | Value    | 
|------------------|----------|
| NATextureAddresss| 0
| Wrap             | 1
| Mirror           | 2
| Clamp            | 3
| Border           | 4

## Possible child sections

* [[RWString|RWString]]
* [[RWExtension|RWExtension]]
