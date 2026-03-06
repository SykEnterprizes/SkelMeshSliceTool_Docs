## Capping Menu Overview

Once valid edge loops are detected, the Capping Menu becomes available.

This menu creates one Cap widget per-edgeloop, and the options in the widget control how open mesh boundaries are sealed.

What Capping Does
---
Capping:
- Seals open geometry
- Generates interior surfaces
- Optionally creates gore or organic surfaces
- Prevents rendering and physics issues

Capping is optional, but strongly recommended for:
--
- Animated limbs
- Physics-enabled meshes
- Gore effects

Cap Selection
---
Each detected edge loop can be capped independently.

This allows:
- Multiple cuts on a single mesh
- Selective capping
- Different cap styles per cut

## Cap Geometry Controls

Controls that affect how end-cap and extension geometry is generated and skinned

Fade Controls
---
This adds fade rings to the edgeloop, allowing the mesh to be extended, and a gore material to the added geometry 

- Add Fade Rings is a toggle to enable the ring generation
- Use Bone Axis Or Computed Normal determines the normal used in the extension direction
- Fade length sets how far the mesh can extend
- Fade Collapse Amount sets how much the leading edge of the FadeRings can collapse toward the computed edgeloop center
- Fade Ring Amount sets how many intermediate loops are added between the original edgeloop and the first Fade Ring, allowing higher-detail deformation when noise is enabled.

Useful for:
- If end caps need to be extended, constricted or flared for effect

Noise Controls
---
This adds organic noise to all generated cap geometry

- Add Noise enables the noise generation
- Noise Amount sets the strength of the applied noise

Useful for:
- Organic looking cuts

Soft tissue surfaces

Dome Controls
---
End caps may be a standard Fan Cap with one center point, or a more organic Dome style

- Cap Type selects between Fan Cap and Dome Cap
- Dome Hieght changes how far the dome protrudes from, or retracts into the generated mesh
- Inner Ring Number sets how many inner rings are added to the dome.  It allows noise to affect the mesh more dramatically
  
Useful for:
- Organic Gore appearance

Bridging  Controls
---
This joins two edgeloops together, creating a bridge of geometry

- Toggle Bridge Edgeloops enables the bridging
- Loop To Bridge To, selects a valid loop the current loop will bridge to

Useful for:
- Meshes with low weight thresholds that have gaps in betwen edge loops (eg: joint vertices missing between bones in a chain)

Skinning Type
---
This is the type of skinning applied to the generated cap geometry

- Skinning Type selects between Rigid bind and proximity Bind.
  - Rigid Bind assigns all generated vertices full weight to the caps associated bone
  - Proximity Bind assigns blended weights between the chain's root bone, and the root bones parent 

Useful for:
- Adjusting visual discrepancies under animation with overlapping generated meshes

Cap UV Controls
---
This adjusts the UVs on the generated cap and fade-ring geometry

- UV Scale adjusts the scale/tiling of the UVs
- UV Rotation Degrees adjusts the rotation of the added texture/material on the geometry
- UV Offset Amount allows for the texture/material to be moved around on the geometry

Useful for:
- Adjusting the positioning and visuals of the material applied to the generated cap geometry

Reverse Cap Options
---
This allows for a reverse cap to be generated to compliment the created cap. 

i.e a cap and reverse cap that fit together in a socket fashion

All controls in this section work the same as the FadeRing Controls

Useful for:
- Creating a gib mesh that complements a generated cap mesh.  
- Attach to a mesh socket, hide the bone and unhide the gib for a quick, inexpensive gore effect

Reverse Cap UV Controls
---
This allows the UVs to be adjusted on the Reverse Cap texture/material

All controls in this section work the same as the Cap UV Controls

Useful for:
- Adjusting the UVs on the generated gib, to give randomised gore visuals

Cap Material
---
The material applied to the generated cap geometry

Note - if no material is selected, the default used will be Material element 0 of the source base mesh

Fade-Ring Material
---
The material applied to the Fade-Ring geometry

Note - if no material is selected, the default used will be Material element 0 of the source base mesh
