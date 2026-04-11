# Awesome 3D Modeling with Blender for CAD

A curated list of addons, tools, file formats, and resources for **3D modeling with Blender for CAD** — covering precision modeling, parametric workflows, BIM/IFC authoring, 3D printing preparation, technical drawing, and CAD file interoperability.

> Blender is an open-source 3D creation suite (GPL-3.0) developed by the Blender Foundation. It uses polygonal mesh modeling and does not include native NURBS-based solid modeling found in traditional CAD applications. CAD-related functionality is provided through built-in addons, third-party extensions, and the Python API (`bpy` module).

---

## Table of Contents

- [Blender CAD Workflows](#blender-cad-workflows)
- [Supported File Formats](#supported-file-formats)
- [Built-in Addons for CAD](#built-in-addons-for-cad)
- [CAD & Precision Modeling Addons](#cad--precision-modeling-addons)
- [CAD File Import/Export Addons](#cad-file-importexport-addons)
- [Measurement & Dimensioning](#measurement--dimensioning)
- [Technical Drawing & Annotation](#technical-drawing--annotation)
- [Hard Surface Modeling Addons](#hard-surface-modeling-addons)
- [Architectural & BIM Tools](#architectural--bim-tools)
- [Procedural & Parametric Tools](#procedural--parametric-tools)
- [3D Printing & Mesh Preparation](#3d-printing--mesh-preparation)
- [Python API & Automation](#python-api--automation)
- [Complementary CAD Software](#complementary-cad-software)
- [Tutorials & Learning Resources](#tutorials--learning-resources)
- [Related Awesome Lists](#related-awesome-lists)
- [Contributing](#contributing)
- [License](#license)

---

## Blender CAD Workflows

This section documents workflows achievable in Blender for CAD-related tasks. Each workflow uses specific tools and has documented capabilities and limitations.

| Workflow | Description | Primary Tools |
|---|---|---|
| **Precision Mesh Modeling** | Mesh-based modeling with snapping, numeric input, and constraint solvers | Snap tools (built-in), Precision Drawing Tools, CAD Sketcher |
| **Hard Surface Modeling** | Boolean-based operations with modifier stack; produces polygonal mesh output | Bool Tool (built-in), HardOps/BoxCutter (commercial), n-Burn ND (free) |
| **Parametric/Procedural** | Node-based geometry generation with modifiable parameters | Geometry Nodes (built-in), Sverchok |
| **BIM/IFC Authoring** | Authoring and editing IFC (ISO 16739) building information models | Bonsai |
| **Architectural Modeling** | Scene construction using parametric architectural elements | Archipack, JARCH-Vis |
| **3D Printing Preparation** | Mesh analysis, repair, and export for additive manufacturing | 3D Print Toolbox (built-in), MeshLab |
| **Technical Drawing** | 2D dimensioned drawings and annotations from 3D models | Dimensions and Lines, MeasureIt-ARCH, FreeStyle |
| **CAD File Interchange** | Import/export STEP, IGES, DXF, SVG for CAD software interoperability | Import CAD Model, Export IGES, built-in DXF/SVG import |

---

## Supported File Formats

Blender supports various file formats for CAD and 3D modeling. Most import/export addons are disabled by default and must be enabled via `Edit > Preferences > Add-ons`.

### Mesh & Geometry Exchange

| Format | Extension | Import | Export | Enabled by Default | Notes |
|---|---|:---:|:---:|:---:|---|
| Wavefront OBJ | `.obj` | ✓ | ✓ | No | Geometry + materials; widely supported |
| FBX | `.fbx` | ✓ | ✓ | Yes | Autodesk interchange; rigs, animation |
| glTF 2.0 | `.gltf`, `.glb` | ✓ | ✓ | Yes | WebGL, real-time engines; PBR materials |
| Stanford PLY | `.ply` | ✓ | ✓ | Yes | Point clouds, 3D scan data |
| STL | `.stl` | ✓ | ✓ | Yes | 3D printing; single material |
| Alembic | `.abc` | ✓ | ✓ | No | Cached geometry/animation |
| Collada | `.dae` | ✓ | ✓ | No | Cross-software 3D asset interchange |
| USD/USDZ | `.usd`, `.usdc`, `.usdz` | ✓ | ✓ | No | Pixar Universal Scene Description |
| 3D Studio | `.3ds` | ✓ | ✓ | No | Legacy format; limited support |
| X3D/VRML97 | `.x3d`, `.wrl` | ✓ | ✓ | No | XML-based 3D graphics |

### CAD-Specific Formats

| Format | Extension | Import | Export | Method | Notes |
|---|---|:---:|:---:|---|---|
| AutoCAD DXF | `.dxf` | ✓ | ✓ | Built-in addon | 2D/3D CAD interchange; lines, polylines, arcs |
| SVG | `.svg` | ✓ | ✓ | Built-in addon | 2D vector paths; imports as Grease Pencil or curves |
| STEP AP242 | `.stp`, `.step` | Via addon | No | Import CAD Model addon | BRep geometry; converts to mesh |
| IGES | `.iges`, `.igs` | Via addon | Via addon | Import CAD Model / Export IGES | Surface geometry; import converts to mesh, export converts mesh to NURBS surfaces |

---

## Built-in Addons for CAD

These addons ship with Blender (GPL-3.0) and must be enabled via `Edit > Preferences > Add-ons`.

### 3D Print Toolbox

- **Addon ID:** `mesh_print3d_utils`
- **Path:** `Preferences > Add-ons > Mesh > 3D-Print Toolbox`
- **Access:** 3D Viewport Sidebar (`N` key) > `3D-Print` panel
- **Blender Manual:** [3D Print Toolbox](https://docs.blender.org/manual/en/latest/addons/mesh/3d_print_toolbox.html)
- **Analysis Functions:** Intersecting faces, non-manifold edges, bad contiguous geometry, wall thickness, overhang angles, degenerate faces, distorted faces, sharp edges
- **Fix Functions:** Delete loose geometry, dissolve degenerate faces, make manifold, recalculate normals
- **Statistics Output:** Volume, surface area, bounding box dimensions (X/Y/Z), triangle/face/edge/vertex counts, overhang area and percentage

### MeasureIt

- **Addon ID:** `object_measureit`
- **Path:** `Preferences > Add-ons > 3D Viewport > MeasureIt`
- **Access:** 3D Viewport Sidebar (`N` key) > `MeasureIt` panel
- **Blender Manual:** [MeasureIt](https://docs.blender.org/manual/en/latest/addons/add_mesh/measureit.html)
- **Functions:** Linear dimensions, angular dimensions, area measurements, annotations
- **Unit Systems:** Metric (m, cm, mm), Imperial (ft, in)
- **Render Output:** Dimensions visible in Cycles/Eevee renders when enabled

### Precision Drawing Tools (PDT)

- **Path:** `Preferences > Add-ons > 3D View > Precision Drawing Tools`
- **Blender Extensions:** [Precision Drawing Tools](https://extensions.blender.org/add-ons/precision-drawing-tools-pdt/)
- **Functions:** Precision vertex placement, construction lines, numeric coordinate input, planar constraints, trigonometric functions
- **Blender Version:** Ships with Blender 2.82+ as official addon

### Bool Tool

- **Addon ID:** `object_bool_tools`
- **Path:** `Preferences > Add-ons > Object > Bool Tool`
- **Blender Manual:** [Bool Tool](https://docs.blender.org/manual/en/latest/addons/object/bool_tool.html)
- **Operations:** Union, Difference, Intersect
- **Workflow Modes:** Direct (applies immediately), Modifier (non-destructive)

### LoopTools

- **Addon ID:** `mesh_looptools`
- **Path:** `Preferences > Add-ons > Mesh > LoopTools`
- **Blender Manual:** [LoopTools](https://docs.blender.org/manual/en/latest/addons/mesh/looptools.html)
- **Operations:** Circle, Flatten, Relax, Stretch, Space, Gstretch, Bridge

### tinyCAD Mesh Tools

- **Addon ID:** `mesh_tinycad`
- **Path:** `Preferences > Add-ons > Mesh > tinyCAD`
- **Blender Manual:** [tinyCAD](https://docs.blender.org/manual/en/3.6/addons/mesh/tinycad.html)
- **Operations:**
  - `VTX`: Extend, trim, or intersect two edges
  - `V2X`: Place vertex at edge intersection
  - `XALL`: Intersect all selected edges
  - `BIX`: Create bisector of two edges
  - `CCEN`: Calculate circle center from three points

### Import-Export: DXF

- **Addon ID:** `io_scene_dxf`
- **Path:** `Preferences > Add-ons > Import-Export > Import-Export: DXF`
- **AutoCAD Version Support:** R12 through 2018
- **Entities:** Lines, polylines, arcs, circles, dimensions, hatches
- **Geometry:** 3D faces, meshes, surfaces

### Import-Export: SVG

- **Addon ID:** `io_curve_svg`
- **Path:** `Preferences > Add-ons > Import-Export > Import-Export: SVG`
- **Import:** SVG paths as Grease Pencil strokes or Bezier curves
- **Export:** Grease Pencil strokes to SVG

### Import-Export: STL

- **Addon ID:** `io_mesh_stl`
- **Path:** `Preferences > Add-ons > Import-Export > Import-Export: STL`
- **Import Options:** ASCII/binary, forward/backward axis, unit scale
- **Export Options:** ASCII/binary, batch export, unit scale

### FreeStyle

- **Addon ID:** `render_freestyle`
- **Path:** `Preferences > Add-ons > Render > FreeStyle`
- **Blender Manual:** [FreeStyle](https://docs.blender.org/manual/en/latest/render/freestyle/index.html)
- **Line Types:** Silhouette, border, crease, ridge, valley, suggestive contours
- **Output:** SVG, PDF (via Inkscape conversion)

---

## CAD & Precision Modeling Addons

Third-party addons for CAD and precision modeling workflows.

### CAD Sketcher

- **License:** GPL-3.0
- **GitHub:** [hlorus/CAD_Sketcher](https://github.com/hlorus/CAD_Sketcher)
- **Blender Extensions:** [CAD Sketcher](https://extensions.blender.org/add-ons/cad-sketcher/)
- **Website:** [cadsketcher.com](https://www.cadsketcher.com/)
- **Constraint Solver:** Solvespace (BSD-3-Clause)
- **Version:** 0.27.5+
- **Blender Version:** 4.0+
- **Function:** Constraint-based 2D sketcher. Creates geometric entities (points, lines, arcs, circles) with geometric and dimensional constraints. Outputs Bezier curves or mesh geometry.
- **Geometric Constraints:** Horizontal, vertical, parallel, perpendicular, tangent, coincident, equal length, equal radius, symmetric
- **Dimensional Constraints:** Distance, angle, radius/diameter, perimeter
- **Output:** Bezier curves, mesh with UV, modifier-compatible geometry

### Mesh Align Plus

- **License:** GPL-3.0
- **GitHub:** [egtwobits/mesh-align-plus](https://github.com/egtwobits/mesh-align-plus)
- **Function:** Precise mesh/object alignment with custom transformations
- **Operations:** Align, distribute, measure and match, custom transforms
- **Blender Version:** 2.80+

### Offset Edges

- **License:** GPL-3.0
- **GitHub:** [amb/blender-addon-offset-edges](https://github.com/amb/blender-addon-offset-edges)
- **Function:** Creates parallel edges at specified distance from selected edges
- **Blender Version:** 2.80+

### BB-Snap

- **License:** GPL-3.0
- **GitHub:** [riouxr/BB-Snap](https://github.com/riouxr/BB-Snap)
- **Function:** Precise object transformation with snap-to-increment sliders and advanced movement controls
- **Blender Version:** 4.0+

---

## CAD File Import/Export Addons

Addons for importing and exporting CAD file formats (STEP, IGES, NURBS).

### Import CAD Model

- **License:** GPL-3.0
- **GitHub:** [chenpaner/Import-CAD-Model](https://github.com/chenpaner/Import-CAD-Model)
- **Blender Artists Thread:** [Free Addon: Import CAD Model](https://blenderartists.org/t/free-addon-import-cad-model-quickly-import-stp-iges-to-blender/1582013)
- **Blender Version:** 4.0+
- **Platforms:** Windows
- **Supported Formats:** `.step`, `.stp`, `.iges`, `.igs`
- **Conversion Engine:** Mayo toolkit (BRep to mesh)
- **Output Formats:** GLTF (preserves scene hierarchy) or OBJ (collections)
- **Features:**
  - Import via `File > Import` menu or drag-and-drop into viewport
  - Adjustable mesh quality: Very Coarse, Coarse, Medium, Fine, Very Precise
  - Custom global scaling (0.0001× to 100×)
  - Real-time progress monitoring
  - Preset system for import settings
  - Auto-cleanup of temporary files and duplicate materials

### Export IGES

- **License:** Commercial
- **Function:** Converts Blender subdivision/polygonal meshes to NURBS surfaces and exports as IGES format
- **Supported Conversion:** Subdivision surfaces to NURBS B-spline surfaces
- **Output Format:** `.iges`, `.igs`
- **Use Case:** Export Blender models to CAD software (Fusion 360, Rhino, AutoCAD, Inventor)
- **Limitations:** Mesh-to-NURBS conversion produces faceted NURBS surfaces; not true solid modeling

---

## Measurement & Dimensioning

Tools for measuring and displaying dimensions on geometry in Blender.

| Tool | Type | License | Capabilities | Source |
|---|---|---|---|---|
| **MeasureIt** | Built-in addon | GPL-3.0 | Linear, angular, area dimensions; annotations; render output | `Preferences > Add-ons > 3D Viewport > MeasureIt` |
| **MeasureIt-ARCH** | Community addon | MIT | Extended architectural dimensions; dynamic labels; plan annotations | [GitHub](https://github.com/Blender-ARCHVIZ/MeasureIt-ARCH) |
| **CAD Sketcher** | Community addon | GPL-3.0 | Constraint-based dimensions (distance, angle, radius) within sketch environment | [cadsketcher.com](https://www.cadsketcher.com/) |
| **Cad_Dimensions** | Community addon | Free | CAD-style axis-aligned measurements; adjustable text location/size/orientation; viewport "Cadify" styling; imperial unit conversion | [Blender Extensions](https://extensions.blender.org/add-ons/cad-measure-extension/) |
| **Blender Measure Tool** | Built-in tool | N/A | Single distance/angle between two points in Edit mode | Edit mode > Toolbar > Measure Tool |
| **Sverchok Analyzer** | Community addon | GPL-3.0 | Automated area, volume, bounding box, curvature, nearest-point calculations | [Sverchok](https://github.com/nortikin/sverchok) |

### Measure Tool (Built-in, No Addon Required)

- **Activation:** Edit mode > Toolbar > Measure Tool
- **Function:** Click two vertices to display distance; click three vertices to display angle
- **Display:** Floating label in viewport
- **Units:** Follows scene unit settings (metric/imperial)

### Cad_Dimensions

- **Version:** 2.0.0
- **Blender Version:** 4.2 LTS+
- **Features:**
  - Dedicated X, Y, Z buttons for axis-aligned measurements
  - Adjustable dimension text location, size, and orientation
  - "Cadify" button applies ArchiCAD-style viewport styling
  - Imperial unit conversion (v2.0.0+)
  - Extrude-based finalization of dimension placement

---

## Technical Drawing & Annotation

Tools for generating 2D technical drawings, blueprints, and dimensioned layouts.

### Dimensions and Lines

- **License:** GPL-3.0
- **GitHub:** [JanHolinka3/dimensions_and_lines](https://github.com/JanHolinka3/dimensions_and_lines)
- **Function:** Creates CAD-style dimensions, technical drawings, and blueprint layouts in the 3D viewport
- **Features:**
  - Interactive mouse-based dimension placement
  - Non-destructive mesh lines generated from edges (renderable as geometry)
  - Dedicated snapping system for precise placement
  - Camera setup for standard paper sizes with DPI-based render resolution
  - Multiple line types and hatch patterns
- **Documentation:** `Manual_1_0_9.pdf` in repository
- **Tutorial:** [YouTube Technical Drawing Guide](https://www.youtube.com/watch?v=Q3rGMpYz0o8)

### FreeStyle

- **Type:** Built-in addon
- **Path:** `Preferences > Add-ons > Render > FreeStyle`
- **Function:** Non-photorealistic line rendering from 3D geometry
- **Line Types:** Silhouette, border, crease, ridge, valley, suggestive contours
- **Output:** Raster images, SVG (via Inkscape conversion)
- **Use Case:** Technical illustration, line-art documentation

### MeasureIt-ARCH

- **License:** MIT
- **GitHub:** [Blender-ARCHVIZ/MeasureIt-ARCH](https://github.com/Blender-ARCHVIZ/MeasureIt-ARCH)
- **Version:** 0.4.6
- **Function:** Fork of MeasureIt with architectural dimensioning extensions
- **Additional Features Over MeasureIt:** Dynamic dimensions, floor plan annotations, area labeling, technical drawing tools

### Node Dimensions (Geometry Nodes)

- **License:** Commercial
- **Marketplace:** [SuperHive](https://superhivemarket.com/products/node-dimensions-visual-measurements-for-blender-using-geometry-nodes) / [Gumroad](https://blenderrenaissance.gumroad.com/l/node-dimensions-for-blender)
- **Blender Version:** 5.0+
- **Function:** CAD-style measurement indicators implemented as Geometry Nodes modifiers
- **Measurement Types:** Distance, radius, diameter, angle
- **Features:** Non-destructive; pre-animated; configurable units; technical font support
- **Implementation:** Geometry Nodes modifier applied to mesh; displays measurement markers that update with geometry changes

---

## Hard Surface Modeling Addons

Third-party addons for hard surface (boolean-based mechanical) modeling workflows.

### n-Burn ND

- **License:** MIT
- **GitHub:** [michaelg11/nd](https://github.com/michaelg11/nd)
- **Function:** Non-destructive modeling toolkit built on Geometry Nodes and modifier stacks
- **Operations:** Boolean, edge protection, bevel, mirror, array
- **Blender Version:** 4.0+

### Bevel After Boolean

- **License:** GPL-3.0
- **GitHub:** [Weislav/Bevel-After-Boolean](https://github.com/Weislav/Bevel-After-Boolean)
- **Function:** Automatically applies bevel to edges created by boolean modifiers
- **Purpose:** Fix shading artifacts and restore surface continuity after boolean operations

### HardOps

- **License:** Commercial
- **Blender Market:** [HardOps](https://blendermarket.com/products/hardops)
- **Version:** 9.3.2+
- **Blender Version:** 4.0+
- **Function:** Modifier stack manager and boolean/bevel workflow accelerator
- **Operations:** Bevel weighting, modifier hotkeys, status bar feedback

### BoxCutter

- **License:** Commercial
- **Blender Market:** [BoxCutter](https://blendermarket.com/products/boxcutter)
- **Version:** 7.5+
- **Blender Version:** 4.0+
- **Function:** Shape-based cutting and boolean operations in viewport
- **Geometry Types:** Boxes, cylinders, circles, custom shapes

### MESHmachine

- **License:** Commercial
- **Blender Market:** [MESHmachine](https://blendermarket.com/products/meshmachine)
- **Function:** Hard surface topology refinement
- **Operations:** Micro-loops for sharp edges, bevel stamping, boolean retopology

---

## Architectural & BIM Tools

### Bonsai

- **License:** GPL-3.0
- **Website:** [bonsaibim.org](https://bonsaibim.org/)
- **Blender Extensions:** [Bonsai](https://extensions.blender.org/add-ons/bonsai/)
- **Developer:** IfcOpenShell Team
- **Version:** 0.8.5+
- **Blender Version:** 4.2–5.1+
- **Platforms:** Windows (x64), macOS (Apple Silicon, x64), Linux (x64)
- **Standard:** Industry Foundation Classes (IFC) — ISO 16739:2022
- **Features:**
  - Load and view IFC models
  - Edit IFC attributes, properties, classification systems
  - Modify geometry while preserving IFC semantics
  - Create building elements (walls, slabs, doors, windows, columns, beams, spaces)
  - Generate 2D drawings (plans, sections, elevations)
  - MEP modeling (HVAC, plumbing, electrical distribution)
  - Structural analysis model editing
  - Construction scheduling (4D)
  - Quantity takeoff with formulas
  - Clash detection
  - BCF issue tracking
  - IDS validation
- **Documentation:** [bonsaibim.org/docs](https://docs.blenderbim.org/)
- **Demo:** [20-minute demo](https://www.youtube.com/watch?v=Ooh03WF__80)

### Archipack

- **License:** GPL-3.0
- **GitHub:** [s-leger/archipack](https://github.com/s-leger/archipack)
- **Elements:** Walls, slabs, doors, windows, stairs, railings, roofs, frames, moldings
- **Function:** Parametric architectural primitives via modifier stack
- **Editing:** Real-time on-screen dimension editing

### JARCH-Vis

- **License:** GPL-3.0
- **GitHub:** [Blender-ARCHVIZ/JARCH-Vis](https://github.com/Blender-ARCHVIZ/JARCH-Vis)
- **Assets:** Building generators, stair builders, landscape tools
- **Type:** Procedural architectural elements

### Blender 3D Architect

- **Website:** [blender3darchitect.com](https://blender3darchitect.com/)
- **Author:** Allan Brito
- **Content:** Tutorials and documentation for Archipack, BlenderGIS, and Bonsai workflows

---

## Procedural & Parametric Tools

### Geometry Nodes

- **Path:** Built-in modifier system (no addon enable required)
- **Blender Manual:** [Geometry Nodes](https://docs.blender.org/manual/en/latest/modeling/geometry_nodes/index.html)
- **Blender Version:** 3.0+ (modifier system); 4.5+ (volume processing, simulation)
- **Function:** Node-based procedural geometry generation
- **Capabilities:**
  - Procedural mesh generation
  - Point/curve distribution and instancing
  - Attribute manipulation (float, vector, color, boolean)
  - Volume processing (Blender 4.5+)
  - Simulation nodes (Blender 4.5+)
- **Use in CAD:** Parametric component libraries; pattern generation; data-driven layouts; measurement indicators (Node Dimensions)

### Sverchok

- **License:** GPL-3.0
- **GitHub:** [nortikin/sverchok](https://github.com/nortikin/sverchok)
- **Documentation:** [nortikin.github.io/sverchok](https://nortikin.github.io/sverchok/docs/)
- **Node Count:** 600+
- **Blender Version:** 2.93–5.1+
- **Data Types:** Vector, edge, polygon, matrix, curve, surface, NURBS, solid, list
- **CAD Functions:**
  - CSG Boolean operations
  - Bmesh operations and property access
  - Cross-section generation
  - SVG/DXF export
  - BREP/NURBS/IFC data exchange
  - Area and volume calculation
  - Solar radiation/insolation analysis
  - CSV and custom data format import
  - Python scripting (Scripted node)
  - Genetic algorithm support

---

## 3D Printing & Mesh Preparation

### 3D Print Toolbox

- See [Built-in Addons for CAD](#built-in-addons-for-cad) section above.

### MeshLab

- **License:** GPL-2.0
- **Website:** [meshlab.net](https://www.meshlab.net/)
- **Platforms:** Windows, macOS, Linux
- **Function:** Standalone mesh processing application
- **Operations:** Non-manifold repair, decimation, remeshing, Hausdorff distance computation, measurement, filtering
- **Formats:** OBJ, PLY, OFF, STL, 3DS, FBX

### Instant Meshes

- **License:** ZLIB
- **GitHub:** [wjakob/instant-meshes](https://github.com/wjakob/instant-meshes)
- **Platforms:** Windows, macOS, Linux
- **Function:** Automatic retopology from dense meshes to clean quad-dominant geometry
- **Parameters:** Target vertex count, crease weight, alignment mode

### Laser Slicer

- **License:** GPL-3.0
- **GitHub:** [jayanam/laser_slicer](https://github.com/jayanam/laser_slicer)
- **Function:** Cross-sectional slicing of 3D models with SVG export for laser cutting
- **Layer Options:** X, Y, Z axis; configurable slice thickness

---

## Python API & Automation

Blender includes a comprehensive Python API (`bpy` module) for scripting and automation.

- **API Documentation:** [docs.blender.org/api/current](https://docs.blender.org/api/current/)
- **Scripting Reference:** [Blender Manual — Scripting](https://docs.blender.org/manual/en/latest/advanced/scripting/index.html)
- **Standalone Module:** [fake-bpy-module](https://github.com/nutti/fake-bpy-module) — Stubs for IDE autocomplete and linting

### API Modules for CAD Workflows

| Task | API Modules | Notes |
|---|---|---|
| Object creation & manipulation | `bpy.ops.mesh`, `bpy.data.objects`, `bpy.data.meshes` | Create, modify, delete geometry |
| Precision transformations | `bpy.context`, `mathutils` | Exact translations, rotations, scales |
| Modifier stack management | `bpy.types.Modifier` | Add, configure, apply modifiers |
| Custom addon development | `bpy.types.Panel`, `bpy.types.Operator`, `bpy.props` | Build custom UI panels and operators |
| Import/export automation | `bpy.ops.import_scene`, `bpy.ops.export_scene` | Batch file conversion |
| Geometry Nodes | `bpy.types.GeometryNodeTree`, `bpy.types.Node` | Create and modify node trees |
| Data extraction | `bpy.types.Mesh`, `bmesh` | Query vertex/edge/face data; calculate measurements |

---

## Complementary CAD Software

These tools integrate with or complement Blender in CAD workflows.

| Software | License | Type | Integration with Blender |
|---|---|---|---|
| [**FreeCAD**](https://www.freecad.org/) | LGPL (Free) | Parametric 3D CAD | IFC exchange via Bonsai; STEP export from FreeCAD → import to Blender via Import CAD Model |
| [**SolveSpace**](https://solvespace.com/) | GPL (Free) | Parametric 2D/3D CAD | DXF/SVG export → import into Blender |
| [**LibreCAD**](https://librecad.org/) | GPL (Free) | 2D CAD | DXF export → import via built-in DXF addon |
| [**QCAD**](https://qcad.org/) | GPL/Commercial | 2D CAD | DXF export → import into Blender |
| [**OpenSCAD**](https://openscad.org/) | GPL (Free) | Script-based 3D CAD | STL/DXF/SVG export → import into Blender |
| [**Rhino 3D**](https://www.rhino3d.com/) | Commercial | NURBS modeling | 3DM import via Rhino3DM addon; OBJ/FBX exchange |
| [**MeshLab**](https://www.meshlab.net/) | GPL (Free) | Mesh processing | OBJ/PLY/STL exchange |

### FreeCAD ↔ Blender Workflow

```
FreeCAD                          Blender
├── STEP/IGES export ─────────→ Import CAD Model addon (mesh import)
├── IFC export ────────────────→ Bonsai addon (IFC authoring)
├── DXF export ────────────────→ Built-in DXF import
├── STL export ────────────────→ Built-in STL import (3D printing prep)
└── Mesh export (OBJ) ─────────→ OBJ import → visualization/rendering
```

---

## Tutorials & Learning Resources

### Precision & CAD Modeling

| Resource | Type | URL |
|---|---|---|
| CAD Sketcher Documentation | Documentation | [cadsketcher.com](https://www.cadsketcher.com/) |
| CAD Sketcher Tutorial | Video | [YouTube](https://www.youtube.com/results?search_query=cad+sketcher+blender+tutorial) |
| Blender Snapping: CAD Precision | Video | [YouTube](https://www.youtube.com/watch?v=DpNBLcoFCFU) |
| Blender Units: Metric & Imperial | Video | [YouTube](https://www.youtube.com/watch?v=-Bq7YI9ustE) |
| 2D CAD Drawings from Blender | Tutorial | [Blender Artists](https://blenderartists.org/t/tutorial-2d-cad-drawings-with-blender/1550767) |

### Technical Drawing & Dimensioning

| Resource | Type | URL | Notes |
|---|---|---|---|
| Dimensions and Lines Tutorial | Video | [YouTube](https://www.youtube.com/watch?v=Q3rGMpYz0o8) | Technical drawing and CAD dimensioning |
| CAD Like Tools: Snap Measure | Video | [YouTube](https://www.youtube.com/watch?v=JZ-rqRg58Rc) | CAD-style measurement tools |

### Hard Surface Modeling

| Resource | Type | URL |
|---|---|---|
| Josh Gambrell | YouTube | [YouTube/@JoshGambrell](https://www.youtube.com/@JoshGambrell) |
| Cédric Lepiller | YouTube | [YouTube/@CedricLepiller](https://www.youtube.com/@CedricLepiller) |
| Blender Bros — Accelerator | Course | [blenderbros.com](https://www.blenderbros.com/) |
| Creative Shrimp — Hard Surface | Course | [creativeshrimp.com](https://www.creativeshrimp.com/) |

### BIM & Architecture

| Resource | Type | URL |
|---|---|---|
| Bonsai Demo Video | Video | [YouTube](https://www.youtube.com/watch?v=Ooh03WF__80) |
| Bonsai Documentation | Documentation | [docs.blenderbim.org](https://docs.blenderbim.org/) |
| Blender 3D Architect | Website | [blender3darchitect.com](https://blender3darchitect.com/) |
| Architecture Topics | YouTube | [YouTube/@ArchitectureTopics](https://www.youtube.com/@ArchitectureTopics) |
| IfcOpenShell Documentation | Documentation | [docs.ifcopenshell.org](https://docs.ifcopenshell.org/) |

### Parametric & Geometry Nodes (CAD Focus)

| Resource | Type | URL |
|---|---|---|
| Geometry Nodes Manual | Documentation | [Blender Manual](https://docs.blender.org/manual/en/latest/modeling/geometry_nodes/index.html) |
| Sverchok Documentation | Documentation | [nortikin.github.io/sverchok](https://nortikin.github.io/sverchok/docs/) |
| Chris Prenninger | YouTube | [YouTube/@chrisprenninger](https://www.youtube.com/@chrisprenninger) |
| Nodevember (CAD-focused challenges) | Challenge | [nodevember.org](https://nodevember.org/) |

### STEP/IGES Import

| Resource | Type | URL | Notes |
|---|---|---|---|
| Import CAD Addon Tutorial | Video | [YouTube](https://www.youtube.com/watch?v=NOLGch4agzE) | STEP/IGES import workflow |
| Import CAD Model Discussion | Forum | [Blender Artists](https://blenderartists.org/t/free-addon-import-cad-model-quickly-import-stp-iges-to-blender/1582013) | Setup and usage guide |

---

## Related Awesome Lists

| List | URL | Scope |
|---|---|---|
| awesome-blender | [github.com/agmmnn/awesome-blender](https://github.com/agmmnn/awesome-blender) | Blender addons and tools |
| awesome-blender-addons | [github.com/ChrisLend/awesome-blender-addons](https://github.com/ChrisLend/awesome-blender-addons) | Notable addons |
| awesome-3d-printing | [github.com/tttmmz/awesome-3d-printing](https://github.com/tttmmz/awesome-3d-printing) | 3D printing |
| awesome-cad | [github.com/fougue/awesome-cad](https://github.com/fougue/awesome-cad) | CAD tools |

---

## External CAD Conversion Tools

Standalone tools for converting CAD files for import into Blender.

| Tool | Platform | Supported Input | Supported Output | License |
|---|---|---|---|---|
| **CAD Exchanger** | Windows, macOS, Linux | 30+ CAD formats (STEP, IGES, CATIA, SolidWorks, JT, Parasolid, IFC, DWG) | OBJ, STL, glTF, STEP | Commercial (free viewer) |
| **SimLab CAD Composer** | Windows, macOS | DWG, DXF, 3D PDF, DWF | FBX, OBJ, glTF | Commercial |
| **Mayo** | Windows | STEP, IGES | glTF, OBJ | GPL-3.0 |
| **Gltf-Pipeline** | Windows, macOS, Linux | glTF | OBJ, STL | MIT |

---

## Contributing

Contributions are welcome. Please ensure:

- The resource is directly relevant to 3D modeling with Blender for CAD workflows
- The link is active and resolves to the correct resource
- The entry includes: name, license (Free/Commercial), a one-line description, and a working link
- Commercial tools are marked as **Commercial**; free/open-source tools specify their license (GPL, MIT, etc.)
- Entries are placed in the most appropriate section

---

## License

[![CC0](https://i.creativecommons.org/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

This work is dedicated to the public domain under the Creative Commons Zero 1.0 Universal license.

---

<p align="center">A factual, community-maintained resource for Blender CAD workflows</p>
