---
title: "Post-Build Process"
description: "How the linked firmware becomes BMW-programmable Software Entity files."
---

## Build configurations

The Code Composer Studio project defines (at least) **Release**, **Debug** and **Fault Injection** configurations. The [Build Environment](./build-environment/) manual lists per-configuration excluded files: the [Fault Injection](../asw/FltInjection/) component and test scaffolding are excluded from production builds, and hardware-near files not needed by the application build (for example unused cyclic-redundancy-check or crypto objects) are excluded per configuration.

## Link step

- Linker command file: `BMW_UKL_MCV_EPS_TMS570/SwProject/TMS570LS202x6SFlashLnk.cmd` (Nexteer) — places vector tables, initialised sections, calibration segments (`FlashCalSeg`/`RamCalSeg`), crypto no-init regions and the reset-cause flag; flash regions are filled to contiguous ranges for Error Correction Code generation.
- Default output names: `EPS_UKL_MCV_dbg` (debug) and `EPS_UKL_MCV_flt` (fault-injection); metric/Central Processing Unit-load variants exist for timing analysis.

## Post-build orchestration (`SwProject/postbuild.bat`)

1. **Hex generation** — converts the linker output (`.out`) to Intel-hex/Motorola S-records with `hex470`.
2. **Error Correction Code injection** — `Tools/nowECC/nowECC.exe` appends Error Correction Code data for the TMS570 flash (see [nowECC User's Guide](./nowecc-users-guide/)).
3. **Software Entity packaging** — `Tools/SWE_Generator/` builds the three BMW Software Entity containers (`00001892_000_000_000`, `00001893_000_000_000`, `00001894_000_000_000`) with hashes/signatures, assisted by `Tools/CCT/` via `Tools/PostBuild/PostBuildCCT.bat` and inspected with [HexView](./hexview-reference-manual/).
4. **Archiving** — `archive.bat` packs the deliverables into the required secure-library archives (WinZip command-line add-on required on the build host).

Set `ARCHIVE_ACTIVE=0` in `postbuild.bat` to skip the archive step during development iterations.
