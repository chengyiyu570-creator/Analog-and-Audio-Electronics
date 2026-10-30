# Analog & Audio Electronics

Analog circuit and audio hardware designs.

This repository groups independent projects within one hardware discipline. Each project folder has its own README, source files, images, and design documentation.

## Project Index

| Project | Status |
| --- | --- |
| [Headphone Amplifier](Headphone-Amplifier/) | Design files imported; in development |
| [Microphone Preamplifier](Microphone-Preamplifier/) | Scaffold only; source files and validation pending |
| [Audio Filters](Audio-Filters/) | Scaffold only; source files and validation pending |
| [Other Analog Circuits](Other-Analog-Circuits/) | Scaffold only; source files and validation pending |

Scaffolds are organizational placeholders, not completed designs. Only the headphone amplifier currently contains imported engineering files.

## Working Convention

- Keep each complete project in its primary discipline. Cross-link supporting work rather than duplicating the hardware across repositories.
- Document goals, schematics, PCB design, component selection, simulation, measurements, and unresolved issues in each project README.
- Keep source files and required models under version control. Exclude generated caches and automatic backups with the root .gitignore.
- Commit one project at a time, using messages such as `Headphone-Amplifier: Update PCB power routing`.
- Altium PCB and schematic files are binary: include exported images or reports to make revisions reviewable.
- No repository-wide open-source license has been selected. Preserve third-party notices with the relevant project.

## Portfolio Repositories

- [Analog & Audio Electronics](https://github.com/chengyiyu570-creator/Analog-and-Audio-Electronics)
- [Embedded Systems](https://github.com/chengyiyu570-creator/Embedded-Systems)
- [Digital Design & FPGA](https://github.com/chengyiyu570-creator/Digital-Design-and-FPGA)
- [Power Electronics](https://github.com/chengyiyu570-creator/Power-Electronics)
