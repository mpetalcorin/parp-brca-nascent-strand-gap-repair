# Datasheet

## Dataset name

Synthetic simulation outputs and assay-like observables from the PARP-BRCA nascent strand gap repair extended proof-of-concept model

## Motivation

This project does not rely on a conventional empirical dataset as its primary analytical substrate. Instead, it generates synthetic time-course outputs from a reduced mechanistic simulation of PARP inhibitor-induced daughter-strand gap formation and BRCA1-BRCA2-RAD51-dependent rescue.

The aim of these data products is to support mechanistic exploration, visualization, perturbation analysis, stochastic simulation, compartmental analysis, and synthetic fitting workflows.

## Data composition

The generated outputs may include trajectories for:

- **L(t)**, ligatable nascent lagging-strand discontinuities
- **T(t)**, trapped PARP-DNA complexes
- **G(t)**, persistent daughter-strand gaps
- **R(t)**, RAD51 repair intermediates
- **M(t)**, matured nascent DNA
- **D(t)**, secondary double-strand breaks
- **S(t)**, predicted survival
- **Ψ(t)**, repair vulnerability index

Compartmental extensions may also include:

- **Lₚ(t), Tₚ(t), Gₚ(t), Rₚ(t), Mₚ(t), Dₚ(t)**, fork-proximal states
- **L_d(t), T_d(t), G_d(t), R_d(t), M_d(t), D_d(t)**, fork-distal states
- total proximal plus distal summaries

Synthetic assay-emulation outputs may include:

- comet tail moment-like values
- DNA combing IdU tract length-like values
- RAD51 foci-like values

## Data generation process

Outputs are produced by numerically integrating a reduced system of ordinary differential equations over time. Depending on the notebook section, the workflow may also include:

- deterministic parameter sweeps
- local sensitivity perturbations
- stochastic lesion inflow
- compartment transfer between proximal and distal states
- synthetic data generation with observation noise
- random-search parameter fitting against synthetic observables

## Source data

The outputs are simulation-derived. They are not direct experimental measurements.

The design of the model and the directionality of some synthetic observables are conceptually informed by peer-reviewed PubMed-indexed literature on PARP trapping, replication gaps, Okazaki fragment processing, and BRCA-dependent rescue, but the generated values themselves are synthetic.

## Recommended use

Appropriate uses include:

- visualizing mechanistic state trajectories
- comparing modeled stress states across perturbations
- teaching and demonstration
- testing code pipelines for model fitting
- exploring candidate hypotheses before experimental work
- designing future calibration workflows for real datasets

## Non-recommended use

These simulation-derived outputs should not be used for:

- clinical inference
- estimating absolute lesion burden in real cells
- benchmarking treatment efficacy in patients
- training deployable predictive models without recalibration
- treating the synthetic observables as experimentally measured truth

## Biases and limitations

Key limitations include:

- dependence on user-specified parameter values
- simplified mechanistic structure
- synthetic assay outputs that are only qualitatively benchmarked
- no direct mapping to measured experimental units by default
- limited representation of biochemical complexity
- incomplete representation of heterogeneity unless stochastic simulations are used

These outputs should therefore be interpreted as model-dependent abstractions.

## Preprocessing and formatting

Data may appear in the notebook as:

- time-course arrays
- pandas DataFrames
- sweep summary tables
- fitted parameter tables
- line plots, heatmaps, and bar plots

Unless otherwise specified, values are expressed in arbitrary or normalized units.

## Splits and subsets

The dataset may be subdivided into:

- baseline deterministic simulations
- parameter sweep outputs
- local sensitivity outputs
- stochastic simulation runs
- compartmental simulation outputs
- synthetic assay-target datasets
- fitted assay-prediction datasets

## Distribution

The synthetic outputs are distributed inside the notebook environment and in any exported tables or figures derived from the notebook.

## Maintenance and future development

Future versions of this datasheet may include:

- explicit units for calibrated models
- links between synthetic observables and real assay scales
- uncertainty estimates for fitted parameters
- standardized benchmark datasets
- structured export formats for external analysis pipelines

## Citation
**Petalcorin, M.I.R.** (2026). A Reduced Dynamical Systems Model of PARP Inhibitor-Induced Nascent Strand Gap Formation and BRCA1-BRCA2-RAD51-Dependent Repair During DNA Replication. https://github.com/mpetalcorin/parp-brca-nascent-strand-gap-repair
