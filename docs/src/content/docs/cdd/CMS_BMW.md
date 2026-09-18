---
title: "Calibration and Measurement System, BMW Variant"
description: "BMW-variant diagnostic communication services: customer-specific Unified Diagnostic Services handling over the calibration and measurement interface. The Calibration and Measurement System expansion is an assumption (see Glossary)."
---

*Directory `CMS_BMW/` — Complex Device Drivers.*

:::tip[Custom — BMW customer-specific implementation]
Developed in-house for the BMW customer project (variant-specific behaviour, interfaces or diagnostics). Owned by this project; changes must respect BMW vehicle-interface agreements.
:::


## Purpose and responsibility

BMW-variant diagnostic communication services: customer-specific Unified Diagnostic Services handling over the calibration and measurement interface. The Calibration and Measurement System expansion is an assumption (see Glossary).

## Directory layout

Sources live in `CMS_BMW/`. The standard module layout is:

| Folder | Content |
| --- | --- |
| `src/` | present — C/assembler implementation and local headers |
| `include/` | present — Public headers (if present) |
| `generate/` | — — Generator batch files / templates (if present) |
| `tools/` | — — Host-side helper scripts (if present) |
| `utp/` | present — Unit-test project artefacts (if present) |

## Key files

- `CMS_BMW/src/EPS_DiagSrvcs_ISO.Customer.c`
- `CMS_BMW/src/EPS_DiagSrvcs_SrvcLUTbl.c`
- `CMS_BMW/include/EPS_DiagSrvcs_ISO.Customer.h`
- `CMS_BMW/include/EPS_DiagSrvcs_ISO.Interface.h`
- `CMS_BMW/include/EPS_DiagSrvcs_XCP.Interface.h`

## Public interface (runnables and operations)

Runnable entities and client-server operations found in the implementation (called by the Runtime Environment / task schedule):

- `CM_VehCfg_Scom_SetVariantSelect`
- `CM_VehCfg_Scom_GetVariantSelect`

```c
/* Typical invocation context (scheduled by the operating-system task,
   dispatched through the generated Runtime Environment): */

```

## Dependencies

- `EPS_DiagSrvcs_SrvcLUTbl.h`
- `EPS_DiagSrvcs_ISO.h`
- `EPS_DiagSrvcs_ISO.Customer.h`
- `NvM.h`
- `EPS_DiagSrvcs_ISO.Interface.h`
- `EPS_DiagSrvcs_XCP.Interface.h`
- `EPS_DiagSrvcs_XCP.h`

## Usage notes

The `CMS_BMW` component is scheduled through the Runtime Environment: periodic runnables run in their assigned operating-system task/rate, initialisation runnables run during startup, and client-server (`Scom`) operations are invoked by testers, manufacturing services or other components. Calibration constants are tuned via the measurement and calibration tool chain (see [Tools and Build System](../tools/)).

See also: [Complex Device Drivers](./) · [Architecture overview](../general/architecture/) · [Vector versus custom](../general/vector-vs-custom/)
