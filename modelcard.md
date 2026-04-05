# Model Card

## Model name

PARP-BRCA Nascent Strand Gap Repair Proof-of-Concept Model

## Model type

Reduced mechanistic dynamical systems model implemented as a deterministic ordinary differential equation proof of concept.

## Summary

This model represents a simplified mechanistic framework for PARP inhibitor-induced nascent strand gap formation and BRCA1-BRCA2-RAD51-dependent repair during DNA replication. It is designed to capture qualitative system behavior rather than to provide calibrated quantitative biological predictions.

The model tracks ligatable lagging-strand discontinuities, trapped PARP-DNA complexes, persistent daughter-strand gaps, RAD51-mediated repair intermediates, mature nascent DNA restoration, secondary double-strand break formation, and predicted survival.

## Intended use

This model is intended for:

- conceptual exploration of replication-associated DNA repair dynamics
- teaching and demonstration of mechanistic systems biology ideas
- hypothesis generation for PARP inhibitor and BRCA pathway biology
- building a starting framework for future model refinement

## Out-of-scope use

This model is not intended for:

- clinical decision making
- prediction of patient drug response
- quantitative estimation of viability in real cell lines without calibration
- regulatory, diagnostic, or therapeutic use
- replacement of experimental validation

## Inputs

The model takes pathway activity and condition parameters such as:

- LIG1 activity, **η_LIG1**
- BRCA1 activity, **η_BRCA1**
- BRCA2 activity, **η_BRCA2**
- PARP inhibitor intensity, **I_PARPi**
- inhibitor trapping strength, **τ**
- kinetic constants controlling discontinuity formation, trapping, repair, gap conversion, and survival weighting

## Outputs

The model returns time courses and summary metrics for:

- **L(t)**, ligatable nascent discontinuities
- **T(t)**, trapped PARP-DNA complexes
- **G(t)**, daughter-strand gaps
- **R(t)**, RAD51 intermediates
- **M(t)**, matured nascent DNA
- **D(t)**, secondary DSBs
- **S(t)**, predicted survival
- AUC for gap burden and DSB burden
- final vulnerability index **Ψ**

## Biological assumptions

The model assumes:

1. nascent lagging-strand discontinuities are produced continuously during replication
2. canonical LIG1-dependent maturation reduces the discontinuity burden
3. PARP inhibitors increase the persistence of PARP-DNA complexes
4. persistent ligation intermediates and trapped complexes contribute to daughter-strand gap formation
5. BRCA1 and BRCA2 promote RAD51-dependent rescue of these gaps
6. unresolved gaps can contribute to secondary DSB formation and reduced survival

## Limitations

Major limitations include:

- no direct parameter fitting to experimental datasets
- no explicit separation of leading and lagging strands beyond the conceptual interpretation
- no explicit modeling of fork reversal, PRIMPOL, or lesion-specific chemistry
- deterministic structure without cell-to-cell variability
- simplified survival function based on integrated burden rather than detailed death pathway modeling

## Performance characteristics

This model should be evaluated qualitatively, not by predictive accuracy. Relevant assessment criteria include:

- internal consistency with the mechanistic hypothesis
- biologically sensible ordering of condition severity
- transparency and interpretability
- ease of extension

## Expected qualitative phenotype ranking

Under the default proof-of-concept parameterization, the expected severity order is:

WT < WT + PARPi < BRCA2 deficiency + PARPi < LIG1 depletion + PARPi < LIG1 depletion plus BRCA2 deficiency + PARPi

This ranking is qualitative and parameter-dependent.

## Risks and cautions

Potential misuse risks include:

- overinterpreting simulated curves as real measured biology
- assuming parameter values are experimentally validated
- treating simplified survival outputs as directly translatable to cell viability assays

Users should clearly state that the model is exploratory and conceptual.

## Maintenance

This model is intended as a foundation for further refinement. Future versions may incorporate calibrated parameters, additional repair pathway states, stochastic dynamics, or experimental data fitting.

## Citation
**Petalcorin, M.I.R.** (2026). A Reduced Dynamical Systems Model of PARP Inhibitor-Induced Nascent Strand Gap Formation and BRCA1-BRCA2-RAD51-Dependent Repair During DNA Replication. https://github.com/mpetalcorin/parp-brca-nascent-strand-gap-repair
