# AI Systems Engineering × Offensive Security

## Master Execution Roadmap | September 2026 → September 2030

This repository is the **expanded execution layer** for the canonical four-year roadmap.

- **Canonical plan:** [`iausafali/MachineLearning/AI-Security-Roadmap`](https://github.com/iausafali/MachineLearning/tree/main/AI-Security-Roadmap)
- **Execution hub:** [`Roadmap_Execution/`](Roadmap_Execution/)
- **Canonical alignment:** [`CANONICAL_ALIGNMENT.md`](CANONICAL_ALIGNMENT.md)

The canonical roadmap defines the long-term sequence, resource spine, time allocation, and learning method. This repository turns that plan into phase-level projects, implementation targets, experiments, security labs, benchmarks, and documentation requirements.

## Principles

### Problem-first learning

`Attempt → struggle → diagnose the missing piece → learn only what is missing → implement → reattempt → modify → benchmark → document`

### Evidence over completion

A course is not complete because lectures were watched. Each phase must produce concrete evidence of independent capability: implementation, experiment, benchmark, security lab record, research artifact, or technical write-up.

### Phase verification standard

Every flagship project follows the same engineering loop:

1. **Derive** the relevant mathematics, systems logic, or security model.
2. **Implement** the core mechanism rather than hiding it behind a high-level wrapper.
3. **Benchmark** against an independent baseline with stated metrics.
4. **Break** the system inside an owned or explicitly authorized environment.
5. **Patch** the discovered failure and re-test the fix.
6. **Document** the architecture, evidence, limitations, and results.

### Time architecture

- University periods: approximately **70% AI / mathematics / systems** and **30% security / networking**.
- Breaks: shift toward the current deep-dive specialty.
- Post-graduation: converge toward approximately **50% AI systems / research** and **50% security / research**.

## Execution phases

The execution repository uses 12 folders (`00`–`11`) while the canonical roadmap uses 13 conceptual phases (`0`–`12`). This is intentional: the execution folders consolidate adjacent canonical material where that produces a cleaner project sequence. The exact mapping is documented in [`CANONICAL_ALIGNMENT.md`](CANONICAL_ALIGNMENT.md).

| Execution | Canonical | Timeline | Flagship focus |
|---|---|---|---|
| 00 | 0 | Sep 2026 | CS/programming reactivation + secure systems utilities |
| 01 | 1–2 | Sep 2026 – Jan 2027 | Semester-integrated ML/AI + xv6 + security foundation |
| 02 | 3 | Feb – Apr 2027 | Deep learning + networking + autodiff/NIDS |
| 03 | 4 | May – Jul 2027 | CV/NLP + advanced web security |
| 04 | 5 | Aug – Oct 2027 | Language modeling + binary exploitation |
| 05 | 6 | Nov 2027 – Jan 2028 | MLOps + reverse engineering |
| 06 | 7 | Feb – Apr 2028 | Agents + enterprise identity/security |
| 07 | 8 | May – Jun 2028 | FYP/research integration |
| 08 | 9 | Jul – Dec 2028 | Deep RL + autonomous security testing |
| 09 | 10 | Jan – Jun 2029 | Formal security + AI red teaming |
| 10 | 11 | Jul – Dec 2029 | Research reproductions + ML theory |
| 11 | 12 | Jan – Sep 2030 | Original AI/security research + invention |

> **Date authority:** the canonical roadmap in `iausafali/MachineLearning` controls long-term phase boundaries. Detailed execution schedules may contain catch-up or semester-specific planning notes, but they must not change the canonical curriculum without an explicit roadmap revision.

## Resource spine

### AI, mathematics, and systems

- [CS50x](https://cs50.harvard.edu/x/)
- [MIT 6.006 Algorithms](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/)
- [MIT 18.06 Linear Algebra](https://ocw.mit.edu/courses/18-06-linear-algebra-spring-2010/)
- [MIT 18.05 Probability & Statistics](https://ocw.mit.edu/courses/18-05-introduction-to-probability-and-statistics-spring-2014/)
- [MIT 18.065 Matrix Methods in Data Analysis](https://ocw.mit.edu/courses/18-065-matrix-methods-in-data-analysis-spring-2018/)
- [Stanford CS229](https://cs229.stanford.edu/)
- [Deep Learning Specialization](https://www.coursera.org/specializations/deep-learning)
- [fast.ai](https://course.fast.ai/)
- [Stanford CS231n](https://cs231n.stanford.edu/)
- [Stanford CS224N](https://web.stanford.edu/class/cs224n/)
- [Stanford CS336](https://cs336.stanford.edu/)
- [Stanford CS229S](https://cs229s.stanford.edu/)
- [Made With ML](https://madewithml.com/)
- [Machine Learning in Production](https://www.coursera.org/learn/machine-learning-in-production)
- [Hugging Face LLM Course](https://huggingface.co/learn/llm-course)
- [Hugging Face Agents Course](https://huggingface.co/agents-course)
- [Stanford CS224R](https://cs224r.stanford.edu/)
- [Stanford CS229T](https://cs229t.stanford.edu/)

### Security

- [Stanford CS144](https://cs144.github.io/)
- [CS50 Cybersecurity](https://cs50.harvard.edu/cybersecurity/)
- [MIT 6.1600](https://www.eecs.mit.edu/academics/curriculum/catalog/courses/6-1600/)
- [PortSwigger Web Security Academy](https://portswigger.net/web-security)
- [OWASP WSTG](https://owasp.org/www-project-web-security-testing-guide/)
- [pwn.college](https://pwn.college/)
- [OpenSecurityTraining2](https://opensecuritytraining.info/)
- [Ghidra](https://ghidra-sre.org/)
- [Hack The Box Academy](https://academy.hackthebox.com/)
- [AWS Skill Builder](https://skillbuilder.aws/)
- [MITRE ATT&CK](https://attack.mitre.org/)

## Compute philosophy

Use local CPU/WSL2 and free resources whenever they are sufficient. Rent cloud resources only when memory or GPU capacity is genuinely required. The phase READMEs contain the detailed compute assumptions and budget ranges.

## Security boundary

All offensive-security experimentation stays inside owned, intentionally vulnerable, or explicitly authorized environments. Do not test third-party systems without authorization, and do not use random malware samples as practice targets.

## Start here

Read [`CANONICAL_ALIGNMENT.md`](CANONICAL_ALIGNMENT.md), then open [`Roadmap_Execution/README.md`](Roadmap_Execution/README.md) and the current phase directory.