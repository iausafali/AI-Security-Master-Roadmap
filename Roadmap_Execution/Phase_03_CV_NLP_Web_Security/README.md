[← Back to Master Execution Table](../../README.md)

# Phase 3: CV/NLP + Web Security Depth — Self-Audited CV/NLP Web Application

**Timeline:** May – July 2027 (~12 Weeks)  
**Compute Tier:** Colab / Codespaces GPU-lite — $20–40/mo  
**Project Directory:** `Project_Audited_CV_NLP_App/`  
**No Academic Freezes** (summer).

---

## ⚡ The 30/70 Efficiency Rule (Fluff Filter)

| Course | ▶️ MUST WATCH (Core Theory & Depth) | ❌ SKIP / FAST-FORWARD |
|--------|------------------------------------|------------------------|
| **Stanford CS231n (CV)** | Lectures 5–8 (CNN Backprop, Pooling, Architecture Design). Lectures 9–11 (ResNet, DenseNet, Transfer Learning). Lectures 12–14 (Object Detection: R-CNN, YOLO, Faster R-CNN). Lectures 15–16 (Segmentation: FCN, Mask R-CNN). | Lectures 1–4 (Image classification basics, kNN, SVM, basic neural nets - covered in CS229/Deep Learning Spec). |
| **Stanford CS224N (NLP)** | Lectures 6–9 (RNN/LSTM/GRU, Bi-directional, Seq2Seq, Attention). Lectures 10–12 (Transformer, BERT, GPT, Scaling Laws). Lectures 13–15 (Question Answering, SQuAD, NER, Coreference). | Lectures 1–5 (Word vectors basics, SVD, GloVe - covered in CS231n/Linear Algebra). |
| **PortSwigger Academy (Advanced)** | Expert-tier labs: HTTP Request Smuggling (CL.TE/TE.CL), WebSocket Vulnerabilities, GraphQL, Server-Side Template Injection (Jinja2, Freemarker), Prototype Pollution, OAuth2/OIDC Flow Attacks. | Apprentice/Practitioner tier (already completed in Phase 1). |
| **OWASP WSTG v4.2** | Full methodology application: WSTG-INFO (Recon), WSTG-ATHN/ATHZ (Auth), WSTG-INPV (XSS/SQLi/CMDi), WSTG-SESS (Session), WSTG-CLNT (CSRF/XSS/Clickjacking), WSTG-API (GraphQL/REST). | Reading the methodology without executing tests against your own deployed app. |

---

## 📅 Flagship Milestone Schedule (12-Week Breakdown)

### 🏃 Sprint 1: Core Mathematical Derivation & Model Training (Weeks 1–3: May 1 – May 21)
* **Week 1 (CV Model Training — From-Scratch ResNet/YOLO):**
  * Derive ResNet bottleneck block gradient flow: $\frac{\partial L}{\partial x} = \frac{\partial L}{\partial F(x)} + \frac{\partial L}{\partial x}$ (identity skip gradient preservation).
  * Train ResNet-50 on COCO 2017 detection using PyTorch (Phase 2 autodiff not GPU-optimized yet) targeting mAP $\ge 0.45$ on val2017.
  * Export to ONNX for production serving.
* **Week 2 (NLP Model Training — BERT Fine-Tuning):**
  * Derive BERT masked language model loss: $\mathcal{L}_{\text{MLM}} = -\sum \log P(x_i | x_{\backslash i})$.
  * Fine-tune `bert-base-uncased` on SQuAD 2.0 for QA (F1 $\ge 0.88$) and CoNLL-2003 for NER (F1 $\ge 0.92$).
  * Export to ONNX / TensorRT for inference optimization.
* **Week 3 (Model Serving Infrastructure):**
  * Build FastAPI inference server with ONNX Runtime (CPU + GPU modes).
  * Implement model versioning: A/B routing, canary deployment, drift detection hooks.

---

### 🏃 Sprint 2: Low-Level Implementation — Zero Wrappers (Weeks 4–6: May 22 – Jun 11)
* **Week 4 (Frontend Application & Auth):**
  * React + TypeScript + TailwindCSS SPA with image upload (drag-drop → canvas preview → bounding box overlay).
  * Text analysis panel with entity highlighting and sentiment visualization.
  * OAuth2 + JWT authentication flow (Auth0 or self-hosted OIDC).
* **Week 5 (Backend API & Database):**
  * PostgreSQL schema: users, predictions, model_versions, audit_logs.
  * Redis caching layer for frequent inference results (TTL 1hr).
  * Rate limiting: token bucket per user tier.
* **Week 6 (Deployment & Observability):**
  * Docker Compose stack: nginx → FastAPI → Redis → PostgreSQL.
  * Deploy to Hugging Face Spaces / Railway / Render with public HTTPS.
  * Prometheus metrics + Grafana dashboards (latency p50/p99, error rates, GPU utilization).

---

### 🏃 Sprint 3: Benchmarking against Standard Baselines (Weeks 7–8: Jun 12 – Jun 25)
* **Week 7 (Model Accuracy & Inference Benchmarks):**
  * CV: mAP@0.5:0.95 on COCO val2017 $\ge 0.45$; inference latency $\le 80$ms (batch=1, GPU).
  * NLP: SQuAD 2.0 dev F1 $\ge 0.88$; NER CoNLL F1 $\ge 0.92$; latency $\le 40$ms.
  * API: End-to-end p99 latency $\le 200$ms under 100 RPS load test (`wrk`).
* **Week 8 (Load & Stress Testing):**
  * Sustained 500 RPS for 10 minutes with $\le 0.1\%$ error rate.
  * GPU memory stability: no OOM over 24hr soak test.

---

### 🏃 Sprint 4: Adversarial Attack / Stress Testing & GDB Patching (Weeks 9–10: Jun 26 – Jul 9)
* **Week 9 (OWASP WSTG Full Application Pentest):**
  * Execute **all 91 WSTG tests** against deployed application.
  * Document findings with exploit PoCs in `pentest/WSTG_REPORT.md`:
    * WSTG-INPV-01: Reflected XSS in search query parameter.
    * WSTG-INPV-05: SQL Injection in model version filter.
    * WSTG-ATHN-02: JWT algorithm confusion attack.
    * WSTG-CLNT-03: CSRF on model retraining endpoint.
    * WSTG-API-01: GraphQL introspection + field suggestion abuse.
    * (Minimum 10 critical/high findings required)
* **Week 10 (Remediation & Hardening):**
  * Patch all findings: CSP headers, parameterized queries, JWT RS256 enforcement, SameSite cookies, GraphQL depth limiting.
  * Re-run exploit scripts to confirm mitigation.
  * Adversarial ML: FGSM/PGD attacks on image upload (perturb images to evade detection); measure robustness drop.

---

### 🏃 Sprint 5: Documentation & Post-Mortem Writeup (Weeks 11–12: Jul 10 – Jul 23)
* **Week 11 (Formal Artifacts):**
  * `PENTEST_REPORT.md`: Executive summary, methodology, 91-test matrix, exploit PoCs, remediation evidence.
  * `ADVERSARIAL_REPORT.md`: ML attack results, defense effectiveness, accuracy-robustness tradeoff curves.
* **Week 12 (Final Sign-Off):**
  * Security regression test suite in CI (`pytest-pentest` plugin).
  * Tag `v3.0-self-audited-app-complete`.

---

## 🏗 System Architecture

```text
┌────────────────────────────────────────────────────────────────┐
│         Self-Audited CV/NLP Production Web Application         │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  Frontend: React + TailwindCSS                                 │
│    - Image upload → Object detection visualization            │
│    - Text input → Sentiment analysis + entity extraction      │
│    - User authentication (OAuth2 + JWT)                        │
│                                                                │
│  Backend API: FastAPI / Flask                                  │
│    - POST /api/detect → CV model inference                    │
│    - POST /api/analyze → NLP model inference                  │
│    - Model versioning + A/B testing                           │
│                                                                │
│  Models (deployed from Phase 3 training):                      │
│    - CV: ResNet-50 + YOLO for object detection                │
│    - NLP: BERT-based sentiment + NER                          │
│                                                                │
│  Infrastructure:                                               │
│    - Docker containers                                         │
│    - PostgreSQL (user data + audit logs)                      │
│    - Redis (session store)                                    │
│    - Nginx reverse proxy                                      │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

## 🔬 The S++++++ Audit Protocol

### Stage 1: Derive — Mathematical Foundations
- **ResNet Gradient Flow:**
  $$
  y = x + F(x) \implies \frac{\partial L}{\partial x} = \frac{\partial L}{\partial y} \left(1 + \frac{\partial F}{\partial x}\right)
  $$
- **BERT MLM Loss:**
  $$
  \mathcal{L} = -\sum_{i \in \text{masked}} \log \frac{\exp(w_i^T h_i)}{\sum_{j \in V} \exp(w_j^T h_i)}
  $$
- **YOLOv3 Loss (Multi-Task):**
  $$
  \mathcal{L} = \lambda_{\text{coord}} \sum \text{CIoU} + \lambda_{\text{obj}} \sum \text{BCE}_{\text{obj}} + \lambda_{\text{cls}} \sum \text{CE}_{\text{cls}}
  $$

### Stage 2: Implement — Zero Wrappers (where possible)
- Inference server uses ONNX Runtime (industry standard) but training from-scratch logic documented.
- Frontend/Backend built with standard frameworks (security surface is the target, not the framework).

### Stage 3: Benchmark — Performance Targets
| Metric | Target |
|--------|--------|
| COCO mAP@0.5:0.95 | $\ge 0.45$ |
| SQuAD 2.0 F1 | $\ge 0.88$ |
| API p99 Latency | $\le 200$ms |
| Sustained RPS | $\ge 500$ |
| GPU Memory (24hr) | Stable, no OOM |

### Stage 4: Break & Patch
- Full WSTG v4.2 audit (91 tests) against own deployed application.
- Minimum 10 critical/high findings documented with exploit PoCs.
- All findings patched and re-verified.
- Adversarial ML evaluation (FGSM/PGD) on vision models.

---

## ✅ Exit Criteria Checklist
- [ ] CV model achieves mAP $\ge 0.45$ on COCO val2017.
- [ ] NLP model achieves F1 $\ge 0.88$ on SQuAD 2.0 dev.
- [ ] Application deployed publicly with HTTPS.
- [ ] WSTG audit complete: $\ge 10$ findings exploited, patched, re-tested.
- [ ] Formal pentest report (40+ pages) published to GitHub.
- [ ] CI includes security regression tests.
- [ ] Git tagged `v3.0-self-audited-app-complete`.