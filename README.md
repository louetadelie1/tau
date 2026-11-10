# Tau PTM simulations

Simulation inputs and analysis code for the manuscript:

> **Tau phosphorylation and acetylation shift the balance between intramolecular and intermolecular interactions in condensates**
> Adelie Louet, Jan F. M. Stuke, Lisa M. Pietrek, Michele Vendruscolo, Gerhard Hummer

The notebooks analyse all-atom molecular dynamics simulations of the tau-K32 fragment in seven
post-translational modification (PTM) states, as isolated chains and in 60-chain condensates,
and the tau-K18 force-field benchmark.

![Snapshots of 60-chain tau-K32 condensates for the seven modification states](images/condensate_slabs.png)

*Representative snapshots of 60-chain tau-K32 condensates for the seven modification states. Rectangles
mark the initial slab boundary. The fully phosphorylated and fully acetylated condensates contract into
denser, narrower slabs, whereas the unmodified and sparsely modified condensates extend beyond it.*

## Repository layout

```
analysis_files/   Jupyter notebooks for the analyses in the manuscript
simulations/      GROMACS run parameters (.mdp) for the all-atom simulations
images/           Figures used in this README
```

## Simulations

We provide the GROMACS run parameters for both simulation systems: the single-chain simulations
and the condensate simulations. All runs are all-atom, at 300 K, with modified TIP3P water
(`-DUSE_MODIFIED_TIP3P_EPS`).

**`simulations/run_para_single_chain/`**: isolated tau-K32 chains

| File | Step |
|---|---|
| `minim.mdp` | Steepest-descent energy minimisation |
| `nvt.mdp` | NVT equilibration, protein position-restrained (100 ps) |
| `npt.mdp` | NPT equilibration, protein position-restrained (250 ps) |
| `npt_no_retraints.mdp` | NPT equilibration without restraints (250 ps) |
| `md_re.mdp` | Production MD, Parrinello-Rahman barostat (100 ns per run) |
| `num_ions.py` | Number of ion pairs for a given water count and salt concentration: `python num_ions.py <n_waters> <conc_M>` |

**`simulations/run_para_condensates/`**: 60-chain tau-K32 condensates (back-mapped from Martini
coarse-grained slabs)

| File | Step |
|---|---|
| `soft_npt.mdp` | Steepest-descent minimisation with soft-core interactions, to resolve clashes after back-mapping |
| `soft_nvt.mdp` | Soft-core (free-energy) settings used with the step above |
| `nvt.mdp` | NVT equilibration, protein position-restrained (1 fs steps, 50 ps) |
| `npt.mdp` | NPT equilibration, protein position-restrained (250 ps) |
| `npt_no_retraints.mdp` | NPT equilibration without restraints (250 ps) |

## Notebooks

| Notebook | What it analyses |
|---|---|
| `analysis_files/single_chain_analysis_all_reps.ipynb` | Single-chain tau-K32: charge, radius of gyration, salt bridges, contacts, secondary structure, convergence |
| `analysis_files/condensate_analysis_all_reps.ipynb` | 60-chain condensates: density profiles, interchain and intrachain contacts, contact coupling, secondary structure, slab radius of gyration |
| `analysis_files/ff_comaparison.ipynb` | Force-field benchmark on tau-K18: radius of gyration, SAXS, residual dipolar couplings (RDCs) |
| `analysis_files/HCG_v_MD.ipynb` | Hierarchical chain growth (HCG) structures compared with MD |

## Requirements

Python 3 with:

- `numpy`, `scipy`, `pandas`
- `matplotlib`, `seaborn`
- `mdtraj`
- `MDAnalysis`
