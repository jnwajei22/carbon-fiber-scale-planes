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

Status: Validated in production

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


Status: Superseded

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


Status: Validated in production

__________________________________________________________________________________________



Entry 4: Body_Upper alignment system redesign (Fusion tab keys) + coupon preparation

Date:

2026-03-07

Change made:

Replaced the previously planned slicer-style connector alignment for Body_Upper with a Fusion-modeled tab-and-pocket alignment system. Implemented standardized floating rectangular alignment keys across all Body_Upper station seams. Two tab sizes were defined to match the two pocket geometries created during segmentation.

Why:

The slicer-connector strategy originally chosen for Body_Upper proved less controllable than expected when working with already-segmented geometry. Modeling the alignment features directly in Fusion allows:

deterministic geometry control

consistent engagement depth

repeatable tolerances across seams

independence from slicer-specific connector tooling

Rectangular floating tabs also simplify assembly in areas where three sections meet at a joint and avoid over-constraining the seam compared to dowel-style joins.

How (settings/params):

Body_Upper join pockets created during segmentation:

Type A pockets

Opening face:
30 × 5 mm

Pocket depth:
24 mm

Used at seams between:

Section 01–02

Section 02–03_L / 03_C / 03_R

Section 03–04 center joints

Alignment key used:

TAB30

26 × 4 × 20 mm
0.5 mm chamfer on insertion edges

Clearances:

width: 2 mm per side

thickness: 0.5 mm per side

depth: ~2 mm per side when centered

Type B pockets

Opening face:
20 × 5 mm

Pocket depth:
24 mm

Used at seams between:

Section 04_L / 04_C / 04_R

Section 05_L / 05_R

Alignment key used:

TAB20

16 × 4 × 20 mm
0.5 mm chamfer on insertion edges

Clearances:

width: 2 mm per side

thickness: 0.5 mm per side

depth: ~2 mm per side when centered

Design characteristics

Tabs act as floating alignment keys rather than structural tongues:

prevent seam step

prevent yaw/rotation during assembly

maintain repeatable registration

Glue and seam faces carry structural load; tabs provide positional indexing only.

All tabs standardized to 20 mm engagement depth for consistent assembly behavior.

Result:

Body_Upper alignment strategy is now fully defined using Fusion-modeled tab keys rather than slicer connectors. All seams use one of two standardized alignment keys (TAB30 or TAB20), simplifying manufacturing and assembly.

CAD alignment system for the upper body is now complete.

Next:

Print fit-test coupons representing Body_Upper seam geometry to validate:

Tab insertion force

Printed tolerance behavior

Seam closure when tabs are installed

Rotational stability during dry-fit

Adjust tab dimensions if necessary before committing to full Body_Upper production prints.


Status: Implemented, not yet validated

Entry 5: Body_Upper production printing completed + TAB30 tolerance revision + pre-assembly validation

Date:

2026-09-05

Change made:

Completed production printing of all 10 structural Body_Upper sections and performed full dry-fit and pre-assembly inspection of the upper and lower tooling masters.

The Fusion-modeled tab-and-pocket alignment system introduced in Entry 4 was physically evaluated using the completed Body_Upper sections. Physical fit testing identified excessive lateral clearance in the original TAB30 alignment key. TAB30 was subsequently revised from 26 mm nominal width to 29 mm nominal width while retaining the existing 4 mm thickness, 20 mm length, and 0.5 mm insertion chamfer.

A single TAB30 Rev B was printed and physically tested before committing to the replacement production batch. The revised geometry substantially reduced lateral movement while retaining sufficient clearance for manual insertion and removal.

Production printing of the canopy remains outstanding. Its current slicer estimate is documented below and will be replaced/supplemented with actual print telemetry after fabrication.

Why:

Body_Upper represented the second major additive-manufacturing phase of the tooling-master fabrication process. Unlike Body_Lower, which uses cylindrical dowels, Body_Upper uses floating rectangular keys to provide positional registration across the segmented geometry.

The original TAB30 design incorporated 2 mm of lateral clearance per side within the nominal 30 mm-wide Type A pocket. Physical testing showed that this clearance was excessive for the intended registration function. Although the tab engaged the pocket without interference, the resulting lateral movement permitted excessive positional freedom between adjoining sections.

Increasing TAB30 nominal width from 26 mm to 29 mm reduced the designed lateral clearance from 4 mm total to approximately 1 mm total, or 0.5 mm per side.

The revised TAB30 was printed individually and test-fitted before producing the replacement batch, limiting additional material and fabrication time in the event that further tolerance adjustment was required.

Completion of the structural upper-body printing and alignment validation establishes a formal phase boundary between additive manufacturing and plug assembly/surface preparation.

How (settings/params):

Printer:

Bambu Lab A1

0.4 mm nozzle

Textured PEI build plate

Material:

Generic PLA

Gray / silver

1.75 mm filament

Layer settings:

Layer height: 0.16 mm

Initial layer height: 0.20 mm

Infill:

12% gyroid

Adhesion:

Outer brim

5 mm width

Supports:

Enabled as required for Body_Upper production geometry


Body_Upper structural production:

BODY_UPPER_01

Duration: 2h 41m (slicer estimate)

Material: 75.45 g (slicer estimate)


BODY_UPPER_02

Duration: 7h 04m (slicer estimate)

Material: 210.45 g (slicer estimate)


BODY_UPPER_03_L

Duration: 5h 02m

Material: 134.98 g


BODY_UPPER_03_C

Duration: 9h 56m

Material: 290.96 g


BODY_UPPER_03_R

Duration: 5h 01m

Material: 136.46 g


BODY_UPPER_04_L

Duration: 3h 34m

Material: 91.09 g


BODY_UPPER_04_C

Duration: 7h 07m

Material: 241.31 g


BODY_UPPER_04_R

Duration: 3h 21m

Material: 86.71 g


BODY_UPPER_05_L

Duration: 4h 21m

Material: 116.01 g


BODY_UPPER_05_R

Duration: 4h 20m

Material: 116.04 g


Total Body_Upper structural print time:

52h 27m


Total Body_Upper structural material:

1,499.46 g PLA


Canopy:

Production print pending

Current slicer estimate:

Duration: 2h 55m

Material: 42.98 g PLA

Estimated Body_Upper total including canopy:

55h 22m

1,542.44 g PLA


Alignment hardware:

Original TAB30 / TAB20 production batch:

7 × TAB30 Rev A

5 × TAB20

Duration: 42m

Material: 14.6 g PLA


TAB30 Rev A:

26 × 4 × 20 mm

0.5 mm insertion chamfer

Nominal Type A pocket:

30 × 5 mm

Physical observation:

Excessive lateral movement during fit testing. The original 26 mm width provided approximately 4 mm total nominal lateral clearance and did not provide sufficiently precise registration.


TAB30 Rev B:

29 × 4 × 20 mm

0.5 mm insertion chamfer

Nominal Type A pocket:

30 × 5 mm

Nominal lateral clearance:

1.0 mm total

Approximately 0.5 mm per side


TAB30 Rev B validation print:

Quantity: 1

Duration: 10m

Material: 1.69 g PLA

Physical observation:

Substantially reduced lateral movement compared with TAB30 Rev A. Minor clearance remained, allowing insertion and removal without excessive force. No major lateral slippage was observed.

Fit accepted for production use.


TAB30 Rev B production batch:

Quantity: 5

Duration: 23m

Material: 8.17 g PLA


TAB20:

16 × 4 × 20 mm

0.5 mm insertion chamfer

Quantity produced: 5

Geometry unchanged from Entry 4.


Alignment-development / hardware printing documented during this phase:

Total print time: 1h 15m

Total material: 24.46 g PLA

This includes the original mixed TAB30 Rev A / TAB20 batch, one TAB30 Rev B validation print, and the five-piece TAB30 Rev B replacement production batch.


Inspection / validation:

All 10 structural Body_Upper sections were successfully fabricated.

The complete Body_Upper assembly was dry-fitted to evaluate overall geometry, seam continuity, and registration before permanent bonding.

Body_Lower was also dry-fitted and retained as an independent tooling master. Body_Upper and Body_Lower will not be permanently bonded to one another.

Individual inventory photographs were taken of the printed upper- and lower-body components.

Lower-body alignment fit-test coupons were retained and photographed as physical validation artifacts.

Inspection of the lower-body blind dowel sockets identified residual support/printed material in the bottoms of some sockets. The sockets are nominally 25.0 mm deep while the dowel design requires 22.5 mm engagement per side, providing approximately 2.5 mm of axial relief.

Socket cleanup will therefore target restoration of the required usable engagement depth rather than unnecessary removal of all material at the absolute bottom of each blind socket.


Result:

Production printing of all primary Body_Upper structural sections is complete.

The Body_Upper floating-tab alignment concept was physically demonstrated using the completed production geometry. Testing identified excessive lateral clearance in the original 26 mm TAB30 design.

TAB30 was revised to 29 mm nominal width. A single Rev B tab was fabricated and physically validated before the replacement production batch was printed. The revised geometry provides acceptable registration with substantially reduced lateral movement while maintaining sufficient assembly clearance.

Body_Upper structural fabrication required approximately 52h 27m of printing and 1.50 kg of PLA. Including the currently estimated canopy print, the complete upper tooling master is expected to require approximately 55h 22m and 1.54 kg of PLA, excluding alignment hardware.

For comparison, Body_Lower production required 27h 54m and 728.88 g PLA.

Based on the currently documented values, the complete upper and lower tooling-master geometry, including the estimated canopy but excluding alignment hardware and earlier lower-body validation coupons/dowels, represents approximately:

83h 16m of additive manufacturing

2,271.32 g PLA

The project has now progressed from primary additive manufacturing into pre-assembly preparation. No permanent structural bonding, exterior fairing, or mold-surface finishing has begun.


Next:

Begin plug assembly and surface preparation.

Clean lower-body dowel sockets only as required to restore the designed 22.5 mm minimum usable engagement depth.

Remove brim remnants, support residue, blobs, and other printing artifacts from mating surfaces.

Use a rigid sanding block to flatten mating faces as required while avoiding rounding or altering exterior tooling geometry.

Repeatedly dry-fit adjoining sections during surface preparation to verify seam closure and alignment.

Perform a final complete dry-fit after mating-face preparation.

Permanently bond Body_Upper sections into one rigid upper tooling master and Body_Lower sections into one rigid lower tooling master.

Reinforce bonded joints from non-tooling/interior surfaces where accessible.

Begin exterior seam filling, fairing, filler-primer application, and progressive sanding in preparation for mold fabrication.

Record actual canopy production telemetry after printing and update the fabrication totals accordingly.


Status:

Body_Upper structural production printing complete

TAB30 Rev B physically validated and accepted

Primary additive-manufacturing phase complete pending canopy

Ready for plug assembly and surface preparation