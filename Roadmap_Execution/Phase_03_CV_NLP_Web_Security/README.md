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
| **Stanford CS224N (NLP)** | Lectures 6–9 (RNN/LSTM/GRU, Bi-directional, Seq2Seq, Attention). Lectures 10–12 (Transformer, BERT, GPT, Scaling Laws). Lectures 13–15 (Question Answering, SQuAD, NER, Coreference). | Lectures 1–5 (Word vectors basics, SVD, GloVe - covered in earlier foundations). |
| **PortSwigger Academy (Advanced)** | Expert-tier labs: HTTP Request Smuggling (CL.TE/TE.CL), WebSocket Vulnerabilities, GraphQL, Server-Side Template Injection (Jinja2, Freemarker), Prototype Pollution, OAuth2/OIDC Flow Attacks. | Apprentice/Practitioner tier already completed in earlier phases. |
| **OWASP WSTG v4.2** | Full methodology application: WSTG-INFO (Recon), WSTG-ATHN/ATHZ (Auth), WSTG-INPV (XSS/SQLi/CMDi), WSTG-SESS (Session), WSTG-CLNT (CSRF/XSS/Clickjacking), WSTG-API (GraphQL/REST). | Reading methodology without executing tests against your own deployed app. |

---

## 📅 Flagship Milestone Schedule (12-Week Breakdown)

### 🏃 Sprint 1: Core Mathematical Derivation & Model Training (Weeks 1–3)
* **Week 1:** Derive ResNet gradient flow and train/evaluate the planned CV models on the selected dataset; export the production candidate.
* **Week 2:** Derive BERT masked-language-model loss; fine-tune QA/NER models and record reproducible evaluation metrics.
* **Week 3:** Build FastAPI inference infrastructure with ONNX Runtime, model versioning, A/B routing, canary deployment, and drift hooks.

### 🏃 Sprint 2: Application Implementation (Weeks 4–6)
* **Week 4:** React + TypeScript application with image upload, detection visualization, text analysis, OAuth2/JWT authentication.
* **Week 5:** PostgreSQL schema, Redis caching, audit logging, and per-user rate limiting.
* **Week 6:** Docker Compose deployment, public HTTPS deployment, Prometheus metrics, and Grafana dashboards.

### 🏃 Sprint 3: Benchmarking against Standard Baselines (Weeks 7–8)
* **Week 7:** Measure CV mAP, NLP F1, inference latency, and end-to-end API p99 latency against documented baselines.
* **Week 8:** Stress test the service under sustained load and perform memory/GPU stability testing.

### 🏃 Sprint 4: Authorized Security Testing & Remediation (Weeks 9–10)
* **Week 9:** Execute the WSTG methodology against the application's own deployed environment and document reproducible findings.
* **Week 10:** Patch findings, add regression tests, and re-run the security suite. Evaluate FGSM/PGD robustness on the ML components.

### 🏃 Sprint 5: Documentation & Release (Weeks 11–12)
* **Week 11:** Produce `PENTEST_REPORT.md` and `ADVERSARIAL_REPORT.md` with methodology, evidence, remediation, and accuracy/robustness trade-offs.
* **Week 12:** Finalize CI security regression tests and tag `v3.0-self-audited-app-complete`.

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
│    - CV/NLP inference endpoints                                │
│    - Model versioning + A/B testing                            │
│                                                                │
│  Infrastructure:                                               │
│    - Docker containers                                         │
│    - PostgreSQL (user data + audit logs)                      │
│    - Redis (session/cache store)                              │
│    - Nginx reverse proxy                                      │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

## 🔬 Engineering Verification Protocol

### Stage 1: Derive — Mathematical Foundations
- **ResNet Gradient Flow:**
  $$y = x + F(x) \implies \frac{\partial L}{\partial x} = \frac{\partial L}{\partial y}\left(1 + \frac{\partial F}{\partial x}\right)$$
- **BERT MLM Loss:**
  $$\mathcal{L} = -\sum_{i \in \text{masked}} \log \frac{\exp(w_i^T h_i)}{\sum_{j \in V} \exp(w_j^T h_i)}$$
- **Detection Objective:** document the selected detector's loss, evaluation metric, and thresholding assumptions.

### Stage 2: Implement
- Inference server uses ONNX Runtime where appropriate; training and security-relevant mechanisms are documented rather than hidden behind wrappers.
- Frontend/backend use standard frameworks because the application itself is the security-testing surface.

### Stage 3: Benchmark
| Metric | Target |
|--------|--------|
| CV mAP@0.5:0.95 | ≥ 0.45 |
| SQuAD 2.0 F1 | ≥ 0.88 |
| API p99 Latency | ≤ 200 ms |
| Sustained RPS | ≥ 500 |
| GPU Memory | Stable during defined soak test |

### Stage 4: Break & Patch
- Full WSTG v4.2 methodology applied to the owned application.
- Findings are reproduced, patched, and re-tested.
- Adversarial ML evaluation uses FGSM/PGD within the controlled project environment.

---

## ✅ Exit Criteria Checklist
- [ ] CV model meets the phase benchmark on the selected validation set.
- [ ] NLP model meets the phase benchmark on the selected evaluation set.
- [ ] Application deployed with HTTPS.
- [ ] WSTG audit complete with reproducible findings and verified remediation.
- [ ] Formal pentest report published.
- [ ] CI includes security regression tests.
- [ ] Git tagged `v3.0-self-audited-app-complete`.