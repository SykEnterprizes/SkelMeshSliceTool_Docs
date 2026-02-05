## Overview
---
The Procedural Limb Extraction Plugin is an editor-only Unreal Engine tool designed
to extract bone-chain-specific skeletal meshes from an existing Skeletal Mesh while
preserving bind pose alignment, skeleton hierarchy, and usable skin weights.

It is intended for workflows that require modular character parts, detachable limbs,
or skeletal props that remain animation-compatible via Master Pose or shared skeletons.
All mesh generation is performed at editor-time to avoid runtime overhead and editor-only
dependencies in packaged builds.

Extraction can be driven either by selecting predefined bone chains (e.g. arms, legs,
spine) or by using a Cut Plane Tool to define custom separation boundaries. The resulting
meshes can optionally be capped with procedural gore and re-skinned automatically
using proximity-based weighting.

This tool is designed to integrate cleanly into existing character pipelines and does
not replace traditional DCC workflows, but instead automates repetitive and error-prone
tasks that are difficult to author manually.
