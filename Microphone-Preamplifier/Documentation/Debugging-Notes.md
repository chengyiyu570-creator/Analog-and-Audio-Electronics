# Hardware Debugging Notes

[Back to project overview](../README.md)

## 1. Scope and Evidence

The observations below come from the supplied project history. No oscilloscope captures or original bench logs have been imported. The available AC and transient plots are LTspice simulations.

## 2. Debugging Process

1. **Verified the microphone bias network**
   - Found a microphone bias resistor populated with **75 Ω** instead of the intended **750 Ω**.
   - Replaced the resistor and rechecked the microphone bias voltage. After adjusting the bias network, the microphone DC operating point stabilized at approximately **4.3 V**.

2. **Checked MOSFET bias operating points**
   - Measured DC voltages around the MOSFET bias and current-source stages.
   - At M6, the source measured approximately **10.35 V** and the gate/drain node measured **8.6 V**. These measurements indicated that at least part of the bias network was active.

3. **Tested the BJT output-stage devices**
   - Checked the BCP56 and BCP53 junctions with the multimeter's diode-test mode. The measured drops of approximately **0.65 V** showed no obvious open or short in the junctions tested.
   - Measured the base, collector, and emitter voltages during operation.

4. **Investigated the Class-AB diode bias chain**
   - Measured DC voltages at the D1–D4 bias network. The nodes were initially close to **0 V**, suggesting that the intended bias current had not been established.
   - Checked continuity between the diode network, transistor bases, and MOSFET stages.

5. **Checked for shorts and PCB connectivity problems**
   - Used continuity and resistance measurements to check critical signal and bias nets.
   - Measured approximately **1.8 MΩ** from the node at the top of D1 to ground, ruling out a direct short to ground at that node.
   - Verified connections between the MOSFET current-source stages and the Class-AB bias network.

6. **Recovered the output DC operating point**
   - After addressing bias issues, the node before the speaker output coupling capacitor reached approximately **6 V DC**, close to the midpoint of the **12 V** single supply.
   - The isolation test below established the condition under which this node held steady.

7. **Verified the speaker and output coupling path**
   - Measured approximately **8.4 Ω** through the speaker path, consistent with a connected speaker and wiring.
   - Measured approximately **70 µF** across the installed output capacitor in circuit. The hardware schematic specifies **1000 µF** at C4. The installed value remains to be verified out of circuit.
   - Measured approximately **0 V DC** across the speaker terminals, consistent with the coupling capacitor blocking the output stage's DC bias.

8. **Traced the AC audio signal**
   - In multimeter AC mode, the amplifier output node read approximately **0.3 V AC at idle** and up to **2.3 V AC while speaking into the microphone**. The change showed that the output responded to microphone activity.
   - The reading directly across the speaker was approximately **5–6 mV AC**, and the prototype produced no usable audio.

9. **Observed oscillation at the amplifier output**
   - With the microphone connected, the output node oscillated around its nominal **6 V** DC operating point.
   - The instability was consistent with the earlier fluctuating multimeter readings and lack of clean audio. The oscillation frequency and amplitude were not recorded.

10. **Performed an isolation test**
    - Kept the speaker connected and disconnected only the microphone. The amplifier output returned to a stable operating point of approximately **6 V DC**.
    - Reconnecting the microphone brought back the instability.

11. **Assessed the prototype**
    - The amplifier could hold the intended DC operating point with the microphone disconnected. With the microphone and speaker both connected, the system was unstable.
    - Candidate causes include acoustic feedback from microphone and speaker proximity, electrical coupling through the PCB, and insufficient frequency compensation in the high-gain amplifier. The isolation test did not establish the root cause.
    - Lessons from this revision include controlling feedback, reviewing component placement and ground return paths, checking frequency compensation, and isolating variables during bench tests.

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
