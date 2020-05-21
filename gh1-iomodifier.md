---
layout: single
source: https://www.grasshopper3d.com/forum/topics/what-are-the-icons-on-a-component-s-input-output-parameter
---

## I/O Modifier

![](/img/gh1/iomods.png)

| icon | name |
| ---  | --- |
| ![](/img/icons/gh/io/Degrees.png)        | [Degrees](#degrees-) |
| ![](/img/icons/gh/io/Expression.png)     | [Expression](#expression-) |
| ![](/img/icons/gh/io/Flatten.png)        | [Flatten](#flatten-) |
| ![](/img/icons/gh/io/Graft.png)          | [Graft](#graft-) |
| ![](/img/icons/gh/io/Invert.png)         | [Invert](#invert-) |
| ![](/img/icons/gh/io/Principal.png)      | [Principal](#principal-) |
| ![](/img/icons/gh/io/Reparameterize.png) | [Reparameterize](#reparameterize-) |
| ![](/img/icons/gh/io/Reverse.png)        | [Reverse](#reverse-) |
| ![](/img/icons/gh/io/Simplify.png)       | [Simplify](#simplify-) |


The I/O modifiers can be applied to the inputs and outputs of a compononent by right clicking on it. By the exception of "Principal" and "Reparameterize" all items in the context menu have a dedicated Grasshopper component, which work in the same manner. Hovering over a modifier will give you a tooltip explaining its function.


While most functions might be clear, some are more obscure.

### Degrees ![](/img/icons/gh/math/Degrees.png)
The Degrees input modifier indicates that the numbers received are actually measured in \[Degrees\] ![](/img/icons/gh/math/Degrees.png) rather than Radians. Think of it more like a preference setting for each angle input on a Grasshopper Component that state you prefer to work in Degrees. There is no output option as this is only available on Angle inputs.

### Expression ![](/img/icons/gh/io/Expression.png)
The Expression I/O modifier allows you to change the input value by evaluating an expression such as `-x/2` which will have the input divided by 2 and made negative. If you hover over the tag a tooltip will be displayed with the expression. On some components it can also be used as output modifier, but it is uncommon to actually do that. (_Note that you always use `x` instead of the input parameter name._)  
Works like the \[Expression\] ![](/img/icons/gh/math/Expression.png) component.

### Flatten ![](/img/icons/gh/io/Flatten.png)
The Flatten I/O modifier will collapse a multi-path tree down to a single list on the `{0}` path, excatly like the \[Flatten Tree\] ![](/img/icons/gh/sets/Flatten_Tree.png) component.

### Graft ![](/img/icons/gh/io/Graft.png)
The Graft I/O modifier will create a new branch for each individual item in a list (or lists), exactly like the \[Graft\] ![](/img/icons/gh/sets/Graft_Tree.png) component.

### Invert ![](/img/icons/gh/io/Invert.png)
The Invert input modifier works in a similar way to a \[Not Gate\] ![](/img/icons/gh/math/Gate_Not.png) in boolean logic negating the input. A good example of when to use this is on \[Cull Pattern\] ![](/img/icons/gh/sets/Cull_Pattern.png) where you wish to invert the logic to get the opposite results. There is no output option as this is only available on Boolean inputs.

### Principal ![](/img/icons/gh/io/Principal.png)
The Principal input modifier is possibly the most obscure in this set. An input set to Principal is designated the major input of a component for the purposes of path assignment. This is important if you need to preserve the tree structure.

### Reparameterize ![](/img/icons/gh/io/Reparameterize.png)
The Reparameterize input modifier will only work on lines, curves and surfaces forcing the domains of all geometry to the `[0.0 to 1.0]` range, which is very helpful if you want to work in generalized manner; e.g. `0.5` should always yield the midpoint of a curve.

### Reverse ![](/img/icons/gh/io/Reverse.png)
The Reverse I/O modifier will reverse the order of a list (or lists in a multiple path structure), similiar to the \[Reverse List\] ![](/img/icons/gh/sets/ListReverse.png).

### Simplify ![](/img/icons/gh/io/Simplify.png)
The Simplify I/O modifier will remove the overlap shared amongst all branches, like \[Simplify Tree\] ![](/img/icons/gh/sets/Simplify_Tree.png) (_Note that a single branch does not share any overlap with anything else._)  
Simplifiy does not seem to work? You might encounter a "bug" here, which can't be changed for the life of Grasshopper 1: Some components will _graft_ their ouput and even throwing the Simplify modifier on it will result in a tree of `{0;0}` – not what we expected! Instead use the \[Suirify\] ![](/img/icons/gh/io/Simplify.png) component residing under `Params > Util`.  
<sub>See also [this post](https://discourse.mcneel.com/t/simplify-option-needs-to-get-universal/70311).</sub>