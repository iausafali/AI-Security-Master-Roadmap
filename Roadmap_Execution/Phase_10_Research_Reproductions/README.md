[← Back to Master Execution Table](../../README.md)

# Phase 10: Research Reproductions — AI × Security Research Suite

**Timeline:** July – December 2029 (~24 Weeks)  
**Compute Tier:** Local + Cloud GPU as demanded by each paper  
**Project Directory:** `Project_Research_Reproductions_Suite/`

## Core objective

Demonstrate that research capability comes from independently understanding, reproducing, testing, and extending published work rather than merely reading papers or running authors' repositories.

## Resource spine

- **Stanford CS229T — Machine Learning Theory:** use as the theory track for learning theory, generalization, optimization, and rigorous analysis relevant to the selected research problems.
- **Research literature:** select six high-quality AI × security papers from venues such as USENIX Security, IEEE S&P, ACM CCS, NDSS, NeurIPS, and ICLR.
- **Scientific methodology:** reproducibility, statistical evaluation, ablations, failure analysis, artifact packaging, and technical writing.

CS229T is a theory component, not a seventh reproduction. Allocate time according to the mathematical needs of the selected papers.

## Research sequence

### Sprint 1 — Selection and decomposition

1. Select six papers spanning adversarial robustness, LLM/agent security, and systems/program analysis.
2. Read each paper actively: problem, assumptions, threat model, mathematical objective, baselines, dataset, metrics, and limitations.
3. Re-derive the important mathematics before implementation.
4. Build a common experiment harness for seeds, configurations, compute cost, metrics, and artifacts.

### Sprint 2 — Reproductions 1–3

- Reimplement the first three papers independently.
- Reproduce primary quantitative claims where feasible.
- Record hardware, software versions, hyperparameters, datasets, and deviations.

### Sprint 3 — Reproductions 4–6

- Repeat the process for the remaining three papers.
- Include at least one systems/security paper where the artifact requires low-level or program-analysis work.

### Sprint 4 — Ablation and failure analysis

- Run at least three meaningful ablations per paper where feasible.
- Identify divergence from published results.
- Separate implementation errors, environmental differences, statistical variance, undocumented assumptions, and genuine paper limitations.

### Sprint 5 — Scientific synthesis

- Produce six concise reproduction reports.
- Produce a cross-paper synthesis comparing assumptions, evaluation quality, reproducibility, and failure modes.
- Package reusable experiment infrastructure and artifact documentation.
- Prepare a workshop-quality submission when the results warrant it. Submission is a research opportunity, not a guaranteed outcome.

## Evidence and exit criteria

- [ ] Six papers independently reproduced or rigorously evaluated when exact reproduction is impossible.
- [ ] CS229T concepts applied to the theoretical analysis of selected work.
- [ ] Ablations and sensitivity analyses documented.
- [ ] Divergences from original results explained rather than hidden.
- [ ] Reproducibility environment and experiment harness released.
- [ ] Technical reports are auditable by another researcher.
