## Scene section "WaypointSystem"

This section describes the waypoint system especially for duel scenes, if this section is used for overworld scenes is not confirmed yet.
This seems unlikely as none of the arrays for overworld scenes have any content. The waypoints for these scenes are set with [[triggers|SCN_Trigger]].<br/>
Although the executable does not read certain data for different versions, the only versions used in the files are 5 and 6.

### Format

| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | Version of the waypoint system format |
|  4B  | uint  | This field has to be zero |
| 24B  | byte[]| _version >= 5_ __unknown__ |
|  4B  | uint  | count of waypoints |
|      | Waypoint[] | see [[waypoint format|#waypoint]] |
|  4B  | uint  | _version >= 2_ count of unknown secondary data |
|      | SecondaryData[] | _version >= 2_ see [[secondary data format|#secondry-data]] |
|      | WaypointExt[] | _version >= 3_ for each waypoint some additional information, see [[waypoint extension format|#waypoint-extension]] |
|  4B  | uint  | This field has to be 0xFFFF |

#### Waypoint
| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | probably an id, unique for every waypoint per scene |
|  4B  | uint  | _version >= 4_ probably an id to another element (is never bigger than the count of waypoints) |
| 12B  | Vec3f | position |
|  4B  | uint  | count of first inner data |
|      | uint[]| first inner data, array of waypoint ids |
|  4B  | uint  | count of second inner data |
|      | uint[]| second inner data, array of waypoint ids |

#### Waypoint extension
| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | count of third inner data |
|      | uint[]| third inner data, array of waypoint ids |

#### Secondary data
| Size | Type  | Description |
|------|-------|-------------|
|  4B  | uint  | probably an id, does *not* reference a waypoint |
|  4B  | uint  | count of inner data |
|      | uint[]| inner data, array of secondary data ids |

### More understandable format

As this format is rather complex, it is probably helpful for a different explanation:

* The waypoint system has two arrays of data: waypoints and unknown secondary data
    * Waypoints are composed out of 
        * An id unequal to their index in the array
        * Another id not always but sometimes the same as the first one
        * A position vector
        * Three arrays with waypoint ids inside them, probably edges between waypoints?
    * The unknown secondary data is composed out of
        * An id
        * An array of secondary data ids
