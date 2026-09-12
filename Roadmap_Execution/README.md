[← Back to Root Master Roadmap](../README.md)

# Master Execution Hub: AI Systems Engineering × Offensive Security
**September 2026 – September 2030**

This is the execution layer for the canonical roadmap. The canonical curriculum and long-term phase intent live in `iausafali/MachineLearning/AI-Security-Roadmap`; this hub translates that plan into concrete projects, experiments, labs, benchmarks, and exit criteria.

## Executive Phase Index

| # | Phase | Timeline | Focus | Primary evidence |
|---|---|---|---|---|
| **00** | [Recall Sprint](Phase_00_Recall_Sprint/) | Sep 8–25, 2026 | Programming, CS, C/Linux foundations | Working systems utilities + debugging evidence |
| **01** | [Semester 5 Fusion](Phase_01_Semester_5_Fusion/) | Sep 26, 2026 – Jan 2027 | University ML/AI/OS/InfoSec/SE + security integration | xv6 instrumentation + ML detector + security evaluation |
| **02** | [Systems + Deep Learning](Phase_02_Systems_Deep_Learning/) | Feb–Apr 2027 | Deep learning + networking/Linux/Windows systems | Autodiff framework + TCP/NIDS integration |
| **03** | [CV/NLP + Web Security](Phase_03_CV_NLP_Web_Security/) | May–Jul 2027 | Vision, NLP, web security | Deployed CV/NLP application + authorized pentest report |
| **04** | [LLM + Binary Exploitation](Phase_04_LLM_Binary_Exploitation/) | Aug–Oct 2027 | Language modeling + assembly/exploitation | LLM implementation + controlled binary exploitation lab |
| **05** | [MLOps + Reverse Engineering](Phase_05_MLOps_Reverse_Engineering/) | Nov 2027–Jan 2028 | ML systems + RE | Serving/drift platform + blind binary analysis |
| **06** | [Agents + Enterprise Security](Phase_06_Agents_Enterprise_Security/) | Feb–Apr 2028 | Agents + AD/enterprise/cloud foundations | Agent security lab in owned AD environment |
| **07** | [FYP Integration](Phase_07_FYP_Integration/) | May–Jun 2028 | Research/FYP integration | Thesis-grade research artifact |
| **08** | [RL + Autonomous Security Agent](Phase_08_RL_Autonomous_Security_Agent/) | Jul–Dec 2028 | Deep RL + security testing | Sandboxed autonomous security-testing benchmark |
| **09** | [Formal Security + AI Red Team](Phase_09_Formal_Security_AI_RedTeam/) | Jan–Jun 2029 | Security theory + adversarial AI | Secure RAG + formal verification + red-team benchmark |
| **10** | [Research Reproductions](Phase_10_Research_Reproductions/) | Jul–Dec 2029 | ML/security research methodology | Six reproductions + ablations + divergence analysis |
| **11** | [Original Invention](Phase_11_Original_Invention/) | Jan–Sep 2030 | Original AI × security research | Novel system + rigorous evaluation + publication/release |

## Canonical alignment

The folder structure intentionally consolidates the canonical 13 conceptual phases into 12 execution folders. The complete mapping and restored canonical resources are documented in [`CANONICAL_ALIGNMENT.md`](../CANONICAL_ALIGNMENT.md).

**Canonical resources that must remain in the execution plan:**

- MIT 18.06 Linear Algebra
- MIT 18.05 Probability & Statistics
- **MIT 18.065 Matrix Methods in Data Analysis**
- Stanford CS229
- Deep Learning Specialization
- fast.ai
- Stanford CS231n
- Stanford CS224N
- Stanford CS336
- Stanford CS229S
- **Made With ML**
- **DeepLearning.AI Machine Learning in Production**
- Hugging Face LLM Course
- Hugging Face Agents Course
- **Stanford CS229T**
- Stanford CS224R
- Stanford CS144
- CS50 Cybersecurity
- MIT 6.1600
- PortSwigger Web Security Academy
- OWASP WSTG
- pwn.college
- OpenSecurityTraining2 + Ghidra
- MITRE ATT&CK

## Engineering verification protocol

Every flagship project should progress through:

1. **Derive** relevant mathematics, systems logic, or security invariants.
2. **Implement** the core mechanism and understand the abstractions being used.
3. **Benchmark** against an independent baseline with quantitative metrics.
4. **Break** the implementation in an owned, intentionally vulnerable, or explicitly authorized environment.
5. **Patch** the discovered failure and verify the fix.
6. **Document** the architecture, methods, evidence, limitations, and results.

This is a verification standard, not a requirement to avoid all libraries. High-level frameworks are appropriate when the learning objective is systems integration; first-principles implementation is required when the phase explicitly targets understanding of the underlying mechanism.

## Academic integration

University coursework is the academic floor, not a second copy of the roadmap. When a university subject overlaps a roadmap topic, use coursework for required academic coverage and use the execution project to push beyond it. Avoid redundant re-learning of material that can already be demonstrated.

During university periods, maintain the planned emphasis on AI, mathematics, and systems while keeping a deliberate security/networking lane. During breaks, deepen the current specialty. After graduation, converge AI systems/research and security/research toward the final research phase.

## Compute policy

Prefer local CPU/WSL2 and free resources. Rent cloud CPU/GPU/RAM only when the workload genuinely requires it. The phase READMEs contain detailed assumptions and budget ranges.

## Security boundary

All offensive-security work must remain inside owned, intentionally vulnerable, or explicitly authorized environments. Never test third-party systems without authorization.
