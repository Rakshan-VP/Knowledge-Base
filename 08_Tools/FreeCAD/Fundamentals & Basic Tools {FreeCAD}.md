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

Sketches are the foundation of parametric modeling in FreeCAD. A good sketch should be **geometrically correct, properly constrained, and easy to modify**.

### Sketch Settings

Before creating sketches, check the relevant settings in:

`Edit → Preferences → Sketcher`

- **Allow External Geometry as Construction Geometry** — Allows external/reference geometry to be used directly as construction geometry.
- Review other Sketcher preferences according to your workflow.

> [!tip]
> Set up these preferences once before starting a project.


### Creating a Sketch

The typical workflow is:

1. Select **Create Sketch** from the toolbar.
2. Select the required sketch plane.
3. Start creating the geometry.

For most designs, prefer the **Origin planes** when possible:

- XY Plane
- XZ Plane
- YZ Plane

Using the origin planes keeps the model properly referenced to the global coordinate system and makes the design easier to manage.


### Sketching Strategy

> [!note] Rule of thumb
> **Draw first → Constrain second.**

#### Recommended order

1. **Create the reference geometry**
   - Use **External Geometry** to bring existing edges or geometry into the sketch.
   - These edges provide references for positioning and constraining new geometry.

2. **Create the basic geometry**
   - Lines
   - Circles
   - Arcs
   - Rectangles
   - etc.

3. **Apply geometric constraints**
   - Coincident
   - Horizontal / Vertical
   - Parallel
   - Perpendicular
   - Symmetry
   - Tangent

4. **Apply dimensional constraints**
   - Length
   - Distance
   - Radius
   - Diameter
   - Angle

5. Continue until the sketch is **Fully constrained**.

> [!success] Goal
> A well-defined sketch should normally show **Fully constrained** in the Sketcher Tasks panel.


### External Geometry

**External Geometry** is useful for referencing existing model edges while creating a new sketch.

```text
Existing edge → External Geometry → New sketch geometry → Constrain relative to the edge
```

This is particularly useful when creating features that must align with existing holes, edges, or other geometry.


### Important Constraints

| Constraint | Purpose |
|---|---|
| Coincident | Joins points or geometry |
| Horizontal / Vertical | Keeps geometry horizontal or vertical |
| Parallel | Makes two lines parallel |
| Perpendicular | Makes two lines 90° apart |
| Symmetry | Makes geometry symmetric about a reference |
| Tangent | Creates a smooth tangent connection |

Use dimensional constraints in addition to geometric constraints to define the actual size and position of the geometry.


### Fully Constrained Sketch

While editing a sketch, monitor the degrees of freedom shown in the Tasks panel.

The preferred final state is:

> [!success]
> **Fully constrained**

This means the sketch geometry has no remaining unintended degrees of freedom.

A fully constrained sketch is generally:

- More stable
- Easier to modify
- Less likely to move unexpectedly
- Better suited for parametric modeling


### Viewing Inside the Model

When working with sketches or features inside an existing solid, **Section View** can be useful.

Use it to temporarily cut through the model and inspect internal geometry.

```text
Solid model → Section View → Inspect internal sketch / feature
```


This is especially useful for checking holes, internal pockets, cavities, and alignment.


### Moving a Sketch

A sketch can be repositioned through the Property Editor.

Navigate to:

`Property Editor → Attachment → Attachment Position`

The position is defined **relative to the sketch's local coordinate system**, not directly to the global coordinate system.

For example:

- **X** → movement along the sketch's local X-axis
- **Y** → movement along the sketch's local Y-axis
- **Z** → movement perpendicular to the sketch plane

Therefore, when you want to move a sketch normal to its plane, the **local Z position** is generally the relevant parameter.

> [!warning] Important
> The Z value here is the sketch's **local Z**, so it should not automatically be interpreted as global Z.


### Sketch Workflow — Quick Reference

```text
Create Sketch → Select Plane → Use External Geometry → Draw Geometry
     → Geometric Constraints → Dimensional Constraints
     → Fully Constrained → Create 3D Feature
```

## Related Links
### Examples
### Notes
### External