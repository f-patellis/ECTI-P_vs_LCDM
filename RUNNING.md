## How to run

### Requirements

The analysis requires a standard scientific Python environment:

Python ≥ 3.9

numpy

scipy

pandas

matplotlib

tqdm

emcee (v3)

corner (optional, for corner plots)


All dependencies are listed in requirements.txt.


---

### Installation

Clone the repository and install dependencies:

git clone https://github.com/f-patellis/ECTI-P_vs_LCDM.git
cd ECTI-P_vs_LCDM
pip install -r requirements.txt


---

### Quick sanity check (no MCMC)

This mode allows full verification of the pipeline without running any sampling.

It executes:

data loading

background models

likelihoods

χ² recomputation at reference MAP parameters

all post-processing figures and tables


Steps:

1. Open the main notebook:



jupyter notebook

2. In Cell 1.1.2, set:



RUN_MCMC = False

3. Run the notebook top-to-bottom.



All post-MCMC cells are skip-safe and will execute using stored MAP values.

This mode is intended for:

referees

code inspection

fast consistency checks



---

### Full reproduction (MCMC)

This mode reproduces the full paired MCMC analysis.

Steps:

1. In Cell 1.1.2, set:



RUN_MCMC = True

2. Execute the notebook top-to-bottom.



MCMC sampling is performed using emcee v3 with:

identical parameter vectors for ΛCDM and ECTI-P

an HDF5 backend (resume-safe)

paired runs for FAIR comparison


Final outputs include:

χ² values

Δχ² / ΔAIC / ΔBIC

figures

tables

convergence diagnostics



---

### Expected runtime

Runtime depends on hardware and number of steps:

Sanity-check mode: a few minutes

Full MCMC reproduction: several hours per paired run


The reference results shown in the README were obtained using 10,000-step paired MCMC runs.


---

 ### Outputs

All outputs are generated automatically:

figures/ : plots (corner, residuals, χ² breakdown, stability)

tables/  : numerical summaries

meta/    : run metadata and configuration


The repository is committed without outputs; no pre-generated files are required.


---

### Reproducibility notes

The notebook is committed without execution counts or outputs.

All χ² values are recomputed directly from the likelihood functions.

Fixed ECTI-P parameters (β, z_t) are documented and validated via sensitivity analysis.

The RSD dataset includes explicit row-by-row provenance.
