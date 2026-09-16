#type/method #domain/software #status/learning #scope/fundamental
> [!abstract] Summary 
> One or two sentences explaining the main idea.

## Overview

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

## FreeCAD — Sketches

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

## Related Links
### Examples
### Notes
### External
- [Deltahedra|New to FreeCAD? Start HERE (Ultimate Beginner Tutorial)](https://www.youtube.com/watch?v=KmtqNaGPiiQ)