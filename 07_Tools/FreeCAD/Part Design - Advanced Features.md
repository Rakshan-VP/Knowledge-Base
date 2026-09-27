#type/method #domain/CAD #status/completed #scope/intermediate
> [!abstract] Summary 
> This note covers the **intermediate Part Design tools in FreeCAD** used to create more complex parametric models. It focuses on advanced additive and subtractive operations, feature transformations, dress-up operations, Boolean features, and reference geometry.

## Overview 

After the basic **Sketch → Pad/Pocket** workflow, FreeCAD provides several tools for creating more complex geometry and controlling how features interact with a model. This note introduces tools such as **Revolution, Pipe, Loft, Groove, Thickness, Draft, MultiTransform, Boolean operations, and Datum features**, along with their typical applications in parametric modeling.

**FreeCAD Version : 1.1.3**

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

![[Revolute.png]]

| **Parameter**      | **Description**                                                                      |
| ------------------ | ------------------------------------------------------------------------------------ |
| **Profile**        | Selects the sketch or closed geometry that will be revolved to create the solid.     |
| **Axis**           | Defines the axis around which the profile is revolved.                               |
| **Angle**          | Sets how far the profile is revolved around the axis, typically from `0°` to `360°`. |
| Reversed           | Reverses the direction of the revolution.                                            |
| Symmetric to plane | Revolves the profile equally on both sides of the selected plane.                    |
| Midplane           | Centers the revolution around the selected plane.                                    |

### Additive Loft
Creates a solid by **blending between two or more sketch profiles** positioned on different planes. It is useful for creating smooth, tapered, or irregularly shaped transitions.

![[AdditiveLoft.png]]

| **Parameter**         | **Description**                                                                                       |
| --------------------- | ----------------------------------------------------------------------------------------------------- |
| **Sections**          | Selects the two or more sketch profiles between which the solid is created.                           |
| **Transition**        | Controls how the geometry transitions between the selected profiles.                                  |
| Ruled                 | Creates straight, ruled surfaces between the sections instead of smoothly transitioning between them. |
| Closed                | Closes the loft by connecting the last section back to the first section.                             |
| Allow multiple solids | Allows the operation to create multiple solids when the loft does not connect to the existing Body.   |

### Additive Pipe
Creates a solid by **sweeping a sketch profile along a path**. It is commonly used for creating tubes, curved members, and other swept geometries.

![[AdditivePipe.png]]

| **Parameter** | **Description** |
|---|---|
| **Profile** | Selects the sketch that defines the cross-section of the solid being swept. |
| **Spine** | Defines the path along which the profile is swept. |
| Auxiliary Spine | Provides an additional path to control the orientation or shape of the swept profile. |
| Corner Transition | Controls how the pipe transitions through corners in the path. |
| Transition | Controls how the profile is oriented as it follows the path. |
| Frenet | Keeps the profile orientation aligned with the curvature of the path. |
| Make Solid | Creates a solid from the swept geometry when the profile forms a closed section. 

## Subtractive Tools
**Subtractive tools** are used to **remove material** from an existing Body to create features such as grooves, channels, cavities, and other complex cuts.

![[Part-Subtract.png]]

### Hole
Creates a **parametric hole** in a solid based on a selected sketch point or geometry. It provides options for properties such as diameter, depth, threading, countersinking, and counterboring.

![[Hole.png]]

| **Parameter**     | **Description**                                                                                            |
| ----------------- | ---------------------------------------------------------------------------------------------------------- |
| **Profile**       | Selects the sketch or points that define the hole locations.                                               |
| **Hole Cut Type** | Defines the hole style, with options such as **Simple**, **Counterbore**, and **Countersink**.             |
| **Diameter**      | Sets the nominal diameter of the hole.                                                                     |
| **Depth**         | Defines how deep the hole extends, with options such as **Dimension**, **Through all**, or **Up to face**. |
| Threading         | Enables a threaded hole and provides options for thread standard and size.                                 |
| Tapered           | Creates a tapered hole instead of a cylindrical hole.                                                      |
| Drill Point       | Defines the bottom geometry of the hole, with options such as **Angled** or **Flat**.                      |
| Drill Point Angle | Sets the angle of the drill tip when an angled drill point is used.                                        |

### Groove
Removes material by **revolving a sketch profile around an axis**. It is commonly used to create circular grooves, channels, and recesses.

![[Groove.png]]

| **Parameter**      | **Description**                                                      |
| ------------------ | -------------------------------------------------------------------- |
| **Profile**        | Selects the sketch that defines the material to be removed.          |
| **Axis**           | Defines the axis around which the profile is revolved.               |
| **Angle**          | Sets how far the profile is revolved, typically from `0°` to `360°`. |
| Reversed           | Reverses the direction of the groove operation.                      |
| Symmetric to plane | Revolves the profile equally on both sides of the selected plane.    |
| Midplane           | Centers the groove operation around the selected plane.              |

### Subtractive Loft
Removes material by **lofting between two or more sketch profiles**. It is useful for creating tapered or smoothly transitioning cavities and cutouts.

![[SubtractiveLoft.png]]

| **Parameter**  | **Description**                                                                                       |
| -------------- | ----------------------------------------------------------------------------------------------------- |
| **Sections**   | Selects the two or more sketch profiles between which material is removed.                            |
| **Transition** | Controls how the geometry transitions between the selected profiles.                                  |
| Ruled          | Creates straight, ruled surfaces between the sections instead of smoothly transitioning between them. |
| Closed         | Closes the loft by connecting the last section back to the first section.                             |

### Subtractive Pipe
Removes material by **sweeping a sketch profile along a path**. It can be used to create curved channels, passages, and other swept cut features.

![[SubtractivePipe.png]]

| **Parameter**     | **Description**                                                                       |
| ----------------- | ------------------------------------------------------------------------------------- |
| **Profile**       | Selects the sketch that defines the cross-section of the material to be removed.      |
| **Spine**         | Defines the path along which the profile is swept.                                    |
| Auxiliary Spine   | Provides an additional path to control the orientation or shape of the swept profile. |
| Corner Transition | Controls how the pipe transitions through corners in the path.                        |
| Transition        | Controls how the profile is oriented as it follows the path.                          |
| Frenet            | Keeps the profile orientation aligned with the curvature of the path.                 |

## Boolean
**Boolean tools** are used to perform **geometric operations between solid Bodies**, allowing multiple bodies to be combined or their volumes to be subtracted or intersected.

![[Part-Boolean.png]]

| **Operation** | **Description**                                                                       |
| ------------- | ------------------------------------------------------------------------------------- |
| **Fuse**      | Merges the selected tool body or bodies with the active body to form a single solid.  |
| **Cut**       | Subtracts the selected tool body or bodies from the active body.                      |
| **Common**    | Keeps only the volume shared by the active body and the selected tool body or bodies. |

![[BooleanOp.png]]

| **Parameter** | **Description** |
|---|---|
| **Base Body** | Defines the active body that is used as the primary body in the Boolean operation. |
| **Tool Bodies** | Selects the additional body or bodies used with the base body. |
| **Operation** | Defines the Boolean operation, with options **Fuse**, **Cut**, and **Common**. |

## Dress-Up Features
**Dress-Up features** are used to **refine and modify existing geometry**, primarily for improving edge geometry, manufacturability, and the final appearance of a model.

![[Part-Dress-Up.png]]

### Draft
Applies a **taper or angular deformation to selected faces** relative to a specified neutral plane. It is commonly used to create draft angles required for manufacturing processes such as injection molding.

![[Draft.png]]

| **Parameter**     | **Description**                                                         |
| ----------------- | ----------------------------------------------------------------------- |
| **Faces**         | Selects the faces to which the draft angle is applied.                  |
| **Neutral Plane** | Defines the reference plane about which the selected faces are drafted. |
| **Draft Angle**   | Sets the amount of taper applied to the selected faces.                 |
| Reversed          | Reverses the direction of the draft angle.                              |

### Thickness
Creates a **hollow shell from a solid** by removing selected faces and applying a specified wall thickness. It is useful for creating enclosures, housings, and thin-walled components.

![[Thickness.png]]

| **Parameter** | **Description**                                                                                           |
| ------------- | --------------------------------------------------------------------------------------------------------- |
| **Faces**     | Selects the faces to be removed to create the open side of the shell.                                     |
| **Thickness** | Defines the wall thickness of the resulting hollow solid.                                                 |
| **Mode**      | Controls how the thickness is applied, with options such as **Skin** and **Pipe**.                        |
| **Join Type** | Defines how the offset surfaces are joined at corners, with options such as **Arc** and **Intersection**. |
| Reversed      | Reverses the direction in which the thickness is applied.                                                 |

## Transformation Features
**Transformation features** are used to **repeat, mirror, or reposition existing features** without having to recreate their geometry manually.

![[Part-Transform.png]]

### Linear Pattern
Creates multiple copies of a feature **along one or more linear directions** with a specified spacing and number of occurrences. It is useful for regularly spaced holes, slots, ribs, and similar features.

![[Linearpattern.png]]

| **Parameter** | **Description** |
|---|---|
| **Original Feature** | Selects the feature or features to be repeated. |
| **Direction** | Defines the direction in which the feature is patterned. |
| **Occurrences** | Sets the total number of instances in the pattern. |
| **Length** | Defines the overall distance covered by the pattern. |
| Reversed | Reverses the direction of the pattern. |

### Polar Pattern
Creates multiple copies of a feature **around a selected axis** at a specified angular spacing. It is commonly used for circular arrangements of holes, slots, or other repeated features.

![[PolarPattern.png]]

| **Parameter**        | **Description**                                                        |
| -------------------- | ---------------------------------------------------------------------- |
| **Original Feature** | Selects the feature or features to be repeated.                        |
| **Axis**             | Defines the axis around which the feature is patterned.                |
| **Occurrences**      | Sets the total number of instances in the pattern.                     |
| **Angle**            | Defines the total angular range over which the pattern is distributed. |
| Reversed             | Reverses the direction of the angular pattern.                         |

### Multi-Transform
Combines **multiple transformation operations** to create complex patterns from an existing feature. It allows transformations such as linear patterns, polar patterns, mirroring, and other supported transformations to be applied together.

![[MultiTransform.png]]

| **Parameter**                 | **Description**                                                                                                                          |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Original Feature**          | Selects the feature or features to be transformed.                                                                                       |
| **Transformations**           | Defines the sequence of transformations applied to the selected feature, such as **Linear Pattern**, **Polar Pattern**, or **Mirrored**. |
| **Transformation Parameters** | Provides the parameters specific to each selected transformation.                                                                        |

## Related Links
### Examples
### Notes
- [[Basic Tools & Settings]]
- [[Parametric Modelling via Spreadsheets]]
### External
- [Wiki|PartDesign Workbench](https://wiki.freecad.org/PartDesign_Workbench)
- [Wiki|PartDesign Revolution](https://wiki.freecad.org/PartDesign_Revolution)
- [Wiki|PartDesign Additive Loft](https://wiki.freecad.org/PartDesign_AdditiveLoft)
- [Wiki|PartDesign Additive Pipe](https://wiki.freecad.org/PartDesign_AdditivePipe)
- [Wiki|PartDesign Hole](https://wiki.freecad.org/PartDesign_Hole)
- [Wiki|PartDesign Groove](https://wiki.freecad.org/PartDesign_Groove)
- [Wiki|PartDesign Subtractive Loft](https://wiki.freecad.org/PartDesign_SubtractiveLoft)
- [Wiki|PartDesign Subtractive Pipe](https://wiki.freecad.org/PartDesign_SubtractivePipe)
- [Wiki|PartDesign Boolean](https://wiki.freecad.org/PartDesign_Boolean)
- [Wiki|PartDesign Draft](https://wiki.freecad.org/PartDesign_Draft)
- [Wiki|PartDesign Thickness](https://wiki.freecad.org/PartDesign_Thickness)
- [Wiki|PartDesign Linear Pattern](https://wiki.freecad.org/PartDesign_LinearPattern)
- [Wiki|PartDesign Polar Pattern](https://wiki.freecad.org/PartDesign_PolarPattern)
- [Wiki|PartDesign Multi-Transform](https://wiki.freecad.org/PartDesign_MultiTransform)