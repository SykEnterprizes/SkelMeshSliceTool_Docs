## Edge Loop & Auto-Skinweight Controls

These controls directly affect mesh quality and are visible during normal use.
They are designed to help stabilize cut boundaries, improve capping results, and reduce manual cleanup.

Edge Loop Detection
---
After vertex extraction, the system scans for open boundaries in the generated mesh.

An edge loop is a continuous boundary of open edges created by:

Bone chain truncation

Cut Plane extraction

Weight threshold filtering

These loops define where caps may be generated.

## Edge Loop Validation (How Loops Are Accepted or Rejected)

After extraction, detected edge loops are validated before being exposed to the capping system.

This validation is designed to:

Reject degenerate or unstable topology

Prevent extremely small or broken loops

Avoid editor stalls caused by excessive invalid cap-data widgets

This process does not reshape or smooth loops — it only determines whether a loop is usable.

Validation Step 1: Minimum Vertex Count
---
Each edge loop must contain a minimum number of vertices.

This prevents:

Single-edge loops

Sliver geometry

Loops created by noise or isolated triangles

If a loop does not meet the minimum vertex count, it is discarded.

Validation Step 2: Minimum Circumference
---
The total length of the loop is calculated by summing the distance between consecutive vertices.

This ensures the loop represents a meaningful surface boundary, not a tiny artifact.

Loops with a circumference below the configured minimum are rejected.

This is especially important when:

Weight thresholds are aggressive

Mesh density varies significantly

Small protrusions exist near cut regions

Validation Step 3: Circularity Check (Optional)
---
An optional circularity test is used to detect irregular or malformed loops.

This check:

Computes the loop’s center point

Calculates the average radius from the center

Measures how much each vertex deviates from that average

If the loop:

Collapses toward a point

Has extreme deviation

Forms a highly irregular shape

…it is rejected.

This helps avoid:

Self-intersecting caps

Twisted or folded geometry

Unstable gore surfaces

Why Circularity Is Optional

Not all valid cuts are circular.

For example:

Spine cuts

Shoulder separations

Asymmetrical damage

Disabling circularity allows these shapes through, at the cost of potentially rougher caps.

What This System Does Not Do

It does not simplify or smooth loops

It does not modify vertex positions

It does not “fix” topology

It only determines whether a loop is safe to pass downstream to the capping stage.

## Practical Guidance

If no loops appear → reduce minimum circumference

If loops look broken → enable circularity check

If editor hangs → increase minimum vertex count

If asymmetrical cuts are rejected → disable circularity

## Auto Skin Weighting

Auto Skin Weighting recalculates skin weights on the extracted mesh to produce stable deformation after separation.

This is primarily used when:

Extracting partial bone chains

Removing shared vertices near joints

Creating clean limb props or master-pose compatible meshes

The system operates entirely at editor time and does not affect the source mesh.

Blend Zone Width
---
Controls the size of the transition area between bones.

Lower values

Tighter weighting

Harder transitions

Useful for clean limb breaks or rigid props

May introduce visible seams if too low

Higher values

Smoother blending across joints

Better deformation for animation

Can cause weight bleeding into nearby bones if pushed too far

Tip:
Increase this slightly if joints collapse or snap during animation.

Falloff Sharpness
---
Controls how quickly influence fades across the blend zone.

Lower values

Gradual weight transitions

Softer deformation

Better for organic movement

Higher values

Sharper transitions

More rigid behavior

Useful for gore cuts or mechanical separations

This does not change which bones influence a vertex — only how strongly they transition.

Hierarchy Falloff
---
Controls how much influence propagates through the bone hierarchy.

Lower values

Weights stay close to the target bone

Minimal parent/child bleed

Good for isolated limbs

Higher values

Influence spreads to parent and child bones

Smoother full-chain deformation

Useful for spine or multi-bone segments

This is especially important for spine and torso chains.

Filter MetaHuman Ancillary Bones
---
When enabled, automatically excludes non-deforming helper bones commonly found in MetaHuman skeletons.

This prevents:

Weight pollution from facial, twist, or helper bones

Unstable deformation after extraction

Excessively fragmented bone influence sets

Recommended:

Enabled for MetaHuman assets

Optional for custom skeletons, or if basic skinning is required, excluding helper bone influence

## When to Use Auto Skin Weighting

Enable Auto Skin Weighting if:

The extracted mesh collapses or stretches

Vertices snap toward a single bone

You are creating animated limb props

Source Mesh weights are not high quality

The source mesh used shared deformation across chains

You may disable it if:

The extracted mesh is rigid

You are creating static props

The original weights are already clean and isolated

Common Adjustment Patterns
---
Issue	Suggested Change
Hard seams at joints ->	Increase Blend Zone Width
Mushy deformation ->	Increase Falloff Sharpness
Chain deformation feels stiff -> Increase Hierarchy Falloff
MetaHuman weights look noisy ->	Enable Filter MetaHuman Ancillary Bones

Important Note
---
Auto Skin Weighting is not designed for meshes with extreme protrusions, such as:

Large hair clusters

Accessories intersecting limbs

Dense secondary geometry near joints

In these cases, manual thresholds or cut-plane extraction may produce better results.

Practical Guidance
---
If edge loops look uneven → adjust Loop Size Threshold

If the capping menu becomes slow → reduce Loop Count Limit

If animation looks broken → enable Auto-Skinweighting

If joints look mushy → reduce Influence Radius

