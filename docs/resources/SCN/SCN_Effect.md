# Effects (Effects[_v2])

These sections describe simple effects or how complex effects (per file) should be included.

## Format

Each section is an array of their respective structure.

### Effect
| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | some kind of index |
|  4B  | enum  | [effect type](#effect-type) |
|      |EffectData| [effect type specific data](#effect-data) |

### Effect_v2
| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | some kind of index |
|  4B  | enum  | [effect type](#effect-type) |
|  4B  | uint  | __unknown__ some integer parameter |
|  4B  | uint  | __unknown__ some integer parameter |
|  4B  | uint  | __unknown__ some integer parameter |
|  4B  | uint  | __unknown__ some integer parameter |
|  4B  | uint  | __unknown__ some integer parameter |
|      |EffectData| [effect type specific data](#effect-data) |

### Effect type
| Value | Description |
|:-----:|-------------|
|   1   | |
|   4   | unused |
|   5   | unused |
|   6   | |
|   7   | unused |
|  10   | |
|  11   | Snowflakes |
|  13   | |

### Effect data

_if type == 1 or 5 or 6 or 10_

| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | __unknown__ some integer parameter |
| 12B  | Vec3f | __unknown__ some vector |
| 12B  | Vec3f | __unknown__ some vector |
<br/>

_if type == 4_

| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | __unknown__ some integer parameter |
| 12B  | Vec3f | __unknown__ some vector |
<br/>

_if type == 7_

| Size | Type  | Description |
|------|-------|-------------|
|      |zstring| effect filename |
| 12B  | Vec3f | __unknown__ some vector |
<br/>

_if type == Snowflakes_

| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | __unknown__ some integer parameter |
<br/>

_if type == 13_

| Size | Type  | Description |
|------|-------|-------------|
|      |zstring| effect filename |
| 12B  | Vec3f | __unknown__ some vector |
| 12B  | Vec3f | __unknown__ some vector |
| 12B  | Vec3f | __unknown__ some vector |
|  4B  | uint  | __unknown__ some integer parameter |
