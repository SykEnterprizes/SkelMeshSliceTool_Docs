## CutPlaneTool Controls

The CutplaneTool has only 3 editable controls to reduce User confusion

The basic use of the CutPlaneTool is to position the Red box over the desired mesh to extract

Plane Radius
---
- This directly changes the size of the plane equally in in its axis
- The size is applied to the Miror Plane if enabled, and will be of equal size to the initial plane
- Sizing is in Unreal cm units

Extraction Depth
---
- This changes the depth of the Red Extraction Box, giving a direct visual cue to how much mesh 
  will be extracted
- The depth is equal in size on the Mirror Plane if enabled
- The Extraction Box directly shows the User how much mesh will be considered for extraction and can be moved or rotated as desired
- Sizing is in Unreal cm units

Tolerance
---
- Tolerance controls how forgiving the Cutplane Tool is when detecting where the slicing plane intersects the mesh.
- In practice, it defines a thickness zone around the cutplane within which vertices, edges, and intersection points are considered valid.
- The default value is 0.2, which is tuned to work well with typical UE-scale character meshes.

Think of tolerance as:
- “How thick the knife blade is when slicing the mesh.”

A razor-thin blade (low tolerance) is precise but unforgiving.
A thicker blade (higher tolerance) is forgiving but less exact.

What Tolerance Affects
---
Tolerance influences the Cutplane Tool in three key ways:

1. Plane Thickness (Intersection Detection)

- The cutplane is not treated as an infinitely thin mathematical plane.
  Instead, it behaves like a thin slab centered on the plane.
- Any geometry whose vertices fall within this slab is considered eligible for intersection testing.

Lower tolerance: 
- Thinner slab
- Requires geometry to be very close to the plane
- Can miss intersections on dense or uneven meshes

Higher tolerance:
- Thicker slab  
- More forgiving intersection detection
- Can include extra or noisy geometry if pushed too far

This is especially important for meshes with:
- Slightly uneven topology
- Non-uniform triangle sizes
- Skinned meshes that are not perfectly planar at the cut

2. Edge Crossing Detection

When testing triangle edges, tolerance indirectly controls how reliably an edge is considered to cross the plane.

Edges are only treated as valid crossings if:
- One vertex is on each side of the plane
- The intersection point falls within the plane bounds
- A tolerance that is too small may cause:
- Missed crossings
- Broken or incomplete edgeloops

A tolerance that is too large may cause:
- Multiple intersections per edge
- Extra points near corners or folds

3. Point Deduplication

After intersection points are found, tolerance is used again to merge nearby points into a single point.

This prevents:
- Duplicate vertices from shared edges
- Very small numerical differences producing broken loops

If tolerance is too low:
- Nearly identical points are treated as unique
- Edgeloops can zig-zag or self-intersect

If tolerance is too high:
- Legitimate nearby points may collapse together
- Loop detail can be lost

Recommended Usage - 

Default (0.2)
Works well for most humanoid characters at UE scale.

Increase tolerance if:
- No edgeloop is generated
- The loop is incomplete or broken
- The mesh has uneven density or noisy topology

Decrease tolerance if:
- Too many points are generated
- The loop includes geometry far from the intended cut
- Fine, precise cuts are required

Create Mirror Cut 
---
This creates a plane that mirrors the initial plane

Recommended Usage:
- Use when something from each side of a mesh need to be included in the final mesh (eg: both hands for a modular mesh setup)

Only set to true if a mirrored cut is required or it may produce undesired results
