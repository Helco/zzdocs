# RWClump (0x0010)

`A Clump is a container for a Frame hierarchy to which Atomics, Lights and Cameras are attached.` - [gtamodding](http://www.gtamodding.com/wiki/RpClump)

As ZanZarah does not save any light or camera data this section is exclusively used as root section of [[DFF files]]. The structure data is not really intersting as the count of Atomics, etc. can be counted by just reading the other child sections.

## Structure format

| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | number of Atomics
|  4b  | uint | number of Lights <br>__optional__ only after version 0x33000
|  4b  | uint | number of Cameras <br>__optional__ only after version 0x33000

## Possible child sections

* [[RWAtomic]]
* RWLight
* RWCamera
* [[RWFrameList]]
* [[RWGeometryList]]
* [[RWExtension]]
    * RWCollisionModel
