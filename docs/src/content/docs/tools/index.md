---
title: "Tools and Build System"
description: "Host-side tools, build environment, post-build chain and converted tool manuals."
---

Host-side tooling around the firmware: how it is built, packaged for BMW programming, calibrated and analysed.

## Build and packaging

| Page | Content |
| --- | --- |
| [Toolchain Overview](./toolchain/) | Compiler, Code Composer Studio project, DaVinci generation, CANape, QA-C |
| [Post-Build Process](./postbuild/) | Link step, hex generation, Error Correction Code injection, Software Entity packaging, archiving |
| [Build Environment](./build-environment/) | Converted Word manual: compile settings, optimisation, excluded files, project properties |

## Converted tool manuals

| Page | Source document |
| --- | --- |
| [nowECC User's Guide](./nowecc-users-guide/) | Texas Instruments SPNU491B (PDF, 15 pages) |
| [HexView Reference Manual](./hexview-reference-manual/) | HexView 1.6 reference (PDF, 79 pages) |
| [Software Entity Generator Release Notes](./swe-generator-release-notes/) | SWE Generator history up to 3.8.0 (PDF, 7 pages) |
| [Software Entity Generator Help Note](./swe-generator-help-note/) | Reading guide for the two `.chm` help files (not convertible to Markdown) |

See the [Documentation Guide](../general/documentation-guide/) for the full conversion register and limitations.
