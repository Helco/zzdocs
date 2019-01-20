# 3D Samples (3DSamples_v2)

This sections describes 3D samples, but much is yet to be known how these are triggered.

## Format

The section is an array of 3DSample structures.

| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | index in FX category (see [SceneItemTypes](./SCN_Scene.md)) |
|      |zstring| sound filename |
| 12B  | Vec3f | position |
| 12B  | Vec3f | forward |
| 12B  | Vec3f | up |
|  4B  | float | minimal distance |
|  4B  | float | maximum distance |
|  4B  | uint  | volume (0-100) |
|  4B  | uint  | loop count |
|  4B  | uint  | falloff (probably priority based on distance) |
