---
title: "Application Software"
description: "Steering functions, safety monitors and BMW vehicle features implemented as AUTOSAR software components (`Ap_*` application components, `Sa_*` sensor/actuator components)."
---

Steering functions, safety monitors and BMW vehicle features implemented as AUTOSAR software components (`Ap_*` application components, `Sa_*` sensor/actuator components).

## Modules in this layer

| Module directory | Module long name | Origin |
| --- | --- | --- |
| `AbsHwPos` | [Absolute Hardware Position](./AbsHwPos/) | Custom (in-house) |
| `ActivePull` | [Active Pull Compensation](./ActivePull/) | Custom (in-house) |
| `AssistFirewall` | [Assist Plausibility Firewall](./AssistFirewall/) | Custom (in-house) |
| `Polarity` | [Assist Polarity Management](./Polarity/) | Custom (in-house) |
| `AssistSumnLmt` | [Assist Summation Limiter](./AssistSumnLmt/) | Custom (in-house) |
| `AvgFricLrn` | [Average Friction Learning](./AvgFricLrn/) | Custom (in-house) |
| `BkCpPc` | [Backup Capacitor Pre-Charge](./BkCpPc/) | Custom (in-house) |
| `Assist` | [Base Power Assist](./Assist/) | Custom (in-house) |
| `BVDiag` | [Battery Voltage Diagnostics](./BVDiag/) | Custom (in-house) |
| `BatteryVoltage` | [Battery Voltage Sensing](./BatteryVoltage/) | Custom (in-house) |
| `BmwHaptcFb` | [BMW Haptic Feedback](./BmwHaptcFb/) | Custom (BMW-specific) |
| `CBD_BmwRtnAbrn` | [BMW Return Arbitration](./CBD_BmwRtnAbrn/) | Custom (BMW-specific) |
| `BmwTqOvrlCdng` | [BMW Torque Overlay Coding](./BmwTqOvrlCdng/) | Custom (BMW-specific) |
| `Xcp` | [Calibration and Measurement Access](./Xcp/) | Custom (in-house) |
| `CtrldDisShtdn` | [Controlled Disable Shutdown](./CtrldDisShtdn/) | Custom (in-house) |
| `CtrlTemp` | [Controller Temperature Monitoring](./CtrlTemp/) | Custom (in-house) |
| `CustPL_BMW` | [Customer Product Line, BMW Variant](./CustPL_BMW/) | Custom (BMW-specific) |
| `DampingFirewall` | [Damping Plausibility Firewall](./DampingFirewall/) | Custom (in-house) |
| `DrvDynCtrl` | [Driving Dynamics Control](./DrvDynCtrl/) | Custom (in-house) |
| `DrvDynEnbl` | [Driving Dynamics Enable](./DrvDynEnbl/) | Custom (in-house) |
| `ElecPwr` | [Electrical Power Management](./ElecPwr/) | Custom (in-house) |
| `EOTActuatorMng` | [End-of-Travel Actuator Management](./EOTActuatorMng/) | Custom (in-house) |
| `EtDmpFw` | [Enhanced Torque Damping Firewall](./EtDmpFw/) | Custom (in-house) |
| `FltInjection` | [Fault Injection](./FltInjection/) | Custom (in-house) |
| `Sweep` | [Frequency Sweep Excitation](./Sweep/) | Custom (in-house) |
| `FrqDepDmpnInrtCmp` | [Frequency-Dependent Damping and Inertia Compensation](./FrqDepDmpnInrtCmp/) | Custom (in-house) |
| `GenPosTraj` | [Generic Position Trajectory](./GenPosTraj/) | Custom (in-house) |
| `Gsod` | [Global Shutdown](./Gsod/) | Custom (in-house) |
| `HwTrq` | [Handwheel Torque Sensing](./HwTrq/) | Custom (in-house) |
| `HwPwUp` | [Hardware Power-Up Sequencing](./HwPwUp/) | Custom (in-house) |
| `HiLoadStall` | [High-Load Stall Protection](./HiLoadStall/) | Custom (in-house) |
| `HystAdd` | [Hysteresis Addition](./HystAdd/) | Custom (in-house) |
| `HystComp` | [Hysteresis Compensation](./HystComp/) | Custom (in-house) |
| `LrnEOT` | [Learn End of Travel](./LrnEOT/) | Custom (in-house) |
| `LnRkCr` | [Learn Rack Center](./LnRkCr/) | Custom (in-house) |
| `LmtCod` | [Limiter Coding](./LmtCod/) | Custom (in-house) |
| `LktoLkStr` | [Lock-to-Lock Steering Travel](./LktoLkStr/) | Custom (in-house) |
| `MtrCtrl_VM` | [Motor Control, Voltage Mode](./MtrCtrl_VM/) | Custom (in-house) |
| `MtrCurr_VM` | [Motor Current Sensing, Voltage Mode](./MtrCurr_VM/) | Custom (in-house) |
| `MtrPos` | [Motor Position Sensing](./MtrPos/) | Custom (in-house) |
| `MtrTempEst` | [Motor Temperature Estimation](./MtrTempEst/) | Custom (in-house) |
| `MtrVel` | [Motor Velocity Estimation](./MtrVel/) | Custom (in-house) |
| `OscTraj` | [Oscillation Trajectory Generator](./OscTraj/) | Custom (in-house) |
| `ParkAstEnbl_BMW` | [Park Assist Enable, BMW Variant](./ParkAstEnbl_BMW/) | Custom (BMW-specific) |
| `PrkAstMfgServCh2` | [Park Assist Manufacturing Service, Channel 2](./PrkAstMfgServCh2/) | Custom (in-house) |
| `PhaseDscnt` | [Phase Disconnect](./PhaseDscnt/) | Custom (in-house) |
| `PosServo` | [Position Servo Control](./PosServo/) | Custom (in-house) |
| `PwrLmtFunc` | [Power Limit Function](./PwrLmtFunc/) | Custom (in-house) |
| `RackLoad` | [Rack Load Estimation](./RackLoad/) | Custom (in-house) |
| `ReturnFirewall` | [Return Plausibility Firewall](./ReturnFirewall/) | Custom (in-house) |
| `Return` | [Return-to-Center Control](./Return/) | Custom (in-house) |
| `ShtdnMech` | [Shutdown Mechanism](./ShtdnMech/) | Custom (in-house) |
| `SgnlCond` | [Signal Conditioning](./SgnlCond/) | Custom (in-house) |
| `StabilityComp` | [Stability Compensation](./StabilityComp/) | Custom (in-house) |
| `StOpCtrl` | [Start-Stop Control](./StOpCtrl/) | Custom (in-house) |
| `Damping` | [Steering Damping](./Damping/) | Custom (in-house) |
| `StaMd` | [System State Manager](./StaMd/) | Custom (in-house) |
| `TmprlMon` | [Temporal Monitor](./TmprlMon/) | Custom (in-house) |
| `ThrmDutyCycle` | [Thermal Duty Cycle Management](./ThrmDutyCycle/) | Custom (in-house) |
| `TrqOsc` | [Torque Oscillation Management](./TrqOsc/) | Custom (in-house) |
| `TrqBasedInrtCmp` | [Torque-Based Inertia Compensation](./TrqBasedInrtCmp/) | Custom (in-house) |
| `TJADamp` | [Traffic Jam Assist Damping](./TJADamp/) | Custom (in-house) |
| `TuningSelAuth` | [Tuning Selection Authority](./TuningSelAuth/) | Custom (in-house) |
| `VehSpdLmt` | [Vehicle Speed Limiter](./VehSpdLmt/) | Custom (in-house) |
