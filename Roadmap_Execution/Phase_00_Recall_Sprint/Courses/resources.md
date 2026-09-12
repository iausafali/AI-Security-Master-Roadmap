# Phase 0: Recall Sprint — Course Resources & Certificate Audit

**Timeline:** September 12–27, 2026 (16 days)  
**Objective:** Cold recall of calculus, linear algebra, DSA, and OOP forgotten over the summer.  
**Balance:** 100% foundational; no AI/security split yet.  
**Compute:** Local only, zero cost.

---

## 📚 Resource Index

### 1. CS50x — Introduction to Computer Science (Harvard)
- **Primary URL:** https://cs50.harvard.edu/x/
- **Lecture Videos:** https://www.youtube.com/playlist?list=PLhQjrBD2T382_TiJqI5zV-jKsK2T8zJxO
- **Problem Sets:** https://cs50.harvard.edu/x/2024/psets/
- **Syllabus:** https://cs50.harvard.edu/x/2024/syllabus/
- **Ed Discussion:** https://edstem.org/join/351Q9J
- **Gradebook:** https://cs50.harvard.edu/x/2024/gradebook/
- **Submission Portal:** https://submit.cs50.io/
- **GitHub Codespaces Template:** https://github.com/cs50/codespace

**Local Download (yt-dlp):**
```bash
# Full lecture playlist (2024)
yt-dlp -f "bestvideo+bestaudio" --write-sub --sub-lang en \
  -o "Roadmap_Execution/Phase_00_Recall_Sprint/Courses/Assets/CS50x/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PLhQjrBD2T382_TiJqI5zV-jKsK2T8zJxO"

# Individual problem set specs (HTML)
mkdir -p "Roadmap_Execution/Phase_00_Recall_Sprint/Courses/Assets/CS50x/psets"
for i in {0..9}; do
  curl -s "https://cs50.harvard.edu/x/2024/psets/$i/" \
    -o "Roadmap_Execution/Phase_00_Recall_Sprint/Courses/Assets/CS50x/psets/pset$i.html"
done
```

**Free Verified Certificate Audit:**
- ✅ **CS50x offers a FREE verified certificate via edX Audit Track → Upgrade path**
- **Enrollment Steps:**
  1. Go to https://learning.edx.org/course/course-v1:HarvardX+CS50+X/
  2. Click "Enroll" → Select "Audit" (free)
  3. Complete all 9 problem sets + final project with ≥70% each
  4. Certificate auto-issued on edX dashboard — **no payment required**
- **Deadline:** Self-paced; typical completion 10–12 weeks, but recall sprint targets 16 days
- **Badge:** Verified certificate appears on LinkedIn/edX profile

---

### 2. MIT 6.006 — Introduction to Algorithms (Spring 2020)
- **Primary URL:** https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/
- **Lecture Videos:** https://www.youtube.com/playlist?list=PLUl4u3cNGP61Oq3tWYp6V_F-5jb5L2iHb
- **Recitation Videos:** https://www.youtube.com/playlist?list=PLUl4u3cNGP63WbdFxL8h1P2VBC8s6PvZd
- **Problem Sets (PDF):** https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/assignments/
- **Exams & Solutions:** https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/exams/
- **Readings (CLRS chapters):** https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/readings/
- **Syllabus:** https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/syllabus/

**Local Download:**
```bash
# Lecture videos
yt-dlp -f "bestvideo+bestaudio" --write-sub --sub-lang en \
  -o "Roadmap_Execution/Phase_00_Recall_Sprint/Courses/Assets/MIT_6.006/lectures/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PLUl4u3cNGP61Oq3tWYp6V_F-5jb5L2iHb"

# Recitations
yt-dlp -f "bestvideo+bestaudio" --write-sub --sub-lang en \
  -o "Roadmap_Execution/Phase_00_Recall_Sprint/Courses/Assets/MIT_6.006/recitations/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PLUl4u3cNGP63WbdFxL8h1P2VBC8s6PvZd"

# Problem sets & exams (PDF)
mkdir -p "Roadmap_Execution/Phase_00_Recall_Sprint/Courses/Assets/MIT_6.006/psets"
for i in {1..8}; do
  curl -sL "https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-spring-2020/assignments/pset$i/" \
    | grep -oP '(?<=href=")[^"]*\.pdf(?=")' | head -1 \
    | xargs -I {} curl -sL "https://ocw.mit.edu{}" \
    -o "Roadmap_Execution/Phase_00_Recall_Sprint/Courses/Assets/MIT_6.006/psets/pset$i.pdf"
done
```

**Free Certificate Audit:**
- ❌ **MIT OCW does NOT offer certificates** (open courseware only)
- **Alternative:** Complete all problem sets + exams locally; self-grade using provided solutions
- **Portfolio Evidence:** Push annotated solutions to GitHub repo as proof of mastery

---

### 3. SQLBolt — Interactive SQL Tutorial
- **Primary URL:** https://sqlbolt.com/
- **Lessons:** https://sqlbolt.com/lesson/select_queries_introduction (18 lessons + exercises)
- **No video content** — fully browser-based interactive exercises

**Local Archive:**
```bash
# Mirror the full tutorial for offline use
mkdir -p "Roadmap_Execution/Phase_00_Recall_Sprint/Courses/Assets/SQLBolt"
wget --mirror --convert-links --adjust-extension --page-requisites --no-parent \
  -P "Roadmap_Execution/Phase_00_Recall_Sprint/Courses/Assets/SQLBolt" \
  https://sqlbolt.com/
```

**Free Certificate Audit:**
- ❌ **SQLBolt does NOT offer certificates**
- **Alternative:** Complete all 18 lessons + exercises; screenshot final lesson completion
- **Portfolio Evidence:** Create a local SQLite database demonstrating all query types learned

---

## 🎯 Phase 0 Certificate Summary

| Course | Free Verified Certificate? | Alternative Evidence |
|--------|---------------------------|---------------------|
| CS50x | ✅ YES (edX Audit → Verified) | GitHub repo with all PSETs |
| MIT 6.006 | ❌ NO (OCW only) | Annotated solutions repo |
| SQLBolt | ❌ NO | Screenshots + SQLite demo DB |

**Recommendation:** Prioritize CS50x certificate — it's the only verifiable credential in this phase and carries Harvard branding. Use MIT 6.006 for rigorous algorithm practice; SQLBolt for quick SQL fluency.

---

## 📥 Quick-Start Download Script

```bash
#!/bin/bash
# run_phase0_downloads.sh
# Run from repository root

set -e

echo "=== Phase 0 Asset Download ==="

# CS50x
echo "Downloading CS50x lectures..."
yt-dlp -f "bestvideo+bestaudio" --write-sub --sub-lang en \
  -o "Roadmap_Execution/Phase_00_Recall_Sprint/Courses/Assets/CS50x/lectures/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PLhQjrBD2T382_TiJqI5zV-jKsK2T8zJxO" || echo "CS50x download failed (check yt-dlp)"

# MIT 6.006 Lectures
echo "Downloading MIT 6.006 lectures..."
yt-dlp -f "bestvideo+bestaudio" --write-sub --sub-lang en \
  -o "Roadmap_Execution/Phase_00_Recall_Sprint/Courses/Assets/MIT_6.006/lectures/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PLUl4u3cNGP61Oq3tWYp6V_F-5jb5L2iHb" || echo "MIT 6.006 lectures failed"

# MIT 6.006 Recitations
echo "Downloading MIT 6.006 recitations..."
yt-dlp -f "bestvideo+bestaudio" --write-sub --sub-lang en \
  -o "Roadmap_Execution/Phase_00_Recall_Sprint/Courses/Assets/MIT_6.006/recitations/%(playlist_index)02d-%(title)s.%(ext)s" \
  "https://www.youtube.com/playlist?list=PLUl4u3cNGP63WbdFxL8h1P2VBC8s6PvZd" || echo "MIT 6.006 recitations failed"

# SQLBolt (full site mirror)
echo "Mirroring SQLBolt..."
wget --mirror --convert-links --adjust-extension --page-requisites --no-parent \
  -P "Roadmap_Execution/Phase_00_Recall_Sprint/Courses/Assets/SQLBolt" \
  https://sqlbolt.com/ || echo "SQLBolt mirror failed"

echo "=== Phase 0 downloads complete ==="
echo "Assets located in: Roadmap_Execution/Phase_00_Recall_Sprint/Courses/Assets/"
```