#  Genetic Algorithm for Feature Selection

> A biologically-inspired optimization approach to selecting the most informative features for machine learning classification tasks.

---

##  Overview

This project implements a **Genetic Algorithm (GA)** to perform **wrapper-based feature selection** — evolving a population of candidate feature subsets over multiple generations to maximize classification performance.

Instead of exhaustively searching all 2ⁿ possible feature subsets, the GA navigates the search space efficiently using mechanisms inspired by natural selection: **selection**, **crossover**, and **mutation**.

---

##  How It Works

Each individual in the population is a **binary chromosome** of length *n* (number of features), where:
- `1` = feature is selected
- `0` = feature is excluded

The algorithm evolves over generations:

```
Initialize population
      │
      ▼
 Evaluate fitness (e.g. cross-validated accuracy on selected features)
      │
      ▼
 Selection  ──►  Crossover  ──►  Mutation
      │
      ▼
 New generation
      │
      ▼
 Repeat until stopping criterion met
      │
      ▼
 Return best individual (optimal feature subset)
```

### Key Components

| Component | Description |
|-----------|-------------|
| **Chromosome** | Binary vector encoding selected features |
| **Fitness function** | Cross-validated score (e.g. accuracy, balanced accuracy) of a classifier trained on the selected features |
| **Selection** | Tournament or roulette-wheel selection of parents |
| **Crossover** | Single-point or uniform crossover to combine parent chromosomes |
| **Mutation** | Random bit flips to maintain diversity and avoid local optima |
| **Elitism** | Best individuals carried over unchanged to the next generation |

---

##  Repository Structure

```
Genetic-Algorithm-for-Feature-Selection/
└── feature_selection/
    └── *.ipynb      # Jupyter notebooks with GA implementation & experiments
```

---


##  Algorithm Parameters

| Parameter | Description | Typical Value |
|-----------|-------------|---------------|
| `population_size` | Number of individuals per generation | 20–100 |
| `n_generations` | Number of evolution cycles | 50–200 |
| `crossover_rate` | Probability of crossover between two parents | 0.7–0.9 |
| `mutation_rate` | Probability of flipping each gene | 0.01–0.05 |
| `elite_size` | Number of top individuals preserved each generation | 1–5 |
| `classifier` | Model used to evaluate fitness | e.g. Random Forest, SVM |
| `cv_folds` | Cross-validation folds for fitness evaluation | 5 |

---

##  Example Results

```
Generation  1/50  |  Best fitness: 0.742  |  Features selected: 38/100
Generation 10/50  |  Best fitness: 0.801  |  Features selected: 22/100
Generation 25/50  |  Best fitness: 0.834  |  Features selected: 17/100
Generation 50/50  |  Best fitness: 0.849  |  Features selected: 14/100
```

> *Values are illustrative — update with your actual experiment results.*

---

##  Fitness Convergence

The notebook includes plots tracking:
- Best and average fitness across generations
- Number of selected features over time
- Comparison vs. baseline (all features / random selection)

---



##  Why Genetic Algorithms?

- **No gradient required** — works with any black-box classifier
- **Global search** — less prone to local optima than greedy methods
- **Flexible fitness** — any metric (accuracy, F1, balanced accuracy, AUC) can be optimized
- **Interpretable output** — result is a simple list of selected features

---

##  Technologies Used

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.x-orange?logo=scikit-learn)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![NumPy](https://img.shields.io/badge/NumPy-2.x-blue?logo=numpy)
![Pandas](https://img.shields.io/badge/Pandas-2.x-blue?logo=pandas)

---
