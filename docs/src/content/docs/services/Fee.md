---
title: "Flash EEPROM Emulation"
description: "Texas Instruments Flash EEPROM Emulation for TMS570: emulates EEPROM semantics on data flash. Third-party code, do not edit."
---

*Integration sources: `Fee/` — Basic Software: Services.*

:::caution[Third-party code: Texas Instruments]
Provided by an external vendor (see below). **Do not edit manually** — update only via an official vendor delivery.
:::


## Purpose and responsibility

Texas Instruments Flash EEPROM Emulation for TMS570: emulates EEPROM semantics on data flash. Third-party code, do not edit.

## Files (excerpt)

Header/copyright evidence in this directory points to: **see file headers**.


## Usage notes

Call the module only through its AUTOSAR-specified API from the Runtime Environment, scheduler tasks or upper layers; never bypass the abstraction with direct hardware access. Faults are reported via the Default Error Tracer (development) and the Diagnostic Event Manager (production), and are coordinated by the [Diagnostic Manager](../services/DiagMgr/).

See also: [Basic Software: Services](./) · [Architecture overview](../general/architecture/) · [Vector versus custom](../general/vector-vs-custom/)
