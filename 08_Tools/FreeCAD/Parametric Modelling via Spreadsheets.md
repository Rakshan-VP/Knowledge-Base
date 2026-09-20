#type/method #type/example #domain/CAD #status/learning #scope/advanced
> [!abstract] Summary 
> This note covers **parametric design using spreadsheets** in FreeCAD. Dimensions are stored as named variables in one spreadsheet, so changing a value updates the model automatically.

## Overview
In parametric design, a model's dimensions are linked to named parameters rather than typed in as fixed numbers. This note builds a **box** whose **length, breadth and height** are controlled from a FreeCAD spreadsheet. The same method scales to any part with many dimensions. 

**FreeCAD Version : 1.1.3**

We will: 
- Store the three dimensions in a spreadsheet and give each one an **alias**. 
- Create a box and link its dimensions to those aliases. 
- Change a value in the spreadsheet and watch the box resize.

## Methodology

1. In the **Workbench selector**, switch to **Spreadsheet** and click **Create spreadsheet**. Rename it to `Params` (select it in the tree and press `F2`).
2. Open the sheet and enter the values below in cells **A1:B3**. You can copy and paste them as they are.

   | A       | B     |
   | ------- | ----- |
   | Length  | 50 mm |
   | Breadth | 30 mm |
   | Height  | 20 mm |

3. Select each value cell in column **B**, then go to **Properties → Alias** and enter the matching name from column **A** (`Length`, `Breadth`, `Height`). Recompute with `Ctrl+R`.

	![[ParamModel_Step1.png]]
	
4. Switch to the **Part Design** workbench, create a **Body**, then add **Additive Primitive → Box**. The box's **Length**, **Width** and **Height** fields appear in the dialog.

	![[ParamModel_Step2.png]]
	
5. Click the **`f(x)`** (expression) button next to each value and enter:

	```text
	   Length  →  <<Params>>.Length
	   Width   →  <<Params>>.Breadth
	   Height  →  <<Params>>.Height
	```

6. Click **OK**. The box is now built from the spreadsheet values.
7. Go back to the spreadsheet and change **Height** to `40 mm`, then recompute. The box updates to the new height.

	![[ParamModel_Step3.png]]

> [!NOTE] Alias rules
> An alias **cannot contain spaces** or start with a number, and it cannot clash with a unit name (e.g. `mm`). Use names like `Length` or `box_width`.

> [!TIP] Formulas also work
> You can also write formulas, not just values, e.g. `<<Params>>.Length / 2` or `<<Params>>.Breadth * 2 + 5 mm`. In spreadsheet cells, use aliases directly, e.g. `=Length / 2`. This lets one value drive others, such as making **Height** always half of **Length**.


## Related Links
### Examples
### Notes
- [[Basic Tools & Settings]]
- [[Part Design - Advanced Features]]
### External