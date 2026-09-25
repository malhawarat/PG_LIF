# PG-LIF: A Plateau-Gated Two-Compartment Spiking Neuron for Multi-Timescale Gradient Propagation and Local, Hardware-Compatible Learning

Code, notebooks, and figures accompanying the manuscript submitted to *Neurocomputing* (Elsevier).

## Overview

PG-LIF is a reduced two-compartment spiking neuron in which an event-triggered,
all-or-none dendritic plateau state `p` is repurposed for two roles at once:

1. a slow, reset-immune pathway for gradient propagation across long timescales
   (the somatic drive term `kappa * p * (1 - alpha_m)`), and
2. a neuron-local, three-factor instructive gate for synaptic plasticity, inspired
   by behavioral timescale synaptic plasticity (BTSP).

The repository contains the notebooks used to run every experiment reported in
the paper and the exact figures included in the manuscript. The manuscript
source itself is not part of this repository.

## Repository structure

```
notebooks/               Experiment notebooks (model + training/eval code), one per experiment
notebooks/executed_runs/ Notebooks re-executed with outputs retained, used as evidence
                          for specific reported numbers/figures (see table below)
figures/                 Final manuscript figures (fig1-fig13), 300 DPI
```

## Notebook -> experiment / manuscript section map

| Notebook | Section(s) | Purpose |
|---|---|---|
| `PG_LIF_P0_single_neuron_validation.ipynb` | Sec. 4-5 | Single-neuron dynamics validation (plateau bound, f-I curve, firing regimes) |
| `PG_LIF_P1_SHD_benchmark.ipynb`, `PG_LIF_P1_SHD_benchmark_v2.ipynb` | Sec. 6, Table 1 | Regime A: offline BPTT on Spiking Heidelberg Digits (SHD), family comparison (PG-LIF, ALIF, TC-LIF, DH-LIF, plateau-ablated control) |
| `PG_LIF_P1_paper_mode.ipynb` | Sec. 6, Table 1, Fig. 1 | Consolidated paper-mode run producing the headline SHD results and Figure 1 |
| `PG_LIF_P1_consolidation.ipynb` | Sec. 6 | Cross-seed consolidation / statistics for Regime A results |
| `PG_LIF_P1_diagnostics.ipynb`, `PG_LIF_P1_fix_sweep.ipynb`, `PG_LIF_collapse_diagnostic.ipynb` | Sec. 4.3, App. | Diagnostics for the leak-amplification failure mode and its fix |
| `PG_LIF_grad_horizon_diagnostic.ipynb` | Sec. 4.3, Fig. 11 | Empirical verification of the gradient-propagation claim (exact autograd gradient-norm ratios vs. horizon) |
| `PG_LIF_SSC_confirmation.ipynb` | Sec. 6 (SSC), Fig. 13 | Single-seed cross-dataset confirmatory check on Spiking Speech Commands (SSC) |
| `PG_LIF_P3a_one_shot_memorization.ipynb` | Sec. 7.4, Fig. 8, Fig. 12 | One-shot memorization (BTSP-style memory layer), gated vs. ungated control, and faithful reproduction of the Wu & Maass (2025) baseline |
| `PG_LIF_P3b_gated_eprop.ipynb` | Sec. 7, Table 2, Fig. 2 | Regime B: online e-prop with plateau-gated vs. permuted-gated vs. ungated three-factor rule |
| `PG_LIF_P4_sensitivity.ipynb` | Sec. 8, Fig. 10 | Hyperparameter sensitivity analysis |

`notebooks/executed_runs/` holds re-executed copies (with cell outputs retained)
of the notebooks used to extract the exact numbers/figures reported for the
gradient-horizon diagnostic, the SSC confirmation, the Wu-Maass comparison, and
the final Regime B (e-prop) learning curves (Figure 2) — kept as a record of
provenance for those specific results.

## Figures

`figures/` contains the 13 figures used in the manuscript at 300 DPI, named
`fig1_...png` through `fig13_...png` matching their in-text labels.

## Reproducing results

Each notebook is self-contained (model definition, training loop, and
evaluation/plotting in one file) and can be run top-to-bottom in Jupyter.
Random seeds are set explicitly in each notebook; where a result is reported
across multiple seeds, the seed loop is included in the same notebook.

### Requirements

See `requirements.txt`. Tested with Python 3.10+.

## Data availability

SHD and SSC are the public Spiking Heidelberg/Speech Commands datasets
(Cramer et al.), downloaded automatically by the relevant notebooks via their
standard loaders. No proprietary data is used.

## Citation

If you use this code, please cite the manuscript (citation details to be
added upon publication).

## License

MIT License — see `LICENSE`.
