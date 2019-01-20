## ZZVersion

There exists a common structure for versions in Zanzarah, used internally in the executable, in [scenes](../resources/SCN/index.md) and savefiles.

### Format

| Size | Type  | Description |
|------|-------|-------------|
|      |zstring| The name of the author |
|  4B  | enum  | The country in which the game version was released (see [countries](#build-countries)) |
|  4B  | enum  | The type of release (see [build types](#build-types)) |
|  4B  | uint  | __unknown__ |
|  4B  | uint  | The build versions, it seems like build versions shall be incompatbible to each other |
|  4B  |zstring| A formatted date string at which the file was built |
|  4B  |zstring| A formatted time string at which the file was built |
|  4B  | uint  | The year at which the file was built |
|  4B  | uint  | __unknown__ |


### Build Countries
| Value | Description  |
|:-----:|--------------|
|   0   | Germany      |
|   1   | English      |
|   2   | France       |
|   3   | Spain        |
|   4   | Italy        |
|   5   | Japanese     |
|   6   | __English6__ |
|   8   | Russia       |

### Build Types
| Value | Description  |
|:-----:|--------------|
|   0   | Debug        |
|   1   | Release      |
|   2   | WebDemo      |
|   3   | CdDemo       |
