---
title: "Microcontroller Abstraction"
description: "Microcontroller Abstraction Layer and startup: direct TMS570 peripheral drivers (Vector MICROSAR, Texas Instruments) plus in-house startup code."
---

Microcontroller Abstraction Layer and startup: direct TMS570 peripheral drivers (Vector MICROSAR, Texas Instruments) plus in-house startup code.

## Modules in this layer

| Module directory | Module long name | Origin |
| --- | --- | --- |
| `Dio` | [Digital Input Output Driver](./Dio/) | Vector-provided |
| `Fls` | [Flash Driver](./Fls/) | Third-party (Texas Instruments) |
| `Fr` | [FlexRay Driver](./Fr/) | Vector-provided |
| `FrTrcvPhy` | [FlexRay Transceiver Physical Driver](./FrTrcvPhy/) | Vector-provided |
| `Gpt` | [General Purpose Timer Driver](./Gpt/) | Vector-provided |
| `Mcu` | [Microcontroller Unit Driver](./Mcu/) | Vector-provided |
| `Port` | [Port Driver](./Port/) | Vector-provided |
| `Spi` | [Serial Peripheral Interface Driver](./Spi/) | Vector-provided |
| `Startup` | [Startup Code](./Startup/) | Custom (in-house) |
| `Wdg` | [Watchdog Driver](./Wdg/) | Vector-provided |
