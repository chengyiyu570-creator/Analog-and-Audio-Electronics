# Microphone-to-Speaker Amplifier

[Back to project index](../README.md)

**Analog Audio Circuit | PCB Design | Hardware Debugging**

**Project status:** Prototype completed — stability issue unresolved, according to the supplied project notes.

This project explores a custom microphone-to-speaker amplifier using discrete transistors. The initial PCB was fabricated and assembled, but unexpected oscillation prevented stable operation. This repository documents the design, available simulation screenshots, and hardware debugging experience.

This documentation is an outline populated from the supplied project history and images. Native design files, simulation data, and bench captures have not yet been imported.

## 1. Design Goals

- Capture a microphone signal, amplify it, and drive a speaker.
- Practice discrete analog circuit design, PCB layout, assembly, and debugging.
- To document: hardware supply voltage, microphone specifications, speaker impedance, target gain, bandwidth, and output power.

## 2. System Architecture

**Microphone → Input bias and coupling → Discrete MOSFET amplification → Complementary BJT output stage → Output coupling capacitor → Speaker**

The supplied schematic shows BSS138 and BSS84 MOSFETs, BCP56/BCP53 output transistors, and a diode bias network. Stage operation, operating points, feedback, and component selection remain to be documented against the native schematic.

## 3. Hardware Design

### Schematic

![Hardware schematic](Images/Schematic.png)

### PCB Layout

![PCB layout screenshot](Images/PCB.png)

To document: board dimensions, layer stack, power and ground return paths, placement decisions, footprints, and design-rule checks. The PCB screenshot records the layout view; it is not a photograph of the assembled board.

Native project files should be placed in [Hardware/Altium](Hardware/Altium/).

## 4. Simulation

The supplied LTspice screenshots show a 12 V supply, an 8 Ω resistive load, and a 2 kHz sine source with 5 mV peak amplitude. These are simulation settings, not confirmed bench conditions.

### Simulation Circuit

![LTspice circuit](Images/LTspice.png)

### AC Sweep

![AC sweep simulation](Images/AC_sweep.png)

The displayed response has a midband magnitude of approximately 56 dB. The circuit screenshot labels the input source AC 1; confirm the plotted transfer function and circuit revision using the original simulation files.

### Transient Response

![Transient simulation](Images/Transient.png)

The screenshot shows approximately 20 output cycles over 10 ms, with output peaks around ±3.1 V. The blue trace is labeled V(n015); its node identity requires the native simulation.

These screenshots do not establish hardware stability, distortion, or measured output power. See [Simulation Notes](Documentation/Simulation-Notes.md) for settings, limitations, and revision differences.

## 5. Hardware Testing and Debugging

The supplied project history reports:

| Test or change | Reported observation | Interpretation |
| --- | --- | --- |
| Component inspection | A microphone bias resistor was fitted as 75 Ω instead of the intended 750 Ω | Assembly value error identified |
| Resistor replacement | Replaced with 750 Ω | Correction reported; effect on oscillation not separately recorded |
| Node probing | Oscillation observed at a node described as the microphone side of C4 | Exact node and design revision need confirmation |
| Microphone disconnected | Oscillation disappeared and the node stabilized | The microphone input path was implicated; root cause remains unresolved |

**Reference discrepancy:** In the supplied hardware schematic, C4 is the 1000 µF speaker output coupling capacitor. In the LTspice screenshot, C4 is a 10 µF input coupling capacitor. The historical node description must be reconciled with the design revision before assigning a hardware test point.

See [Debugging Notes](Documentation/Debugging-Notes.md) for the investigation outline.

## 6. Known Issues and Lessons Learned

- Stable hardware operation was not achieved in the reported prototype.
- Acoustic feedback, microphone bias conditions, electrical coupling, and power-supply coupling remain hypotheses.
- Verify component values and operating points before full-system testing.
- Record exact test points, circuit revisions, and measurement conditions.
- Simulation and hardware evidence must be evaluated separately.

## 7. Next Steps

- [ ] Import native Altium files, BOM, and tool version.
- [ ] Import LTspice schematic, models, raw data, and tool version.
- [ ] Reconcile simulation and hardware component values and reference designators.
- [ ] Confirm the intended 750 Ω resistor's hardware reference designator.
- [ ] Add assembled-board photographs and available bench captures.
- [ ] Document supply, load, probe setup, and oscillation frequency/amplitude.
- [ ] Test with a dummy load and controlled electrical input to help separate acoustic feedback from electrical instability.
- [ ] Validate individual stages and investigate bias, grounding, decoupling, and signal coupling before a board revision.

## 8. Repository Structure

- [Images](Images/): supplied schematic, PCB layout, and simulation screenshots.
- [Documentation/Debugging-Notes.md](Documentation/Debugging-Notes.md): historical observations and proposed tests.
- [Documentation/Simulation-Notes.md](Documentation/Simulation-Notes.md): screenshot evidence and reproducibility outline.
- [Hardware/Altium](Hardware/Altium/): reserved for native hardware sources.
- [Simulation/LTspice](Simulation/LTspice/): reserved for native simulation sources.

The folder name remains Microphone-Preamplifier within the parent repository; the project title reflects the supplied microphone-to-speaker design.
