# Phase 1: Semester 5 Fusion — AI-Driven OS-Level Security Monitor

**Timeline:** September 26, 2026 – January 2027  
**Compute Tier:** Local CPU/WSL2 + GitHub Codespaces — $0–10/mo  
**Project Directory:** `Project_OS_Security_Monitor/`

## Purpose

Integrate the university semester with the canonical AI + systems + security roadmap. University coursework supplies the academic floor; this project supplies implementation and systems depth.

## Resource spine

| Resource | Role |
|---|---|
| **Stanford CS229** | Core machine learning theory and algorithms |
| **Berkeley CS188** | Search, MDPs, planning, and decision-making where useful to the semester |
| **MIT 6.1810 (xv6)** | Operating systems, system calls, traps, page tables, locks, filesystems |
| **PortSwigger Web Security Academy** | Authorized web-security practice against the project dashboard/API |
| **OWASP WSTG** | Structured web application security testing methodology |
| **MIT 18.06** | Linear algebra refresh needed for ML derivations |
| **MIT 18.05** | Probability/statistics refresh for inference and evaluation |
| **MIT 18.065** | Matrix methods in data analysis, connecting linear algebra to PCA, SVD, optimization, and data analysis |

Use problem-first learning. Attempt the relevant university/problem-set/project task before consuming supplementary lectures. Skip material that can already be demonstrated independently.

## Flagship project

Build an AI-driven OS-level security monitor: instrument xv6, stream syscall telemetry, extract statistical features, implement baseline anomaly detectors, and expose results through a small monitoring service. Test the resulting application only in the owned lab environment using the WSTG methodology, then remediate the findings.

## Academic integration

Maintain university exam periods as priority windows. When the academic calendar differs from the provisional dates below, update the freeze dates before the semester starts rather than pretending a roadmap knows the university timetable better than the university.

## Engineering evidence

- [ ] xv6 kernel instrumentation works and is reproducible.
- [ ] Syscall telemetry reaches userspace reliably.
- [ ] ML inference path is understood and tested against an independent library baseline.
- [ ] Detection metrics are measured on a documented synthetic dataset.
- [ ] Web/API security assessment is performed only against the owned application.
- [ ] Findings are patched and re-tested.
- [ ] CI builds the project and runs the core tests.
- [ ] A technical report records design decisions, benchmarks, failures, and limitations.
