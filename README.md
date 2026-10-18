# Delivery Parcel Selection Optimization: GA vs Binary PSO

A Computational Intelligence assignment (SAIA 1193, Universiti Teknologi Malaysia).
It solves a delivery van loading problem, a 0/1 knapsack-style selection, using two
metaheuristics and compares their results:

- **Genetic Algorithm (GA)**
- **Binary Particle Swarm Optimization (Binary PSO)**

## Problem
A delivery van with a **57 kg** capacity must choose which of 6 Kuala Lumpur
delivery locations to serve. Each location has a parcel weight, a distance and a
priority level.

| ID | Location | Distance (km) | Weight (kg) | Priority |
|---|---|---|---|---|
| L1 | KLCC | 9 | 8 | 5 |
| L2 | Bukit Bintang | 10 | 7 | 5 |
| L3 | Cheras | 12 | 14 | 4 |
| L4 | Setiawangsa | 7 | 11 | 4 |
| L5 | Wangsa Maju | 6 | 10 | 3 |
| L6 | Damansara | 15 | 9 | 3 |

Each solution is a **binary vector** (1 = location selected, 0 = skipped).

**Fitness function**
`Fitness = Total Priority Score − Total Distance − Penalty`
- Priority score = Σ (weight × priority) of selected locations
- Penalty = 100 × (kg over van capacity)

## Algorithm Settings

| | GA | Binary PSO |
|---|---|---|
| Population / swarm size | 6 | 6 |
| Generations / iterations | 37 | 37 |
| Selection | Tournament (k = 2) | n/a |
| Crossover | Single-point, rate 0.8 | n/a |
| Mutation | Bit-flip, rate 0.1 | n/a |
| Elitism | Yes | n/a |
| Inertia weight (w) | n/a | 0.7 |
| c1 / c2 | n/a | 1.5 / 1.5 |
| Position update | n/a | Sigmoid of velocity |

## Results
Both algorithms found the same best solution:

| Metric | Value |
|---|---|
| Selected locations | KLCC, Bukit Bintang, Cheras, Setiawangsa, Wangsa Maju |
| Total weight | 50 kg (within the 57 kg capacity) |
| Total priority score | 205 |
| Total distance | 44 km |
| Penalty | 0 |
| **Best fitness** | **161** |

The notebook also plots the convergence of each algorithm (`ga_convergence.png`,
`pso_convergence.png`) and a combined GA vs PSO convergence comparison
(`ga_vs_pso_convergence.png`).

## Notebook Structure
- **Part C:** GA with initial population, fitness evaluation, selection, crossover,
  mutation, 37-generation run and convergence graph
- **Part D:** Binary PSO with initial particles, parameters, concepts (velocity,
  sigmoid, pBest, gBest), 37-iteration run and convergence graph
- **Part E:** side-by-side GA vs PSO comparison table and combined convergence plot

## How to Run
```bash
pip install numpy matplotlib tabulate
jupyter notebook PARTC_D_E.ipynb
```
Or upload the notebook to Google Colab. A fixed random seed (42) is used for
reproducibility.

## Tech Stack
Python, NumPy, Matplotlib, Tabulate

## Author
Naufal, Faculty of Artificial Intelligence, UTM

