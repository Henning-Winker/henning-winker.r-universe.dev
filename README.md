# Henning Winker's R-universe

[![R-universe status](https://henning-winker.r-universe.dev/badges/:registry)](https://github.com/r-universe/henning-winker)
[![Packages](https://henning-winker.r-universe.dev/badges/:total)](https://henning-winker.r-universe.dev/)

R packages for fisheries stock assessment, simulation and harvest strategy
evaluation, developed for capacity-building and training courses.

Packages are built automatically for **Windows, macOS and Linux** at
<https://henning-winker.r-universe.dev>. You install ready-made binaries with
`install.packages()`: no Rtools, Xcode or compiler needed, even for the
packages with compiled TMB code.

---

## Quick install

Copy and paste this into R:

```r
repos <- c(
  hw   = "https://henning-winker.r-universe.dev",
  flr  = "https://flr.r-universe.dev",
  CRAN = "https://cloud.r-project.org"
)

install.packages(
  c("JABBA3", "FLicc", "cpueTargeting", "FLOSS", "mmsyFM"),
  repos = repos
)
```

All three repositories are needed: your packages come from here, the FLR
dependencies (`FLCore`, `ggplotFL`, `FLBRP`, `FLasher`, `FLife`, `FLRef`, ...)
from the [FLR universe](https://flr.r-universe.dev), and everything else from
CRAN.

To install just one package, replace the vector with its name, e.g.
`install.packages("JABBA3", repos = repos)`.

---

## Packages

### [JABBA3](https://henning-winker.r-universe.dev/JABBA3) &nbsp;·&nbsp; [GitHub](https://github.com/Henning-Winker/JABBA3)
**Bayesian state-space surplus production models in RTMB.**
The next generation of JABBA (Just Another Bayesian Biomass Assessment). Fits
state-space surplus production models in well under a second, with full
posteriors via `tmbstan` (NUTS) when needed. Inputs and outputs follow FLR
conventions for use with `ggplotFL`, `FLRef` and `mse`, and helpers convert
classic JABBA inputs.

### [FLicc](https://henning-winker.r-universe.dev/FLicc) &nbsp;·&nbsp; [GitHub](https://github.com/Henning-Winker/FLicc)
**Length-interval catch-curve models in TMB.**
FLR-friendly implementation of equilibrium multi-gear length-interval
catch-curve models, inspired by `fishblicc`, for data-limited assessment from
length-frequency data.

### [cpueTargeting](https://henning-winker.r-universe.dev/cpueTargeting) &nbsp;·&nbsp; [GitHub](https://github.com/Henning-Winker/cpueTargeting)
**Simulators and tools for CPUE targeting and standardization.**
Multispecies operating models for exploring spatial and vertical targeting
(including longline hook-depth by hooks-between-floats), plus a step-by-step
toolbox for real catch and effort data: formatting, species curves, fleet and
catch-composition exploration, habitat-based subsetting, and targeting
covariates via PCA and clustering of fishing tactics.

### [FLOSS](https://henning-winker.r-universe.dev/FLOSS) &nbsp;·&nbsp; [GitHub](https://github.com/Henning-Winker/FLOSS) &nbsp;·&nbsp; [Website](https://henning-winker.github.io/FLOSS/)
**FL Operating model and Sampling Simulator.**
Builds multi-fleet, multi-species age-structured operating models from
life-history parameters, selectivity, catchability and a target MSY, and
generates the data such fisheries produce: catch, effort, CPUE, survey
indices, length frequencies and biological samples. Designed for trainers who
need realistic example datasets with a known truth.

### [mmsyFM](https://henning-winker.r-universe.dev/mmsyFM) &nbsp;·&nbsp; [GitHub](https://github.com/Henning-Winker/mmsyFM)
**Multispecies MSY fleet model for mixed-fishery harvest strategies.**
Simulates fleet segments allocating fishing days across métiers by expected
profit, on top of surplus-production stocks. Finds multispecies MSY subject to
a safeguard for every stock, and tunes and tests effort- and closure-based
harvest strategies with assessment and implementation error.

---

## For course participants

**Make it permanent.** To avoid typing the repositories every time, add them
to your `.Rprofile` so `install.packages()` and `update.packages()` just work:

```r
usethis::edit_r_profile()   # opens the file; paste the line below, save, restart R
options(repos = c(hw   = "https://henning-winker.r-universe.dev",
                  flr  = "https://flr.r-universe.dev",
                  CRAN = "https://cloud.r-project.org"))
```

**Update before a course.**

```r
update.packages(ask = FALSE, repos = repos)
```

**Troubleshooting**

- *"package 'X' is not available"*: check that all three repositories are in
  `repos`, and that your R version is recent (R ≥ 4.1; binaries are built for
  the current and previous R release).
- *Installation asks to compile from source*: answer **No** to install the
  ready-made binary.
- *Old version still loaded*: restart R (in RStudio: Session → Restart R)
  and try again.
- Check your setup with `packageVersion("JABBA3")` and `sessionInfo()`.

---

## Acknowledgements

FLR packages are maintained by the [FLR project](https://flr-project.org) and
hosted at <https://flr.r-universe.dev>. Infrastructure by
[R-universe](https://r-universe.dev) (rOpenSci).

## For maintainers

Packages are listed in [`packages.json`](packages.json). R-universe rebuilds
on every push to a listed repository, but users only receive an update through
`update.packages()` when the `Version:` field in `DESCRIPTION` is bumped.
Build logs: <https://github.com/r-universe/henning-winker/actions>.
