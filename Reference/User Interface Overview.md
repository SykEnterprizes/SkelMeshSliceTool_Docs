## User Interface Overview

The Limb Extraction Tool UI is intentionally divided into stages, each corresponding to a step in the extraction workflow.
Controls are shown or hidden based on the selected extraction mode to reduce clutter and prevent invalid operations.

There are also Pop-Up prompts in case of user error, stating what what step is missed

## Extraction Mode Selector

At the top of the tool is the Extraction Mode selector.

- This determines how vertices are selected before mesh generation.

Available Modes
---
- Bone Chain Extraction
- Cut Plane Extraction

Changing modes will:
---
- Show or hide relevant controls
- Reset mode-specific state
- Prevent incompatible options from being active at the same time

Skeletal Mesh Selection
---
The Skeletal Mesh picker defines the source mesh used for extraction.

Once a mesh is selected:
---
- The skeleton hierarchy becomes available
- Bone chains can be selected (Bone Chain mode)
- Bones can be Excluded from a chain (eg: exclude fingers on a lower-arm->hand chain)
- The Cut Plane Tool can be spawned (Cut Plane mode)

Note
The skeleton tree may be collapsed or hidden after selection to keep the UI focused on extraction controls.

Weight Threshold Controls
---
Weight Thresholding controls how strictly vertices must be weighted to the selected bones in order to be included.

What the Threshold Does
---
Vertices with lower influence than the threshold are discarded

This applies to BoneAndWeight etraction only, with UseMasterPose = false

It affects both primary mesh vertices and transitional edge regions

Practical Effects:
Lower values - 
More aggressive filtering
→ Fewer vertices
→ Can introduce holes near joints or cut boundaries

Higher values - 
More permissive
→ More complete meshes
→ Cleaner results for most cases

This control is especially important near edge loops and cut boundaries.

Final Mesh Setup options
---
Controls to change what type, and what features the final mesh will have

- Modular meshes or Partial skeletons
- Singular bone extraction or bone chain extraction
- Select Morph targets to be extracted and applied
- Auto-Skinweighting of the final mesh
- Extract as a static mesh or a skeletal mesh
- Prune influences and normalize weights to Unreals influence MAX of 4
  
Edge Loop Detection & Filtering
---
After vertices are extracted, the system identifies open edge loops along the cut boundary.

Edge loops are used for:
- Procedural mesh capping
- Gore surface generation
- Preventing open or broken geometry

Edge Loop Filtering
---
Not all detected loops are suitable for capping.

The tool filters loops based on:
- Size
- Shape consistency
- Vertex count

This is necessary because:
- Large meshes can generate dozens of micro-loops
- Too many loops can severely impact performance while waiting for the menu to populate
  
The capping system operates synchronously

Important - 
Excessive edge loops may cause the editor to appear frozen during processing.

Filtering is designed to:
- Keep only meaningful loops
- Maintain predictable capping behavior
- Prevent UI lockups (Safe guards are now in place in the UI)

Capping Menu Overview
---
Once valid edge loops are detected, the Capping Menu becomes available.

This menu controls how open boundaries are sealed.

Capping Options Include:
- Cap generation per edge loop
- Cap resolution and smoothing
- Gore surface generation
- Normal direction control
- Material assignment

Each option is designed to work independently, allowing:
- Clean mechanical cuts
- Organic gore caps
- Hybrid results

Capping is optional — meshes can be generated uncapped if desired.

Generate Mesh
---
The Generate Mesh button performs the final build step.

This includes:
- Vertex remapping
- Skin weight normalization
- Skeletal mesh construction
- Optional capping
- Optional auto-skinweighting

Warning
Mesh generation is an editor-time operation and may take several seconds depending on mesh complexity.

Merge / View
---
After generation:
- Extracted meshes can be previewed
- Merged meshes can be inspected 
- Results can be validated and tested with animation/deformation before saving
- Physics asset generation (if enabled)

This step is separated intentionally to allow iteration without regenerating meshes unnecessarily.

