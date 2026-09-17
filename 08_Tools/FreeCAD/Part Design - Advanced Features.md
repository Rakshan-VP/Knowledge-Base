#type/method #domain/software #status/learning #scope/intermediate
> [!abstract] Summary 
> This note covers the **intermediate Part Design tools in FreeCAD** used to create more complex parametric models. It focuses on advanced additive and subtractive operations, feature transformations, dress-up operations, Boolean features, and reference geometry.

## Overview 

After the basic **Sketch → Pad/Pocket** workflow, FreeCAD provides several tools for creating more complex geometry and controlling how features interact with a model. This note introduces tools such as **Revolution, Pipe, Loft, Groove, Thickness, Draft, MultiTransform, Boolean operations, and Datum features**, along with their typical applications in parametric modeling.

## Helper Features

![[Part-Helper.png|875]]

- **New Body**: creates a Body object in the active document and makes it active.
- **New Sketch**
	- **New Sketch** – creates a new sketch on a selected face or plane.
	- **Attach Sketch** – attaches a sketch to geometry selected from the active body.
	- **Edit Sketch** – opens the selected sketch for editing.
- **Validate Sketch** – checks and adjusts the tolerance of points in a sketch.
- **Check Geometry** – checks selected objects for geometric errors.
- **Sub-Shape Binder** – creates a shape binder referencing geometry from other objects.
- **Clone** – creates a clone of the selected body.

## Additive Tools
**Additive tools** are used to **add material** to a Body and build up the solid geometry using operations such as revolution, sweeping, and lofting.

![[Part-Add.png]]

### Revolution
### Additive Loft
### Additive Pipe

## Subtractive Tools
**Subtractive tools** are used to **remove material** from an existing Body to create features such as grooves, channels, cavities, and other complex cuts.

![[Part-Subtract.png]]

### Hole
### Groove
### Subtractive Loft
### Subtractive Pipe

## Boolean
**Boolean tools** are used to perform **geometric operations between solid Bodies**, allowing multiple bodies to be combined or their volumes to be subtracted or intersected.

![[Part-Boolean.png]]

## Dress-Up Features
**Dress-Up features** are used to **refine and modify existing geometry**, primarily for improving edge geometry, manufacturability, and the final appearance of a model.

![[Part-Dress-Up.png]]

### Draft
### Thickness

## Transformation Features
**Transformation features** are used to **repeat, mirror, or reposition existing features** without having to recreate their geometry manually.

![[Part-Transform.png]]

### Linear Pattern
### Polar Pattern
### Multi-Transform

## Related Links
### Examples
### Notes
- [[Basic Tools & Settings]]
### External
- [Wiki|PartDesign Workbench](https://wiki.freecad.org/PartDesign_Workbench)
