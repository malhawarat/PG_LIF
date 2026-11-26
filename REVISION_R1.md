# Revision R1 (Neurocomputing NEUCOM-D-26-21785)

This folder holds the code and results added during the first revision. Copy its
contents into the repository root, keeping the folder structure, and commit.

## Notebooks (`notebooks/`)

| Notebook | What it runs | Reported in |
|---|---|---|
| `PG_LIF_P1_paper_mode_R1.ipynb` | Regime A revision runs: the 2x2 mechanism factorial, the kappa-initialized-at-zero control, the two alternative stabilization strategies, and the five-seed `P0 = 2` and `tau_p = 250` runs. Also the scanner that writes the complete discard table. | Table 4, Table 5, Sections 7.1 and 7.4 |
| `PG_LIF_P3b_gated_eprop_R1.ipynb` | Regime B with the two neuron-local gate normalizations, full-test-set accuracy, and log-only non-finite counting. Reproduces the three published rules unchanged. | Table 2, Section 7.3 |
| `PG_LIF_P3a_confirmatory_matched_controls_R1.ipynb` | Confirmatory one-shot experiment, 50 new seeds (100-149), with the mismatched-pattern, permuted-gate and learning-rate-matched random controls. | Table 6, Figure 11, Section 7.5 |
| `PG_LIF_P3a_one_shot_memorization_R1_eq12_sensitivity.ipynb` | Sensitivity run of the one-shot experiment under the alternative gate normalization. | Section 7.5 |

`notebooks/executed_runs/` holds the executed copies of these notebooks, with
their outputs, as a record of the runs the paper reports.

## Results (`results/`)

| File | Contents |
|---|---|
| `discard_table_full_R1.csv` | Every Regime A run in the project, with its best test accuracy, discarded-step count, discard rate, stabilization mode, and whether any parameter was non-finite at the end. This is the source of Table 5. |
| `regime_b_R1/` | One JSON per Regime B run (5 rules x 5 seeds), each with the per-epoch history, the gate statistics, the non-finite counters and the calibration constants, plus `summary_R1.json`. |
| `oneshot_confirmatory_stats_R1.json` | Paired differences, bootstrap confidence intervals, Wilcoxon and sign tests, Holm adjustment and the equivalence tests for the confirmatory experiment. |
| `oneshot_confirmatory_matching_R1.json` | Evidence that the controls are matched: mean gated-neuron count, summed gate per pattern, and per-neuron update totals for every rule. |
| `oneshot_confirmatory_stats_eq12_sensitivity.json` | The same statistics under the alternative gate normalization. |

## Figures (`figures/`)

`fig0_overview.png` (the new model-overview figure, Figure 1),
`fig14_oneshot_matched_controls.png` (Figure 11) and `fig_p3b_R1.png`
(the Regime B revision runs).

## Note on the seed budget

The Regime A revision runs use seeds 0-4 and the confirmatory one-shot
experiment uses seeds 100-149, which were not used anywhere in the submitted
version. The three original Regime B rules reproduce their published per-seed
results exactly, so the published numbers and the revision numbers come from the
same protocol.
