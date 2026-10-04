# Computational Science & Bioinformatics Roadmap

![License](https://img.shields.io/badge/license-MIT-green.svg) ![language](https://img.shields.io/badge/language-python%20%7C%20julia-blue.svg) ![focus](https://img.shields.io/badge/focus-simulation%20%2B%20genomics-green.svg)

Use code to simulate physical systems and analyze biological data, with the reproducibility standards scientific results require.

## Table of Contents

1. [Workflow Overview](#workflow-overview)
2. [Prerequisites](#prerequisites)
3. [Phase 1: Scientific Computing Foundations](#phase-1-scientific-computing-foundations)
4. [Phase 2: Numerical Methods](#phase-2-numerical-methods)
5. [Phase 3: Simulation & Reproducibility](#phase-3-simulation--reproducibility)
6. [Phase 4: Bioinformatics Core](#phase-4-bioinformatics-core)
7. [Phase 5: Applied Genomics & Structure](#phase-5-applied-genomics--structure)
8. [Capstone Projects](#capstone-projects)
9. [Repository Layout](#repository-layout)
10. [Engineering Rules](#engineering-rules)
11. [Exit Criteria](#exit-criteria)

---

## Workflow Overview

```
 Scientific Python --> Numerical methods --> Simulation (ODE/PDE/Monte Carlo)
                                                       |
 Reproducibility (Snakemake, envs) <-------------------+
        |
        v
 Sequence analysis --> Genomics pipelines --> Applied biology (scRNA, structure)
```

## Prerequisites

- [ ] Python and NumPy (Stages 1 and 4 of the ML roadmap)
- [ ] Calculus and linear algebra (Stages 0 and 3 of the ML roadmap)
- [ ] Basic probability and statistics
- [ ] No biology background is needed; Phase 4 teaches what you need

## Phase 1: Scientific Computing Foundations

Goal: Be fluent with the tools scientists use.

| Resource | Type | Why |
|----------|------|-----|
| [Scientific Python Lectures](https://scipy-lectures.org/) | Free notes | NumPy, SciPy, Matplotlib essentials |
| [Think Stats](https://greenteapress.com/wp/think-stats-2e/) | Free book | Statistics through code |
| [Think Bayes](https://allendowney.github.io/ThinkBayes2/) | Free book | Bayesian inference through code |
| [Julia Documentation](https://docs.julialang.org/) | Docs | Optional: fast language common in scientific computing |

- [ ] Vectorize numerical code and profile it
- [ ] Statistical tests and confidence intervals on real data
- [ ] Bayesian updating on two worked problems

**Deliverables**
- [ ] `notebooks/foundations/` with 3 analyses and written conclusions

## Phase 2: Numerical Methods

Goal: Know when numerical answers are trustworthy.

| Resource | Type | Why |
|----------|------|-----|
| [Fundamentals of Numerical Computation](https://fncbook.com/) | Free book | Root finding, linear systems, ODEs, PDEs |
| [Computational Physics (Mark Newman)](http://www-personal.umich.edu/~mejn/cp/) | Book site with data and code | Applied numerical problems |
| [DifferentialEquations.jl Docs](https://docs.sciml.ai/DiffEqDocs/stable/) | Docs | Reference solvers and theory notes |

- [ ] Root finding, interpolation, and quadrature with error analysis
- [ ] Solve ODEs with Euler, RK4, and an adaptive solver
- [ ] Solve the 1-D heat equation and verify the convergence order
- [ ] Understand conditioning and floating-point error

**Deliverables**
- [ ] `src/numerics/` solvers with convergence tests
- [ ] `docs/convergence_report.md` with log-log error plots

## Phase 3: Simulation & Reproducibility

Goal: Make results others can rerun and trust.

| Resource | Type | Why |
|----------|------|-----|
| [Good Enough Practices in Scientific Computing](https://arxiv.org/abs/1609.00037) | Paper | Minimum standard for reproducible work |
| [Software Carpentry Lessons](https://software-carpentry.org/lessons/) | Short lessons | Git, shell, testing for scientists |
| [Snakemake Documentation](https://snakemake.readthedocs.io/en/stable/) | Docs | Reproducible workflow engine |
| [Nextflow Documentation](https://www.nextflow.io/docs/latest/) | Docs | Alternative workflow engine common in genomics |

- [ ] Monte Carlo simulation with variance estimates
- [ ] Pin environments with a lock file
- [ ] Turn a multi-step analysis into a Snakemake workflow

**Deliverables**
- [ ] `workflows/` Snakemake pipeline that reproduces a result from raw data with one command

## Phase 4: Bioinformatics Core

Goal: Learn sequence algorithms by implementing them.

| Resource | Type | Why |
|----------|------|-----|
| [Rosalind](https://rosalind.info/) | Problem set | Learn bioinformatics by solving programming problems |
| [Bioinformatics Algorithms: An Active Learning Approach](https://www.bioinformaticsalgorithms.org/) | Textbook site | Algorithms behind sequence analysis |
| [Biopython Tutorial](https://biopython.org/DIST/docs/tutorial/Tutorial.html) | Docs | Standard Python bioinformatics library |
| [NCBI BLAST Help](https://blast.ncbi.nlm.nih.gov/doc/blast-help/) | Docs | Understand the tool you will reimplement in miniature |
| [Galaxy Training Network](https://training.galaxyproject.org/) | Tutorials | Practical genomics workflows |

- [ ] Rosalind: complete the first 60 problems
- [ ] Implement Needleman-Wunsch and Smith-Waterman
- [ ] Implement k-mer indexing and a seed-and-extend aligner

**Deliverables**
- [ ] `src/bio/` alignment algorithms tested against Biopython
- [ ] `notebooks/bio/` showing results on real sequences

## Phase 5: Applied Genomics & Structure

Goal: Analyze real datasets end to end.

| Resource | Type | Why |
|----------|------|-----|
| [Computational Genomics with R](https://compgenomr.github.io/book/) | Free book | Genomics statistics and pipelines |
| [Scanpy Tutorials](https://scanpy.readthedocs.io/en/stable/tutorials/) | Docs | Single-cell RNA-seq in Python |
| [AlphaFold Protein Structure Database](https://alphafold.ebi.ac.uk/) | Database | Predicted protein structures to explore |

- [ ] Run a single-cell RNA-seq analysis on a public dataset
- [ ] Quality control, normalization, clustering, marker genes
- [ ] Explore AlphaFold structures for a protein family you chose

**Deliverables**
- [ ] Snakemake-driven analysis with a written report in `docs/analysis_report.md`

## Capstone Projects

- [ ] Physics: a PDE simulation with verified convergence order and a documented stability limit
- [ ] Bioinformatics: a seed-and-extend aligner tested against Biopython, with a performance comparison
- [ ] Applied: a reproducible single-cell analysis from raw counts to annotated clusters, rerunnable with one command
- [ ] Publish each as a short methods-and-results writeup

## Repository Layout

```
comp-sci-bio/
├── README.md
├── pyproject.toml
├── environment.lock          # pinned environment
├── src/
│   ├── numerics/
│   └── bio/
├── workflows/                # Snakemake pipelines
├── notebooks/
├── data/                     # gitignored; document sources and checksums
├── tests/
└── docs/
    ├── convergence_report.md
    └── analysis_report.md
```

## Engineering Rules

These are strict. A phase is not complete until its deliverables follow all of them.

### 1. Daily 1:3 Theory-to-Building Ratio

- [ ] For every 1 hour of reading or watching, spend 3 hours building, solving, or running labs
- [ ] Log hours in `docs/log.md` at the end of each session
- [ ] No new chapter until the previous one has working code or a written lab report

### 2. Git Branch Hygiene

- [ ] `main` is always green and never receives direct commits
- [ ] One branch per deliverable: `phase-N/short-description`
- [ ] Small commits with imperative messages; squash-merge via PR after checks pass
- [ ] Delete branches after merge

### 3. Quality Gates

- [ ] `mypy --strict src/`, `ruff`, and `pytest` pass
- [ ] Numerical tests use tolerances and convergence-order checks, not exact equality
- [ ] [Hypothesis](https://hypothesis.readthedocs.io/) property tests for algorithms with known invariants
- [ ] Workflows rerun from scratch in CI on a small dataset

### 4. Branch-Specific Rules

- [ ] Every numerical method is checked against a problem with a known answer
- [ ] Every plot states units, sample size, and uncertainty
- [ ] Raw data is never modified; derived data comes from code
- [ ] Cite data sources and licenses; do not publish human-subject data that is not public and consented

## Exit Criteria

- [ ] Show a solver converges at its theoretical order
- [ ] Reimplement an alignment algorithm and match a reference tool's output
- [ ] Rerun an entire analysis from a clean checkout with one command
- [ ] Explain a result's uncertainty and what would invalidate it
