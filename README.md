# Electric Power Steering (Electric Power Steering) System for BMW UKL (BMW Front-Wheel-Drive Platform)

![License: MIT](https://img.shields.io/badge/license-MIT-green)
![Language: C](https://img.shields.io/badge/language-C-blue)
![Standard: AUTOSAR](https://img.shields.io/badge/standard-AUTOSAR-orange)
![Safety: ISO 26262 ASIL D](https://img.shields.io/badge/safety-ISO%2026262%20ASIL%20D-red)
![Microcontroller: TMS570](https://img.shields.io/badge/microcontroller-TMS570-lightgrey)
![Documentation: Astro Starlight](https://img.shields.io/badge/documentation-Astro%20Starlight-purple)

Complete **Electric Power Steering (Electric Power Steering)** firmware for the **BMW UKL (BMW front-wheel-drive platform)** vehicle platform, running on a **Texas Instruments TMS570** safety microcontroller. The software follows the **AUTOSAR (Automotive Open System Architecture)** layered architecture and targets **ISO 26262 ASIL D (Automotive Safety Integrity Level D)**, the highest functional-safety integrity level.

> **Documentation site:** the full reference documentation (Astro with Starlight theme) lives in [`docs/`](docs/) — start at the [documentation landing page](docs/src/content/docs/index.md), or build it with `cd docs && npm install && npm run build`. Published pages derive their GitHub Pages address from the git remote automatically, so forks work without edits.

## Table of Contents

- [Features](#features)
- [Repository Structure](#repository-structure)
- [AUTOSAR Layer Overview](#autosar-layer-overview)
- [Module Catalogue](#module-catalogue)
- [Vector-Provided versus Custom Code](#vector-provided-versus-custom-code)
- [Installation and Build](#installation-and-build)
- [BMW UKL Platform](#bmw-ukl-platform)
- [Contributing](#contributing)
- [License](#license)

## Features

- **Precise power-assisted steering control** — Base Power Assist converts driver handwheel torque and vehicle speed into a motor torque command, refined by damping, return-to-center, inertia-compensation and vehicle-dynamics overlays.
- **Safety by construction (ISO 26262 ASIL D)** — plausibility firewalls around every torque contribution, redundant sensing paths, an independent Shutdown Mechanism, Temporal Monitor supervision with the Watchdog Manager, and TMS570 Microcontroller Diagnostics.
- **Complete vehicle integration** — FlexRay communication (Vector MICROSAR stack), Unified Diagnostic Services diagnostics with BMW customer services, non-volatile memory management over Flash EEPROM Emulation, and Universal Measurement and Calibration Protocol measurement/calibration access.
- **Adaptation and learning** — Average Friction Learning, Learn End of Travel, Learn Rack Center, Motor Temperature Estimation and Thermal Duty Cycle Management keep feel consistent and hardware protected.

## Repository Structure

```text
<repository root>/
├── LICENSE                      # MIT License
├── README.md                      # This file
├── docs/                          # Documentation site source (Astro + Starlight project root)
│   ├── astro.config.mjs           # Site config — GitHub Pages URL derived from git remote
│   ├── package.json               # astro, @astrojs/starlight, sharp
│   └── src/content/docs/          # All documentation pages (general, asw, cdd, services, …)
├── Assist/  StaMd/  …             # One directory per software component (see catalogue)
│   ├── src/  include/  generate/  tools/  utp/
├── BMW_UKL_MCV_EPS_TMS570/        # Integration project: Basic Software, Runtime Environment, tools
│   ├── SwProject/Source/          # BSW/, CDD/, GenData*/, Appl_*.c, …
│   ├── SwProject/*.bat, *.cmd     # Pre/post-build steps, TMS570 linker command file
│   └── Tools/                     # nowECC, HexView, SWE Generator, CANape, DataDictTool, QAC, …
├── NxtrLib/  StdDef/  GliwaT1/    # Shared libraries
└── zzz_binaries/                  # Build-output / binary drop folder
```

<details>
<summary><strong>AUTOSAR layer overview (click to expand)</strong></summary>

| AUTOSAR Layer | Documentation | Repository Location |
| --- | --- | --- |
| Application Software | [`docs/src/content/docs/asw/`](docs/src/content/docs/asw/) | Top-level `Ap_*` / `Sa_*` directories |
| Complex Device Drivers | [`docs/src/content/docs/cdd/`](docs/src/content/docs/cdd/) | Top-level `Cd_*` directories, `SVDrvr/`, `SVDiag/`, `CMS_*/` |
| Basic Software: Services | [`docs/src/content/docs/services/`](docs/src/content/docs/services/) | `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/*`, `DiagMgr/` |
| ECU Abstraction | [`docs/src/content/docs/ecu-abstraction/`](docs/src/content/docs/ecu-abstraction/) | `BSW/IoHwAb`, `BSW/FrIf`, top-level `Adc/`, `Dma/`, `Nhet/`, `SpiNxt/` |
| Microcontroller Abstraction | [`docs/src/content/docs/mcal/`](docs/src/content/docs/mcal/) | `BSW/Mcu`, `BSW/Port`, `BSW/Dio`, `BSW/Gpt`, `BSW/Spi`, `BSW/Wdg`, `BSW/Fr`, `Fls/`, `TMS570_Startup/` |
| Runtime Environment and Operating System | [`docs/src/content/docs/rte-os/`](docs/src/content/docs/rte-os/) | `Source/GenData*`, `BSW/Os`, `Appl_Tasks.c` |
| Libraries | [`docs/src/content/docs/libraries/`](docs/src/content/docs/libraries/) | `NxtrLib/`, `StdDef/`, `GliwaT1/` |
| Tools and Build System | [`docs/src/content/docs/tools/`](docs/src/content/docs/tools/) | `BMW_UKL_MCV_EPS_TMS570/Tools/`, `SwProject/*.bat` |

</details>

## Module Catalogue

Short directory names are expanded to long names (see the [Glossary](docs/src/content/docs/general/glossary.md) for every abbreviation).

<details>
<summary><strong>All component directories with layer and origin (click to expand)</strong></summary>

| Directory | Module Long Name | AUTOSAR Layer | Origin |
| --- | --- | --- | --- |
| `AbsHwPos` | Absolute Hardware Position | Application Software | Custom (in-house) |
| `ActivePull` | Active Pull Compensation | Application Software | Custom (in-house) |
| `Adc` | Analog-to-Digital Converter Driver | ECU Abstraction | Custom (in-house) |
| `AssistFirewall` | Assist Plausibility Firewall | Application Software | Custom (in-house) |
| `Polarity` | Assist Polarity Management | Application Software | Custom (in-house) |
| `AssistSumnLmt` | Assist Summation Limiter | Application Software | Custom (in-house) |
| `AvgFricLrn` | Average Friction Learning | Application Software | Custom (in-house) |
| `BkCpPc` | Backup Capacitor Pre-Charge | Application Software | Custom (in-house) |
| `Assist` | Base Power Assist | Application Software | Custom (in-house) |
| `BVDiag` | Battery Voltage Diagnostics | Application Software | Custom (in-house) |
| `BatteryVoltage` | Battery Voltage Sensing | Application Software | Custom (in-house) |
| `BmwHaptcFb` | BMW Haptic Feedback | Application Software | Custom (BMW-specific) |
| `CBD_BmwRtnAbrn` | BMW Return Arbitration | Application Software | Custom (BMW-specific) |
| `BmwTqOvrlCdng` | BMW Torque Overlay Coding | Application Software | Custom (BMW-specific) |
| `Xcp` | Calibration and Measurement Access | Application Software | Custom (in-house) |
| `CMS_BMW` | Calibration and Measurement System, BMW Variant | Complex Device Drivers | Custom (BMW-specific) |
| `CMS_Common` | Calibration and Measurement System, Common Services | Complex Device Drivers | Custom (in-house) |
| `CtrldDisShtdn` | Controlled Disable Shutdown | Application Software | Custom (in-house) |
| `CtrlTemp` | Controller Temperature Monitoring | Application Software | Custom (in-house) |
| `CustPL_BMW` | Customer Product Line, BMW Variant | Application Software | Custom (BMW-specific) |
| `DampingFirewall` | Damping Plausibility Firewall | Application Software | Custom (in-house) |
| `DiagMgr` | Diagnostic Manager | Basic Software: Services | Custom (in-house) |
| `Dma` | Direct Memory Access Driver | ECU Abstraction | Custom (in-house) |
| `DrvDynCtrl` | Driving Dynamics Control | Application Software | Custom (in-house) |
| `DrvDynEnbl` | Driving Dynamics Enable | Application Software | Custom (in-house) |
| `ElecPwr` | Electrical Power Management | Application Software | Custom (in-house) |
| `EOTActuatorMng` | End-of-Travel Actuator Management | Application Software | Custom (in-house) |
| `EtDmpFw` | Enhanced Torque Damping Firewall | Application Software | Custom (in-house) |
| `FltInjection` | Fault Injection | Application Software | Custom (in-house) |
| `FrTrcvPhy` | FlexRay Transceiver Physical Driver | Microcontroller Abstraction | Vector-provided |
| `Sweep` | Frequency Sweep Excitation | Application Software | Custom (in-house) |
| `FrqDepDmpnInrtCmp` | Frequency-Dependent Damping and Inertia Compensation | Application Software | Custom (in-house) |
| `GenPosTraj` | Generic Position Trajectory | Application Software | Custom (in-house) |
| `GliwaT1` | Gliwa Timing Measurement Library T1 | Libraries | Third-party (Gliwa) |
| `Gsod` | Global Shutdown | Application Software | Custom (in-house) |
| `HwTrq` | Handwheel Torque Sensing | Application Software | Custom (in-house) |
| `HwPwUp` | Hardware Power-Up Sequencing | Application Software | Custom (in-house) |
| `Nhet` | High-End Timer Driver | ECU Abstraction | Custom (in-house) |
| `HiLoadStall` | High-Load Stall Protection | Application Software | Custom (in-house) |
| `HystAdd` | Hysteresis Addition | Application Software | Custom (in-house) |
| `HystComp` | Hysteresis Compensation | Application Software | Custom (in-house) |
| `LrnEOT` | Learn End of Travel | Application Software | Custom (in-house) |
| `LnRkCr` | Learn Rack Center | Application Software | Custom (in-house) |
| `LmtCod` | Limiter Coding | Application Software | Custom (in-house) |
| `LktoLkStr` | Lock-to-Lock Steering Travel | Application Software | Custom (in-house) |
| `MtrCtrl_VM` | Motor Control, Voltage Mode | Application Software | Custom (in-house) |
| `MtrCurr_VM` | Motor Current Sensing, Voltage Mode | Application Software | Custom (in-house) |
| `MtrPos` | Motor Position Sensing | Application Software | Custom (in-house) |
| `MtrTempEst` | Motor Temperature Estimation | Application Software | Custom (in-house) |
| `MtrVel` | Motor Velocity Estimation | Application Software | Custom (in-house) |
| `NxtrLib` | Nexteer Mathematics and Utility Library | Libraries | Custom (in-house) |
| `NvMMgr` | Non-Volatile Memory Manager | Complex Device Drivers | Custom (in-house) |
| `NvMProxy` | Non-Volatile Memory Proxy | Complex Device Drivers | Custom (in-house) |
| `OscTraj` | Oscillation Trajectory Generator | Application Software | Custom (in-house) |
| `ParkAstEnbl_BMW` | Park Assist Enable, BMW Variant | Application Software | Custom (BMW-specific) |
| `PrkAstMfgServCh2` | Park Assist Manufacturing Service, Channel 2 | Application Software | Custom (in-house) |
| `PhaseDscnt` | Phase Disconnect | Application Software | Custom (in-house) |
| `PosServo` | Position Servo Control | Application Software | Custom (in-house) |
| `PwrLmtFunc` | Power Limit Function | Application Software | Custom (in-house) |
| `SVDiag` | Power Stage Diagnostics | Complex Device Drivers | Custom (in-house) |
| `SVDrvr` | Power Stage Driver | Complex Device Drivers | Custom (in-house) |
| `RackLoad` | Rack Load Estimation | Application Software | Custom (in-house) |
| `ReturnFirewall` | Return Plausibility Firewall | Application Software | Custom (in-house) |
| `Return` | Return-to-Center Control | Application Software | Custom (in-house) |
| `SpiNxt` | Serial Peripheral Interface Driver, Nexteer Extension | ECU Abstraction | Custom (in-house) |
| `ShtdnMech` | Shutdown Mechanism | Application Software | Custom (in-house) |
| `SgnlCond` | Signal Conditioning | Application Software | Custom (in-house) |
| `StabilityComp` | Stability Compensation | Application Software | Custom (in-house) |
| `StdDef` | Standard Type Definitions | Libraries | Custom (in-house) |
| `StOpCtrl` | Start-Stop Control | Application Software | Custom (in-house) |
| `Damping` | Steering Damping | Application Software | Custom (in-house) |
| `TurnsCounter` | Steering Turns Counter | Complex Device Drivers | Custom (in-house) |
| `StaMd` | System State Manager | Application Software | Custom (in-house) |
| `TmprlMon` | Temporal Monitor | Application Software | Custom (in-house) |
| `ThrmDutyCycle` | Thermal Duty Cycle Management | Application Software | Custom (in-house) |
| `TMS570_uDiag` | TMS570 Microcontroller Diagnostics | Complex Device Drivers | Custom (in-house) |
| `TrqOsc` | Torque Oscillation Management | Application Software | Custom (in-house) |
| `TrqBasedInrtCmp` | Torque-Based Inertia Compensation | Application Software | Custom (in-house) |
| `TJADamp` | Traffic Jam Assist Damping | Application Software | Custom (in-house) |
| `TuningSelAuth` | Tuning Selection Authority | Application Software | Custom (in-house) |
| `TcFlshPrg` | Turns Counter Flash Programming | Complex Device Drivers | Custom (in-house) |
| `VehSpdLmt` | Vehicle Speed Limiter | Application Software | Custom (in-house) |

</details>

Key Basic Software modules of the integration project (all Vector MICROSAR unless noted) are documented individually under [`docs/src/content/docs/services/`](docs/src/content/docs/services/), [`docs/src/content/docs/mcal/`](docs/src/content/docs/mcal/), [`docs/src/content/docs/ecu-abstraction/`](docs/src/content/docs/ecu-abstraction/) and [`docs/src/content/docs/rte-os/`](docs/src/content/docs/rte-os/) — including Communication, Communication Manager, Diagnostic Communication Manager, Electronic Control Unit State Manager, Non-Volatile Memory Manager, Watchdog Manager, FlexRay stack, Operating System and Runtime Environment. Third-party exceptions: Diagnostic Event Manager (Elektrobit), Flash EEPROM Emulation and Flash Driver (Texas Instruments), Timing Measurement Library T1 (Gliwa).

## Vector-Provided versus Custom Code

- **Custom in-house code** (Nexteer, including BMW customer-specific variants): all Application Software components and in-house drivers — safe to modify through the project change process.
- **Vector-provided code** (Vector MICROSAR stack, DaVinci Configurator and generator outputs in `Source/GenData*`): **do not edit by hand** — change the configuration and regenerate.
- **Other third-party code** (Elektrobit, Texas Instruments, Gliwa, open-source decompression): update only via official vendor deliveries.

Every documentation page carries an origin badge with the applicable rule — see [Vector versus Custom Code](docs/src/content/docs/general/vector-vs-custom.md).

## Installation and Build

### Prerequisites

- Code Composer Studio v5 with ARM Optimizing C/C++ Compiler v4.6 (Texas Instruments TMS570 target).
- Vector DaVinci Configurator toolchain for regenerating Basic Software configuration (`Source/GenData*`).
- Windows build host with the WinZip command-line add-on (required by the archive step).
- Node.js (only for building this documentation site in `docs/`).

### Firmware build

1. Clone this repository.
2. Open `BMW_UKL_MCV_EPS_TMS570/SwProject` in Code Composer Studio v5.
3. The pre-build step (`SwProject/prebuild.bat`) shields conflicting compiler `Std_Types.h`-family headers automatically.
4. Build the desired configuration (`Release`, `Debug`, or `Fault Injection`).
5. The post-build step (`SwProject/postbuild.bat`) generates the hex image, injects Error Correction Code data with `nowECC`, packages the three BMW Software Entity containers with the SWE Generator, and archives the deliverables.
6. Flash the resulting image onto the TMS570 microcontroller (linker layout: `SwProject/TMS570LS202x6SFlashLnk.cmd`).

Full details: [Toolchain Overview](docs/src/content/docs/tools/toolchain.md), [Post-Build Process](docs/src/content/docs/tools/postbuild.md), [Build Environment manual](docs/src/content/docs/tools/build-environment.md).

### Documentation site build

```sh
cd docs
npm install
npm run build    # output in docs/dist/
npm run preview  # local preview
```

No repository or user names are hardcoded: `docs/astro.config.mjs` derives the GitHub Pages `site` and `base` addresses from the `origin` git remote at build time.

## BMW UKL Platform

The **BMW UKL (BMW front-wheel-drive platform)** platform is a BMW vehicle architecture. Example vehicles based on it:

1. **BMW 2 Series Active Tourer**: compact multi-purpose vehicle with efficient engines.
2. **BMW 2 Series Gran Tourer**: larger variant with additional seating and cargo capacity.
3. **MINI Clubman**: compact estate with agile handling.
4. **MINI Countryman**: compact crossover for urban and outdoor use.

## Contributing

We encourage contributions! If you would like to improve this project, please submit a pull request. Respect code ownership: custom components may be changed directly, while Vector-provided and third-party files must be updated through their generators or vendor deliveries (see [Vector versus Custom Code](docs/src/content/docs/general/vector-vs-custom.md)).

## License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for the full text.
