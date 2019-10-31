Building a nice G1 or G2 blend surface
 between two input surfaces that don’t intersect together is very easy by using curves drawn on those surfaces, then building a “Loft surface” between the two curves, followed by “Match surface” with the “CurveNearSurface=On” option. Here is a short turotial:

is there an advantage in doing this in comparison to
split at isocurve and then blendsurface?

in many cases blendsurface creates way too many control points.

Also, if you Loft and MatchSrf to extracted isocurves on the surface (CurveNearSurface=On) and use History, you can MoveExtractedIsocurve and slide the blend around to get the shape right. Unfortunately this (History on MatchSrf) only works on one side at a time.