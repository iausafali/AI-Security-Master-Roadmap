[← Back to Master Execution Table](../../README.md)

# Phase 1: Semester 5 Fusion — AI-Driven OS-Level Security Monitor

**Timeline:** September 28, 2026 – January 2027 (~16 Weeks)  
**Compute Tier:** Local CPU/WSL2 + GitHub Codespaces — $0–10/mo  
**Project Directory:** `Project_OS_Security_Monitor/`  
**University Reality:** ML, AI, OS, InfoSec, and Software Engineering land simultaneously in Semester 5.

---

## ⚡ The 30/70 Efficiency Rule (Fluff Filter)

| Course | ▶️ MUST WATCH (Core Theory & Depth) | ❌ SKIP / FAST-FORWARD (Already Known / Irrelevant) |
|--------|------------------------------------|-----------------------------------------------------|
| **Stanford CS229 (ML)** | Lectures 1–5 (Supervised Learning, Normal Equations, Logistic Regression, GDA, Naive Bayes), Lectures 6–8 (SVMs, Kernels, KKT conditions), Lectures 11–13 (GMM, EM Algorithm, PCA). | Skip Lectures on basic Python/Octave setups, general AI overviews, simple linear algebra review (Strang covers it better). |
| **Berkeley CS188 (AI)** | Lectures on Adversarial Search (Minimax, $\alpha$-$\beta$ pruning), MDPs, Bellman Equations, and Value/Policy Iteration. | Skip intro BFS/DFS/A* search basics (covered in 6.006/DSA), basic probability definitions. |
| **MIT 6.1810 (xv6 OS)** | Lectures & Labs on System Calls, Page Tables, Traps/Interrupts, Locks, and File System Logging. | Skip basic C syntax intro, command line user utilities lab (covered in Phase 0). |
| **PortSwigger Academy** | Deep dives into Server-Side Vulnerabilities (SQLi, Command Injection, Directory Traversal, SSRF) and Authentication/Access Control. | Skip elementary introductory video overviews; jump straight into Practitioner/Expert tier labs. |
| **OWASP WSTG** | Methodology sections: WSTG-INPV (Input Validation), WSTG-ATHZ (Authorization), WSTG-ERRH (Error Handling), WSTG-CONF (Configuration). | Skip repetitive high-level compliance overviews; focus on actionable test cases. |
| **MIT 18.06 / 18.05** | Strang's 4 Fundamental Subspaces, SVD, Eigenvalues; 18.05 Central Limit Theorem, Hypothesis Testing & Likelihood Ratios. | Skip basic scalar probability, high-school algebra calculations. |

---

## 🛑 Academic Freeze Enforcer

* **Midterm Hard Freeze Window:** **November 9 – November 23, 2026 (14 Days)**
  * *Policy:* 100% roadmap development freeze. Zero commits to flagship project. Focus exclusively on UCP midterm exam prep (OS, ML, SE, InfoSec).
* **Finals Hard Freeze Window:** **December 28, 2026 – January 15, 2027 (18 Days)**
  * *Policy:* 100% roadmap development freeze. All compute instances halted. Dedicated university final exam revision.

---

## 📅 Flagship Milestone Schedule (16-Week Breakdown)

### 🏃 Sprint 1: Core Mathematical Derivation & Data Structures (Weeks 1–3: Sep 28 – Oct 18)
* **Week 1 (Kernel Syscall Architecture):**
  * Instrument `kernel/syscall.c` in xv6-riscv to intercept all trapframe registers (`a0`–`a7`).
  * Mathematically derive memory alignment constraints for RISC-V page tables and 64-bit timestamps.
* **Week 2 (Lockless / Low-Overhead Ring Buffer):**
  * Derive concurrency invariants for kernel ring buffer: proof of single-producer / multi-consumer thread safety with spinlocks.
  * Implement `kernel/audit_log.c` (64KB circular ring buffer in kernel memory).
* **Week 3 (Character Device & Userspace Bridge):**
  * Implement `/dev/auditlog` character device (`kernel/audit_dev.c`) exposing structured JSONL stream.
  * Build user-space reader daemon (`user/log_reader.c`) with zero memory leakage.

---

### 🏃 Sprint 2: Low-Level Implementation — Zero Wrappers (Weeks 4–6: Oct 19 – Nov 8)
* **Week 4 (Streaming Feature Extraction Engine):**
  * Implement `ml/feature_engineering.py` without blackbox AutoML tools.
  * Extract 10 continuous sliding-window features: syscall frequencies, argument entropy, inter-syscall delta variance, read/write ratio, and fork frequency.
* **Week 5 (From-Scratch ML Anomaly Detector):**
  * Implement mathematical inference loops in pure Python/C (no scikit-learn in runtime path):
    1. Logistic Regression: $h_\theta(x) = \frac{1}{1 + e^{-\theta^T x}}$ with thresholding.
    2. Support Vector Machine with RBF kernel: $f(x) = \text{sign}\left(\sum \alpha_i y_i \exp(-\gamma \|x - x_i\|^2) + b\right)$.
    3. Gaussian Mixture Model (GMM): Log-likelihood scoring for unsupervised zero-day anomaly detection.
* **Week 6 (Real-Time Alert Dispatcher & Dashboard):**
  * Build `alert/manager.py` routing anomalies into SQLite with WAL mode enabled.
  * Construct lightweight security monitoring dashboard using Flask + Server-Sent Events (SSE).

---

### ❄️ **ACADEMIC FREEZE 1: Nov 9 – Nov 23, 2026 (UCP Midterm Exams)** ❄️

---

### 🏃 Sprint 3: Benchmarking against Standard Baselines (Weeks 7–9: Nov 24 – Dec 14)
* **Week 7 (Kernel Performance Benchmarking):**
  * Measure syscall throughput degradation in QEMU: Target $\le 5\%$ overhead vs. vanilla xv6.
  * Verify spinlock hold duration ($\le 1.0\,\mu\text{s}$ per audit entry).
* **Week 8 (ML Detector Precision/Recall Benchmarks):**
  * Generate 100,000 synthetic syscall traces (benign vs. fork-bomb, exfiltration, privilege escalation).
  * Benchmark against Scikit-Learn baseline: Verify that from-scratch inference matches within $10^{-5}$ numerical precision with Precision $\ge 0.85$ and Recall $\ge 0.90$.
* **Week 9 (End-to-End Latency Measurement):**
  * Profile end-to-end pipeline latency from kernel trap to dashboard alert: Benchmark target $\le 100\,\text{ms}$.

---

### ❄️ **ACADEMIC FREEZE 2: Dec 28, 2026 – Jan 15, 2027 (UCP Final Exams)** ❄️

---

### 🏃 Sprint 4: Adversarial Attack / Stress Testing & GDB Patching (Weeks 10–12: Dec 15–27, 2026 & Jan 16–22, 2027)
* **Week 10 (Kernel Race Condition Attack):**
  * Introduce CWE-362 (Race Condition) in `audit_log_append()` across multi-core QEMU (`CPUS=4`).
  * Attach GDB (`gdb-multiarch kernel/kernel`), capture corrupted `head`/`tail` pointers, and implement atomic spinlock remediation.
* **Week 11 (OWASP WSTG Full Pentest Audit):**
  * Execute 20 distinct tests from OWASP WSTG against the dashboard and alert ingestion API (Stored XSS, SQLi, Auth Bypass, Path Traversal).
  * Build exploit PoCs in `pentest/exploit_*.py` demonstrating successful attack execution.
* **Week 12 (Hardening & Remediation):**
  * Patch all web vulnerabilities: parameterize queries, enforce strict Content Security Policy (CSP), sanitize JSON output.
  * Re-run exploit scripts to prove that all vulnerabilities are completely mitigated.

---

### 🏃 Sprint 5: Documentation & Post-Mortem Writeup (Weeks 13–14: Jan 23 – Jan 31, 2027)
* **Week 13 (Formal Verification & Audit Documentation):**
  * Write `docs/S6_AUDIT_REPORT.md` (50+ pages): Mathematical derivations, kernel memory maps, GDB traces, benchmark graphs, and WSTG pentest report.
* **Week 14 (CI/CD Pipeline & Final Sign-Off):**
  * Establish GitHub Actions workflow `.github/workflows/ci.yml` building xv6-riscv and running automated ML accuracy tests.
  * Tag repository `v1.0-semester5-fusion-complete`.

---

## 🏗 System Architecture

```text
┌────────────────────────────────────────────────────────────────────────┐
│              AI-Driven OS-Level Security Monitor                        │
│                    (xv6 Kernel + Userspace ML Stack)                    │
├────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  ┌──────────────────────────────────────────────────────────────────┐ │
│  │                       xv6 Kernel Space                            │ │
│  │  ┌────────────────┐         ┌────────────────┐                   │ │
│  │  │  syscall.c     │────────▶│ audit_log.c    │                   │ │
│  │  │  (hook all     │         │ (ring buffer)  │                   │ │
│  │  │   syscalls)    │         │ 64KB fixed     │                   │ │
│  │  └────────────────┘         └───────┬────────┘                   │ │
│  │                                     │                             │ │
│  │                                     │ Netlink-style IPC           │ │
│  │                                     ▼                             │ │
│  │                          ┌────────────────────┐                   │ │
│  │                          │   /dev/auditlog    │                   │ │
│  │                          │  (char device)     │                   │ │
│  │                          └──────────┬─────────┘                   │ │
│  └─────────────────────────────────────┼──────────────────────────── │ │
│                                        │ read()                       │ │
│  ┌─────────────────────────────────────┼──────────────────────────── │ │
│  │                  xv6 Userspace      │                             │ │
│  │                                     ▼                             │ │
│  │                          ┌────────────────────┐                   │ │
│  │                          │  log_reader.c      │                   │ │
│  │                          │  (feature extract) │                   │ │
│  │                          └──────────┬─────────┘                   │ │
│  │                                     │ JSONL stream                │ │
│  │                                     ▼                             │ │
│  │                          ┌────────────────────────────┐           │ │
│  │                          │    ml_detector.py          │           │ │
│  │                          │  (trained anomaly model)   │           │ │
│  │                          │   - Logistic Regression    │           │ │
│  │                          │   - SVM (RBF kernel)       │           │ │
│  │                          │   - GMM (unsupervised)     │           │ │
│  │                          │  Outputs: alert score      │           │ │
│  │                          └──────────┬─────────────────┘           │ │
│  │                                     │                             │ │
│  │                                     ▼                             │ │
│  │                          ┌────────────────────────────┐           │ │
│  │                          │   alert_manager.py         │           │ │
│  │                          │  (threshold + action)      │           │ │
│  │                          │   - Log to SQLite          │           │ │
│  │                          │   - HTTP dashboard         │           │ │
│  │                          │   - Kill process (demo)    │           │ │
│  │                          └────────────────────────────┘           │ │
│  └─────────────────────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 🔬 The S++++++ Audit Protocol

### Stage 1: Derive — Mathematical Foundations
- **Logistic Regression Loss & Gradient:**
  $$J(\theta) = -\frac{1}{m}\sum_{i=1}^m \left[y^{(i)}\log(h_\theta(x^{(i)})) + (1-y^{(i)})\log(1-h_\theta(x^{(i)}))\right]$$
  $$\frac{\partial J}{\partial \theta_j} = \frac{1}{m}\sum_{i=1}^m (h_\theta(x^{(i)}) - y^{(i)})x_j^{(i)}$$
- **RBF Kernel SVM Dual Formulation:**
  $$\max_\alpha \sum_{i=1}^m \alpha_i - \frac{1}{2}\sum_{i,j=1}^m \alpha_i \alpha_j y^{(i)} y^{(j)} \exp(-\gamma \|x^{(i)} - x^{(j)}\|^2)$$
- **Gaussian Mixture Model Expectation-Maximization:**
  $$\gamma(z_{nk}) = \frac{\pi_k \mathcal{N}(x_n | \mu_k, \Sigma_k)}{\sum_{j=1}^K \pi_j \mathcal{N}(x_n | \mu_j, \Sigma_j)}$$

### Stage 2: Implement — Zero Wrappers
- xv6 kernel extension in C; from-scratch mathematical model inference in Python/C without scikit-learn in runtime serving path.

### Stage 3: Benchmark — Performance Targets
- Kernel syscall overhead $\le 5\%$.
- Model precision $\ge 0.85$, recall $\ge 0.90$, FPR $\le 5\%$.
- Pipeline end-to-end latency $\le 100\,\text{ms}$.

### Stage 4: Break & Patch
- Introduce ring buffer race condition (CWE-362), trace in multi-core GDB session, and apply atomic spinlocks.
- Execute OWASP WSTG 20-test pentest suite, document exploit PoCs, and remediate all findings.

---

## ✅ Exit Criteria Checklist
- [ ] Modified xv6 kernel boots cleanly with `/dev/auditlog` enabled.
- [ ] Syscall stream successfully feeds real-time ML anomaly detector.
- [ ] 3 attack vectors (fork-bomb, file exfiltration, privesc) detected with F1 $\ge 0.87$.
- [ ] GDB kernel trace session fully recorded and documented.
- [ ] WSTG pentest report complete with 20 findings exploited and remediated.
- [ ] GitHub Actions CI pipeline passes building kernel and testing ML pipeline.
- [ ] Git tagged `v1.0-semester5-fusion-complete`.