[← Back to Master Execution Table](../../README.md)

# Phase 5: MLOps + Reverse Engineering — MLOps Platform & Binary Audit

**Timeline:** November 2027 – January 2028 (~12 Weeks)  
**Compute Tier:** RAM-bound Cloud VM (16GB–32GB RAM) — $20–50/mo  
**Project Directory:** `Project_MLOps_Platform_Binary_Audit/`

---

## Resource spine

| Resource | Role in this phase |
|---|---|
| **Stanford CS229S — Machine Learning Systems Design** | Model serving, data pipelines, monitoring, scaling, reliability |
| **Made With ML** | End-to-end production ML workflow, reproducibility, testing, deployment, monitoring |
| **DeepLearning.AI — Machine Learning in Production** | Production lifecycle, deployment, monitoring, model maintenance, operational trade-offs |
| **OpenSecurityTraining2** | x86-64 architecture, assembly, calling conventions, reverse engineering |
| **Ghidra** | Static analysis, decompilation, control-flow recovery, scripting |

The three ML-production resources are complementary. Do not treat them as three independent full-time courses: use the overlapping material diagnostically and spend the majority of time implementing the flagship system.

## Academic Freeze

Keep the existing university final-exam freeze window in this phase. During the freeze, university obligations take priority and the flagship project is paused rather than rushed.

## Flagship project

Build a monitored ML serving platform with canary deployment, drift detection, automated retraining triggers, observability, and reproducible deployment. In parallel, perform controlled reverse engineering of a binary that you own and intentionally compiled for the exercise.

### Core implementation targets

- asynchronous model serving
- canary and shadow deployment
- KS and PSI drift detection
- automated retraining workflow
- Prometheus/Grafana observability
- reproducible Docker environment
- stripped-binary analysis with Ghidra
- CFG and data-structure recovery
- headless Ghidra automation
- documented reverse-engineering findings

## Evidence and exit criteria

- [ ] CS229S concepts demonstrated in the serving platform.
- [ ] Made With ML production workflow translated into reproducible project practice.
- [ ] Machine Learning in Production lifecycle concepts demonstrated in deployment/monitoring decisions.
- [ ] Serving platform measures latency, throughput, drift, and deployment state.
- [ ] Automated retraining path is tested end-to-end.
- [ ] Owned stripped binary is analyzed without source access.
- [ ] Reverse-engineering findings are documented with evidence.
- [ ] Final technical report and reproducibility instructions published.
