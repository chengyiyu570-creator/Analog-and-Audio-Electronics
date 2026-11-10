# Hardware Debugging Notes

[Back to project overview](../README.md)

## 1. Scope and Evidence

The observations below come from the supplied project history. No oscilloscope captures or original bench logs have been imported. The available AC and transient plots are LTspice simulations.

## 2. Reported Debugging Sequence

| Step | Action | Reported result | Missing details |
| --- | --- | --- | --- |
| 1 | Inspect microphone bias components | Found 75 Ω fitted where 750 Ω was intended | Reference designator, BOM revision, and measurement |
| 2 | Replace resistor with 750 Ω | Assembly value corrected | Node voltages and effect on behavior |
| 3 | Probe the node described as the microphone side of C4 | Oscillation observed | Revision, exact net, frequency, amplitude, probe setup |
| 4 | Disconnect microphone | Oscillation disappeared; node stabilized | Load, supply, wiring, and microphone/speaker placement |

## 3. Resolve Reference Designators

The hardware screenshot labels the 1000 µF speaker coupling capacitor C4. The LTspice screenshot labels a 10 µF input coupling capacitor C4. Do not use the historical C4 description as a confirmed hardware test point until the original revision or annotated measurement location is available.

The intended microphone bias resistance in the history is 750 Ω. The hardware screenshot includes R10 = 1.5 kΩ, R11 = 1 kΩ, and R12 = 1 kΩ near the microphone, while the simulation uses different values and references. The supplied material does not establish which hardware component received the reported correction.

## 4. Working Hypotheses

- Acoustic feedback between microphone and speaker.
- Microphone bias or input operating-point problems.
- Electrical coupling between output and input through routing, grounding, or supply.
- Amplifier instability that depends on input loading.

These are possible explanations, not established root causes. Disconnecting the microphone changes both the acoustic signal path and electrical input conditions.

## 5. Proposed Controlled Tests

No results are recorded for these tests.

| Test | Purpose | Record |
| --- | --- | --- |
| Check component values and DC operating points | Establish the assembled circuit configuration | BOM revision, voltages, current, resistor values |
| Replace speaker with a suitably rated resistive dummy load | Remove the speaker's acoustic output | Output waveform and supply waveform |
| Replace microphone with a controlled electrical source and defined bias/load | Evaluate amplifier behavior under known input conditions | Input level, source impedance, output waveform |
| Vary microphone/speaker separation with other settings fixed | Investigate acoustic sensitivity | Distance, orientation, onset and frequency of oscillation |
| Probe supply and successive signal stages | Locate where instability appears | Exact nets, DC levels, frequency, amplitude, bandwidth |
| Evaluate decoupling and return paths | Investigate electrical coupling | One change at a time and before/after captures |

## 6. Measurement Record Template

- Date and board revision:
- Schematic revision and annotated test point:
- Supply voltage and current limit:
- Microphone/source and speaker/load:
- Instrument and probe configuration:
- Input signal and physical placement:
- Change made:
- Expected behavior:
- Observed behavior:
- Waveform file:
- Conclusion and remaining uncertainty:

## 7. Current Outcome

The reported prototype did not achieve stable operation. The exact root cause remains unresolved.
