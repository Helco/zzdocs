## Scene section "VertexModifiers"

This section describes some kind of vertex modification, but it isn't used in the game files.

### Format

The section is an array of VertexModifier structures.

| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | some kind of index |
|  4B  | uint  | __unknown__ some kind of type |
| 12B  | Vec3f | __unknown__ some vector |
|  4B  | uint  | __unknown__ some color |
| 12B  | Vec3f | _type == 1_ __unknown__ some vector |
|  4B  | uint  | __unknown__ some integer parameter |
|  1B  | uint  | __unknown__ some byte |
