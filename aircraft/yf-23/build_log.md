Entry 1: Lower section alignment system (implemented, pending print validation)

Date:

2026-02-13

Change made:

Converted mesh files retrieved from thingiverse to solids. Constructed offset planes as cutting tools/planes. Cut offset planes to section lower body for printing (~190.5 mm). Implemented alignment peg + socket system across YF-23 lower-seam segments (including special-case offsets near nacelles and nose).

Why:

To ensure repeatable registration during dry-fit and bonding, reduce seam shear during handling/finishing, and standardize joins across segments.

How (settings/params):

Seam length reference: 215.875 mm
Dowel placement: 2 per seam at ±54.0 mm from seam center
Nacelle-adjacent seam: 2 per seam at ±36.0 mm from seam center (72 mm spacing)
Nose cone seam width: 86.041 mm; dowels at ±21.5 mm from centerline (~43 mm spacing)
Socket: Ø5.0 mm, depth 25.0 mm per side
Peg: scaled 0.925× → Ø4.625 mm, total length 45.0 mm (22.5 mm engagement per side + 2.5 mm relief per side)
Chamfers: 1.00 mm chamfer on peg ends and 1.00 mm chamfer on socket entries
Validation: Fusion interference check run → no interferences detected

Result:

CAD join system is fully defined for lower portion; geometry passes interference checks. Real-world fit still unvalidated.

Next:

Begin Body_Upper segmentation and implement the same join standard (Ø5.0 sockets, Ø4.625 pegs, 45 mm length, 25 mm socket depth, 1 mm chamfers). Defer peg-fit coupon until printer access is available; coupon remains required before committing to full production prints.


__________________________________________________________________________________________



Entry 2: Upper body segmentation (completed) + switch to slicer-style alignment pins + Fusion stability workaround

Date:

2026-02-17

Change made:

Completed full Body_Upper segmentation into 11 parts (including canopy). Switched Body_Upper alignment from Fusion-modeled dowels to slicer-style pins/connectors. Implemented a workflow workaround to stabilize the problematic upper-body geometry (canopy/cockpit artifacts and persistent boolean/splitting failures) so segmentation could be completed without degrading the exterior surfaces.

Why:

Body_Upper mesh/solid operations were unstable in Fusion due to non-manifold/self-intersecting geometry and canopy/cockpit artifacts; booleans and Boundary Fill repeatedly failed. Global rebuild/remesh attempts introduced visible surface degradation, which is unacceptable for a public-facing project. Slicer-style pins provide robust registration across many seams without relying on fragile boolean feature modeling. A stability workaround was required to get the upper geometry into a state where clean station splitting could proceed reliably.

How (settings/params):

Overall scaled dimensions:

Length (nose→tail): 914.4 mm

Max width: 596.322 mm

Max height (approx): 217 mm

Primary segmentation:

Longitudinal station spacing: 190.5 mm along length (consistent with Body_Lower approach)

Mid-body lateral splitting:

~596.322 mm wide station: 3-way split (L / center spine / R) with center spine width = 180.000 mm (cut planes at ±90.000 mm from centerline)

~573.597 mm wide station: 3-way split (L / center spine / R) with center spine width = 170.000 mm (cut planes at ±85.000 mm from centerline)

Rear/ruddervator+nacelle section:

Centerline split (L/R) due to thin/precarious geometry and internal cavities; avoided additional seams in this region

Alignment approach:

Body_Upper: slicer-style pins/connectors (for anti-step and anti-rotation across many seams, avoiding Fusion boolean dependency)

Body_Lower: retains Fusion-modeled dowel sockets/pegs as previously defined

Workaround (Fusion stability / solidization):

After import and scaling, the upper body remained unstable even after remeshing and converting to BRep—boolean operations and downstream splitting were still failing. To stabilize the geometry, all resulting bodies were first combined into a single body, then a new component was created from that body, and the component was exported as a STEP. Re-importing that STEP back into Fusion effectively “laundered” the geometry into a clean, unified solid that behaved normally for splitting and further edits. After re-import, remaining canopy/cockpit artifacts were removed via Modify → Remove (targeting internal faces/surface scraps) to preserve the exterior surface.

Result:

Body_Upper is now fully segmented into printable parts at the correct scale, with a consistent cut strategy and canopy artifact cleanup completed without compromising exterior geometry. Alignment plan is locked: pins/connectors for upper; Fusion dowels remain on lower.

Next:

Print fit-test coupons for both join standards before committing to full prints:

Lower body dowel coupon: validate Ø5.0 socket / Ø4.625 peg clearance, insertion force, chamfer effectiveness, and repeatability.

Upper body pin/connector coupon: validate connector diameter/tolerance, depth/engagement, and resistance to seam step/rotation under clamp/glue load.

Adjust tolerances/fit based on coupon results, then lock final connector parameters and export production STLs for full upper/lower printing when fabrication access is available.


__________________________________________________________________________________________



Entry 3: Body_Lower production printing (completed) + join validation

Date:

2026-03-05

Change made:

Completed full production printing of all Body_Lower sections (01–05) using Bambu Lab A1 printers at Tarrant County Makerspace. Printed join-validation coupons and dowels prior to committing to full parts to confirm dowel clearance, insertion force, seam alignment, and rotational stability.

Why:

The Body_Lower join system relies on Fusion-modeled dowels and sockets for alignment and anti-rotation across station seams. Because this is the first physical validation of the CAD join design, a staged approach was used:

Print test coupons representing the seam geometry.

Print alignment dowels and confirm clearance and engagement.

Validate seam alignment, rotational rigidity, and separation behavior.

Proceed with full-scale printing only after join geometry was confirmed to behave correctly.

This avoided committing ~30 hours of printing to parts that might not assemble correctly.

How (settings/params):

Printer:

Bambu Lab A1
0.4 mm nozzle
Textured PEI build plate

Material:

Generic PLA (Hobby Lobby brand)
Blue
1.75 mm filament

Layer settings:

Layer height: 0.16 mm
Initial layer height: 0.20 mm

Z-offset adjustment:

+0.15 mm offset applied (G-code / machine adjustment) due to non-standard nozzle installed on makerspace printer.

Infill:

Gyroid pattern

Sections 01–03: 15%
Sections 04–05: 12%

Adhesion:

Outer brim only
5 mm width

Supports:

Sections 01–02: none
Section 03: supports enabled
Section 04: supports enabled
Section 05: none
Coupons: none

Production prints:

Body_Lower_01 + 02
Duration: 5h 17m
Material: 150.31 g

Body_Lower_03
Duration: 10h 45m
Material: 273.12 g

Body_Lower_04
Duration: 7h 45m
Material: 208.17 g

Body_Lower_05
Duration: 4h 07m
Material: 97.28 g

Total Body_Lower print time:

27h 54m

Total material used:

728.88 g PLA

Validation prints:

Test alignment dowels (2 pcs): printed prior to coupon testing to verify socket clearance and insertion force. Print time ~10 minutes; material negligible (~1–2 g).

Fit-test coupon A: 2h 30m, 79 g.

Fit-test coupon B: 1h 40m, estimated ~35–45 g (exact mass not recorded).

Production dowels (8 pcs): printed after coupon validation for final Body_Lower assembly. Print time ~26 minutes total; one dowel failed during printing and was reprinted.

Post-print observations:

All five Body_Lower sections printed successfully with no critical failures. Initial dry-fit without dowels showed clean seam alignment on flat exterior surfaces across sections.

Dowel sockets contained minor support residue, preventing full engagement until cleaned. This was resolved by clearing sockets using a drill bit by hand (no powered drilling) to restore the designed clearance.

After cleanup, dowel insertion required minimal force while still providing strong anti-rotation behavior. Rotational integrity and seam alignment were confirmed during dry-fit testing.

Result:

Body_Lower is now fully printed and physically validated. The Fusion-modeled dowel join system performs as intended, providing accurate registration and rotational stability across seams.

Next:

Complete full dry-fit assembly of all Body_Lower sections with dowels installed, then proceed to permanent assembly and seam finishing (bonding + filler). In parallel, begin planning composite workflow validation using a smaller training mold section before committing to full clamshell mold fabrication.