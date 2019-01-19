# RWFrameList (0x000E)

The Frame list stores "Frames" whatever these magical structures might be...

It can be seen as child of [[RWAtomic]] sections.

## Structure format

| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | count of frames
|      |Frame[]| frames

### Frame
| Size | Type | Description |
|------|------|-------------|
| 36b  |Mat3x3| rotation matrix
| 12b  |Vector| position
|  4b  | uint | parent frame
|  4b  | uint | matrix creation flags (__unused__)

## Possible child sections

* [[RWExtension]]
    * [[RWAnimationPLG]]
