## Core Concepts

### Bone Chains

A Bone Chain is a contiguous hierarchy of bones selected from the source Skeleton
(e.g. upperarm → lowerarm → hand, or spine_01 → spine_03).

During extraction, vertices are evaluated based on how strongly they are influenced
by bones within the selected chain. Only vertices that meaningfully belong to the
chain are included in the resulting mesh.

Bone chains allow limbs and body sections to be extracted in a way that preserves
animation compatibility, rather than relying on spatial cuts alone.

### Weight Threshold

The Weight Threshold defines the minimum skin weight a vertex must have from the
selected bone chain in order to be included in the extracted mesh.

Higher values are more permissive and include more vertices, while lower values
are more restrictive and may exclude transitional vertices near joints or edge
loops, potentially creating holes if set too low.

The value is evaluated in the context of Unreal’s skin weight range (0–255),
where values closer to 255 require stronger influence from the chain.

If no vertices meet the threshold, extraction will fail due to insufficient vertex data.


### Cut Plane Tool

As an alternative to bone-chain-only extraction, the Cut Plane Tool allows a
user-defined plane to influence which vertices are included.

This is useful for custom separation boundaries that do not align cleanly with
bone hierarchies, such as mid-bone cuts or stylized dismemberment.

The Cut Plane Tool complements bone-chain extraction rather than replacing it.

### Resulting Meshes

Extracted meshes can be generated as:

- Skeletal meshes compatible with Master Pose
- Partial skeleton props
- Gore-capped limb meshes
- Physics-ready assets with generated collision

All resulting meshes preserve bind pose alignment with the source Skeletal Mesh.

