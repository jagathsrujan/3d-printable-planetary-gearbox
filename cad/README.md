# AS5600-to-NEMA-17 press-fit encoder mount (PLA)

Rear-mounted AS5600 breakout on a NEMA 17. The holder is a compliant PLA print:
a slotted skirt grips the motor body and a snap-rail pocket holds the sensor
board. No screws are needed; the four M3 holes are optional retention.

## Files

| File | What it is |
| --- | --- |
| `encoder_mount.FCStd` | Clean FreeCAD assembly: motor, sensor, magnet, `Holder_PLA`. |
| `encoder_mount_holder.step` / `.stl` | The printable holder. |
| `encoder_mount_assembly.step` | Motor + holder + sensor + magnet. |
| `nema17_17he15_1504s.step` | Reference motor model. |
| `as5600_module_and_magnet.step` | Reference sensor + 6 × 2.5 mm magnet. |

## Interfaces

**Motor** — 42.3 × 42.3 × 38 mm body, 4 mm corner chamfers, 4 × M3 at 31 × 31 mm,
Ø22 × 2 mm front boss, Ø5 × 23.5 mm front D-shaft, Ø12 × 2 mm rear boss.
The model adds a Ø5 × 2.5 mm rear shaft carrying the magnet.

**Sensor** — 23.0 × 23.0 × 1.6 mm PCB (actual modules about 23.1 × 22.5),
4 × Ø3.2 mm at 16 × 16 mm, AS5600 SOIC-8 (3.9 × 4.9 × 1.75 mm) at the centre,
3-pin + 4-pin 2.54 mm headers on the flat back. Magnet: Ø6 × 2.5 mm diametric.

## Holder — PLA-compliant design

| Feature | Value |
| --- | --- |
| Overall | 46.3 × 46.3 × 18 mm (10 mm plate + 8 mm skirt) |
| Motor socket | 42.7 × 42.7 × 8 mm, R4.5 (0.2 mm/side clearance) |
| Grip ribs | 3 × 0.25 mm high × 8 × 4 mm on +Y, +X, −X walls |
| Effective motor grip | 42.2 mm → ≈0.05 mm/side press, not a rigid 0.15 mm |
| Corner reliefs | 4 × 4 mm wide × 7 mm deep, R1 bottom; leaves a **1 mm living hinge** |
| Mouth lead-in | 1 mm deep × 2 mm wide counterbore (44.7 mm) |
| Board pocket | 23.2 × 23.2 × 1.9 mm deep, R1 corners |
| Board snap | 0.3 mm high × 22.6 mm X-only rails, 45° lead-in; Y open at 23.2 mm |
| Board seat | Back 0.3 mm below outer face; chip side faces the motor |
| Pocket walls | 0.6 mm, deliberately flexible |
| Flex slots | 2 × 1.6 × 14 mm at x = ±13.0 mm, with Ø2 stress-relief holes |
| Component/magnet relief | Ø18 mm through the pocket floor |
| Board removal | 2 × Ø2.5 mm at (0, ±9.5) — push from the motor side |
| Optional screws | 4 × Ø3.2 at 31 × 31 mm, Ø6.5 × 3 mm counterbores |
| Connector relief | 18 × 8 mm through the skirt on −Y, R1.5 corners |

The board is gripped on its **long (X) edges only**: 0.2 mm per side on a 23.0 mm
board, 0.25 mm per side on a 23.1 mm board. The short (Y) direction has 23.2 mm
opening — 0.35 mm total clearance on a 22.5 mm board — so print tolerance does
not fight the snap.

**Air gap.** Chip face z = −6.35, magnet face z = −5.0: **1.35 mm**. Target
0.5–3 mm; move the magnet on the rear shaft with a 0.5–1 mm spacer if needed.

## Print (PLA)

- **Sensor face down**, no supports, brim recommended.
- 0.2 mm layers, **3 walls**, 40 % infill, 4 top/bottom layers.
- The 45° snap-lip taper, 1 mm hinge, vertical corner notches, grip ribs and mouth
  counterbore are all self-supporting.
- The pocket floor ring is only ~2.6 mm wide around the Ø18 relief, so it bridges
  cleanly.
- PLA is brittle in bending: do not force the board or motor. If the snap is too
  tight, file the lip or scale the pocket +0.1–0.2 mm; if loose, add a strip of
  tape or use the four M3 holes only if your motor's rear holes are threaded.

## Assembly

1. Solder the 3-pin and 4-pin headers on the **flat back** of the sensor board.
2. Glue the magnet to the motor's rear shaft, centred on the shaft axis.
3. Slide the holder over the motor's **front shaft** (the shaft passes through
   the Ø18 relief) and press it onto the rear 8 mm. The skirt walls flex at the
   corner reliefs and the grip ribs snap onto the body; the connector exits
   through the side opening.
4. Press the board into the pocket, **chip toward the magnet**, headers outward.
   It passes the 45° lip, the X rails snap over its long edges, and it seats on
   the ledge 0.3 mm below the outer face.
5. Check the chip-to-magnet gap (0.5–3 mm) and centre the magnet over the chip.
   Wire and calibrate.

To remove the board, push it out through the two Ø2.5 mm access holes; the X
rails flex and release. To remove the holder, pull it straight off the motor.

## Assumption to check

This mount puts the sensor on the **rear shaft**. The linked Robu 17HE15-1504S
is single-shaft, so it has nothing at the rear to sense. The photos show a motor
with a rear shaft/boss; this CAD assumes a double-shaft motor or a rear magnet
carrier. If the motor is single-shaft, the encoder has to go on the gearbox
output (the Ø14 mm magnet-cap bolt circle) instead.
