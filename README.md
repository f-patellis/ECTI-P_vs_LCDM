# ECTI-P vs ΛCDM — Late-time, background-only extension
FAIR k=5 comparison with Planck compressed 3D (and optional lensing)


ECTI-P is a purely phenomenological, late-time background-only extension, not derived from a specific fundamental theory.


This repository contains a referee-grade Jupyter notebook implementing a fair comparison between the standard ΛCDM cosmological model and ECTI-P, a phenomenological late-time extension of the background expansion.
The analysis is designed for full reproducibility, academic scrutiny, and direct inspection by referees.

# Scientific scope (strict)
ECTI-P modifies the cosmological model only at late times and only at the background level.
The model acts exclusively through the expansion history H(z) at low redshift.
No early-time physics is modified:
– no recombination changes
– no perturbation equations
– no Boltzmann solvers (CLASS or CAMB)
– no CMB TT / TE / EE likelihoods
– no CLik
All early-universe physics is therefore kept identical to ΛCDM.
Planck information is included exclusively through compressed distance priors.

# Model comparison (FAIR k = 5)
Both ΛCDM and ECTI-P are sampled with the same parameter vector:
(H₀, Ωₘ₀, σ₈, M, ω_b)
ΛCDM uses the standard background evolution.
ECTI-P uses the same parameter vector, with its internal late-time parameters (β, zₜ) fixed and not sampled.
Because both models have the same number of free parameters, information criteria reduce to:
ΔAIC = ΔBIC = Δχ².

# Datasets
## Supernovae
Pantheon+ (2022) supernova compilation with SH0ES calibration.
## Baryon Acoustic Oscillations
DESI 2024 BAO measurements implemented as a Gaussian likelihood.
## Redshift-Space Distortions
A curated compilation of fσ₈(z) measurements extracted from the literature.
The data file is included directly in the repository, together with an explicit row-by-row provenance document.
The RSD likelihood uses the standard GR linear growth equation driven by the background expansion H(z).
No additional growth parameters are introduced.
## Weak Lensing
KiDS S₈ compressed Gaussian prior.
This is not the full cosmic shear two-point likelihood.
## Cosmic Microwave Background (compressed)
Planck 2018 compressed distance priors (R, ℓ_A, ω_b) with full covariance.
## CMB Lensing (optional)
Planck 2018 lensing-only derived one-dimensional constraint, enabled via a notebook flag and consistently included in χ² and BIC when used.

# Repository structure
The repository contains:
– the main analysis notebook
– a data directory containing the RSD table and its provenance
– directories for figures, tables, and metadata generated at runtime
All runtime outputs are generated automatically and are not required to execute the notebook.

# Requirements
The notebook requires a standard scientific Python environment (Python 3.9 or later).
Required packages:
– numpy
– scipy
– pandas
– matplotlib
– tqdm
– emcee (version 3)
– corner (optional, only for corner plots)
Runtime warnings related to floating-point underflows are intentionally suppressed in the notebook for readability.
This does not affect the numerical results.

# How to run
Documentation and sanity-check mode
Set the flag RUN_MCMC = False in the notebook.(cell 1.1.2)
The notebook can then be executed top-to-bottom without running any sampling.
All post-MCMC cells are skip-safe.
Full reproduction mode
Set RUN_MCMC = True.
MCMC chains are generated using emcee with an HDF5 backend (resume-safe).
Final χ² values, AIC/BIC, tables, and figures are produced automatically.
The notebook assumes it is run from the root of the repository; input data (including RSD) are loaded via relative paths (e.g. data/rsd/rsd.csv)

# Reproducibility notes
The notebook is committed without outputs and without execution counts.
χ² values are always recomputed from the likelihood functions at the reported MAP parameters.
The RSD likelihood uses a curated literature compilation with explicit provenance.

# Citation
If you use this work, please cite:
– Pantheon+ (Brout et al. 2022)
– SH0ES (Riess et al. 2022)
– DESI 2024 BAO
– Planck 2018 (Planck Collaboration 2018 results Planck Legacy Archive)
– The primary RSD survey papers listed in the RSD provenance file
A CITATION.cff file may be added for automated citation support.

# License
The code is released under the repository license.
All data values are extracted from published literature and must be cited accordingly.

