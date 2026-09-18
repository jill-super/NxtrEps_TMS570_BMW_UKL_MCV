---
title: "Flash Driver"
description: "Texas Instruments F021 flash application programming interface for the TMS570 (delivered as library plus headers). Third-party code, do not edit."
---

*Integration sources: `Fls/` — Microcontroller Abstraction.*

:::caution[Third-party code: Texas Instruments]
Provided by an external vendor (see below). **Do not edit manually** — update only via an official vendor delivery.
:::


## Purpose and responsibility

Texas Instruments F021 flash application programming interface for the TMS570 (delivered as library plus headers). Third-party code, do not edit.

## Files (excerpt)

Header/copyright evidence in this directory points to: **see file headers**.


## Usage notes

Call the module only through its AUTOSAR-specified API from the Runtime Environment, scheduler tasks or upper layers; never bypass the abstraction with direct hardware access. Faults are reported via the Default Error Tracer (development) and the Diagnostic Event Manager (production), and are coordinated by the [Diagnostic Manager](../services/DiagMgr/).

See also: [Microcontroller Abstraction](./) · [Architecture overview](../general/architecture/) · [Vector versus custom](../general/vector-vs-custom/)
