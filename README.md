# ECTI-P vs ΛCDM  
### Late-time, background-only phenomenological extension  
**FAIR k = 5 comparison using SN Ia, BAO (DESI 2024), RSD, KiDS, Planck compressed priors, and optional CMB lensing**

---
### TL;DR:

Δχ² = −11.31 (FAIR k=5, same parameters as ΛCDM)

5/6 late-time probes improved; BAO penalty negligible (+0.07)

Late-time H(z) only; no recombination / no perturbations / no TT/TE/EE

Robust across 3 independent runs; insensitive to ±10% variations in fixed parameters

**Posterior comparison (ΛCDM vs ECTI-P, FAIR k = 5)**
<p align="center">
<img width="2124" height="2124" alt="corner_overlay_LCDM_vs_ECTI_k5" src="https://github.com/user-attachments/assets/6d777861-811f-4cd4-9bb4-6593d7702ce9" />
</p>

---

## Key empirical result

Across six independent late-time cosmological probes, ECTI-P yields a net improvement
in total χ² relative to ΛCDM, with 5/6 probes improved and a negligible BAO penalty (+0.07), under a strictly FAIR comparison with the same number of free parameters (k = 5).

### χ² improvement by dataset (ECTI − ΛCDM)

| Dataset | Δχ² |
|------|------|
| Pantheon+ SN Ia | −9.84 |
| Planck CMB (compressed) | −1.03 |
| CMB lensing | −0.26 |
| RSD (fσ₈) | −0.16 |
| KiDS (S₈ prior) | −0.09 |
| DESI 2024 BAO | +0.07 |
| **Total** | **−11.31** |
<p align="center">
<img width="1548" height="864" alt="delta_chi2_per_probe_k5" src="https://github.com/user-attachments/assets/5d185e3b-c755-457f-9c28-3920b1fe362b" />
</p>
Because both models have the same number of sampled parameters,  
**ΔAIC = ΔBIC = Δχ²**.
<p align="center">
<img width="1152" height="864" alt="stability_deltas_k5" src="https://github.com/user-attachments/assets/8d6d920e-9ff6-48c0-92d7-c3efee015bae" />
</p>
---

## Scientific scope (strict)

ECTI-P is a **purely phenomenological, late-time, background-only extension** of ΛCDM.

The model modifies **only the expansion history H(z)** at low redshift.

Explicitly, ECTI-P does **not** modify:
- recombination physics
- perturbation equations
- linear or non-linear growth sector
- neutrinos or radiation content
- sound horizon physics rₛ
- CMB primary anisotropies

Accordingly:
- no Boltzmann solvers (CLASS or CAMB)
- no TT / TE / EE likelihoods
- no CLik

Planck information is included **exclusively through compressed distance priors** and, optionally, through the Planck 2018 lensing-only constraint.

## Effective background modification

ECTI-P modifies the late-time expansion history through an effective deformation
of the ΛCDM background evolution.

The expansion rate is written as:

    E(z)^2 = E_LCDM(z)^2 × F(z; beta, z_t)

with:

    F(z; beta, z_t) → 1   for   z >> z_t

The parameters (beta, z_t) control the amplitude and redshift location of a smooth
late-time transition in H(z).

In the limit beta → 0, the model continuously reduces to standard ΛCDM.
The explicit functional form of F(z; beta, z_t) is defined in the notebook
and implemented directly in the code.
---
## Late-time deformation of the expansion history (visualization)

the following figures are provided for physical interpretation and visualization.
They are derived from the reference MAP parameters and are not part of the automatic reproduction pipeline.

<p align="center">
<img width="1600" height="1000" alt="Hz_LCDM_vs_ECTI_from_LASTH5MAP_k5" src="https://github.com/user-attachments/assets/332c7ac0-ef7b-4bf0-af33-f23830ccbd3c" />
</p>

<p align="center">
<img width="1600" height="1000" alt="Hz_ratio_ECTI_over_LCDM_from_LASTH5MAP_k5" src="https://github.com/user-attachments/assets/ef311fc2-c3c6-4b61-a535-790da3be817b" />
</p>

## Model comparison (FAIR k = 5)

Both models are sampled with the identical parameter vector:

    theta = (H0, Omega_m0, sigma8, M, omega_b)
    
where:
- H0        : Hubble constant
- Omega_m0 : present-day matter density
- sigma8   : amplitude of matter fluctuations
- M        : SN absolute magnitude
- omega_b  : physical baryon density
  
- ΛCDM uses the standard background evolution.
- ECTI-P uses the same vector, with its internal late-time parameters (β, zₜ) fixed and not sampled.

No additional degrees of freedom are introduced in ECTI-P.

---

## Datasets

### Supernovae
Pantheon+ (2022) compilation with SH0ES calibration.

### Baryon Acoustic Oscillations
DESI 2024 BAO measurements implemented as a Gaussian likelihood.

### Redshift-Space Distortions
Curated compilation of published fσ₈(z) measurements.  
The data file is included directly in this repository, together with an explicit row-by-row provenance document.

The RSD likelihood assumes standard GR linear growth, computed by solving the linear growth equation self-consistently using the model-specific background expansion H(z). No modified gravity or additional growth parameters are introduced.

### Weak Lensing
KiDS S₈ compressed Gaussian prior (not the full cosmic shear likelihood).

### Cosmic Microwave Background (compressed)
Planck 2018 compressed distance priors (R, ℓ_A, ω_b) with full covariance.

### CMB Lensing (optional)
Planck 2018 lensing-only derived one-dimensional constraint, enabled via a notebook flag and consistently included in χ² and BIC.

---

## Robustness and convergence

The results are stable across **three independent paired MCMC runs**.

| Run | Δχ² |
|----|----|
| 1 | −11.31 |
| 2 | −11.30 |
| 3 | −11.31 |

All chains satisfy:
- R̂ < 1.02
- high effective sample size
- no stuck walkers or pathological behavior

## Sensitivity Analysis (Fixed Parameters)

The ECTI-P specific parameters (`β`, `z_t`) are treated as fixed characteristics of the effective late-time modification for the MCMC sampling ($k=5$).

To verify that the observed $\chi^2$ improvement is not the result of hyper-fine-tuning, we performed a grid search in the $(\beta, z_t)$ plane around the reference values (±10%).

<p align="center">
  <img width="1600" height="960" alt="grid_beta_zt_FIXEDMAP_LASTRUN_k5" src="https://github.com/user-attachments/assets/36938771-73f7-4bb9-b358-9e20083e0bb2" />
</p>
(The sensitivity analysis and grid search shown below were performed in preliminary campaigns and are provided here to document the robustness of the fixed parameter choice. They are not part of the final MCMC notebook pipeline.)

**Result :** The $\chi^2$ landscape is shallow around the reference solution.  
Even for ±10% deviations in the fixed parameters, ECTI-P retains a substantial advantage over ΛCDM, with $\Delta\chi^2 \approx -9$ to $-11$.

This demonstrates that the statistical gain is driven by the late-time structural modification of $H(z)$ around $z \sim 0.1$, rather than by precise parameter tuning.
---

## Visual diagnostics

- Supernova distance modulus residuals
  <p align="center">
  <img width="1368" height="576" alt="residuals_SN_raw_k5" src="https://github.com/user-attachments/assets/46c76e28-23a6-4bad-a42d-a067080fa50f" />
  </p>
  Supernova distance modulus residuals at the reference MAP parameters.
ECTI-P improves the global fit without introducing redshift-dependent systematics or residual structure.

- BAO residuals
<p align="center">
<img width="1152" height="864" alt="pulls_BAO_k5_LAST_run003" src="https://github.com/user-attachments/assets/a648baea-f5b2-4286-9d4b-8bea9b689417" />
</p>
BAO pulls at the reference MAP parameters.
ECTI-P preserves the standard ruler constraints and remains statistically neutral with respect to ΛCDM.

- RSD residuals
<p align="center">
  <img width="1368" height="576" alt="pulls_RSD_k5" src="https://github.com/user-attachments/assets/b1f07afb-469d-4075-90dc-be292db39820" />
</p>
RSD pulls at the reference MAP parameters.

Both ΛCDM and ECTI-P remain consistent with fσ₈ measurements, indicating that the late-time background modification does not introduce growth-sector tensions.

All figures are generated automatically by the notebook.

---

Repository structure:

- ECTI_P_vs_LCDM_full_likelihood_Planck_3D_+*.ipynb  
  Main analysis notebook (self-contained, generates all outputs)

- data/rsd/  
  RSD tables and provenance

- README.md  
  Project overview and scientific context

- RUNNING.md  
  Reproducibility and execution instructions

- CITATION.cff  
  Citation metadata

- LICENSE  
  MIT license

  All figures, tables, and diagnostics are generated automatically by the notebook and are not stored in the repository.
---

## How to run

For full reproduction instructions, see RUNNING.md

## Next step
The definitive test of this phenomenological extension requires confrontation with the full Planck TT/TE/EE likelihood, which necessitates a Boltzmann treatment and HPC environment not currently available to the autor.

## Contact

For questions regarding the methodology, reproducibility, or scope of the results,  
feel free to contact the author via GitHub or email.

## Citation
If you use this work, please cite:
Pantheon+ (Brout et al. 2022)
SH0ES (Riess et al. 2022)
DESI 2024 BAO
Planck 2018 results (Planck Legacy Archive)
The primary RSD survey papers listed in the RSD provenance file
A CITATION.cff file is provided.

## License
Released under the repository license.
All data values originate from published literature and must be cited accordingly.
