# Models (Models[_v?])

These sections describe models which are essential to the gameplay or the design of the scene. <br/>
There are different version of the section, but for now only Models_v3 is described, as the other versions are not used in the game files.

### Format

Each section is an array of their respective structure.

#### Model_v3

| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | some kind of index |
|      |zstring| model filename |
| 12B  | Vec3f | position |
| 12B  | Vec3f | direction vector |
| 12B  | Vec3f | scale |
|  4B  | uint  | color |
|  1B  | uint  | __unknown__ |
|  4B  | uint  | __unknown__ |
|  1B  | uint  | __unknown__ |
