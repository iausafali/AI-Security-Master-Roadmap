# Phase 1: Semester 5 Fusion — Course Resources & Certificate Audit

**Timeline:** September 28, 2026 – January 2027 (~4 months)  
**Objective:** University transcript convergence — ML, AI, OS, InfoSec, SE all in one semester.  
**Balance:** ~60% university-anchored depth / 40% fusion build.  
**Compute:** Local CPU/WSL2 + GitHub Codespaces — $0-10/mo.  
**Freeze Window:** Hard 14-day freeze before UCP midterms (~mid-Nov) and finals (~mid/late Jan).

---

## 📚 Resource Index

### 1. Stanford CS229 — Machine Learning
- **Primary URL:** https://cs229.stanford.edu/
- **Lecture Videos (Autumn 2018):** https://www.youtube.com/playlist?list=PLoROMvodv4rMiGQp3WXShtMGgzqpfVfbU
- **Problem Sets (2024):** https://cs229.stanford.edu/problem-sets/
- **Syllabus:** https://cs229.stanford.edu/syllabus-autumn2024.html
- **Lecture Notes:** https://cs229.stanford.edu/main_notes.pdf
- **Section Notes:** https://cs229.stanford.edu/sections2024.html
- **Projects Archive:** https://cs229.stanford.edu/projects.html

**Key Algorithms Covered:**
- Supervised Learning: Linear Regression, Logistic Regression, GDA, Naive Bayes, SVM, Neural Networks
- Unsupervised Learning: K-Means, GMM, EM, PCA, ICA
- Learning Theory: Bias/Variance, VC Dimension, PAC Learning
- Reinforcement Learning: MDP, Value Iteration, Policy Iteration, Q-Learning

**Local Download:**
```bash
# Lecture videos
yt-dlp -f "bestvideo+bestaudio" --write-sub --sub-lang en \
  -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/CS229/lectures/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PLoROMvodv4rMiGQp3WXShtMGgzqpfVfbU"

# Lecture notes (official PDF)
curl -L https://cs229.stanford.edu/main_notes.pdf \
  -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/CS229/cs229_lecture_notes.pdf"

# Problem sets (scrape from site)
mkdir -p "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/CS229/psets"
for i in {0..4}; do
  curl -L "https://cs229.stanford.edu/ps$i/ps$i.pdf" \
    -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/CS229/psets/ps$i.pdf" 2>/dev/null || echo "PS$i unavailable"
done
```

**Free Certificate Audit:**
- ❌ **Stanford CS229 does NOT offer free certificates** (on-campus course; Coursera version is paid)
- **Alternative:** Stanford School of Engineering posts lecture recordings publicly but no credential
- **Portfolio Evidence:** Implement all PS algorithms from scratch; publish repo with test suites

---

### 2. Berkeley CS188 — Introduction to Artificial Intelligence
- **Primary URL:** https://inst.eecs.berkeley.edu/~cs188/
- **Current Semester (Fall 2024):** https://inst.eecs.berkeley.edu/~cs188/fa24/
- **Lecture Videos (Fall 2021):** https://www.youtube.com/playlist?list=PLsOUugYMBBJENfZ3XAToMsg44W7LeUVhF
- **EdX Archive (CS188.1x):** https://courses.edx.org/courses/BerkeleyX/CS188.1x-4/1T2015/ (no longer active enrollment)
- **Project Specs (Pacman AI):** https://inst.eecs.berkeley.edu/~cs188/fa24/projects/
- **Lecture Slides:** https://inst.eecs.berkeley.edu/~cs188/fa24/schedule/
- **Practice Exams:** https://inst.eecs.berkeley.edu/~cs188/fa24/exams/

**Key Topics:**
- Search: DFS, BFS, UCS, A*, Heuristics
- CSP: Backtracking, Arc Consistency, Local Search
- Adversarial Search: Minimax, Alpha-Beta Pruning, Expectimax
- MDPs & RL: Value Iteration, Policy Iteration, Q-Learning, Approximate Q-Learning
- Probabilistic Reasoning: Bayes Nets, Inference, HMMs, Particle Filtering
- ML Basics: Perceptron, Neural Nets (lightweight intro)

**Local Download:**
```bash
# Lecture videos (Fall 2021 full playlist)
yt-dlp -f "bestvideo+bestaudio" --write-sub --sub-lang en \
  -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/CS188/lectures/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PLsOUugYMBBJENfZ3XAToMsg44W7LeUVhF"

# Project specs (Pacman framework)
git clone https://github.com/berkeleydeeprlcourse/homework_fall2021.git \
  "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/CS188/pacman_projects" || \
curl -L https://inst.eecs.berkeley.edu/~cs188/fa24/assets/projects/search.zip \
  -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/CS188/projects.zip"

# Lecture slides (scrape current semester)
mkdir -p "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/CS188/slides"
for i in {1..25}; do
  curl -L "https://inst.eecs.berkeley.edu/~cs188/fa24/assets/slides/lec$i.pdf" \
    -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/CS188/slides/lec$i.pdf" 2>/dev/null || echo "Lecture $i unavailable"
done
```

**Free Certificate Audit:**
- ❌ **Berkeley CS188 does NOT offer certificates** (on-campus course)
- ❌ **EdX CS188.1x is archived** (no new enrollments; old certificates expired)
- **Portfolio Evidence:** Complete all 5 Pacman projects with autograder scores; publish solutions + writeup

---

### 3. MIT 6.1810 (xv6) — Operating System Engineering
- **Primary URL:** https://pdos.csail.mit.edu/6.1810/2025/
- **xv6 Book (RISC-V):** https://pdos.csail.mit.edu/6.1810/2025/xv6/book-riscv-rev4.pdf
- **xv6 Source Code:** https://github.com/mit-pdos/xv6-riscv
- **Labs:** https://pdos.csail.mit.edu/6.1810/2025/schedule.html
- **Lecture Videos (2020):** https://www.youtube.com/playlist?list=PLTsf9UeqkReZHXWY9yJvTwLJWYYPcKEqK (unofficial recordings)
- **Official Lecture Notes:** https://pdos.csail.mit.edu/6.1810/2025/lec/
- **Piazza (read-only archive):** https://piazza.com/mit/spring2021/6s081 (requires signup)

**Key Labs (11 total):**
1. Utilities (system calls)
2. System calls (kernel entry)
3. Page tables (VM internals)
4. Traps (interrupts & exceptions)
5. Lazy allocation (on-demand paging)
6. Copy-on-write (fork optimization)
7. Multithreading (user-level threads)
8. Locks (kernel synchronization)
9. File system (inode cache, logging)
10. mmap (memory-mapped files)
11. Network driver (E1000 NIC)

**Local Download:**
```bash
# Clone xv6 source
git clone https://github.com/mit-pdos/xv6-riscv.git \
  "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/MIT_6.1810/xv6-riscv"

# xv6 book PDF
curl -L https://pdos.csail.mit.edu/6.1810/2025/xv6/book-riscv-rev4.pdf \
  -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/MIT_6.1810/xv6_book.pdf"

# Lecture notes (HTML to PDF conversion)
mkdir -p "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/MIT_6.1810/lectures"
for i in {1..24}; do
  curl -L "https://pdos.csail.mit.edu/6.1810/2025/lec/l-$i.txt" \
    -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/MIT_6.1810/lectures/lec$i.txt" 2>/dev/null || echo "Lecture $i unavailable"
done

# Unofficial lecture videos (2020 recordings)
yt-dlp -f "bestvideo+bestaudio" --write-sub --sub-lang en \
  -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/MIT_6.1810/lectures/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PLTsf9UeqkReZHXWY9yJvTwLJWYYPcKEqK"
```

**Free Certificate Audit:**
- ❌ **MIT 6.1810 does NOT offer certificates** (on-campus course, no OCW equivalent)
- **Portfolio Evidence:** Complete all 11 labs with passing tests; fork xv6 repo with custom kernel extension (Phase 1 project integration)

---

### 4. PortSwigger Web Security Academy
- **Primary URL:** https://portswigger.net/web-security
- **All Learning Paths:** https://portswigger.net/web-security/all-topics
- **Labs (Interactive):** https://portswigger.net/web-security/all-labs
- **Cheat Sheets:** https://portswigger.net/web-security/cheat-sheet
- **Video Tutorials:** https://portswigger.net/web-security/learning-path (embedded in lessons)

**Core Vulnerability Classes (20 topics):**
- SQL Injection, XSS, CSRF, Clickjacking, CORS
- XXE, SSRF, Path Traversal, Command Injection, Deserialization
- Authentication, Session Management, Access Control
- Business Logic, HTTP Request Smuggling, OAuth, JWT
- WebSockets, GraphQL, SSTI, Prototype Pollution

**Each Topic Structure:**
- Theory lesson → 5-15 labs (Apprentice → Practitioner → Expert tiers)
- All labs run in-browser (Burp Suite Community Edition sufficient)

**Local Archive:**
```bash
# Clone PortSwigger learning resources (community repo mirror)
git clone https://github.com/botesjuan/Burp-Suite-Certified-Practitioner-Exam-Study.git \
  "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/PortSwigger/study_guide" || \
mkdir -p "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/PortSwigger"

# Download cheat sheet PDF (print page as PDF)
curl -L https://portswigger.net/web-security/cheat-sheet \
  -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/PortSwigger/cheat_sheet.html"
```

**Free Certificate Audit:**
- ✅ **Burp Suite Certified Practitioner (BSCP) exam is PAID ($99 USD, one attempt)**
- ✅ **BUT: All 200+ labs are FREE to complete without exam registration**
- **Free Credential Path:**
  1. Complete all labs (track progress at https://portswigger.net/users/yourusername)
  2. Screenshot final lab completion dashboard showing "100% complete"
  3. Export lab writeups to GitHub repo
  4. **No free certificate, but verifiable public profile**: https://portswigger.net/users/yourusername shows completion %
- **Paid BSCP Certificate (optional):** Exam is 4 hours, practical web pentest in browser — consider post-Phase 3

---

### 5. OWASP Web Security Testing Guide (WSTG)
- **Primary URL:** https://owasp.org/www-project-web-security-testing-guide/
- **WSTG v4.2 (Latest):** https://github.com/OWASP/wstg/releases/tag/v4.2
- **Full HTML Version:** https://owasp.org/www-project-web-security-testing-guide/stable/
- **PDF Download:** https://github.com/OWASP/wstg/releases/download/v4.2/wstg-v4.2.pdf
- **Testing Checklist:** https://github.com/OWASP/wstg/blob/master/checklist/WSTG-Checklist.xlsx

**Structure (12 Sections, 91 Tests):**
- 4.1: Information Gathering (10 tests)
- 4.2: Configuration & Deployment (7 tests)
- 4.3: Identity Management (5 tests)
- 4.4: Authentication (9 tests)
- 4.5: Authorization (4 tests)
- 4.6: Session Management (9 tests)
- 4.7: Input Validation (19 tests)
- 4.8: Error Handling (2 tests)
- 4.9: Cryptography (4 tests)
- 4.10: Business Logic (9 tests)
- 4.11: Client-Side (13 tests)
- 4.12: API Testing (1 test — GraphQL/REST)

**Local Download:**
```bash
# WSTG full repository
git clone https://github.com/OWASP/wstg.git \
  "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/OWASP_WSTG"

# PDF version
curl -L https://github.com/OWASP/wstg/releases/download/v4.2/wstg-v4.2.pdf \
  -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/OWASP_WSTG/wstg-v4.2.pdf"

# Testing checklist
curl -L https://github.com/OWASP/wstg/raw/master/checklist/WSTG-Checklist.xlsx \
  -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/OWASP_WSTG/WSTG-Checklist.xlsx"
```

**Free Certificate Audit:**
- ❌ **OWASP does NOT offer certificates for WSTG** (it's a methodology guide, not a course)
- **Portfolio Evidence:** Apply all 91 tests against Phase 1 project (AI-Driven OS-Level Security Monitor); generate formal WSTG-compliant pentest report

---

### 6. MIT 18.06 — Linear Algebra (Spring 2010)
- **Primary URL:** https://ocw.mit.edu/courses/18-06-linear-algebra-spring-2010/
- **Lecture Videos:** https://www.youtube.com/playlist?list=PL49CF3715CB9EF31D
- **Textbook (Strang):** *Introduction to Linear Algebra, 5th Ed.* — PDF available via course site
- **Problem Sets:** https://ocw.mit.edu/courses/18-06-linear-algebra-spring-2010/pages/assignments/
- **Exams:** https://ocw.mit.edu/courses/18-06-linear-algebra-spring-2010/pages/exams/
- **Interactive Tool (Strang's Demos):** https://ocw.mit.edu/ans7870/18/18.06/tools.html

**Local Download:**
```bash
# Lecture videos
yt-dlp -f "bestvideo+bestaudio" --write-sub --sub-lang en \
  -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/MIT_18.06/lectures/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PL49CF3715CB9EF31D"

# Problem sets (scrape OCW)
mkdir -p "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/MIT_18.06/psets"
# Manual download required — OCW uses dynamic links
```

**Free Certificate Audit:**
- ❌ **MIT OCW does NOT offer certificates**
- **Portfolio Evidence:** Implement matrix operations library from scratch (Phase 1 ML detector uses this)

---

### 7. MIT 18.05 — Introduction to Probability and Statistics (Spring 2014)
- **Primary URL:** https://ocw.mit.edu/courses/18-05-introduction-to-probability-and-statistics-spring-2014/
- **Lecture Notes (HTML):** https://ocw.mit.edu/courses/18-05-introduction-to-probability-and-statistics-spring-2014/pages/readings/
- **Problem Sets:** https://ocw.mit.edu/courses/18-05-introduction-to-probability-and-statistics-spring-2014/pages/assignments/
- **No lecture videos** (text-based course)

**Local Download:**
```bash
# Clone OCW course repo (unofficial)
git clone https://github.com/emeryberger/OCW-18.05.git \
  "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/MIT_18.05" || \
mkdir -p "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/MIT_18.05"

# Lecture notes (HTML scrape)
wget --mirror --convert-links --adjust-extension --page-requisites --no-parent \
  -P "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/MIT_18.05" \
  https://ocw.mit.edu/courses/18-05-introduction-to-probability-and-statistics-spring-2014/pages/readings/
```

**Free Certificate Audit:**
- ❌ **MIT OCW does NOT offer certificates**
- **Portfolio Evidence:** Implement statistical tests (hypothesis testing, confidence intervals) from scratch; apply to Phase 1 anomaly detection

---

## 🎯 Phase 1 Certificate Summary

| Course | Free Verified Certificate? | Alternative Evidence |
|--------|---------------------------|---------------------|
| Stanford CS229 | ❌ NO | GitHub repo: all PS algorithms implemented |
| Berkeley CS188 | ❌ NO | Pacman projects + autograder scores |
| MIT 6.1810 (xv6) | ❌ NO | xv6 fork with Phase 1 kernel extension |
| PortSwigger Academy | ✅ PUBLIC PROFILE (100% completion) | Public profile: https://portswigger.net/users/[username] |
| OWASP WSTG | ❌ NO (methodology only) | Formal WSTG pentest report for Phase 1 project |
| MIT 18.06 | ❌ NO (OCW only) | Custom matrix library in Phase 1 ML detector |
| MIT 18.05 | ❌ NO (OCW only) | Statistical tests in anomaly detection |

**Key Insight:** Phase 1 has ZERO free verified certificates from academic institutions. The only public credential is **PortSwigger Web Security Academy public profile** showing 100% lab completion (viewable at `https://portswigger.net/users/[your_username]`).

**Recommendation:** Focus on building a **unified GitHub portfolio** with:
1. CS229/CS188 algorithm implementations
2. xv6 kernel extension (Phase 1 project)
3. PortSwigger lab writeups
4. WSTG pentest report

This portfolio IS the credential — more valuable to employers than isolated course certificates.

---

## 📥 Quick-Start Download Script

```bash
#!/bin/bash
# run_phase1_downloads.sh

set -e
echo "=== Phase 1 Asset Download ==="

# CS229
yt-dlp -f "bestvideo+bestaudio" \
  -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/CS229/lectures/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PLoROMvodv4rMiGQp3WXShtMGgzqpfVfbU" || echo "CS229 download failed"

# CS188
yt-dlp -f "bestvideo+bestaudio" \
  -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/CS188/lectures/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PLsOUugYMBBJENfZ3XAToMsg44W7LeUVhF" || echo "CS188 download failed"

# MIT 6.1810 (xv6)
git clone https://github.com/mit-pdos/xv6-riscv.git \
  "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/MIT_6.1810/xv6-riscv" || echo "xv6 clone failed"
curl -L https://pdos.csail.mit.edu/6.1810/2025/xv6/book-riscv-rev4.pdf \
  -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/MIT_6.1810/xv6_book.pdf"

# MIT 18.06
yt-dlp -f "bestvideo+bestaudio" \
  -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/MIT_18.06/lectures/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PL49CF3715CB9EF31D" || echo "MIT 18.06 download failed"

# WSTG
git clone https://github.com/OWASP/wstg.git \
  "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/OWASP_WSTG" || echo "WSTG clone failed"
curl -L https://github.com/OWASP/wstg/releases/download/v4.2/wstg-v4.2.pdf \
  -o "Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/OWASP_WSTG/wstg-v4.2.pdf"

echo "=== Phase 1 downloads complete ==="
echo "Assets located in: Roadmap_Execution/Phase_01_Semester_5_Fusion/Courses/Assets/"
```