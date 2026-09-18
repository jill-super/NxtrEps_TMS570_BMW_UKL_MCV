---
title: "Gliwa Timing Measurement Library T1"
description: "Third-party timing-measurement library (T1) for worst-case execution-time analysis and Central Processing Unit load measurement. Provided by Gliwa; configure, do not modify."
---

*Directory `GliwaT1/` — Libraries.*

:::caution[Third-party code: Gliwa]
Provided by an external vendor (see below). **Do not edit manually** — update only via an official vendor delivery.
:::


## Purpose and responsibility

Third-party timing-measurement library (T1) for worst-case execution-time analysis and Central Processing Unit load measurement. Provided by Gliwa; configure, do not modify.

## Directory layout

Sources live in `GliwaT1/`. The standard module layout is:

| Folder | Content |
| --- | --- |
| `src/` | present — C/assembler implementation and local headers |
| `include/` | present — Public headers (if present) |
| `generate/` | — — Generator batch files / templates (if present) |
| `tools/` | — — Host-side helper scripts (if present) |
| `utp/` | present — Unit-test project artefacts (if present) |

## Key files

- `GliwaT1/src/T1_AppInterface.c`
- `GliwaT1/src/T1_AppInterface_Cfg.c`
- `GliwaT1/src/T1_config.c`
- `GliwaT1/src/sys_pmu.asm`
- `GliwaT1/include/GCP_config.h`
- `GliwaT1/include/GCP_driverInterface.h`
- `GliwaT1/include/GCP_sharedInterface.h`
- `GliwaT1/include/GCP_startCode.h`
- `GliwaT1/include/GCP_stopCode.h`
- `GliwaT1/include/Metrics.h`
- `GliwaT1/include/T1_AppInterface.h`
- `GliwaT1/include/T1_AppInterface_Cfg.h`

## Public interface (runnables and operations)

Runnable entities and client-server operations found in the implementation (called by the Runtime Environment / task schedule):

- `T1_Init`

```c
/* Typical invocation context (scheduled by the operating-system task,
   dispatched through the generated Runtime Environment): */

T1_Init();  /* initialisation runnable (startup) */
```

## Dependencies

- `T1_AppInterface.h`
- `T1_AppInterface_Cfg.h`
- `sys_pmu.h`
- `osek.h`
- `T1_MemMap.h`
- `ComStack_Types.h`
- `T1_config.h`
- `GCP_driverInterface.h`
- `Cdc_Cfg.h`
- `T1_bid.h`
- `T1_baseConfig.h`
- `T1_contConfig.h`
- `Rte_dcm.h` (generated Runtime Environment contract)

## Usage notes

The `GliwaT1` component is scheduled through the Runtime Environment: periodic runnables run in their assigned operating-system task/rate, initialisation runnables run during startup, and client-server (`Scom`) operations are invoked by testers, manufacturing services or other components. Calibration constants are tuned via the measurement and calibration tool chain (see [Tools and Build System](../tools/)).

See also: [Libraries](./) · [Architecture overview](../general/architecture/) · [Vector versus custom](../general/vector-vs-custom/)
