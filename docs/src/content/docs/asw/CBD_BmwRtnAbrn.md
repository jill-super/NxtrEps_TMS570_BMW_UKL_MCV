---
title: "BMW Return Arbitration"
description: "Implements the CF019A BMW return-arbitration building block: arbitrates return-to-center requests from BMW vehicle functions."
---

*Directory `CBD_BmwRtnAbrn/` — Application Software.*

:::tip[Custom — BMW customer-specific implementation]
Developed in-house for the BMW customer project (variant-specific behaviour, interfaces or diagnostics). Owned by this project; changes must respect BMW vehicle-interface agreements.
:::


## Purpose and responsibility

Implements the CF019A BMW return-arbitration building block: arbitrates return-to-center requests from BMW vehicle functions.

## Directory layout

Sources live in `CBD_BmwRtnAbrn/`. The standard module layout is:

| Folder | Content |
| --- | --- |
| `src/` | present — C/assembler implementation and local headers |
| `include/` | — — Public headers (if present) |
| `generate/` | — — Generator batch files / templates (if present) |
| `tools/` | present — Host-side helper scripts (if present) |
| `utp/` | — — Unit-test project artefacts (if present) |

## Key files

- `CBD_BmwRtnAbrn/src/Ap_BmwRtnArbn.c`

## Public interface (runnables and operations)

Runnable entities and client-server operations found in the implementation (called by the Runtime Environment / task schedule):

- `BmwRtnArbn_Init1`
- `BmwRtnArbn_Per1`

```c
/* Typical invocation context (scheduled by the operating-system task,
   dispatched through the generated Runtime Environment): */

BmwRtnArbn_Per1();  /* periodic runnable */
BmwRtnArbn_Init1();  /* initialisation runnable (startup) */
```

## Host-side helpers

- `CBD_BmwRtnAbrn/tools/RteGen.bat`
- `CBD_BmwRtnAbrn/tools/contract`

## Dependencies

- `CalConstants.h`
- `filters.h`
- `GlobalMacro.h`
- `fixmath.h`
- `interpolation.h`
- `MemMap.h`
- `Rte_Ap_BmwRtnArbn.h` (generated Runtime Environment contract)

## Usage notes

The `CBD_BmwRtnAbrn` component is scheduled through the Runtime Environment: periodic runnables run in their assigned operating-system task/rate, initialisation runnables run during startup, and client-server (`Scom`) operations are invoked by testers, manufacturing services or other components. Calibration constants are tuned via the measurement and calibration tool chain (see [Tools and Build System](../tools/)).

See also: [Application Software](./) · [Architecture overview](../general/architecture/) · [Vector versus custom](../general/vector-vs-custom/)
