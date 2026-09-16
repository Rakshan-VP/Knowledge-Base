#type/method #domain/software #status/learning #scope/fundamental
> [!abstract] Summary 
> This note covers the **fundamental FreeCAD tools, interface, settings, and sketching practices** required to build stable parametric models. It also introduces the basic Part Design features used to create and modify 3D solids.

## Overview
FreeCAD is a **parametric 3D CAD application** where models are built by defining sketches, applying constraints, and creating feature-based solids. This note provides the essential setup and fundamental tools needed to establish a smooth and reliable modeling workflow.

## FreeCAD GUI

The FreeCAD interface is divided into several key areas, each serving a specific role in the design workflow.

![[FreeCAD.png|875]]

- **Menu Bar** — Provides access to application commands, settings, and document operations.  
  *Examples: `File → Save`, `Edit → Preferences`, `View → Panels`.*

- **Tool Bar** — Provides quick access to frequently used commands and modeling tools.  
  *Examples: Create Sketch, Pad, Pocket, Fillet, Chamfer.*

- **Workbench Selector** — Selects the workbench that provides the tools required for a particular task.  
  *Examples: `Part Design`, `Sketcher`, `Part`, `TechDraw`.*

- **Model View** — Displays the document structure as a model/feature tree. It shows how the model is built heirachically and allows objects to be selected and organized.  
  *Examples: `Body → Sketch → Pad → Pocket`.*

- **Property Editor** — Displays and allows modification of the properties of the selected object.  
  *Examples: changing a Pad's `Length`, a Sketch's constraints, or an object's `Placement`.*

- **Navigation** — Provides controls for navigating and orienting the 3D view.  
  *Examples: rotating, panning, zooming, and switching to Front, Top, or Axonometric views.*

- **Tasks** — Displays the options and parameters for the currently active operation.  
  *Examples: defining Pad length, Pocket depth, or Sketcher constraints.*

## Sketches

Sketches are the foundation of parametric modeling in FreeCAD: **geometrically correct, properly constrained, and easy to modify.**

### Setup

`Edit → Preferences → Sketcher`

- **Allow External Geometry as Construction Geometry** — lets external/reference geometry be used directly as construction geometry.
- Review other Sketcher preferences to match your workflow.

> [!tip]
> Set these up once, before starting a project.

### Workflow

```text
Create Sketch → Select Plane → External Geometry → Draw Geometry
     → Geometric Constraints → Dimensional Constraints
     → Fully Constrained → Create 3D Feature
```

- **Create Sketch** → select plane → start drawing. Prefer **Origin planes** (XY / XZ / YZ) — keeps the model referenced to the global coordinate system.
- **Rule of thumb: Draw first → Constrain second.**

> [!success] Goal
> Sketcher Tasks panel should read **Fully constrained** — no unintended degrees of freedom left. This makes a sketch more stable, easier to modify, and better suited for parametric modeling.

### External Geometry

Import existing edges as references so new geometry stays aligned to holes, edges, or other features.

```text
Existing edge → External Geometry → New sketch geometry → Constrain relative to the edge
```

### Constraints

| Type | Options |
|---|---|
| **Geometric** | Coincident, Horizontal/Vertical, Parallel, Perpendicular, Symmetry, Tangent |
| **Dimensional** | Length, Distance, Radius, Diameter, Angle |

| Constraint | Purpose |
|---|---|
| Coincident | Joins points or geometry |
| Horizontal / Vertical | Locks orientation |
| Parallel | Two lines parallel |
| Perpendicular | Two lines at 90° |
| Symmetry | Mirrors geometry about a reference |
| Tangent | Smooth tangent connection |

Apply geometric constraints first, then dimensional constraints to fully define size and position.

### Section View

Cuts through a solid to inspect internal geometry — useful for checking holes, pockets, cavities, and alignment.

```text
Solid model → Section View → Inspect internal sketch / feature
```

### Moving a Sketch

`Property Editor → Attachment → Attachment Position`

Position is relative to the **sketch's local** coordinate system:

- **X** → local X-axis
- **Y** → local Y-axis
- **Z** → perpendicular to the sketch plane

> [!warning]
> This Z is **local**, not global — don't assume it matches the model's global Z.

## Part Design Tools

The most-used tools for turning a sketch into a solid: **Pad, Pocket, Fillet, Chamfer, Mirror.**

### Pad

Extrudes a sketch into a solid along its normal direction. The most basic feature-creation tool.

```text
Sketch → Pad → Solid
```

| Option | Purpose |
|---|---|
| Length | Extrusion distance (one direction) |
| Symmetric to plane | Extrudes equally on both sides of the sketch |
| Reversed | Flips extrusion direction |
| Up to Face / Up to Shape | Extrudes until it hits a chosen face or object |
| Draft angle | Adds taper to the extrusion |

> [!tip]
> Use **Symmetric to plane** when the sketch plane should stay centered in the final solid.

### Pocket

Removes material by extruding a sketch profile *into* an existing solid — the cut counterpart to Pad.

```text
Sketch (on/inside solid) → Pocket → Material removed
```

| Option | Purpose |
|---|---|
| Length | Depth of the cut |
| Through all | Cuts completely through the solid |
| Reversed | Flips cut direction |
| Up to Face / Up to Shape | Cuts until it hits a chosen face or object |

> [!note]
> The sketch must lie on or reference the solid it's cutting into.

### Fillet

Rounds selected edges or faces — softens sharp corners.

```text
Select edge/face → Fillet → Rounded edge
```

| Option | Purpose |
|---|---|
| Radius | Size of the rounded edge |
| All edges | Applies fillet to every edge of a face at once |
| Variable radius | Different radius values along one edge |

> [!tip]
> Fillet **after** the main solid features are stable — early fillets often break later edits (edge references shift).

### Chamfer

Cuts a flat, angled bevel on selected edges — the angular counterpart to Fillet.

```text
Select edge/face → Chamfer → Beveled edge
```

| Option | Purpose |
|---|---|
| Distance | Size of the bevel (equal on both faces) |
| Distance × Distance | Asymmetric bevel size |
| Distance × Angle | Bevel defined by one distance and an angle |

> [!note]
> Use Chamfer over Fillet when a machined/angular look is needed (e.g. edges that mate with other parts, printed thread starts).

### Mirror

Duplicates a feature or sketch symmetrically across a plane.

```text
Select feature/sketch → Mirror plane → Mirrored copy
```

| Option | Purpose |
|---|---|
| Mirror plane | XY / XZ / YZ or a custom datum plane |
| Selected features | One or more Pad/Pocket/Sketch features to mirror |

> [!tip]
> Mirroring a **feature** (not just a sketch) keeps the copy parametric — it updates automatically if the original changes.

### General Order of Use

```text
Sketch → Pad/Pocket → Fillet/Chamfer → Mirror (if symmetric)
```

> [!warning]
> Apply Fillet/Chamfer and Mirror **late** in the feature tree — doing them too early makes later sketches lose their references when edges shift.


## Related Links
### Examples
### Notes
### External
- [Deltahedra|New to FreeCAD? Start HERE (Ultimate Beginner Tutorial)](https://www.youtube.com/watch?v=KmtqNaGPiiQ)