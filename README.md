<!-- SHOWCASE: false -->

# Point Scattering Problem

> A genetic algorithm study comparing three problem representations for maximizing minimum pairwise distance among n points placed within a unit circle.

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Language](https://img.shields.io/badge/language-Python-blue)
![Semester](https://img.shields.io/badge/semester-Spring%202026-orange)

---

## Course Information

| Field                  | Details                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Course Title           | Evolutionary Computation                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Course Number          | CAP 5512                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Semester               | Spring 2026                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Assignment Title       | Point Scattering Problem: Homework 2                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Assignment Description | Explore the impact of problem representation on GA performance for the point scattering problem. Given an integer n, place n points in a unit circle such that the minimum pairwise distance between any pair of points is maximized. Implement and compare three distinct representations: Cartesian (x, y), polar (r, theta), and boundary (theta only). Evaluate each for n = 5, n = 10, and n = 25 across 25 independent trials and analyze the strengths and weaknesses of each representation. |

---

## Project Description

This project implements and compares three genetic algorithm representations for the point scattering problem: Cartesian coordinates, polar coordinates, and a boundary-constrained polar representation that forces all points to the unit circle perimeter. Each representation uses a custom initialization and mutation strategy suited to its coordinate space, with uniform crossover and tournament selection shared across all three. The experiment runs 25 independent trials per representation per value of n, collecting per-generation fitness curves and final solution statistics including mean, standard deviation, and 95% confidence intervals.

---

## Screenshots / Demo

![Cartesian Fitness Curve](graphs/cartesian_n10_best_run.png)
![Cartesian Final Distribution](graphs/cartesian_n10_best_final.png)

> Cartesian representation (n = 10): fitness curve for the best trial (left) and final point distribution of the best solution (right).

![Polar Fitness Curve](graphs/polar_n10_best_run.png)
![Polar Final Distribution](graphs/polar_n10_best_final.png)

> Polar representation (n = 10): fitness curve for the best trial (left) and final point distribution of the best solution (right).

![Boundary Fitness Curve](graphs/boundary_n10_best_run.png)
![Boundary Final Distribution](graphs/boundary_n10_best_final.png)

> Boundary representation (n = 10): fitness curve for the best trial (left) and final point distribution showing all points constrained to the perimeter (right).

---

## Results

When run correctly, the program prints per-representation statistics to the console and saves fitness curve and point distribution plots to the `graphs/` folder.

**Sample terminal output:**

```
!!!! Running Experiment with 25 trials !!!!
===== Cartesian Implementation (x, y) =====
Printing Cartesian results........
Cartesian final stats:
MEAN: 0.618
STD: 0.012
95% Confidence Interval: 0.612, 0.624
Final Best Minimum Distance: 0.631457
Best mean fitness at final generation: 0.621
===== Polar Implementation (r, θ) =====
...
===== Boundary Implementation (θ) =====
...
```

**How to interpret the output:**

- `MEAN` and `STD` summarize final-generation fitness across 25 trials.
- `95% Confidence Interval` gives the t-distribution CI on that mean.
- `Final Best Minimum Distance` is the single best solution found across all trials for that representation.
- `Best mean fitness at final generation` reflects the population-average quality at convergence.
- Higher values indicate better solutions (points are more evenly spread).

**Generated files:**

- `graphs/[representation]_n[N]_best_run.png` - Fitness curve for the best trial.
- `graphs/[representation]_n[N]_best_final.png` - Point distribution plot of the best final solution.
- `logs/[representation]_n[N]_gen200.txt` - Per-generation point coordinates for the best individual.

If results look unexpectedly low, check the `--indpb` value and ensure `--seed` is consistent. Adjust population size or generation count in the `Config` dataclass in `utility.py`.

---

## Key Concepts

`genetic-algorithms` `problem-representation` `point-scattering` `evolutionary-computation` `fitness-maximization` `uniform-crossover` `tournament-selection` `euclidean-distance` `polar-coordinates` `statistical-analysis`

---

## Languages & Tools

- **Language:** Python 3
- **Framework/SDK:** DEAP (Distributed Evolutionary Algorithms in Python)
- **Hardware:** N/A
- **Build System:** None (script-based)

---

## File Structure

```
point-scattering-problem/
├── main.py                     # Entry point; parses args and runs all three experiments
├── utility.py                  # Shared helpers: fitness functions, stats, plotting, config
├── implementations/
│   ├── cartesian.py            # GA using (x, y) Cartesian representation
│   ├── polar.py                # GA using (r, theta) polar representation
│   └── boundary.py             # GA using (theta) boundary-only representation (r = 1)
├── graphs/                     # Output: fitness curves and point distribution plots
├── logs/                       # Output: per-generation coordinate logs
└── requirements.txt
```

---

## Installation & Usage

### Prerequisites

- Python 3.10+
- pip

### Setup

```bash
# 1. Clone the repository
git clone https://github.com/yourusername/UCF-EvolutionaryComputation-PointScatteringProblem.git
cd UCF-EvolutionaryComputation-PointScatteringProblem

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run with a chosen n value (default: 5)
python main.py --n 5
```

To run all three n values used in the assignment:

```bash
python main.py --n 5
python main.py --n 10
python main.py --n 25
```

### Controls

| Argument  | Description                                  | Default |
| --------- | -------------------------------------------- | ------- |
| `--n`     | Number of points to place in the unit circle | `5`     |
| `--indpb` | Per-gene mutation probability                | `0.2`   |
| `--seed`  | Base random seed for reproducibility         | `42`    |

---

## Contributors

| Name               | Role                                                                                             | GitHub                                             |
| ------------------ | ------------------------------------------------------------------------------------------------ | -------------------------------------------------- |
| Alexander Green    | Software setup, Cartesian implementation, polar-to-Cartesian conversion, boundary implementation | [@alexneilgreen](https://github.com/alexneilgreen) |
| Christian Pumarada | Software review, polar implementation, graphing setup                                            | [@Aurelius1824](https://github.com/Aurelius1824)   |

---

## Academic Integrity

This repository is publicly available for **portfolio and reference purposes only**.
Please do not submit any part of this work as your own for academic coursework.
