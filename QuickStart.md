## Quick Start
---
## 1. Enable the Plugin

Enable Procedural Limb Extraction Plugin in the Plugin Manager

Restart the editor if prompted

## 2. Open the Limb Extractor Tool

Navigate to Tools → Limb Extractor

The tool runs editor-only and does not modify the source mesh

## 3. Select a Skeletal Mesh

Assign a Skeletal Mesh in the picker

Once selected, the skeleton hierarchy will be available for bone-chain selection

## 4. Choose an Extraction Method

You can extract a limb in one of two ways:

Bone Chain Selection
Select a root bone (e.g. upperarm_l, spine_03) to extract a continuous chain

Cut Plane Tool (Optional)
Use the Cut Plane Gizmo to manually define a separation point

Bone-chain extraction is recommended for first use.

## 5. Set the Weight Threshold

Start with a value between 125 – 255 (recommended default)

Higher values include more vertices and produce a more complete mesh

Lower values are more restrictive and may introduce holes

If no vertices meet the threshold, mesh generation will fail.

## 6. Generate the Mesh

Click Generate Mesh

A new skeletal mesh asset will be created with:

Preserved bind pose alignment

Filtered and renormalized skin weights

Optional procedural capping

## 7. Merge / View Result

Use Merge / View to preview the extracted limb

Generated meshes are compatible with:

Props

Modular characters

Master Pose setups

Recommended First-Time Settings
---
Weight Threshold: 125 – 255
Auto Skin Weighting: Enabled
Procedural Capping: Enabled

## Common First-Time Issues

Mesh missing sections → Increase Weight Threshold

Holes near joints → Increase Weight Threshold or adjust bone chain

No mesh generated → Threshold too restrictive or invalid bone chain
