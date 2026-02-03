# Procedural Limb Extraction Plugin (UE5)

## Overview
An **editor-only Unreal Engine 5 plugin** for extracting **bone-chain-specific skeletal limb meshes**
from existing skeletal meshes.

Designed for gore systems, modular characters, and breakable body parts,
this tool preserves **bind pose alignment**, **valid skin weights**, and supports
procedural mesh capping and auto-skinweighting.

---

## What This Does
- Extracts skeletal sub-meshes based on bone chains (arms, legs, spine, etc)
- Builds partial skeletal meshes suitable for:
  - Props
  - Detached limbs
  - MasterPose-compatible modular meshes
- Preserves original bind pose alignment
- Caps open mesh boundaries with procedural gore
- Supports automatic re-skinweighting of extracted meshes

> **Editor-time only by design** — no runtime mesh generation or editor-only runtime dependencies.

---

## Key Features
- Bone-chain-based limb extraction
- Partial skeletal mesh generation
- MasterPose-compatible mesh output
- Procedural gore capping
- Skin-weight threshold filtering
- Auto-skinweighting support
- No runtime editor-only dependencies
- Tested and developed against **UE 5.0.3+**

---

## Demo Videos
▶ YouTube link here

---

## Quick Start
1. Enable the plugin
2. Open the **Limb Extractor Tool**
3. Select a source Skeletal Mesh
4. Choose a Bone Chain *(or optional Cut Plane tool)*
5. Adjust the **Skin Weight Threshold**
6. Generate the extracted mesh

---

## Requirements
- Unreal Engine **5.0.3**
- Editor-only usage

---

## Known Limitations
- No runtime mesh generation *(by design)*
- Source mesh must contain valid skin weights
- Auto-skinweighting requires:
  - A valid skeleton
  - All vertices initially weighted to at least one bone
  - Auto-skinweighting at this time is not designed for meshes with complex or atypical geometry,
  such as large protrusions, dense hair sections, or accessories positioned
  close to limbs or other bones. In these cases, manual cleanup or authoring separate meshes is recommended.
---

## Status
This plugin is under active development.
APIs, UI, and extraction + auto-skinweighting behavior may evolve as features stabilize.


## License
MIT / Custom

