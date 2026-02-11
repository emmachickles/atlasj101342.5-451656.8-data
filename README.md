# Data Release for ATLAS J101342.5−451656.8 (ATLAS J1013−4516)

This repository contains the photometric and spectroscopic data products used in:

**Chickles et al. (2026)**,
*An eclipsing 8.56-minute orbital period mass-transferring AM CVn binary*,
The Astrophysical Journal (in press).

The datasets provided here are the processed, science-ready products used in the analysis and figures of the paper. Raw survey images and instrument pipeline intermediates are not redistributed.

---

## Contents

This release contains the following files:

```
atlas_photometry.csv
ultracam_photometry.csv
lightspeed_photometry.csv
llamas_spectra.fits
```

Each file is described below.

---

# 1. ATLAS Forced Photometry

### `atlas_photometry.csv`

Time-series forced photometry from the Asteroid Terrestrial-impact Last Alert System (ATLAS).

## Columns

* **mjd**
  Modified Julian Date (UTC) at the start of the 30 s exposure.
  These timestamps are not barycentric corrected.

* **flux_uJy**
  Calibrated flux in microJanskys.

* **flux_err_uJy**
  1σ uncertainty in microJanskys.

* **filter**
  ATLAS filter:

  * `c` = cyan
  * `o` = orange

* **mag_5sigma_limit**
  Five-sigma limiting magnitude for the exposure.

## Notes

* Fluxes are calibrated on the AB system.
* Flux values may be negative from choice of reference frame.
* Only the columns required to reproduce the timing analysis (Section 3.4 of Chickles et al. 2026) are included.
* The full ATLAS forced-photometry output includes additional diagnostic quantities (PSF parameters, fit statistics, background terms), which are not necessary for reproducing the results and are therefore omitted.
* ATLAS filter definitions and throughput curves are described in Tonry et al. (2018), PASP, 130, 064505.

---

# 2. ULTRACAM High-Speed Photometry

### `ultracam_photometry.csv`

Combined multi-night ULTRACAM photometry.

Observations were obtained using ULTRACAM on the ESO New Technology Telescope (NTT).

## Columns

* **bjd_tdb**
  Barycentric Julian Date in TDB.

* **flux_rel**
  Normalized (relative) flux.

* **flux_rel_err**
  1σ uncertainty in relative flux.

* **filter**
  ULTRACAM filter: `u`, `g`, `r`, or `i` (as available).

* **exptime_s**
  Exposure time in seconds.

## Notes

* Fluxes are provided in relative (normalized) units.
* Absolute flux calibration was not required for the eclipse modeling and was not uniformly performed across all nights; therefore only relative photometry is released.
* Flux normalization was performed per night and filter using differential photometry against field comparison stars.
* These data were used to measure eclipse depths and refine orbital timing (Sections 3.3 and 3.4 of Chickles et al. 2026).

---

# 3. proto-Lightspeed Photometry

### `lightspeed_photometry.csv`

High-speed photometry obtained with the proto-Lightspeed imager on the Magellan Clay telescope.

## Columns

* **bjd_tdb**
  Barycentric Julian Date in TDB.

* **flux_rel**
  Normalized (relative) flux.

* **flux_rel_err**
  1σ uncertainty in relative flux.

* **filter**
  `g`

* **exptime_s**
  Exposure time in seconds.

## Notes

* Fluxes are relative (normalized).
* These data extend the long-baseline timing analysis.
* Instrument description: Layden et al. (2026, submitted to PASP), "proto-Lightspeed: a high-speed, ultra-low read noise imager on the Magellan Clay Telescope"

---

# 4. LLAMAS Spectroscopy

### `llamas_spectra.fits`

Phase-resolved spectra obtained with LLAMAS on the Magellan Baade telescope.

## Observations

* Date: 2025 December 14
* 28 exposures × 30 s
* Wavelength coverage: approximately 3400–10,000 Å

## Reduction

Data were reduced using the **llamas-pyjamas** reduction pipeline (Hughes et al. 2026, in preparation), followed by additional throughput normalization and manual inspection as described in Section 2.3 of Chickles et al. (2026).

Only the central fiber corresponding to the target position is included in this release. The full IFU data cube (≈2400 fibers per exposure) is not redistributed.

## FITS Structure

The FITS file contains stacked 2D arrays (n_exposures × n_wavelength):

* `WAVELENGTH_BLUE`, `FLUX_BLUE`, `MJD_OBS_BLUE`
* `WAVELENGTH_GREEN`, `FLUX_GREEN`, `MJD_OBS_GREEN`
* `WAVELENGTH_RED`, `FLUX_RED`, `MJD_OBS_RED`

Flux units are as provided by the reduction pipeline llamas-pyjamas (https://github.com/mit-kavli-institute/llamas-pyjamas).

These spectra were used for emission-line identification and phase-resolved analysis (Section 3.1 of Chickles et al. 2026).

---

# Reproducibility

The data provided here are sufficient to reproduce:

* The long-baseline orbital timing and period derivative measurement.
* Eclipse depth measurements and wavelength dependence.
* Spectral line identification and phase-resolved behavior.

The analysis code used in the paper is maintained separately and may be released in a future repository.

---

# Citation

If using these data, please cite:

Chickles et al. (2026), *An eclipsing 8.56-minute orbital period mass-transferring AM CVn binary*, ApJ.

Please also cite the ATLAS survey (Tonry et al. 2018) and relevant instrument papers as appropriate.

