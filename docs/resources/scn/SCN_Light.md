# Scene section "Lights"

As the name states, this section defines the scene lights although its effect is yet to be shown.

## Format

The section is an array of light structures.

| Size | Type  | Description                                      |
|------|-------|--------------------------------------------------|
|  4B  |  uint | index in light category (see [[SceneItemTypes]]) |
|  4B  |  enum | [Type of the light](#light-type)                 |
|  4B  | float | Color component red                              |
|  4B  | float | Color component green                            |
|  4B  | float | Color component blue                             |
|  4B  | float | Color component alpha                            |
|  4B  | uint  | Flags (see [light-flags](#light-flags))          |
|      |       | Type-specific data                               |

### Directional light
| Size | Type  | Description |
|------|-------|-------------|
| 12B  | Vec3f | position    |
| 12B  | Vec3f | direction   |

### Point light
| Size | Type  | Description |
|------|-------|-------------|
|  4B  | float | radius      |
| 12B  | Vec3f | position    |

### Spot light

The cone angle of spot lights are hard-coded to 0.5 radians.

| Size | Type  | Description                                                    |
|------|-------|----------------------------------------------------------------|
|  4B  | float | radius                                                         |
| 12B  | Vec3f | position                                                       |
| 12B  | Vec3f | A point for the spot light to look at (only direction is used) |

### Light type

| Value | Description                               |
|:-----:|-------------------------------------------|
|   1   | Directional                               |
|   2   | Ambient (not supported by the scene file) |
|  128  | Point                                     |
|  129  | Spot                                      |

