---
layout: single
---

## Good model practices & techniques

Surfacing _is_ hard! So don't worry if the first result is not 100% there where you want it.

### Golden Rule
Garbage in, garbage out.  
Sounds harsh, but it's true. Take good care of your work and stay as precise as needed while keeping your control point structure as clean as possible.

### Fillet vs Blend
If you encounter really sophisticated problems avoid `_FilletEdge` and give `_BlendEdge` a try. While it has its own quirks, it creates the right control point structure end to end.

If you notice that a blended surface needs many control points to properly fit to an edge, you should use [`_MatchSrf`](https://docs.mcneel.com/rhino/6/help/en-us/commands/matchsrf.htm) with the `CurveNearSurface` option, which is overlookey by many users, since it implies the requirement of a curve. However by pressing Enter before selecting the target surface you skip the curve selection step. This lets you directly match the surfaces.

### Weights
A good surface model ideally should **not** contain any weighted surfaces, since this leads to further problems down the stream. The most dominant reason is the difficulty of matching to weighted geometry.

### Modifying Surface Structures
Helpful commands include `_Rebuild` surface and `_RebuildUV`, as well as `_InsertKnot`/`_RemoveKnot` + `_InsertControlPoint`/`_RemoveControlPoint`. [Knots](http://help.mcneel.com/en/rhino/5/level1/06-point-editing) aren't points, but _parameters_ (see also [a more technical explanation](https://www.rhino3d.com/nurbs)).

Rhino tends to keep its geometry mathematically accurate, at the cost of making the model heavier. Also it might introduce "wobblyness": surfaces not being visually pleasing. Not to speak of possible complications down the road when having an abundance of control points.  
Fully using the native tolerance everywhere might lead to an excessive amount of control points and you should refrain from using an even tighter tolerance locally, if you aren't 100% sure what you're doing.

Also stay from `_NetworkSrf`: It looks like you can just cram a lot of input into there and it will provide you with a magical solution. However the results won't be satisfying. Most times you think you are in need of Network Surface it is best to split the task into a polysurface.

### Join or Merge?
Often enough there is some confusion between the terms "merge" and "join" going on. The words have similar meanings in common English but in Rhino they have specific and different meanings.

In Rhino to _merge_ two surfaces means to create a _single surface_ with a single common UV domain and set of control points which has exactly the same geometry as the two surfaces it was created from. Surfaces can only be merged along untrimmed, full length edges.

In Rhino to _join_ surfaces means to create a polysurface from two or more surfaces. The UV domain and control points of each surface are retained and stay seperate. A polysurface is considered as a single object, but can be exploded. Surfaces can be joined along trimmed edges.
The `_Join` command will actually pull edges from surfaces together if they are _within tolerance_.

### Looks
Use `_Zebra` and `_Emap` to have a quick visual view of how smooth your surface will join. To display a meaningful zebra analysis for high curvature surfaces, the underlying mesh resolution needs to be fine enough. In these situations the `adjust mesh` option in Rhino's Zebra analysis dialogue helps.