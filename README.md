# Carbon Fiber Scale Planes

A multi-aircraft project focused on producing **large-scale composite display models** of experimental and reconnaissance aircraft using a repeatable pipeline:

**3D-printed master → surface finishing → mold making → carbon fiber layup → wall-mounted display**

The goal is not just a single model, but a **scalable process** that can be reused across multiple aircraft with consistent quality and documentation.

---

## Scope

This repository covers:
- Digital preparation of high-fidelity aircraft models
- Scaling and segmentation for constrained 3D printer volumes
- Physical master assembly and surface finishing
- Mold design and fabrication
- Carbon fiber layup (including “white carbon” aesthetic finishes)
- Structural and mounting considerations for large wall-hung models

Initial aircraft include:
- **YF-23 Black Widow II**
- **SR-71 / YF-12 family**

Additional aircraft may be added over time.

---

## Why This Exists

Large composite display models sit in an awkward gap:
- Too big for typical hobby prints
- Too small for traditional aerospace tooling
- Too complex to treat as “just a model”

This project treats each aircraft like a **small airframe**:
- Segmented shells, not monolithic prints
- Alignment keys and structural intent
- Materials and processes chosen for long-term stability, not just appearance

---

## Repository Structure

High-level structure:

docs/ → shared pipeline standards and methods
aircraft/ → per-aircraft projects (CAD, STLs, logs, photos)
templates/ → reusable documentation templates


Each aircraft is self-contained so lessons learned on one platform carry forward cleanly to the next.

---

## Current Status

- Target display scale: **~3 ft (≈1:17–1:18, aircraft dependent)**
- Printer constraint: **229 × 229 mm build volume**
- Assembly method: segmented shells with alignment features
- Final finish: composite layup over printed master

Progress and decisions are tracked per aircraft in their respective `build_log.md`.

---

## Notes

- This is **not** a flight-worthy or RC project.
- Models prioritize external geometry accuracy and surface quality.
- Some reference materials may be interpretive where public data is limited.

---

## License

Unless otherwise noted, documentation and original work in this repository are released under the included license.  
Third-party models and references remain the property of their respective owners.
