# Bill of Materials — Two-Stage 16:1 Planetary Gearbox

Complete buy-list: printed parts, hardware, and the motor drive.

Fastener lengths below are **measured from the STL geometry**, not copied from the original
build notes — each joint was checked against the counterbore depth, clearance length and
insert pocket in the model. See [Screw joint measurements](#5-screw-joint-measurements) for the
numbers behind the lengths.

---

## 1. Printed parts (PLA)

| Qty | Part | File |
| --- | --- | --- |
| 1 | Ring gear + housing, both stages | `Ring gear.stl` |
| 1 | Front cover (output side) | `Front cover.stl` |
| 1 | Back cover (motor side) | `Back cover r1.stl` |
| 1 | NEMA 17 mounting plate | `NEMA17 mount r2.stl` |
| 1 | Input shaft + stage-1 sun | `Input shaft r1.stl` |
| 6 | Planet gear, 15 tooth helical | `Planet gear - 15 tooth helical.stl` |
| 2 | Stage 1 carrier halves | `Carrier p1 - stage 1.stl`, `Carrier p1 - stage 1 - Output.stl` |
| 2 | Stage 2 carrier halves | `Carrier p1 - stage 2.stl`, `Carrier p2 - stage 2 - Output.stl` |

The stage-1 carrier's output half carries the stage-2 sun gear — there is no separate sun part.

---

## 2. Fasteners

| Qty | Screw | Joint |
| --- | --- | --- |
| 6 | M3 × 12 socket head (DIN 912) | Front cover → housing |
| 6 | M3 × 16 socket head (DIN 912) | Back cover → housing |
| 4 | M3 × 16 socket head (DIN 912) | NEMA plate → back cover |
| 6 | M3 × 10 countersunk (DIN 965) | Carrier halves (3 per carrier) |
| 4 | M3 × 14 countersunk (DIN 965) | Motor → NEMA plate |
| 4 | M3 × (driven flange + 5 mm) socket head | Output face |
| 1 | M4 × 5–6 grub (set) screw | Input shaft → motor shaft |

| Qty | Insert | Location |
| --- | --- | --- |
| 26 | M3 heat-set, brass, Ø4.0–4.2 × 5 mm | 12 housing (6 per cover face), 6 carrier halves, 4 back cover, 4 output face |

Threaded inserts must sit **flush with the pocket mouth** — the screw lengths assume it. If an
insert sinks deeper, add that depth to the screw length.

**Heads and washers.** The covers, NEMA plate and output face use *cylindrical* counterbores
(Ø7.4 × 3.1–3.2 mm), so they need socket or button heads — a countersunk screw will not seat.
Head-only depth is 3.1–3.2 mm, so **no washers** under those screws. The carriers and the motor's
own bolt holes have 90° countersinks and need countersunk (flat) heads.

**No screw shorter than 10 mm is used anywhere in this design.**

---

## 3. Bearings, pins, bushings

| Qty | Item | Where |
| --- | --- | --- |
| 1 | Ball bearing 6805 — 25 × 37 × 7 | Front cover, inner seat (Ø37 × 7), on the stage-2 output journal |
| 2 | Ball bearing 6803 — 17 × 26 × 5 | Front cover outer seat (Ø26 × 3.5, protrudes ~1.5 mm for the driven part's pilot), back cover input seat (Ø26 × 5) |
| 2 | Ball bearing 6802 — 12 × 21 × 5 | Stage-1 carrier pocket (input shaft tip), stage-2 carrier pocket (stage-1 carrier's output stub) |
| 6 | Steel cylinder rod 6 × 22 mm | Planet pins |
| 6 | Bushing 8 mm OD × 10 mm | In each planet (10 mm bushing in a 9 mm gear: 1 mm protrudes each side) |
| 12 | M6 washer | Either side of each planet gear |

> The STLs provide one Ø37 × 7 seat (front cover). The source build article lists two 6805 —
> these models only have a home for one.

---

## 4. Motor and drive electronics

| Qty | Item | Notes |
| --- | --- | --- |
| 1 | NEMA 17 stepper, 42 × 40 mm, 1.5 A, 0.4 N·m, **D-shaft** | 31 mm mounting pattern, 5 mm × 22–24 mm shaft |
| 1 | A4988 driver + heatsink | Use DRV8825 or TMC2209 if running above ~1 A |
| 1 | Arduino Nano (or ESP32 for wireless commands) | Step/direction pulses |
| 1 | 12 V 2 A supply | 24 V gives more torque at speed |
| 1 | 100 µF electrolytic capacitor | Across the driver's VMOT/GND — required |
| 1 | A3144 Hall sensor + 6 × 3 mm magnet | Home reference at power-up |
| 1 | AS5600 12-bit magnetic encoder + 6 × 2.5 mm diametral magnet | Optional: absolute angle, closed loop |
| — | Jumpers, headers, 4-core cable | |

**Sizing.** The gearbox needs ≈0.25 N·m at the input for its ≈2 N·m output, so a 0.4 N·m motor
has margin at ~1.2 A. Drive it from full-step (3200 steps per output revolution, 0.1125°/step).
Keep the input under ~300–400 rpm (≤20–25 rpm out): the planets run on plain bushings and the
helical teeth add axial load.

**Motor fastening.** Bolt the NEMA plate to the motor first with the 4 × M3 × 14 countersunk
screws, slide the shaft into the input shaft's Ø5 × 25 mm bore (do not bottom it), tighten the
M4 grub screw through the gap around the plate's central bore, then fasten the plate to the back
cover with the 4 × M3 × 16.

---

## 5. Screw joint measurements

Measured from the meshes; "head seat" is the distance the screw shank travels before reaching
the housing face.

| Joint | Counterbore | Clearance / travel | Engagement | Screw |
| --- | --- | --- | --- | --- |
| Front cover → housing | Ø7.4 × 3.2 | 5.8 mm | 10 mm blind pocket, 5 mm insert | 12 mm |
| Back cover → housing | Ø7.4 × 3.2 | 10.8 mm | 10 mm blind pocket, 5 mm insert | 16 mm |
| NEMA plate → back cover | — (through holes) | 10.0 mm (plate thickness) | Ø4.1 × 6 mm pocket, 5 mm insert | 16 mm |
| Carrier halves | 90° countersink, 2.4 deep | 5.0 mm (2.6 passage + interface) | Ø4.2 × 7.9 mm pocket, 5 mm insert | 10 mm |
| Motor → NEMA plate | 90° countersink | 10.0 mm (plate) | ~4.5 mm in the motor | 14 mm |
| Output face | socket head | driven flange | Ø4.2 × 9.9 mm pocket on Ø14 BC | flange + 5 mm |
| Input shaft coupling | — | radial Ø4.0 cross-hole at the motor end | — | M4 × 5–6 |

A 6 mm screw reaches none of the cover joints: it engages 0.2 mm in the front cover and is
4.8 mm short in the back cover.

---

## 6. Sourcing (India, prices as of Sep 2026)

OnlyScrews (`onlyscrews.in`) stocks M3 socket head in 6/8/10/12/16/20/25/30/35/40/50/60 mm and
countersunk in 6/8/10/12/16/20/25/30 mm — **14 mm and 15 mm are not stocked in either head
style**, so budget either the 12 mm countersunk substitute for the motor joint or a source for
the 14 mm.

| Item | Unit | Qty | Subtotal |
| --- | --- | --- | --- |
| M3 × 12 socket head | ₹3.40 | 6 | ₹20.40 |
| M3 × 16 socket head | ₹3.60 | 10 | ₹36.00 |
| M3 × 10 countersunk | ₹1.60 | 6 | ₹9.60 |
| M3 × 12 countersunk *(motor joint)* | ₹1.80 | 4 | ₹7.20 |
| **Fasteners total** | | **26** | **₹73.20** |

Add ~18 % GST at checkout; free shipping applies only above ₹799. M3 × 5 mm 3D-printing knurled
brass inserts (OD 4.4 mm, right for the Ø4.2 pockets) are ₹4.60 each — 26 for ₹119.60.

Motor, driver and controller are commodity hobby parts (Robu, Flyrobo, Amazon): NEMA 17 ≈ ₹600–900,
A4988 ≈ ₹150, Arduino Nano ≈ ₹250, 12 V 2 A supply ≈ ₹250.
