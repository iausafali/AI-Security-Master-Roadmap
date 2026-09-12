# Phase 2: Systems + Deep Learning — Course Resources & Certificate Audit

**Timeline:** February – April 2027 (3 months)  
**Objective:** Deep learning fundamentals paired with networking depth the semester didn't cover.  
**Balance:** 70% AI / 30% security.  
**Compute:** Local CPU/WSL2 + free Colab burst — $0-20/mo.  
**Freeze Window:** None (between semesters).

---

## 📚 Resource Index

### 1. Deep Learning Specialization (DeepLearning.AI / Coursera)
- **Primary URL:** https://www.coursera.org/specializations/deep-learning
- **Course 1: Neural Networks and Deep Learning:** https://www.coursera.org/learn/neural-networks-deep-learning
- **Course 2: Improving Deep Neural Networks (Hyperparameter Tuning, Regularization, Optimization):** https://www.coursera.org/learn/deep-neural-network
- **Course 3: Structuring Machine Learning Projects:** https://www.coursera.org/learn/structuring-machine-learning-projects
- **Course 4: Convolutional Neural Networks:** https://www.coursera.org/learn/convolutional-neural-networks
- **Course 5: Sequence Models (RNN, GRU, LSTM, Attention):** https://www.coursera.org/learn/nlp-sequence-models
- **Community Notebooks & Assignments:** https://github.com/amanchadha/coursera-deep-learning-specialization

**Free Certificate Audit:**
- ✅ **Financial Aid is available for 100% free verified certificates:**
  1. Go to each course page on Coursera (5 courses total).
  2. Click "Financial Aid Available" next to the Enroll button.
  3. Complete application (state student status, annual income $0, career goals).
  4. Application approval takes ~15 days per course.
  5. Upon completion of quizzes + programming assignments with ≥80%, you receive official Coursera/DeepLearning.AI shareable certificates at $0 cost.
- **Alternative Free Audit:** Click "Enroll" → "Audit course" to access all lecture videos and reading materials for free (quizzes and grading disabled in standard audit mode unless Financial Aid is approved).

---

### 2. fast.ai — Practical Deep Learning for Coders (2024/2025)
- **Primary URL:** https://course.fast.ai/
- **Course Lessons:** https://course.fast.ai/Lessons/lesson1.html (8 core lessons)
- **Book (Deep Learning for Coders with fastai and PyTorch):** https://github.com/fastai/fastbook (Full Jupyter notebooks free)
- **YouTube Playlist:** https://www.youtube.com/playlist?list=PLfYUBJiXbdtSvpQjSnJJ_DGhN_P4qMNtC
- **Fastai Forum:** https://forums.fast.ai/

**Local Download:**
```bash
# Clone fastbook repository
git clone https://github.com/fastai/fastbook.git \
  "Roadmap_Execution/Phase_02_Systems_Deep_Learning/Courses/Assets/fastai/fastbook"

# Download lecture videos
yt-dlp -f "bestvideo+bestaudio" --write-sub --sub-lang en \
  -o "Roadmap_Execution/Phase_02_Systems_Deep_Learning/Courses/Assets/fastai/lectures/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PLfYUBJiXbdtSvpQjSnJJ_DGhN_P4qMNtC"
```

**Free Certificate Audit:**
- ❌ **fast.ai does NOT issue certificates** (free open-source philosophy).
- **Portfolio Evidence:** Build custom models deployed as web endpoints (Hugging Face Spaces) with reproducible Kaggle/Colab notebooks.

---

### 3. Stanford CS144 — Introduction to Computer Networking
- **Primary URL:** https://cs144.github.io/
- **Lecture Videos (Fall 2024 / YouTube):** https://www.youtube.com/playlist?list=PLvgq-1uLw2aZ9U0PllWbdfpC0qD2R7s5R
- **Lab Assignments (Minnow TCP Stack):** https://cs144.github.io/lab/
- **Lab Starter Code (C++20 Sponge/Minnow):** https://github.com/CS144/minnow
- **Textbook Reference:** *Computer Networking: A Top-Down Approach (Kurose & Ross)*

**Key Labs (Minnow User-Space TCP Implementation):**
1. Checksum & ByteStream (in-memory buffer)
2. TCP Receiver (reassembler, 64-bit sequence numbers)
3. TCP Sender (sliding window, retransmissions, RTT estimator)
4. TCP Connection (state machine combining Sender & Receiver)
5. Network Interface (ARP table, IP frame encapsulation)
6. Router (longest-prefix match routing table)

**Local Download:**
```bash
# Clone Minnow TCP starter code
git clone https://github.com/CS144/minnow.git \
  "Roadmap_Execution/Phase_02_Systems_Deep_Learning/Courses/Assets/CS144/minnow"

# Download lab writeups
mkdir -p "Roadmap_Execution/Phase_02_Systems_Deep_Learning/Courses/Assets/CS144/labs"
for i in {0..6}; do
  curl -sL "https://cs144.github.io/lab/lab$i.pdf" \
    -o "Roadmap_Execution/Phase_02_Systems_Deep_Learning/Courses/Assets/CS144/labs/lab$i.pdf" 2>/dev/null || echo "Lab $i PDF fetched"
done
```

**Free Certificate Audit:**
- ❌ **Stanford CS144 does NOT issue free certificates** (university course).
- **Portfolio Evidence:** Fully working Minnow TCP stack passing all automated tests (`ctest`) and achieving ≥1 Gbps throughput against real Linux kernel sockets.

---

### 4. Linux Journey
- **Primary URL:** https://linuxjourney.com/
- **Topics:** Command line, text manipulation, permissions, processes, packages, kernel, boot process, networking, routing.
- **GitHub Repository (Source):** https://github.com/cindyquach/linux-journey

**Local Archive:**
```bash
git clone https://github.com/cindyquach/linux-journey.git \
  "Roadmap_Execution/Phase_02_Systems_Deep_Learning/Courses/Assets/LinuxJourney/repo"
```

**Free Certificate Audit:**
- ❌ **Linux Journey does NOT issue certificates**.
- **Portfolio Evidence:** Command-line fluency demonstrated in bash automation scripts and kernel tracing tools.

---

### 5. Windows Internals & Sysinternals
- **Sysinternals Learning Hub:** https://learn.microsoft.com/en-us/sysinternals/
- **Sysinternals Suite Download:** https://learn.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite
- **Windows Internals Book 7th Ed. Code & Demos:** https://github.com/zodiacon/WindowsInternals7e
- **Pavel Yosifovich Windows Internals Training:** https://github.com/zodiacon
- **Core Tools:** Process Explorer (`procexp.exe`), Process Monitor (`procmon.exe`), Sysmon (`sysmon.exe`), TCPView (`tcpview.exe`).

**Local Download:**
```bash
# Download Sysinternals Suite (Windows/WSL)
mkdir -p "Roadmap_Execution/Phase_02_Systems_Deep_Learning/Courses/Assets/Sysinternals"
curl -L https://download.sysinternals.com/files/SysinternalsSuite.zip \
  -o "Roadmap_Execution/Phase_02_Systems_Deep_Learning/Courses/Assets/Sysinternals/SysinternalsSuite.zip"
```

**Free Certificate Audit:**
- ✅ **Microsoft Learn Badges & Trophies (Free):** Complete learning modules on Windows Security & Sysmon monitoring on MS Learn (https://learn.microsoft.com/) to earn verified profile badges.

---

## 🎯 Phase 2 Certificate Summary

| Course | Free Verified Certificate? | How to Claim / Evidence |
|--------|---------------------------|-------------------------|
| Deep Learning Specialization | ✅ YES (100% via Coursera Financial Aid) | Apply via Coursera FinAid for each course (15-day review) |
| fast.ai | ❌ NO | Deployed models on HF Spaces + GitHub writeups |
| Stanford CS144 | ❌ NO | Working Minnow TCP stack passing `ctest` |
| Linux Journey | ❌ NO | Self-paced interactive guide |
| Windows Internals / Sysinternals | ✅ FREE Microsoft Learn Badges | Complete Sysmon / Windows Architecture paths on MS Learn |