# LTspice Simulation Notes

## Available Circuits

| Circuit | Saved analysis settings | Main nodes |
| --- | --- | --- |
| `DAC_Amp.asc` | `.tran 0 10m 0 10u`, B=T=0.5; input SINE(1.65 1.65 1k) | BUF, Vout1, Vout2, Vout, Vref |
| `Bass_Treble.asc` | `.ac dec 100 10 100k`; B and T each sweep through 0, 0.25, 0.5, 0.75, and 1, giving 25 combinations | Vout1, Vout4 |

These settings come from the existing files. No new simulations were run during repository preparation. AC analysis and parameter sweeps in DAC_Amp are currently commented out. Its existing `.plt` file contains only an AC Analysis configuration; select transient traces separately after running transient analysis.

## Reproduction Steps

1. Open the relevant `.asc` file in LTspice, keeping the `.asy` and `.lib` files in the same directory.
2. Check model resolution and the SPICE Error Log. If duplicate subcircuit definitions appear, check for models loaded through both symbol ModelFile attributes and explicit schematic include directives.
3. For DAC_Amp, run transient analysis and select V(vout). Inspect V(vref), V(buf), and intermediate outputs as needed. The output is capacitively coupled to a 32-ohm load.
4. For Bass_Treble, run the AC sweep and select V(vout4). The AC input amplitude is 1 V. Inspect magnitude, phase, and the B/T combinations; interpret absolute output amplitude using the defined input stimulus.
5. Capture the actual LTspice window with the circuit name, axes, trace labels, and analysis settings visible, then update the README.

## Models and Design Revisions

- The OPA161x.lib header identifies it as an independently created LTspice behavioral approximation based on device documentation. It is not a TI transistor-level model and is not validated for THD+N, noise, PSRR, CMRR, overvoltage, thermal behavior, or efficiency.
- OPAx197.LIB and OPA1622.LIB retain their original TI model notices. Simulation does not replace hardware measurements.
- DAC_Amp uses an OPA1622 output model. The Altium output stage and the OPA1656 / OPA1688 choices discussed during development still need to be reconciled. This simulation does not establish the performance of the final PCB device.
- Bass_Treble and DAC_Amp use different resistor and capacitor values. They represent different design stages and should not be treated as the same hardware revision.

## Verification Scope

Analysis directives, symbol dependencies, and existing simulation logs were inspected. LTspice was not rerun. Existing raw results are retained locally and excluded by `.gitignore`. Access to the LTspice application was not approved during the initial preparation, so actual LTspice window screenshots remain outstanding.

## Cloud Import Check

The supplied `OPA161x.asy` uses `ModelFile OPA161x.LIB`, while the archive contains `OPA161x.lib`. These names differ on case-sensitive filesystems. The schematic include directives use the supplied lowercase extension. Original simulation files were preserved; reconcile the symbol reference before running with tools that require exact filename case.

Neither LTspice nor Altium is available in the current cloud environment. Static file checks do not establish successful model loading or simulation results.
