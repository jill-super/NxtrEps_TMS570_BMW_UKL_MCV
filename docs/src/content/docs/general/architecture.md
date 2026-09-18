---
title: "System Architecture"
description: "End-to-end architecture of the Electric Power Steering firmware on TMS570."
---

This page describes how the Electric Power Steering (Electric Power Steering) firmware is organised and how data flows from the driver's hands to the steering rack.

## Hardware context

- **Microcontroller:** Texas Instruments TMS570 (Cortex-R4F, lockstep-capable safety microcontroller with Error Correction Code flash, Error Signaling Module and memory protection).
- **Power stage:** 3-phase permanent-magnet synchronous motor driven by a gated power bridge with phase-disconnect capability.
- **Sensors:** redundant handwheel torque sensing, motor position sensing, motor current sensing, battery voltage sensing, controller temperature sensing and a Serial Peripheral Interface turns counter that retains absolute steering-wheel revolutions across power cycles.
- **Vehicle network:** FlexRay cluster (E-Ray controller plus TJA1080 transceiver) for chassis communication, diagnostics and calibration.

## Signal flow

1. **Driver intent acquisition** — [Handwheel Torque Sensing](../asw/HwTrq/) and [Absolute Hardware Position](../asw/AbsHwPos/) acquire and plausibility-check the driver inputs; [Signal Conditioning](../asw/SgnlCond/) filters shared sensor signals.
2. **Assist computation** — [Base Power Assist](../asw/Assist/) converts torque and vehicle speed into a base command; overlays ([Active Pull Compensation](../asw/ActivePull/), [Steering Damping](../asw/Damping/), [Return-to-Center Control](../asw/Return/), [Frequency-Dependent Damping and Inertia Compensation](../asw/FrqDepDmpnInrtCmp/), [Torque-Based Inertia Compensation](../asw/TrqBasedInrtCmp/), BMW-specific overlays) add their contributions.
3. **Safety bounding** — each contribution passes a plausibility firewall ([Assist Plausibility Firewall](../asw/AssistFirewall/), [Damping Plausibility Firewall](../asw/DampingFirewall/), [Return Plausibility Firewall](../asw/ReturnFirewall/), [Enhanced Torque Damping Firewall](../asw/EtDmpFw/)) and the contributions are summed and limited by the [Assist Summation Limiter](../asw/AssistSumnLmt/) and [Power Limit Function](../asw/PwrLmtFunc/).
4. **Motor execution** — [Motor Control, Voltage Mode](../asw/MtrCtrl_VM/) (current estimation, phase control, voltage control) drives the [Power Stage Driver](../cdd/SVDrvr/) through the [Phase Disconnect](../asw/PhaseDscnt/) safe-state path, closing the loop with [Motor Position Sensing](../asw/MtrPos/), [Motor Current Sensing, Voltage Mode](../asw/MtrCurr_VM/) and [Motor Velocity Estimation](../asw/MtrVel/).
5. **Adaptation and protection** — [Average Friction Learning](../asw/AvgFricLrn/), [Learn End of Travel](../asw/LrnEOT/), [Learn Rack Center](../asw/LnRkCr/), [Motor Temperature Estimation](../asw/MtrTempEst/) and [Thermal Duty Cycle Management](../asw/ThrmDutyCycle/) adapt behaviour and derate effort before hardware limits are reached.

## Supervision

- The [System State Manager](../asw/StaMd/) owns the Electric Power Steering state machine; every component follows the published state mode.
- The [Diagnostic Manager](../services/DiagMgr/) collects, debounces and prioritises faults, triggers fail-safe actions and reports to the [Diagnostic Event Manager](../services/Dem/).
- The [Temporal Monitor](../asw/TmprlMon/) and the [Watchdog Manager](../services/WdgM/) supervise program flow and timing; the [Shutdown Mechanism](../asw/ShtdnMech/) and [Controlled Disable Shutdown](../asw/CtrldDisShtdn/) force safe states.
- Microcontroller-level faults are caught by [TMS570 Microcontroller Diagnostics](../cdd/TMS570_uDiag/) (clock, Error Correction Code, Error Signaling Module, loss of execution).

## Layered view

The software is layered per Automotive Open System Architecture: [Application Software](../asw/) on top of the [Runtime Environment](../rte-os/Rte/), with [Complex Device Drivers](../cdd/) for hardware-near functions, [Services](../services/), [ECU Abstraction](../ecu-abstraction/) and the [Microcontroller Abstraction](../mcal/) below. See [AUTOSAR layers](./autosar-layers/) for the full mapping and [Vector versus custom](./vector-vs-custom/) for code ownership.
