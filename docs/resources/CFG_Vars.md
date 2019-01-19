## CFG for ai.cfg / wizform.cfg / net.cfg

These config files store variables which are either a floating point number or a string. The binary format is a bit unnecessary complicated and the actual use of the variables is yet to be known.

### Format

| Size | Type | Description          |
|------|------|----------------------|
| 16B  | MD5  | A MD5 hash of the current file starting at the first named variable |
|  3B  | uint | __unknown__ header |
|      |CfgValue| __unknown__ first value (see [[CfgValue|#CfgValue]]) |
|      |CfgVariable[]| array of variables to the end of the file (see [[CfgVariable|#CfgVariable]]) |

#### CfgVariable

| Size | Type | Description          |
|------|------|----------------------|
|  1B  | uint | size of name string |
|      |char[]| name string, but every character is XOR'ed with 0x75 |
|  1B  | char | zero byte (as end character for the name) |
|      |CfgValue| value of the variable

#### CfgValue

| Size | Type | Description          |
|------|------|----------------------|
|  4B  |float | numeric value (of the variable) |
|  1B  | uint | size of the string value, if > 0 the numeric value is set to 0.0 |
|      |char[]| value string |
|  1B  | char | ignored end byte (in the most cases 0) |
