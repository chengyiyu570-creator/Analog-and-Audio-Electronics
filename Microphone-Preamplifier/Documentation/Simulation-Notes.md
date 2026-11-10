# Simulation Notes

[Back to project overview](../README.md)

## 1. Available Evidence

- [LTspice circuit screenshot](../Images/LTspice.png)
- [AC sweep screenshot](../Images/AC_sweep.png)
- [Transient screenshot](../Images/Transient.png)

Native schematic, device model files, raw results, logs, and simulator version are pending import. No simulation has been rerun as part of creating this outline.

## 2. Settings Visible in the Circuit Screenshot

| Item | Visible setting |
| --- | --- |
| Supply | 12 V |
| Output load | 8 Ω resistor |
| Transient input | SINE(0 5m 2000), Rser=10 |
| AC input | AC 1 |
| AC analysis text | .ac dec 100 1 100Meg |
| Transient analysis text | .tran 0 10m 0 1u; a second .tran line is also visible |
| Fourier analysis text | .four 2k V(vout) |
| Included model paths | Lib/BCP56.lib, Lib/BCP53.lib, Lib/BSS138.lib |
| Options text | .options plotwinsize=0 reltol=1e-5 |

The screenshot contains multiple analysis directives. Confirm which were enabled for each plot using the original files. No Fourier output or THD result was supplied.

## 3. Screenshot Observations

- The AC plot spans 1 Hz to 100 MHz and shows approximately 56 dB midband magnitude with low- and high-frequency roll-off.
- The transient plot spans 0–10 ms and shows roughly 20 output cycles with peaks around ±3.1 V.
- The transient trace names are V(vout) and V(n015). Confirm the latter's net before interpreting it as the input.
- Values above are visual estimates. Exact gain, cutoff frequencies, distortion, and power require the underlying data.

## 4. Hardware and Simulation Differences

The screenshots must not be assumed to represent an identical revision.

- Hardware C4 is the 1000 µF output capacitor; simulation C2 is the 1000 µF output capacitor.
- Simulation C4 is a 10 µF input coupling capacitor.
- Hardware R2/R3/R4 show 75 kΩ / 15 kΩ / 30 kΩ; the simulation bias network R6/R7/R8 shows 75 kΩ / 25 kΩ / 20 kΩ.
- The microphone-side networks have different values and reference designators.
- The simulation uses an electrical sine source and resistive load; the hardware schematic includes a microphone and speaker.

## 5. Reproducibility Outline

- [ ] Add the original .asc file and required models under Simulation/LTspice.
- [ ] Record simulator version and model provenance.
- [ ] Identify the revision associated with each plot.
- [ ] Confirm operating points and active directives.
- [ ] Export numeric gain, bandwidth, and transient measurements.
- [ ] Document model limitations and compare with controlled bench tests.

A displayed driven transient waveform and AC response do not resolve the prototype's reported oscillation issue.
