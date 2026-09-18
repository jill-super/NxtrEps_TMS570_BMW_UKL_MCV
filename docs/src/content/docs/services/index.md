---
title: "Basic Software: Services"
description: "System services: diagnostics, communication, memory, watchdogs, cryptography and the application Diagnostic Manager."
---

System services: diagnostics, communication, memory, watchdogs, cryptography and the application Diagnostic Manager.

## Modules in this layer

| Module directory | Module long name | Origin |
| --- | --- | --- |
| `DiagBoot` | [Bootloader Diagnostics](./DiagBoot/) | Custom (in-house) |
| `Cal` | [Calibration Data Manager](./Cal/) | Custom (in-house) |
| `Com` | [Communication](./Com/) | Vector-provided |
| `ComM` | [Communication Manager](./ComM/) | Vector-provided |
| `Cpl` | [Crypto Platform Library](./Cpl/) | Custom (in-house) |
| `Crypto` | [Cryptographic Services](./Crypto/) | Custom (in-house) |
| `Cdc` | [Custom Diagnostic Communication](./Cdc/) | Custom (in-house) |
| `Crc` | [Cyclic Redundancy Check](./Crc/) | Vector-provided |
| `Det` | [Default Error Tracer](./Det/) | Vector-provided |
| `Darh` | [Diagnostic Authentication and Roles Handling](./Darh/) | Custom (in-house) |
| `Dcm` | [Diagnostic Communication Manager](./Dcm/) | Vector-provided |
| `Dem` | [Diagnostic Event Manager](./Dem/) | Third-party (Elektrobit) |
| `DiagMgr` | [Diagnostic Manager](./DiagMgr/) | Custom (in-house) |
| `EcuM` | [Electronic Control Unit State Manager](./EcuM/) | Vector-provided |
| `E2E` | [End-to-End Protection](./E2E/) | Vector-provided |
| `Fee` | [Flash EEPROM Emulation](./Fee/) | Third-party (Texas Instruments) |
| `FrSM` | [FlexRay State Manager](./FrSM/) | Vector-provided |
| `FrTp` | [FlexRay Transport Protocol](./FrTp/) | Vector-provided |
| `FreeTimer` | [Free-Running Timer Service](./FreeTimer/) | Custom (in-house) |
| `IpduM` | [Interaction-Layer Protocol Data Unit Multiplexer](./IpduM/) | Vector-provided |
| `MemIf` | [Memory Abstraction Interface](./MemIf/) | Vector-provided |
| `NvM` | [Non-Volatile Memory Manager](./NvM/) | Vector-provided |
| `Nrv2b` | [NRV2B Decompression](./Nrv2b/) | Third-party (open-source (UCL)) |
| `PduR` | [Protocol Data Unit Router](./PduR/) | Vector-provided |
| `SipVersionCheck` | [Software Integration Package Version Check](./SipVersionCheck/) | Vector-provided |
| `SysTimeClient` | [System Time Client](./SysTimeClient/) | Vector-provided |
| `XcpSvc` | [Universal Measurement and Calibration Protocol Service](./XcpSvc/) | Vector-provided |
| `Coding` | [Variant Coding](./Coding/) | Custom (in-house) |
| `Vsm` | [Vehicle System Manager](./Vsm/) | Vector-provided |
| `WdgIf` | [Watchdog Interface](./WdgIf/) | Vector-provided |
| `WdgM` | [Watchdog Manager](./WdgM/) | Vector-provided |
