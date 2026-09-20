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
Creates a solid by **revolving a sketch profile around a selected axis** through a specified angle. It is useful for creating rotationally symmetric parts such as shafts, discs, and flanges.

### Additive Loft
Creates a solid by **blending between two or more sketch profiles** positioned on different planes. It is useful for creating smooth, tapered, or irregularly shaped transitions.

### Additive Pipe
Creates a solid by **sweeping a sketch profile along a path**. It is commonly used for creating tubes, curved members, and other swept geometries.

## Subtractive Tools
**Subtractive tools** are used to **remove material** from an existing Body to create features such as grooves, channels, cavities, and other complex cuts.

![[Part-Subtract.png]]

### Hole
Creates a **parametric hole** in a solid based on a selected sketch point or geometry. It provides options for properties such as diameter, depth, threading, countersinking, and counterboring.

### Groove
Removes material by **revolving a sketch profile around an axis**. It is commonly used to create circular grooves, channels, and recesses.

### Subtractive Loft
Removes material by **lofting between two or more sketch profiles**. It is useful for creating tapered or smoothly transitioning cavities and cutouts.

### Subtractive Pipe
Removes material by **sweeping a sketch profile along a path**. It can be used to create curved channels, passages, and other swept cut features.

## Boolean
**Boolean tools** are used to perform **geometric operations between solid Bodies**, allowing multiple bodies to be combined or their volumes to be subtracted or intersected.

![[Part-Boolean.png]]

## Dress-Up Features
**Dress-Up features** are used to **refine and modify existing geometry**, primarily for improving edge geometry, manufacturability, and the final appearance of a model.

![[Part-Dress-Up.png]]

### Draft
Applies a **taper or angular deformation to selected faces** relative to a specified neutral plane. It is commonly used to create draft angles required for manufacturing processes such as injection molding.

### Thickness
Creates a **hollow shell from a solid** by removing selected faces and applying a specified wall thickness. It is useful for creating enclosures, housings, and thin-walled components.

## Transformation Features
**Transformation features** are used to **repeat, mirror, or reposition existing features** without having to recreate their geometry manually.

![[Part-Transform.png]]

### Linear Pattern
Creates multiple copies of a feature **along one or more linear directions** with a specified spacing and number of occurrences. It is useful for regularly spaced holes, slots, ribs, and similar features.

### Polar Pattern
Creates multiple copies of a feature **around a selected axis** at a specified angular spacing. It is commonly used for circular arrangements of holes, slots, or other repeated features.

### Multi-Transform
Combines **multiple transformation operations** to create complex patterns from an existing feature. It allows transformations such as linear patterns, polar patterns, mirroring, and other supported transformations to be applied together.

## Related Links
### Examples
### Notes
- [[Basic Tools & Settings]]
### External
- [Wiki|PartDesign Workbench](https://wiki.freecad.org/PartDesign_Workbench)
- [Wiki|PartDesign Revolution](https://wiki.freecad.org/PartDesign_Revolution)
