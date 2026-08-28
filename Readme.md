# Steel Pipe Rack – Refinery Process Unit (STAAD.Pro)

Structural analysis and design of a 3-tier steel pipe rack for a petroleum refinery process unit, modeled and checked in STAAD.Pro per **IS 800:2007 (Limit State Design)**.

## Project Overview

| Parameter | Value |
|---|---|
| Structure type | Steel pipe rack, moment/braced frame |
| Longitudinal span | 6 bays × 6.0 m = 36.0 m |
| Transverse span | 1 bay × 6.0 m |
| Tiers | 3, at EL +4.500 m / +8.000 m / +11.500 m |
| Base level | EL 0.000 (top of pedestal) |
| Design code | IS 800:2007 (LSD) |
| Load codes | IS 875 (Wind), IS 1893 Part 4 (Seismic – Industrial Structures) |
| Seismic zone | Zone V |
| Basic wind speed | 50 m/s |
| Joints / Members | 56 / 127 |

## Structural System

- **Columns** (members 1–42): ISHB400, oriented with strong axis (Izz) resisting transverse wind bending via `BETA 90`, since the frame relies on portal action in that direction.
- **Longitudinal tier beams** (members 43–63): ISHB450.
- **Pipe support beams** (members 64–99): ISHB300 — upgraded from an initial ISMB300 selection after the slenderness check (KL/ryy) exceeded the IS 800 allowable of 180 for these 6.0 m unbraced spans; ISHB300 also gave a bending capacity margin.
- **Bracing** (members 100–127): ISA 200×200×16 double angles, released as pin-ended (axial/truss members only).
- **Supports**: All 14 column bases fixed at top-of-pedestal level; foundation design carried separately.
- **Material**: Structural steel, Fe250 (Fy = 250 MPa), E = 2.05×10⁸ kN/m².

## Loading

| Load Case | Description |
|---|---|
| 1 | Dead load – selfweight of steel |
| 2 | Pipe dead load – operating (empty + fluid + insulation), tiered UDLs of 6.0 / 4.0 / 2.5 kN/m |
| 3 | Live load – maintenance walkway, top tier (1.0 kN/m) |
| 4 | Wind load, transverse (+Z), IS 875 Part 3 |
| 5 | Seismic load, longitudinal (+X), IS 1893 Part 4, Zone V |

**8 load combinations** per IS 800, including ultimate limit state combinations (1.5(DL+PL+LL), 1.2(DL+PL+LL+WL), etc.), uplift/reversal checks (0.9DL + 1.5WL/EL), and a serviceability combination for deflection checks.

## Design Parameters

```
CODE IS800 LSD
FYLD 250000 ALL
NSF 0.85 ALL
TRACK 2 ALL
```

## Repository Contents

| File | Description |
|---|---|
| `pipe_rack_refinery.std` | STAAD.Pro input/analysis file |

## Tools Used

STAAD.Pro (analysis + IS 800 code check)

## Notes

This project is part of a structural engineering portfolio built during core/PSU placement preparation (IIT Guwahati, Civil Engineering).
