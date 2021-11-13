# RenderOrder

## 3D

Defaults: Wrap | True | LessEqual | True | True | 0 | SrcAlpha | InvSrcAlpha | 0.082352944 | True |

| Render State | Description | TexAddress | Fog | ZFunc | ZTest | ZWrite | ZBias | SrcBlend | DestBlend | AlphaRef? | VertexAlpha
|:------------:|:------------|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| 67 | Static backdrop | Wrap | True | LessEqual | True | True | 0 | SrcAlpha | InvSrcAlpha | 0.082352944 | True |
|    | Dynamic backdrop |
| 56 | World  | Wrap | True | LessEqual | True | True | 0 | One | Zero | 0.082352944 | True |
| 44 | Footprints | Wrap | True | LessEqual | True | False | 1 | SrcAlpha | InvSrcAlpha | 0.082352944 | True |
| 63 | Actor parts | Wrap | True | LessEqual | True | True | 0 | SrcAlpha | InvSrcAlpha | 0.082352944 | True |
| 58 | FOModel Standard | Wrap | True | LessEqual | True | True | 0 | SrcAlpha | InvSrcAlpha | 0.082352944 | True |
| 59 | FOModel Additive 3 | Wrap | False | LessEqual | True | True | 0 | SrcAlpha | One | 0.082352944 | True |
|    | Effect Order 0 |
| 64 | Model | Wrap | True | LessEqual | True | True | 0 | SrcAlpha | InvSrcAlpha | 0 | True |
| 58 | FOModel Standard 2 | Wrap | True | LessEqual | True | True | 0 | SrcAlpha | InvSrcAlpha | 0.082352944 | True |
| 59 | FOModel Additive 2 | Wrap | False | LessEqual | True | True | 0 | SrcAlpha | One | 0.082352944 | True |
| 61 | FOModel EnvMap | Wrap | True | LessEqual | True | False | 1 | SrcAlpha | InvSrcAlpha | 0.082352944 | True |
|    | Effect Order 1 |
| 68 | DynModels Not4 | Wrap | True | LessEqual | True | True | 0 | SrcAlpha | InvSrcAlpha | 0 | True |
| 69 | DynModels | Wrap | True | LessEqual | True | True | 0 | One | Zero | 0.082352944 | True |
| 58 | FOModel Standard 3 | Wrap | True | LessEqual | True | True | 0 | SrcAlpha | InvSrcAlpha | 0.082352944 | True |
| 60 | FOModel Additive 1 | Wrap | False | LessEqual | True | False | 0 | SrcAlpha | One | 0.082352944 | True |
| 65 | Effect Order 2 | WrapNoPersp | True | LessEqual | True | False | 0 | SrcAlpha | InvSrcAlpha | 0 | True |
|    | StdEffect |
| 66 | Debug Waypoint system | Wrap | True | LessEqual | True | True | 0 | SrcAlpha | InvSrcAlpha | 0.082352944 | True |
|    | Debug Actor collider |
|    | Debug FOModel collider |
|    | Debug Triggers |
|    | Debug Waypoint trigger |
|    | Debug Soundeffects 3D |
| Mod | DebugIcon Effects |
|     | DebugIcon Soundeffects 3D |
|     | DebugIcon Triggers |
|     | DebugIcon Lights |
|     | DebugIcon FOModels |
|     | DebugText Effects |
|     | DebugText Models |
|     | DebugText FOModels |
|     | DebugText DynModels |
|     | Debug local trigger points |
|     | Debug spline |