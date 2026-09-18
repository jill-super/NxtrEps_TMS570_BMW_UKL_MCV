---
title: "Repository Structure"
description: "Top-level layout of the repository and where the documentation site lives."
---

## Top-level layout

```text
<repository root>/
├── LICENSE                              # MIT License (this project)
├── README.md                            # Project landing page (this documentation links from it)
├── docs/                                # ★ Documentation site source (Astro + Starlight project root)
│   ├── astro.config.mjs                 # Site configuration (GitHub Pages URL derived from git remote)
│   ├── package.json                     # Node dependencies (astro, @astrojs/starlight, sharp)
│   ├── tsconfig.json
│   ├── public/                          # Static assets copied verbatim
│   └── src/
│       ├── assets/                      # Logo and images
│       ├── styles/custom.css            # Site styles
│       └── content/docs/                # ★ All documentation pages (see below)
├── <Module>/                            # One directory per software component, e.g. Assist/, StaMd/
│   ├── src/                             # Implementation (.c/.asm)
│   ├── include/                         # Public headers (where present)
│   ├── generate/                        # Generator batch files / templates (where present)
│   ├── tools/                           # Host-side helpers, e.g. RteGen.bat (where present)
│   └── utp/                             # Unit-test project artefacts (where present)
├── BMW_UKL_MCV_EPS_TMS570/              # Integration project (Basic Software, Runtime Environment, tools)
│   ├── SwProject/Source/                # BSW/, CDD/, GenData*/, Appl_*.c, NtWrap.c, …
│   ├── SwProject/*.bat, *.cmd           # Pre/post-build steps, TMS570 linker command file
│   └── Tools/                           # Host utilities: Build Environment, nowECC, HexView,
│                                        #   SWE Generator, CANape, DataDictTool, QAC, PostBuild, …
├── NxtrLib/  StdDef/  GliwaT1/          # Shared libraries
└── zzz_binaries/                        # Build-output / binary drop folder (not documented in detail)
```

## Documentation content layout

Inside `docs/src/content/docs/` (the Astro project root is `docs/`, so every path below is relative to it):

```text
docs/src/content/docs/
├── index.md                 # Landing page
├── general/                 # Architecture, layers, Vector-vs-custom, glossary, …
├── asw/                     # Application Software module pages + index
├── cdd/                     # Complex Device Driver pages + index
├── services/                # Basic Software Services pages + index
├── ecu-abstraction/         # ECU Abstraction pages + index
├── mcal/                    # Microcontroller Abstraction pages + index
├── rte-os/                  # Runtime Environment & Operating System pages + index
├── libraries/               # Library pages + index
└── tools/                   # Build/tool pages + converted Word/PDF manuals + index
```

Only `docs/` contains documentation-site files (configuration, `package.json`, `src/`, `public/`). The firmware sources, tools and binaries elsewhere in the repository are untouched.

## Documentation workflow

1. Edit Markdown under `docs/src/content/docs/` (Starlight front matter: `title` plus `description`).
2. Navigation is generated automatically from the folder structure (`autogenerate` groups in `docs/astro.config.mjs`).
3. Build and preview locally (requires Node.js):
   ```sh
   cd docs
   npm install
   npm run build
   npm run preview
   ```
4. Publishing to GitHub Pages needs no configuration edit: `docs/astro.config.mjs` derives `site` and `base` from the `origin` git remote at build time, so forks publish under their own coordinates automatically.
