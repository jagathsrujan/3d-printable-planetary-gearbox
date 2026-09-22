# 3D Printed Two-Stage Planetary Gearbox (16:1)

A 16:1 reduction planetary gearbox designed for a NEMA 17 stepper motor, printed in PLA.
Two 4:1 planetary stages in series, with the ring gear doubling as the gearbox housing.

This design is a rebuild of the gearbox from [How To Mechatronics — How Planetary Gears Work](https://howtomechatronics.com/how-it-works/how-planetary-gears-work-3d-printed-planetary-gearbox-design-and-test/)
(originally modelled in Onshape). The STLs here are the printable output.

---

## Design specifications

| Parameter | Value |
| --- | --- |
| Overall ratio | 16:1 (two stages × 4:1) |
| Gear module | 1.5 |
| Tooth counts | Sun 15T / Planet 15T / Ring 45T |
| Planets per stage | 3 |
| Tooth profile | Helical (meshing pair must have opposite helix direction) |
| Input | NEMA 17 stepper |
| Material | PLA |

Single-stage planetary sets realistically span 3:1 to 10:1, so a whole-number
~15:1 target requires two stages. The final ratio is the **product** of the stage ratios
(4 × 4 = 16), and torque scales with the same product in an ideal gearbox.

The two planetary design rules both hold here:

- `Zring = Zsun + 2 × Zplanet` → `45 = 15 + 2(15)`
- `(Zsun + Zring) / n_planets` = whole number → `(15 + 45) / 3 = 20`

The second rule keeps the planets equally spaced so the radial forces from the sun
cancel out. Unequal spacing produces a net force that makes the sun wobble, causing
vibration and uneven load sharing.

A 0.1 mm backlash offset was applied when generating the gear teeth, because FDM parts
print slightly oversized and gears without it will not mesh.

---

## STL files

| File | Description |
| --- | --- |
| `Ring gear.stl` | Ring gear + housing, both stages (the internally-toothed housing) |
| `Front cover.stl` | Output-side cover plate, 6 × M3 |
| `Back cover r1.stl` | Motor-side cover plate, 6 × M3 + 4 × M3 NEMA plate mount |
| `NEMA17 mount r2.stl` | Motor mounting plate, 31 mm motor pattern + 33 × 48 mm gearbox pattern |
| `Input shaft r1.stl` | Sun gear of stage 1 + input shaft (grub-screw coupling to the motor) |
| `Planet gear - 15 tooth helical.stl` | Planet gear, 6 off |
| `Carrier p1 - stage 1.stl` | Stage 1 carrier, upper half |
| `Carrier p1 - stage 1 - Output.stl` | Stage 1 carrier, lower (output-side) half |
| `Carrier p1 - stage 2.stl` | Stage 2 carrier, upper half |
| `Carrier p2 - stage 2 - Output.stl` | Stage 2 carrier, lower half + output face |
| `CUTOUT - *.stl` | Sectioned versions of the covers and ring gear, for visualisation |

The carrier halves interlock: the planet pins are supported at **both** ends
(z ≈ 0–5 mm and z ≈ 18–22 mm), which is why the carriers look bulky.

---

## Bill of materials

### 3D printed parts

All PLA. One housing, two covers, one motor plate, one input shaft, six planet gears,
and four carrier halves (two halves per carrier × two carriers).

### Hardware

| Item | Spec | Qty |
| --- | --- | --- |
| Steel cylinder rod | 6 mm × 22 mm (planet pins) | 6 |
| Bushings | 8 mm OD × 10 mm long | 6 |
| Ball bearing | 6805 — 25 × 37 × 7 mm | 2 |
| Ball bearing | 6803 — 17 × 26 × 5 mm | 2 |
| Ball bearing | 6802 — 12 × 21 × 5 mm | 2 |
| Threaded inserts | M3 heat-set, Ø4.0–4.2 × 5 mm | 26 |
| M6 washers | either side of each planet gear | 12 |

### M3 bolts

These lengths were measured directly from the STL meshes. The original build notes never
specify bolt lengths, and the covers are much thicker than they look — the back cover in
particular needs a long bolt before it reaches the insert.

| Joint | Qty | Fastener | Length |
| --- | --- | --- | --- |
| Front cover → housing | 6 | M3 socket head (DIN 912) | **12 mm** |
| Back cover → housing | 6 | M3 socket head | **16 mm** |
| Carrier halves | 6 | **M3 countersunk** (DIN 965) | **10 mm** |
| NEMA plate → back cover | 4 | M3 socket head | **16 mm** |
| Motor → NEMA plate | 4 | **M3 countersunk** | **14 mm** |
| Output face → driven part | 4 | M3 socket head | flange thickness + ~5 mm |

Notes:

- The covers use a **cylindrical counterbore** (Ø7.4 × 3.1 mm), so socket-head screws fit
  but an M3 washer does not — head + washer is 3.5 mm, deeper than the 3.1 mm recess.
- The carriers and the motor holes use a **90° countersink**, so those need countersunk
  (flat head) screws, not socket heads.
- The motor bolt lengths assume a typical NEMA 17 threaded hole depth of ~4.5 mm. Check
  your motor and adjust.

### Where the bolts land (measured)

| Feature | Dimension |
| --- | --- |
| Housing insert pockets | Ø4.2 × 10.0 mm deep, 6 per cover |
| Front cover | counterbore Ø7.4 × 3.1, then Ø3.0 × 5.8 clearance — head seat 5.9 mm from housing face |
| Back cover | Ø3.0 × 10.8 clearance, then counterbore Ø7.4 × 3.1 — head seat 10.8 mm from housing face |
| Carrier lower half | 90° countersink (Ø2.8 → Ø7.5 over 2.4 mm), then Ø2.8 × 2.6 passage |
| Carrier upper half | Ø4.2 × 7.9 mm insert pocket |
| NEMA plate thickness | 10.0 mm |
| Back cover NEMA pockets | Ø4.1 × 6.0 mm deep |
| Output face | 4 × Ø4.2 × 9.9 mm pockets on a Ø14 mm bolt circle |

Threaded inserts should be installed **flush with the pocket mouth**; the bolt lengths
above assume that. If you sink an insert deeper, add that depth to the bolt length.

---

## Assembly

1. Press the M3 heat-set inserts into the housing (6 per cover face), both upper carrier
   halves (3 each), the back cover (4), and the stage 2 output face (4).
2. Install the 6 mm planet pins into the carrier lower halves, fit the 8 mm bushings into
   the planet gears (10 mm bushing in a 9 mm gear, so 1 mm protrudes each side), and fit
   M6 washers either side.
3. Bolt the carrier halves together with the 10 mm countersunk screws.
4. Slide the carriers into the housing, fit the bearings, then fit and bolt the front and
   back covers.
5. Bolt the NEMA plate to the motor, slide the motor shaft into the input shaft, then
   fasten the plate to the back cover. Tighten the input shaft grub screw through the
   access hole in the plate.
6. Lubricate the gear teeth. Grease reduces friction but increases backlash — the two are
   directly traded against each other.

### Print settings that matter

The two settings that dominate dimensional accuracy on a filament printer:

- **Horizontal Expansion:** 0.02 mm
- **Hole Horizontal Expansion:** 0.04 mm

Run your own test prints; these values are printer-specific.

---

## Measured performance

**Backlash:** ~18 arcminutes. Essentially no coercive play at 100 mm without load;
~0.6–1.2 mm displacement under hand force, and ~0.2–0.3 mm each way under a 1.5 N load.

**Torque / efficiency:** output was measured at 20 N on a 100 mm arm, i.e. **≈ 2 Nm**.
A bare NEMA 17 is about 0.28 Nm, so the gain is roughly 7× rather than the ideal 16× —
an efficiency of about **50%**.

The losses come from friction: the gears mesh tightly (which is also why the backlash is
so low), the planets run on plain bushings rather than ball bearings, and the helical
teeth generate axial loads that bushings cannot take. Reducing backlash and improving
efficiency are competing goals here.

> Note: the source article lists these figures as "200 Nm" and "28 Nm", which is off by a
> factor of 10. The stated 7–8× torque gain only makes sense with the corrected values
> (2 Nm / 0.28 Nm), so these are the figures used above.

---

## Credits

Design by [How To Mechatronics](https://howtomechatronics.com/how-it-works/how-planetary-gears-work-3d-printed-planetary-gearbox-design-and-test/).
Released as a build-along tutorial; this repository collects the printable models and
documents the hardware sizing.
