# Warring States Optimization Algorithm (WSOA)

**A Novel Heuristic Optimization Algorithm Inspired by the Chinese Warring States Period History**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.8+](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)

[English](README.md) | [中文](README_CN.md)

## Citation

If you use WSOA in your research, please cite the following paper:

> **Chaoqun Li.** Warring States Optimization Algorithm (WSOA): A Novel Heuristic Optimization Algorithm Inspired by the Chinese Warring States Period History. *DOI: coming soon*

**BibTeX:**

```bibtex
@article{li2026wsoa,
  title   = {Warring States Optimization Algorithm (WSOA): A Novel Heuristic Optimization Algorithm Inspired by the Chinese Warring States Period History},
  author  = {Li, Chaoqun},
  year    = {2026},
  note    = {DOI: coming soon}
}
```

> Please update the BibTeX entry once the DOI is officially assigned.

---

## Introduction

WSOA is a population-based metaheuristic optimization algorithm inspired by the historical dynamics of the Warring States period (475–221 BC) in ancient China. Seven subpopulations (representing the seven states: Qin, Qi, Chu, Yan, Zhao, Wei, Han) compete and cooperate in the search space, ultimately converging to the global optimum through a process of "unification".

## Algorithm Overview

### Five Phases

| Phase | Name | Mechanism |
|-------|------|-----------|
| I | **Seven States Established** | Initialize 7 subpopulations + opposition-based learning |
| II | **Reform & Compete** | 7 distinct search strategies (Levy flight / multi-teacher learning / Cauchy mutation / dual-elite guidance / adaptive DE / DE mutation / sine-cosine) + strategy adaptation |
| III | **Alliance & Diplomacy** | Vertical alliance (weak states share info) ; Horizontal alliance (strong state attracts talent) ; Espionage mechanism ; Befriend distant, attack nearby |
| IV | **Conquest & Annexation** | Weakest state eliminated, resources redistributed ; Dynamic population rebalancing |
| V | **Unification** | Merge all populations, multi-operator fine-grained search |

### Benchmark Suites

Supports 4 IEEE CEC standard test suites:

| Suite | Functions | Dimensions | Year |
|-------|-----------|-----------|------|
| CEC2005 | 25 | 10, 30 | 2005 |
| CEC2014 | 30 | 10, 30, 50 | 2014 |
| CEC2017 | 29 | 10, 30, 50 | 2017 |
| CEC2022 | 12 | 10, 20 | 2022 |

### Comparison Algorithms (11)

| Algorithm | Full Name | Year |
|-----------|-----------|------|
| PSO | Particle Swarm Optimization | 1995 |
| DE | Differential Evolution | 1997 |
| GA | Genetic Algorithm | 1975 |
| ABC | Artificial Bee Colony | 2007 |
| GWO | Grey Wolf Optimizer | 2014 |
| WOA | Whale Optimization Algorithm | 2016 |
| SCA | Sine Cosine Algorithm | 2016 |
| HHO | Harris Hawks Optimization | 2019 |
| MPA | Marine Predators Algorithm | 2020 |
| AO | Aquila Optimizer | 2021 |
| DBO | Dung Beetle Optimizer | 2023 |

## Project Structure

```
├── README.md                   # Project documentation
├── run.py                      # Entry point (CLI)
├── warring_states_algorithm.py # WSOA core algorithm
├── benchmark_functions.py      # CEC benchmark functions (via opfunu)
├── comparison_algorithms.py    # 11 comparison algorithms
├── plotting.py                 # Visualization module
├── run_experiment.py           # Experiment runner + CSV export
└── results/                    # Experiment outputs
    └── <SUITE>/
        ├── results_summary.csv     # Best/Worst/Mean/Median/Std
        ├── results_ranking.csv     # Rankings + average rank
        ├── results_raw.csv         # Raw fitness per run
        ├── results_convergence.csv # Convergence curve data
        ├── convergence_F*.png      # Convergence plots
        ├── summary_comparison.png  # Bar chart comparison
        ├── ranking_radar.png       # Ranking radar chart
        └── experiment_*.log        # Experiment log
```

## Requirements

```bash
pip install numpy matplotlib opfunu
```

## Quick Start

```bash
# Quick test (dim=10, 3 runs, 100 iterations)
python run.py --quick

# Default run (CEC2022, dim=10, 200 iterations, 5 runs)
python run.py

# Specify suite and dimension
python run.py --suite CEC2017 --dim 30

# Run all 4 CEC suites
python run.py --all_suites --dim 10 --runs 5

# Custom parameters
python run.py --suite CEC2014 --dim 30 --runs 10 --max_iter 500
```

## CSV Output (for Paper)

| File | Content | Paper Usage |
|------|---------|-------------|
| `results_summary.csv` | Best/Worst/Mean/Median/Std | Main result table |
| `results_ranking.csv` | Per-function rankings + average rank | Friedman test |
| `results_raw.csv` | Raw fitness values per run | Wilcoxon rank-sum test |
| `results_convergence.csv` | Convergence curve data | Redraw in Origin/MATLAB |

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

## Contact

- **Author:** Chaoqun Li
- **GitHub:** [supergroupli](https://github.com/supergroupli)
