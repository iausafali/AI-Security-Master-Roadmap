# Phase 3: CV/NLP + Web Security Depth — Course Resources & Certificate Audit

**Timeline:** May – July 2027 (3 months)  
**Objective:** Applied perception/language models; security returns to full pentest methodology.  
**Balance:** 70% AI / 30% security.  
**Compute:** Colab / Codespaces GPU-lite — $20-40/mo.  
**Freeze Window:** None (summer).

---

## 📚 Resource Index

### 1. Stanford CS231n — Convolutional Neural Networks for Visual Recognition
- **Primary URL:** https://cs231n.stanford.edu/
- **Lecture Videos (Spring 2017):** https://www.youtube.com/playlist?list=PL3FW7Lu3i5JvHM8ljYj-zLfQRF3EO8sYv
- **Lecture Notes (HTML):** https://cs231n.github.io/
- **Assignments (2023/2024):** https://cs231n.stanford.edu/assignments.html
- **PyTorch Tutorial:** https://github.com/kuleshov/cs231n-assignments
- **Project Gallery:** https://cs231n.stanford.edu/reports/2023.html

**Local Download:**
```bash
# Lecture videos
yt-dlp -f "bestvideo+bestaudio" --write-sub --sub-lang en \
  -o "Roadmap_Execution/Phase_03_CV_NLP_Web_Security/Courses/Assets/CS231n/lectures/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PL3FW7Lu3i5JvHM8ljYj-zLfQRF3EO8sYv"

# Assignment specs (clone from kuleshov repo)
git clone https://github.com/kuleshov/cs231n-assignments.git \
  "Roadmap_Execution/Phase_03_CV_NLP_Web_Security/Courses/Assets/CS231n/assignments"
```

**Free Certificate Audit:**
- ❌ **Stanford CS231n does NOT offer certificates** (university course).
- **Portfolio Evidence:** Complete all 3 assignments (Q1: CNN, Q2: ResNet, Q3: Detection/Captioning) with ≥95% autograder score; publish trained models + writeups.

---

### 2. Stanford CS224N — Natural Language Processing with Deep Learning
- **Primary URL:** https://web.stanford.edu/class/cs224n/
- **Lecture Videos (Winter 2022):** https://www.youtube.com/playlist?list=PLoROMvodv4rOhcuXMZkNm7j3fVwBBY42z
- **Lecture Notes:** https://web.stanford.edu/class/cs224n/syllabus.html
- **Assignments (Default Final Project):** https://web.stanford.edu/class/cs224n/assignments.html
- **PyTorch Implementation Repo:** https://github.com/stanfordnlp/cs224n

**Local Download:**
```bash
# Lecture videos
yt-dlp -f "bestvideo+bestaudio" --write-sub --sub-lang en \
  -o "Roadmap_Execution/Phase_03_CV_NLP_Web_Security/Courses/Assets/CS224N/lectures/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PLoROMvodv4rOhcuXMZkNm7j3fVwBBY42z"

# Assignments
git clone https://github.com/stanfordnlp/cs224n.git \
  "Roadmap_Execution/Phase_03_CV_NLP_Web_Security/Courses/Assets/CS224N/assignments"
```

**Free Certificate Audit:**
- ❌ **Stanford CS224N does NOT offer certificates** (university course).
- **Portfolio Evidence:** Complete default final project (e.g., dependency parsing, NER, or machine translation); publish trained model + evaluation.

---

### 3. PortSwigger Web Security Academy (Advanced)
- **Primary URL:** https://portswigger.net/web-security
- **Advanced Topics:** Business Logic, HTTP Request Smuggling, WebSocket Vulnerabilities, GraphQL, Prototype Pollution, Server-Side Template Injection (SSTI), OAuth2/OIDC, JWT, Deserialization.
- **All Labs:** https://portswigger.net/web-security/all-labs

**Free Certificate Audit:**
- Same as Phase 1 — complete remaining advanced labs (Apprentice → Practitioner → Expert tiers); 100% completion visible on public profile.

---

### 4. OWASP Web Security Testing Guide (WSTG) — Full Application
- **Primary URL:** https://owasp.org/www-project-web-security-testing-guide/
- **Full Checklist:** 91 tests across 12 categories
- **Target:** Your own deployed CV/NLP web application

**Free Certificate Audit:**
- ❌ No certificate — methodology only.
- **Portfolio Evidence:** Full WSTG-compliant pentest report against your deployed application.

---

## 🎯 Phase 3 Certificate Summary

| Course | Free Verified Certificate? | Evidence |
|--------|---------------------------|----------|
| CS231n | ❌ NO | Assignments + trained models |
| CS224N | ❌ NO | Final project + model |
| PortSwigger (Advanced) | Public Profile Only | 100% completion profile |
| WSTG | ❌ NO | Formal pentest report |