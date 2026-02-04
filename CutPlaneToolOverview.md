## Cut Plane Tool (Quick Overview)

The Cut Plane Tool is an alternative extraction method that allows you to define a custom cut region directly in the viewport, 
instead of relying on predefined bone chains.

This is useful when:

A clean bone chain is not available

You need a non-standard cut (torso damage, partial limbs, asymmetrical breaks)

You want more visual control over where the mesh is separated

## When to Use the Cut Plane Tool

Use the Cut Plane Tool when:

Bone-chain extraction produces unwanted geometry

You need to cut across multiple bones

You want to visually position the cut rather than selecting bones

You want mirrored extractions (eg: left and right full arms for a modular mesh asset)

You want a bone chain, but only a partial section of the root or child bones

## Basic Cut Plane Workflow

Select a Skeletal Mesh

Switch Extraction Mode to Cut Plane

Toggle the Cut Plane Tool

Position and orient the plane in the viewport

Adjust extraction depth and bounds

Generate Mesh

The tool extracts vertices within the defined cut volume and builds a new skeletal mesh from the result.

## How the Cut Plane Works (High-Level)

The Cut Plane Tool:

Defines a 3D extraction volume aligned to a plane

Selects vertices inside that volume

Filters vertices based on bone influence

Preserves skin weights for the extracted bones

Leaves an open boundary suitable for procedural capping

No geometry is modified until Generate Mesh is pressed.

## Important Notes

The Cut Plane Tool does not automatically create clean loops
(edge loops are detected and filtered later during capping)

Very large extraction volumes may include unintended vertices

Weight thresholding still applies and affects which vertices are kept

## Performance Considerations

Extraction is editor-time only

Complex meshes or large extraction volumes may take longer to process

Excessive edge loops can impact capping performance

## Recommended First Use

Tip - 
For your first extraction, start with bone-chain mode.
Use the Cut Plane Tool once you are familiar with how weight thresholds and capping behave.
