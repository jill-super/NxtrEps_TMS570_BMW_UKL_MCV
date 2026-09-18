---
title: "BMW Haptic Feedback"
description: "BMW-specific haptic feedback overlay that shapes steering feel cues (for example lane-keeping or warning feedback) requested by the vehicle."
---

*Directory `BmwHaptcFb/` — Application Software.*

:::tip[Custom — BMW customer-specific implementation]
Developed in-house for the BMW customer project (variant-specific behaviour, interfaces or diagnostics). Owned by this project; changes must respect BMW vehicle-interface agreements.
:::


## Purpose and responsibility

BMW-specific haptic feedback overlay that shapes steering feel cues (for example lane-keeping or warning feedback) requested by the vehicle.

## Directory layout

Sources live in `BmwHaptcFb/`. The standard module layout is:

| Folder | Content |
| --- | --- |
| `src/` | present — C/assembler implementation and local headers |
| `include/` | — — Public headers (if present) |
| `generate/` | — — Generator batch files / templates (if present) |
| `tools/` | present — Host-side helper scripts (if present) |
| `utp/` | — — Unit-test project artefacts (if present) |

## Key files

- `BmwHaptcFb/src/Ap_BmwHaptcFb.c`

## Public interface (runnables and operations)

Runnable entities and client-server operations found in the implementation (called by the Runtime Environment / task schedule):

- `BmwHaptcFb_Init1`
- `BmwHaptcFb_Per1`

```c
/* Typical invocation context (scheduled by the operating-system task,
   dispatched through the generated Runtime Environment): */

BmwHaptcFb_Per1();  /* periodic runnable */
BmwHaptcFb_Init1();  /* initialisation runnable (startup) */
```

## Host-side helpers

- `BmwHaptcFb/tools/Contract`
- `BmwHaptcFb/tools/RteGen.bat`

## Dependencies

- `CalConstants.h`
- `GlobalMacro.h`
- `interpolation.h`
- `fixmath.h`
- `filters.h`
- `MemMap.h`
- `Rte_Ap_BmwHaptcFb.h` (generated Runtime Environment contract)

## Usage notes

The `BmwHaptcFb` component is scheduled through the Runtime Environment: periodic runnables run in their assigned operating-system task/rate, initialisation runnables run during startup, and client-server (`Scom`) operations are invoked by testers, manufacturing services or other components. Calibration constants are tuned via the measurement and calibration tool chain (see [Tools and Build System](../tools/)).

See also: [Application Software](./) · [Architecture overview](../general/architecture/) · [Vector versus custom](../general/vector-vs-custom/)
