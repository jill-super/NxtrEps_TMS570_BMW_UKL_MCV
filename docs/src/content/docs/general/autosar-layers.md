---
title: "AUTOSAR Layers"
description: "How the repository maps onto the Automotive Open System Architecture layers."
---

The repository is organised into the classic Automotive Open System Architecture (AUTOSAR) layers. The table below shows where each part of the source tree belongs.

## Layer map

| AUTOSAR layer | Documentation section | Repository location | Content |
| --- | --- | --- | --- |
| Application Software | [Application Software](../asw/) | Top-level `Ap_*` / `Sa_*` directories | Steering functions, safety monitors, BMW vehicle features |
| Complex Device Drivers | [Complex Device Drivers](../cdd/) | Top-level `Cd_*` directories, `SVDrvr/`, `SVDiag/`, `CMS_*/` | Power stage, memory manager, microcontroller diagnostics, diagnostic communication |
| Services | [Basic Software: Services](../services/) | `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/*`, `DiagMgr/` | Diagnostics, communication, memory, watchdogs, cryptography |
| ECU Abstraction | [ECU Abstraction](../ecu-abstraction/) | `BSW/IoHwAb`, `BSW/FrIf`, `BSW/FreeTimer`, top-level `Adc/`, `Dma/`, `Nhet/`, `SpiNxt/` | Sensor/actuator abstraction, memory hardware abstraction, peripheral drivers |
| Microcontroller Abstraction | [Microcontroller Abstraction](../mcal/) | `BSW/Mcu`, `BSW/Port`, `BSW/Dio`, `BSW/Gpt`, `BSW/Spi`, `BSW/Wdg`, `BSW/Fr`, `Fls/`, `TMS570_Startup/`, top-level `FrTrcvPhy/` | Direct TMS570 peripheral drivers, flash driver, startup code |
| Runtime Environment, Operating System | [Runtime Environment and Operating System](../rte-os/) | `Source/GenData*`, `BSW/Os`, `Appl_Tasks.c`, `ApplCallbacks.c` | Generated component glue, tasks, alarms, ECU state callouts |
| Libraries | [Libraries](../libraries/) | `NxtrLib/`, `StdDef/`, `GliwaT1/` | Mathematics, standard types, timing measurement |
| Integration and tools | [Tools and Build System](../tools/) | `BMW_UKL_MCV_EPS_TMS570/Tools/`, `SwProject/*.bat`, linker command file | Build environment, post-build chain, host utilities |

## Naming conventions

- `Ap_*` — Application Software components (for example `Ap_Assist.c` in `Assist/`).
- `Sa_*` — Sensor/Actuator Software components close to the hardware (for example `Sa_HwTrq.c`).
- `Cd_*` — Complex Device Driver components (for example `Cd_FeeIf.c`).
- `Rte_*` — Generated Runtime Environment contracts (for example `Rte_Ap_Assist.h` in `GenDataRte/`); never edited by hand.
- `*_Cfg.*` — Generated configuration (DaVinci Configurator / Basic Software generators) under `Source/GenData/`; regenerate instead of editing.

## Safety architecture

Safety (ISO 26262 ASIL D, the highest Automotive Safety Integrity Level) is implemented by construction: redundant sensing paths, plausibility firewalls around every torque contribution, an independent shutdown mechanism, temporal supervision and microcontroller diagnostics. See [System Architecture](./architecture/) for the supervision chain.
