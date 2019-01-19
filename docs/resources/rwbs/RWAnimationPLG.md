## RWAnimationPLG (0x0108)

The RWAnimationPLG section is the most confusing section of all. [kabbi](https://github.com/kabbi/zanzarah-tools/blob/master/dff-parser.coffee#L126) does read it, but even to him it is apparently not understandable as he calls it the "strangeAnimData". I have to investigate this...

It can be seen as child of [[RWClump|RWClump]], as well as single child of the many [[RWExtension|RWExtension]] sections of [[RWClump|RWClump]]->[[RWFrameList|RWFrameList]].

## Data format

| Size | Type | Description |
|------|------|-------------|
| 4b   | int  | _i1_
| 4b   | bool | optional<br>determines if the next items are stored
| 4b   | uint | _ii1_
| 4b   | uint | count of _items1_
| 4b   | uint | count of _items2_
|      | AnimData[] | _items1_
|      | AnimData[] | _items2_

### AnimData
| Size | Type | Description |
|------|------|-------------|
|      |zstring| _name_
| 4b   |enum  | Currently only __Type1__ or __Type2__<br>Determines type of _innerItems1_
| 4b   | uint | count of _innerItems1_
| 4b   | uint | count of _innerItems2_
|      | InnerItems1[] | _innerItems1_
|      | InnerItems2[] | _innerItems2_

### InnerItems1
| Size | Type | Description |
|------|------|-------------|
| 4b   |float | _f1_
| 4b   |float | _f2_
| 4b   |float | _f3_
| 4b   |float | _f4_<br>Only if _type_ is __Type2__

### InnerItems2
| Size | Type | Description |
|------|------|-------------|
| 4b   | uint | _i1_
| 4b   | uint | _i2_
| 4b   |float | _f_
