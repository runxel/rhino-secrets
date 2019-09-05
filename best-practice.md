# Good model practices

Surfacing is hard! So don't worry if the first result is not 100% there where you want it.

### Fillet vs Blend
If you encounter really sophisticated problems avoid `_FilletEdge` and give `_BlendEdge` a try. While it has its own quirks, it creates the right control point structure end to end.

### Weights
A good surface model ideally should not contain any weighted surfaces, since this leads to further problems down the stream. The most dominant reason is the difficulty of matching to weighted geometry.

### Looks
Use `_Zebra` and `_Emap` to have a quick visual view of how smooth your surface will join. To display a meaningful zebra analysis for high curvature surfaces, the underlying mesh resolution needs to be fine enough. In these situations the "adjust mesh" option in Rhino's Zebra analysis dialogue helps.

----

One “old-timer’s” trick to deal with singularities (edges collapsed to a point) is to select the point and use _Smooth - have “fix boundaries” unchecked, and give it some pretty small tolerance value like your file tolerance. It will “unstick” the collapsed points and create a tiny edge that has the same UV structure as the rest of the surface so that it really is a 4-edged surface. You do need to be careful what actually happens at that edge later, but it can make some things work that didn’t before.

---
https://knowledge.autodesk.com/support/alias-products/getting-started/caas/CloudHelp/cloudhelp/2019/ENU/Alias-Tutorials/files/GUID-21501AEB-9E7A-4F9F-A0B3-0A4B3431B9BD-htm.html