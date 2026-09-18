---
title: "NRV2B Decompression"
description: "NRV2B (Not Really Vanished 2 Byte) decompression stream used for compressed software-update payloads. Third-party algorithm, do not modify."
---

*Integration sources: `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Nrv2b/` — Basic Software: Services.*

:::caution[Third-party code: open-source (UCL)]
Provided by an external vendor (see below). **Do not edit manually** — update only via an official vendor delivery.
:::


## Purpose and responsibility

NRV2B (Not Really Vanished 2 Byte) decompression stream used for compressed software-update payloads. Third-party algorithm, do not modify.

## Files (excerpt)

Header/copyright evidence in this directory points to: **see file headers**.

- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Nrv2b/nrv2b_stream.c`
- `BMW_UKL_MCV_EPS_TMS570/SwProject/Source/BSW/Nrv2b/nrv2b_stream.h`

## Usage notes

Call the module only through its AUTOSAR-specified API from the Runtime Environment, scheduler tasks or upper layers; never bypass the abstraction with direct hardware access. Faults are reported via the Default Error Tracer (development) and the Diagnostic Event Manager (production), and are coordinated by the [Diagnostic Manager](../services/DiagMgr/).

See also: [Basic Software: Services](./) · [Architecture overview](../general/architecture/) · [Vector versus custom](../general/vector-vs-custom/)
