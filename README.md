# crawler-pi-hardware

Hardware designs for **crawler-pi**, an autonomous tracked robot based on a Raspberry Pi and ROS 2.

This repository contains KiCad PCB projects, manufacturing files, and hardware documentation. Additional 3D-printable customization parts may be included in the future, subject to the necessary permissions.

The ROS 2 software is maintained separately in [crawler-pi](https://github.com/christianarrer/crawler-pi).

## PCB projects

### 1. crawler-pi — Sensor and power distribution board

**Location:** [`pcb/crawler-pi/`](pcb/crawler-pi/)

A distribution and interface PCB for the crawler's Raspberry Pi electronics. Its purpose is to simplify the wiring between the Raspberry Pi, sensors, motor-driver control signals, lighting, and power components.

The board provides:

- Connections for I²C sensors and related peripheral wiring.
- GPIO connections for the left and right motor-driver control signals.
- A GPIO-controlled switch for the headlights.
- Battery and DC/DC buck-converter connections for the crawler's power distribution.
- Reverse-polarity protection and fuse protection.

The project includes KiCad schematic and PCB design files. The [`gerber/`](pcb/crawler-pi/gerber/) directory contains manufacturing outputs from an earlier board revision.

#### Through-hole (THT) components — hand soldering

The following **19 components** require through-hole hand soldering. The reference designators and part numbers are reproduced from the original BOM (including `BS170` and `178.6165.0001`).

| Reference | Manufacturer | MPN | LCSC | Type |
| --- | --- | --- | --- | --- |
| R_POL_PD1 | VISHAY | RN60E1003BRE6 | C1796719 | Resistor |
| R_LED_GATE1 | YAGEO | MFR-25FRF52-100R | C1740087 | Resistor |
| R_LED_PD1 | VISHAY | RN60E1003BRE6 | C1796719 | Resistor |
| Q_PMOS_GDS | onsemi | FQP27P06 | C462764 | p-channel MOSFET |
| BS170 | onsemi | BS170 | C111691 | n-channel MOSFET |
| 178.6165.0001 | Littelfuse | 178.6165.0001 | C207060 | Fuseholder |
| J_BATT1 | CUI | TB010-508-02BE | C5954901 | Terminal Block |
| J_MOT_DRV_L_PWR1 | CUI | TB010-508-02BE | C5954901 | Terminal Block |
| J_MOT_DRV_R_PWR1 | CUI | TB010-508-02BE | C5954901 | Terminal Block |
| J_PWR_SWITCH1 | CUI | TB010-508-02BE | C5954901 | Terminal Block |
| J_POWER_MON_PWR1 | Amphenol | VI0421550000G | C3816565 | Terminal Block |
| J_BUCk1 | Amphenol | VI0421550000G | C3816565 | Terminal Block |
| J_RPI1 | ZHOURI | PC104-2*20 | C5307344 | Pin Stacking Header 2x20 |
| J_PWR_MON_I2C1 | hanxia | HX PH254-01-04-Z-L11.5 | C52016392 | Pin Header 1x4 |
| J_ODO_L_I2C1 | hanxia | HX PH254-01-04-Z-L11.5 | C52016392 | Pin Header 1x4 |
| J_IMU_I2C1 | hanxia | HX PH254-01-04-Z-L11.5 | C52016392 | Pin Header 1x4 |
| J_ODO_R_I2C1 | hanxia | HX PH254-01-04-Z-L11.5 | C52016392 | Pin Header 1x4 |
| J_MOT_DRV_L_CTRL1 | hanxia | HX PZ2.54-2x4P ZZ | C32713277 | Pin Header 2x4 |
| J_MOT_DRV_R_CTRL1 | hanxia | HX PZ2.54-2x4P ZZ | C32713277 | Pin Header 2x4 |

**Documentation still to be added:** connector assignments, assembly instructions, and board-specific wiring notes. Consult the schematic and PCB files for authoritative pin assignments and component values.

### 2. crawler-pi-charger — NiMH charger and power-path board

**Location:** [`pcb/crawler-pi-charger/`](pcb/crawler-pi-charger/)

**Status: Work in progress — not yet validated for construction or operation.**

This project aims to provide an integrated charging and power-path solution for the crawler's **6-cell (7.2 V nominal) NiMH battery pack** and docking station.

The design is based on the **Analog Devices LTC4011** NiMH battery charger controller. The intended functionality includes:

- Charging the NiMH battery when the crawler is connected to its dock.
- Using the LTC4011's supported fast-charge termination and battery-temperature sensing features.
- Providing a power path between the external dock supply, battery, and crawler system load.
- Supporting continued system operation when docking power is connected or removed, subject to the final switching and power-budget design.
- Interfaces for the docking-station supply, battery, system power, and DC/DC converter connections.

The design explores MOSFET-based power-path switching inspired by the Analog Devices DC674B demonstration circuit. Power-path component ratings, charger configuration, thermal protection, current limits, and the distribution of power to the motors and Raspberry Pi must be verified before use.

**Important:** This is an experimental hardware project. Do not assume that the present schematic is suitable for unattended battery charging or direct connection to the robot without electrical verification and testing.

## Repository structure

```text
crawler-pi-hardware/
├── pcb/
│   ├── crawler-pi/          # Sensor, GPIO, and power distribution PCB
│   │   └── gerber/          # Manufacturing files
│   └── crawler-pi-charger/  # NiMH charger and power-path PCB (WIP)
└── stl/                     # Possible future 3D-printable parts
```

The `stl/` directory is **planned**, not necessarily present in the repository. Original designs or adaptations of third-party parts will only be published where redistribution is permitted.

## Working with the designs

Open each PCB project using its `.kicad_pro` file in KiCad. Before ordering or assembling boards, review the schematic, PCB layout, design-rule checks, component footprints, and manufacturing outputs. Existing Gerber files represent a particular exported revision and should not be assumed to match subsequent schematic or PCB edits.

## License

See [LICENSE](LICENSE) for the repository's current license. Rights to any third-party reference designs, components, and future mechanical files remain subject to their respective owners and licenses.
