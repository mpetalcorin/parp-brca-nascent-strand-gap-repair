# parp-brca-nascent-strand-gap-repair
A proof-of-concept dynamical systems model of PARP inhibitor-induced nascent strand gap formation and BRCA1-BRCA2-RAD51-dependent repair during DNA replication.
<img width="1146" height="656" alt="Screenshot 2026-04-04 at 19 57 12" src="https://github.com/user-attachments/assets/2b2a1fee-dc17-41f0-b44b-864b7f81e7ce" />
# PARP-BRCA Nascent Strand Gap Repair Proof-of-Concept

## Overview

This repository contains a computational proof-of-concept framework for modeling PARP inhibitor-induced nascent strand gap formation and BRCA1-BRCA2-RAD51-dependent repair during DNA replication.

The project implements a reduced dynamical systems model together with several extensions that broaden its biological and computational scope. These include parameter sweeps, local sensitivity analysis, stochastic lesion formation, explicit fork-proximal and fork-distal compartments, and fitting to synthetic assay-like datasets representing comet assay, DNA combing, and RAD51 foci measurements.

This repository is intended for conceptual, educational, and hypothesis-generating use. It is not a parameter-fitted experimental model and should not be interpreted as a clinically validated predictor of PARP inhibitor response.

## Scientific rationale

PARP inhibitors can trap PARP enzymes on endogenous replication-associated DNA intermediates, especially unresolved lagging-strand discontinuities related to incomplete Okazaki fragment maturation. In repair-proficient cells, some of the resulting daughter-strand gaps can be managed through BRCA1-BRCA2-RAD51-dependent rescue. In BRCA-deficient or ligation-defective settings, this rescue capacity is reduced, promoting persistent gap burden, downstream double-strand break formation, and reduced survival.

The model is designed to encode this mechanistic logic in an interpretable mathematical form.

# PARP inhibitor-induced nascent strand gap repair: proof-of-concept notebook

This notebook implements a reduced dynamical systems model for **PARP inhibitor-induced nascent strand gap formation** and **BRCA1-BRCA2-RAD51-dependent repair**.

## Biological variables

- **L(t)**: ligatable nascent lagging-strand discontinuities  
- **T(t)**: trapped PARP-DNA complexes  
- **G(t)**: persistent daughter-strand gaps  
- **R(t)**: RAD51 repair intermediates  
- **M(t)**: matured nascent DNA  
- **D(t)**: secondary double-strand breaks  
- **S(t)**: predicted survival  

## Reduced model

$$
\frac{dL}{dt} = \alpha - \eta_{LIG1} k_{lig} L - k_p L
$$

$$
\frac{dT}{dt} = k_{trap}^{max} I_{PARPi} \tau k_p L - \delta_T T
$$

$$
\frac{dG}{dt} = \beta_1 L + \beta_2 T - \gamma \eta_{BRCA1}\eta_{BRCA2} G - \kappa G - \delta_G G
$$

$$
\frac{dR}{dt} = \gamma \eta_{BRCA1}\eta_{BRCA2} G - \rho R - \delta_R R
$$

$$
\frac{dM}{dt} = \eta_{LIG1} k_{lig} L + \rho R
$$

$$
\frac{dD}{dt} = \kappa G - \delta_D D
$$

and the survival function is

$$
S(t) = \exp\left[-\omega_G \int_0^t G(u)\,du - \omega_D \int_0^t D(u)\,du\right]
$$

This is a **conceptual model**, not a parameter-fitted experimental model.

The extended notebook adds the following modules:

- parameter sweeps over **I_PARPi**, **η_BRCA2**, and **η_LIG1**
- local sensitivity analysis for **β₂**, **γ**, and **κ**
- stochastic lesion formation in place of deterministic inflow
- explicit fork-proximal and fork-distal compartments
- fitting to synthetic assay-like datasets for comet assay, DNA combing, and RAD51 foci-like observables

## Repository contents

- `parp_brca_gap_repair_proof_of_concept_extended.ipynb`, a notebook implementing the model and analyses
- `parp_brca_final_manuscript_intext.docx`, formatted manuscript with table and figures embedded in-text
- `README.md`, repository overview and usage guide
- `modelcard.md`, model card describing intended use, assumptions, outputs, and limitations
- `datasheet.md`, datasheet describing the simulation-derived data products and assay-like synthetic outputs

## Baseline modeled conditions

The notebook includes baseline simulations for:

- untreated wild type
- wild type plus PARP inhibitor
- BRCA2-deficient plus PARP inhibitor
- LIG1-depleted plus PARP inhibitor
- combined LIG1 depletion and BRCA2 deficiency plus PARP inhibitor
- wild type plus a veliparib-like trapping condition
- wild type plus a talazoparib-like trapping condition

## How to use

1. Open the extended notebook.
2. Run the import and simulator cells.
3. Execute the baseline condition panel.
4. Review the time-course plots for lesion burden, repair intermediates, and survival.
5. Run the parameter sweeps and sensitivity analysis sections.
6. Run the stochastic lesion generation section to observe heterogeneous trajectories.
7. Run the compartmental section to compare fork-proximal and fork-distal dynamics.
8.	Run the synthetic fitting section to test fitting of β₂, γ, and κ to assay-like observables.

## Interpretation

The model is designed to support qualitative interpretation of how PARP inhibitor intensity, lagging-strand ligation capacity, and BRCA-dependent rescue determine system behavior.

Key expected themes include:

- daughter-strand gap burden rises with stronger PARP trapping
- BRCA2 loss reduces RAD51-dependent rescue and increases persistent lesion burden
- LIG1 reduction increases the upstream pool of unresolved lagging-strand intermediates
- stochastic lesion inflow broadens phenotype variability
- proximal and distal compartments can diverge over time even when they are mechanistically linked

## Limitations

This framework is intentionally simplified and does not explicitly represent many mechanistic details, including:

- full leading- versus lagging-strand chemistry
- detailed fork reversal, repriming, or nuclease processing
- homologous pairing and strand invasion substeps
- chromatin context and cell-to-cell lineage structure
- direct calibration to experimental assay units
- clinical prediction of treatment outcome

## Suggested next steps

Potential future improvements include:

- calibration against real comet assay, DNA combing, or RAD51 foci datasets
- incorporation of explicit fork reversal and repriming modules
- stochastic population simulations with cell-to-cell heterogeneity
- Bayesian parameter inference and uncertainty propagation
- benchmarking against experimentally measured PARP inhibitor trapping differences

## Intended audience

This repository is most suitable for:

- researchers interested in PARP biology or replication stress
- students learning mechanistic systems modeling
- computational biologists exploring reduced DNA repair models
- users developing data-integrated frameworks for hypothesis testing

## Citation
**Petalcorin, M.I.R.** (2026). A Reduced Dynamical Systems Model of PARP Inhibitor-Induced Nascent Strand Gap Formation and BRCA1-BRCA2-RAD51-Dependent Repair During DNA Replication. chemRxiv. https://doi.org/10.26434/chemrxiv.15001697/v1

## License and use

Use this repository for scientific exploration, education, model development, and hypothesis generation. Quantitative biological claims should be made cautiously and validated experimentally.
