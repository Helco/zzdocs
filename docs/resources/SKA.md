# SKA
SKA files are used to describe animations of actors. Despite the data format being developed by Criterion Software for Renderware, the file does not inherit the [RWBS](./RWBS/index.md) format.

## Data format

| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | number of frames
|  4b  | uint | _flags_ __unused__
|  4b  |float | _duration_
|      |KeyFrame[]| the frames

### KeyFrame

| Size | Type | Description |
|------|------|-------------|
| 16b  |Quaternion|Bone rotation
| 12b  |Vector|Bone position
|  4b  |float | _time_
|  4b  | uint | data offset of parent frames
