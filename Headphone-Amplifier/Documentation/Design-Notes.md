# Design Notes

**Status:** work in progress. These notes describe design intent and review work, not verified performance.

## Signal Path and EQ

Input coupling and buffering feed stereo bass/treble EQ, volume control, and an AC-coupled headphone output. Confirm feedback values, gain, headroom, and EQ corner frequencies against the final schematic. The two LTspice circuits use different component values and must not be treated as identical hardware revisions.

## Supply, Bias, and Protection

The Power and Vref sheets cover USB-C / PD input, protection, regulation, and buffered reference voltage. Review operating voltages, device limits, startup/shutdown behavior, protection thresholds, and decoupling. Verify reference distribution and headphone-output DC behavior before connecting a load.

## PCB Review

Four layers are the intended approach. Record the actual stack-up after inspecting the board. Review return paths, analog signal placement, supply routing, local decoupling, connector footprints, and mechanical clearances. Save electrical-validation and DRC results with the reviewed revision.

## Remaining Integration Work

Confirm the STM32 device, source connector, DAC architecture, sample rate, and physical top-level signal connections.

## Revision Record

- October 30, 2026: reorganized design, simulation, documentation, and evidence directories; updated project-relative dependencies. No circuit-value or PCB-layout changes were made.
- Prior preparation history: [design-status.md](design-status.md).
