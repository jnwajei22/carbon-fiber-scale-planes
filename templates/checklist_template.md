# Checklist Template

> Use this checklist for any aircraft and any phase. Copy a section into a new checklist file (or into the build log entry) and fill it out.
>
> Convention:
> - [ ] = not done
> - [x] = done
> - Include numbers/units whenever possible (mm, °C, hr, g).
> - If you deviate from standards, record **why** and **what changed**.

---

## 0) Metadata

- Aircraft: `<yf-23 / yf-12 / ...>`
- Phase: `<Model Prep / Segmentation / Slicing / Printing / Assembly / Layup / Finish / Mounting>`
- Date started: `<YYYY-MM-DD>`
- Date completed: `<YYYY-MM-DD>`
- Owner: `<name>`
- Files/links:
  - CAD: `<path>`
  - STL: `<path>`
  - Slicer project: `<path>`
  - Photos: `<path>`
- Notes (1–3 lines max):
  - `<...>`

---

## 1) Inputs & Requirements

- [ ] Target scale confirmed (length and/or scale ratio): `<...>`
- [ ] Printer envelope confirmed (X/Y/Z): `229 x 229 x <Z> mm`
- [ ] Max part size set (safety margin): `<e.g., 220 mm>`
- [ ] Orientation constraint(s) noted (e.g., keep stabilizers one piece): `<...>`
- [ ] Cosmetic constraint(s) noted (hide seams on panel lines / chines): `<...>`
- [ ] Strength constraint(s) noted (hang load path, seam shear risk): `<...>`

---

## 2) Model Intake & Sanity Checks

Source
- [ ] Source model documented (where it came from, license/permission if relevant): `<...>`
- [ ] Units verified (mm/inches) and scale applied correctly
- [ ] Model is watertight / manifold (or repair plan documented)
- [ ] Normals checked (no inverted shells)
- [ ] Thin walls / non-solid surfaces identified (problem areas noted)

Geometry QA
- [ ] Non-manifold edges fixed
- [ ] Self-intersections fixed
- [ ] Holes filled / shell repaired
- [ ] Convert to solid completed (method + settings recorded)
- [ ] Final “clean” master saved (before segmentation)

Record (fill)
- Tool used: `<Blender / Meshmixer / Fusion / ...>`
- Repair steps summary: `<3–6 bullets>`
- Output master file: `<path>`

---

## 3) Segmentation Plan (Printability + Assembly)

Split strategy
- [ ] Split lines chosen to minimize visible seams (notes: `<...>`)
- [ ] Each segment fits printer envelope with margin
- [ ] Segment count reasonable (avoid “100-piece tragedy”)
- [ ] Key surfaces will be accessible for sanding/finishing
- [ ] Internal access considered (if you need mounts, wires, etc.)

Alignment & joints
- [ ] Alignment method selected: `<pegs / dovetail / keys / magnets / tabs>`
- [ ] Peg/key dimensions set:
  - Peg diameter: `<mm>`
  - Peg length: `<mm>`
  - Clearance: `<mm>` (typical: 0.20–0.40 mm depending on printer/material)
- [ ] Peg quantity/placement confirmed (avoid weak thin areas)
- [ ] Dry-fit strategy defined (which parts test-fit first)

Naming & organization
- [ ] Segment naming scheme applied (e.g., `yf23_top_A01`, `yf23_bot_B03`)
- [ ] Exported STLs organized into `aircraft/<plane>/stl/<rev>/...`

Record (fill)
- Segmentation tool: `<...>`
- Revision tag: `<v1 / v2 / ...>`
- Notes on seam placement: `<...>`
- Known risks: `<...>`

---

## 4) Slicing Setup (Baseline + Deviations)

Printer/material
- [ ] Filament/material chosen: `<PLA / PETG / ASA / ...>`
- [ ] Nozzle size: `<0.4 / 0.6 / ... mm>`
- [ ] Layer height: `<mm>`
- [ ] Wall/perimeter count: `<#>`
- [ ] Top/bottom layers: `<#>`
- [ ] Infill % + pattern: `<...>`
- [ ] Supports: `<none/tree/custom>` with density `<...>`
- [ ] Adhesion method: `<brim/raft>` size `<mm>`
- [ ] Seam setting: `<aligned/random>` location strategy `<...>`

Fit/tolerance considerations
- [ ] Horizontal expansion / XY compensation set (if used): `<mm>`
- [ ] Hole compensation considered (if pegs/magnets)
- [ ] Test coupon planned if tolerances are new/changed

Record (fill)
- Slicer: `<OrcaSlicer / PrusaSlicer / Cura / ...>`
- Profile name: `<...>`
- Project file saved to: `aircraft/<plane>/slicing/<rev>/...`

---

## 5) Print Execution Checklist

Before print
- [ ] Bed cleaned
- [ ] First-layer calibration OK
- [ ] Filament dry enough (or note moisture risk)
- [ ] G-code preview checked (supports, seams, thin walls)
- [ ] Estimated print time + filament usage recorded

During print
- [ ] First layer verified (photos optional)
- [ ] Warping risk monitored (corners, long spans)
- [ ] Support interface behaving as expected

After print (immediate)
- [ ] Part labeled with segment ID + revision
- [ ] Warping measured (max lift in mm): `<...>`
- [ ] Dimensional check (critical dims): `<...>`
- [ ] Surface defects noted (zits, under-extrusion, layer shifts)

---

## 6) Post-Print QA & Prep

Cleanup
- [ ] Supports removed cleanly (damage noted if any)
- [ ] Brim/raft removed
- [ ] Edges deburred

Fit check
- [ ] Dry-fit performed (which segments): `<...>`
- [ ] Seam gaps measured (mm): `<...>`
- [ ] Peg fit evaluated: `<too tight / good / too loose>`
- [ ] Adjustments needed logged (clearance, peg size, split line)

Surface prep (for finish/layup later)
- [ ] Sanding grit progression planned: `<e.g., 120 → 220 → 400>`
- [ ] Filler/primer plan noted (if any)
- [ ] Dust control + PPE ready

---

## 7) Assembly Checklist (Dry-fit → Bond)

Dry-fit
- [ ] Order of assembly defined
- [ ] Clamping method defined (tape, clamps, jigs)
- [ ] Alignment checked (centerline, symmetry)

Bonding
- [ ] Adhesive chosen: `<CA/epoxy/etc.>` brand `<...>`
- [ ] Surface prep done (scuffed + cleaned)
- [ ] Bond line thickness controlled (method: `<...>`)
- [ ] Cure time recorded: `<...>`

Post-bond QA
- [ ] Seam strength check (light stress test)
- [ ] Alignment rechecked after cure
- [ ] Seam fill plan noted (putty/epoxy slurry/etc.)

---

## 8) Composite Layup Checklist (Optional / When Applicable)

Safety
- [ ] Gloves + respirator + eye protection
- [ ] Ventilation confirmed
- [ ] Waste disposal plan (resin, rags) noted

Materials
- [ ] Cloth type/weave/weight: `<...>`
- [ ] Resin system: `<...>`
- [ ] Mix ratio by weight: `<...>`
- [ ] Pot life @ temp: `<...>`
- [ ] Peel ply / breather / vacuum bag plan (if used)

Process
- [ ] Surface keyed/sanded appropriately
- [ ] Dust-free + cleaned (IPA/acetone per material compatibility)
- [ ] Layup schedule defined (layers + orientation)
- [ ] Cure schedule defined (time/temp)
- [ ] Post-cure plan defined (if used)

QA
- [ ] Air bubbles addressed
- [ ] Dry spots addressed
- [ ] Edge peel/bridging checked

---

## 9) Finishing Checklist (Optional)

- [ ] Seam work complete
- [ ] Final sanding done (final grit: `<...>`)
- [ ] Clear coat / paint plan defined
- [ ] Cosmetic defects logged and accepted/reworked

---

## 10) Mounting & Load Checklist (Hanging / Stand)

Mount plan
- [ ] Mount type selected: `<wire/rod/stand/wall mount>`
- [ ] Attachment points identified (load path)
- [ ] Reinforcement plan defined (internal plates, epoxy blocks, etc.)

Load sanity check
- [ ] Estimated mass: `<kg>`
- [ ] Safety factor target: `<e.g., 3x>`
- [ ] Hardware rating verified (hooks, wire, anchors)
- [ ] Test hang performed close to ground first

Record
- [ ] Final mounting photos saved to `aircraft/<plane>/photos/mounting/`

---

## 11) Closeout

- [ ] Files saved + committed:
  - [ ] STLs exported
  - [ ] Slicer project saved
  - [ ] Key photos uploaded
- [ ] Build log updated with:
  - [ ] What changed
  - [ ] Measured results
  - [ ] Next step
- [ ] TODOs captured (no loose ends floating in your brain)
