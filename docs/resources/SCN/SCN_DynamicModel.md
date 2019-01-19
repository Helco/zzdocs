## Scene section "DynamicModels"

This section describes models which can change their appearence over time, but there is little information how and in which way this occurs.

### Format

The section content contains an structural array.

| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | some kind of index |
|  4B  | uint  | __unknown__ some integer |
|  4B  | uint  | __unknown__ some integer |
| 12B  | Vec3f | position |
| 12B  | Vec3f | direction vector |
|  4B  | float | __unknown__ floating parameter |
|  4B  | float | __unknown__ floating parameter |
| 12B  | Vec3f | __unknown__ some vector |
|  4B  | uint  | __unknown__ some integer |
|  4B  | uint  | __unknown__ some integer |
|      |DynModelData[3]| __unknown__ change parameters (see [[DynModelData|#dynmodeldata]]) |

#### DynModelData

| Size | Type  | Description |
|------|-------|-------------|
|  4B  | float | __unknown__ some floating parameter |
|  4B  | float | __unknown__ some floating parameter |
|  4B  | float | __unknown__ some floating parameter |
|  4B  | float | __unknown__ some floating parameter |
|  4B  | float | __unknown__ some floating parameter |
|  4B  | float | __unknown__ some floating parameter |
|  4B  | float | __unknown__ some floating parameter |
|  1B  | uint  | __unknown__ some integer |
|  4B  | uint  | __unknown__ some color |
|  4B  | uint  | __unknown__ some integer parameter |
|      |zstring| model filename |
|      |zstring| texture filename |
