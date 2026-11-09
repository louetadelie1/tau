# Tau PTM simulations: analysis notebooks

Analysis code for the manuscript:

> **Tau phosphorylation and acetylation shift the balance between intramolecular and intermolecular interactions in condensates**
> Adelie Louet, Jan F. M. Stuke, Lisa M. Pietrek, Michele Vendruscolo, Gerhard Hummer

The notebooks analyse all-atom molecular dynamics simulations of the tau-K32 fragment in seven
post-translational modification (PTM) states, as isolated chains and in 60-chain condensates,
and the tau-K18 force-field benchmark. Each notebook produces the figures listed below.

## Notebooks

| Notebook | What it analyses | Manuscript figures |
|---|---|---|
| `single_chain_analysis_all_reps.ipynb` | Single-chain tau-K32: charge, radius of gyration, salt bridges, contacts, secondary structure, convergence | Figures 1, 4, 5, 6; Figures S6–S11 |
| `condensate_analysis_all_reps.ipynb` | 60-chain condensates: density profiles, interchain and intrachain contacts, contact coupling, secondary structure, slab radius of gyration | Figures 3, 7; Figures S4, S5 |
| `ff_comaparison.ipynb` | Force-field benchmark on tau-K18: radius of gyration, SAXS, residual dipolar couplings (RDCs) | Figures S2, S3 |
| `HCG_v_MD.ipynb` | Hierarchical chain growth (HCG) structures compared with MD | Figure S1 |

Figure 2 (condensate snapshots) was rendered with PyMOL and is not produced here.

The single-chain notebook also writes `figure_s10_rg_windows.csv`: radius of gyration in 200 ns
windows for each system, with the spread between and within replicas.

## Requirements

Python 3 with:

- `numpy`, `scipy`, `pandas`
- `matplotlib`, `seaborn`
- `mdtraj`
- `MDAnalysis`
