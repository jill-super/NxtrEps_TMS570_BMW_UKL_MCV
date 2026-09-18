---
title: "BMW Torque Overlay Coding"
description: "BMW-specific coding of external torque overlay requests, adapting vehicle-requested overlays to the Electric Power Steering torque interface."
---

*Directory `BmwTqOvrlCdng/` — Application Software.*

:::tip[Custom — BMW customer-specific implementation]
Developed in-house for the BMW customer project (variant-specific behaviour, interfaces or diagnostics). Owned by this project; changes must respect BMW vehicle-interface agreements.
:::


## Purpose and responsibility

BMW-specific coding of external torque overlay requests, adapting vehicle-requested overlays to the Electric Power Steering torque interface.

## Directory layout

Sources live in `BmwTqOvrlCdng/`. The standard module layout is:

| Folder | Content |
| --- | --- |
| `src/` | present — C/assembler implementation and local headers |
| `include/` | — — Public headers (if present) |
| `generate/` | — — Generator batch files / templates (if present) |
| `tools/` | present — Host-side helper scripts (if present) |
| `utp/` | — — Unit-test project artefacts (if present) |

## Key files

- `BmwTqOvrlCdng/src/Ap_BmwTqOvrlCdng.c`

## Public interface (runnables and operations)

Runnable entities and client-server operations found in the implementation (called by the Runtime Environment / task schedule):

- `BmwTqOvrlCdng_Init1`
- `BmwTqOvrlCdng_Per1`

```c
/* Typical invocation context (scheduled by the operating-system task,
   dispatched through the generated Runtime Environment): */

BmwTqOvrlCdng_Per1();  /* periodic runnable */
BmwTqOvrlCdng_Init1();  /* initialisation runnable (startup) */
```

## Host-side helpers

- `BmwTqOvrlCdng/tools/RteGen.bat`
- `BmwTqOvrlCdng/tools/contract`

## Dependencies

- `CalConstants.h`
- `filters.h`
- `fixmath.h`
- `interpolation.h`
- `SystemTime.h`
- `MemMap.h`
- `Rte_Ap_BmwTqOvrlCdng.h` (generated Runtime Environment contract)

## Usage notes

The `BmwTqOvrlCdng` component is scheduled through the Runtime Environment: periodic runnables run in their assigned operating-system task/rate, initialisation runnables run during startup, and client-server (`Scom`) operations are invoked by testers, manufacturing services or other components. Calibration constants are tuned via the measurement and calibration tool chain (see [Tools and Build System](../tools/)).

See also: [Application Software](./) · [Architecture overview](../general/architecture/) · [Vector versus custom](../general/vector-vs-custom/)
