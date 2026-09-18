---
title: "ECU Abstraction"
description: "Hardware abstraction: uniform sensor/actuator, memory-hardware-abstraction, FlexRay-interface and in-house peripheral drivers."
---

Hardware abstraction: uniform sensor/actuator, memory-hardware-abstraction, FlexRay-interface and in-house peripheral drivers.

## Modules in this layer

| Module directory | Module long name | Origin |
| --- | --- | --- |
| `Adc` | [Analog-to-Digital Converter Driver](./Adc/) | Custom (in-house) |
| `Dma` | [Direct Memory Access Driver](./Dma/) | Custom (in-house) |
| `FrIf` | [FlexRay Interface](./FrIf/) | Vector-provided |
| `Nhet` | [High-End Timer Driver](./Nhet/) | Custom (in-house) |
| `IoHwAb` | [Input Output Hardware Abstraction](./IoHwAb/) | Custom (in-house) |
| `SpiNxt` | [Serial Peripheral Interface Driver, Nexteer Extension](./SpiNxt/) | Custom (in-house) |
