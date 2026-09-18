---
title: "Park Assist Enable, BMW Variant"
description: "BMW-specific enable logic for park-assist steering interventions."
---

*Directory `ParkAstEnbl_BMW/` — Application Software.*

:::tip[Custom — BMW customer-specific implementation]
Developed in-house for the BMW customer project (variant-specific behaviour, interfaces or diagnostics). Owned by this project; changes must respect BMW vehicle-interface agreements.
:::


## Purpose and responsibility

BMW-specific enable logic for park-assist steering interventions.

## Directory layout

Sources live in `ParkAstEnbl_BMW/`. The standard module layout is:

| Folder | Content |
| --- | --- |
| `src/` | present — C/assembler implementation and local headers |
| `include/` | — — Public headers (if present) |
| `generate/` | present — Generator batch files / templates (if present) |
| `tools/` | present — Host-side helper scripts (if present) |
| `utp/` | present — Unit-test project artefacts (if present) |

## Key files

- `ParkAstEnbl_BMW/src/Ap_ParkAstEnbl.c`

## Public interface (runnables and operations)

Runnable entities and client-server operations found in the implementation (called by the Runtime Environment / task schedule):

- `ParkAstEnbl_Per1`

```c
/* Typical invocation context (scheduled by the operating-system task,
   dispatched through the generated Runtime Environment): */

ParkAstEnbl_Per1();  /* periodic runnable */
```

## Configuration and generation

Generator artefacts shipped with the module:

- `ParkAstEnbl_BMW/generate/Ap_ParkAstEnbl_Generate.bat`

## Host-side helpers

- `ParkAstEnbl_BMW/tools/Integrate.bat`
- `ParkAstEnbl_BMW/tools/RteGen.bat`

## Dependencies

- `Ap_ParkAstEnbl_Cfg.h`
- `GlobalMacro.h`
- `fixmath.h`
- `filters.h`
- `CalConstants.h`
- `MemMap.h`
- `Rte_Ap_ParkAstEnbl.h` (generated Runtime Environment contract)

## Usage notes

The `ParkAstEnbl_BMW` component is scheduled through the Runtime Environment: periodic runnables run in their assigned operating-system task/rate, initialisation runnables run during startup, and client-server (`Scom`) operations are invoked by testers, manufacturing services or other components. Calibration constants are tuned via the measurement and calibration tool chain (see [Tools and Build System](../tools/)).

See also: [Application Software](./) · [Architecture overview](../general/architecture/) · [Vector versus custom](../general/vector-vs-custom/)
