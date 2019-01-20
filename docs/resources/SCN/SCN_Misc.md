# Misc

This section stores some core data about the scene and how it is supposed to be rendered.
Internally this section is split into three parts.

## Format

| Size | Type  | Description |
|------|-------|-------------|
|      |zstring| Name of the world file |
|      |zstring| Path of the world file (always ```..\\Resources\\Worlds\\```) |
|      |zstring| Path to the world textures (always ```..\\Resources\\Textures\\Worlds\\```) |
|  4B  | uint  | Color of the ambient light (applied only to Atomics) |
| 12B  | Vec3f | __unknown__ |
| 12B  | Vec3f | __unknown__ |
|  4B  | uint  | background color (used for clearing) |
|  1B  | enum  | [Fog type](#fog-type) |
|  4B  | uint  | _if fog!=None_ fog color |
|  4B  | float | _if fog!=None_ fog distance |
|  4B  | float | __unknown__ |
|  4B  | float | far clip (near clip is constant at 0.1) |