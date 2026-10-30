# Test Results

**Current status: no verified hardware measurements or new simulation plots are published.**

The following is a test plan, not results.

| Check | Required record | Status |
| --- | --- | --- |
| Altium validation and PCB DRC | Tool version, revision, settings, messages, unresolved exceptions | Pending |
| LTspice AC / transient runs | Circuit revision, models, stimulus, load, axes, traces | Pending rerun |
| Frequency response and EQ range | Source amplitude, control positions, load, sweep | Not measured |
| Output and clipping | Supply voltage, load, waveform, clipping criterion | Not measured |
| Noise | Bandwidth, weighting, input termination, gain, load, instrument floor | Not measured |
| Distortion | Frequency, output level, load, bandwidth, instrument capability | Not measured |
| Supply and protection | PD behavior, startup/shutdown, ripple, load, temperature, protection response | Not measured |

## Evidence Locations

- [Simulation/Results](../Simulation/Results/): exported simulation plots.
- [Measurements](../Measurements/): instrument data and measurement metadata.
- [Images/PCB](../Images/PCB/): board views.
- [Images/Assembly](../Images/Assembly/): real board photos.
- [Hardware/Manufacturing](../Hardware/Manufacturing/): reviewed fabrication outputs.

For each result, record the date, hardware revision, software/tool version where applicable, equipment, procedure, units, and limitations. Use descriptive filenames with revision and test conditions.
