---
title: "Toolchain Overview"
description: "Compilers, configurators and host utilities used to build and calibrate the firmware."
---

## Compiler and IDE

- **Code Composer Studio (CCS) v5** with the **ARM Optimizing C/C++ Compiler v4.6** targeting the TMS570 (Cortex-R4F). All files compile in Thumb mode except the ARM-mode files listed in the build-environment manual; optimisation is level 2 / speed 3 with per-file exceptions (see [Build Environment](./build-environment/)).
- The build uses a **generated Makefile** from the CCSv5 installation (see [Build Environment](./build-environment/)).

## Configuration and code generation

- **Vector DaVinci Configurator / Developer** — configures the MICROSAR Basic Software and generates `Source/GenData/**` (module configuration), the Runtime Environment (`Source/GenDataRte/`), the Operating System configuration (`Source/GenDataOS/`) and end-to-end protection wrappers (`Source/GenDataE2EPW/`). See [Runtime Environment](../rte-os/Rte/) and [Operating System](../rte-os/Os/).
- **Data Dictionary Tool** (`Tools/DataDictTool/DDLauncher.bat`) — manages shared data-dictionary definitions consumed by components and generation.
- **Component generator batch files** — each `generate/` folder (for example `MtrCtrl_VM/generate/Ap_PhaseCtrl_Generate.bat`) regenerates the component's artefacts; `tools/RteGen.bat` regenerates the component Runtime Environment contracts.

## Calibration, measurement and analysis

- **CANape** (`Tools/CANape/refresh.bat`, `update_a2l.bat`) with the generated A2L description for measurement and calibration over the [Universal Measurement and Calibration Protocol Service](../services/XcpSvc/).
- **Gliwa T1** ([Timing Measurement Library](../libraries/GliwaT1/)) with the performance-measurement unit initialisation in `sys_pmu.asm` for execution-time analysis.
- **QA-C** (`Tools/QAC/`) configuration for static analysis; MISRA deviations are documented per file (for example library-macro deviations in application components).

## Post-build chain

- **nowECC** (Texas Instruments, `Tools/nowECC/nowECC.exe`) appends Error Correction Code data to the programmed image — see the converted [nowECC User's Guide](./nowecc-users-guide/) and [Post-Build Process](./postbuild/).
- **HexView** (`Tools/HexView/`) inspects/edits hex records during post-build — see the converted [HexView Reference Manual](./hexview-reference-manual/).
- **Software Entity Generator** (`Tools/SWE_Generator/`) produces the BMW Software Entity programmable files (hash/signature packaging) — see the converted [Release Notes](./swe-generator-release-notes/), the [help note](./swe-generator-help-note/) and [Post-Build Process](./postbuild/).
- **CCT** (`Tools/CCT/`, invoked via `Tools/PostBuild/PostBuildCCT.bat`) and **hex470** complete the image preparation; `SwProject/postbuild.bat` orchestrates all steps.

## Pre-build step

`SwProject/prebuild.bat` (by Nexteer) renames the compiler-toolchain standard AUTOSAR headers (`Compiler.h`, `Compiler_Cfg.h`, `Platform_Types.h`, `Std_Types.h` with `.bak`) so they cannot shadow the project/Vector headers during compilation.
