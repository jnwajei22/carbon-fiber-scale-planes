# Printing Standards (v0 — unknown printer)

I do not have established printer defaults yet. This doc defines:
- what parameters matter
- the initial test plan to establish real defaults
- what to record so settings become repeatable

## What I need to learn (and will measure)
- dimensional accuracy (XY error in mm)
- peg/hole fit clearance needed for reliable assembly
- warping tendency on long, thin parts
- surface quality needed before finishing

## Initial assumptions (placeholders)
These are NOT “standards,” just starting points until tested:
- Nozzle: 0.4 mm
- Layer height: 0.20 mm
- Walls/perimeters: 3
- Infill: 10–15% (grid/gyroid)
- Supports: only when required; prefer “tree” where available

## Test plan (establish real defaults)
1) Dimensional coupon
   - Print a 100 mm calibration bar
   - Measure actual length and record error

2) Peg-fit coupon
   - Print pegs/holes at clearances: 0.15 / 0.25 / 0.35 / 0.45 mm
   - Record which fits by hand without force and without slop

3) Warp coupon
   - Print a long thin strip similar to a wing edge
   - Measure max lift/warp (mm)

## What to record every time
- printer model
- filament type
- nozzle + layer height
- walls/infill/supports
- measured outcomes: fit, warp (mm), surface notes
