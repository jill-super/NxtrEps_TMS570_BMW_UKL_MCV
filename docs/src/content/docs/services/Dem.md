---
title: "Diagnostic Event Manager"
description: "AUTOSAR Diagnostic Event Manager (Elektrobit implementation): stores diagnostic events, freeze frames and extended data; used by the Diagnostic Manager."
---

*Integration sources: `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/` — Basic Software: Services.*

:::caution[Third-party code: Elektrobit]
Provided by an external vendor (see below). **Do not edit manually** — update only via an official vendor delivery.
:::


## Purpose and responsibility

AUTOSAR Diagnostic Event Manager (Elektrobit implementation): stores diagnostic events, freeze frames and extended data; used by the Diagnostic Manager.

## Files (excerpt)

Header/copyright evidence in this directory points to: **Elektrobit Automotive GmbH**.

- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem.h`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_Api_Depend.h`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_Api_Depend_Specific.h`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_Api_Static.h`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_Api_Static_Specific.h`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_ApplyDTCFilter.c`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_ClearDTC.c`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_ClearEntry.c`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_ClearPrestoredFreezeFrame.c`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_ControlDTCRecordUpdate.c`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_ControlDTCStorage.c`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_ControlEventStatusUpdate.c`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_DataCopy.c`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_DebounceCounterBased.c`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_DebounceFrequencyBased.c`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_DebounceMonitor.c`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_DebounceTimeBased.c`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Dem/Dem_Depend.c`
- …and 83 more (see the repository).

## Usage notes

Call the module only through its AUTOSAR-specified API from the Runtime Environment, scheduler tasks or upper layers; never bypass the abstraction with direct hardware access. Faults are reported via the Default Error Tracer (development) and the Diagnostic Event Manager (production), and are coordinated by the [Diagnostic Manager](../services/DiagMgr/).

See also: [Basic Software: Services](./) · [Architecture overview](../general/architecture/) · [Vector versus custom](../general/vector-vs-custom/)
