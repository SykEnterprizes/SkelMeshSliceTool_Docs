## Morph Target Preservation
Morph Target Preservation is an option where the user can extract morph targets from the source mesh
and have them apply to the extracted mesh

Only relevant morphs are applied to the extracted mesh so irrelevant morphs do not appear in the mesh details

Morph target extraction, and application to the extracted mesh are dependant on a higher level of
Vert Weight Strength during extraction

Higher values:
- extract more of the source mesh selected bone/chain vertices
- extract higher quality morph deltas (if enabled) due to a more complete relevant mesh section
- apply the morphs more accurately (if enabled) due to having more relavant vertices to map to

Lower values:
- extract less of the source mesh selected bone/chain vertices
- extract lower quality morph deltas (if enabled) due to incomplete mesh sections
- apply the morphs less accurately (if enabled) due to having less relavant vertices to map to
 
Useful for:
---
Modular meshes that require morphs such as faces, or body adjustments like muscle sze etc

Important Note:
---
Morphs cannot be mapped to cap geometry with the tool

Using morphs with capped meshes may cause artifacts during animation/deformation

