# Mechanical design

All CAD files live in [`cad/`](cad/).

| Format | Use |
| --- | --- |
| `.SLDASM` | SolidWorks assemblies |
| `.SLDPRT` | Editable SolidWorks parts |
| `.STL` | Meshes for slicing or viewing without SolidWorks |
| `.3MF` | Print-ready slicer projects for the tubes and rings |

## Key assemblies

| File | Description |
| --- | --- |
| `套筒十二面体装配体.SLDASM` | Full dodecahedral robot |
| `套筒单腿装配体-*.SLDASM` | Single-leg assembly in several extension states (`-爆炸图` = exploded view) |
| `渲染模型.SLDASM`, `渲染模型-2.SLDASM` | Rendering models |

The Chinese filenames are the original working names. They are kept unchanged because SolidWorks assemblies reference parts by file name — keep all files in the same folder.

## Editing workflow

1. Copy the whole `cad/` folder before making changes.
2. Open an assembly from the copy; if references are missing, use **Find References** and point to the same folder.
3. Export fresh STL/3MF files instead of overwriting the provided ones.

Dimensions and clearances reflect the original prototype — check them against your printer, servos, corrugated tubes and fasteners before fabrication.
