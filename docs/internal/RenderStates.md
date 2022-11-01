# RenderStates

Internally the engine manages the render properties by a collection of 70 render states which are applied right before an object is rendered.
However properties in these states can be unset, in which case the current value is unmodified.
At various stages during the rendering a default state is applied which has a full set of properties overwriting every state before.

Many states are equal, pointing towards a semantic name that was lost during compilation.

|  | Name | TexAddressU | TexAddressV | TexPerspective | TexFilter | ZTest | ZWrite | ShadeMode | SrcBlend | DstBlend | FogType | Fog | VertexAlpha | FogColor | FogDensity | ZFunc | AlphaFunc | AlphaRef | ZBias | AlphaTest |
|:-----:|:-----|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| def | *no name yet* | Wrap | Wrap | True | MipLinear | True | True | Gouraud | SrcAlpha | InvSrcAlpha | Linear | True | True | 254,230,184,0 | 0.1 | LessEqual | GreaterEqual | 0.0823529 | 0 | True |
| 0 | *no name yet* | Clamp | Clamp | - | - | True | True | - | One | One | - | - | True | - | - | - | - | - | - | - |
| 1 | *no name yet* | - | - | - | - | - | False | - | SrcAlpha | DestAlpha | - | - | - | - | - | - | - | - | - | - |
| 2 | *no name yet* | - | - | - | - | - | False | - | SrcAlpha | InvSrcAlpha | - | - | - | - | - | - | - | - | - | - |
| 3 | *no name yet* | - | - | False | - | - | - | Gouraud | - | - | - | - | True | - | - | - | - | - | - | - |
| 4 | *no name yet* | Clamp | Clamp | - | - | True | False | - | SrcAlpha | InvSrcAlpha | - | - | True | - | - | - | Always | - | - | - |
| 5 | *no name yet* | Clamp | Clamp | - | - | True | False | - | SrcAlpha | One | - | - | True | - | - | - | Always | - | - | - |
| 6 | *no name yet* | - | - | - | - | False | False | - | SrcAlpha | One | - | False | - | - | - | - | - | 0.0196078 | - | - |
| 7 | *no name yet* | Clamp | Clamp | - | - | False | False | - | SrcAlpha | One | - | False | - | - | - | - | - | 0.0196078 | - | - |
| 8 | *no name yet* | Wrap | Wrap | - | - | True | True | - | One | SrcAlpha | - | - | True | - | - | - | - | - | - | - |
| 9 | *no name yet* | Wrap | Wrap | - | - | True | False | - | SrcAlpha | One | - | - | True | - | - | - | - | - | - | - |
| 10 | *no name yet* | - | - | - | - | True | False | - | SrcAlpha | One | - | - | - | - | - | - | - | - | - | - |
| 11 | *no name yet* | Clamp | Clamp | - | - | True | True | - | One | SrcAlpha | - | - | True | - | - | - | - | - | - | - |
| 12 | *no name yet* | - | - | - | - | - | - | - | - | - | - | False | - | - | - | - | - | - | - | - |
| 13 | *no name yet* | Wrap | Wrap | - | - | True | False | - | SrcAlpha | One | - | - | True | - | - | - | - | - | - | - |
| 14 | *no name yet* | Clamp | Clamp | - | - | True | False | - | SrcAlpha | One | - | - | - | - | - | - | - | - | - | - |
| 15 | *no name yet* | Clamp | Clamp | - | - | True | False | - | SrcAlpha | One | - | - | - | - | - | - | - | 0 | - | - |
| 16 | *no name yet* | - | - | - | - | True | True | - | SrcAlpha | One | - | - | - | - | - | - | - | 0 | - | - |
| 17 | *no name yet* | Wrap | Wrap | - | - | True | False | - | SrcAlpha | One | - | - | - | - | - | - | - | - | - | - |
| 18 | *no name yet* | Wrap | Wrap | - | - | True | False | - | One | Zero | - | - | - | - | - | - | - | - | - | - |
| 19 | *no name yet* | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 20 | *no name yet* | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 21 | *no name yet* | Clamp | Clamp | - | - | True | False | - | SrcAlpha | One | - | - | - | - | - | - | - | 0 | - | - |
| 22 | *no name yet* | Clamp | Clamp | - | - | True | False | - | SrcAlpha | One | - | False | - | - | - | - | - | 0 | - | - |
| 23 | *no name yet* | Wrap | Wrap | - | - | False | False | - | SrcAlpha | One | - | - | - | - | - | - | - | 0.03 | - | - |
| 24 | *no name yet* | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 25 | *no name yet* | - | - | - | - | False | False | - | One | One | - | - | True | - | - | - | - | - | - | - |
| 26 | *no name yet* | - | - | - | - | True | False | - | SrcAlpha | InvSrcAlpha | - | - | False | - | - | - | GreaterEqual | 0 | - | True |
| 27 | *no name yet* | - | - | - | - | - | False | - | SrcAlpha | InvSrcAlpha | - | - | - | - | - | - | - | 0 | - | - |
| 28 | *no name yet* | - | - | - | - | True | False | - | SrcAlpha | InvSrcAlpha | - | - | False | - | - | - | GreaterEqual | 0 | - | True |
| 29 | *no name yet* | - | - | - | - | True | False | - | SrcAlpha | InvSrcAlpha | - | False | False | - | - | - | GreaterEqual | 0 | - | True |
| 30 | *no name yet* | - | - | - | - | False | False | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 31 | *no name yet* | - | - | - | - | False | False | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 32 | *no name yet* | - | - | - | - | - | - | - | - | - | - | False | - | - | - | - | - | - | - | - |
| 33 | *no name yet* | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 34 | *no name yet* | - | - | - | - | False | False | - | - | - | - | False | - | - | - | - | - | - | - | - |
| 35 | *no name yet* | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 36 | *no name yet* | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 37 | *no name yet* | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 38 | *no name yet* | - | - | - | - | False | False | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 39 | *no name yet* | - | - | - | - | - | False | - | One | Zero | - | - | False | - | - | - | - | - | - | False |
| 40 | *no name yet* | - | - | - | - | - | False | - | SrcAlpha | InvSrcAlpha | - | - | True | - | - | - | Always | - | - | True |
| 41 | *no name yet* | - | - | - | - | - | False | - | SrcAlpha | One | - | - | True | - | - | - | Always | - | - | True |
| 42 | *no name yet* | - | - | - | - | False | False | - | SrcAlpha | InvSrcAlpha | - | False | True | - | - | - | - | - | - | - |
| 43 | *no name yet* | - | - | - | - | False | False | - | One | Zero | - | False | - | - | - | - | - | - | - | False |
| 44 | *no name yet* | - | - | - | - | - | False | - | - | - | - | - | - | - | - | - | - | - | 1 | - |
| 45 | *no name yet* | - | - | - | - | False | False | - | - | - | - | False | - | - | - | - | - | 0.03125 | - | - |
| 46 | *no name yet* | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 47 | *no name yet* | - | - | - | - | False | False | - | One | One | - | False | - | - | - | - | - | 0 | - | - |
| 48 | *no name yet* | - | - | - | - | False | False | - | SrcAlpha | One | - | False | - | - | - | - | - | 0 | - | - |
| 49 | *no name yet* | - | - | - | - | False | True | - | SrcAlpha | InvSrcAlpha | - | False | - | - | - | - | - | 0.03125 | - | - |
| 50 | *no name yet* | - | - | - | - | False | False | - | One | Zero | - | False | - | - | - | - | - | 0 | - | - |
| 51 | *no name yet* | - | - | - | - | False | False | - | Zero | InvSrcAlpha | - | False | - | - | - | - | - | 0 | - | - |
| 52 | *no name yet* | Clamp | Clamp | - | - | - | - | - | - | - | - | False | - | - | - | - | - | - | - | - |
| 53 | *no name yet* | Clamp | Clamp | - | - | - | False | - | Zero | InvSrcColor | - | False | True | - | - | - | - | - | 1 | - |
| 54 | *no name yet* | Clamp | Clamp | - | - | - | False | - | SrcAlpha | - | - | - | True | - | - | - | - | - | - | - |
| 55 | *no name yet* | - | - | - | - | - | - | - | - | - | - | False | True | - | - | Greater | - | - | - | - |
| 56 | *no name yet* | - | - | - | - | - | - | - | One | Zero | - | - | - | - | - | - | - | - | - | - |
| 57 | *no name yet* | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 58 | *no name yet* | - | - | - | - | - | - | - | SrcAlpha | InvSrcAlpha | - | - | - | - | - | - | - | - | - | - |
| 59 | *no name yet* | - | - | - | - | - | True | - | SrcAlpha | One | - | False | - | - | - | - | - | - | - | - |
| 60 | *no name yet* | - | - | - | - | - | False | - | SrcAlpha | One | - | False | - | - | - | - | - | - | - | - |
| 61 | *no name yet* | - | - | - | - | True | False | - | SrcAlpha | InvSrcAlpha | - | - | - | - | - | - | - | - | 1 | - |
| 62 | *no name yet* | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 63 | *no name yet* | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 64 | *no name yet* | - | - | - | - | - | - | - | SrcAlpha | InvSrcAlpha | - | - | - | - | - | - | GreaterEqual | 0 | - | True |
| 65 | *no name yet* | - | - | False | - | - | False | - | SrcAlpha | InvSrcAlpha | - | - | - | - | - | - | - | 0 | - | - |
| 66 | *no name yet* | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 67 | *no name yet* | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 68 | *no name yet* | - | - | - | - | - | True | - | SrcAlpha | InvSrcAlpha | - | - | - | - | - | - | - | 0 | - | - |
| 69 | *no name yet* | - | - | - | - | True | True | - | One | Zero | - | - | - | - | - | - | - | - | - | - |
