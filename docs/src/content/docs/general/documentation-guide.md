---
title: "Documentation Guide"
description: "Register of documents converted from Word and PDF originals, and conversion limitations."
---

## Converted documents

The repository contained no `doc/` folders inside the module directories. The convertible documents found elsewhere (host-tool folders) were converted to Markdown and published under [Tools and Build System](../tools/):

| Original file | Published page | Format | Conversion |
| --- | --- | --- | --- |
| `BMW_UKL_MCV_EPS_TMS570/Tools/Build Environment/Build Environment.docx` | [Build Environment](../tools/build-environment/) | Word `.docx` (164 paragraphs, 42 tables) | Full conversion: headings, lists, tables preserved |
| `BMW_UKL_MCV_EPS_TMS570/Tools/nowECC/SPNU491B.pdf` | [nowECC User's Guide](../tools/nowecc-users-guide/) | PDF, 15 pages (Texas Instruments) | Full conversion, structured by the PDF table of contents |
| `BMW_UKL_MCV_EPS_TMS570/Tools/SWE_Generator/releasenotes.pdf` | [Software Entity Generator Release Notes](../tools/swe-generator-release-notes/) | PDF, 7 pages | Full conversion |
| `BMW_UKL_MCV_EPS_TMS570/Tools/HexView/ReferenceManual_HexView.pdf` | [HexView Reference Manual](../tools/hexview-reference-manual/) | PDF, 79 pages | Full conversion, structured by the PDF table of contents |

Each converted page starts with a banner naming its source file. Section headings follow the original table of contents; original PDF page breaks are marked with HTML comments. Complex figures and embedded images are not carried over — consult the original file in the repository for pixel-faithful diagrams.

## Files that could not be converted to Markdown

| File | Reason | What is published instead |
| --- | --- | --- |
| `BMW_UKL_MCV_EPS_TMS570/Tools/SWE_Generator/SWE-GeneratorHelp.chm` | Compiled HTML Help (`.chm`) cannot be faithfully converted with the available tooling | [Software Entity Generator help note](../tools/swe-generator-help-note/) — structured summary: purpose in the post-build chain, how to open the file on Windows, and where the generator is invoked |
| `BMW_UKL_MCV_EPS_TMS570/Tools/SWE_Generator/SWE-GeneratorHelp_engl.chm` | Same as above (English edition) | Covered by the same help note |

## Module documentation

No Word or PDF files were found inside the component directories, so every module page in this site is generated from the code itself: purpose, key files, runnables, includes, generator artefacts and dependencies are read from the actual sources. Where a short name or detail is ambiguous, the page states the assumption explicitly.
