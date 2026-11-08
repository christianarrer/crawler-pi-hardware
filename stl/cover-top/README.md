# Top Cover Assembly

This directory contains the three 3D-printable top cover sections for the customized crawler based on the tracked robot platform originally designed by **Dejan Nedelkovski**.

The three sections replace the original upper assembly while retaining the existing mounting points on the original chassis tub. **No modifications to the original chassis tub are required.**

## Cover sections

| File | Purpose |
| --- | --- |
| `cover-front.stl` | Covers the battery and accommodates the green headlight LEDs. Provision for a front-facing camera is planned for a future revision. |
| `cover-center.stl` | Supports and positions the LiDAR sensor and its USB driver board. |
| `cover-rear.stl` | Houses the rear-facing docking camera, the charging PCB, and the copper contact pads that mate with the docking station. |

The rear section also incorporates ventilation slots and a provision for a TPU insert used as a mechanical docking stop.

## Assembly and mounting

The three cover sections are interconnected by hinges using **brass welding rods as hinge pins**. The hinged construction allows the covers to be opened for access to the components underneath.

The assembly uses the **existing M3 screw mounting locations** provided by Dejan Nedelkovski's original design. The screws can be loosened or removed as needed to open or detach the covers for maintenance. No changes to the original chassis tub are necessary.

Before assembly, check the fit and alignment of the printed hinge features and the brass rods. Verify that the covers move freely without interfering with nearby wiring or electronics.

## Notes

- The `cover-front` camera provision is a **future plan**, not a feature of the current STL.
- The `cover-rear` charging board is mounted on the underside of the cover, with its components facing into the crawler.
- Ensure adequate cable clearance when opening the hinged covers, especially for the docking camera's ribbon cable.
- Check the fit of the docking contacts and mechanical stop before the first powered docking test.

## Design attribution

This is a custom top-cover assembly intended for use with **Dejan Nedelkovski's original tracked robot platform**. The original platform design is credited to Dejan Nedelkovski; the cover modifications and electronics integration are part of this crawler customization.
