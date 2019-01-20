# FOModels (FOModels[_v?])

These sections describe optional models, which are not essential to the gameplay. <br/>
There are different version of the section, but for now only FOModels_v4 is described, as the older versions are not used in the game files.

## Format

Each section is a array of their respective structure.

### FOModel_v4

| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | some kind of index |
|      |zstring| model filename |
| 12B  | Vec3f | position |
| 12B  | Vec3f | direction vector |
|  4B  | Vec3f | __unknown__ some floating parameter |
|  4B  | Vec3f | __unknown__ some floating parameter |
|  4B  | Vec3f | __unknown__ some floating parameter |
|  4B  | Vec3f | __unknown__ some floating parameter |
|  4B  | Vec3f | __unknown__ some floating parameter |
|  4B  | uint  | color |
|  1B  | uint  | detail level at which the model is rendered |
|  1B  | uint  | __unknown__ |
|  4B  | enum  | [render type](#render-type) |
|  1B  | uint  | __unknown__ |
|  4B  | uint  | __unknown__ |

### Render type

| Value |    Name   | Description |
|:-----:|-----------|-------------|
|   0   | Standard1 | Alpha cutout |
|   1   | Additive1 | |
|   2   | EnvMap32  | |
|   3   | EnvMap64  | |
|   4   | EnvMap96  | used in the cathedral |
|   5   | EnvMap128 | |
|   6   | EnvMap196 | used for the house windows in London |
|   7   | EnvMap255 | used for the cupboard windows in London |
|   8   | Standard2 | Metallic? |
|   9   | Standard3 | Plants? |
|  10   | Additive2 | used for cob webs |
|  11   | Additive3 | |