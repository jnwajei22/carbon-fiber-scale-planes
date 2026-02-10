# YF-23 Black Widow II — Composite Scale Model

Large-scale composite display model of the **Northrop YF-23 Black Widow II**, built using a segmented 3D-printed master and carbon fiber layup.

This aircraft is the **baseline platform** for validating the pipeline used across the Carbon Fiber Scale Planes project.

---

## Goal & scale

- **Goal:** Produce a static, hangable display model with a composite exterior (target “white carbon” finish) using a 3D-printed master + molds.
- **Target length:** ~3 ft (≈36 in / 914 mm)
- **Approx. scale:** ~1:17–1:18 (varies with reference)
- **Why YF-23:** Geometry stress-tests segmentation, seam hiding, surface finishing, and mold fidelity (diamond planform, integrated control surfaces, serpentine intakes, all-moving V-tails).

---

## Printer constraints

- **Build volume:** 229 × 229 mm
- **Implications:**
  - Airframe must be segmented into print-fit shells/sections.
  - Seams should be placed where they are least visible or easiest to finish.
  - Intake geometry may force non-intuitive splits.

---

## Segmentation plan (with diagrams later if you want)

- **Approach:**
  - High-resolution mesh sourced, repaired, and scaled to target length.
  - **Top and bottom shells handled independently.**
  - Segmentation driven by:
    - printer envelope
    - intake geometry / internal curvature
    - minimizing visible seam lines
- **Export location:** `stl/` (print-ready segmented STLs)
- **Notes:** Diagrams and split-line map can be added later once top-shell segmentation is finalized.

---

## Alignment/joins (peg size, spacing, clearance)

- **Method:** Alignment pegs + bonded joints between segments.
- **Status:** Peg strategy validated on bottom shell.
- **Parameters:** *(to be finalized and recorded here once locked)*
  - Peg diameter: `<TBD mm>`
  - Peg length: `<TBD mm>`
  - Clearance: `<TBD mm>`
  - Placement/spacing: `<TBD>` (avoid thin/weak shell regions; prioritize shear resistance)
- **Design intent:** Joints should locate reliably during dry-fit and reduce seam shear during handling/finishing.

---

## Assembly plan (adhesive, seam strategy)

- **Master assembly intent:** Printed segments assembled into a **rigid reference surface** (master).
- **Adhesive:** `<TBD>` (record final choice + cure time)
- **Seam strategy:**
  - place seams where they are easiest to sand/fill or visually hidden
  - refine seams post-bond (filler/primer plan lives in docs)
- **Control surfaces:** Cut and hinged **post-print** (after master assembly).

---

## Finish/layup plan

- **Finish target:** Mold-ready surface quality on the printed master.
- **Composite process (planned):**
  1. Assemble printed master
  2. Surface refinement to mold-ready finish
  3. Create molds
  4. Carbon fiber layup (target “white carbon” finish)
- **Standards/docs:**
  - `docs/printing_standards.md`
  - `docs/materials_and_tools.md`
  - `docs/mold_standards.md`
  - `docs/layup_standards_white_carbon.md`
  - `pipeline_overview.md`

---

## Mount plan

- **Intent:** Final assembly designed for **wall mounting**.
- **Mounting standards:** `docs/mounting_standards.md`
- **Details TBD:** hardware choice, attachment points/load path, reinforcement (if required).

---

## Current status + next step

**Status: In progress**

- Bottom shell: segmented, repaired, aligned
- Control surfaces: planned post-print
- Top shell: pending segmentation and prep

**Next step:**
- Segment and prep the **top shell** to match bottom-shell join strategy and printer constraints.

---

## Known issues / TODO

Tracked in `build_log.md`, including:
- Final segmentation count (especially around intakes)
- Peg tolerances vs adhesive choice (fit vs bond gap)
- Internal reinforcement requirements (if mounting loads demand it)
- Final mounting strategy (hardware + load path)
- Composite layup schedule + resin system selection

---

## Repo structure (local reference)

- `refs/` → reference images, drawings, notes  
- `cad/` → Fusion 360 files and mesh sources  
- `stl/` → print-ready segmented STLs  
- `slicing/` → slicer profiles and project files  
- `photos/` → WIP and finished build photos  
- `build_log.md` → chronological build notes  
