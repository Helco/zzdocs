# 2D Samples (2DSamples_v2)

This sections describes 2D samples, but much is yet to be known how these are triggered.

## Format

The section is an array of 2DSample structures.

| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | index in FX category (see [SceneItemTypes](./SCN_Scene.md)) |
|      |zstring| sound filename |
|  4B  | uint  | volume (0-100) |
|  4B  | uint  | loop count |
|  1B  | uint  | __unknown__ some flag |
