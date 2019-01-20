# Basic information
----------------------
FBS files are used to store various numeric and/or textual data about various aspects of the gameplay. They store information about the texts displayed in the game, fairy, spell, item and NPC information. They are the biggest source for [scripts](../../internal/Scripts). This format was developed by Funatics Entertainment for ZanZarah.

## Data format
There are actually two types of FBS files: the one whose only file is called "_fb0x00.fbs" and all the other files. The first one is the database index file, it stores all column names and some number which doesn't seem to be used and is the same for all columns.

| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | number of column data
|      |Column[]| the columns

### Column
| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | _type_
|      |zstring| name of the column

The other database files store the actual row data, but every row has its indivitually sized array of columns and data type it stores in those columns. Every row has at least an uid column which is therefore not even mentioned in the index file. <br/>
Unfortunately the column index stored in the row data is not always correct, but the order of row data is for one database always the same.

| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | number of rows
|      | Row[]| row data

### Row
| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | UID of row
|  4b  | uint | number of filled columns
|      |ColumnData[]| the data

### ColumnData
| Size | Type | Description |
|------|------|-------------|
|  4b  | enum | data type
|  4b  | uint | the column index
|      |      | This is eiter zstring, 4b uint, 1b uint, UUID or Buffer

### data type enum
| Name     | Value |
|----------|:-----:|
|  String  |   0   |
|   Uint   |   1   |
|   UUID   |   3   |
|   Byte   |   4   |
|  Buffer  |   5   |

### UUID
| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | __unused__
|  4b  | uint | _uid_
|  4b  | uint | _type_

### Buffer
| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | _size_
|  1b  |uint[]| _data_

## The content

| Filename | Description |
|:--------:|-------------|
| fb0x00   | The index file |
| [[fb0x01]] | Fairies |
| [[fb0x02]] | Strings |
| [[fb0x03]] | Spells  |
| [[fb0x04]] | Items   |
| [[fb0x05]] | NPCs    |
| [[fb0x06]] | Dialog lines |
