---
title: "Customer Product Line, BMW Variant"
description: "BMW customer product-line adaptations: variant-specific behaviour and interfaces for the BMW product line. Name expansion is an assumption (see Glossary)."
---

*Directory `CustPL_BMW/` — Application Software.*

:::tip[Custom — BMW customer-specific implementation]
Developed in-house for the BMW customer project (variant-specific behaviour, interfaces or diagnostics). Owned by this project; changes must respect BMW vehicle-interface agreements.
:::


## Purpose and responsibility

BMW customer product-line adaptations: variant-specific behaviour and interfaces for the BMW product line. Name expansion is an assumption (see Glossary).

## Directory layout

Sources live in `CustPL_BMW/`. The standard module layout is:

| Folder | Content |
| --- | --- |
| `src/` | present — C/assembler implementation and local headers |
| `include/` | — — Public headers (if present) |
| `generate/` | — — Generator batch files / templates (if present) |
| `tools/` | present — Host-side helper scripts (if present) |
| `utp/` | — — Unit-test project artefacts (if present) |

## Key files

- `CustPL_BMW/src/Ap_CustPL.c`

## Public interface (runnables and operations)

Runnable entities and client-server operations found in the implementation (called by the Runtime Environment / task schedule):

- `MSA_State_Init`
- `CustPL_Init1`
- `CustPL_Per1`

```c
/* Typical invocation context (scheduled by the operating-system task,
   dispatched through the generated Runtime Environment): */

CustPL_Per1();  /* periodic runnable */
MSA_State_Init();  /* initialisation runnable (startup) */
```

## Host-side helpers

- `CustPL_BMW/tools/RteGen.bat`
- `CustPL_BMW/tools/contract`

## Dependencies

- `fixmath.h`
- `GlobalMacro.h`
- `interpolation.h`
- `CalConstants.h`
- `MemMap.h`
- `Rte_Ap_CustPL.h` (generated Runtime Environment contract)

## Usage notes

The `CustPL_BMW` component is scheduled through the Runtime Environment: periodic runnables run in their assigned operating-system task/rate, initialisation runnables run during startup, and client-server (`Scom`) operations are invoked by testers, manufacturing services or other components. Calibration constants are tuned via the measurement and calibration tool chain (see [Tools and Build System](../tools/)).

See also: [Application Software](./) · [Architecture overview](../general/architecture/) · [Vector versus custom](../general/vector-vs-custom/)
