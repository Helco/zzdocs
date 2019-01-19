# RWBinMeshPLG (0x050E)

`The Bin Mesh plugin holds an optimized representation of the model topology. Triangles are grouped together into Meshes by their Material and stored as triangle strips when the rpGEOMETRYTRISTRIP flag (0x1) is set in the Geometry, otherwise as triangle lists.` -  [gtamodding](http://www.gtamodding.com/wiki/Bin_Mesh_PLG_(RW_Section))

This section can usually be seen as [[RWExtension]] childs of [[RWGeometry]] or [[RWAtomicSection]]. The size of the _indices_ datatype would change to 16 bit if the executable were build for OpenGL. As ZanZarah is DirectX exclusive we ignore this case and always work with 32 bit.

## Structure format

| Size | Type | Description |
|------|------|-------------|
|  4b  | enum | __TriList__ (0) or __TriStrip__ (1)
|  4b  | uint | count of sub-Meshes
|  4b  | uint | total count of indices
|      | Mesh[] | the sub-meshes

### Mesh
| Size | Type | Description |
|------|------|-------------|
|  4b  | uint | count of indices
|  4b  | uint | material index (of the geometry/world material list)
|  4b  | uint[] | indices
