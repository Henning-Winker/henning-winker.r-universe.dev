# Henning Winker's R-universe

[![R-universe](https://henning-winker.r-universe.dev/badges/:registry)](https://github.com/r-universe/henning-winker)
[![Packages](https://henning-winker.r-universe.dev/badges/:total)](https://henning-winker.r-universe.dev/)

Fisheries stock-assessment and simulation tools used in training courses.
Pre-built binaries for Windows, macOS and Linux are at
<https://henning-winker.r-universe.dev>, so no Rtools or compiler is needed.

| Package | What it does |
|---|---|
| **JABBA3** | Bayesian state-space surplus production models in RTMB |
| **FLicc** | Length-interval catch-curve models in TMB (FLR) |
| **cpueTargeting** | Simulators and tools for CPUE targeting and standardization |
| **FLOSS** | FL operating model and sampling simulator for training datasets |
| **mmsyFM** | Multispecies MSY fleet model for mixed-fishery harvest strategies |

## Install

The FLR dependencies (FLCore, ggplotFL, FLBRP, FLasher, FLife, FLRef, ...) come
from the FLR universe, so list all three repositories:

```r
repos <- c(
  hw   = "https://henning-winker.r-universe.dev",
  flr  = "https://flr.r-universe.dev",
  CRAN = "https://cloud.r-project.org"
)

install.packages(c("JABBA3", "FLicc", "cpueTargeting", "FLOSS", "mmsyFM"),
                 repos = repos)
```

To make this permanent (so `install.packages()` and `update.packages()` just
work), add the `options(repos = repos)` line to your `~/.Rprofile`.

## Adding a package

Add an entry to [`packages.json`](packages.json). R-universe rebuilds on every
push to a listed repository, but users only see an update via
`update.packages()` when the `Version:` field in `DESCRIPTION` is bumped.
