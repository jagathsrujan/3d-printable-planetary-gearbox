# BOM from CAD — Two-Stage 16:1 Planetary Gearbox

Original design: [How To Mechatronics — 3D printed planetary gearbox](https://howtomechatronics.com/how-it-works/how-planetary-gears-work-3d-printed-planetary-gearbox-design-and-test/).
This list was measured from that design's STEP file; it does not change the design.

**Source:** `E:\bangalore tech summit\Planetary Gearbox - Two-stage 16to1 ratio.step`, imported into
FreeCAD (GUI) on 11 Nov 2026. 44 solids, axis along Y, output face at Y = −60, motor at +Y.
All dimensions are in mm and measured from the B-rep (cylinder radii, face extents). Nothing here is
copied from the README unless it says so.

Some terms used below:
- **Seat** — the printed pocket a bearing's outer ring presses into.
- **Journal** — the part of a shaft that sits inside a bearing's inner ring.
- **Counterbore** — a flat-bottomed step that lets a socket-head screw sit below the surface.
- **Countersink** — a 90° cone for a flat-head (countersunk) screw.
- **Heat-set insert** — a brass threaded sleeve pressed into the plastic with a soldering iron.

---

## 1. Solid count (44)

| Part (STEP label) | Qty | Type |
| --- | --- | --- |
| Planet gear | 6 | printed |
| Carrier p1 – stage 1 | 1 | printed |
| Carrier p1 – stage 1 – Output | 1 | printed |
| Carrier p1 – stage 2 | 1 | printed |
| Carrier p2 – stage 2 – Output | 1 | printed |
| Input shaft | 1 | printed |
| Ring gear | 1 | printed |
| Front cover | 1 | printed |
| Back cover | 1 | printed |
| NEMA17 mount | 1 | printed |
| Pin "6x11mm" | 6 | bought |
| Bushing 8mm | 6 | bought |
| Washer 6mm | 12 | bought |
| Bearing 25x37x7mm | 1 | bought |
| Ball Bearing 12x21x5mm | 2 | bought |
| Ball Bearing 17x26x5mm | 1 | bought |
| Stepper NEMA 17 | 1 | bought (owned) |
| **Total** | **44** | 15 printed + 29 bought |

---

## 2. Printed parts (PLA)

| Qty | Part | STL file | Envelope | Key features measured |
| --- | --- | --- | --- | --- |
| 1 | Ring gear / housing | `Ring gear.stl` | Ø85 × 47 | 45T internal teeth in two 12 mm bands (stage 1 Y −12…0, stage 2 Y −35.5…−23.5); Ø72 clearance recesses for the carriers; 6 + 6 insert pockets Ø4.2 × 10 deep, one set per end, on a Ø78.5 bolt circle |
| 1 | Front cover | `Front cover.stl` | Ø85 × 11 | Ø37 × 7 bearing seat; 0.5 mm Ø34 shoulder; Ø26 × 3.5 **clearance bore** for the Ø25 output hub (0.5 mm gap, not a bearing seat); 6 × Ø3.0 clearance + Ø7.5 × 3.2 counterbore |
| 1 | Back cover | `Back cover r1.stl` | Ø85 × 14 | Ø26 × 5 bearing seat; Ø72 × 7 carrier recess; Ø24 / Ø18 shaft passage; 6 × Ø3.0 × 10.8 clearance + Ø7.5 × 3.2 counterbore; 4 × Ø4.2 × 6.0 insert pockets for the NEMA plate |
| 1 | NEMA 17 mount | `NEMA17 mount r2.stl` | 56 × 41 × 10 | Ø24 central hole; 4 × Ø3.0 motor holes on 31 × 31 with 90° countersink (Ø7) on the **gearbox side**; 4 × Ø3.0 through holes at (±16.5, ±24) to the back cover; Ø3.5 radial hex-key access hole on −X at Y = 19.5 |
| 1 | Input shaft + stage-1 sun | `Input shaft r1.stl` | Ø25.5 × 36.4 | 15T helical sun; Ø11.94 × 5 journal (inner 12 × 21 bearing); Ø16.94 journal (17 × 26 bearing); Ø19.94 shoulder; Ø5.08 × 25 motor bore; radial Ø4.0 grub-screw hole, 5.9 mm long, at Y = 16.6 |
| 6 | Planet gear, 15T helical | `Planet gear - 15 tooth helical.stl` | Ø25.5 × 9 | Ø8.0 × 9 bore for the bushing |
| 1 | Carrier, stage 1, motor-side half | `Carrier p1 - stage 1.stl` | Ø56 × 19 | 3 × Ø6 pin holes, 4 deep; 3 × Ø4.2 × 8 insert pockets |
| 1 | Carrier, stage 1, output half + stage-2 sun | `Carrier p1 - stage 1 - Output.stl` | Ø56 × 29 | Ø21 × 5 bearing seat; 3 × Ø6 × 5 pin holes; 15T helical sun; Ø12 × 5 journal; 3 × countersink Ø7.5 → Ø2.8 passage |
| 1 | Carrier, stage 2, motor-side half | `Carrier p1 - stage 2.stl` | Ø56 × 19 | same as the stage-1 motor-side half (identical volume) |
| 1 | Carrier, stage 2, output half + output hub | `Carrier p2 - stage 2 - Output.stl` | Ø56 × 24 | Ø21 × 5 bearing seat; Ø25 × 15 output journal; 4 × Ø4.2 × 10 insert pockets on a Ø14 bolt circle; 3 × countersink Ø7.5 → Ø2.8 passage |

**STL vs STEP check:** all 10 printable STLs match their STEP part to within 0.05 % in volume and
0.1 mm in envelope (the difference is mesh faceting). The `CUTOUT - *.stl` files are display
sections, not print parts.

---

## 3. Bought parts

| Qty | Item | Spec measured in CAD | Where | Price |
| --- | --- | --- | --- | --- |
| 1 | Ball bearing **6805** | 25 × 37 × 7 | Front cover Ø37 seat, on the Ø25 output journal | not checked |
| 1 | Ball bearing **6803** | 17 × 26 × 5 | Back cover Ø26 seat, on the input shaft Ø17 journal | not checked |
| 2 | Ball bearing **6801** | 12 × 21 × 5 | Ø21 seats in both carrier output halves: one on the input-shaft tip, one on the stage-1 carrier's Ø12 stub | not checked |
| 6 | Steel pin | Ø6 × **22** (STEP label says "6x11") | Planet axles; full height of a carrier pair (5 mm in the output half, 4 mm in the motor-side half, 13 mm free) | not checked |
| 6 | Plain bushing | Ø8 OD × Ø6 ID × 10 | In each planet bore (Ø8 × 9), protrudes **0.5 mm** each side | not checked |
| 12 | Washer | Ø11.8 × Ø6.2 × 1.3 as modelled | Either side of each planet | not checked |
| 1 | NEMA 17 stepper | Model: 41 × 41 × 40 body, Ø5 D-shaft protruding 23.3, Ø23 × 2 pilot, M3 holes 5.5 deep, **no rear shaft** | — | already owned |

---

## 4. Fasteners, derived from the holes

The STEP has no screws or inserts, only their holes. "Travel" is the length of screw shank between the
underside of the head and the face where the thread begins to engage. All inserts are assumed to be
M3 × 5 mm, pressed **flush** with the pocket mouth.

| Joint | Qty | Hole geometry (measured) | Travel | Thread room | Screw | Engagement |
| --- | --- | --- | --- | --- | --- | --- |
| Front cover → housing | 6 | Ø7.5 × 3.2 counterbore, Ø3.0 × 5.8 clearance; housing pocket Ø4.2 × 10 | 5.8 | 10 | **M3 × 12 socket head** | 6.2 (10 mm also works: 4.2) |
| Back cover → housing | 6 | Ø3.0 × 10.8 clearance, Ø7.5 × 3.2 counterbore; housing pocket Ø4.2 × 10 | 10.8 | 10 | **M3 × 16 socket head** | 5.2 (max length 20) |
| NEMA plate → back cover | 4 | Ø3.0 × 10 through plate, no counterbore; back-cover pocket Ø4.2 × **6.0** | 10.0 | 6.0 | **M3 × 14 socket head** (see note) | 4.0 |
| Motor → NEMA plate | 4 | 90° countersink Ø7 × 2 + Ø3.0 × 8, head on the gearbox side; motor hole 5.5 deep in the model | 8 below head | 5.5 (model) | **M3 × 14 countersunk** (length includes head) | 4.0 |
| Carrier halves | 6 (3 per carrier) | 90° countersink Ø7.5 × 2.35 + **Ø2.8** × 2.65 passage; mating pocket Ø4.2 × 8 | 2.65 | 8 | **M3 × 10 countersunk** | 5.0 (12 mm also fits: 7.0) |
| Output face → driven part | 4 | Ø4.2 × 10 pockets on Ø14 bolt circle | — | 10 | M3 socket head, driven flange + 5 | up to 9 |
| Input shaft → motor shaft | 1 | radial Ø4.0 × 5.9 | — | — | grub (set) screw, see "to verify" | — |

**NEMA plate → back cover note:** the README and `BOM.md` give M3 × 16. A 16 mm screw reaches
exactly 6.0 mm below the plate, which is the full pocket depth, so it bottoms out on the PLA floor
and may stop clamping before the head is tight. A washer cannot fix it, because the screw head
already sits within 0.1 mm of the motor body. M3 × 14 gives 4 mm of thread in the 5 mm insert.
`BOM.md` notes OnlyScrews does not stock 14 mm; the alternative is M3 × 16 with 1 mm filed off.

**Heads.** Covers: socket head only. Head height 3.0 mm in a 3.2 mm counterbore, so no washer.
Carriers and motor: countersunk (flat head) only.

**Heat-set inserts:** 26 × M3 × 5 (12 in the housing, 6 in the carrier motor-side halves, 4 in the back cover,
4 in the output face). Add 1 more if the grub hole takes an insert.

| Screw | Qty | Price (from `BOM.md` §6, OnlyScrews, Sep 2026, ex-GST) |
| --- | --- | --- |
| M3 × 12 socket head | 6 | ₹3.40 each |
| M3 × 16 socket head | 6 (+4 if you file them for the NEMA plate) | ₹3.60 each |
| M3 × 14 socket head | 4 | not stocked there, not checked elsewhere |
| M3 × 14 countersunk | 4 | not stocked there, not checked elsewhere |
| M3 × 10 countersunk | 6 | ₹1.60 each |
| M3 × 5 heat-set insert | 26–27 | ₹4.60 each |
| Grub screw | 1 | not checked |

---

## 5. Disagreements with the existing documents

| # | Item | README / BOM.md says | CAD says | Verdict |
| --- | --- | --- | --- | --- |
| 1 | Bearing count | README: 2 × 6805, 2 × 6803, 2 × "6802" (6). BOM.md: 1 × 6805, 2 × 6803, 2 × "6802" (5) | 1 × 25×37×7, 1 × 17×26×5, 2 × 12×21×5 (4) | **CAD is right.** The printed parts have exactly four bearing-sized seats: Ø37 × 7 (front cover), Ø26 × 5 (back cover), Ø21 × 5 × 2 (carrier output halves). The front cover's Ø26 × 3.5 bore that `BOM.md` calls a second 6803 seat sits 0.5 mm around the Ø25 output hub: a 17 mm-bore bearing cannot fit there. The Ø72 recesses in the housing and back cover are clearance for the Ø56 carriers. |
| 2 | 12 × 21 × 5 bearing name | "6802" | 12 × 21 × 5 | **The name is wrong.** By standard 68xx sizing, 12 × 21 × 5 is a **6801**. A 6802 is 15 × 24 × 5, and the cycloidal `BOM.md` correctly uses 6802 for 15 × 24 × 5. A 6802 will not fit these Ø21 seats. Check which size you actually have. |
| 3 | Planet pin | STEP label "Pin 6x11mm" | Ø6 × 22 | Label is wrong; 22 mm (as README) is right. |
| 4 | Bushing overhang | "1 mm protrudes each side" | 10 mm bushing in a 9 mm gear: **0.5 mm** each side | README arithmetic error. |
| 5 | Washers | "M6 washers" | Modelled Ø11.8 × Ø6.2 × **1.3** | A standard DIN 125 M6 washer is 12 × 6.4 × 1.6. Planet cavity is 13.0 long: modelled stack 1.3 + 10 + 1.3 = 12.6 (0.4 float); with 1.6 mm washers it is 13.2, **0.2 mm too long**. |
| 6 | NEMA plate → back cover screw | M3 × 16 | Pocket only 6.0 deep | 16 mm bottoms out; use 14 (see §4). |
| 7 | Motor screw substitute | `BOM.md` §6 budgets M3 × 12 countersunk "for the motor joint" | Plate is 10 mm, head flush | 12 mm gives only 2 mm of thread in the motor. Use 14 mm. |
| 8 | Counterbore size | Ø7.4 × 3.1 (README), Ø7.4 × 3.1–3.2 (BOM.md) | Ø7.5 × 3.2 | Minor. |
| 9 | Grub screw | `BOM.md`: M4 × 5–6 | Radial hole Ø4.0 | Ø4.0 is clearance size for M4, so an M4 grub screw has nothing to thread into (M4 tap drill is 3.3). It is the right size for an M3 heat-set insert plus an M3 grub. |
| 10 | Grub access | README step 5: tighten through the access hole | Plate access hole at Y = 19.5, grub hole at Y = 16.6 | **2.9 mm out of line** in the assembled model; the shaft can float about 1.3 mm toward the motor, which still leaves about 1.6 mm. A 1.5 mm or 2 mm hex key may not reach the socket. |
| 11 | Rear motor shaft | `cad/README.md` assumes a rear shaft | STEP motor has none | Consistent with your build: magnet on the shaft end through the back-plate hole. |

---

## 6. Salvage plan for the rebuild (from the user, 11 Nov 2026)

| Item | Qty | Status | Notes |
| --- | --- | --- | --- |
| All 15 printed parts | 15 | **reprint** | Sliced 11 Nov 2026 (Bambu Studio CLI, P1S 0.4, 0.20 mm Standard, 2 walls, 15 % grid infill, no supports, Bambu PLA Basic): **one plate, 164 g / 54.1 m, ≈ 5 h 10 min** — `rebuild/planetary_rebuild_all_parts_P1S.3mf` |
| 6805 / 6803 / 12×21×5 bearings | 1 / 1 / 2 | **reuse** | The old unit ran with these, so the 12×21×5 pair are 6801-size whatever their label says |
| Ø6 × 22 pins | 6 | **reuse** | |
| Washers | 12 | **reuse** | Old build fitted, so the thickness worked in practice |
| Bushings 8 × 6 × 10 | 6 | **not used** | Never found; old planets ran without them (Ø8 bore on a Ø6 pin = 1 mm radial slop). See design change 1 |
| M3 heat-set inserts | 26 (+1 for grub) | **buy** | Old ones clogged during install |
| M3 screws | 26 | **buy** | Old ones were too short; plates were taped on |
| Grub screw | 1 | **buy** | Size to confirm (see §5 item 9) |
| NEMA 17 stepper | 1 | **buy** | New motor must also expose the rear shaft end for the AS5600 magnet |
| AS5600 encoder | 1 | **reuse** (spare on hand) | |

### Buy list with known prices

Prices from `BOM.md` §6 (OnlyScrews, Sep 2026, ex-GST) and the cycloidal `BOM.md` (motor); anything else is "not checked".

| Item | Qty | Unit ₹ | Line ₹ |
| --- | --- | --- | --- |
| M3 × 12 socket head (front cover) | 6 | 3.40 | 20.40 |
| M3 × 16 socket head (back cover) | 6 | 3.60 | 21.60 |
| M3 × 16 socket head, file 2 mm off → 14 (NEMA plate; 14 not stocked) | 4 | 3.60 | 14.40 |
| M3 × 10 countersunk (carriers) | 6 | 1.60 | 9.60 |
| M3 × 16 countersunk, file 2 mm off → 14 (motor; 14 not stocked) | 4 | not checked | — |
| M3 × 5 heat-set insert | 27 | 4.60 | 124.20 |
| Grub screw | 1 | not checked | — |
| **Fasteners with a known price** | | | **190.20** (+18 % GST ≈ 224) |
| NEMA 17, 42-40, Ø5 D-shaft (Amazon.in, cycloidal BOM) | 1 | 549.00 | 549.00 |

OnlyScrews shipping is free only above ₹799, so add these screws to the cycloidal OnlyScrews order
rather than ordering them separately.

---

## 7. Rebuild changes (user's modifications to the original design)

Files are in `rebuild/`. The originals in the STL folder are unchanged.

| # | Change | Why | Cost | Reprint | File |
| --- | --- | --- | --- | --- | --- |
| 1 | Planet bore Ø8.0 → **Ø6.2**, no bushing; planet runs directly on the Ø6 steel pin with grease | The 8 × 6 × 10 bushings were never found; the old build ran a Ø8 bore on a Ø6 pin (≈1 mm radial slop), so the planets could rock | ₹0 (6 bushings dropped from the BOM) | 6 planets | `rebuild/Planet gear - 15T helical - bore 6.2.stl` / `.step` |

| 2 | All M3 clearance holes → **Ø3.3** (front cover ×6, back cover ×6, NEMA plate ×8, both carrier output halves ×3 each) | Holes were Ø3.0 (and Ø2.8 in the carriers), the same as or smaller than the screw, so screws threaded into the PLA instead of passing through | ₹0 | front cover, back cover, NEMA plate, 2 carrier output halves | `rebuild/Front cover - M3 3.3.stl`, `Back cover - M3 3.3.stl`, `NEMA17 mount - M3 3.3 - grub access.stl` (includes change 3), `Carrier stage 1 - Output - M3 3.3.stl`, `Carrier stage 2 - Output - M3 3.3.stl` (+ `.step`) |

| 3 | Motor-plate hex-key access hole (Ø3.5, radial, −X side) moved from 5.5 mm to **3.25 mm** above the back-cover face (assembly Y 19.5 → 17.25); old hole filled | The grub screw sits at Y 16.6–17.9 (the input shaft can slide 1.3 mm), so the old hole was 1.6–2.9 mm out of line and the key could not reach | ₹0 | NEMA plate (already reprinting) | `rebuild/NEMA17 mount - M3 3.3 - grub access.stl` / `.step` |

Change 3 details: checked in CAD with a 1.5 mm hex key (for an M3 grub screw). It reaches the grub socket with
zero overlap at both ends of the shaft's travel; with the old plate it hit the plate at every position. Grub
fixing: an M3 × 5 heat-set insert in the input shaft's Ø4.0 radial hole, plus an M3 grub screw
(length not checked; the hole wall is 5.9 mm, so M3 × 4–6 depending on how far the insert sits in). At assembly,
turn the input shaft until its grub hole faces the access hole, then tighten onto the flat of the motor shaft.

Change 2 details: only the plain hole sections changed. Counterbores, countersinks, insert pockets and
every other feature are untouched; the volume removed matches the calculation for each part. The STLs
are in the same position and orientation as the original STLs. The covers and NEMA plate match exactly;
each carrier half matches on the end that faces the bed, but is turned by an arbitrary angle about its
axis, which does not affect printing. Wall left between the cover holes and the Ø85 rim: 1.6 mm (was 1.75).

Change 1 details: teeth, width (9.0) and end chamfers are unchanged; only the bore was filled and re-cut
(volume +180.7 mm³, which matches the ring calculation exactly). Print it flat, like the original. The bore
assumes your Bambu hole compensation is around +0.04 mm. **Print one planet first:** it should spin freely
on a pin with no rocking. If it binds, ream the bore with a 6.2–6.3 mm drill by hand. If it rocks, re-export
at Ø6.1.

---

## 8. To verify on the real parts

1. **Which "6802" bearings you have:** measure the bore. 12 mm means a 6801, which fits; 15 mm means a true 6802, which does not.
2. **Washer thickness:** if 1.6 mm, either use thinner (1.0–1.2 mm) shim washers or check the planet cavity on the old carriers.
3. **Motor thread depth:** the model says 5.5 mm; `BOM.md` assumed ~4.5. With 4.5 mm, an M3 × 14 countersunk screw (4.0 engagement) still fits.
4. **Clearance holes are Ø3.0 for M3** (covers ×12, NEMA plate ×8) and **Ø2.8** in the carrier output halves (×6). These are line-to-line or undersize. M3 screws will thread into the PLA rather than pass through, so drill them to 3.2–3.4 mm.
5. **Grub screw:** what did the old build use, M4 tapped into PLA or an M3 insert? And did the hex key reach through the access hole?
6. **Bushing material** (bronze, brass, steel?) and pin material are not stated anywhere.
7. **Planet pin retention:** pins sit flush with both carrier outer faces and are held axially only by the 2 mm gap to the neighbouring part. Check that the old pins were a press fit.
