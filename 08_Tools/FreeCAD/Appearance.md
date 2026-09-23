#type/method #domain/CAD #status/completed #scope/fundamental
> [!abstract] Summary 
> This note covers the **Shape Appearance** properties in FreeCAD (introduced in FreeCAD 1.0/newer versions), detailing how six core material attributes control light interaction and surface aesthetics.

## Overview
FreeCAD features a refactored material and appearance system where the old single "Shape color" property is expanded into **six appearance properties** located under the `View properties -> Object Style` group (`Shape Appearance` umbrella). 

Alternatively, access them via the **Appearance task panel** (`Ctrl+D`) and the **Material Properties** dialog.

## Shape Appearance Properties

### Diffuse Colors
Controls the surface's base color under direct illumination, scattering light evenly across all angles.

![[Appearance_Diffuse.png]]

* **Sphere 1 (`#FF0000`):** Bright Red
* **Sphere 2 (`#00FF00`):** Bright Green
* **Sphere 3 (`#0000FF`):** Bright Blue
* **Sphere 4 (`#FFD700`):** Gold

### Ambient Colors
Controls the surface color under indirect, uniform lighting, influencing how shadowed areas appear. (Base Diffuse: `#FF0000`)

![[Apperance_Ambient.png]]

* **Sphere 1 (`#555555`):** Default Gray Ambient (Standard look)
* **Sphere 2 (`#C80000`):** Darker Red Shade (Richer, realistic shadow)
* **Sphere 3 (`#000000`):** Pure Black (Harsh, deep shadows)
* **Sphere 4 (`#0000FF`):** Cool Blue Tint (Contrasting indirect tone)

### Specular Colors
Controls the color and intensity of bright, mirror-like highlights on shiny surfaces. (Fixed Base Diffuse: `#3366CC`)

![[Appearance_Specular.png]]

* **Sphere 1 (`#333333`):** Dark Gray Specular (Matte finish, low reflection)
* **Sphere 2 (`#808080`):** Medium Gray Specular (Standard semi-gloss sheen)
* **Sphere 3 (`#FFFFFF`):** Pure White Specular (High-gloss plastic shine)
* **Sphere 4 (`#FFD700`):** Gold Tint Specular (Colored metallic reflection look)

### Emissive Colors
Controls the color of a surface that appears to emit light, creating a self-illuminated illusion. (Fixed Base Diffuse: `#101010`)

![[Appearance_Emissive.png]]

* **Sphere 1 (`#000000`):** Pure Black (No emission, standard surface)
* **Sphere 2 (`#FF6400`):** Bright Orange Glow (Warm self-illumination effect)
* **Sphere 3 (`#00FFFF`):** Bright Cyan Glow (Neon-style light emission)
* **Sphere 4 (`#FFFFFF`):** Pure White Glow (Intense self-illuminated look)

### Shininess
Controls the size and sharpness of specular highlights on a surface (using default diffuse).

![[Apperance_Shininess.png]]

* **Sphere 1 (`10%`):** Broad and soft specular highlight.
* **Sphere 2 (`40%`):** Moderate highlight size.
* **Sphere 3 (`70%`):** Small and sharp highlight.
* **Sphere 4 (`90%`):** Extremely sharp, pinpoint highlight.

### Transparency
Controls how much light passes through an object for see-through opacity (using default diffuse).

![[Apperance_Transparency.png]]

* **Sphere 1 (`0%`):** Fully opaque surface.
* **Sphere 2 (`30%`):** Slight see-through opacity.
* **Sphere 3 (`70%`):** Highly transparent surface.
* **Sphere 4 (`100%`):** Fully transparent (invisible) surface.

> [!tip] Quick Workflow
> For most general use cases, setting the **Diffuse Color** (for base color) and adjusting the gray value of the **Specular Color** (for reflectivity) is fully sufficient.

## Related Links
### Notes
- [[Basic Tools & Settings]]
- [[Part Design - Advanced Features]]
### External
- [FreeCAD Blog|Explainer:Appearance Properties in FreeCAD](https://blog.freecad.org/2025/11/09/explainer-appearance-properties-in-freecad/)
- [FCB Lounge|Appearance Properties in FreeCAD Explained](https://www.youtube.com/watch?v=oN-oO3bn8Qw)