# Electronics Brief — Motor Drive and Orientation Control

A short hand-off spec for whoever does the electrical side of this build.

**The mechanism is finished.** The gearbox is a two-stage 16:1 planetary reduction
(module 1.5, sun 15T / planet 15T / ring 45T, 3 planets per stage), assembled, lubricated
and characterised: ≈2 N·m at the output at ≈50 % efficiency, ≈18 arcmin of backlash.

**Scope:** everything from the motor's 4-pin connector onward — motor, driver, controller,
power, sensors, firmware. The mechanics are done; please do not re-engineer the gearbox,
the gears, or the housing.

---

## 1. What you need

| Qty | Item | Notes |
| --- | --- | --- |
| 1 | NEMA 17 stepper, 42 × 40 mm, 1.5 A, 0.4 N·m, **D-shaft** | Fits the printed plate as-is |
| 1 | A4988 driver + heatsink | DRV8825 or TMC2209 if running above ~1 A |
| 1 | Arduino Nano (or ESP32 for wireless commands) | |
| 1 | 12 V 2 A supply | 24 V gives more torque at speed |
| 1 | 100 µF electrolytic capacitor | Across the driver's VMOT/GND — required |
| 1 | A3144 Hall sensor + 6 × 3 mm magnet | Home reference |
| 1 | AS5600 12-bit magnetic encoder + 6 × 2.5 mm diametral magnet | Optional, for closed loop |
| — | Jumpers, headers, 4-core cable | |

Full fastener list, including the fourth item for the motor joint, is in [BOM.md](BOM.md).

Test rig: 100 mm lever and a luggage scale (torque), a protractor or pointer taped to the
output (angle), a multimeter, and something to measure motor temperature.

## 2. Mechanical interface

- Motor bolts to the printed NEMA plate with **4 × M3 × 14 countersunk** screws — bolt the
  plate to the motor first, then the plate to the back cover with 4 × M3 × 16.
- The motor shaft (5 mm × 22–24 mm) slides into the input shaft's **Ø5 × 25 mm** bore.
  **Do not bottom it** — check it turns freely before tightening.
- Lock it with the **M4 grub screw**; access is through the annular gap between the shaft
  (Ø17) and the plate's central bore (Ø23.8).
- The output shaft is Ø25 and protrudes 4 mm. Its face has 4 × M3 insert pockets on a
  Ø14 mm bolt circle — that is where the magnet cap for the encoder mounts.

## 3. Constants — use these instead of re-deriving

| Quantity | Value |
| --- | --- |
| Gear ratio | 16:1 (input faster) |
| Motor steps | 200 full steps/rev |
| Output resolution | **3200 full steps per output revolution = 0.1125°/step** (8.889 steps/degree; × microstep setting) |
| Backlash | ≈18 arcmin ≈ **0.3°** — positioning tolerance cannot be tighter |
| Torque | ≈0.25 N·m at the input for the ≈2 N·m output |
| Motor current | ~1.2 A is plenty; **do not exceed 1.5 A**. Vref ≈ 0.96 V for 1.2 A on a 0.1 Ω A4988 |
| Speed | Input **≤ 300–400 rpm** (≤ 20–25 rpm output) → ~1200 steps/s at full step |
| Encoder resolution | AS5600 12-bit = 0.088° (finer than the backlash) |

## 4. Required behaviour

**Command interface** over serial (or BLE on an ESP32):

- absolute output angle in degrees (e.g. `45.0`, `-30.0`)
- jog continuously CW / CCW, and stop
- home / re-zero

**Firmware requirements**

- Step/direction generation with acceleration limiting — never step instantly from rest to
  full speed on a plastic gear train.
- Home on power-up using the A3144 and the magnet; set that as zero.
- **Backlash handling is mandatory**, not optional: either always approach a target from the
  same direction (overshoot then come back), or run a feedback loop with a deadband
  **≥ 0.35°**. Without one of these, bi-directional positioning will be sloppy regardless of
  code quality.
- With the encoder fitted: closed-loop GOTO, and **stall detection** — if the following error
  grows past a threshold while driving, stop the motor before the PLA teeth take the damage.

## 5. Acceptance tests

Please demonstrate each of these, not just deliver code:

1. **Bench, motor free:** 200 steps = exactly one motor revolution (tape flag). Both
   directions clean. Warm, not hot, after 10 minutes of holding.
2. **Coupled, output unloaded:** 300–900 steps/s in both directions for several minutes
   without stalling. Note the speed where it starts to complain.
3. **Homing:** five power cycles return to the same physical angle within ~0.5°, with no
   false triggers over a full revolution.
4. **Positioning:** command ±45°, ±180°, and back to 0°. Repeatability within ~0.3–0.5°,
   approaching each target from both sides.
5. **Encoder (if fitted):** push the output by hand while holding — it returns; block the
   output — stall detection stops the motor.
6. **Load and thermal:** with the 100 mm lever and known weights, find the torque where it
   stalls; log motor and gearbox temperature over 30 minutes of running.

## 6. Limits — the ways this build breaks

- Above ~300–400 rpm input the planets run hot on plain bushings and the helical teeth load
  them axially; speed is the main wear driver.
- A stall against a hard stop strips PLA teeth. Set the current limit first, and rely on
  stall detection if the encoder is fitted.
- Do not rely on the motor's bearings for the gearbox's axial load; the 6803 and 6802 bearings
  in the cover and carrier carry it.
- Do not exceed 1.5 A on the motor, or ~1 A on an uncooled A4988.

## 7. Deliverables

- Firmware in a `firmware/` folder in this repository.
- A wiring diagram, and the Vref / current the driver was actually set to.
- The measured numbers from the acceptance tests (home repeatability, positioning
  repeatability, stall torque, temperatures) so they can be added to the README's
  performance section alongside the existing 2 N·m and 18 arcmin figures.
