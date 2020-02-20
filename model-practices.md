---
layout: single
---

## Good model practices & techniques

Surfacing _is_ hard! So don't worry if the first result is not 100% there where you want it.

### Fillet vs Blend
If you encounter really sophisticated problems avoid `_FilletEdge` and give `_BlendEdge` a try. While it has its own quirks, it creates the right control point structure end to end.

### Weights
A good surface model ideally should not contain any weighted surfaces, since this leads to further problems down the stream. The most dominant reason is the difficulty of matching to weighted geometry.

### Looks
Use `_Zebra` and `_Emap` to have a quick visual view of how smooth your surface will join. To display a meaningful zebra analysis for high curvature surfaces, the underlying mesh resolution needs to be fine enough. In these situations the `adjust mesh` option in Rhino's Zebra analysis dialogue helps.
