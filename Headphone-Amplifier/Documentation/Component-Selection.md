# Component Selection

**Status:** selection review pending. This is not a released BOM.

| Area | Current evidence | Required decision or check |
| --- | --- | --- |
| OPA1612 / OPA161x | User-specified design direction and OPA161x behavioral model | Confirm schematic parts, supply/headroom, and noise requirements; the model does not validate device performance |
| Output stage | DAC_Amp uses OPA1622; earlier notes mention OPA1656 / OPA1688 | Reconcile schematic, BOM, purchasing choice, and simulation |
| Tone control | EQ schematic and Bass_Treble simulation | Reconcile values, EQ range, tolerances, and potentiometer footprints |
| USB-C / PD and LDO supply | Power schematic | Confirm device choices, negotiated voltage, dropout, load current, thermal margins, and protection |
| Reference voltage | Vref schematic | Verify bias level, buffering, stability, loading, and noise |
| Connectors and passives | Native design and local libraries | Confirm pinouts, dimensions, manufacturer part numbers, and footprint provenance |

Record selected parts, alternatives, rationale, datasheet revisions, and design checks when confirmed. Add an actual exported BOM under Hardware/Manufacturing when ready.

See [simulation notes](simulation.md) and [third-party notices](../THIRD_PARTY_NOTICES.md) for model limitations.
