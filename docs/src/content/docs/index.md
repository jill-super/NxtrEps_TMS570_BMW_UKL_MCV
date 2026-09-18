---
title: Electric Power Steering Firmware Documentation
description: Reference documentation for the AUTOSAR-based Electric Power Steering firmware on Texas Instruments TMS570 for the BMW UKL platform.
template: splash
hero:
  tagline: Reference documentation for the AUTOSAR-based Electric Power Steering firmware — layers, modules, build system and tools.
  image:
    file: ../../assets/eps-logo.svg
  actions:
    - text: System architecture
      link: general/architecture/
      icon: right-arrow
    - text: Application Software modules
      link: asw/
      icon: open-book
    - text: Vector versus custom code
      link: general/vector-vs-custom/
      icon: information
---

import { Card, CardGrid } from '@astrojs/starlight/components';

## Project overview

This site documents an **Electric Power Steering (Electric Power Steering)** system for the **BMW UKL (BMW front-wheel-drive platform)** vehicle platform, running on a **Texas Instruments TMS570** safety microcontroller. The software follows the **AUTOSAR (Automotive Open System Architecture)** layered architecture and the **ISO 26262 ASIL D (Automotive Safety Integrity Level D)** functional-safety standard, the highest integrity level.

Steering torque requested by the driver is measured at the handwheel, conditioned through safety firewalls, converted by the base assist function into a motor torque command, and executed by a voltage-mode motor control loop — all supervised by redundant diagnostics, a system state manager and a watchdog chain.

<CardGrid stagger>
  <Card title="Application Software" icon="puzzle">
    Steering functions, safety monitors and BMW vehicle features as AUTOSAR software components.
    [Browse modules](./asw/)
  </Card>
  <Card title="Complex Device Drivers" icon="cpu">
    Hardware-near drivers: power stage, memory manager, microcontroller diagnostics and diagnostic communication.
    [Browse modules](./cdd/)
  </Card>
  <Card title="Basic Software: Services" icon="lifebuoy">
    Diagnostics, communication, memory, watchdogs and cryptography services.
    [Browse modules](./services/)
  </Card>
  <Card title="ECU Abstraction" icon="layers">
    Hardware abstraction for sensors, actuators, memory and FlexRay communication.
    [Browse modules](./ecu-abstraction/)
  </Card>
  <Card title="Microcontroller Abstraction" icon="setting">
    Direct TMS570 peripheral drivers and startup code.
    [Browse modules](./mcal/)
  </Card>
  <Card title="Runtime Environment & Operating System" icon="rocket">
    Generated Runtime Environment glue, MICROSAR Operating System and scheduler tasks.
    [Browse modules](./rte-os/)
  </Card>
  <Card title="Libraries" icon="open-book">
    Shared mathematics library, standard types and timing-measurement library.
    [Browse modules](./libraries/)
  </Card>
  <Card title="Tools & Build System" icon="wrench">
    Build environment, post-build chain and converted tool manuals.
    [Browse modules](./tools/)
  </Card>
</CardGrid>

## Vector-provided versus custom code

A central convention of this documentation: every module page carries an **origin badge** that tells you whether the code is **Vector-provided** (Vector MICROSAR stack or DaVinci-generated — do not edit by hand), **third-party** (Elektrobit, Texas Instruments, Gliwa — update only via vendor deliveries) or **custom in-house** code (owned by this project — safe to modify, including BMW customer-specific variants). Read [Vector versus custom code](./general/vector-vs-custom/) before changing anything.

## How to read this documentation

- Start with the [System architecture](./general/architecture/) and [AUTOSAR layers](./general/autosar-layers/) overviews.
- Find any abbreviation or short module name in the [Glossary](./general/glossary/) — short names are always expanded to long names.
- Module pages state purpose, key files, public interface (runnables), dependencies and configuration for every directory in the repository.
- Tool manuals converted from Word and PDF originals live under [Tools and Build System](./tools/), with the conversion register in [Documentation guide](./general/documentation-guide/).
