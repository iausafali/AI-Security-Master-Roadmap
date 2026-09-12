[← Back to Master Execution Table](../../README.md)

# Phase 10: Research Reproductions — 6 Paper Reproductions with Ablations

**Timeline:** July – December 2029 (~24 Weeks)  
**Compute Tier:** Cloud GPU as demanded per paper — $100–300/mo  
**Project Directory:** `Project_Research_Reproductions_Suite/`  
**Core Objective:** Demonstrate rigorous academic research capability by independently reproducing 6 milestone papers from top-tier venues (USENIX Security, IEEE S&P, ACM CCS, NDSS, NeurIPS, ICLR) with documented divergences and ablations.

---

## ⚡ The 30/70 Efficiency Rule (Fluff Filter)

| Activity | ▶️ FOCUS (Research Rigor & Depth) | ❌ SKIP / AVOID |
|----------|-----------------------------------|-----------------|
| **Paper Selection & Reading** | Top-tier peer-reviewed papers (USENIX Security, IEEE S&P, ACM CCS, NeurIPS) with clear mathematical formulations and experimental baselines. | Reading papers passively without writing code; unverified preprints without reproducible evaluation setups. |
| **Experimental Execution** | From-scratch reimplementation of core algorithms; independent hyperparameter sweeps; systematic failure mode analysis and $\ge 3$ ablations per paper. | Running authors' unmodified release scripts and calling it reproduction. |

---

## 📅 Flagship Milestone Schedule (24-Week Breakdown)

### 🏃 Sprint 1: Paper Selection, Mathematical Decomposition & Infrastructure (Weeks 1–4: Jul 1 – Jul 28)
* **Week 1 (Paper Selection & Feasibility Audit):**
  * Select 6 landmark papers at the AI $\times$ Security intersection across 3 domains:
    1. *Adversarial Robustness / Certified Defenses* (e.g., Randomized Smoothing, Certified Patch Defenses).
    2. *LLM Security / Automated Jailbreaking / Backdoors* (e.g., Suffix Optimization, Sleeper Agents, Poisoning).
    3. *Systems Security / AI-Assisted Fuzzing / Program Analysis* (e.g., Neural Fuzzing, Binary Decompilation via Transformers).
* **Week 2 (Mathematical Decomposition & Derivation Notebooks):**
  * Deconstruct all mathematical proofs, bounds, and objective functions across the 6 papers.
* **Week 3 (Compute Infrastructure & Dataset Ingestion):**
  * Set up automated reproducible Docker environments and download required benchmark datasets.
* **Week 4 (Experimental Framework & Metric Harness):**
  * Build standardized evaluation harness to log exact compute costs, random seeds, and metric outputs.

---

### 🏃 Sprint 2: Full Reproduction — Papers 1 through 3 (Weeks 5–10: Jul 29 – Sep 8)
* **Weeks 5–6 (Paper 1: Certified Adversarial Defenses):**
  * Re-implement core defense from scratch; run certified radius evaluation.
  * *Deliverable:* Complete reproduction report comparing original vs. reproduced figures.
* **Weeks 7–8 (Paper 2: Automated LLM Jailbreak & Suffix Optimization):**
  * Re-implement gradient-based discrete token optimization (GCG / AutoDAN).
  * *Deliverable:* Attack success rate comparison across target model sizes.
* **Weeks 9–10 (Paper 3: Neural Program Analysis / Binary Decompilation):**
  * Re-implement transformer-based binary type recovery model; train on stripped binaries.
  * *Deliverable:* Struct recovery accuracy matrix vs. author baseline.

---

### 🏃 Sprint 3: Full Reproduction — Papers 4 through 6 (Weeks 11–16: Sep 9 – Oct 20)
* **Weeks 11–12 (Paper 4: Data Poisoning & Backdoor Injection in LLMs):**
  * Re-implement clean-label poisoning attacks; evaluate trigger persistence post-fine-tuning.
* **Weeks 13–14 (Paper 5: Autonomous Vulnerability Discovery & Fuzzing):**
  * Re-implement neural coverage-guided fuzzer; evaluate crash discovery on Google FuzzBench.
* **Weeks 15–16 (Paper 6: Agentic Multi-Step Cyber Exploitation):**
  * Re-implement LLM-driven autonomous exploitation pipeline on standard CTF benchmark.

---

### 🏃 Sprint 4: Ablation Matrix & Failure Mode Deep Dive (Weeks 17–20: Oct 21 – Nov 17)
* **Weeks 17–18 (Systematic Ablation Execution):**
  * Execute $\ge 3$ distinct ablations per paper (18 total ablation experiments):
    * *Example:* Modify optimizer, vary poison budget, alter reward structure, test out-of-distribution datasets.
* **Weeks 19–20 (Failure Mode & Divergence Analysis):**
  * Document all discrepancies between published results and reproduction findings.
  * Root cause analysis: Identify unstated hyperparameters, hardware sensitivities, or dataset leakage in original papers.

---

### 🏃 Sprint 5: Scientific Synthesis & Artifact Release (Weeks 21–24: Nov 18 – Dec 14)
* **Weeks 21–22 (Comprehensive Synthesis Report):**
  * Author 6 mini-papers (6–10 pages each) formatted in ACM/IEEE template with high-resolution vector plots.
* **Weeks 23–24 (Artifact Evaluation & Open-Source Release):**
  * Package complete reproducibility repository meeting ACM Artifact Evaluation "Artifacts Available & Reusable" standards.
  * Submit findings to a top-tier workshop (e.g., NeurIPS Workshop on Robustness / USENIX Security WoOT).
  * Tag `v10.0-research-reproductions-complete`.

---

## 🔬 The S++++++ Audit Protocol

### Stage 1: Derive — Mathematical Foundations
- Full derivation of all underlying theoretical theorems and optimization objectives for all 6 papers.

### Stage 2: Implement — Zero Wrappers
- Re-implemented from scratch without relying on authors' proprietary unverified codebases.

### Stage 3: Benchmark — Performance Targets
- Reproduce primary claims within $\pm 5\%$ margin of published numbers (or explicitly prove why original numbers fail to replicate).

### Stage 4: Break & Patch
- Document specific brittleness modes and failure conditions discovered through ablation experiments.

---

## ✅ Exit Criteria Checklist
- [ ] 6 top-tier papers fully reproduced from scratch.
- [ ] 18 ablation experiments completed and documented.
- [ ] Formal divergence analysis explaining any variance from original claims.
- [ ] ACM Artifact Evaluation-compliant open-source repository published.
- [ ] Workshop paper drafted or submitted.
- [ ] Git tagged `v10.0-research-reproductions-complete`.