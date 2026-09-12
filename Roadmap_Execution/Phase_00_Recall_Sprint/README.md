[← Back to Master Execution Table](../../README.md)

# Phase 0: Recall Sprint — Secure Systems Utility Suite

**Timeline:** September 8 – September 25, 2026 (Canonical Phase Window)  
**Execution Start:** September 12, 2026  
**Compute Tier:** Local CPU / WSL2 — $0  
**Project Directory:** `Project_Utility_Suite/`  
**Core Objective:** Cold recall of systems programming, pointers, low-level memory layout, networking sockets, and data structures.

---

## 📅 Granular Day-by-Day Execution Schedule (Execution Sequence)

> The canonical phase window is **Sep 8–25, 2026**. This detailed sequence is a 16-day execution sequence designed to begin on Sep 12; compress or combine non-critical blocks as needed so the phase closes by Sep 25.

### 🕒 Days 1–2 — C Memory & Pointer Bridge
* **The 30/70 Fluff Filter:**
  * ❌ **SKIP:** CS50x Weeks 0 (Scratch), 1 (C Syntax/Loops), and 2 (Arrays/Compiling).
  * ❌ **SKIP:** SQLBolt basic `SELECT` intro.
  * ▶️ **WATCH:** CS50x Week 4 (Memory) at 1.5x speed (`malloc`/`free`, pointers, pointer arithmetic, stack vs. heap layout, `char*`, dereferencing, valgrind fundamentals).
  * ▶️ **STUDY:** MIT 6.006 Lecture 1 (Algorithmic Thinking & Peak Finding) + Lecture 2 (Data Structures & Dynamic Arrays).
* **WSL2 Lab Work & Deliverables:**
  * Build 3 standalone C micro-programs in `Project_Utility_Suite/tests/micro/`:
    1. `dynamic_array.c`: Resizable dynamic array of arbitrary structs with `realloc` doubling strategy and geometric growth amortized analysis ($O(1)$).
    2. `ptr_string_swap.c`: In-place pointer manipulation, manual string tokenization, and substring reverse without allocating extra heap buffers.
    3. `struct_file_stream.c`: Binary file I/O reading/writing raw structs with endianness preservation using `fread`, `fwrite`, and `fseek`.
  * **Zero-Leak Memory Gate:** Run all 3 programs through Valgrind:
    ```bash
    gcc -Wall -Wextra -Wpedantic -g3 dynamic_array.c -o dynamic_array
    valgrind --leak-check=full --show-leak-kinds=all --track-origins=yes --error-exitcode=1 ./dynamic_array
    ```
    *Exit Bar: 0 errors from 0 contexts, 0 bytes in use at exit.*

---

### 🕒 Days 3–6 — Systems Utility Engine (Integrity & Log Analyzer)
* **The 30/70 Fluff Filter:**
  * ❌ **SKIP:** Standard textbook string manipulation libraries (`string.h` wrapper abstractions like `strtok` stateful quirks).
  * ▶️ **STUDY:** OpenSSL EVP API documentation (`man EVP_DigestInit_ex`) and POSIX directory traversal (`opendir`, `readdir`, `stat`).
* **Sprint 1 (Days 3–4) — CLI File Integrity Checker (`integrity.c`):**
  * Implement SHA-256 file hashing via C file I/O chunking (64KB read buffers).
  * Build an in-memory Merkle Tree: calculate hash of each file leaf → construct binary tree → compute single Root Manifest Fingerprint.
  * Store manifest as a memory-mapped binary file (`mmap`) for instant O(1) random-access verification against tampering.
* **Sprint 2 (Days 5–6) — Pure C Log Analyzer (`log_analyzer.c`):**
  * Single-pass, streaming log parser in pure C without external heavy libraries.
  * Direct pointer-walking parser for `/var/log/syslog` and `/var/log/auth.log`.
  * Sliding-window state tracker: detect ≥ 5 failed SSH authentication attempts within a 300-second window.
  * Stream formatted alerts directly into structured JSONL format to `stdout`.

---

### 🕒 Days 7–12 — Low-Level C Networking & Database Integration
* **The 30/70 Fluff Filter:**
  * ❌ **SKIP:** High-level web framework tutorials and socket wrappers (e.g., libcurl, libuv).
  * ▶️ **STUDY:** Beej's Guide to Network Programming (Chapters 3–7: Sockets, Structs, `bind`, `listen`, `accept`, `select`/`epoll`).
  * ▶️ **STUDY:** SQLite3 C/C++ Interface Specification (`sqlite3_prepare_v2`, `sqlite3_bind_*`, `sqlite3_step`).
* **Sprint 3 (Days 7–9) — Raw POSIX TCP Client & Server (`tcp_server.c`, `tcp_client.c`):**
  * Implement a concurrent TCP Server handling raw binary frames (4-byte Big-Endian length header + payload).
  * Handle edge cases: partial sends/receives (`recv()` returning less than requested), `SIGPIPE` ignores, non-blocking sockets via `fcntl` and `epoll`.
  * Build an interactive CLI client REPL with connection retry, keepalive, and hex dump inspection.
* **Sprint 4 (Days 10–11) — CLI SQLite Database Layer (`cli_db.c`):**
  * Integrate `<sqlite3.h>` using prepared statements only — **zero string concatenation**.
  * Schema: `files(id INTEGER PRIMARY KEY, path TEXT UNIQUE, hash TEXT, size INT, mtime INT, manifest_id INT)`.
  * Enable Write-Ahead Logging (WAL mode) and verify concurrent read performance.
* **Sprint 5 (Day 12) — Minimal HTTP/1.1 Static Server (`http_server.c`):**
  * Implement an RFC 7230 compliant HTTP/1.1 parser from raw socket buffers.
  * Handle `GET`, `HEAD`, `Connection: keep-alive`, chunked transfer encoding, and zero-copy file transmission via `sendfile()`.

---

### 🕒 Days 13–16 — Audit, Debugging & GDB Patching
* **The 30/70 Fluff Filter:**
  * ❌ **SKIP:** IDE GUI debuggers — use raw GDB CLI and AddressSanitizer.
  * ▶️ **STUDY:** GDB advanced commands: layout asm, conditional breakpoints, memory watchpoints (`watch *ptr`), frame inspection (`bt full`).
* **GDB Break-and-Patch Protocol (Days 13–14):**
  1. **Introduce Bug 1 (Stack Buffer Overflow):** Introduce an unchecked `memcpy` in `http_server.c:parse_headers` when parsing custom headers > 8192 bytes.
  2. **Introduce Bug 2 (Heap Use-After-Free):** Force an early `free()` on the client connection struct in `tcp_server.c` before an asynchronous write completion callback.
  3. **Reproduce Crash in GDB:**
     ```bash
     gcc -g3 -fno-stack-protector -z execstack src/http_server.c -o http_server
     gdb ./http_server
     (gdb) run 8080
     # Send exploit payload via python script
     (gdb) bt full
     (gdb) info registers
     ```
  4. **Patch & Verify:** Replace vulnerable buffers with bounded string operations, compile with `-fsanitize=address,undefined,leak -fstack-protector-strong`, and verify zero crashes.
* **Final Verification Sign-Off (Days 15–16):**
  * Execute 24-hour fuzz test using `afl-clang-fast`.
  * Benchmark TCP throughput against `iperf3` baseline (≥ 8 Gbps loopback).
  * Compile `AUDIT_REPORT.md` and seal git tag `v0.6-audit-complete`.

---

## 🏗 System Architecture

```text
┌─────────────────────────────────────────────────────────────────┐
│                    Secure Systems Utility Suite                  │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌──────────────┐  ┌──────────────────┐  ┌──────────────────┐  │
│  │  TCP Client  │  │ File-Integrity   │  │    Log Analyzer  │  │
│  │  / Server    │  │    Checker       │  │  (syslog/auth)   │  │
│  │  (C/Raw      │  │  (SHA-256,       │  │  Regex + JSON    │  │
│  │   Sockets)   │  │   Merkle Tree)   │  │  Output)         │  │
│  └──────┬───────┘  └────────┬─────────┘  └────────┬─────────┘  │
│         │                   │                      │            │
│         └───────────────────┼──────────────────────┘            │
│                             ▼                                   │
│              ┌──────────────────────────────┐                  │
│              │      CLI Database App        │                  │
│              │    (SQLite3 + Prepared       │                  │
│              │     Statements)              │                  │
│              └──────────────┬───────────────┘                  │
│                             │                                   │
│                             ▼                                   │
│              ┌──────────────────────────────┐                  │
│              │      HTTP/1.1 Server         │                  │
│              │  (Chunked encoding, headers, │                  │
│              │   static file serve)         │                  │
│              └──────────────────────────────┘                  │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🔬 Engineering Verification Protocol

### Stage 1: Derive — Mathematical Foundations
- **TCP Congestion Control (Reno):**
  $$W_{\text{new}} = W + \frac{1}{W} \quad (\text{Congestion Avoidance})$$
- **Merkle Tree Inclusion Proof:**
  $$\text{Root} = H(H(L_1 \parallel L_2) \parallel H(L_3 \parallel L_4))$$
- **SHA-256 Compression Schedule:**
  $$W_t = \sigma_1(W_{t-2}) + W_{t-7} + \sigma_0(W_{t-15}) + W_{t-16}$$

### Stage 2: Implement — Zero Wrappers
- Written in clean C17 with zero third-party wrapper dependencies.
- Compile flags: `-std=c17 -Wall -Wextra -Wpedantic -Werror -O2 -g3`.

### Stage 3: Benchmark — Performance Targets
- TCP Throughput: ≥ 8 Gbps loopback.
- Integrity Check: ≤ 2.0s per 10,000 files.
- Memory Footprint: ≤ 5 MB RSS under 100 concurrent connections.
- Valgrind Leak Check: 0 bytes leaked.

### Stage 4: Break & Patch
- Introduce CWE-121 (Stack Overflow) and CWE-416 (Heap UAF).
- Trace in GDB, capture registers, patch with bounds checks, re-verify with AddressSanitizer.

---

## ✅ Exit Criteria Checklist
- [ ] Micro-programs pass Valgrind with 0 leaks.
- [ ] File integrity checker computes deterministic Merkle roots over directories.
- [ ] Log analyzer detects brute-force SSH attacks in real time and streams JSONL.
- [ ] TCP client/server handles 100 concurrent connections via `epoll`.
- [ ] HTTP/1.1 server serves static files with keep-alive and chunked responses.
- [ ] Stack overflow and UAF reproduced in GDB and remediated.
- [ ] Git repo tagged `v0.6-audit-complete`.
