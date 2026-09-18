---
title: "Glossary"
description: "Every abbreviation and short module name expanded to its long name."
---

Short names are expanded everywhere in this documentation. Entries marked **(assumption)** are best-effort expansions where the repository does not spell the name out; they are flagged on the relevant module pages as well.

## General and AUTOSAR abbreviations

| Short form | Long name |
| --- | --- |
| ASIL D | Automotive Safety Integrity Level D (highest level, ISO 26262) |
| ASW | Application Software |
| AUTOSAR | Automotive Open System Architecture |
| BMW UKL | BMW front-wheel-drive platform (Unterklasse) |
| BSW | Basic Software |
| CBD | Customer Building Block Designation (project-specific prefix for customer building blocks) **(assumption)** |
| CDD | Complex Device Driver |
| CMS | Calibration and Measurement System **(assumption)** |
| CRC | Cyclic Redundancy Check |
| DaVinci | Vector DaVinci Configurator / Developer (configuration and modelling tools) |
| ECC | Error Correction Code |
| ECU | Electronic Control Unit |
| EOL | End of Line (manufacturing) |
| EOT | End of Travel |
| EPS | Electric Power Steering |
| ESM | Error Signaling Module (TMS570) |
| HMI | Human-Machine Interface |
| ISO 26262 | Road vehicles — Functional safety (standard) |
| MCAL | Microcontroller Abstraction Layer |
| MICROSAR | Vector implementation of AUTOSAR Basic Software |
| NHET | New High-End Timer (TMS570 co-processor) |
| NVM | Non-Volatile Memory |
| OS | Operating System |
| QAC | QA-C static code analyser |
| RTE | Runtime Environment |
| SCom | Server-call (client-server) Communication operation |
| SWE | Software Entity (BMW software packaging unit) |
| TJA | Traffic Jam Assist **(assumption)** |
| UDS | Unified Diagnostic Services (ISO 14229) |
| VM | Voltage Mode (motor-control variant designation) **(assumption)** |
| XCP | Universal Measurement and Calibration Protocol |

## Module short names

| Directory | Long name |
| --- | --- |
| `AbsHwPos/` | Absolute Hardware Position |
| `ActivePull/` | Active Pull Compensation |
| `Adc/` | Analog-to-Digital Converter Driver |
| `Assist/` | Base Power Assist |
| `AssistFirewall/` | Assist Plausibility Firewall |
| `AssistSumnLmt/` | Assist Summation Limiter |
| `AvgFricLrn/` | Average Friction Learning |
| `BVDiag/` | Battery Voltage Diagnostics |
| `BatteryVoltage/` | Battery Voltage Sensing |
| `BkCpPc/` | Backup Capacitor Pre-Charge **(assumption)** |
| `BmwHaptcFb/` | BMW Haptic Feedback |
| `BmwTqOvrlCdng/` | BMW Torque Overlay Coding |
| `CBD_BmwRtnAbrn/` | BMW Return Arbitration (customer building block) |
| `CMS_BMW/` | Calibration and Measurement System, BMW Variant |
| `CMS_Common/` | Calibration and Measurement System, Common Services |
| `CtrlTemp/` | Controller Temperature Monitoring |
| `CtrldDisShtdn/` | Controlled Disable Shutdown |
| `CustPL_BMW/` | Customer Product Line, BMW Variant **(assumption)** |
| `Damping/` | Steering Damping |
| `DampingFirewall/` | Damping Plausibility Firewall |
| `DiagMgr/` | Diagnostic Manager |
| `Dma/` | Direct Memory Access Driver |
| `DrvDynCtrl/` | Driving Dynamics Control |
| `DrvDynEnbl/` | Driving Dynamics Enable |
| `EOTActuatorMng/` | End-of-Travel Actuator Management |
| `ElecPwr/` | Electrical Power Management |
| `EtDmpFw/` | Enhanced Torque Damping Firewall **(assumption)** |
| `Fee/` | Flash EEPROM Emulation |
| `Fls/` | Flash Driver |
| `FltInjection/` | Fault Injection |
| `FrTrcvPhy/` | FlexRay Transceiver Physical Driver |
| `FrqDepDmpnInrtCmp/` | Frequency-Dependent Damping and Inertia Compensation |
| `GenPosTraj/` | Generic Position Trajectory |
| `GliwaT1/` | Gliwa Timing Measurement Library T1 |
| `Gsod/` | Global Shutdown **(assumption)** |
| `HiLoadStall/` | High-Load Stall Protection |
| `HwPwUp/` | Hardware Power-Up Sequencing |
| `HwTrq/` | Handwheel Torque Sensing |
| `HystAdd/` | Hysteresis Addition |
| `HystComp/` | Hysteresis Compensation |
| `LktoLkStr/` | Lock-to-Lock Steering Travel |
| `LmtCod/` | Limiter Coding |
| `LnRkCr/` | Learn Rack Center |
| `LrnEOT/` | Learn End of Travel |
| `MtrCtrl_VM/` | Motor Control, Voltage Mode |
| `MtrCurr_VM/` | Motor Current Sensing, Voltage Mode |
| `MtrPos/` | Motor Position Sensing |
| `MtrTempEst/` | Motor Temperature Estimation |
| `MtrVel/` | Motor Velocity Estimation |
| `Nhet/` | High-End Timer Driver |
| `NvMMgr/` | Non-Volatile Memory Manager |
| `NvMProxy/` | Non-Volatile Memory Proxy |
| `NxtrLib/` | Nexteer Mathematics and Utility Library |
| `OscTraj/` | Oscillation Trajectory Generator |
| `ParkAstEnbl_BMW/` | Park Assist Enable, BMW Variant |
| `PhaseDscnt/` | Phase Disconnect |
| `Polarity/` | Assist Polarity Management |
| `PosServo/` | Position Servo Control |
| `PrkAstMfgServCh2/` | Park Assist Manufacturing Service, Channel 2 |
| `PwrLmtFunc/` | Power Limit Function |
| `RackLoad/` | Rack Load Estimation |
| `Return/` | Return-to-Center Control |
| `ReturnFirewall/` | Return Plausibility Firewall |
| `SVDiag/` | Power Stage Diagnostics (System Voltage / Supervisory Diagnostics) |
| `SVDrvr/` | Power Stage Driver (System Voltage / Supervisory Driver) |
| `SgnlCond/` | Signal Conditioning |
| `ShtdnMech/` | Shutdown Mechanism |
| `SpiNxt/` | Serial Peripheral Interface Driver, Nexteer Extension |
| `StOpCtrl/` | Start-Stop Control **(assumption)** |
| `StaMd/` | System State Manager |
| `StabilityComp/` | Stability Compensation |
| `StdDef/` | Standard Type Definitions |
| `Sweep/` | Frequency Sweep Excitation |
| `TJADamp/` | Traffic Jam Assist Damping |
| `TMS570_Startup/` | TMS570 Startup Code |
| `TMS570_uDiag/` | TMS570 Microcontroller Diagnostics |
| `TcFlshPrg/` | Turns Counter Flash Programming |
| `ThrmDutyCycle/` | Thermal Duty Cycle Management |
| `TmprlMon/` | Temporal Monitor |
| `TrqBasedInrtCmp/` | Torque-Based Inertia Compensation |
| `TrqOsc/` | Torque Oscillation Management |
| `TuningSelAuth/` | Tuning Selection Authority |
| `TurnsCounter/` | Steering Turns Counter |
| `VehSpdLmt/` | Vehicle Speed Limiter |
| `Xcp/` | Calibration and Measurement Access |
