# Pipeline Overview (v0)

This repo is documenting an end-to-end workflow for building large static display aircraft using:
- segmented 3D-printed masters
- bonded assembly + surface refinement
- optional molds + composite layup
- final mounting (hang/stand)

## Assumptions (v0)
- Printer build volume target: 229 × 229 mm (or similar)
- Models will be split into print-fit sections with alignment features
- Goal is display quality, not RC flight loads

## Workflow stages
1) Reference + model intake
   - Inputs: mesh + reference images
   - Done when: scale chosen; known geometry compromises listed

2) Mesh repair + solid conversion
   - Done when: watertight/solid master mesh saved

3) Segmentation + joins
   - Done when: every part fits build volume with margin; join strategy defined

4) Slicing + print
   - Done when: test coupons validate fit/tolerances; first real segments print cleanly

5) Dry-fit + bonding
   - Done when: assembled master is rigid and aligned; gaps measured and recorded

6) Surface finishing (mold-ready if doing molds)
   - Done when: seam lines are filled/sanded to target finish

7) Optional: mold making
   - Done when: mold releases cleanly; surface quality acceptable

8) Optional: composite layup (white carbon target)
   - Done when: cured part has acceptable weave + finish plan

9) Mounting
   - Done when: mount load path is safe; test hang completed

## Definition of “v1 success”
- One aircraft (YF-23) fully assembled as a clean master
- Repeatable segmentation + alignment approach documented
- Lessons captured in build logs so next aircraft is faster
