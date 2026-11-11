# Hardware Debugging Notes

[Back to project overview](../README.md)

## 1. Scope and Evidence

The observations below come from the supplied project history. No oscilloscope captures or original bench logs have been imported. The available AC and transient plots are LTspice simulations.

## 2. Debugging Process

1. **Checked the microphone bias circuit**
   - Found a **75 Ω resistor installed instead of 750 Ω** and corrected it.
   - **Result:** Microphone DC bias returned to a reasonable level of approximately **4.3 V**.
2. **Measured MOSFET bias voltages**
   - Checked key MOSFET source, gate, and drain voltages.
   - **Result:** Confirmed that the bias/current-source stages were active and identified abnormal operating points for further troubleshooting.
3. **Tested the output transistors**
   - Used diode mode to check the BCP56 and BCP53 transistor junctions.
   - **Result:** Junction drops were approximately **0.65 V**, indicating no obvious shorted or open transistors.
4. **Checked the Class-AB diode bias chain**
   - Measured the D1–D4 bias-network voltages.
   - **Result:** Initially found the diode-chain nodes close to **0 V**, showing that the output-stage bias had not been established correctly.
5. **Verified PCB connectivity**
   - Used continuity and resistance measurements on critical bias and signal nets.
   - **Result:** Confirmed the intended PCB connections and ruled out a direct short from the bias node to ground.
6. **Verified the amplifier DC output point**
   - Measured the node before the speaker coupling capacitor.
   - **Result:** The output eventually stabilized near **6 V**, matching the expected mid-supply bias for a **12 V single-supply amplifier**.
7. **Checked the speaker output path**
   - Measured the speaker resistance and output coupling capacitor.
   - **Result:** Speaker path measured approximately **8.4 Ω**, and the speaker had approximately **0 V DC** across its terminals.
8. **Traced the AC signal**
   - Measured the amplifier output while speaking into the microphone.
   - **Result:** The output changed with microphone input, confirming that the signal was propagating through the amplifier.
9. **Detected output instability**
   - Monitored the 6 V output operating point during normal operation.
   - **Result:** The DC output point oscillated instead of remaining stable when the microphone was connected.
10. **Performed a microphone isolation test**
    - Disconnected the microphone while keeping the speaker connected.
    - **Result:** The output returned to a stable **~6 V**, showing that the instability was related to the microphone signal path.
11. **Final diagnosis**
    - Compared system behavior with and without the microphone connected.
    - **Result:** The most likely cause was **feedback or oscillation involving the microphone path**, potentially caused by close microphone-speaker placement, PCB coupling, or insufficient amplifier stability.

## 3. Resolve Reference Designators

The hardware screenshot labels the 1000 µF speaker coupling capacitor C4. The LTspice screenshot labels a 10 µF input coupling capacitor C4. Do not use the historical C4 description as a confirmed hardware test point until the original revision or annotated measurement location is available.

The intended microphone bias resistance in the history is 750 Ω. The hardware screenshot includes R10 = 1.5 kΩ, R11 = 1 kΩ, and R12 = 1 kΩ near the microphone, while the simulation uses different values and references. The supplied material does not establish which hardware component received the reported correction.

## 4. Working Hypotheses

- Acoustic feedback between microphone and speaker.
- Microphone bias or input operating-point problems.
- Electrical coupling between output and input through routing, grounding, or supply.
- Amplifier instability that depends on input loading.

These are possible explanations, not established root causes. Disconnecting the microphone changes both the acoustic signal path and electrical input conditions.

## 5. Current Outcome

The reported prototype did not achieve stable operation. The exact root cause remains unresolved.
