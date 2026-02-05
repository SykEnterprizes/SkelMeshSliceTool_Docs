## EdgeLoop Detection

A core feature of the tool is its ability to detect edge loops on cut or open meshes.

Detected edge loops are used as anchor points for:

Procedurally generated cap geometry

Fade rings and extensions

Bridging and reverse-cap operations

Each detected edge loop can be capped regardless of size, shape, or uniformity.

EdgeLoop Filtering
---
Depending on mesh complexity, multiple edge loops may be detected in a single cut.

Edge loop filtering allows you to:

Reduce clutter in the cap menu

Focus only on relevant loops

Prevent editor stalls caused by excessive loop generation

Important Note
---
Highly detailed meshes can generate a large number of edge loops.

Meshes with:

Dense topology

Protrusions

Hair or accessory geometry near the cut area

may produce many small or irregular loops.

These loops should be filtered to avoid overwhelming the UI and to prevent the Editor from stalling while cap data is being generated.

Why This Matters
---
The cap system generates UI widgets and geometry data per loop.
Filtering edge loops is strongly recommended before opening the cap menu on complex meshes.
