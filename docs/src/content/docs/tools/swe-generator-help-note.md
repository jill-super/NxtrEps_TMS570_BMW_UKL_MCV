---
title: "Software Entity Generator Help Note"
description: "What the SWE Generator compiled-help files cover and how to read them."
---

## Scope of this note

Two compiled Windows help files ship with the Software Entity (SWE) Generator and cannot be converted to Markdown with the available tooling:

- `BMW_UKL_MCV_EPS_TMS570/Tools/SWE_Generator/SWE-GeneratorHelp.chm` (German online help)
- `BMW_UKL_MCV_EPS_TMS570/Tools/SWE_Generator/SWE-GeneratorHelp_engl.chm` (English online help)

## What the help files cover

Based on the installation context and the converted [Release Notes](./swe-generator-release-notes/): the Software Entity Generator packages the post-build hex image into BMW Software Entity containers (hash/signature tables, `EDCH` tables, `CHECKSUM_TABLE_TO_EDCH_TABLE` commands), with a **Config-Editor mode** (configuration buttons replaced the former configuration menu) and switchable generator modes under the View menu.

## How to read the originals

1. On a Windows host, double-click the `.chm` file (use the `_engl` file for English).
2. If the content pane stays blank, unblock the file (right-click → Properties → Unblock) — Windows blocks scripted content in help files downloaded from other machines.
3. The generator itself is invoked from `SwProject/postbuild.bat` with the `SWEGEN_PATH` tool directory; the three Software Entity identifiers built for this project are `00001892_000_000_000`, `00001893_000_000_000` and `00001894_000_000_000` (see [Post-Build Process](./postbuild/)).
